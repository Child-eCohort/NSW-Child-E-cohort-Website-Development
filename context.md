# Project Context: NSW Child E Cohort Website

## Background
This repo builds the public website for the **NSW Child E Cohort Program**, based in the UNSW School of Population Health and led by Dr Kathleen Falster.

The design/UX reference point is [spcanelon/silvia](https://github.com/spcanelon/silvia) / [silviacanelon.com](https://silviacanelon.com/) — a personal academic site built with **Quarto**, inspired by the Hugo Apéro theme. Navbar sections are, in order: **Mission, People, Projects, Publications, Media**.

## Decisions
| Decision | Choice | Why |
|---|---|---|
| Framework | **Quarto** | Matches the reference site; markdown/YAML-based so lab members can add people/publications/projects without touching code. |
| Hosting | **GitHub Pages** | Free, deploys straight from this repo via GitHub Actions. |
| Initial content | **Placeholders** | Structure and styling built now; team bios, real publications, project descriptions, and media items to be swapped in later. |
| Branding | **Navy / slate / cornflower blue** | Palette: `#00205B` navy, `#7A8B99` slate, `#6495ED` cornflower blue accent (replaced an initial gold `#D4AF37` accent per user request to remove all yellow-toned color), applied to the reference site's clean academic layout. |

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
- 2026-07-02: Projects page trimmed — removed the "Prior NHMRC Early Career Fellowship research" section and dollar figures from all funding lines (funder/grant name kept, amount dropped); Projects intro line shortened to drop the profile-link sentence.
- 2026-07-02: Mission page ("About the Program"/"Our aims") rewritten with the Program's real mission statement, adapted from a reference statement but reframed around overall early-life development/wellbeing rather than child protection specifically (child-protection-specific data sector and outcome sentences dropped).
- 2026-07-02: New logo mark designed (`assets/images/logo-mark.svg`): four linked data points tracing an upward path (navy → navy → slate → gold), symbolising the cohort's data linkage tracing children's journey from early life to better outcomes. Applied to navbar (`logo.svg`), favicon, and featured large in the homepage hero banner.
- 2026-07-02: Removed gold/yellow-toned accent entirely per user request. Replaced with cornflower blue `#6495ED` (a lighter tint within the navy family) across `styles.scss` (renamed `$gold` → `$accent`) and the logo/favicon/logo-mark SVGs — the mark's end node is now blue instead of gold.
- 2026-07-02: Fixed inconsistent card border colors (was cycling accent/navy/slate per card on the homepage only) — all `.info-card` boxes now use one consistent border treatment (slate side/bottom border, accent top border) on every page. Removed the now-unused `.home-highlights` class from `index.qmd`.
- 2026-07-02: Fixed double-underlined card headings (browser's default link underline stacking with the custom colored `border-bottom`) by disabling the default `<a>` text-decoration inside `.info-card h3` — only the single colored underline remains.
- 2026-07-02: Replaced the linked-data-path logo mark with a new design: three growing silhouettes (no facial features, just shape) from infant (accent blue, smallest) to child (slate, medium) to teenager (navy, tallest), representing the Program's early-life development focus. Applied to `logo-mark.svg` (hero), `logo.svg` (navbar), and `favicon.svg`.
- 2026-07-02: Restyled the site to follow [silviacanelon.com](https://silviacanelon.com/)'s layout, keeping our navy/slate/cornflower-blue palette: navbar section links moved from the `left:` group to the `right:` group in `_quarto.yml` so they sit as a bar on the top right (logo stays top left, matching the reference); homepage hero replaced the full-bleed navy banner with a contained, light-background intro (short heading/subtitle/paragraph on the left, large logo mark on the right) and dropped `page-layout: full` so the page uses Quarto's standard contained width. Also fixed a pre-existing bug found along the way: `logo.svg` had baked-in "NSW Child E Cohort" text that duplicated the navbar's separate auto-generated site title — made `logo.svg` icon-only.
