---
name: interview-debrief
description: >
  Use this skill when the user asks to "debrief an interview",
  "synthesize interview notes", "summarize user research",
  "create a user value map", "analyze interview findings",
  or needs help extracting insights from user interviews
  and consolidating them into actionable patterns.
version: 1.0.0
---

# Interview Debrief & Synthesis

Synthesize notes from user interviews into structured takeaways. Two modes: single interview debrief and cross-interview synthesis with User Value Map generation.

## When to Use

- **After each interview**: Quick debrief to capture insights while fresh
- **After all interviews**: Full synthesis to consolidate patterns and generate User Value Map

## Mode 1: Single Interview Debrief

### Step 1: Gather the Notes

Ask the PM for:
- Raw notes or transcript (pasted, uploaded, or referenced from file)
- Interview number (e.g., "3 of 6")
- Problem hypothesis being tested

If an interview guide exists in the workspace, use it as reference.

### Step 2: Extract 4 Debrief Components

**1. User Profile**
- Relevant demographics/firmographics
- Product behaviors (usage patterns, segment)
- Which target audience attributes they match

**2. Problem Observations**
For each observation:
- Is the problem the same as hypothesized? If different, how?
- What alternatives do they use today?
- Why do they choose those alternatives?
- What goal are they trying to achieve?

Tag each: **supports hypothesis**, **contradicts hypothesis**, or **new finding**.

**3. Takeaways**

Three types:
- **Problem takeaways**: What aspect of the problem really matters beneath surface complaints?
- **Severity takeaways**: How serious? Consequences (time, money, stress, compliance, reputation)?
- **Alternative takeaways**: How bad are current workarounds? Indicates urgency and willingness to change.

**4. Process Assessment**

Recommend one of:
- **Continue as planned**: Not yet saturated, still getting new insights
- **Adjust questions**: Saturated on some topics, go deeper on new themes
- **Stop interviewing**: Patterns clear, diminishing returns

### Step 3: Generate Debrief Document

```
# Interview Debrief: [Interviewee Name/ID]
Project: [name]
Date: [date]
Interview #: [X of Y]

## User Profile
[demographics + behaviors + target attributes]

## Key Observations
### Supports Hypothesis
- [observation + evidence]
### Contradicts Hypothesis
- [observation + evidence]
### New Findings
- [observation + evidence]

## Takeaways
### Problem
[insight]
### Severity
[assessment with evidence]
### Alternatives
[current workarounds + quality]

## Recommendation for Next Interview
[continue / adjust / stop + rationale]

## Suggested Question Adjustments
[new questions to add, questions to drop]
```

## Mode 2: Cross-Interview Synthesis

Run after completing all (or most) interviews.

### Step 1: Gather All Debriefs

Ask the PM to provide all debrief documents. If they exist in workspace, offer to read them automatically.

### Step 2: 5-Step Synthesis

**1. Cluster by Problem**
Group by problem type. Identify most frequent, unexpected, and outlier findings.

**2. Patterns by User Profile**
- Different profiles have different problems?
- Same problem, different severity?
- Any "anti-audiences" (people without this problem)?

**3. Alternatives & Severity Patterns**
- Which problems have terrible alternatives (manual, broken, expensive)?
- Which have decent alternatives reducing urgency?
- Strongest opportunity = highest severity + worst alternatives

**4. Generate User Value Map**

```
## User Value Map

### User Profile (Refined)
[who the user actually is, based on evidence]

### User Problem (Refined)
- Main problem clusters: [list]
- Severity: [assessment]
- Current alternatives: [assessment]

### User Goals (Refined)
- Qualitative: [how experience improves]
- Quantitative: [metrics to track]
- Non-goals: [what we're NOT solving in v0]
```

**5. Project Assessment**
- **Proceed**: Hypotheses reinforced, clear direction
- **Pivot**: Problem different than expected, redefine scope
- **Kill**: No real user pain, or too niche
- **More research**: Ambiguous findings, specific gaps to fill

### Step 3: Generate Synthesis Document

```
# Interview Synthesis: [Project Name]
Date: [date]
Interviews completed: [X]

## Problem Clusters
### Cluster 1: [name]
- Frequency: [X of Y interviewees]
- Key evidence: [summary]

## Patterns by User Profile
[cross-reference]

## Alternatives & Severity Analysis
[most urgent problems]

## User Value Map
[refined map]

## Project Assessment
[proceed / pivot / kill / more research + rationale]

## Recommended Next Steps
- [ ] [action]
```

## Common Mistakes

1. **Overweighting memorable responses**: One vocal user ≠ pattern. Check frequency.
2. **Generalizing without segmenting**: "Users think it's expensive" — WHICH users?
3. **Missing cross-cutting themes**: Same need in different segments = strong signal.
4. **Skipping synthesis**: Interviews without synthesis is theater — busy calendar, no decisions.

## Key Principle

Debrief captures fresh insights. Synthesis creates leverage. Without both, user interviews don't inform decisions.
