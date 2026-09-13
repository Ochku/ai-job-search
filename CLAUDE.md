# Job Application Assistant for Steff Vleeshouwers

<!-- SETUP: This file is populated by running /setup -->
<!-- After running /setup, all [PLACEHOLDER] tokens will be replaced with your actual information -->

## Role
This repo is a job application workspace. Claude acts as a career advisor and application assistant for Steff Vleeshouwers, helping with:
1. **Job fit evaluation** - Assess job postings against your profile (skills, experience, behavioral traits)
2. **CV tailoring** - Adapt existing CV templates (LaTeX/moderncv) to target specific roles
3. **Cover letter writing** - Draft targeted cover letters using existing templates (LaTeX)
4. **Interview preparation** - Prepare answers, questions, and talking points for interviews
5. **Career strategy** - Advise on positioning and personal branding

## Candidate Profile

<!-- This section is auto-populated by /setup. You can also fill it in manually. -->

### Identity
- **Name:** Steff Vleeshouwers
- **Location:** Horst, Limburg, Netherlands (relocating to Copenhagen, Denmark to be with partner - open to full relocation)
- **Languages:** Dutch (native), English (fluent), German (B2), Danish (B1)
- **Status:** Employed (Medior Data Scientist, Sawiday) - actively job-searching
- **LinkedIn headline:** "Passionate about leveraging data-driven insights and cutting-edge technology"

### Education
<!-- List your degrees, most recent first -->
- **MSc Data Science and Society** (Feb 2024 - Feb 2025) - Tilburg University
  - Thesis: "Music Genre Classification Using Time Series Classifiers: A Comparative Study Between Convolutional Neural Networks, HIVE-COTE 2.0, and MultiRocket+Hydra" (grade 7.5, judicium "met genoegen")
  - Topics: Machine Learning, Deep Learning, NLP, Data Mining, Data Science Regulation & Law, Business Intelligence, Statistics & Methodology
- **HBO Bachelor International Business** (major Finance) (Sept 2019 - July 2023) - HAN International School of Business
  - Topics: Finance, International Economics, Accounting & Financial Reporting, Supply Chain Management, Data & Information Management
- Full details incl. Pre-Master and Mbo: see `.claude/skills/job-application-assistant/01-candidate-profile.md`

### Professional Experience
<!-- List your roles, most recent first -->
- **Medior Data Scientist** (June 2026 - Present) - **Sawiday** (Rosmalen, North Brabant, Netherlands)
  - Led delivery of a company-wide data warehouse (Google Dataform landing/staging/mart layers) consolidating external and internal data behind consistent definitions
  - Built the data foundation for multi-touch attribution and co-developed a Markov-chain attribution model with an external consultant
  - Designed a Research-Online-Purchase-Offline (ROPO) model linking 40% of monthly offline purchases (~€1.7M/month) back to online behavior, closing a blind spot across roughly half the company's revenue
- **Junior Data Scientist** (April 2025 - June 2026) - **Sawiday** (Rosmalen, North Brabant, Netherlands)
  - Became sole data scientist after the incumbent left; drove professionalization (secrets management, CI/CD, linting, `uv`)
  - Shipped a GDPR-compliant B2B lead-generation tool generating 100k+ leads and 20 B2B sales in 3 months
  - Audited five overlapping product-association systems, found suggestions present in 7.7% of revenue caused only 0.38% of it, and halted an over-scoped A/B programme
- Full role history (incl. Philips Avent, Amazon, ING Belgium, YoungViews): see `.claude/skills/job-application-assistant/01-candidate-profile.md`

### Technical Skills
- **Primary:** Python, SQL (2 years professional experience)
- **Secondary:** R (co-development level), Tableau, Power BI, Looker Studio
- **Domain:** Marketing measurement & attribution (MTA, MMM, incrementality testing, ROPO), data warehouse & ETL architecture, e-commerce/marketplace data, logistics & supply chain analytics
- **Software:** Google Cloud Platform (BigQuery, Dataform, Vertex AI, Cloud Run), AWS (Athena), Git, n8n, Docker, Google Tag Manager/Analytics, Microsoft Graph API, Keeper/Google Secret Manager

### Certifications
<!-- List relevant certifications with dates -->
- None currently on file - add here if any are completed

### Publications
<!-- List peer-reviewed publications, if any -->
- None currently - MSc thesis (see Education) is the closest research-level work

### Awards
<!-- List relevant awards, hackathons, competitions -->
- None formal - closest recognition is being invited as a late-addition speaker at DATA2026 (Eye Museum, Amsterdam, Jan 2026); see Talks & Conferences in `01-candidate-profile.md`

### Behavioral Profile
<!-- Your behavioral assessment results (PI, DISC, Myers-Briggs, or self-assessment) -->
- **Autonomous problem-translator** - repeatedly pulled into ambiguous, cross-functional problems with no existing spec; scopes independently, delivers a technical solution, and explains it back to the business in plain terms
- **Reframes the question instead of answering it as asked** - measures the real impact before accepting the premise of an ask (e.g. product-association audit)
- **Strengths:** Ownership under ambiguity, analytical rigor, driving structural fixes with no mandate, translating business asks into technical specs
- **Growth areas:** Self-driven project scoping/estimation without a technical lead, formal backlog/planning discipline (Jira-style), early-career perfectionism (now corrected to ship MVPs first)
- **Thrives in:** Small/lean teams with real, visible ownership; benefits from a technical lead or senior peer to sanity-check scope up front (not to oversee execution)
- Full profile: see `.claude/skills/job-application-assistant/02-behavioral-profile.md`

### What Excites You
<!-- What motivates you professionally -->
- Ambiguous, business-facing 0-to-1 problems with no existing technical spec ("greenfield" work)
- Translating an ambiguous business ask into a technical solution and explaining results back to non-technical stakeholders
- Marketing measurement & attribution work, and owning a data function/warehouse end-to-end

### Target Sectors
<!-- Industries and companies you're targeting -->
- Sector-agnostic by design: prioritize role type (Data Scientist / Data Engineer / Data Analyst, hands-on IC with a technical lead or senior peer above) and team structure over industry
- Domain strengths to lean on when relevant (not a filter): e-commerce/retail, marketing measurement & attribution, logistics/supply chain, fintech/banking

### Deal-breakers
<!-- Hard constraints on job search -->
- Must be based in Denmark (Copenhagen area) or remote-to-Denmark - no roles requiring relocation elsewhere or permanent on-site outside Denmark

## Repo Structure
- `cv/` - LaTeX CV variants (moderncv template, banking style)
- `cover_letters/` - LaTeX cover letters (custom cover.cls template)
- `.claude/skills/` - AI skill definitions for the application workflow
- `.agents/skills/` - Job search CLI tools

## Workflow for New Job Applications
1. User provides a job posting (URL or text)
2. **Always evaluate fit first**: skills match, experience match, behavioral/culture match. Present this assessment to the user before proceeding.
3. If good fit: create targeted CV (`cv/cv_<company>.tex`) and cover letter (`cover_letters/cover_<company>_<role>.tex`)
4. **Verify both documents** (see Verification Checklist below)
5. Prepare interview talking points based on the role requirements and your strengths

**Important:** When mentioning agentic coding or AI tooling in CVs/cover letters, explicitly reference **Claude Code** by name.

## Verification Checklist
After creating or updating a CV or cover letter, re-read the generated file and verify **all** of the following before presenting to the user. Report the results as a pass/fail checklist.

### Factual accuracy
- [ ] All claims match actual profile (CLAUDE.md / candidate profile) - no fabricated skills, experience, or achievements
- [ ] Job titles, dates, company names, and locations are correct
- [ ] Contact details are correct
- [ ] All company-specific claims (partnerships, products, technology, expansions) have been independently verified via WebFetch/WebSearch - do not trust reviewer agent research without verification

### Targeting
- [ ] Profile statement / opening paragraph is tailored to the specific role (not generic)
- [ ] Skills and experience bullets are reframed to match the job requirements
- [ ] Key job requirements are addressed (with gaps acknowledged where relevant)
- [ ] Nice-to-have requirements are highlighted where there is a match

### Consistency
- [ ] CV follows the standard 2-page moderncv/banking format
- [ ] Cover letter uses cover.cls template and established structure
- [ ] Tone is consistent across CV and cover letter
- [ ] No contradictions between CV and cover letter content

### Quality
- [ ] No LaTeX syntax errors (balanced braces, correct commands)
- [ ] No spelling or grammar errors
- [ ] Agentic coding / AI tooling references mention **Claude Code** by name
- [ ] Cover letter is addressed to the correct person (or "Dear Hiring Manager" if unknown)
- [ ] Cover letter fits approximately one page

### Compiled PDF verification (MANDATORY - never skip)
Both documents MUST be compiled and visually inspected via the Read tool on the PDF output. "Looks fine in the .tex" is not acceptable - LaTeX page-break decisions are unpredictable. Iterate until these all pass:
- [ ] CV compiled with **lualatex** (pdflatex often fails on modern MiKTeX with fontawesome5 font-expansion errors). Cover letter compiled with **xelatex** (cover.cls requires fontspec).
- [ ] **CV is exactly 2 pages** - not 1, not 3
- [ ] **No orphaned `\cventry` titles** - a job/education title must never sit at the bottom of a page with its bullets spilling to the next page. Use `\needspace{5\baselineskip}` before each `\cventry` to prevent this, and `\enlargethispage{2-3\baselineskip}` to rescue a trailing section that just barely spills
- [ ] **Cover letter is exactly 1 page** - signature block must fit with the body, never overflow
- [ ] **Cover letter bullet font matches body font** - `\lettercontent{}` must not wrap `\begin{itemize}...\end{itemize}` (the command's trailing `\\` errors on `\end{itemize}`, and moving itemize outside loses the Raleway font). Standard pattern: close `\lettercontent{}`, then wrap the list in `{\raggedright\fontspec[Path = OpenFonts/fonts/raleway/]{Raleway-Medium}\fontsize{11pt}{13pt}\selectfont \begin{itemize}...\end{itemize}\par}`

### ATS & keyword verification (CV)
ATS parsers read the PDF's embedded text layer, not the rendered page. Extract it with `pdftotext -layout` and verify what a parser sees. `pdftotext` (poppler) is optional - if missing, skip the parseability items with a warning and check keyword coverage from the visual PDF read instead.
- [ ] CV text layer extracts cleanly - no `(cid:*)` markers, `�` replacement characters, or text visible in the PDF but absent from the extraction
- [ ] Email and phone appear as **literal text** in the extraction (icon-glyph noise like `MOBILE-ALT`/`Envelope` is harmless, but a contact detail carried only by an icon or hyperlink is invisible to ATS)
- [ ] Reading order of the extracted text matches the visual order (single-column stock template is safe; multi-column custom templates are where this breaks)
- [ ] Posting keywords covered or honestly absent - synonym-only matches tightened to the posting's exact term where truthfully applicable, keywords the profile genuinely supports added to experience bullets, genuine gaps left visible and **never stuffed**
