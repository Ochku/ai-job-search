# Template: steff-modern

- **Type:** CV
- **Engine:** lualatex
- **Page limit:** 1 page
- **Fonts:** Carlito (metric-compatible with Calibri), standard TeX Live font (`texlive-fontsextra`), no bundled files
- **Class/packages:** `article` (a4paper, 10pt). Packages: `geometry`, `fontspec`, `xcolor`, `titlesec`, `enumitem`, `array`, `hyperref`. No icon fonts. No custom `.cls`.

## Compile command

    cd cv && lualatex -interaction=nonstopmode cv_<company>.tex

## Style rules

- Created 2026-10-13 as a LaTeX recreation of the user's reference design (`~/Downloads/Steff_Vleeshouwers_CV.pdf`, originally made with ReportLab). Since 2026-10-21 the only CV template (`steff-ats` retired; see `05-cv-templates.md`)
- Output file: `cv/cv_<company>.tex` - the only CV format since 2026-10-21
- Colors: name near-black `#1F1F1F`; headline and section headings blue `#1F4E79`; department/institution after the em dash slate `#4A5D73`; dates, title lines, contact line and sub-group labels grey `#6B7280`; section rules light grey `#BFC6D0`
- **Header** (`\cvheader{name}{headline}{contact}`): large bold name, a one-line blue **headline**, then two grey lines separated by ` | ` (`\sep`): phone (use `~` between digit groups so it never breaks), email, LinkedIn; then (after `\newline`) relocation note, work rights, notice period
- **Section order:** Profile → Experience → Skills → Education → Speaking. Section headings are uppercase blue with a thin light-grey rule
- **Entries:** `\entry{Company}{Department or title}{dates}` renders "**Company** — Department" with grey dates right-aligned. For education the degree goes first: `\entry{MSc ...}{University}{dates}`. A promotion goes on a grey `\roles{...}` line as "Data Scientist (promoted from Junior Data Scientist, Jun 2026)"
- **Sub-groups:** `\subgroup{...}` in grey italics splits a long employer section into themes
- **Bullets:** result first, key number early in the bullet; **no bold inside bullets** (user decision 2026-10-19); one tense per role
- **Skills:** two-column table (bold category, ragged-right values), one line per category where possible; Languages is the last row
- **Speaking:** one line, "Event, City — Talk: topic" with the date right-aligned

## Known pitfalls

- `\MakeUppercase` must sit in the `\titleformat` before-code argument (`{\MakeUppercase}`), not in the format argument: in the format it also uppercases the rule's color name (`RULECOLOR`, undefined → black rule). And never put a `%` comment on the `\titleformat` line before the `[after-code]`, or the rule is silently commented out
- Never start a bullet with `[` (`\item [x]` becomes a label), and never start a table row with `[` (after `\\` it is read as a spacing argument and breaks the row). Placeholders therefore read `PLACEHOLDER - ...` / `CATEGORY 1`
- Each of the two contact lines must fit on one line; if the work-rights line wraps, shorten it rather than letting it break mid-phrase. The phone number uses `~` so it never breaks
- The skills value column must be `>{\raggedright\arraybackslash}p{...}`: a justified `p` column stretches word spacing on wrapped rows
- Latin Modern "Font \TU/lmr ... not loadable" error in the log is harmless (fontspec loads it before Carlito replaces it); install `texlive-fontsrecommended` to silence it
- Don't fix overflow by shrinking `\linespread{1.08}`, margins or section spacing; reword bullets that end in one orphaned word, then cut by relevance
