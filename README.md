# Yushun Xiang's academic homepage

A Hugo website, published at [yushunxiang.github.io](https://yushunxiang.github.io/). The homepage is a standalone template; posts and other pages use the [HugoBlox](https://github.com/HugoBlox/kit) theme (Tailwind CSS v4). The separate Hexo blog is maintained independently.

## Local preview

Requirements: **Hugo Extended 0.170.1** (`brew install hugo`), **Go** (`brew install go`, used to download the theme module) and **Node.js** (for Tailwind CSS).

```sh
npm install      # first time, or after package.json changes
hugo server      # http://localhost:1313
```

The first run downloads the HugoBlox module, which takes a little while. To check the production build, run `hugo --gc --minify`; output goes to `public/`.

When upgrading Hugo, also update `HUGO_VERSION` in `.github/workflows/gh-pages.yml` so CI and local builds match.

## Content

| What | Where |
|---|---|
| Publications (title, authors, venue, links, figure) | `data/publications.yaml`; figures in `static/images/pubs/` |
| News | `data/news.yaml` |
| Bio, interests, education, honors, email | `data/authors/me.yaml` |
| Portrait | `assets/media/authors/me.jpg` |
| CV | `static/uploads/CV.pdf` |
| Homepage layout and styles | `layouts/home.html`, `assets/css/home.css` |
| Navigation on theme pages | `config/_default/menus.yaml` |
| Theme settings (colors, header, math, etc.) | `config/_default/params.yaml` |

To add a post, create `content/post/<slug>/index.md` with YAML front matter (`title`, `date`, optional `summary`, `tags`, `categories`, and `math: true` if needed), followed by Markdown. Put images in the same folder and reference them by filename; a `featured.jpg` becomes the post's cover.

## GitHub Pages

In **Settings → Pages → Build and deployment**, set **Source** to **GitHub Actions**. Pushes to `main` build and deploy the site; pull requests only run the build.
