# Template: mikkel-template

- **Type:** CV
- **Engine:** lualatex
- **Page limit:** 1 page
- **Fonts:** CormorantGaramond + charter (serif; both standard TeX-distribution font packages, no bundled files, must have a full TeX distribution installed)
- **Class/packages:** `article` (letterpaper, 10pt). Packages: `fullpage`, `titlesec`, `enumitem`, `hyperref` (hidelinks), `fancyhdr`, `fontawesome5`, `multicol`, `bookmark`, `lastpage`, `ragged2e`, `CormorantGaramond`, `charter`, `xcolor`. All standard — no custom `.cls`.

## Compile command

    cd cv && lualatex -interaction=nonstopmode cv_<company>.tex

## Style rules

- Colors: `accentTitle`/`accentText` = `#0e6e55` (dark green) for the name, section headings, and small-caps text; `accentLine` = `#a16f0b` (gold/brown) for horizontal rules
- Name/title block: centered, `\Huge\scshape` name in accentTitle, bracketed above and below by an accentLine `\hrule`, with a small headline/subtitle line and a `\faIdBadge`-prefixed contact line (name, phone, email, LinkedIn — each with a FontAwesome icon) between the rules
- Section headings (`\section{}`): small-caps, bold, accentText color, with an accentLine `\titlerule` underneath — no numbering
- Job/education entries: `\headingBf{Company | Department}{Date range}` (bold, dates right-aligned via `\hfill`) followed by `\headingIt{Title}{}` (italic role) on the next line, then a `resume_list` itemize block with tight spacing (`itemsep=-2px, parsep=1pt`)
- Skills section uses a 2-column `multicols` block with `\item[\textbf{Category:}] list` pairs — keep categories short so they don't wrap awkwardly in the narrow columns
- Tight margins (`\addtolength` overrides on `oddsidemargin`, `textwidth`, `topmargin`, `textheight`) are intentional, they make the 1-page format work. Do not loosen them; cut content instead
- Readability spacing (set 2026-10-13 after the original felt cramped): `\linespread{1.08}`, `resume_list` `itemsep=2pt`, skills list `itemsep=1pt`, `\vspace{2pt}` above section headings, `\multicolsep` 3pt. Do not shrink these back to make content fit - cut content instead
- Bullets use `--` (`\renewcommand\labelitemi{--}`), not the default disc
- Section order: Technical Competencies → Recent Experience → Education → Extracurricular Activities. **No Summary section** (removed 2026-10-13) - the two-line headline does the role targeting. Preserve this order
- ATS glyph-to-unicode mapping is already wired in (`\input{glyphtounicode}`, `\pdfgentounicode=1`) — do not remove

## Known pitfalls

- **Already fixed in `template.tex`, do not remove:** `\multicolsep` was originally `-3.0pt`, which let the taller skills column run into the next section heading. Now `3.0pt`. Still keep the two skills columns about the same height
- **Already fixed in `template.tex`, do not remove:** `\documentTitle` ends its title with `\par` so a two-line headline gets proper `\Huge` line spacing. Do not add `\vspace{5pt}` after the `\\` line break in the headline (older CVs did; it now doubles the gap)
- An entry with no bullet list under it (e.g. a bachelor degree with only title lines) lets the next `\section{}` heading overlap it: add `\vspace{6pt}` after that entry
- A `resume_list` placed directly under a `\section{}` (e.g. Extracurricular) touches the section rule because the list starts with `\vspace{-7pt}`: add `\vspace{8pt}` between the section and the list
- A "Font \TU/lmr ... not loadable" error in the log is harmless (fontspec loads Latin Modern before XCharter replaces it); install `texlive-fontsrecommended` to silence it

- Requires `lualatex` or `xelatex` — `fontawesome5` fails on `pdflatex` under modern MiKTeX with font-expansion errors (matches the project's existing CV compile guidance)
- **Already fixed in `template.tex`, do not remove:** `\input{glyphtounicode}` uses the pdfTeX-only primitive `\pdfglyphtounicode`, which is undefined under LuaLaTeX and throws "Undefined control sequence" ~100 times. Fixed by loading `\usepackage{luatex85}` (guarded by `\ifluatex`) before the input, which restores pdfTeX-compatible primitives.
- **Already fixed in `template.tex`, do not remove:** the original `\usepackage{charter}` (classic NFSS/PostScript font package) silently falls back to Latin Modern under LuaLaTeX/XeLaTeX, because `CormorantGaramond` pulls in `fontspec` and switches the document to Unicode (`TU`) font encoding, which `charter` doesn't define shapes for — body text renders in Latin Modern instead of Charter with no error, only a font-shape warning. Fixed by using `\ifpdftex` (from `iftex`) to keep `\usepackage{charter}` under pdflatex but load the OpenType-native `\setmainfont{XCharter}` via fontspec under lualatex/xelatex.
- `\numberedPages`/`\documentFooter` (footer with page numbers via `lastpage`) are present but commented out in the original; if activated, the doc must be compiled **twice** for `\pageref{LastPage}` to resolve
- This is a genuinely tight 1-page layout — the margins are already pushed to their limits (`\addtolength{\textwidth}{1.19in}` etc.). If content overflows to a second page, the fix is cutting bullets/summary length, not loosening spacing further
- The skills `itemize` block uses 2 columns split by `\columnbreak` — balance by rendered line count, not item count (a category that wraps to 3 lines counts as 3)
