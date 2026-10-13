# CV Templates and Tailoring Guide

<!-- BEGIN ACTIVE-TEMPLATE (managed by /add-template - do not edit by hand) -->
> **Active template override: `steff-ats`**
>
> A custom template is active. Where this block conflicts with the stock guidance below, this block wins. Structural advice below (tailoring, page-budget, cutting rules) still applies.
>
> - **Template skeleton:** `templates/cv/steff-ats/template.tex` — use this as the structural reference instead of the stock template
> - **Manifest:** `templates/cv/steff-ats/TEMPLATE.md` — read this for style rules and known pitfalls before drafting
> - **Compile with:** `lualatex` (not the engine named in the stock guidance below)
> - **Fonts:** CormorantGaramond + XCharter, standard TeX Live font packages (no bundled files, no icon fonts)
> - **Page limit:** exactly 1 page
> - **Output file:** unchanged (`cv/cv_<company>.tex`); no extra class/font files need to be copied to the output directory
<!-- END ACTIVE-TEMPLATE -->

> **Always produce two versions of every CV (user decision 2026-10-13).** Same content, two layouts:
> 1. `cv/cv_<company>.tex` with the active template **`steff-ats`** (serif, plain single column, no headline - built for ATS parsing)
> 2. `cv/cv_<company>_modern.tex` with **`steff-modern`** (`templates/cv/steff-modern/` - sans-serif Carlito, blue headline under the name, bold key numbers, skills table after Experience)
>
> Write the content once, then port it into the second layout. Compile, visually check and run the ATS text-layer checks on **both** PDFs; both must be exactly 1 page. Present both to the user. The modern version keeps a one-line headline; the ATS version does not.

<!-- SETUP: Profile statements and section ordering are personalized by running /setup -->

## Template: LaTeX moderncv (Banking Style) - legacy stock template

> **Only applies when no ACTIVE-TEMPLATE override is set above.** With a custom template active (currently the 1-page `steff-ats`), skip this section's structure, color and `\cventry` advice; the tailoring, cutting and ATS guidance further down still applies.

All CVs use the moderncv LaTeX package with the "banking" style and "blue" color scheme.

**Output file:** `cv/cv_<company>.tex`
**Compile with:** **lualatex** on MiKTeX/TeX Live. pdflatex often fails on modern MiKTeX installs with `fontawesome5` font-expansion errors; lualatex handles the same sources cleanly.
**Master reference:** `cv/main_example.tex` (comprehensive CV with all competencies, experience, and achievements - use as source when building targeted CVs)

### Compile command

```bash
cd cv && lualatex -interaction=nonstopmode cv_<company>.tex
```

Expected output: `Output written on cv_<company>.pdf (N pages, ...)` where N is the active template's page limit (1 for `steff-ats`). Any other page count is a failure that must be fixed before presenting to the user.

## Document Structure

```latex
\documentclass[11pt,a4paper,sans]{moderncv}
\moderncvstyle{banking}
\moderncvcolor{blue}

% Force both first and last name AND section headings to render in moderncv
% blue (color1). Default banking on lualatex+MiKTeX leaves these black, which
% looks inconsistent with the rest of the blue accent scheme.
\renewcommand*{\firstnamestyle}[1]{{\fontsize{34}{36}\bfseries\upshape\color{color1}#1}}
\renewcommand*{\lastnamestyle}[1]{{\fontsize{34}{36}\bfseries\upshape\color{color1}#1}}
\renewcommand*{\sectionstyle}[1]{{\sectionfont\color{color1}#1}}

\usepackage[utf8]{inputenc}
\usepackage{hyperref}
\hypersetup{
    colorlinks=true,
    linkcolor=blue,
    filecolor=magenta,
    urlcolor=blue,
    pdftitle={[YOUR_NAME] - CV},
    pdfpagemode=FullScreen,
}
\usepackage[scale=0.77]{geometry}
\usepackage{import}

% Personal data
\name{[FIRST_NAME]}{[LAST_NAME]}
\address{[YOUR_ADDRESS]}{}{}
\phone[mobile]{[YOUR_PHONE]}
\email{[YOUR_EMAIL]}
\extrainfo{\href{[YOUR_LINKEDIN_URL]}{LinkedIn}, \href{[YOUR_GITHUB_URL]}{GitHub}}

\begin{document}
\makecvtitle

% 1. Profile statement (2-3 lines, tailored per role)
% 2. Skills section
% 3. Education section
% 4. Professional Experience section
% 5. Selected Publications (if applicable)
% 6. Honors and Awards (if applicable)
% 7. References

\end{document}
```

### Color overrides

The three `\renewcommand*` lines in the preamble are required on lualatex+MiKTeX. Without them the firstname, lastname, and section headings render in black even though `\moderncvcolor{blue}` is set, which looks inconsistent with the rest of the blue accent scheme (links, bullet markers, contact icons). The override forces all three to use `color1` (moderncv's accent colour, which becomes blue under `\moderncvcolor{blue}`). Both names render bold; if you prefer the firstname in regular weight, change the firstnamestyle override from `\bfseries` to `\mdseries`. Don't drop the override - on most modern installs the defaults render visibly wrong.

### Never wrap placeholder or bullet text in square brackets inside `itemize`

LaTeX's `\item` command treats a `[...]` immediately following it as an optional custom-label argument, not literal text. `\item [Responsibility or achievement 1]` silently truncates most of the bracketed text (it gets typeset as a narrow left-margin label and overflows), producing a broken-looking bullet and an `Overfull \hbox` warning at that line. This bit a placeholder-bullet draft of `main_example.tex` in Aug 2026 - the fix is to never open a bullet's text with `[`; write plain text (`\item Responsibility or achievement 1 -- to be added`) instead, even for TODO-style placeholders.

### Spacing inside itemize lists (important)

**Do not place `\vspace{...}` between `\item` entries in an `itemize` list.** Even though the source looks symmetric, this pattern occasionally produces a noticeably oversized gap before a single item: the inter-item `\vspace` creates a paragraph break that interacts unpredictably with the list's internal `\itemsep`, so LaTeX renders one of the gaps wider than the rest. Remove the inter-item `\vspace` and let `itemize` use its native uniform spacing.

```latex
% WRONG - intermittently produces an oversized gap before one bullet
\begin{itemize}
\item \textbf{Foo}: ...
\vspace{1pt}
\item \textbf{Bar}: ...
\vspace{1pt}
\item \textbf{Baz}: ...
\end{itemize}

% RIGHT - uniform spacing using the list's native itemsep
\begin{itemize}
\item \textbf{Foo}: ...
\item \textbf{Bar}: ...
\item \textbf{Baz}: ...
\end{itemize}
```

Two related patterns are fine and should be kept:
- `\vspace{1pt}` immediately after `\section{...}` (between section heading and first item) - this is between the heading and the list, not between list items.
- `\vspace{3pt}` between top-level `\cventry` blocks in Professional Experience or Education - this gives breathing room between roles and renders consistently.

## Section-by-Section Tailoring

### Header and Profile (Best Practice)
**Header:** name, plain-text contact line, and a location line - **no headline/tagline under the name** (decided 2026-10-13). The location line answers relocation and work rights before a recruiter has to ask, e.g. "Horst, Netherlands · relocating to Copenhagen, Denmark". Never use icon fonts for contact details: the ATS reads their glyph names as words.

**Profile:** a 2-3 line section directly under the header - Danish CVs usually have one, and it lets a recruiter place you in seconds. Structure: who you are in one clause (you may echo the posting's job title), the single strongest proof point, the background. Tailor it per posting.

> Example (AI roles): "Data scientist who builds and runs AI agents in production: sole engineer behind a multi-agent Customer Service system on Claude, with a background in data warehousing, API integrations and process automation."

**Exclusion: never mention the MSc in the profile.** Education belongs only in the Education section. Do not repeat numbers in the profile that the first bullet already carries if space is tight.

### Skills Section Keyword Coverage (Best Practice)
**List every tool the experience bullets mention**, including engineering tooling (Git, GitHub Actions CI/CD, pytest, uv, ruff, mypy), Dataform, n8n etc., in an "Engineering" or similar category. ATS keyword matching reads the skills section first; a tool that appears only inside a bullet is easy to miss. (This replaces the earlier rule that kept CI/CD and testing out of the skills section.)

### Core Competencies / Skills Section (Best Practice)
Reorder and emphasize based on the role. Use bold category labels.

List **5-7 key competencies** in bullet format, tailored to the specific job. For each competency, briefly explain how it adds value to the position.

### Education
- Always include your highest degrees
- For senior roles, keep education brief (dates and titles only)
- Include thesis topics when relevant to the target role

### Professional Experience
- Rewrite bullet points to emphasize aspects most relevant to the target role
- Use 4-6 bullets for most recent role, 3-4 for previous, 2-3 for older
- **Emphasize measurable results** where possible: "Reduced processing time by X%", "Model adopted by the team"

### Handling Employment Gaps (Best Practice)
If there is a gap in your employment history:
- The gap should be explained matter-of-factly if needed
- Describe how professional development continued during the gap
- Frame as deliberate skill-building and career repositioning

### Publications
- Include Google Scholar link if applicable
- Select 3-4 most relevant publications (not always all of them)
- For non-academic roles, keep brief

### Honors and Awards
- Keep format brief, one line each

### References
- List 2-4 references with name, title, company, and contact
- End with: "More references are available upon request."
- **Do not attach reference letters** - employers typically contact references directly

## Compile-and-Inspect Loop (MANDATORY)

After writing the CV and before presenting to the user, always compile and visually inspect the PDF. Iterate until the layout is clean. Workflow:

1. Run `lualatex -interaction=nonstopmode cv_<company>.tex` (on Linux, TeX Live needs `texlive-luatex texlive-latexextra texlive-fontsextra`; a "Font \TU/lmr ... not loadable" error in the log is harmless - Latin Modern is loaded by fontspec before XCharter replaces it - and goes away with `texlive-fontsrecommended`)
2. Check the output page count: must match the active template's limit (**exactly 1 page** for `steff-ats`)
3. Read the PDF via the Read tool and visually inspect it
4. Check for **overlaps and cramped spots** (the common failures of the tight 1-page template):
   - Elements touching or overlapping (headings, rules, bullets) - see the active template's `TEMPLATE.md` pitfalls for template-specific fixes
   - Header text layer: `pdftotext` must show plain name, phone, email and LinkedIn - no icon names
   - Bullets ending in a single orphaned word on their last line: reword to save the line - each one is a full line of page budget

**Problem: spills to page 2**
Cut content using relevance-weighted cutting (below). Do not shrink margins, `\linespread`, `itemsep` or section spacing back down: those values were set on 2026-10-13 because the original values looked cramped. Rewording bullets that end in one or two words on their last line is usually the cheapest saving.

**Problem: content finishes early (bottom quarter of the page empty)**
Restore the highest-relevance item that was previously cut - a 1-page CV ending well short of the page looks thin.

## ATS Parseability

Most employers run CVs through an ATS before a human sees them, and the ATS reads the PDF's embedded **text layer**, not the rendered page. A CV can pass visual inspection and still extract as garbage. After the layout passes the compile-and-inspect loop, verify the text layer:

```bash
cd cv && pdftotext -layout cv_<company>.pdf cv_<company>.txt
```

`pdftotext` comes from [poppler](https://poppler.freedesktop.org/), not the TeX distribution - it is an **optional** dependency. If it is not installed, skip the mechanical check with a warning and rely on the visual PDF read for keyword coverage.

What to check in the extraction:

- **Contact details as literal text.** The stock template's fontawesome contact icons extract as glyph names (`MOBILE-ALT`, `Envelope`) - harmless noise, because the actual address and number are printed beside them. The failure mode is a contact detail carried *only* by an icon or a hyperlink (like the `LinkedIn` link text, whose URL is not in the text layer): invisible to an ATS. The email address must always appear as printed text.
- **No garbled output.** `(cid:NNN)` markers or `�` characters mean a font is embedded without a Unicode mapping - an ATS sees the same garbage. This shows up with unusual fonts in custom templates, not with the stock moderncv setup under lualatex.
- **Reading order.** The stock banking style is single-column, so extraction order matches visual order. Custom templates (via `/add-template`) with sidebars or multi-column layouts can interleave unrelated lines; if extraction order is scrambled, the user is trading ATS compatibility for looks and should be told.
- **Keyword coverage.** Match the posting's required/preferred terms against the extracted text, in the posting's language. Prefer the posting's exact term over a synonym when it is truthfully applicable - ATS matching is often literal. Never add a keyword the profile does not support.

## Page Budget

The page limit comes from the active template (see the ACTIVE-TEMPLATE block at the top - currently **exactly 1 page**). Guide for the 1-page template:

| Section | Max budget |
|---------|-----------|
| Header | name + contact line + location line |
| Profile | 2-3 lines |
| Technical Skills | 4-6 single-line categories (one column) |
| Most recent role | 6-8 bullets in 2 themed sub-groups, 1-3 lines each, result first |
| Previous roles | 1 bullet each, ideally 1 line |
| Education | 2 entries |
| Speaking | 1 line |
| Languages | 1 line |

**If in doubt, cut rather than squeeze.** Reducing `\vspace` or geometry scale to force-fit content makes the CV look cramped.

## Relevance-weighted cutting (the right way to shrink a CV)

**Cut by signal, not by section.** Static priority lists ("remove oldest education first, then shorten the earliest role...") are wrong when a relevant "lower-priority" item is competing with an irrelevant "higher-priority" item. An older-role bullet that speaks directly to the posting is worth more than a recent-role bullet that does not.

For every candidate line, score three things:

1. **Relevance to THIS posting** — does the line hit a named tool, keyword, or stated responsibility in the job ad?
2. **Uniqueness** — is it the only place this claim appears, or is it duplicated elsewhere in the CV?
3. **Narrative load** — does the cover letter depend on it? If cutting the line would force you to rewrite a cover-letter paragraph, it is load-bearing.

Cut the lowest-total-score line first, regardless of which section it sits in.

### Practical order of cuts (easiest → last resort)

1. **Redundancy.** If an achievement appears in both Core Competencies AND a role bullet, the Core Competencies version is usually the cleaner cut (the experience bullet is more concrete evidence).
2. **Profile padding.** A profile clause that only restates the first bullet. Keep the profile to 2 lines when space is tight.
3. **Low-relevance experience bullets.** A bullet about work that does not touch posting keywords, wherever it sits. This cuts across sections before touching the structural list.
4. **Low-relevance supporting content.** An older-role bullet that does not speak to the target role. A certification that does not touch the posting's stack. A language entry that can be condensed to one line.
5. **Low-relevance publications.** Keep 1-2 publications that best match the posting. Cut the rest before touching experience bullets.
6. **Last-resort structural cuts.** Oldest education entry, tightening an older role to 2 bullets, collapsing Certifications into a single line. These only happen if the relevance-weighted cuts above have already been exhausted.

### Pitfalls to avoid

- Do not mechanically cut from the bottom of a static section list without checking relevance. "Cut the oldest role first" is wrong if that role is literally about the skill the posting asks for.
- Do not cut the one concrete example the cover letter leans on. Relevance is measured against the cover letter you wrote, not just the job posting — interviewers will have read both.
- For a near-miss (one or two lines over), first reword bullets that end in an orphaned word; only then cut a low-relevance line.

## Recommended Section Order

Follow the active template's order: Header (no headline) -> Profile -> Technical Skills -> Experience -> Education -> Speaking -> Languages. No References section ("available upon request" is assumed).
