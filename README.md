# Bates' Blog

Personal blog built with [Hugo](https://gohugo.io/) + [PaperMod](https://github.com/adityatelange/hugo-PaperMod) theme, deployed to GitHub Pages.

**Live site:** https://bates33.github.io/

## Project Structure

```
.
├── assets/css/extended/    # Custom CSS overrides (DO NOT edit theme files)
├── content/posts/          # Blog posts (Markdown with front matter)
├── layouts/                # Layout overrides (single.html for floating TOC)
│   ├── _default/single.html
│   └── shortcodes/cf_img.html
├── themes/PaperMod/        # Theme (git submodule, do not modify)
├── .github/workflows/      # GitHub Actions deploy workflow
├── hugo.toml               # Site configuration
└── static/                 # Static assets (favicon, etc.)
```

## Prerequisites

Install Hugo (extended version):

```bash
brew install hugo
```

## Local Development

```bash
# Start local dev server with drafts
hugo server --buildDrafts

# Site will be available at http://localhost:1313/
```

## Writing a New Post

Create a new Markdown file in `content/posts/`:

```bash
hugo new content posts/my-new-post.md
```

Or manually create a file with front matter:

```yaml
---
title: "文章标题"
date: "2025-02-08"
tags: ["标签1", "标签2"]
description: "文章简介"
summary: "文章简介"
draft: false
ShowToc: true
TocOpen: true
---

正文内容...
```

Set `draft: true` to hide the post from production.

## Using Cloudflare Images

Use the `cf_img` shortcode to reference images hosted on Cloudflare R2:

```
{{</* cf_img src="travel/japan.jpg" alt="Japan Trip" */>}}
```

This automatically prepends `https://static.bybates.com/` to the `src`.

You can also use standard Markdown images with full URLs:

```markdown
![alt text](https://static.bybates.com/blog-01-02.png)
```

## Deploy

Deployment is **automatic** — just push to `main`:

```bash
git add -A
git commit -m "describe your changes"
git push
```

GitHub Actions will build the site and deploy to GitHub Pages. The workflow typically completes in ~30 seconds.

### Manual Re-deploy

Go to the repo's [Actions tab](https://github.com/bates33/bates33.github.io/actions), select the workflow, and click "Run workflow".

## Design Notes

- **Accent color:** `#cb4042` (red) — used for titles, links, buttons, tags
- **Font stack:** Inter, PingFang SC, Hiragino Sans GB, Microsoft YaHei
- **TOC:** Floating sidebar on desktop (≥1280px), inline on mobile
- **Dark mode:** Disabled
- **Theme overrides** go in `layouts/` and `assets/css/extended/` — never edit files inside `themes/PaperMod/`
