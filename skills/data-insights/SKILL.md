---
name: data-insights
description: >
  Use this skill when the user asks to "analyze my data",
  "explore this dataset", "help me understand these numbers",
  "what does this data tell me", "find insights in this data",
  "investigate a metric drop", "help me with data analysis",
  "look at this CSV", "query my data", or needs help going
  from a data question to an actionable insight.
version: 1.0.0
---

# Data Insights

Guide a PM through exploratory data analysis — from formulating the right question to loading data, running analyses, interpreting results, and verifying accuracy. Produces actionable insights, not just charts.

## When to Use

- **Investigating a metric change**: "Signups dropped 15% last month — what's going on?"
- **Exploring user behavior**: "How are people using feature X?"
- **Validating a hypothesis with data**: "We think power users drive referrals — is that true?"
- **Preparing for a decision**: "We need data to support whether to invest in mobile or desktop"
- **Understanding a dataset**: "I exported this CSV from our analytics tool — help me make sense of it"
- **Ad hoc questions**: Any data curiosity a PM has about their product, users, or business

## Core Principle

Data analysis for PMs is not about writing perfect SQL or building dashboards — it's about asking the right questions and interpreting the answers correctly. The biggest mistake PMs make with data isn't technical — it's asking vague questions that produce vague answers. This skill prioritizes question quality over query complexity.

## Adapting to the PM's Level

This skill works for PMs at different levels of data fluency. Detect the level from context and adapt:

**PM who is new to data analysis**: Needs more guidance on what kinds of questions data can answer, how to interpret results, and what the numbers actually mean. Explain metrics, suggest follow-up questions, and flag common misinterpretations. Don't assume they know what a cohort is or why correlation isn't causation.

**PM who is comfortable with data**: Needs less hand-holding, more structure and rigor. Focus on sharpening the question, suggesting non-obvious analyses, and challenging assumptions about what the data shows. Skip the basics.

When in doubt, start with a clarifying question about their experience rather than assuming either way.

## Process

### Step 1: Define the Data Question

Ask the PM:
- **What are you trying to learn?** The specific question or curiosity. ("Why did retention drop?" / "Which features drive upgrade?" / "How do our user segments differ?")
- **What decision will this inform?** Data analysis without a decision context produces interesting charts that don't lead anywhere. Even if the decision is vague ("understand our users better"), naming it focuses the analysis.
- **What do you already know or suspect?** Existing hypotheses, hunches, or context. This prevents the PM from "discovering" what they already know and focuses the analysis on what's actually unknown.
- **Output format**: What format for the final document? (docx, md, or pdf). Default: docx.

**Sharpen the question**: Most PMs start with vague questions. Help them get specific:

- Vague: "How is our product doing?" → Specific: "What's our 7-day retention rate by acquisition channel for the last 3 months?"
- Vague: "Are users happy?" → Specific: "What percentage of users who completed onboarding are still active after 30 days?"
- Vague: "Why is growth slow?" → Specific: "At which step in the signup funnel is the biggest drop-off, and has it changed in the last quarter?"

The question should be specific enough that you'd know the answer if someone told you a number. If it's not, it's not specific enough.

**Question hierarchy**: If the PM has multiple questions, help them prioritize. Start with the question that most directly informs the decision. Other questions become follow-ups.

### Step 2: Identify and Load the Data

Help the PM figure out where the data lives and how to get it into the analysis.

**Common data sources for PMs**:
- CSV or Excel exports from analytics tools (Google Analytics, Mixpanel, Amplitude)
- Database exports (user tables, event logs, transaction records)
- Spreadsheets with manual data (survey results, competitive analysis, financial models)
- API exports from tools (Stripe, Intercom, HubSpot)

**Loading approaches** (from simplest to most powerful):

1. **Upload a CSV or Excel file**: The PM uploads the file directly. Simplest approach — works for most ad hoc analyses.
   - Limitation: file size caps. If the dataset is too large, suggest pre-aggregating (e.g., daily totals instead of individual events).

2. **Paste data directly**: For small datasets (< 100 rows), the PM can paste the data into the conversation. Quick and dirty but effective for small explorations.

3. **Connect to a database via MCP**: If available, connect directly to the data source. This enables real-time querying and avoids the export-upload cycle.

**Before analyzing, understand the data**:
- What does each column represent?
- What's the time range?
- What's the granularity? (per-user, per-event, per-day, aggregated)
- Are there any known data quality issues? (missing values, duplicates, test data mixed with real data)

If the PM can't answer these questions, help them explore: describe the dataset, count rows, check for nulls, look at value distributions. Understanding the data before analyzing it prevents garbage-in-garbage-out.

### Step 3: Clean and Validate

Before running the analysis, check the data quality. This step is often skipped and it's where most wrong conclusions come from.

**Automated checks to run**:
- **Duplicates**: Are there duplicate rows? If so, why? (double-counting inflates metrics)
- **Missing values**: Which columns have nulls? What percentage? Are they random or systematic? (If all churned users have null for a field, that null IS data)
- **Outliers**: Are there extreme values that could skew averages? (One user with 10,000 sessions will distort "average sessions per user")
- **Date ranges**: Does the data cover the expected time period? Are there gaps?
- **Test data**: Is there internal/test traffic mixed in? (Look for internal email domains, test account flags, suspicious patterns)

**Report data quality to the PM**: Before presenting any analysis, state what was found and cleaned. "I removed 47 duplicate rows and excluded 12 internal test accounts. The dataset covers Jan 1 - Mar 10 with no gaps."

If the data quality is poor (>20% missing values in key fields, significant duplicates, unclear definitions), flag this before proceeding. Bad data produces confident-looking charts that are wrong.

### Step 4: Run the Analysis

This is the core of the exploration. The approach depends on the question type.

**For "what happened?" questions** (metric changes, trends):
1. Show the metric over time — is the change sudden or gradual?
2. Segment by the most likely dimensions (channel, platform, user type, geography)
3. Look for correlations with other metrics that changed at the same time
4. Check for external factors (seasonality, holidays, product releases, marketing campaigns)

**For "who are they?" questions** (user segments, behavior patterns):
1. Define the segments clearly (what makes someone a "power user"? Be specific: ">5 sessions/week" not "uses it a lot")
2. Compare segments across key metrics
3. Look for the behavior that most differentiates segments
4. Check segment sizes — a pattern in 0.5% of users is interesting but not actionable

**For "why is this happening?" questions** (root cause, causation):
1. Start with correlation analysis — what metrics move together?
2. Check for confounders (users who do X also tend to be Y — is it X causing the outcome or Y?)
3. Look at the sequence of events — what happened first?
4. Compare users who experienced the issue vs. those who didn't — what's different?
5. **Flag the causation trap**: Correlation is not causation. Always note this when presenting findings. "Users who complete onboarding retain better" doesn't mean "forcing onboarding completion will improve retention." It might mean "motivated users both complete onboarding AND retain."

**For "should we do X?" questions** (decision support):
1. Frame as hypothesis: "If we do X, we expect Y to happen because Z"
2. Find data that supports or contradicts the hypothesis
3. Quantify the opportunity: how many users are affected? What's the potential impact?
4. Identify what the data CAN'T tell you — and recommend how to find out (experiment, interviews)

**Visualization guidance**:
- **Line charts**: Trends over time
- **Bar charts**: Comparisons across categories
- **Scatter plots**: Relationships between two metrics
- **Pie charts**: Composition (use sparingly — bar charts are almost always better)
- **Heatmaps**: Patterns across two dimensions (e.g., day of week × hour of day)
- **Funnel charts**: Sequential drop-off (signup → activation → retention)
- **Cohort tables**: Behavior over time by group (retention by signup month)

Always label axes, include time ranges, and note sample sizes. A chart without context is decoration, not analysis.

### Step 5: Verify Accuracy

Before presenting conclusions, verify the analysis. This step separates rigorous PMs from ones who share the first number they find.

**Three levels of verification**:

1. **Sanity check**: Do the numbers make sense? If the analysis says you have 10M users but you know the product has ~50K, something is wrong. Compare results against known benchmarks or existing dashboards.

2. **Code review**: If SQL or code was generated, review it. Common errors:
   - Wrong JOIN type (INNER vs LEFT — are you accidentally excluding users?)
   - Missing WHERE clauses (are you including test data or inactive accounts?)
   - Aggregation errors (AVG when you meant MEDIAN, COUNT(*) vs COUNT(DISTINCT user_id))
   - Time zone mismatches (data in UTC but analysis assumes local time)

3. **Alternative approach**: For critical analyses, run the same question a different way. If two approaches give the same answer, confidence goes up. If they disagree, investigate why.

**Ask the AI to explain its work**: When code is generated, ask for a step-by-step explanation. This makes errors visible and helps the PM learn. "Can you walk me through what this query does, step by step?"

### Step 6: Interpret and Contextualize

Raw numbers without interpretation are useless. This step turns data into insight.

**For every finding, answer three questions**:
1. **So what?** Why does this matter for the product, the user, or the business?
2. **Compared to what?** Is this number good or bad? Compare against benchmarks, historical performance, expectations, or industry standards.
3. **Now what?** What should the PM do with this information? What decision does it inform?

**Common interpretation traps to flag**:

- **Survivorship bias**: "Our active users love feature X!" — but what about the users who churned before using it?
- **Simpson's paradox**: A trend that appears in aggregated data but disappears (or reverses) when you segment. Always check segments before trusting aggregates.
- **Small sample fallacy**: "Users from Twitter convert 3x better!" — based on 12 users. Flag when sample sizes are too small for reliable conclusions.
- **Recency bias**: One week of data doesn't make a trend. How far back does the pattern go?
- **Correlation vs. causation**: Always flag this. Suggest experiments to establish causation when the data only shows correlation.
- **Cherry-picking**: If the PM asked 10 questions and only one gave a favorable answer, the 9 unfavorable ones are also data. Don't let them ignore inconvenient findings.

### Step 7: Suggest Follow-Up Analyses

Great data analysis raises more questions than it answers. After the main analysis, suggest 2-3 follow-up explorations:

- "This shows WHAT happened. To understand WHY, I'd suggest looking at [X]."
- "This pattern is strong for [segment A] but we didn't check [segment B]. Worth exploring."
- "The data shows correlation but not causation. To validate, consider running an experiment: [hypothesis]."
- "This metric looks good in aggregate but might be hiding segment differences. Worth breaking down by [dimension]."

Connect follow-ups to the decision context from Step 1. Don't suggest analyses for curiosity's sake — suggest ones that would change the decision.

### Step 8: Generate the Insights Document

Produce the document in the user's chosen format (default: docx). If docx, use the docx skill. If pdf, use the pdf skill. If md, write as markdown. Use the following structure:

```
# Data Insights: [Question / Topic]
Date: [date]
Author: [PM name]
Data source: [where the data came from]
Data range: [time period covered]

## Question
[The specific question being investigated, sharpened from Step 1]

## Decision Context
[What decision this analysis informs]

## Data Quality Notes
- Records analyzed: [count]
- Data cleaning: [what was removed/fixed and why]
- Known limitations: [gaps, quality issues, caveats]

## Key Findings

### Finding 1: [headline — the insight, not the metric]
[Explanation with supporting data, visualizations, and context]
- So what: [why this matters]
- Compared to: [benchmark or historical context]
- Confidence: [high/medium/low — based on sample size, data quality, and methodology]

### Finding 2: [headline]
[...]

### Finding 3: [headline]
[...]

## Interpretation & Caveats
[What the data shows vs. what it doesn't. Causation vs. correlation flags. Alternative explanations. Survivorship bias risks. Small sample warnings.]

## Recommended Actions
1. [Action based on findings — connected to the decision context]
2. [Action]
3. [Action]

## Suggested Follow-Up Analyses
- [Follow-up question 1 — what it would clarify and why it matters]
- [Follow-up question 2]
- [Follow-up question 3]
```

**Document tone**: Findings should be written as insights, not as data descriptions. "Power users (>5 sessions/week) retain at 85% vs. 23% for casual users, suggesting that driving session frequency may be the highest-leverage retention strategy" — not "The retention rate for users with >5 sessions is 85% and for users with <5 sessions is 23%."

## Common Mistakes

1. **Starting with the data instead of the question**: "I have this CSV, what can we learn?" produces unfocused analysis. Always start with "What decision are we trying to make?" and work backward to what data is needed.

2. **Trusting the first number**: The first analysis is usually wrong — or at least incomplete. Always verify, segment, and check for confounders before sharing findings.

3. **Conflating correlation and causation**: The most common and most dangerous mistake in PM data analysis. Always flag it. Always suggest experiments when causation matters.

4. **Ignoring sample size**: A 50% conversion rate based on 4 users is meaningless. Always report sample sizes alongside percentages.

5. **Skipping data quality**: Analyzing dirty data produces confident-looking wrong answers. Spend time understanding and cleaning the data before drawing conclusions.

6. **Over-aggregating**: Averages hide everything interesting. Segment by user type, time period, platform, geography — the interesting patterns are usually in the segments, not the aggregate.

7. **Analysis without action**: A beautiful chart that doesn't lead to a decision or next step was a waste of time. Every analysis should end with "therefore we should..."

8. **Presenting data without context**: "We had 10,000 signups last month" means nothing without context. Is that up or down? Compared to what? Is it good for this stage? Always provide a reference point.

9. **Confirmation bias**: Looking for data that supports a pre-existing belief and stopping when you find it. The most valuable analyses are the ones that surprise you. Actively look for data that contradicts the hypothesis.

10. **Not documenting methodology**: If someone asks "how did you get this number?" and you can't reproduce it, the analysis is unreliable. Always save the queries, note the filters, and document the approach.

## Key Principle

Data doesn't speak for itself — it needs an interpreter. The PM's job is not to produce charts but to produce insights that drive decisions. A single well-interpreted finding that changes a product decision is worth more than a hundred dashboards that nobody reads.
