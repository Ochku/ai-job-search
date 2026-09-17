# Search Queries for Job Scraper

<!-- SETUP: Customize these queries based on your skills, target roles, and location -->

## Search Sites

Primary (Danish job market):
- **jobindex.dk** - largest Danish job board
- **linkedin.com/jobs** - LinkedIn job listings (filter: Denmark / Copenhagen)
- **karriere.dk** - IDA's job board (engineering/science roles)
- **jobfinder.dk** - another major Danish job board
- **akademikernes.dk** - academic union job board
- **it-jobbank.dk** - IT-focused Danish job board

Secondary (company career pages via Google):
- Direct Google searches with `site:` filters for known target companies

## Query Categories

Queries are grouped by priority. Each query should be combined with location terms ("Copenhagen", "Hovedstaden", "Sjælland", "Hillerød") where the site supports it. Sector is deliberately not used as a filter - see Target Sectors in `CLAUDE.md` (sector-agnostic by design).

### Priority 1: Data Scientist / Data Analyst / Data Engineer

These match the broadened career goal (general DS/ML/DE/analyst, not narrowly specialized) and strongest skills (Python, SQL, GCP).

```
site:jobindex.dk "Data Scientist" Copenhagen OR Hillerød
site:jobindex.dk "Data Analyst" Copenhagen OR Hillerød
site:jobindex.dk "Data Engineer" Copenhagen OR Hillerød
site:jobindex.dk "Python" "SQL" Copenhagen OR Hillerød
site:linkedin.com/jobs "Data Scientist" Denmark
site:linkedin.com/jobs "Data Engineer" Denmark
site:it-jobbank.dk "Data Scientist"
site:it-jobbank.dk "Data Engineer"
site:it-jobbank.dk "Data Analyst"
```

When running the live-browser search (not the WebSearch fallback), also run the Jobindex geography filter for Hillerød directly, e.g. `https://www.jobindex.dk/jobsoegning/hilleroed?q=data+scientist&lang=en` (mirror the `koebenhavn` pattern used for Copenhagen) - the Copenhagen geo-filter does not reliably include Hillerød postings even though it's in the same commute region.

### Priority 2: Marketing Measurement / E-commerce Data

These match domain expertise (MTA/MMM/attribution, ROPO, data warehouse/ETL) - a strength to search for, not a sector restriction.

```
site:jobindex.dk "marketing analytics" OR "marketing attribution" Copenhagen OR Hovedstaden
site:jobindex.dk "BigQuery" OR "Dataform" Copenhagen
site:linkedin.com/jobs "attribution" "data" Copenhagen Denmark
```

### Priority 3: Analytics Engineer / BI Developer / BI Engineer / ML Engineer

Adjacent roles that fit the "stay hands-on IC, broaden beyond one title" goal.

```
site:jobindex.dk "Analytics Engineer" Copenhagen
site:jobindex.dk "BI Developer" OR "BI Udvikler" OR "Business Intelligence Engineer" Copenhagen
site:jobindex.dk "Machine Learning Engineer" Copenhagen
site:linkedin.com/jobs "Business Intelligence Engineer" Denmark
site:linkedin.com/jobs "Machine Learning Engineer" Denmark
site:it-jobbank.dk "Analytics Engineer" OR "BI Udvikler" OR "Business Intelligence Engineer"
site:it-jobbank.dk "Machine Learning Engineer"
```

### Priority 4: Broader Technical / Consulting

Wider net for general technical roles that use the same core toolset.

```
site:jobindex.dk "Python" developer Copenhagen
site:linkedin.com/jobs "SQL" "Python developer" Copenhagen
site:jobindex.dk "technical consultant" data Copenhagen
```

## Location Filter

When evaluating results, verify the job location is compatible with the Denmark deal-breaker (see `CLAUDE.md` Deal-breakers). Define acceptable areas:
- Copenhagen (København) and Frederiksberg - ideal
- Greater Copenhagen / Hovedstaden region, including Hillerød - acceptable
- Remote-to-Denmark (company based in Denmark, role explicitly remote-friendly) - acceptable
- Other Danish cities requiring on-site presence (e.g. Aarhus, Odense) - borderline, flag for discussion since it would mean a second relocation within Denmark
- Any role requiring relocation outside Denmark or permanent on-site outside Denmark - fails the deal-breaker, exclude

## Date Filter

Only include jobs posted within the last 14 days, or with an application deadline that has not yet passed. If a posting date cannot be determined, include it but flag as "date unknown".

## Adapting Queries

If the user specifies a focus area, select queries from the matching category and also generate 2-3 custom queries for that focus. For example:
- "/scrape [focus_area]" -> relevant category queries + custom focus-specific queries
