# NSW-Child-E-cohort-Website-Development
Website for the NSW Child E Cohort Program, UNSW School of Population Health, led by Dr Kathleen Falster.

Design inspired by [spcanelon/silvia](https://github.com/spcanelon/silvia). Navbar: Projects, People, Mission, Publications, Media.

See [context.md](context.md) for the full project background and build decisions.

## Local development

This site is built with [Quarto](https://quarto.org). Install the Quarto CLI, then from the repo root:

```sh
quarto preview   # live preview at http://localhost:<port>
quarto render    # build the static site into _site/
```

## Content

- **Projects** — `projects.qmd`
- **People** — `people.qmd`
- **Mission** — `mission.qmd`
- **Publications** — `publications.qmd`, backed by `references.bib` (add a BibTeX entry to add a paper)
- **Media** — `media.qmd`

All current content is placeholder text — see the "Known follow-ups" list in [context.md](context.md) for what needs replacing before launch (real bios/photos, project descriptions, publications, media items, and verified UNSW brand colors).

## Deployment

Pushing to `main` triggers `.github/workflows/publish.yml`, which renders the site with Quarto and publishes `_site/` to the `gh-pages` branch. After the first successful run, point the repo's **Settings → Pages** at the `gh-pages` branch (one-time setup).