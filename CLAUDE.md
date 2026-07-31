# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

A personal blog built with **Hugo v0.164.0 (extended)** and the **hugo-theme-stack** theme, deployed to GitHub Pages. Content is written in Chinese (zh-cn).

## Commands

```bash
# Local development server (with draft posts)
hugo server -D

# Production build
hugo --gc --minify

# Create a new post
hugo new post/<post-name>/index.md

# Create a new post with archetype
hugo new --kind <archetype> post/<post-name>/index.md
```

## Project Structure

```
myblog/
├── assets/
│   ├── img/avatar.jpg          # Sidebar avatar image
│   └── jsconfig.json           # JS path mapping for theme assets
├── archetypes/
│   └── default.md              # Default front matter template for new posts
├── content/
│   └── post/
│       ├── hello-world/        # First blog post
│       └── hugo-stack-guide/   # Hugo + Stack theme setup guide
├── layouts/
│   └── _partials/head/
│       └── custom-font.html    # Overrides theme fonts with system font stack (China CDN optimization)
├── themes/
│   └── hugo-theme-stack/       # Git submodule (CaiJimmy/hugo-theme-stack)
├── .github/workflows/hugo.yml  # GitHub Actions: auto-build & deploy to Pages on main push
├── .gitignore                  # Ignores /public/, /resources/_gen/, .hugo_build.lock
└── config.yaml                 # All Hugo site configuration
```

## Architecture

- **Hugo static site generator** — no runtime dependencies beyond the Hugo binary. No Node.js or Go needed to build.
- **Theme**: `hugo-theme-stack` is a Git submodule. Customizations live outside the theme in `layouts/` (Hugo's lookup order prioritizes site-level over theme-level templates).
- **CI/CD**: GitHub Actions workflow (`.github/workflows/hugo.yml`) builds with `hugo --gc --minify` and deploys to GitHub Pages via `actions/deploy-pages`.
- **Content**: Posts live under `content/post/<slug>/index.md` with Markdown front matter. Each post is its own directory (page bundle) for per-post image assets.

## Key Configuration

- **config.yaml** contains all settings: base URL, theme, sidebar avatar, menu (social links), pagination (5 per page), article TOC, Markdown rendering (unsafe HTML enabled), and syntax highlighting.
- **Avatar** is at `assets/img/avatar.jpg` — Hugo processes `assets/` with Pipes; use `static/` for raw files.
- Custom font override at `layouts/_partials/head/custom-font.html` uses a system font stack to avoid Google Fonts latency in China.

## Deployment

Pushing to the `main` branch triggers the GitHub Actions workflow. The workflow:
1. Checks out with submodules (to pull the theme)
2. Installs Hugo extended 0.164.0
3. Runs `hugo --gc --minify`
4. Uploads `./public` as a Pages artifact
5. Deploys via `actions/deploy-pages`
