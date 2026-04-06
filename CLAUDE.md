# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository overview

Jekyll-based personal blog (华航笔记) published at https://blog.huahang.im via GitHub Pages (CNAME-backed). Content is Chinese-language posts under `_posts/`. Uses the `minima` theme — there are no custom layouts/includes/sass in the repo, all theme assets come from the gem.

## Commands

- `bundle install` — install gem dependencies.
- `bundle exec jekyll serve` — run local dev server with live reload.
- `bundle exec jekyll build` — build the static site into `_site/`.
- `bundle exec jekyll post "Title"` — scaffold a new post in `_posts/` (via jekyll-compose).
- `bundle exec jekyll draft "Title"` / `bundle exec jekyll publish _drafts/...` — draft workflow.

Note: `_config.yml` is NOT auto-reloaded; restart `jekyll serve` after editing it.

## Architecture notes

- `_config.yml` pins `url: https://blog.huahang.im` and enables plugins: `jekyll-admin`, `jekyll-compose`, `jekyll-feed`, `jekyll-seo-tag`, `jekyll-sitemap`. Markdown engine is `kramdown`.
- Gemfile pins `jekyll ~> 3.8.5` and `minima ~> 2.5.0` — this is an older Jekyll 3.x site, not GitHub Pages' bundled version (the `github-pages` gem is deliberately commented out). Keep version-sensitive syntax compatible with Jekyll 3.8.
- Posts in `_posts/` follow `YYYY-MM-DD-slug.md` naming and use standard Jekyll front matter. Content is primarily in Chinese.
- No tests, linters, or CI configured. Recent commits are almost entirely content edits plus Dependabot bumps of transitive gems (addressable, rack).

## Git conventions

- Commit messages must follow the [Conventional Commits](https://www.conventionalcommits.org/) format (e.g. `feat:`, `fix:`, `chore:`, `docs:`, `build(deps):`).
- Always commit with sign-off (`git commit -s`) so a `Signed-off-by:` trailer is included.
