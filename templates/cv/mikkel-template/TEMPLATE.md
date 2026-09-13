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
- Extremely tight margins/spacing (`\addtolength` overrides on `oddsidemargin`, `textwidth`, `topmargin`, `textheight`) — this is intentional, it's what makes the 1-page format work. Do not loosen these to fit more content; cut content instead
- Bullets use `--` (`\renewcommand\labelitemi{--}`), not the default disc
- Section order: Summary → Technical Competencies → Recent Experience → Education → Extracurricular Activities. Preserve this order
- ATS glyph-to-unicode mapping is already wired in (`\input{glyphtounicode}`, `\pdfgentounicode=1`) — do not remove

## Known pitfalls

- Requires `lualatex` or `xelatex` — `fontawesome5` fails on `pdflatex` under modern MiKTeX with font-expansion errors (matches the project's existing CV compile guidance)
- **Already fixed in `template.tex`, do not remove:** `\input{glyphtounicode}` uses the pdfTeX-only primitive `\pdfglyphtounicode`, which is undefined under LuaLaTeX and throws "Undefined control sequence" ~100 times. Fixed by loading `\usepackage{luatex85}` (guarded by `\ifluatex`) before the input, which restores pdfTeX-compatible primitives.
- **Already fixed in `template.tex`, do not remove:** the original `\usepackage{charter}` (classic NFSS/PostScript font package) silently falls back to Latin Modern under LuaLaTeX/XeLaTeX, because `CormorantGaramond` pulls in `fontspec` and switches the document to Unicode (`TU`) font encoding, which `charter` doesn't define shapes for — body text renders in Latin Modern instead of Charter with no error, only a font-shape warning. Fixed by using `\ifpdftex` (from `iftex`) to keep `\usepackage{charter}` under pdflatex but load the OpenType-native `\setmainfont{XCharter}` via fontspec under lualatex/xelatex.
- `\numberedPages`/`\documentFooter` (footer with page numbers via `lastpage`) are present but commented out in the original; if activated, the doc must be compiled **twice** for `\pageref{LastPage}` to resolve
- This is a genuinely tight 1-page layout — the margins are already pushed to their limits (`\addtolength{\textwidth}{1.19in}` etc.). If content overflows to a second page, the fix is cutting bullets/summary length, not loosening spacing further
- The skills `itemize` block relies on exactly 3 items per column (2 columns via `\columnbreak`) for visual balance — adding/removing categories should keep the two columns roughly even
