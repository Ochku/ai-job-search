# Template: steff-ats

> **Retired 2026-10-21** - no longer produced for new applications; `steff-modern` is the only CV format. Kept for the record of earlier applications.

- **Type:** CV
- **Engine:** lualatex
- **Page limit:** 1 page
- **Fonts:** CormorantGaramond (headings) + XCharter (body), both standard TeX Live font packages (`texlive-fontsextra`), no bundled files
- **Class/packages:** `article` (a4paper, 10pt). Packages: `iftex`, `luatex85`, `fullpage`, `titlesec`, `enumitem`, `hyperref` (hidelinks), `fancyhdr`, `ragged2e`, `CormorantGaramond`, `xcolor`. No icon fonts (`fontawesome5` deliberately dropped). No custom `.cls`.

## Compile command

    cd cv && lualatex -interaction=nonstopmode cv_<company>.tex

## Style rules

- Created 2026-10-13 from `mikkel-template` after an ATS/recruiter review. Same colors and fonts, but built to be read by both an ATS and a recruiter scanning for seconds
- Colors: `accentTitle`/`accentText` = `#0e6e55` (dark green) for the name, section headings and sub-group labels; `accentLine` = `#a16f0b` (gold) for rules
- **Header** (`\documentHeader{name}{contact}{location}`): name in `\Huge\scshape`, then a plain-text contact line (phone, email, LinkedIn separated by `\sep`, a centered dot), then a location line that answers relocation, work rights and availability up front (e.g. "Horst, Netherlands · relocating to Copenhagen, Denmark · EU citizen, no work permit needed · 1 month's notice"). **No headline/tagline and no icons** - icon-font names (ID-BADGE, Envelope, LINKEDIN) leak into the ATS text layer
- **Section order:** Profile → Technical Skills → Experience → Education → Speaking → Languages
- **Profile:** 2-3 lines, tailored to the posting: who you are in one clause, the strongest proof point, the background. Can use the posting's job title wording
- **Technical Skills:** single column, one bold category per line (no `multicols`, so extraction order is always correct). Include the searchable tools the bullets mention (Git/CI, pytest, Dataform, n8n...) so ATS keyword matching finds them, but only tools that set the candidate apart - no standard libraries (pandas, Pydantic), test/lint/packaging tools (pytest, ruff, mypy, uv), practices or Power BI; see `05-cv-templates.md`
- **Entries** (`\entry{Company[, Department]}{dates}{title(s)}`): company bold with dates right-aligned, title italic on the next line - the same pattern for every job and degree. A promotion at one employer goes on one italic line as "Data Scientist (promoted from Junior Data Scientist, Jun 2026)" (no local level terms like "Medior")
- **Sub-groups** (`\subgroup{...}`): split a long employer section into themed groups (e.g. "AI Customer Service agents (Claude, Zendesk)" / "Automation & data") so it scans quickly
- **Bullets:** real bullet character (`\textbullet`), result first, **no bold inside bullets** (not even numbers), one tense per role (past tense; a noun-phrase lead like "Sole engineer behind..." is fine), 1-3 lines each. Translate jargon once ("each request type earns more autonomy only after passing evaluations", not "autonomy ladder")
- Older / weaker roles get one tight line; spend the space on the most recent role
- **Speaking** and **Languages** are their own one-line sections (languages joined with `\sep`)

## Known pitfalls

- Never start a bullet's text with `[` - `\item [text]` is parsed as a custom label and the text disappears into the margin. Template placeholders therefore read `\item PLACEHOLDER - ...`
- Use `\sep` between items, never a literal ` · `: `\sep` uses `\unskip`/`\ignorespaces`, so line breaks in the source don't add uneven spacing around the dot. End header lines with `%` for the same reason
- Latin Modern "Font \TU/lmr ... not loadable" error in the log is harmless (fontspec loads it before XCharter replaces it); install `texlive-fontsrecommended` to silence it
- Do not shrink `\linespread{1.08}`, list `itemsep` or section spacing to make content fit - those were set because tighter values looked cramped. Cut or reword instead: a bullet ending in a single orphaned word on its last line is the cheapest line to win back
- Check the text layer after every compile (`pdftotext -layout`): the header must read as plain name / phone / email / LinkedIn text with no icon names
