# Project Context: NSW Child E Cohort Website

## Background
This repo builds the public website for the **NSW Child E Cohort Program**, based in the UNSW School of Population Health and led by Dr Kathleen Falster.

The design/UX reference point is [spcanelon/silvia](https://github.com/spcanelon/silvia) — a personal academic site built with **Quarto**, inspired by the Hugo Apéro theme. Navbar sections must be, in order: **Projects, People, Mission, Publications, Media**.

## Decisions
| Decision | Choice | Why |
|---|---|---|
| Framework | **Quarto** | Matches the reference site; markdown/YAML-based so lab members can add people/publications/projects without touching code. |
| Hosting | **GitHub Pages** | Free, deploys straight from this repo via GitHub Actions. |
| Initial content | **Placeholders** | Structure and styling built now; team bios, real publications, project descriptions, and media items to be swapped in later. |
| Branding | **UNSW branding** | UNSW Yellow/Black core palette adapted into the reference site's clean academic layout, rather than reusing the reference site's own colors. |

## Site structure
```
_quarto.yml              site config: navbar order, theme, output
index.qmd                Home: hero + highlight cards linking to the 5 sections
mission.qmd              Program mission/aims/background
projects.qmd             Research project listing (placeholder cards)
people.qmd               Team grid (lead, investigators, staff/students)
publications.qmd         Publication list, rendered from references.bib
media.qmd                News/media mentions
styles.scss              Custom SCSS theme (UNSW colors)
assets/images/           logo, favicon, hero image, photo placeholders
.github/workflows/publish.yml   GitHub Actions: render + deploy to gh-pages
references.bib           placeholder BibTeX entries for Publications page
```

## Known follow-ups (things a human needs to do)
1. **Verify UNSW brand hex codes** against the official UNSW brand toolkit before public launch — this build uses commonly published UNSW Yellow (`#FFD100`) / Black as a reasonable placeholder, not a fetched brand PDF.
2. **Point GitHub Pages at the `gh-pages` branch** in the repo's Settings → Pages (one-time manual step after the first Actions run creates that branch).
3. **Install the Quarto CLI** locally (https://quarto.org/docs/get-started/) to run `quarto preview`/`quarto render` on this machine — it wasn't detected during this build. CI renders independently of this.
4. **Replace placeholder content**: team bios/photos, real project descriptions, actual publications (`references.bib`), and media/news items.
