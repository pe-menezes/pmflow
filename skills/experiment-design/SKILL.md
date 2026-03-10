---
name: experiment-design
description: >
  Use this skill when the user asks to "design an experiment",
  "set up an A/B test", "calculate sample size", "plan a test",
  "figure out how long to run a test", "prioritize my tests",
  "decide how to split users", "launch an experiment",
  "monitor test data", "call a test", "segment test results",
  "analyze experiment results", "iterate on a test",
  or needs help with the mechanics of running a rigorous experiment
  from test design through result analysis.
version: 1.0.0
---

# Experiment Design

Design, run, and analyze rigorous experiments. Covers the full test lifecycle: defining test parameters, calculating statistical requirements, minimizing build complexity, launching cleanly, monitoring data, calling tests complete, evaluating outcomes across segments, and iterating based on learnings.

## When to Use

- **Test setup**: Have a solution to test and need to define the test parameters
- **Sample size calculation**: Need to figure out how many users and how long
- **Test prioritization**: Have multiple tests ready and need to sequence them
- **Launch planning**: Need to plan the rollout — timing, ramping, user assignment
- **Monitoring**: Test is live and need to know what to watch and when to act
- **Calling a test**: Need to decide if the test is done and what the result is
- **Result analysis**: Test is complete and need to extract maximum learning
- **Iteration planning**: Test didn't win (or did) and need to decide what's next

## Prerequisites

Before using this skill, the PM should have:
- A defined strategic opportunity (use experiment-strategy if not)
- At least one solution with a clear hypothesis
- Defined evaluation metrics (primary, secondary, tradeoff, leading indicators)

Before starting, ask: **Output format**: What format for the final document? (docx, md, or pdf). Default: docx.

## Process

### Step 1: Define Test Parameters

For each test, establish the statistical foundation:

**Baseline metric**: The current performance of your primary metric for the control group. This is your starting point. Get this from historical data — the more data, the more accurate.

Example: If your primary metric is signup rate and historically 10% of homepage visitors sign up, your baseline metric is 10%.

**Minimum Detectable Effect (MDE)**: The smallest relative improvement you'd consider worth implementing. This is a business decision, not a statistical one.

Considerations:
- What's the minimum impact that justifies the implementation cost?
- What's realistic given the type of change? (UI copy change → 5-10% MDE. New feature → 15-30% MDE.)
- Smaller MDE = more samples needed = longer test. Find the balance.

Example: With a 10% baseline signup rate and a 10% MDE, you're testing whether the solution can move the signup rate from 10% to at least 11%.

**P-value threshold**: The probability of a false positive (calling a test positive when there's actually no difference). Standard is 0.05 (5%). Rarely need to change this.

**Statistical power**: The probability of correctly detecting a real difference. Standard is 0.80 (80%), meaning a 20% chance of missing a real effect. Rarely need to change this.

**Sample size calculation for percentage metrics** (signup rate, conversion rate, retention rate):

```
Sample size per variation = (Z_α/2 + Z_β)² × [p₁(1-p₁) + p₂(1-p₂)] / (p₂ - p₁)²

Where:
- Z_α/2 = 1.96 (for p-value of 0.05)
- Z_β = 0.84 (for 80% power)
- p₁ = baseline metric (e.g., 0.10)
- p₂ = baseline × (1 + MDE) (e.g., 0.11)
```

**Sample size calculation for continuous metrics** (average order value, time on page):

```
Sample size per variation = (Z_α/2 + Z_β)² × 2σ² / (MDE × baseline)²

Where:
- σ = standard deviation of the metric (from historical data)
```

Help the PM calculate this and understand the implications: total samples needed, daily traffic available, estimated test duration.

**Output**: Baseline metric, MDE, p-value threshold, power, required sample size per variation, estimated test duration.

### Step 2: Prioritize Tests (if multiple)

When multiple tests are ready, prioritize using Return on Time Invested (ROTI):

```
ROTI = (Estimated opportunity size) / (Time to build + Time to get results)
```

**Time to get results** = Sample size per variation × number of variations / daily eligible traffic

**Estimated opportunity size** = (Current metric value) × (Expected improvement %) × (Revenue or user impact per unit of metric) × (Time horizon)

**Time to build** = Engineering + design + QA time in days

Compare ROTI across tests. Higher ROTI = do it first. But also factor in:
- Dependencies between tests (run foundational tests first)
- Team capacity and skill match
- Seasonal timing constraints

**Sequential vs. simultaneous testing**: Running tests simultaneously against the same control requires fewer total samples (you reuse the control group). But it introduces interaction risk — if the tests affect similar parts of the experience, they can interfere with each other. Default to simultaneous when tests are independent, sequential when they overlap.

### Step 3: Minimize Build Complexity

The purpose of a test is to learn fast. Over-building test solutions is one of the most common mistakes.

**Four questions to reduce scope:**

1. **What platforms do I need to test on?** If 80% of traffic is mobile web, maybe skip the desktop build for the test. Test where the data is.

2. **What integrations are needed?** Can you mock or manually handle integrations during the test period instead of building full integrations?

3. **What resources are needed from other teams?** Can you reduce dependencies by using simpler implementations? (e.g., static content instead of dynamic, manual process instead of automated)

4. **How can we ship the test?** Can you use a feature flag, an experimentation platform, or a simple code change? Don't build production-grade infrastructure for a test.

The test solution should be good enough to accurately represent the user experience being tested, but nothing more. Polish can come after the test validates the hypothesis.

### Step 4: Plan User Assignment

How you split users between control and solution groups is critical to data quality.

**Core principle**: Split users as close to the test experience as possible. Only include users who will actually encounter the change. Users who are eligible for the test but never see it are "dead weight" — they dilute your sample and extend your timeline.

Example: If you're testing a new checkout page, don't include all site visitors in your test — only users who reach checkout. This dramatically reduces the sample size needed and speeds up results.

**Randomization**: Users must be randomly assigned. Any systematic pattern (first 50% get control, next 50% get solution) can introduce bias. Use proper randomization tools.

**Common assignment challenges:**

*B2B products with tiers*: Should you split by individual user, team, or account?
- Default to the lowest level possible (more samples, faster results)
- But move up if the feature creates interference between levels (e.g., a collaboration feature can't be split at the individual level — teammates need the same experience)
- Monetization experiments usually need account-level assignment

*Social/viral products*: When users in the solution group can influence control group users (e.g., sharing features, messaging improvements), consider:
- Geographic splitting (test in one market, control in a similar market)
- Assign at the network cluster level rather than individual
- Build minimal functionality for control users to respond to solution-group interactions

*Marketplaces with fixed supply*: When one side of the marketplace seeing the solution can affect the other side's results, you may need geographic or time-based splits rather than individual randomization.

**Client-side vs. server-side testing:**
- *Client-side*: Changes happen in the browser. Easy to implement, good for surface-level design changes. Can be slow to load and may cause flickering.
- *Server-side*: Changes happen on the server. Better for product-level changes, complex logic, and performance-sensitive tests. Requires more engineering effort.

### Step 5: Plan the Launch

Three categories of launch errors to prevent:

**1. Data interference** — external factors that bias your results

Four types to check:
- *Seasonal variation*: Is user behavior different this time of year? (holidays, school breaks, industry cycles)
- *Internal promotions*: Are there ongoing campaigns that could affect one variation more than the other?
- *Product-specific timing*: Does the product have natural cycles? (monthly resets, weekly patterns) If so, run the test for full cycle lengths.
- *External market factors*: Is a competitor launching something? Is there industry news that could affect behavior?

Mitigation: Map interference periods on a calendar. Launch during clean windows. If a test spans a cycle, run it for full cycle intervals (whole weeks, whole months).

**2. Launch authority** — who can greenlight a test launch

Default toward "beg forgiveness" over "ask permission." Centralized launch authority from senior leaders slows everything down and kills the iteration speed that makes experimentation valuable.

Better approach: peer review before launch (fellow PMs or data analysts review the test plan), decentralized launch authority (the PM or experiment owner launches), and no reverting to "ask permission" culture after a mistake — instead, fix the root cause.

**3. Infrastructure errors** — bugs in the test implementation

Use **ramping** to catch these: launch to a small % of users first (e.g., 10%), verify data is tracking correctly, then ramp to full traffic over 1-2 days.

When to ramp:
- New testing infrastructure or platform
- Testing in a new area of the product for the first time
- Sensitive metrics at risk (anti-metrics that could spike)

When to skip ramping:
- Well-established testing infrastructure
- Routine test in a familiar area
- Very short test window (high traffic, results in hours)

Ramping mechanics: Create three groups — solution variation, control variation, and a "not in test" group. The "not in test" group shrinks as you ramp. Don't change the split ratio between control and solution (always 50/50 between them).

**A/A tests**: Use only as a diagnostic tool when you suspect infrastructure problems — not as a routine practice. Running an A/A before every test is wasteful. If you need to validate infrastructure while also running a real test, use an A/A/B design (two control groups + one solution group).

### Step 6: Monitor the Test

**The primary rule**: Run the test until you reach your calculated sample size, then evaluate. Do not call a test early based on gut feeling.

**Why peeking is dangerous**: Every time you check the p-value before reaching full sample size, the measured p-value understates the actual probability of a Type 1 error. Continuously monitoring and stopping as soon as p < 0.05 gives you a 70-80% chance of a false positive — not 5%.

**What to monitor during the test** (without calling it):
- Is data tracking correctly? (Both variations receiving roughly equal traffic)
- Are there infrastructure errors? (Error rates, page load times, broken experiences)
- Are anti-metrics spiking dramatically? (If a critical metric drops significantly, consider pausing — but don't call the test based on incomplete data)

**When you can statistically justify calling early — Sequential Sampling:**

After every sample, calculate the absolute difference in win rate between solution and control. If the difference exceeds the threshold:

```
Threshold = ± 2 × √(N) / N

Where N = calculated sample size per variation
```

If the observed difference exceeds this threshold at any point, the test can be called early with statistical validity. This must be established as the calling method *before* the test starts. You cannot retroactively decide to use sequential sampling.

**Three reasons to extend a test beyond the calculated sample size:**

1. *Primary metric is close but not significant*: Recalculate sample size with a smaller MDE and extend.
2. *Secondary or tradeoff metric shows a non-significant but concerning trend*: Extend to see if it becomes significant — especially if a positive primary result has a potentially negative tradeoff.
3. *A specific user segment shows a different pattern*: Extend for that segment alone to get segment-level significance.

### Step 7: Call the Test and Evaluate Outcomes

**Calling the test**: After reaching the calculated sample size, evaluate:
- P-value < 0.05 AND statistical power ≥ 0.80 → **Positive or negative impact** (depending on direction)
- Otherwise → **Null impact** (not "no impact" — you simply couldn't detect an impact at this MDE)

**Turning outcomes into action** — use the outcome × tradeoff matrix:

| Primary metric result | Tradeoff positive/neutral | Tradeoff negative |
|---|---|---|
| **Positive impact** | Implement | Implement only if primary gain outweighs tradeoff loss. Consider iterating to preserve gain while mitigating tradeoff. |
| **Null impact** | Check for non-outcome benefits (performance, UX quality, behavior changes). Implement only if benefit justifies cost. | Don't implement. |
| **Negative impact** | Don't implement. Learn why. | Don't implement. Learn why. |

For null results with a positive secondary metric: investigate before claiming a win. Can you link the improvement to the test? Is there a better way to move that secondary metric directly?

### Step 8: Segment Results

Aggregate results hide important patterns. Segment your data to find them.

**Pre-test vs. post-test segmentation:**
- *Pre-test*: Which users should be in the test at all? Exclude irrelevant users (e.g., mobile users for a desktop-only test) to reduce noise.
- *Post-test*: Within your test population, how do subgroups differ? This is where unexpected insights live.

**Key segments to check**: traffic source, geography, visit frequency, actions taken, engagement level, demographics, platform, browser.

**What to do with conflicting segments:**

1. **Identify** which segments are in conflict and evaluate each independently
2. **Project forward** — how will the value from each segment change over time? (New users grow, existing users churn. Mobile is growing, desktop is shrinking.)
3. **Update the decision** — does the segment analysis change whether you should implement?
4. **Mitigate** — can you implement for the positive segment and protect the negative one? (e.g., gradual rollout, opt-out period, targeted experience)

**Watch for Simpson's Paradox**: When every subgroup shows one trend, but the aggregate shows the opposite. This happens when subgroups have very different sizes across variations. Always segment — if you only look at aggregates, you can make exactly the wrong decision.

### Step 9: Extract Maximum Learning

Don't stop at "it worked" or "it didn't." Run through this learning checklist for every test:

**Test outcomes (did the solution work as expected?):**
1. Were outcome metrics impacted as expected? If not, why?
2. Were any metrics unexpectedly impacted? If so, why?
3. Were leading indicators impacted as expected? If not, why?
4. Were leading indicators correlated to outcome metrics as expected? If not, why?

**Customer problem (was the problem correctly defined?):**
5. How should the "what" of the problem be updated?
6. How should the "who" be updated?
7. How should the "where" be updated?
8. How should the "why" be updated?

**Test parameters (was the test well-designed?):**
9. Did sample size and time to results match expectations? If not, why?
10. Did time to build match expectations? If not, why?
11. Does the estimated opportunity size match what we observed? If not, why?
12. Whose predictions were most/least accurate? How were their assumptions different?

### Step 10: Plan the Iteration

Three areas to iterate on — evaluate bottom-up (problem first, not test design first):

**1. Customer problem** (check first): Do the learnings suggest the problem was mis-defined? Is the "who," "what," "where," or "why" wrong or incomplete? If yes → redefine the problem, generate new solutions, redesign the test.

**2. Solution** (check second): Is the problem still valid, but the solution approach is wrong? If yes → generate alternative solutions for the same problem, redesign the test.

**3. Test design** (check last): Is the solution approach sound, but the test implementation had issues? Design flaws, infrastructure bugs, UX problems in the test version? If yes → fix the implementation and retest.

Most teams default to top-down iteration (fix the test design first) because it's fastest. This is a trap — it leads to repeatedly tweaking implementations while the underlying problem definition remains wrong.

**Iterating on wins (don't skip this):**
- **Explore newly uncovered problems**: Fixing one bottleneck creates the next. What's the new constraint? (Improved acquisition → now activation is the bottleneck)
- **Refine the winning solution**: The test version was minimum-viable. What assumptions in the solution haven't been validated? What can be optimized?
- **Expand scope**: If you used a provisional solution, decide whether to test the full version, test another provisional, or shut it down.

### Step 11: Generate the Experiment Design Document

Produce the document in the user's chosen format (default: docx). If docx, use the docx skill. If pdf, use the pdf skill. If md, write as markdown. Use the following structure:

```
# Experiment: [Name]
Date: [date]
Author: [PM name]
Strategic opportunity: [link to experiment-strategy doc]
Status: [Design / Live / Complete / Iterating]

## Hypothesis
If we [change], then [who] will [behavior], resulting in [metric improvement] because [rationale].

## Test Parameters
- Baseline metric: [value] ([metric name])
- MDE: [%]
- P-value threshold: [0.05]
- Statistical power: [0.80]
- Sample size per variation: [calculated]
- Number of variations: [2 or more]
- Estimated daily eligible traffic: [number]
- Estimated test duration: [days]
- ROTI: [calculated]

## Metrics
- **Primary**: [metric — this determines win/loss/null]
- **Secondary**: [metrics — additional positive signals]
- **Tradeoff**: [metrics — watch for negative impact]
- **Leading indicators**: [metrics — early signals]

## User Assignment
- Assignment level: [individual / team / account / geographic]
- Split: [50/50 / other]
- Eligibility criteria: [which users are included/excluded]
- Client-side or server-side: [choice + rationale]

## Launch Plan
- Ramp schedule: [immediate 100% / 10% → 50% → 100% over X days]
- Interference check: [seasonal, promotional, competitive factors]
- Anti-metrics to monitor during ramp: [metrics + thresholds for pausing]
- Calling method: [primary rule / sequential sampling]

## Build Plan
- Engineering effort: [days]
- Design effort: [days]
- Dependencies: [teams, tools, approvals]
- Scope cuts for test: [what's excluded from the test version]

## Pre-Mortem
| Risk | Preparation | Mitigation if triggered |
|------|------------|----------------------|
| [risk 1] | [prep] | [mitigation] |
| [risk 2] | [prep] | [mitigation] |

## Results (fill after test)
- Total samples: [control / solution]
- Duration: [days]
- Primary metric: [control value] → [solution value] (p = [value])
- Secondary metrics: [results]
- Tradeoff metrics: [results]
- Outcome: [Positive / Negative / Null]

## Segment Analysis
| Segment | Control | Solution | Difference | Significant? |
|---------|---------|----------|------------|-------------|
| [segment] | [value] | [value] | [%] | [yes/no] |

## Learning Checklist
[Answers to the 12 questions from Step 9]

## Decision
- **Action**: [Implement / Don't implement / Iterate]
- **Rationale**: [why]
- **Iteration plan**: [if iterating — what changes and why]
- **Next experiment**: [what follows from this learning]
```

## Common Mistakes

1. **No baseline metric**: Testing without knowing the current performance. You can't calculate sample size, MDE, or interpret results without a baseline.

2. **MDE too small**: Setting a 1% MDE "to detect any improvement" requires enormous sample sizes. Be realistic about what improvement justifies implementation.

3. **Peeking and stopping early**: The #1 statistical sin. If you continuously monitor p-value and stop at 0.05, your actual false positive rate is 70-80%. Use the primary rule or establish sequential sampling upfront.

4. **Including irrelevant users**: Every user in the test who never sees the change is noise that extends your timeline. Split as close to the experience as possible.

5. **No tradeoff metrics**: A positive primary result that destroys a tradeoff metric is worse than a null result. Always define what could go wrong.

6. **Top-down iteration**: After a loss, defaulting to "let's tweak the design" instead of questioning whether the customer problem was wrong. Always check problem → solution → test design, in that order.

7. **Ignoring segment differences**: Aggregate results that hide opposite effects in different user groups (Simpson's Paradox). Always segment.

8. **Not learning from wins**: Declaring victory and moving on without extracting learnings, refining the solution, or identifying the next bottleneck.

9. **Not documenting**: If the test isn't documented, the learning doesn't persist. Future teams will repeat the same experiments.

## Key Principle

The value of an experiment is not in its outcome — it's in the learning. A well-designed experiment that produces a null result teaches you something real about your users. A poorly designed experiment that produces a "win" teaches you nothing you can trust. Invest in the rigor of the design, and the learning will follow.
