---
name: job-scraper
description: >
  Scrapes Danish job sites for new positions matching your profile. Deduplicates across runs.
  Triggers on: job scrape, find jobs, search jobs, new jobs, job search, scrape jobs, /scrape
allowed-tools: Read, Write, Edit, Glob, Grep, WebFetch, WebSearch, Agent, AskUserQuestion
---

# Job Scraper

---

## How It Works

This skill searches multiple Danish job sites using targeted queries based on your profile, deduplicates against previously seen jobs and the application tracker, and presents new matches with a quick fit assessment.

## Invocation

The user triggers this skill by saying things like:
- "Find new jobs"
- "Scrape for jobs"
- "Any new positions?"
- "/scrape"

Optional arguments:
- A focus area, e.g. "/scrape data science" or "/scrape geophysics"
- "broad" to run all search categories, e.g. "/scrape broad"

---

## Execution Steps

### Step 0: Load State

1. Read `job_scraper/seen_jobs.json` (create if missing - start with `{"seen": {}}`)
2. Read `job_search_tracker.csv` to extract already-applied companies+roles
3. Read `search-queries.md` (this directory) for the search strategy

### Step 1: Search

**Known limitation - `WebSearch` is stale, prefer live `WebFetch` for LinkedIn and TheHub (fixed 2026-09-17):** `WebSearch` returns results from Google's cached index of these sites, which lags real postings by days and misses same-day listings entirely (verified: a live fetch surfaced postings from 10-25 minutes ago that `WebSearch` didn't return at all). For LinkedIn and TheHub specifically, use `WebFetch` directly on the site's live search-results URL instead of `WebSearch` site-filtered queries:
- LinkedIn: `WebFetch` on `https://www.linkedin.com/jobs/search/?keywords=<role>&location=Copenhagen%2C%20Denmark&f_TPR=r604800` (one fetch per role keyword: "Data Scientist", "Data Engineer", "Data Analyst", etc.), prompting for title/company/location/URL/posting-age for every listing on the page.
- TheHub: `WebFetch` on `https://thehub.io/jobs?roles=engineer&roles=analyst&roles=datascience&countryCode=DK&sorting=mostPopular`, prompting for the same fields. TheHub aggregates Danish startup/scaleup jobs across engineer/analyst/data-science roles - a useful cross-check against Jobindex/LinkedIn since its listings often don't appear on either.
- Jobindex.dk search-results pages are JS-rendered and don't expose listings to `WebFetch` (confirmed) - keep using `WebSearch` site-filtered queries for Jobindex, or the live-browser search noted in `search-queries.md` where available.
- `karriere.dk`, `jobfinder.dk`, `akademikernes.dk`, `it-jobbank.dk` - `WebSearch` has not been confirmed stale for these; keep using it for now, but if a scrape run turns up suspiciously few results, spot-check with a live `WebFetch` the same way as LinkedIn/TheHub.

Run queries from `search-queries.md` (via `WebSearch` for Jobindex-family sites, via live `WebFetch` for LinkedIn/TheHub as above). By default, run the top 3 priority categories. If the user said "broad", run all categories.

If the user specified a focus area (e.g. "data science"), prioritize queries from that category.

For each search:
- Target your configured geographic area
- Look for postings from the last 14 days

### Step 2: Fetch & Parse

For each promising result from Step 1:
- Use `WebFetch` to retrieve the job posting page
- Extract: **job title**, **company**, **location**, **posting date** (or "recent"), **URL**, **key requirements** (brief), **application deadline** (if listed)
- Skip if the URL or company+title combo already exists in `seen_jobs.json`
- Skip if the company+role already appears in `job_search_tracker.csv`

### Step 3: Quick Fit Assessment

For each new job, do a rapid fit check (NOT the full evaluation from `04-job-evaluation.md` - just a quick signal):

- **High match**: Role directly involves your core skills
- **Medium match**: Role is adjacent to your experience
- **Low match**: Role requires significant skills you lack

### Step 4: Deduplicate & Store

1. Add ALL fetched jobs (new and skipped) to `seen_jobs.json` with structure:
```json
{
  "seen": {
    "<url_or_company_title_key>": {
      "title": "...",
      "company": "...",
      "url": "...",
      "first_seen": "YYYY-MM-DD",
      "fit": "high/medium/low",
      "status": "new/skipped/evaluated/ranked/expired"
    }
  }
}
```
2. Only present jobs NOT already in the seen list or tracker.

### Step 5: Present Results

Present new jobs in a table sorted by fit (high first):

```
## New Job Matches - YYYY-MM-DD

Found X new positions (Y high, Z medium, W low match).

| # | Fit | Title | Company | Location | Deadline | URL |
|---|-----|-------|---------|----------|----------|-----|
| 1 | High | ... | ... | ... | ... | [Link](...) |

### High-Match Highlights
For each high-match job, add 2-3 bullet points:
- Why it matches your profile
- Key requirements to check
- Any red flags
```

After presenting, ask:
> "Want me to evaluate any of these in detail? Just give me the number(s)."

If the user picks a number, invoke the **job-application-assistant** skill workflow (fit evaluation first, then CV + cover letter if approved).

If the run found many new jobs (roughly 8+), also suggest `/rank` - it batch-scores all new postings against the full fit framework and returns a ranked shortlist, which beats eyeballing a long table. (`/rank` sets the `ranked` and `expired` status values in `seen_jobs.json`; treat both as already-seen for dedup purposes.)

### Step 6: Update Tracker (Optional)

If the user decides to apply to any job, add a row to `job_search_tracker.csv`.

---

## Important Rules

1. **Never fabricate job postings.** Only present jobs found via actual WebSearch/WebFetch results.
2. **Respect deduplication.** Always check seen_jobs.json AND job_search_tracker.csv before presenting.
3. **Focus on configured geographic area.** Skip jobs that require relocation or are clearly outside commute range.
4. **Only open positions.** Skip postings with expired deadlines or those marked as closed.
5. **Be efficient with WebFetch.** Don't fetch every search result - use titles and snippets to pre-filter before fetching.
6. **Parallel searches.** Use the Agent tool or parallel WebSearch calls to speed up the search phase.
