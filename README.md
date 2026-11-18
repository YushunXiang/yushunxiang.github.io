# Yushun Xiang's academic homepage

A Hugo and Wowchemy academic website, published at [yushunxiang.github.io](https://yushunxiang.github.io/). The separate Hexo blog is maintained independently.

## Local preview

Install **Hugo Extended 0.121.2** and **Go 1.21**. Go is needed to download the Hugo modules specified in `go.mod`. From the repository root, run:

```sh
hugo server
```

Open the local address printed by Hugo. To check the production build, run `hugo --gc --minify`; the generated site is written to `public/`.

## Content

- Edit `content/authors/admin/_index.md` for the biography, interests, education, social links, and honors. Replace `content/authors/admin/avatar.jpg` to update the portrait.
- Edit `content/_index.md` for homepage sections and `config/_default/menus.yaml` for navigation. Update the contact email in both the homepage and author profile when necessary.
- To add a post, create `content/post/<slug>/index.md` with YAML front matter (`title`, `date`, optional `summary`, `tags`, and `categories`), followed by Markdown. Put images in the same directory and refer to them by relative filename. Set `math: true` for a post containing mathematical notation.
- Replace `static/uploads/CV.pdf` to update the CV. Template publications, projects, talks, and slides are retained as drafts; replace their content with verified information before publishing them.
- Site appearance overrides live in `assets/scss/custom.scss`. Site metadata and feature settings live in `config/_default/`.

## GitHub Pages

In the repository's **Settings → Pages → Build and deployment**, set **Source** to **GitHub Actions**. Pushes to `main` build and deploy the site; pull requests run the build without deploying. The workflow can also be run manually on `main`. Check the **Actions** tab and the `github-pages` deployment environment for build or deployment errors. The first build may need network access to download Hugo modules.
