# Candidate Profile

<!-- SETUP: This file is populated by running /setup -->
<!-- After running /setup, all sections will be filled with your actual information -->

## Identity
- **Name:** Steff Vleeshouwers
- **Location:** Horst, Limburg, Netherlands
- **Phone:** +31623521660
- **Email:** s.vleeshouwers@outlook.com
- **LinkedIn:** https://www.linkedin.com/in/steff-vleeshouwers
- **Languages:** Dutch (native), English (fluent), German (B2), Danish (B1 - gets by in social settings; not ready for a job where Danish is the working language)
- **Status:** Employed (Medior Data Scientist, Sawiday) - actively job-searching
- **Constraints:** Relocating to Denmark to be with partner - open to full relocation; Danish B1 and improving
- **Work rights & availability:** EU (Dutch) citizen - no Danish work permit needed; available with 1 month's notice. State both in every CV header (decided 2026-10-19)
- **Title on CVs:** write "Data Scientist (promoted from Junior Data Scientist, Jun 2026)" - never "Medior", a Dutch/Belgian level term Danish recruiters don't recognise

## Education

| Degree | Period | Institution | Key Topics |
|--------|--------|-------------|------------|
| MSc Data Science and Society (thesis: "Music Genre Classification Using Time Series Classifiers: A Comparative Study Between Convolutional Neural Networks, HIVE COTE 2.0, and MultiRocket+Hydra", grade 7.5, judicium "met genoegen", avg. 8.32) | Feb 2024 - Feb 2025 | Tilburg University | Machine Learning, Deep Learning, NLP, Data Mining, Data Science Regulation & Law, Business Intelligence, Statistics & Methodology |
| Pre-Master Data Science and Society | Aug 2023 - Jan 2024 | Tilburg University | Bridging program into MSc |
| Bachelor of Business Administration (BBA) International Business, major Finance (HBO; graduation project focused on the fintech sector). On CVs: "Bachelor of Business Administration (BBA), International Business" - never "BSc" | Sept 2019 - July 2023 | HAN International School of Business (Hogeschool van Arnhem en Nijmegen) | Finance, International Economics, Accounting & Financial Reporting, Supply Chain Management, Data & Information Management |
| Mbo Medewerker marketing en communicatie (Niveau 4 / EQF 4) | 2016 - 2019 | Gilde Opleidingen (Roermond) | Marketing & communications |

## Professional Experience

### Medior Data Scientist - Sawiday (June 2026 - Present)
Rosmalen, North Brabant, Netherlands
- Led cross-functional design and delivery of a company-wide data warehouse (~20 sources incl. Spotler CDP, a custom in-house ERP, Zendesk, Dyflexis; daily dashboards are now ready at 8:00 instead of 9:30 because the slow Tableau extract preprocessing moved into Dataform) (coordinating with IT, the team's data analyst, and an external data engineer from The Data Story) to consolidate external and internal data behind consistent definitions and historical records; built structured landing/staging/mart tables in Google Dataform on a daily schedule, ingested via webhook and API connections from external platforms, and prioritized cross-departmental data needs through direct stakeholder negotiation
- Built the data foundation for multi-touch attribution: gained access to marketing-platform APIs, built data dumps into Dataform mart tables, and constructed customer-journey tables with ROPO stitching for cross-device and online/offline measurement; co-developed a Markov-chain attribution model with an external consultant - working jointly through methodology and implementation rather than reviewing from the sidelines - set up the Vertex AI compute environment to run it, and presented resulting dashboards and modeling logic directly to marketing stakeholders
- Identified and closed a blind spot in marketing measurement - roughly 50% of revenue is offline with no bridge to online behavior - by designing a ROPO (Research Online, Purchase Offline) model using Google Tag Manager first-party email capture matched to GA4 user_pseudo_id and cross-referenced against the appointment system and CDP; in the process, found and fixed a server-side tagging bug that was leaking internal traffic into the data, lifting captured online purchase event journeys from ~73% to ~85%, and linked 40% of monthly offline purchases (~€1.7M/month in revenue) to prior online behavior - unlocking lead-discovery, cross-channel product-index, and improved marketing-attribution use cases
- Leading, and solely building all technical parts of, a production multi-agent AI system for Customer Service on Claude Managed Agents (repo `cs-skills`, live in Zendesk since 28 Sept 2026); works in NL, BE and FR. **Results, first ~3 weeks (28 Sep - 20 Oct 2026, user-supplied):** picked up 4,358 tickets in 7,079 sessions; fully resolved 1,194 tickets on its own (1,386 customer replies, 780 tickets set straight to Solved); weekly fully-resolved tickets 38 -> 331 -> 682, full-resolution rate 9% -> 20% -> 38% (36% in the partial week of 19 Oct); total cost $5,648, cost per full resolution $5.32 -> $1.87 (~$2 all-in, roughly 4 minutes of agent time; median ticket handling time 7.8 minutes); median first response 8 minutes on NL Service tickets it answered vs 3 hours for agent-answered NL Service tickets; 35% of its resolved tickets closed with one reply; volume grew from 36 to 400-1,000 sessions/day, cost now ~$400/day. In one week (13-20 Oct) it performed 1,800+ successful script-based actions in Admin and supplier systems (lower bound): 635 order notes, 185 returns created + 107 return statuses set, 127 service orders created + 179 completed, 222 supplier side-conversations started/answered, 271 tickets parked awaiting supplier, 34 pickups scheduled. Project: repo since 23 Sep 2026; 6 agents (coordinator + 5 specialists), 42 skills, 38 scripts; 237 work PRs merged and 204 production deploys in 4 weeks. User also cites net savings of "176 (median) to 368 (mean)" in week 42 - unit not yet confirmed, do not use on CVs until it is. Architecture: a Zendesk trigger starts one session per ticket via a webhook to the Sessions API; a coordinator agent ("Dirigent", Claude Opus 5.5) reads the ticket through the Zendesk MCP server and delegates to five specialist sub-agents (payments, returns, order & delivery status, cancellations, service requests; Claude Sonnet 5), which operate Sawiday Admin, carrier track & trace and supplier portals through Browserbase browser tools and Python scripts, and return a fixed four-part report (sourced summary, attention points, draft customer reply, actions taken + recommended Zendesk action) that is written back to the ticket
  - Division of work: Steff designed and built the whole harness (agent architecture, orchestration, MCP/tool/browser integrations, scripts, deployment pipeline, CLI, evals, safety); a Customer Service colleague wrote the domain content of the skills (the work-specific procedures), with Steff owning the skill framework they plug into
  - 42 versioned Agent Skills (SKILL.md, in Dutch; 32 at an earlier count) plus 38 scripts encode CS procedures and policy (returns, refunds, service/warranty claims, supplier-specific routes, tone of voice) and load on demand - context engineering in layers (sub-agents, skills, reference files, scripts) so each agent loads only the context a ticket needs; tool calling, MCP servers and sub-agent rosters are declared per agent in config-as-code
  - GitOps control plane (built by Steff): agents, skills, environments and vaults live in git; PRs run validation, pytest and an `ant plan` comment, merges deploy via `ant apply` with approval and lockfiles pinning resource versions, and a nightly drift job pulls edits made in the Claude Console back into the repo as a PR - so the CS colleague can draft skills in the Console while git stays the source of truth; a self-built Python CLI (`cs`, uv-managed) handles validation, drift detection, pulling and catalog generation, with decision records (ADRs) and a Dutch handbook for the CS team lead
  - Safety and rollout: an eval-gated autonomy ladder per intent (from internal-note drafts up to public replies), ticket text treated as untrusted input against prompt injection, destructive tools kept on always-ask, restricted sandbox networking, credentials in workspace-scoped vaults, and no customer data in git; eval suites and rubrics with data in BigQuery
  - Privacy by design: built custom MCP servers for Zendesk and the in-house ERP that strip personal data (email addresses, bank details, names, addresses, etc.) before anything reaches the AI model, so no customer PII enters the AI system
  - Context: this follows the earlier stalled Zendesk AI integration (see Junior role) - the project was rebuilt on Claude and taken into production

### Junior Data Scientist - Sawiday (April 2025 - June 2026)
Rosmalen, North Brabant, Netherlands
- Became the company's sole data scientist after the incumbent left (August 2025), reporting directly to the CFO with no technical lead in place; took ownership of professionalizing data science practice and reconciling ownership of script-based projects that sat between IT and Data Science
- Designed and shipped a GDPR-compliant B2B lead-generation tool combining governmental open-data APIs (company registration, activity code, address) with Google Maps API enrichment and targeted web scraping for contact validation, deployed self-service on Google Cloud Run for business stakeholders to query by location and radius - generated 100k+ qualified leads and contributed to 20 B2B sales within the first 3 months
- Led a cross-functional audit of five parallel product-association systems (Product Management, Marketing, IT, Data); built a revenue-attribution model joining web analytics to order lines showing suggestion blocks touched 7.7% of net revenue but caused only 0.38%, reframing the initiative from algorithm selection to fixing the underlying data (only 0.34% of 423,623 supplier-sent product relationships were usable) and halting an over-scoped A/B testing programme before further investment
- Led professionalization of the data science function: migrated credential management off ad hoc storage (including credentials previously committed to GitHub) onto Keeper/Google Secret Manager/.env, introduced Git-based CI/CD with branching, PR review and documentation, standardized linting, and adopted uv for reproducible Python package management
- Built a best-seller dashboard for Marketing by consolidating disparate product data sources in Tableau Prep Builder into a KPI-driven, product-profile-level ranking used to identify "best seller" and "our choice" merchandising picks
- Built and owned an end-to-end HR hour-registration anomaly-detection pipeline (Python) integrating the Dyflexis Business API and Polaris roster exports, applying a rule-based catalog (missing registrations, break violations, overtime outliers, contract mismatches) and routing flagged anomalies to the correct manager/HR checker via automated Microsoft Graph email alerts; flags ~200 issues per month-end close, saving ~2 hours/week of manager reminders plus ~4 hours per monthly close
- Automated purchase-order-confirmation processing into the ERP system via an n8n workflow with AI-based email classification (Outlook/Microsoft Graph) and a companion PDF/CSV extraction microservice on Google Cloud Run, with supplier-specific parsing and validation flags, and personal data (emails, bank details, names, addresses) stripped before AI classification - 60,000+ emails processed from 15 suppliers; live, saving ~35 hours of manual processing per week (originally projected at up to 1 FTE)
- Stepped up to lead a stalled Zendesk AI ticket-automation integration for Customer Service after initially supporting it through ticket-volume, subject, and resolution-timeline analysis: wrote system prompts, advised on technical direction, liaised with external implementation partners, and supported product-owner hiring interviews - then proactively raised that the role had drifted into de facto project ownership of a department outside Data Science, and negotiated a scoped-back technical-advisor role with management

### Data, AI & Algorithm Intern - Philips Avent Experience Innovation (November 2024 - February 2025)
Eindhoven, Noord-Brabant, Netherlands
- Engineered an end-to-end data science pipeline — raw data processing, exploratory analysis, feature engineering, model prototyping, and on-device execution (R&D prototype only - never shipped in a product, no accuracy/early-warning figure available) — on time-series sleep-phase and respiratory data from a smart baby monitor, enabling detection of infant bed/wake times from as little as 7 nights of data despite the fragmented sleep patterns typical of young children
- Designed a statistical illness-detection model leveraging outlier detection over rolling statistical windows across specific sleep phases, collaborating closely with infant-sleep researchers to validate signals; the model was capable of flagging illness before symptoms were apparent to parents
- Wrote computationally efficient, lightweight algorithms optimized for on-device execution, structured for later reimplementation in a lower-level language at deployment
- Redesigned an on-device analytics dashboard concept for a baby monitor camera, enhancing parent-facing usability and device functionality
- Partnered cross-functionally with infant-sleep researchers and contributed to broader team ideation beyond the core scope of the role

### Financial Analyst - ING Belgium (July 2023)
Brussels, Belgium
- Returned for a summer role at the managing director's invitation following a strong prior internship (Feb-Jul 2022); onboarded and supported new summer interns on internal systems, fielding questions and providing guidance
- Led a GDPR data-cleaning project, ensuring personal data was deleted or anonymized in line with the bank's data-retention guidelines

### Financial Data Analyst Intern - Amazon, SCOT IPC Finance (January 2023 - June 2023)
Luxembourg
- Designed and built a self-service standardization platform (SQL + Excel) consolidating 9 financial entitlement methodologies (distance, spreading, transfer metrics) into one wiki/dashboard, adopted by ~15 cross-functional stakeholders and cutting finance-team dependency for ad hoc data requests
- Proposed and implemented a polynomial regression methodology for cost-curve modeling that replaced a flawed linear cost assumption; the $300M figure is the estimated "potential financial upside from improved product availability" on one project (use this wording, not "impact")
- Identified a statistical flaw in an existing inventory-spreading regression (misapplied "constant is zero" R² calculation), flagged it to stakeholders, and drove a review of the methodology
- Took full ownership of weekly EU/US inventory-transfer reporting to senior VPs for 3 weeks while manager was on leave, independently leading a cross-team audit of the transfer cost methodology after being challenged by a senior manager from another team
- Extracted and analyzed multi-million-row datasets via SQL to support lane-level transportation cost-benefit analysis across EU, US, Canada and India marketplaces
- Authored weekly EU5 inventory-position commentary reviewed by leadership up to C-suite; automated the AKU (average cost-per-unit) analysis that fed into a downstream ML forecasting model
- Audited capacity-constraint cost models across 40,000+ simulated data points, building regression-based marginal-impact estimates used to guide Buying and S&OP decisions

### Financial Analyst Intern - ING Belgium, Transport & Logistics Sector Coverage (February 2022 - July 2022)
Brussels, Belgium
- Supported portfolio management for Transport & Logistics sector clients (container shipping, rail, ports, aviation): financial modeling, credit analysis, covenant monitoring, and annual reviews
- Performed KYC and compliance reviews for corporate lending clients
- Led sector strategy research on Asia-focused port logistics trends and presented findings to internal stakeholders
- Contributed to a 4-person research team analyzing the container shipping industry to inform lending strategy in a specialized sub-sector

### Co-Owner - YoungViews (May 2020 - April 2021)
Meerlo, Limburg, Netherlands
- Co-founded a consultancy alongside studies to help SMEs strengthen their online presence during COVID-19, growing to 7 paying clients over roughly a year - a first hands-on experience with entrepreneurship
- Acted as marketing consultant to clients on social media campaigns and marketing strategy, and built client websites
- Hired and managed two freelancers (content videography/photography and web development) to deliver client work

### Marketing and Communications Intern - Toponderzoek (February 2019 - June 2019)
Horst, Netherlands
- Designed and ran an end-to-end quantitative market research project (problem definition, desk research, stakeholder interview, questionnaire design, sample-size calculation, SPSS analysis, reporting) surveying 171 respondents on engagement with a civic research panel
- Co-developed a social media strategy proposal and analyzed Facebook/Instagram ad performance (CPC/CPM) to benchmark cost-per-lead against national averages

### Marketing and Communications Intern - MIJNWERKPLEK / MIJNVORM (September 2017 - February 2018)
Swolgen, Netherlands
- First introductory internship, gaining initial experience working in a back office with small administrative tasks

<!-- Add more roles as needed -->

## Independent Projects
<!-- Projects outside of employment: freelance, open source, personal -->
- **Brain Tumor MRI Classification** (Deep Learning course group project, Tilburg University, Fall 2024): Built and compared CNN architectures (custom batch-normalized CNN tuned with Optuna, DenseNet121 and ResNet50 transfer learning) to classify brain MRI scans into 4 tumor classes (7,023 images). Led hyperparameter optimization, validation split design, and results analysis; best model reached 81.2% test accuracy.
- **Well-Being Prediction Learning Challenge** (Machine Learning course group project/Kaggle-style leaderboard competition, Tilburg University, May 2024): Predicted momentary self-reported well-being scores from behavioral data collected during a stress-reducing video game. Built preprocessing (dtype correction, time-based and MICE imputation, outlier removal) and feature engineering pipeline (embedding models, weekday/weekend and user-behavior features), and trained/tuned XGBoost and CatBoost models via GridSearchCV. Iteratively improved the leaderboard error score from 209.1 to 127.8.

## Technical Skills

### Programming & ML
- **Python** (2 years professional experience): TensorFlow, Keras, PyTorch, scikit-learn, XGBoost, CatBoost, sktime/aeon, librosa, Optuna, pandas, NumPy, Matplotlib
- **SQL** (2 years professional experience)
- **R** (foundational from one university course, "Research Skills: Programming with R", grade 8.0; since co-developed a Markov-chain attribution model with an external consultant at Sawiday, working through the methodology and implementation jointly rather than as primary day-to-day language)
- Deep learning (CNNs, transfer learning: VGG19, ResNet, DenseNet), time series classification (HIVE-COTE 2.0, MultiRocket+Hydra), hyperparameter optimization (Optuna/Bayesian optimization), audio feature engineering (MFCC, Mel Spectrogram)
- **PySpark + Databricks** (foundational, from MSc coursework, Tilburg University): exposure to distributed DataFrame processing and the Databricks platform in a university course setting; not yet applied in a professional project

### Domain Expertise
- Logistics & supply chain analytics (ING Belgium, Amazon, Sawiday)
- E-commerce / marketplace data (Amazon, Sawiday)
- Marketing measurement & attribution (MTA, incrementality testing, MMM, Markov-chain attribution modeling, ROPO analysis) (Sawiday)
- Data warehouse design & ETL architecture (Google Dataform: landing/staging/mart layers) (Sawiday)
- Production agentic AI / LLM systems: multi-agent orchestration (coordinator + specialist sub-agents), context engineering (layered sub-agents/skills/references), Agent Skills, MCP servers, tool calling, browser automation, eval-gated rollout, prompt-injection safeguards, PII redaction before LLM input (GDPR), GitOps deployment of agents (Sawiday)
- Built and deployed multiple Cloud Run microservices (B2B lead-generation tool, PO-confirmation PDF/CSV extraction service, HR hour-registration anomaly-detection pipeline) (Sawiday)

### Software & Tools
- Git / version control
- n8n
- Claude Code, Codex, Gemini
- Claude Managed Agents / Claude API (Sessions API, Agent Skills, multi-agent), `ant` CLI, MCP (custom Zendesk and ERP MCP servers with PII redaction), Browserbase, Zendesk (triggers, webhooks)
- GitHub Actions (CI/CD, nightly drift sync)
- Google Cloud Platform (BigQuery, Dataform, Vertex AI, Google Cloud Run)
- AWS (Athena)
- DBeaver (MySQL)
- Tableau
- Power BI
- Looker Studio
- Excel
- Confluence
- Jira
- Google Tag Manager
- Google Analytics
- Docker
- uv (Python package manager)
- ruff, black, mypy, bandit (Python lint/type/security tooling)
- Pydantic, Loguru
- Microsoft Graph API (Outlook mail/automation)
- Secrets management: Keeper, Google Secret Manager

## Volunteering
- **OJC Merlin** (youth centre, Meerlo, Netherlands) - ~7 years: assisted leadership with departmental operations, supported back-office event planning, and held sole responsibility for the cash audit

## Talks & Conferences
- **Speaker, DATA2026** (Eye Museum, Amsterdam, January 22, 2026) - added as an extra/late-addition speaker on the practicalities of Media Mix Modelling (MMM) and Multi-Touch Attribution (MTA), triangulated with incrementality testing, for a more comprehensive view of marketing performance - framed deliberately around practical application over methodology/hype
- Attended **NextGenData2026** (Barcelona) alongside Sawiday's external data science/engineering partner, The Data Story
- Attended Ecommerce AI club lunch-and-learn sessions (during Sawiday tenure)

## References
- Nino Weerman, AI & Data Science Lead, The Data Story
- Aditya Khaire, Senior Product Manager Tech, Amazon

More references available upon request.
