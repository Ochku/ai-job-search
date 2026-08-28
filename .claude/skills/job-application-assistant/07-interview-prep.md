# Interview Preparation Guide

<!-- SETUP: STAR examples are personalized by running /setup based on your actual experience -->

## STAR Format

Structure answers as: **Situation** (context), **Task** (your responsibility), **Action** (what you did), **Result** (outcome).

Keep answers to 1-2 minutes. Be specific. End with what you learned or would do differently.

## Ready-Made STAR Examples

<!-- These are populated by /setup from your actual experience. Below are templates showing the format. -->

### 1. [PROJECT_NAME] ([SKILL_DEMONSTRATED])
**S:** [CONTEXT - what was happening, what was the problem]
**T:** [YOUR RESPONSIBILITY - what you specifically needed to do]
**A:** [WHAT YOU DID - specific actions, tools, methods]
**R:** [OUTCOME - measurable results, adoption, impact]
**Use for:** "[QUESTION_TYPE_1]", "[QUESTION_TYPE_2]"

### 2. [PROJECT_NAME] ([SKILL_DEMONSTRATED])
**S:** [CONTEXT]
**T:** [YOUR RESPONSIBILITY]
**A:** [WHAT YOU DID]
**R:** [OUTCOME]
**Use for:** "[QUESTION_TYPE_1]", "[QUESTION_TYPE_2]"

### 3. [PROJECT_NAME] ([SKILL_DEMONSTRATED])
**S:** [CONTEXT]
**T:** [YOUR RESPONSIBILITY]
**A:** [WHAT YOU DID]
**R:** [OUTCOME]
**Use for:** "[QUESTION_TYPE_1]", "[QUESTION_TYPE_2]"

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
**S/T/A/R stub:**
- Situation:
- Task:
- Action:
- Result:

### Co-Owner, YoungViews
**Source:** LinkedIn - YoungViews (May 2020 - April 2021)
**What happened:** Co-owned and ran a business for about a year.
**Why it matters:** Answers questions about ownership, initiative, entrepreneurship, or working without a manager.
**S/T/A/R stub:**
- Situation:
- Task:
- Action:
- Result:

### Career pivot: Finance → Data Science
**Source:** LinkedIn timeline - Financial Analyst roles (ING Belgium, Amazon) followed by Tilburg University MSc Data Science and Society and subsequent Data Scientist roles
**What happened:** Moved from financial analyst positions into a structured career change toward data science via a pre-master and master's degree.
**Why it matters:** Answers "why did you change careers" or "why should we trust you in this new field" - a common friction point in career-change interviews.
**S/T/A/R stub:**
- Situation:
- Task:
- Action:
- Result:

### Master's thesis: Music Genre Classification Using Time Series Classifiers
**Source:** Tilburg University MSc thesis (Dec 2024), grade 7.5, judicium "met genoegen"
**What happened:** Designed and ran a comparative study benchmarking CNNs (VGG19, ResNet152V2, DenseNet169 via transfer learning) against two SOTA time series classifiers (HIVE-COTE 2.0, MultiRocket+Hydra) on the Free Music Archive dataset, including hyperparameter tuning with Optuna, systematic sampling-rate experiments, and computational efficiency analysis (training time, memory, accuracy trade-offs) under real hardware/memory constraints (GPU vs. CPU-only TSC training, HC2 runs up to 22 hours).
**Why it matters:** Strong evidence for "tell me about a data science project end-to-end," "how do you approach model selection," "tell me about working under resource constraints," or technical deep-dive questions on deep learning/time series methods.
**S/T/A/R stub:**
- Situation:
- Task:
- Action:
- Result: VGG19 (MSpec features) achieved best accuracy (43.4%) and by far the best computational efficiency (~3 min vs. up to 22 hours for HC2), demonstrating that industry-standard CNN transfer learning outperformed newer time series classifiers on this task while being far more practical to deploy.

## Common Tough Questions

### "Why did you leave [previous company]?"
> [PREPARE YOUR ANSWER - be honest, forward-looking, no negativity about former employer]

### "You don't have [specific skill/experience]."
> [PREPARE YOUR ANSWER - acknowledge the gap, bridge to adjacent experience, show willingness to learn]

### "Where do you see yourself in 5 years?"
> [PREPARE YOUR ANSWER - show ambition aligned with the role's growth path]

### "What's your biggest weakness?"
> [PREPARE YOUR ANSWER - genuine weakness with concrete mitigation strategy]

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
