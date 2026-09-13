# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

@AGENTS.md

`AGENTS.md` (imported above) is the entry point: where each kind of content lives, the silent failure modes, and the validation commands. Read it before editing.

## Daily dev loop

Ruby 3.x is required (system Ruby 2.6 on macOS is too old). A Homebrew Ruby works:

```bash
export PATH="/opt/homebrew/opt/ruby/bin:$PATH"
bundle install                                # gems are installed into vendor/bundle (see .bundle/config)
bundle exec jekyll serve                      # dev server at http://localhost:4000/
bundle exec jekyll build                      # production-style build to _site/
npm ci && npm run lint:prettier               # Prettier with the Liquid plugin (printWidth 150)
```

ImageMagick (`brew install imagemagick`) must be on `PATH` because `imagemagick.enabled: true` generates responsive `.webp` variants of `.jpg`/`.png` files in `assets/img/`.

## Comments (giscus)

Comments use GitHub Discussions on `bananenpampe/academic-page` (category "Announcements"). The IDs are in `_config.yml` under `giscus:`; `deploy.yml` also rewrites `giscus.repo` to the repository name at build time. Pages opt in with `giscus_comments: true`. Comments render only once the giscus GitHub App is installed on the repository (https://github.com/apps/giscus).

## Deployment

- `deploy.yml` builds on every push to `main` and force-pushes `_site` to `gh-pages`.
- GitHub Pages serves `gh-pages` on the custom domain `kellner.science` (`CNAME` in the repo root, copied into the build via `keep_files`).
- `update-citations.yml` refreshes `_data/citations.yml` from Google Scholar on a schedule and commits it.

## Gem version pins

`Gemfile` pins every `al-*` gem to an exact version in `group :al_folio_plugins`, and `_config.yml` lists the same gems under `plugins:`. Keep both lists in sync. The docs for the upstream starter live in `docs/`.
