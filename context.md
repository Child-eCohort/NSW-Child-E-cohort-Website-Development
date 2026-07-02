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
| Branding | **Navy / slate / gold** | User-specified palette (`#00205B` navy, `#7A8B99` slate, `#D4AF37` gold), replacing the initial UNSW yellow/black placeholder, applied to the reference site's clean academic layout. |

## Site structure
```
_quarto.yml              site config: navbar order, theme, output
index.qmd                Home: hero + highlight cards linking to the 5 sections
mission.qmd              Program mission/aims/background
projects.qmd             Research project listing (placeholder cards)
people.qmd               Team grid (lead, investigators, staff/students)
publications.qmd         Publication list, rendered from references.bib
media.qmd                News/media mentions
styles.scss              Custom SCSS theme (navy/slate/gold colors)
assets/images/           logo, favicon, hero image, photo placeholders
.github/workflows/publish.yml   GitHub Actions: render + deploy to gh-pages
references.bib           placeholder BibTeX entries for Publications page
```

## Known follow-ups (things a human needs to do)
1. **Install the Quarto CLI** locally (https://quarto.org/docs/get-started/) to run `quarto preview`/`quarto render` on this machine — it wasn't detected during this build. CI renders independently of this.
2. **Replace remaining placeholder content**: team bios/photos, actual publications (`references.bib`), and media/news items. Projects (`projects.qmd`) now has real content — see change log below.

## Change log
- 2026-07-02: Repo made public (was private) so GitHub Pages could serve it on the org's free plan; site deployed live at https://child-ecohort.github.io/NSW-Child-E-cohort-Website-Development/.
- 2026-07-02: Navbar/home page section order changed to Mission, People, Projects, Publications, Media.
- 2026-07-02: Color palette changed from UNSW yellow/black placeholder to navy (`#00205B`) / slate (`#7A8B99`) / gold (`#D4AF37`).
- 2026-07-02: `projects.qmd` replaced with real project content sourced from Dr Falster's UNSW staff profile (Research Activities tab: https://www.unsw.edu.au/staff/kathleen-falster) — 14 projects across 4 categories (multi-jurisdictional grant-funded, NSW-specific grant-funded, multi-jurisdictional research using NSW Child E-Cohort data, prior NHMRC Early Career Fellowship research), each with a 1–2 sentence description, funding details, and external collaborators where mentioned on the profile.
