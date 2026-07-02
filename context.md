# Project Context: NSW Child E Cohort Website

## Background
This repo builds the public website for the **NSW Child E Cohort Program**, based in the UNSW School of Population Health and led by Associate Professor Kathleen Falster.

The design/UX reference point is [spcanelon/silvia](https://github.com/spcanelon/silvia) / [silviacanelon.com](https://silviacanelon.com/) — a personal academic site built with **Quarto**, inspired by the Hugo Apéro theme. Navbar sections are, in order: **Mission, People, Projects, Publications, Media**.

## Goals
- Give the Program a public, professional website introducing its mission, team, research projects, publications, and media coverage.
- Keep day-to-day maintenance easy for non-developer lab members: content lives in plain markdown/YAML files (`.qmd`, `.bib`), not code.
- Match the clean academic look of the reference site, but with the Program's own navy/slate/cornflower-blue branding and a "children holding hands" logo motif.
- Run for free, deployed straight from this GitHub repo with no separate hosting to manage.

## Workflow
- **Auto-deploy every change**: each edit is committed and pushed to `main` immediately (no batching, no separate "push it" request needed) — see [[feedback_auto_deploy]] in memory.
- **Build pipeline**: push to `main` → `.github/workflows/publish.yml` renders the Quarto site and publishes `_site/` to the `gh-pages` branch → GitHub Pages serves it live.
- **No local Quarto CLI** on this machine, so changes can't be previewed with `quarto preview` before pushing. Verification happens by re-fetching the live URL (and/or the `gh-pages` branch content) after the Actions run completes, ~30–45 seconds after pushing.
- **This file** (`context.md`) is the running log of decisions and changes — update its Change log whenever a meaningful change is made, so a fresh session (or a fresh Claude conversation) has the full history without re-deriving it.

## Decisions
| Decision | Choice | Why |
|---|---|---|
| Framework | **Quarto** | Matches the reference site; markdown/YAML-based so lab members can add people/publications/projects without touching code. |
| Hosting | **GitHub Pages** | Free, deploys straight from this repo via GitHub Actions. |
| Initial content | **Placeholders**, being replaced incrementally | Structure and styling built first; Mission, Projects, and Dr Falster's People entry now have real content (see Change log) — team bios/photos for other members, real publications, and media items are still pending. |
| Branding | **Navy / slate / cornflower blue** | Palette: `#00205B` navy, `#7A8B99` slate, `#6495ED` cornflower blue accent (replaced an initial gold `#D4AF37` accent per user request to remove all yellow-toned color), applied to the reference site's clean academic layout. |
| Logo | **Children holding hands, gradient blues** | Six (hero) / three (navbar, favicon) child silhouettes of ascending height, holding hands, colored light-to-navy blue — inspired by a reference embroidered-patch image, using only the site's blue palette. |
| Page layout | **Follows silviacanelon.com** | Navbar: icon-only logo on the left, section links pushed right via `right:` group in `_quarto.yml`. Homepage: contained-width, light-background intro (heading/subtitle/paragraph left, large logo right) instead of a full-bleed banner. |

## Site structure
```
_quarto.yml              site config: navbar order, theme, output
index.qmd                Home: contained intro (text + large logo) + highlight cards linking to the 5 sections
mission.qmd              Program mission/aims (real content)
projects.qmd             Research project listing (real content, sourced from Dr Falster's UNSW profile)
people.qmd               Team grid (Dr Falster's entry is real; other roles are placeholders)
publications.qmd         Publication list, rendered from references.bib (placeholder entries)
media.qmd                News/media mentions (placeholder entries)
styles.scss              Custom SCSS theme (navy/slate/cornflower-blue palette)
context.md               This file — project background, decisions, workflow, and change log
assets/images/           logo (hero/navbar/favicon variants), section icons, avatar photos/placeholders
.github/workflows/publish.yml   GitHub Actions: render + deploy to gh-pages
references.bib           placeholder BibTeX entries for Publications page
```

## Known follow-ups (things a human needs to do)
1. **Install the Quarto CLI** locally (https://quarto.org/docs/get-started/) to run `quarto preview`/`quarto render` on this machine — it wasn't detected during this build. CI renders independently of this.
2. **Replace remaining placeholder content**: investigator/staff/student bios and photos, actual publications (`references.bib`), and media/news items.
3. **Optimize `assets/images/kathleen-falster.jpg`**: it's the original ~1MB, 2977×3407px file pulled from her UNSW profile — no image-resizing tool was available in this environment to shrink it. Browsers still display it fine (CSS crops it to a 96px circle), but resizing/compressing it would reduce page load size.

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
- 2026-07-02: Logo redesigned again per a reference image (embroidered patch of colorful children holding hands): now six child silhouettes of ascending height holding hands, in a light-to-navy blue gradient (`#b3cdf5` → `#8fb3ee` → `#6495ed` → `#4472c4` → `#23408a` → `#00205b` — endpoints reuse the existing accent/navy brand colors). Full 6-figure version used in the homepage hero (`logo-mark.svg`); a simplified 3-figure version (light/accent/navy) used for the navbar (`logo.svg`) and favicon at small size.
- 2026-07-02: Added a small flat icon above each homepage highlight card's title (`assets/images/icon-mission.svg`, `icon-people.svg`, `icon-projects.svg`, `icon-publications.svg`, `icon-media.svg`) — compass, linked figures, bar chart, open book, speech bubble respectively — in the site's navy/slate/accent palette.
- 2026-07-02: People page's Dr Falster entry replaced with her real profile (title, bio, research interests, contact/profile links) sourced from https://www.unsw.edu.au/staff/kathleen-falster. Other team entries (investigators, staff, students) remain placeholders pending real names/bios.
- 2026-07-02: Downloaded Dr Falster's real profile photo from her UNSW staff page (`assets/images/kathleen-falster.jpg`) and swapped it in for the placeholder avatar on the People page.
- 2026-07-02: Fixed the homepage highlight cards rendering `###` as literal text instead of a heading — the icon image and the `### [Title]` line had no blank line between them, so Pandoc treated it as a paragraph continuation rather than an ATX heading. Added blank lines around each heading/paragraph in `index.qmd`, and increased the card title size/weight (`font-size: 1.4rem; font-weight: 700;`) in `styles.scss`.
- 2026-07-02: Fixed profile photos not actually rendering circular on the People page — markdown `![]()` images get auto-wrapped by Pandoc in `<p class="img-fluid">`, and relying on `.profile-card img{width;height;border-radius}` alone proved unreliable in the flex layout. Switched to a raw-HTML `<div class="avatar">` wrapper (fixed 96×96px, `overflow:hidden`, `border-radius:50%`) with the `<img>` filling it via `object-fit:cover` — a more robust pattern for circular avatars. Applied to Dr Falster's photo and all placeholder avatars in `people.qmd`.
- 2026-07-02: Restructured this file into Background / Goals / Workflow / Decisions / Site structure / Known follow-ups / Change log sections for easier scanning.
- 2026-07-02: Added the Program's first real publication to `references.bib`: Falster et al. (2025), "Re-envisaging child protection contacts as an early prevention opportunity to support child development and well-being: an Australian data linkage study," *Journal of Epidemiology and Community Health*, 79(7):e223006, doi:10.1136/jech-2024-223006 (https://pmc.ncbi.nlm.nih.gov/articles/PMC12322469/). Publications page auto-includes it via `nocite: "@*"`; the 3 placeholder entries remain alongside it pending cleanup.
