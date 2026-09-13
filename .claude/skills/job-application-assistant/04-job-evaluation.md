# Job Evaluation Framework

<!-- SETUP: Skill match areas and career goals are personalized by running /setup -->

## Scoring Dimensions

Evaluate each job posting against these five dimensions:

### 1. Technical Skills Match (0-100)
How well do the required/preferred skills align with the candidate's capabilities?

| Score | Meaning |
|-------|---------|
| 80-100 | Core requirements are primary skills |
| 60-79 | Most requirements match, 1-2 gaps that are learnable |
| 40-59 | Partial match, significant upskilling needed |
| 0-39 | Fundamental mismatch |

**Strong match areas:** Python, SQL, marketing measurement & attribution (MTA, MMM, incrementality testing, ROPO/Markov-chain modeling), data warehouse & ETL design (Google Dataform, BigQuery landing/staging/mart architecture), Google Cloud Platform (Cloud Run, Vertex AI, BigQuery), stakeholder-facing data storytelling and translating ambiguous business asks into technical specs, e-commerce/marketplace data
**Moderate match areas:** R (code-review/steering level, not primary implementer), deep learning & time series classification (strong academic depth from thesis - CNNs, HIVE-COTE 2.0, MultiRocket+Hydra - limited production ML-engineering mileage), BI/dashboarding tools (Tableau, Power BI, Looker Studio), workflow automation (n8n), AWS (Athena only)
**Weak match areas:** *(no evidence yet in profile - confirm/add)* formal people management, productionized MLOps at scale (model serving/monitoring infrastructure beyond Cloud Run microservices), Danish beyond B1 (relevant for Denmark-based roles requiring fluent/native Danish)

### 2. Experience Match (0-100)
Does work history align with what they're looking for?

| Score | Meaning |
|-------|---------|
| 80-100 | Direct experience in the same domain and role type |
| 60-79 | Related experience, transferable skills clear |
| 40-59 | Adjacent experience, would need to make the case |
| 0-39 | Unrelated experience |

**Strong:** Data science / analytics roles bridging business stakeholders and technical delivery; marketing measurement & attribution; data warehouse/ETL ownership; e-commerce and B2B lead-generation domains; being the sole or lead technical resource on a small data function
**Moderate:** Financial analysis / quantitative modeling roles (ING Belgium, Amazon) - transferable analytical rigor, stakeholder reporting, and regression/statistical modeling, but not under a "data scientist" title; logistics/supply-chain analytics (Amazon, Sawiday)
**Entry-level:** Formal people management (never had direct reports); large-scale production ML engineering / MLOps (ML experience is thesis-level academic depth plus lightweight on-device work at Philips Avent, not high-scale production ML systems)

**Seniority-title calibration (important - self-assessed level is Junior/Medior, not Senior):** Total professional data/DS tenure is Junior Data Scientist (Apr 2025-Jun 2026, ~14 months) + Medior Data Scientist (Jun 2026-present) - under two years total, none of it under a "Data Engineer" title specifically even though the work included real ETL/warehouse ownership. When a posting's title carries a seniority qualifier ("Senior", "Staff", "Lead", "Principal") **and** states an explicit minimum-years requirement in the exact function being hired for (e.g. "3-5 years as a Data Engineer", "6+ years"), cap Experience Match at 55 regardless of tool/domain overlap - broad scope or ownership at a lower title does not substitute for a stated minimum-tenure gate in an ATS-screened posting. If the posting carries a seniority title but states no explicit years requirement (common at smaller/scrappier companies where "Senior"/"Staff" reflects scope and autonomy rather than tenure), score normally but flag the title mismatch as a gap for the user to sanity-check before applying - don't silently ignore it either way.

### 3. Behavioral/Culture Fit (0-100)
Does the role and company culture match the behavioral profile?

| Score | Meaning |
|-------|---------|
| 80-100 | Culture strongly matches behavioral preferences |
| 60-79 | Mixed signals but mostly compatible |
| 40-59 | Some friction areas |
| 0-39 | Significant culture mismatch |

**Red flags to research:** Department disorganization, work dominated by maintenance over development, poor chemistry with leadership, culture mismatches. Check reviews, media coverage, LinkedIn connections, and network contacts for insider perspective.

### 4. Location & Logistics (Pass/Fail + Notes)
- Within commute range: PASS
- Remote with occasional office: PASS
- Requires relocation: FAIL (deal-breaker)
- Frequent international travel: FLAG (discuss with user)

### 5. Career Alignment & Motivation (0-100)
Does this role advance career goals and contain tasks that energize?

| Score | Meaning |
|-------|---------|
| 80-100 | Strongly aligned with career direction, clear growth path |
| 60-79 | Good role but only partially aligned with long-term goals |
| 40-59 | Decent job but doesn't build toward career goals |
| 0-39 | Dead end or backwards step |

**Career goals:**
- Broaden into general data science / ML roles rather than staying narrowly specialized in marketing measurement/attribution
- Stay hands-on as an individual contributor, but in a team structure with a technical lead or senior peer above to sanity-check scope (not solo-DS again)
- Open to general data engineering and data analyst roles that fit the profile, not just "Data Scientist" titles - widens the search rather than narrowing it

**Motivation filter:** Evaluate not just whether you *can* do the tasks, but whether the tasks will *energize* you. Consider:
- Tasks that energize *(from `02-behavioral-profile.md`)*: ambiguous, business-facing 0-to-1 problems with no existing technical spec; translating an ambiguous ask into a technical solution and explaining it back in plain terms; marketing measurement & attribution work; owning a data function/warehouse end-to-end; small/lean teams where impact is visible
- Tasks that drain *(from behavioral profile)*: heavy formal Scrum/Jira backlog discipline as a core expectation; being the sole technical resource indefinitely with no peer or lead to sanity-check scope/estimates; narrowly scoped IC execution with no stakeholder-facing or scoping component
- Non-task factors: leadership style, department culture, company values, degree of autonomy - benefits from a technical lead or senior peer to validate scope up front (not to oversee execution)

**Life situation alignment:** Consider personal constraints:
- **Security**: Moderate urgency - currently employed at Sawiday so not desperate, but actively want to move within the next few months rather than wait indefinitely for a perfect fit
- **Flexibility**: Open to on-site from day one once relocated to Denmark - no remote/hybrid bridge period needed; Sawiday's notice period is the main timing constraint, not a work-mode preference
- **Professional development**: Priority is building formal ML engineering / MLOps depth (production-grade deployment and monitoring beyond current Cloud Run microservice level) - favor roles that offer this over ones that only reuse existing strengths

### 6. Salary Benchmark (Optional)

If the salary lookup tool is configured (`salary_data.json` exists), look up the company:
```
python salary_lookup.py "<Company Name>" --json
```

If a city is known from the posting, add `--city "<City>"` to narrow results.

Present findings as:
```
### Salary Benchmark
| Metric | Value |
|--------|-------|
| [Category] index | XX.X (+/-X.X% vs baseline) |
| Overall index | XX.X (+/-X.X% vs baseline) |
```

Interpret results relative to the baseline defined in the data file's metadata. For index-based data, higher typically means above-market compensation.

If the salary tool is not configured, skip this section.

## Output Format

Present the evaluation as:

```
## Job Fit Evaluation: [Role] at [Company]

| Dimension | Score | Notes |
|-----------|-------|-------|
| Technical Skills | XX/100 | [brief note] |
| Experience Match | XX/100 | [brief note] |
| Behavioral Fit | XX/100 | [brief note] |
| Location | PASS/FAIL | [brief note] |
| Career Alignment | XX/100 | [brief note] |

**Overall Score: XX/100** (weighted average of scored dimensions)

### Verdict: [Strong Fit / Good Fit / Moderate Fit / Weak Fit / Poor Fit]

### Key Strengths for This Role
- [bullet points]

### Gaps to Address
- [bullet points]

### Recommendation
[1-2 sentences: apply/skip/apply with caveats]

### Company Research Checklist
- [ ] Checked company website (mission, values, recent news)
- [ ] Checked review sites (Glassdoor, Jobindex, etc.)
- [ ] Checked LinkedIn for team size, recent hires, connections
- [ ] Checked media for restructuring, growth, or workplace issues
- [ ] Identified network contacts who may know the team/manager
```

## Weighting
- Technical Skills: 30%
- Experience Match: 25%
- Behavioral Fit: 15%
- Career Alignment: 30%

(Location is pass/fail, not weighted)

## Thresholds
- **Strong Fit** (75+): Definitely apply, tailor everything
- **Good Fit** (60-74): Apply, address gaps in cover letter
- **Moderate Fit** (45-59): Consider carefully, discuss with user
- **Weak Fit** (30-44): Probably skip unless strategic reasons
- **Poor Fit** (<30): Skip

## Pre-Application: Call the Employer (Best Practice)

Before writing the application, consider whether the candidate should call the contact person listed in the posting. **Only call if there are substantive questions** - never call just to "be remembered."

### When to Suggest Calling
- The posting has unclear or ambiguous requirements
- It's unclear which competencies are essential vs. nice-to-have
- The role description is vague about day-to-day tasks
- There's a named contact person who invites questions

### Good Questions to Ask
- "What are the primary challenges in this role?"
- "How is time typically divided across the listed responsibilities?"
- "Which competencies are most critical for success in this position?"
- "What does success look like in the first 6-12 months?"

### Rules for the Call
- Prepare a 30-second "elevator pitch" about your background in case they ask
- The call's purpose is **gathering information**, not delivering a pitch
- Take notes - use what you learn to tailor the application
- Reference the conversation naturally in the cover letter ("After speaking with [name], I was especially drawn to...")
