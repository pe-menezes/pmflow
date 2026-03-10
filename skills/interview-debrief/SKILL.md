---
name: interview-debrief
description: >
  Use this skill when the user asks to "debrief an interview",
  "synthesize interview notes", "summarize user research",
  "create a user value map", "analyze interview findings",
  or needs help extracting insights from user interviews
  and consolidating them into actionable patterns.
version: 2.0.0
---

# Interview Debrief & Synthesis

Synthesize notes from user interviews into structured takeaways. Separates real data (concrete facts, specific behaviors, commitments) from noise (compliments, vague opinions, hypothetical promises). Two modes: single interview debrief and cross-interview synthesis with User Value Map generation.

## When to Use

- **After each interview**: Quick debrief to capture insights while fresh (ideally within 30 minutes)
- **After all interviews**: Full synthesis to consolidate patterns and generate User Value Map

## Data Quality Framework

Before extracting insights, every piece of evidence must be classified. This is the most critical step — most interview debriefs fail because they treat all data as equally valid.

### Real Data (high confidence — base decisions on this)
- **Concrete facts about past behavior**: Things they actually did, specific instances they described, real workflows they walked you through
- **Specific numbers and timelines**: "I spent 3 hours last week", "This happened 4 times last month", "We've been doing this for 2 years"
- **Commitments they made**: Time they invested (showed up to a follow-up), reputation they risked (introduced you to their boss), money they put down (pre-order, deposit, paid pilot)
- **Existing workarounds**: Solutions they've already built or bought to solve this problem — shows they care enough to act

### Weak Data (low confidence — note it but don't build on it)
- **Compliments**: "That sounds really cool!", "I love that idea!", "You should definitely build that" — these feel great but mean nothing. People are polite. Deflecting compliments and getting back to facts is essential.
- **Generic claims**: "I usually...", "I always...", "Most people..." — these are identity statements, not behavior reports. Without a specific recent example, they're unreliable.
- **Future promises**: "I would definitely use that", "I'd pay $50/month for that", "I would tell all my friends" — people are overly optimistic about their future behavior. Discount heavily.
- **Hypothetical interest**: "That could be useful", "I could see myself...", "If it did X, I might..." — this is imagination, not evidence.
- **Ideas and feature requests**: "You should add X", "What if it did Y?" — don't take at face value, but note them. The request itself is weak data; the *motivation behind it* is strong data. Always ask "Why do you want that?"

### Emotional Signals (context markers — enrich other data)
When tagging observations, note the emotional context. The same statement carries very different weight depending on whether the person was neutral, frustrated, embarrassed, or excited:
- **Excited** — Marks genuine enthusiasm, but verify with concrete behavior
- **Frustrated / Angry** — Strong signal that the problem is real and painful
- **Embarrassed** — Often the most honest moments; people reveal things they wouldn't say calmly
- **Neutral / matter-of-fact** — May indicate low severity or acceptance of status quo

## Mode 1: Single Interview Debrief

### Step 1: Gather the Notes

Ask the PM for:
- Raw notes or transcript (pasted, uploaded, or referenced from file)
- Interview number (e.g., "3 of 6")
- Problem hypothesis being tested
- The top 3 learning goals for this conversation
- **Output format**: What format for the final document? (docx, md, or pdf). Default: docx.

If an interview guide exists in the workspace, use it as reference.

### Step 2: Extract 5 Debrief Components

**1. User Profile**
- Relevant demographics/firmographics
- Product behaviors (usage patterns, segment)
- Which target audience attributes they match
- Notable: Are they someone who has the problem, knows they have it, has tried to solve it, and has budget? (This is the profile of an ideal early user — flag if they match all four.)

**2. Data Classification**

Go through the notes and classify every meaningful observation:

For each piece of evidence, tag it with:
- **Data type**: fact, workaround, commitment, compliment, fluff, idea, emotional signal
- **Hypothesis alignment**: supports hypothesis, contradicts hypothesis, or new finding
- **Confidence level**: high (concrete past behavior), medium (specific but unverified), low (generic/hypothetical)

Strip out the noise. A debrief full of "They said they'd love it!" is worthless. Focus on what they actually *did*, *do*, and *have done*.

**3. Observation Tagging**

Use signal tags to categorize observations for easier cross-interview sorting:

- **Pain/Problem** — A specific difficulty they described from past experience
- **Goal** — What they're trying to achieve (the job-to-be-done)
- **Obstacle** — Something preventing them from solving the problem even though they want to
- **Workaround** — A makeshift solution they've cobbled together
- **Context** — Background information about their situation
- **Feature request** — A specific solution they suggested (note the request AND the underlying motivation)
- **Mentioned person/company** — Potential referral or competitor worth investigating
- **Follow-up needed** — Something to research or ask in the next interview

**4. Takeaways**

Three types:
- **Problem takeaways**: What aspect of the problem really matters beneath surface complaints? Is it the same problem as hypothesized, or different? How do they describe it in their own words?
- **Severity takeaways**: How serious is it? What are the concrete consequences (time lost, money wasted, stress, compliance risk, reputation damage)? Did they express strong emotion about it? Have they actively tried to solve it, or do they just complain?
- **Alternative takeaways**: How bad are their current workarounds? Are they spending time/money on existing solutions? Are those solutions adequate or terrible? The combination of high severity + terrible alternatives = strongest opportunity signal.

**5. Process Assessment**

Recommend one of:
- **Continue as planned**: Not yet saturated, still getting new insights
- **Adjust questions**: Saturated on some topics, go deeper on new themes that emerged. Suggest specific new questions to add and old ones to drop.
- **Narrow the segment**: Getting inconsistent data — might be talking to too diverse a group. Suggest how to tighten.
- **Stop interviewing**: Patterns clear, diminishing returns

Also assess conversation quality — meta-level review of the interview itself:
- Which questions worked well? Which fell flat?
- Did the PM accidentally lead the interviewee at any point?
- Were there missed opportunities to dig deeper on a signal?
- Were there moments where the PM talked too much or slipped into pitching?

### Step 3: Generate Debrief Document

Produce the document in the user's chosen format (default: docx). If docx, use the docx skill. If pdf, use the pdf skill. If md, write as markdown. Use the following structure:

```
# Interview Debrief: [Interviewee Name/ID]
Project: [name]
Date: [date]
Interview #: [X of Y]

## User Profile
[demographics + behaviors + target attributes]
[Note if they match the "ideal early user" profile: has problem + knows it + tried to solve it + has budget]

## Data Quality Summary
- Facts / concrete past behavior: [count]
- Commitments observed: [count and type — time, reputation, money]
- Compliments (discarded): [count]
- Generic / hypothetical claims (flagged): [count]
- Emotional signals: [count and types]

## Key Observations (sorted by confidence)
### High Confidence (concrete past behavior)
- [observation + exact quote if available + signal tag]
### Medium Confidence (specific but unverified)
- [observation + signal tag]
### Low Confidence (generic/hypothetical — noted but not actionable)
- [observation + signal tag]

## Hypothesis Check
### Supports Hypothesis
- [observation + evidence]
### Contradicts Hypothesis
- [observation + evidence]
### New Findings
- [observation + evidence]

## Takeaways
### Problem
[insight — in their words, not yours]
### Severity
[assessment with concrete evidence — time, money, emotion]
### Alternatives
[current workarounds + quality + what's missing]

## Learning Goals Update
1. [goal 1]: What we learned → [finding]. Confidence: [high/medium/low]
2. [goal 2]: What we learned → [finding]. Confidence: [high/medium/low]
3. [goal 3]: What we learned → [finding]. Confidence: [high/medium/low]

## Conversation Quality Review
- What worked: [questions/techniques that produced good data]
- What to improve: [missed signals, leading moments, pitch slips]

## Recommendation for Next Interview
[continue / adjust / narrow / stop + rationale]

## Suggested Question Adjustments
- Add: [new questions based on what emerged]
- Drop: [questions that are now saturated or unhelpful]
- Modify: [questions to rephrase for better data]

## Follow-ups
- [ ] [person to contact / thing to research / commitment to fulfill]
```

## Mode 2: Cross-Interview Synthesis

Run after completing all (or most) interviews.

### Step 1: Gather All Debriefs

Ask the PM to provide all debrief documents. If they exist in workspace, offer to read them automatically.

### Step 2: 6-Step Synthesis

**1. Separate Signal from Noise**

Before clustering, filter the data:
- Remove or demote all observations based on compliments, generic claims, and hypothetical promises
- Elevate observations backed by concrete past behavior, existing workarounds, and real commitments
- Flag any observation that appeared emotional — it carries extra weight
- If most of your data is compliments and hypotheticals, flag this to the PM: the interviews may have been poorly run (too much pitching, not enough digging into past behavior)

**2. Cluster by Problem**

Group high-confidence observations by problem type. For each cluster:
- Frequency: How many interviewees mentioned this? (count only concrete instances, not hypothetical agreement)
- Intensity: How strong were the emotions? How much time/money are they losing?
- Existing behavior: What workarounds have people built? (People who have already cobbled together solutions are the strongest signal — they care enough to act)

Identify most frequent, most intense, most unexpected, and outlier findings.

**3. Patterns by User Profile**
- Different profiles have different problems?
- Same problem, different severity?
- Any "anti-audiences" (people without this problem)?
- Who matches the ideal early user profile (has problem + knows it + tried to solve it + has budget)?

**Segment consistency check**: If feedback is all over the map — every interviewee has different must-have features and different must-solve problems — the PM probably doesn't have a segment problem. They have a "talking to too many different types of people" problem. Flag this clearly and help them identify which *sub-group* showed the strongest, most consistent signal.

**4. Alternatives & Severity Patterns**
- Which problems have terrible alternatives (manual, broken, expensive)?
- Which have decent alternatives reducing urgency?
- Where are people actively spending time or money to work around the problem?
- Strongest opportunity = highest severity + worst alternatives + most existing workaround behavior

**5. Commitment & Advancement Audit**

Review what commitments interviewees actually made (not what they said they'd do):
- **Time commitments**: Showed up to a follow-up, agreed to a pilot, spent time on a test
- **Reputation commitments**: Introduced the PM to colleagues/boss, agreed to be a reference
- **Financial commitments**: Pre-ordered, signed a letter of intent, put down a deposit

If zero interviewees made any real commitment, that's a major red flag — no matter how positive the conversations felt. Lots of "great meetings" with no advancement means zombie leads.

**6. Generate User Value Map**

```
## User Value Map

### User Profile (Refined)
[who the user actually is, based on evidence — not who you hoped they'd be]
[ideal early user characteristics observed]

### User Problem (Refined)
- Main problem clusters: [list — ranked by frequency × severity × workaround quality]
- Evidence strength: [how much of this is based on concrete facts vs. hypotheticals]
- Severity: [assessment with concrete data points]
- Current alternatives: [what they actually do today + quality assessment]

### User Goals (Refined)
- Qualitative: [how their experience improves — in their words]
- Quantitative: [metrics to track]
- Non-goals: [what we're NOT solving in v0]

### Commitment Signals
- [summary of real commitments observed across interviews]
- [or: "No real commitments observed — hypothesis not yet validated"]
```

**7. Project Assessment**
- **Proceed**: Hypotheses reinforced by concrete behavioral evidence, clear direction, commitment signals present
- **Pivot**: Problem is different than expected, but a real problem was found — redefine scope
- **Narrow**: Signal exists but is inconsistent — need to tighten the segment before proceeding
- **Kill**: No concrete evidence of real user pain. Lots of polite enthusiasm but no workarounds, no urgency, no commitments.
- **More research**: Ambiguous findings, specific gaps to fill — but specify exactly what to learn next

### Step 3: Generate Synthesis Document

Produce the document in the user's chosen format (default: docx). If docx, use the docx skill. If pdf, use the pdf skill. If md, write as markdown. Use the following structure:

```
# Interview Synthesis: [Project Name]
Date: [date]
Interviews completed: [X]

## Data Quality Overview
- Total high-confidence observations: [count]
- Total low-confidence observations (discounted): [count]
- Interviews with strong emotional signals: [count]
- Interviewees with existing workarounds: [count]
- Real commitments received: [count and types]

## Problem Clusters
### Cluster 1: [name]
- Frequency: [X of Y interviewees — concrete instances only]
- Intensity: [emotional signals + severity evidence]
- Existing workarounds: [what people already do]
- Key evidence: [summary with quotes]

### Cluster 2: [name]
[...]

## Segment Analysis
### Strongest signal sub-group
[who showed the most consistent, most intense, most actionable signal]
### Anti-audiences
[who clearly doesn't have this problem — useful for narrowing]
### Segment consistency
[is the data converging or diverging? If diverging, recommend narrowing]

## Alternatives & Severity Analysis
[ranked by: severity × alternative quality × existing behavior]

## Commitment & Advancement Summary
[real commitments vs. "great meetings" with no follow-through]
[zombie lead warning if applicable]

## User Value Map
[refined map — see template above]

## Project Assessment
[proceed / pivot / narrow / kill / more research + detailed rationale grounded in evidence]

## Recommended Next Steps
- [ ] [specific action — not generic "do more research"]
```

## Common Mistakes

1. **Treating compliments as validation**: "Everyone loved it!" means nothing. Check: did anyone actually *do* anything (sign up, pre-order, introduce you to their boss)?
2. **Overweighting memorable responses**: One vocal, passionate user ≠ a pattern. Check frequency across interviews.
3. **Counting opinions instead of behaviors**: "5 of 6 people said they'd use it" is weak. "4 of 6 people described spending 3+ hours/week on manual workarounds" is strong.
4. **Generalizing without segmenting**: "Users think it's expensive" — WHICH users? Break it down by profile.
5. **Missing cross-cutting themes**: Same need in different segments = strong signal.
6. **Skipping synthesis**: Interviews without synthesis is theater — busy calendar, no decisions.
7. **Being a learning bottleneck**: If insights stay in the PM's head and aren't shared with the team, the conversations were wasted. The debrief document IS the team's learning — share it immediately.
8. **Ignoring lukewarm responses**: A "meh" reaction is informative data. It means the problem isn't severe enough for this person. Don't only listen for enthusiasm.
9. **Not updating learning goals**: After each conversation, the top 3 learning goals should evolve. If they haven't changed after 3 interviews, the PM isn't learning from the conversations.

## Self-Diagnostic: Are the Interviews Actually Working?

Flag these warning signs to the PM:

- **PM talked more than the interviewee** → Conversations are pitches, not interviews
- **Most data is compliments and future promises** → Questions aren't anchored to past behavior
- **Every interviewee has a different "must-have"** → Segment is too broad
- **No interviewee has existing workarounds** → Problem might not be real (or audience is wrong)
- **An unexpected finding didn't change anything** → PM is confirming, not learning
- **No question felt scary to ask** → The important questions are being avoided
- **Lots of "great meetings" but no commitments** → Collecting compliments instead of evidence
- **Notes don't have exact quotes** → Key evidence is being lost

## Key Principle

Debrief captures fresh insights. Synthesis creates leverage. The goal is decisions grounded in concrete evidence — not a pile of "positive feedback" that makes everyone feel good but doesn't point anywhere. The most dangerous interview outcome is false confidence from compliments and hypotheticals.
