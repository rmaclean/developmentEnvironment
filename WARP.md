# WARP.md

This file provides guidance to WARP (warp.dev) when working with code in this repository.

Repository overview
- This repository is a lightweight GitHub Pages/Jekyll site that documents a personal development environment and hosts related configuration assets.
- Jekyll site configuration is minimal: the theme is set in _config.yml, and the landing page/content is in index.md. There are no custom plugins, layouts, or a Gemfile present.
- The configs/ directory contains editor/terminal/keymap JSON files referenced from the site and served as static assets. The cura_profiles/ directory contains 3D-printing profiles also linked from the site. These directories are not “built” by any tool; they are published as static files and linked by index.md.

Common commands
- Prerequisites (first time only): install Ruby and Jekyll.
```bash path=null start=null
# macOS prerequisites
brew install ruby

# Install Jekyll and Bundler gems (user-level install)
gem install jekyll bundler
```
- Serve the site locally with live reload:
```bash path=null start=null
jekyll serve --livereload
```
- Build the static site to ./_site:
```bash path=null start=null
jekyll build
```
- Clean generated files:
```bash path=null start=null
jekyll clean
```
Notes on tests/linting
- This repository does not define tests or lint tasks. There are no package manifests (Gemfile, package.json, etc.) or CI workflows in the tree.

High-level architecture and structure
- Site engine: Jekyll. The site relies on the built-in theme specified via _config.yml:
  - _config.yml: sets theme: jekyll-theme-architect, which controls site styling and layout.
  - index.md: main content page with links to external tools and to local configuration assets (e.g., configs/uhk.json, configs/vscode.json, configs/terminal.json, and cura_profiles/* files). The Markdown is simple and does not introduce custom Liquid templates.
- Content vs. assets:
  - Content: Markdown pages at the repo root (currently index.md). With this minimal setup, Jekyll serves/renders these pages for the site.
  - Assets: Any non-underscored directories (configs/, cura_profiles/) are served statically. The linked JSON and text profile files are downloadable/viewable as-is; they are not transformed by the Jekyll build.
- Build/publish model:
  - Local development uses jekyll serve to preview changes. The static site is output to _site when building locally.
  - GitHub Pages typically builds Jekyll sites on push. Because there is no Gemfile or custom plugins, it should work with GitHub’s default Jekyll environment.

Important sources (from existing content)
- _config.yml: sets the site theme to jekyll-theme-architect.
- index.md: documents the development setup (e.g., Fish shell, Starship, VS Code) and links to:
  - configs/uhk.json (Ultimate Hacking Keyboard configuration)
  - configs/vscode.json (VS Code settings)
  - configs/terminal.json (Windows Terminal profile)
  - cura_profiles/* (Cura/Fusion-related profiles)

