# Agent notes

See `README.md` for local preview and where content lives.

## Publishing (manual, to `gh-pages`)

The live site (https://yushunxiang.github.io/) is served from the **`gh-pages` branch** (GitHub Pages source: "Deploy from a branch", `gh-pages` / root).
The `deploy` job in `.github/workflows/gh-pages.yml` does **not** update the live site under this setting, so merging to `main` alone does not publish anything.
Every update must be published by hand after it lands on `main`:

```sh
git checkout main && git pull --ff-only
SITE=$(mktemp -d); GHP=$(mktemp -d)/ghp; SHA=$(git rev-parse --short main)

# 1. Production build of main into a clean directory
HUGO_ENVIRONMENT=production hugo --gc --minify -d "$SITE"

# 2. Check out gh-pages in a separate worktree and replace its contents
git fetch origin
git worktree add --detach "$GHP" origin/gh-pages
rsync -a --delete --exclude .git --exclude .nojekyll "$SITE"/ "$GHP"/

# 3. Review, commit and push (a normal fast-forward push, never --force)
cd "$GHP" && git add -A && git status --short
git commit -m "Publish production homepage from $SHA"
git push origin HEAD:gh-pages
cd - && git worktree remove "$GHP"
```

- Keep `.nojekyll` on `gh-pages` (Hugo does not generate it; the rsync excludes it).
- Before committing, check that `git status --short` only lists files the change should touch. A homepage-only change shows `index.html` plus a renamed `css/home.min.<hash>.css`.
- Name the commit `Publish production homepage from <short sha of main>`.
- Verify: `gh api repos/YushunXiang/yushunxiang.github.io/pages/builds/latest --jq .status` reaches `built` for the new commit, then `curl -s https://yushunxiang.github.io/` shows the change.

If Pages is later switched to **Source: GitHub Actions** (Settings → Pages), pushes to `main` deploy automatically through the workflow and this manual step is no longer needed. Update this file if that happens.
