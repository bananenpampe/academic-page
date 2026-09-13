# kellner.science

Source of my personal academic webpage, [kellner.science](https://kellner.science), built with the [al-folio](https://github.com/alshedivat/al-folio) v1 Jekyll starter and hosted on GitHub Pages.

## Editing content

| What                    | Where                                                                           |
| ----------------------- | ------------------------------------------------------------------------------- |
| Landing page text       | [`_pages/about.md`](_pages/about.md)                                            |
| News items              | [`_news/`](_news/) (one Markdown file per item)                                 |
| Research projects       | [`_projects/`](_projects/) (one Markdown file per project)                      |
| Publications            | [`_bibliography/papers.bib`](_bibliography/papers.bib)                          |
| CV (web version)        | [`_data/cv.yml`](_data/cv.yml); PDF in [`assets/pdf/CV.pdf`](assets/pdf/CV.pdf) |
| Social links            | [`_data/socials.yml`](_data/socials.yml)                                        |
| Site-wide settings      | [`_config.yml`](_config.yml)                                                    |
| Banner / profile images | [`assets/img/`](assets/img/)                                                    |

Comments on project pages are powered by [giscus](https://giscus.app) (GitHub Discussions). Add `giscus_comments: true` to the front matter of any page or post to enable them there.

## Local development

```bash
bundle install                 # Ruby >= 3.x, see Gemfile.lock for the bundler version
bundle exec jekyll serve       # http://localhost:4000/
npm ci && npm run lint:prettier
```

ImageMagick must be on `PATH` for responsive images (`brew install imagemagick`). Alternatively use `docker compose up` (see [`docs/INSTALL.md`](docs/INSTALL.md)).

## Deployment

Every push to `main` runs [`deploy.yml`](.github/workflows/deploy.yml), which builds the site and pushes it to the `gh-pages` branch. GitHub Pages serves that branch on the custom domain in [`CNAME`](CNAME).

## Upstream documentation

The al-folio guides live in [`docs/`](docs/). Layouts, includes and styles come from the `al_folio_core` gem and its siblings, pinned in the [`Gemfile`](Gemfile). The only locally overridden theme file is [`_layouts/about.liquid`](_layouts/about.liquid) (adds the header banner); run `bundle exec al-folio upgrade overrides audit` after bumping the gem versions.

## License

The site template is MIT licensed (see [`LICENSE`](LICENSE)). Content is © Matthias Kellner.
