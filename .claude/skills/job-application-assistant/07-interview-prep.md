# Interview Preparation Guide

<!-- SETUP: STAR examples are personalized by running /setup based on your actual experience -->

## STAR Format

Structure answers as: **Situation** (context), **Task** (your responsibility), **Action** (what you did), **Result** (outcome).

Keep answers to 1-2 minutes. Be specific. End with what you learned or would do differently.

## Ready-Made STAR Examples

<!-- These are populated by /setup from your actual experience. Below are templates showing the format. -->

### 1. The ROPO bridge (Sawiday, data pipeline building + business insight)
**S:** Roughly 50% of Sawiday's revenue happens offline (in-store), with no way to connect it back to the online behavior that led up to it - a blind spot nobody had previously measured.
**T:** As the team building out the data warehouse, I needed to find a way to bridge online and offline behavior so marketing could finally see the full customer journey.
**A:** I used Google Tag Manager to capture first-party email data on-site, matched it to GA4's `user_pseudo_id`, and cross-referenced that against the appointment system and CDP to build a Research-Online-Purchase-Offline (ROPO) model. While building it, I also found and fixed a server-side tagging bug that was leaking internal traffic into the data, which lifted captured online-purchase-event journeys from ~73% to ~85%.
**R:** The model linked 40% of monthly offline purchases (roughly €1.7M/month in revenue) back to prior online behavior, unlocking lead-discovery, cross-channel product-index, and improved attribution use cases the business had never had visibility into before.
**Use for:** "Tell me about a data project with measurable business impact", "Describe a technical problem you solved end-to-end", "Tell me about a time you found a data quality issue and fixed it"

### 2. Reframing the product-association audit (Sawiday, analytical pushback)
**S:** The business asked which algorithm to use for a basket-mismatch warning tool, after mapping turned up five separate, overlapping product-association systems built by different teams at different times.
**T:** I was asked to help pick an algorithm, but suspected the real problem was upstream of that question.
**A:** Instead of comparing algorithms, I built a revenue-attribution audit joining web analytics to order lines for a full quarter, measuring suggestion blocks at three levels of strictness (presence, click, click-and-bought). I also audited the underlying supplier relationship data feeding any future algorithm.
**R:** The audit showed the blocks were present in 7.7% of net revenue but caused only 0.38% of it, and that only 0.34% of 423,623 supplier-sent product relationships were usable. That reframed the conversation from "which algorithm" to "the relationship data is the constraint," and led me to halt an already-scoped A/B testing programme before further investment went into it.
**Use for:** "Tell me about a time you pushed back on how a problem was framed", "Describe a time you influenced a decision without direct authority", "Tell me about a time you stopped a project that wasn't going to work"

### 3. Becoming sole data scientist with no mandate (Sawiday, ownership under ambiguity)
**S:** I joined Sawiday as the second data scientist under a CFO with no technical lead in place. Four months in, the only other data scientist left, and I became the company's sole data scientist. Version control ran through OneDrive, credentials had been committed to GitHub, and ownership of several script-based projects was unclear between IT and Data Science.
**T:** Nobody assigned me to fix this, but the professionalization gaps were actively slowing down the projects I was accountable for.
**A:** I introduced secrets management (Keeper, Google Secret Manager, `.env`), set up Git-based CI/CD with branching and PR review, standardized linting, and adopted `uv` for reproducible Python package management - alongside continuing to deliver the data warehouse, MTA, and ROPO projects.
**R:** The data function now runs on version-controlled, reviewed code with no credentials in source control, and I was promoted from Junior to Medior Data Scientist roughly 14 months after joining.
**Use for:** "Tell me about a time you took initiative without being asked", "Describe stepping up when a colleague left", "Tell me about improving a process with no formal mandate to do so"

### 4. Owning inventory-transfer reporting while manager was on leave (Amazon)
**S:** As a Financial Analyst on Amazon's SCOT IPC Finance team, I was working on a deep-dive into inventory transfer costs at lane-level granularity. My manager then went on a 3-week holiday right as the project moved into its most complex phase, and separately a senior project manager from another team challenged our team's cost-base methodology for the transfer decks.
**T:** I had to take full ownership of the weekly reporting cadence to a group of senior and tenured stakeholders (including a weekly report to a Sr. VP), while also independently resolving the methodology challenge without my manager available.
**A:** I onboarded new data sources and built queries with our BIE (business intelligence engineer) to get lane-level cost data down to the specific transfer, validated the approach with two other teams, and kept updating and presenting three weekly decks on my own. When challenged on the cost-base methodology, I set up meetings directly with the senior project manager, walked him through our approach, and worked through the disagreement to alignment.
**R:** I was publicly recognized by the team's overall manager for handling the audit independently, and my colleague's written feedback noted I was "consistent on this delivery and high bar, even when his manager was OOTO for an extended period." The reporting scope I owned was later expanded to include the EU, Canadian, and Indian marketplaces.
**Use for:** "Tell me about a time you took ownership under pressure", "Describe handling conflict or being challenged by a stakeholder", "Tell me about working with high autonomy"

### 5. Fixing a flawed cost model with a $300M impact (Amazon)
**S:** While building out standardized financial entitlement models for Amazon's SCOT IPC Finance team, I noticed the existing methodology assumed a flat cost benefit regardless of the improvement percentage achieved (e.g., the same benefit for a 0-1% improvement as an 80-81% improvement), which didn't reflect reality.
**T:** I needed to validate whether this was a real flaw and, if so, propose and justify a better methodology to stakeholders who relied on these numbers for financial entitlement decisions.
**A:** I analyzed the existing regression, identified that a per-percentage-point weighting made more sense, and proposed switching to a polynomial regression instead. I also proposed actively cleaning the underlying data (removing constant 0%/100% outliers) to reduce noise, and got sign-off from the methodology's original owner before rolling it out.
**R:** The change was adopted and is estimated to have impacted one project by $300 million, and the data-cleaning proposal was also accepted and applied more broadly. I also separately caught a second methodological flaw (a misapplied "constant is zero" R² calculation) in a related model and flagged it for review.
**Use for:** "Tell me about a time you found and fixed a mistake others missed", "Tell me about a project with measurable business impact", "Describe a time you had to challenge an existing process"

<!-- Add more STAR examples as needed. Aim for 4-6 covering different competencies. -->

## STAR Candidates (Complete Manually)

### Promotion: Junior → Medior Data Scientist at Sawiday
**Source:** LinkedIn - Sawiday
**What happened:** Promoted from Junior to Medior Data Scientist after roughly 14 months (April 2025 to June 2026).
**Why it matters:** Answers "tell me about a time you grew quickly in a role" or "why should we hire you at this level".
**S/T/A/R:**
- **Situation:** I joined as Junior Data Scientist under a more senior data scientist. Four months in, that colleague left, leaving me the sole data scientist reporting directly to the CFO with no technical lead.
- **Task:** I had to keep delivering - and in practice, expand what the role covered - without anyone above me to hand off scoping or review decisions to.
- **Action:** Over the following year I led the company-wide data warehouse build, built the data foundation for multi-touch attribution, designed and shipped the ROPO bridge, and drove the professionalization work (secrets management, CI/CD, linting), while also owning smaller automation projects (HR anomaly detection, PO-confirmation processing).
- **Result:** That body of work - both technical delivery and the judgment to prioritize and professionalize under ambiguity - is what led to the promotion to Medior Data Scientist in June 2026.
**Use for:** "Tell me about a time you grew quickly in a role", "Why should we hire you at this level", "Tell me about taking on more responsibility than your title required"

### Co-Owner, YoungViews
**Source:** LinkedIn - YoungViews (May 2020 - April 2021)
**What happened:** Co-owned and ran a business for about a year.
**Why it matters:** Answers questions about ownership, initiative, entrepreneurship, or working without a manager.
**S/T/A/R:**
- **Situation:** COVID-19 hit small and medium-sized businesses hard, and many local SMEs had little or no online presence to fall back on.
- **Task:** Alongside my studies, I co-founded YoungViews to help SMEs strengthen their online presence during the pandemic - with no manager, existing client base, or playbook to follow.
- **Action:** I acted as marketing consultant to clients on social media campaigns and marketing strategy, built client websites, and hired and managed two freelancers (videography/photography and web development) to deliver work I couldn't do alone.
- **Result:** Grew the business to 7 paying clients over roughly a year - a first hands-on experience running a business end-to-end, including sales, delivery, and managing external contributors.
**Use for:** "Tell me about a time you worked without a manager", "Describe an entrepreneurial project", "Tell me about managing other people's work"

### Career pivot: Finance → Data Science
**Source:** LinkedIn timeline - Financial Analyst roles (ING Belgium, Amazon) followed by Tilburg University MSc Data Science and Society and subsequent Data Scientist roles
**What happened:** Moved from financial analyst positions into a structured career change toward data science via a pre-master and master's degree.
**Why it matters:** Answers "why did you change careers" or "why should we trust you in this new field" - a common friction point in career-change interviews.
**S/T/A/R:**
- **Situation:** Across my finance internships at ING Belgium and Amazon, the parts of the work I found most energizing weren't the finance content itself - they were building the regression models, catching a flawed methodology, and building the SQL/Excel platform that replaced nine separate manual processes.
- **Task:** I had to decide whether to continue on a finance track or make a deliberate, structured pivot toward the technical work I actually wanted to do more of.
- **Action:** I chose the latter: enrolled in a pre-master and then the MSc Data Science and Society at Tilburg University, building formal grounding in ML, deep learning, NLP, and statistics on top of the analytical and stakeholder-facing skills I already had from finance.
- **Result:** That combination - financial/business rigor plus formal data science training - is exactly what let me step into ambiguous, stakeholder-facing data science roles at Philips Avent and then Sawiday, where translating business problems into technical solutions is the core of the job.
**Use for:** "Why did you change careers", "Why should we trust you in this new field", "Tell me about a deliberate career decision"

### Master's thesis: Music Genre Classification Using Time Series Classifiers
**Source:** Tilburg University MSc thesis (Dec 2024), grade 7.5, judicium "met genoegen"
**What happened:** Designed and ran a comparative study benchmarking CNNs (VGG19, ResNet152V2, DenseNet169 via transfer learning) against two SOTA time series classifiers (HIVE-COTE 2.0, MultiRocket+Hydra) on the Free Music Archive dataset, including hyperparameter tuning with Optuna, systematic sampling-rate experiments, and computational efficiency analysis (training time, memory, accuracy trade-offs) under real hardware/memory constraints (GPU vs. CPU-only TSC training, HC2 runs up to 22 hours).
**Why it matters:** Strong evidence for "tell me about a data science project end-to-end," "how do you approach model selection," "tell me about working under resource constraints," or technical deep-dive questions on deep learning/time series methods.
**S/T/A/R:**
- **Situation:** Time series classification research had produced newer, purpose-built methods (HIVE-COTE 2.0, MultiRocket+Hydra) claiming state-of-the-art accuracy, but it wasn't clear whether they actually outperformed standard CNN transfer learning once realistic hardware and time constraints were factored in - a genuinely open question, not one with a settled answer in the literature.
- **Task:** For my thesis, I set out to run a rigorous, like-for-like comparison of CNN architectures (VGG19, ResNet152V2, DenseNet169 via transfer learning) against HIVE-COTE 2.0 and MultiRocket+Hydra on music genre classification from the Free Music Archive dataset.
- **Action:** I converted audio into image-based (Mel Spectrogram/MFCC) representations for the CNNs, tuned hyperparameters with Optuna, ran systematic sampling-rate experiments, and tracked not just accuracy but computational cost (training time, memory) across GPU and CPU-only runs - HC2 runs alone took up to 22 hours.
- **Result:** VGG19 on Mel Spectrogram features achieved the best accuracy (43.4%) and by far the best computational efficiency (~3 minutes vs. up to 22 hours for HC2), showing that industry-standard CNN transfer learning outperformed newer, more complex time series classifiers on this task while being far more practical to deploy. Grade 7.5, judicium "met genoegen".
**Use for:** "Tell me about a data science project end-to-end", "How do you approach model selection", "Tell me about working under resource constraints", "Walk me through a technical deep-dive on a project you led"

## Common Tough Questions

### "Why did you leave [previous company]?"
> I'm not leaving Sawiday because of the work - I've been promoted once already and led the data warehouse, MTA, and ROPO projects there. My partner and I are relocating to Denmark, so I'm looking for a role in the Copenhagen area that lets me keep building on that track record somewhere I can be based long-term.

### "You don't have [specific skill/experience]."
> Depends on the specific gap raised, but the honest pattern across my profile is: strong on Python/SQL/GCP/attribution and data-warehouse work, thinner on formal production ML-engineering/MLOps at scale (my ML depth is thesis-level plus lightweight on-device work) and on formal people management (never had direct reports). I'd acknowledge the gap directly, point to the closest adjacent experience I do have (e.g., deploying and owning multiple Cloud Run microservices in production), and note that building deeper MLOps skill is an active, named priority for me right now - not something I'm hoping to avoid.

### "Where do you see yourself in 5 years?"
> Continuing to grow as a hands-on data practitioner rather than moving into people management - broadening from my current marketing-measurement specialization into general data science, ML, and data engineering, and building real depth in production ML/MLOps. Ideally on a team with a technical lead or senior peer above me, so that scoping and estimates get sanity-checked before they eat into delivery time - that's a real, named growth area for me, not a hypothetical.

### "What's your biggest weakness?"
> Self-driven project scoping and estimation. In both roles I've had without a technical lead (Philips Avent, Sawiday), I had to independently work out scope, timelines, and stakeholders, and my own time estimates consistently ran long - because real time went into figuring out "what to do and how," not into the technical work itself. It's built genuine scoping and stakeholder-mapping skill through necessity, but I'm actively sharpening up-front estimation, and I look for teams with enough structure - or a technical lead - to sanity-check scope before it costs delivery time.

### "Why this company specifically?"
> Customize per company. Must reference: specific projects, company values, market position, or team structure. Never give a generic answer.

## Questions You Should Ask Interviewers

### About the Role
- "What does a typical week look like in this role?"
- "What would success look like in the first 6 months?"
- "What's the biggest challenge the team is facing right now?"

### About the Team
- "How big is the team, and how do you divide work?"
- "What does the development/project lifecycle look like, from idea to production?"
- "How do you onboard new team members?"

### About Tech & Growth
- "What's your current tech stack for [relevant area]?"
- "Is there room to grow into more architectural or strategic decisions?"
- "How does the team stay current with new tools and methods?"

### About Culture (use these to prevent disappointment)
- "How would you describe the team culture?"
- "What does professional development look like here?"
- "Is there flexibility for remote/hybrid work?"
- "What's the balance between development/new projects and maintenance work?"
- "How would you describe the leadership style in this team?"
- "What do people who thrive here have in common?"

## Phone/Video Interview Tips
- Have STAR examples written out (use this file)
- Keep a glass of water nearby
- Smile when speaking (it changes your tone)
- Ask for clarification if a question is vague
- It's OK to take 5 seconds to think before answering
- End with: "Is there anything else you'd like to know about my background?"

## After the Application (Best Practice)

### Follow-Up Etiquette
- **Don't call to "stand out"** or to learn more about the role post-submission - this risks a negative impression
- If the employer specified a timeline, respect it and wait
- If no timeline was given and significant time has passed (2+ weeks), a brief call to ask about status is acceptable
- If you have genuinely new, relevant information to share, a short follow-up is fine

### Thank-You Notes
- When you receive any update (interview invitation, rejection, or status update), send a brief thank-you message
- Express appreciation for their time and the process
- Keep it short (2-3 sentences)

## Roleplay Guidelines
When the user asks for interview practice:
1. Ask which role/company to simulate
2. Start with easy warm-up questions ("Tell me about yourself")
3. Progress to role-specific technical questions
4. Include 1-2 behavioral questions using the competencies from the job posting
5. End with a tough question or curveball
6. After each answer, give brief feedback: what worked, what to sharpen
7. Suggest which STAR example would work best for each question
