# Candidate Profile

<!-- SETUP: This file is populated by running /setup -->
<!-- After running /setup, all sections will be filled with your actual information -->

## Identity
- **Name:** Steff Vleeshouwers
- **Location:** Horst, Limburg, Netherlands
- **Phone:** +31623521660
- **Email:** s.vleeshouwers@outlook.com
- **LinkedIn:** https://www.linkedin.com/in/steffvleeshouwers
- **Languages:** Dutch (native), English (fluent), German (B2), Danish (B1)
- **Status:** Employed (Medior Data Scientist, Sawiday) - actively job-searching
- **Constraints:** Relocating to Denmark to be with partner - open to full relocation; Danish B1 and improving

## Education

| Degree | Period | Institution | Key Topics |
|--------|--------|-------------|------------|
| MSc Data Science and Society (thesis: "Music Genre Classification Using Time Series Classifiers: A Comparative Study Between Convolutional Neural Networks, HIVE COTE 2.0, and MultiRocket+Hydra", grade 7.5, judicium "met genoegen", avg. 8.32) | Feb 2024 - Feb 2025 | Tilburg University | Machine Learning, Deep Learning, NLP, Data Mining, Data Science Regulation & Law, Business Intelligence, Statistics & Methodology |
| Pre-Master Data Science and Society | Aug 2023 - Jan 2024 | Tilburg University | Bridging program into MSc |
| HBO Bachelor International Business, major Finance | Sept 2019 - July 2023 | HAN International School of Business (Hogeschool van Arnhem en Nijmegen) | Finance, International Economics, Accounting & Financial Reporting, Supply Chain Management, Data & Information Management |
| Mbo Medewerker marketing en communicatie (Niveau 4 / EQF 4) | 2016 - 2019 | Gilde Opleidingen (Roermond) | Marketing & communications |

## Professional Experience

### Medior Data Scientist - Sawiday (June 2026 - Present)
Rosmalen, North Brabant, Netherlands
- Led cross-functional design and delivery of a company-wide data warehouse (coordinating with IT, the team's data analyst, and an external data engineer from The Data Story) to consolidate external and internal data behind consistent definitions and historical records; built structured landing/staging/mart tables in Google Dataform on a daily schedule, ingested via webhook and API connections from external platforms, and prioritized cross-departmental data needs through direct stakeholder negotiation
- Built the data foundation for multi-touch attribution: gained access to marketing-platform APIs, built data dumps into Dataform mart tables, and constructed customer-journey tables with ROPO stitching for cross-device and online/offline measurement; supported development of an external consultant's R-based Markov-chain attribution model through code review and feature-development steering, set up the Vertex AI compute environment to run it, and presented resulting dashboards and modeling logic directly to marketing stakeholders
- Identified and closed a blind spot in marketing measurement - roughly 50% of revenue is offline with no bridge to online behavior - by designing a ROPO (Research Online, Purchase Offline) model using Google Tag Manager first-party email capture matched to GA4 user_pseudo_id and cross-referenced against the appointment system and CDP; in the process, found and fixed a server-side tagging bug that was leaking internal traffic into the data, lifting captured online purchase event journeys from ~73% to ~85%, and linked 40% of monthly offline purchases (~€1.7M/month in revenue) to prior online behavior - unlocking lead-discovery, cross-channel product-index, and improved marketing-attribution use cases

### Junior Data Scientist - Sawiday (April 2025 - June 2026)
Rosmalen, North Brabant, Netherlands
- Became the company's sole data scientist after the incumbent left (August 2025), reporting directly to the CFO with no technical lead in place; took ownership of professionalizing data science practice and reconciling ownership of script-based projects that sat between IT and Data Science
- Designed and shipped a GDPR-compliant B2B lead-generation tool combining governmental open-data APIs (company registration, activity code, address) with Google Maps API enrichment and targeted web scraping for contact validation, deployed self-service on Google Cloud Run for business stakeholders to query by location and radius - generated 100k+ qualified leads and contributed to 20 B2B sales within the first 3 months
- Led a cross-functional audit of five parallel product-association systems (Product Management, Marketing, IT, Data); built a revenue-attribution model joining web analytics to order lines showing suggestion blocks touched 7.7% of net revenue but caused only 0.38%, reframing the initiative from algorithm selection to fixing the underlying data (only 0.34% of 423,623 supplier-sent product relationships were usable) and halting an over-scoped A/B testing programme before further investment
- Led professionalization of the data science function: migrated credential management off ad hoc storage (including credentials previously committed to GitHub) onto Keeper/Google Secret Manager/.env, introduced Git-based CI/CD with branching, PR review and documentation, standardized linting, and adopted uv for reproducible Python package management
- Built a best-seller dashboard for Marketing by consolidating disparate product data sources in Tableau Prep Builder into a KPI-driven, product-profile-level ranking used to identify "best seller" and "our choice" merchandising picks
- Built and owned an end-to-end HR hour-registration anomaly-detection pipeline (Python) integrating the Dyflexis Business API and Polaris roster exports, applying a rule-based catalog (missing registrations, break violations, overtime outliers, contract mismatches) and routing flagged anomalies to the correct manager/HR checker via automated Microsoft Graph email alerts
- Automated purchase-order-confirmation processing into the ERP system via an n8n workflow with AI-based email classification (Outlook/Microsoft Graph) and a companion PDF/CSV extraction microservice on Google Cloud Run, with supplier-specific parsing and validation flags - projected to save up to 1 FTE of manual processing work
- Stepped up to lead a stalled Zendesk AI ticket-automation integration for Customer Service after initially supporting it through ticket-volume, subject, and resolution-timeline analysis: wrote system prompts, advised on technical direction, liaised with external implementation partners, and supported product-owner hiring interviews - then proactively raised that the role had drifted into de facto project ownership of a department outside Data Science, and negotiated a scoped-back technical-advisor role with management

### Data, AI & Algorithm Intern - Philips Avent Experience Innovation (November 2024 - February 2025)
Eindhoven, Noord-Brabant, Netherlands
- Engineered an end-to-end data science pipeline — raw data processing, exploratory analysis, feature engineering, model prototyping, and on-device deployment — on time-series sleep-phase and respiratory data from a smart baby monitor, enabling detection of infant bed/wake times from as little as 7 nights of data despite the fragmented sleep patterns typical of young children
- Designed a statistical illness-detection model leveraging outlier detection over rolling statistical windows across specific sleep phases, collaborating closely with infant-sleep researchers to validate signals; the model was capable of flagging illness before symptoms were apparent to parents
- Wrote computationally efficient, lightweight algorithms optimized for on-device execution, structured for later reimplementation in a lower-level language at deployment
- Redesigned an on-device analytics dashboard concept for a baby monitor camera, enhancing parent-facing usability and device functionality
- Partnered cross-functionally with infant-sleep researchers and contributed to broader team ideation beyond the core scope of the role

### Financial Analyst - ING Belgium (July 2023)
Brussels, Belgium
- Returned for a summer role at the managing director's invitation following a strong prior internship (Feb-Jul 2022); onboarded and supported new summer interns on internal systems, fielding questions and providing guidance
- Led a GDPR data-cleaning project, ensuring personal data was deleted or anonymized in line with the bank's data-retention guidelines

### Financial Analyst Intern - Amazon, SCOT IPC Finance (January 2023 - June 2023)
Luxembourg
- Designed and built a self-service standardization platform (SQL + Excel) consolidating 9 financial entitlement methodologies (distance, spreading, transfer metrics) into one wiki/dashboard, adopted by ~15 cross-functional stakeholders and cutting finance-team dependency for ad hoc data requests
- Proposed and implemented a polynomial regression methodology for cost-curve modeling that replaced a flawed linear cost assumption, estimated to impact one project by $300M
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
- **R** (foundational from one university course, "Research Skills: Programming with R", grade 8.0; since used professionally at Sawiday in a code-review/feature-steering capacity on an R-based Markov-chain attribution model, not as primary implementer)
- Deep learning (CNNs, transfer learning: VGG19, ResNet, DenseNet), time series classification (HIVE-COTE 2.0, MultiRocket+Hydra), hyperparameter optimization (Optuna/Bayesian optimization), audio feature engineering (MFCC, Mel Spectrogram)

### Domain Expertise
- Logistics & supply chain analytics (ING Belgium, Amazon, Sawiday)
- E-commerce / marketplace data (Amazon, Sawiday)
- Marketing measurement & attribution (MTA, incrementality testing, MMM, Markov-chain attribution modeling, ROPO analysis) (Sawiday)
- Data warehouse design & ETL architecture (Google Dataform: landing/staging/mart layers) (Sawiday)
- Built and deployed multiple Cloud Run microservices (B2B lead-generation tool, PO-confirmation PDF/CSV extraction service, HR hour-registration anomaly-detection pipeline) (Sawiday)

### Software & Tools
- Git / version control
- n8n (workflow automation/orchestration)
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
- [NAME], [TITLE], [COMPANY] ([EMAIL], [PHONE])

More references available upon request.
