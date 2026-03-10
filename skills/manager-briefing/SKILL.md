---
name: manager-briefing
description: >
  Use this skill when the user asks to "prepare a manager briefing",
  "start a new project", "extract context from my manager",
  "understand why this project was prioritized", "align on project goals",
  or needs to structure hypotheses about strategic fit, user value,
  and business value for a new project.
version: 1.0.0
---

# Manager Briefing

Guide the PM through a structured conversation to extract context from their manager about a new project. Generate a document with explicit hypotheses to validate later.

## When to Use

At the START of any new project or feature, before user research or writing specs. First step of Opportunity Validation.

## The Framework

A manager briefing extracts and structures hypotheses across three components:

1. **Strategic Fit** — How does this project connect to company/product/team goals?
2. **User Value** — Who has the problem, what is it, and why does it matter?
3. **Business Value** — What business outcome does this drive, and how to measure it?

The goal is NOT to validate — it's to make hypotheses explicit so you know what to test next.

## Process

### Step 1: Gather Context

Ask the PM for basic project information:
- Project/feature name
- Who assigned it and why (if known)
- Any context already available (slack messages, docs, brief descriptions)

### Step 2: Strategic Fit — The 4 Levels

Walk through each level. If the PM doesn't know, mark as "hypothesis to validate."

**Level 1 — Company Mission & Vision**
- "What is your company's mission?"
- "How does this project connect to the long-term vision?"

**Level 2 — Company Strategy**
- "What are the company's current strategic priorities (this quarter/half)?"
- "Which priority does this project support?"

**Level 3 — Product Strategy**
- "What are the specific product goals that push this strategy forward?"
- "Where does this project fit in the product roadmap?"

**Level 4 — Team Goals**
- "What are your team's current OKRs or goals?"
- "Which team goal does this project directly support?"
- "What's the expected magnitude of impact?"

### Step 3: User Value — 4 Questions

1. **Who is the user?**
   - Demographics (B2C) or firmographics (B2B)
   - Product behaviors (segment, usage patterns, paid/free)

2. **What problem are we solving?**
   - Problem area (job to be done, cost, performance, accessibility)
   - Signal (data, complaints, quotes, NPS, support tickets)

3. **Why does this problem matter to the user?**
   - Severity (low/medium/high)
   - Number of users impacted
   - Current alternatives and how well they work

4. **What does success look like for the user?**
   - Qualitative: how does their experience improve?
   - Quantitative: metrics (adoption, satisfaction, usage)
   - Non-goals: what are we NOT trying to solve right now?

### Step 4: Business Value — 3 Questions

1. **Who are the business stakeholders?**
   - Decision makers (who needs to approve/align)
   - Supporting functions (CS, marketing, sales — who needs to be informed)

2. **What is success for the business?**
   - Qualitative: what business improvement do we expect?
   - Quantitative: metrics (revenue, retention, activation, conversion)
   - Non-goals: metrics NOT used to judge this initiative

3. **How does this connect back to strategy?**
   - Validate coherence with the 4 levels of strategic fit

### Step 5: Generate the Document

Produce a structured markdown document:

```
# Manager Briefing: [Project Name]
Date: [date]

## Strategic Fit
### Company Mission & Vision
[content]
### Company Strategy
[content]
### Product Strategy
[content]
### Team Goals
[content]

## User Value Hypothesis
### Target User
[who]
### Problem
[what + signal]
### Problem Importance
[severity + # users + alternatives]
### User Success Criteria
[qualitative + quantitative + non-goals]

## Business Value Hypothesis
### Stakeholders
[decision makers + supporting functions]
### Business Success Criteria
[qualitative + quantitative + non-goals]
### Strategic Connection
[how it ties back]

## What to Validate Next
- [ ] [specific hypothesis to test via user interviews]
- [ ] [specific hypothesis to test via data/funnel analysis]
- [ ] [specific alignment to confirm with stakeholders]

## Open Questions
[anything the manager couldn't answer]
```

Save to the user's workspace.

## Tone

- Act as a **structured interviewer**, not a passive note-taker.
- Push for specificity on vague answers: "Improve what aspect? For which users? How would you measure?"
- Gaps are fine — mark them as hypotheses to validate. The briefing surfaces gaps, it doesn't fill them.

## Key Principle

The manager briefing transforms a PM from "executor of what was assigned" into "owner of hypotheses that determine if this project should exist."
