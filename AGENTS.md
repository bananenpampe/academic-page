# Agent Guidelines for kellner.science

This repository is **Matthias Kellner's personal website**, created from the [al-folio](https://github.com/alshedivat/al-folio) v1.x starter. It is _not_ the upstream starter repo, so the upstream rule "never add `_layouts/`, `_includes/` or `_sass/` here" does not apply; local overrides of gem-owned files are allowed when config or content cannot express a change.

## Where things live

| Change                                                | Edit                                                                                |
| ----------------------------------------------------- | ----------------------------------------------------------------------------------- |
| Landing page text, profile image, banner              | `_pages/about.md` (banner file name in `banner:`; images in `assets/img/`)          |
| News items                                            | `_news/YYYY-MM-DD-slug.md` (`inline: true` for one-liners)                          |
| Research projects                                     | `_projects/*.md` (`giscus_comments: true` enables the comment section)              |
| Publications                                          | `_bibliography/papers.bib` (`selected={true}` shows a paper on the landing page)    |
| CV                                                    | `_data/cv.yml` (web version) and `assets/pdf/CV.pdf` (download)                     |
| Socials                                               | `_data/socials.yml`                                                                 |
| Site settings, feature flags, giscus IDs, plugin list | `_config.yml` (plugins must also be pinned in the `Gemfile`)                        |
| Theme runtime (layouts, includes, Sass, tags)         | the owning `al_*` gem (see `docs/BOUNDARIES.md`); override locally only when needed |

Local overrides in use: `_layouts/about.liquid` (header banner + "try my work" card styles). Acknowledge new overrides with `bundle exec al-folio upgrade overrides accept <path>` and commit `.al-folio-overrides.yml`.

## Things that fail silently

1. A feature renders only when its gem is in **both** the `Gemfile` and `_config.yml` `plugins:`, its flag is on, and the page opts in.
2. `baseurl` must stay **empty** (custom domain served from the root). `url` is `https://kellner.science`, and `CNAME` must stay in the repo root.
3. News items dated in the future only render because `future: true` is set in `_config.yml`.

## Validate before pushing

```bash
bundle install
npm ci
npm run lint:prettier            # npx prettier . --write fixes formatting
bundle exec jekyll build         # output in _site/
bundle exec al-folio upgrade audit --no-fail
bundle exec al-folio upgrade overrides audit
```

Pushing to `main` deploys via `.github/workflows/deploy.yml` (builds to the `gh-pages` branch). The upstream guides are in `docs/`.
