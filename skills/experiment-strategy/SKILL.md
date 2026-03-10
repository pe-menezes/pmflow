---
name: experiment-strategy
description: >
  Use this skill when the user asks to "identify what to test",
  "find experimentation opportunities", "define a strategic opportunity",
  "map my growth model", "prioritize experiments", "ideate solutions",
  "plan an experiment", "what should we experiment on",
  "build an experimentation roadmap", or needs help going from a vague
  growth goal to a concrete, prioritized set of solutions ready to test.
version: 1.0.0
---

# Experiment Strategy

Go from a growth goal to a prioritized set of testable solutions. Covers the two foundational phases of experimentation: identifying strategic opportunities (what to test and why) and ideating solutions (how to solve it). Produces a structured experimentation brief ready to hand off to test design.

## When to Use

- **Starting a new experimentation initiative**: The PM knows they need to grow a metric but doesn't know what to test
- **Growth model mapping**: Need to understand the levers available before choosing where to experiment
- **Customer problem scoping**: Have data signals or user insights but haven't framed them as testable problems
- **Solution ideation**: Have a well-defined problem but need to generate a diverse set of solutions
- **Prioritization**: Have multiple ideas and need to decide which to pursue first
- **Experimentation roadmap**: Need to plan a quarter's worth of experiments

## Why Strategy Comes First

Most failed experiments don't fail because of bad statistics or poor test design — they fail because they tested the wrong thing. Ad hoc experimentation ("let's just test this idea") produces scattered learnings and inconsistent value. Strategic experimentation starts by understanding the growth system, identifying the highest-leverage customer problems, defining what success looks like, and only then generating solutions. This discipline is what separates teams that occasionally get wins from teams that systematically compound value.

## Process

### Phase 1: Identify the Strategic Opportunity

A strategic opportunity has three components: a strategy (where in the growth system), a customer problem (what's broken), and a business outcome (what improves if we fix it). All three must be defined before ideating solutions.

#### Step 1: Map the Growth Model

Help the PM understand their product's growth system by mapping three layers:

**1. Acquisition Loops (how new users arrive)**

Identify which loops drive growth:
- **Viral loops**: Users invite other users (direct invites, social sharing, word-of-mouth, collaborative features)
- **Content loops**: Content created in-product attracts new users through search or social (user-generated content, SEO, social distribution)
- **Paid loops**: Revenue funds acquisition spend (performance marketing, paid social, SEM, affiliate)

For each active loop, ask: What's the conversion rate at each step? Where does the loop leak most? What's the cost per acquired user?

**2. Retention & Engagement Loops (how users stay and deepen)**

Map the engagement cycle:
- What triggers bring users back? (notifications, habits, content updates, social triggers, workflow integration)
- What's the natural usage frequency? (daily, weekly, monthly, event-driven)
- What actions indicate deepening engagement vs. shallow usage?

Identify the activation moment — the experience that converts a new user into a retained user. This is often the highest-leverage point in the entire system.

**3. Monetization Model (how value is captured)**

Define four dimensions:
- **What** is monetized (features, content, access, services, data)
- **How** it's monetized (subscription, transaction, freemium, ads, marketplace commission)
- **How much** is charged (pricing tiers, per-unit pricing, bundling)
- **When** users pay (upfront, trial-then-pay, usage-based, milestone-based)

Map where the monetization model sits on the friction spectrum: low friction (ads, freemium) → medium friction (trials, soft paywalls) → high friction (upfront payment, enterprise sales).

**4. Defensibility / Macro Loops (what compounds over time)**

Identify which macro loops strengthen the product over time:
- Direct network effects (more users → more value per user)
- Cross-side network effects (more supply → more demand, and vice versa)
- Data network effects (more usage → better product through data)
- Economies of scale (more volume → lower cost per unit)
- Brand (more awareness → more trust → more conversion)

These loops are rarely the direct target of experiments, but understanding them helps prioritize which micro loops to strengthen.

**Output**: A simple diagram or structured list showing the product's growth system — acquisition loops, engagement loops, monetization model, and defensibility layers.

#### Step 2: Define the Customer Problem

A customer problem has four dimensions. Help the PM define each:

**What**: What is the specific pain, friction, or unmet need? Be concrete. "Users don't understand the value prop" is better than "onboarding is bad." "Users can't find relevant content after their first session" is better than "retention is low."

**Who**: Which users experience this problem? Not all users are equal. Define the segment: new vs. existing, free vs. paid, power users vs. casual, specific personas, geography, platform.

**Where**: Where in the product journey does this problem occur? Map it to a specific moment: first visit, activation, first value moment, repeat engagement, upgrade decision, churn risk.

**Why**: Why does this problem exist? What's the root cause? This is the hardest and most important dimension. Surface-level answers ("the UI is confusing") usually mask deeper issues ("users don't have a mental model for how the product works").

**Two paths to a customer problem:**

*From a user insight*: The PM heard something in interviews, saw behavior in session recordings, or received consistent support tickets. Help them move from the raw signal to a structured problem statement.

*From a data insight*: The PM spotted a drop-off in a funnel, a segment with unusually low retention, or a metric that's underperforming. Help them move from the data point to a hypothesis about what's causing it.

**Four common mistakes to catch:**
1. **Vocal minority bias**: A loud user segment complaining doesn't mean it's the most impactful problem. Check: how many users are actually affected?
2. **Unqualified users**: Users who were never going to succeed (wrong audience, wrong use case) will distort your problem definition. Check: is this a problem for your target user?
3. **Solutions masquerading as problems**: "We need a better onboarding wizard" is a solution. The problem is "users don't reach their first value moment within the first session." Always push to the underlying need.
4. **Analysis paralysis**: Spending months researching the perfect problem definition. If there's enough evidence to form a hypothesis, move forward and let the experiment teach you.

**Output**: A clear problem statement: "[Who] experiences [what problem] at [where in the journey] because [why]."

#### Step 3: Define Outcome Metrics

Define what success looks like if the customer problem is solved. Use three levels:

**Outcome metrics** (the real business impact):
- *Acquisition*: volume metrics (new signups, new accounts) + quality metrics (qualified leads, activation rate of new users)
- *Retention*: retention rate, activation rate, engagement depth, resurrection rate
- *Monetization*: revenue, breadth (% of users paying), depth (revenue per paying user)

Pick 1-2 outcome metrics that directly connect to the customer problem. If you're solving an activation problem, your outcome metric is activation rate or first-week retention — not revenue.

**Intermediate metrics** (leading indicators you can measure faster): Metrics that are correlated with the outcome but move sooner. Example: if the outcome is 30-day retention, the intermediate metric might be "completed 3 key actions in first week."

**Description metrics** (context that helps interpret results): Metrics that describe what's happening but aren't the target. Example: page views, time on page, click-through rate. These help explain *why* an outcome metric moved, but they shouldn't be the success criteria.

**Output**: A metric hierarchy: 1-2 outcome metrics, 2-3 intermediate metrics, and relevant description metrics.

#### Step 4: Prioritize the Strategic Opportunity

If the PM has multiple potential strategic opportunities, help them prioritize using three lenses:

**Impact potential**: How large is the addressable opportunity? Consider the number of users affected, the current performance gap (how far is the metric from its potential?), and the estimated business value if the problem is solved.

**Differentiation**: How much does solving this problem strengthen the product's competitive position? Does it deepen a defensibility loop? Does it create something competitors can't easily copy?

**Order of operations**: Does this opportunity need to be addressed before others can be effective? (Fixing activation before investing in acquisition. Fixing retention before scaling monetization.) Growth model dependencies matter — don't optimize downstream if upstream is broken.

**Output**: A ranked list of strategic opportunities with a brief justification for the top priority.

#### Step 5: Write the Strategic Opportunity Narrative

Combine the previous steps into a concise narrative that anyone on the team can understand:

> We're focused on [growth model area] because [strategic rationale]. Specifically, [who] experiences [what problem] at [where] because [why]. If we solve this, we expect to improve [outcome metric] by [estimated impact], which connects to [company goal]. We chose this over [alternative opportunities] because [prioritization rationale].

This narrative is the foundation for everything that follows — solution ideation, test design, stakeholder communication.

### Phase 2: Ideate Solutions

Now that the strategic opportunity is defined, generate a diverse set of solutions. The goal is to be narrow on the problem but wide on possible solutions.

#### Step 6: Generate Solutions Across the Spectrum

Great ideation produces solutions at every level of ambition, from simple optimizations to bold innovations. Use this spectrum to ensure diversity:

**1. Simplify**: Remove unnecessary steps, reduce cognitive load, eliminate friction. (Example: reduce form fields, remove a confirmation step, simplify copy.)

**2. Enhance**: Improve something that already exists. Better design, clearer messaging, faster performance. (Example: redesign the onboarding screen, improve loading speed, rewrite the value proposition.)

**3. Reorder**: Change the sequence of existing steps. (Example: show social proof before the signup form, move pricing info earlier in the journey, swap the order of onboarding tasks.)

**4. Restructure**: Change the overall architecture of the experience without adding new features. (Example: restructure the navigation, reorganize the dashboard, change the information hierarchy.)

**5. Add**: Introduce a new capability or feature. (Example: add a recommendation engine, introduce a free trial, create a referral program.)

**6. Reinvent**: Fundamentally rethink the approach. (Example: replace the onboarding flow with a product-led guided experience, switch from manual curation to algorithmic personalization, change the business model.)

For each solution, briefly note what it changes about the user experience and why it might solve the customer problem.

**Design modification techniques** to push thinking further:
- **Crossout**: Remove the most "obvious" element of a solution — does it still work? What takes its place?
- **10-foot test**: If a user saw this solution from 10 feet away (3 seconds of attention), would they understand what to do?
- **Minority report**: Design the solution for the 5% edge-case user — what do you learn about the mainstream experience?
- **Table flip**: What would you build if you had to start the product from scratch today?

#### Step 7: Apply the User Psychology Framework

For each solution, evaluate how it manages user psychology:

**Reducing negative friction:**
- *Physical friction*: How many steps, clicks, fields, screens? Can any be removed?
- *Cognitive friction*: How much thinking is required? Can choices be simplified, defaults set, information chunked?

**Amplifying positive motivation:**
- *Emotional triggers*: Does the solution create anticipation, curiosity, delight, or relief?
- *Rewards*: Does the user get immediate feedback, progress indicators, or a sense of accomplishment?
- *Motivational boosts*: Does the solution leverage social proof, scarcity, commitment, reciprocity, or authority?

Solutions that only reduce friction tend to produce incremental gains. Solutions that also amplify motivation tend to produce breakthrough results.

#### Step 8: Evaluate and Prioritize Solutions

**Define evaluation metrics for each solution:**
- *Primary metric*: The one metric that determines if the solution worked (from Step 3)
- *Secondary metrics*: Additional positive outcomes you hope to see
- *Tradeoff metrics*: Metrics that might be negatively impacted (anti-metrics to watch)
- *Leading indicators*: Early signals that the solution is working before outcome metrics move

**Initial evaluation using ICE:**
- **Impact** (1-10): If this works, how much does it move the needle?
- **Confidence** (1-10): How confident are you that it will work? (Based on evidence, not gut feel)
- **Ease** (1-10): How easy is it to build and test?

**Categorize solutions into risk quadrants:**
- **No-brainers** (high confidence, high impact): Do these first
- **Quick wins** (high confidence, lower impact): Fill gaps in the roadmap
- **Big bets** (lower confidence, high impact): Worth the risk for the potential payoff
- **Duds** (low confidence, low impact): Drop these

#### Step 9: Consider Provisional Solutions

For big bets or resource-intensive solutions, consider testing a lighter version first:

- **Painted door test**: Show the feature as if it exists (button, link, CTA) and measure interest — without building the actual feature. Validates demand before investing in build.
- **Wizard of Oz test**: The user experiences the full solution, but it's manually powered behind the scenes instead of automated. Validates the value proposition before investing in automation.
- **Limited feature release**: Build only the core of the solution — the minimum needed to test the hypothesis — and skip all the polish. Validates feasibility and core value.
- **Targeted user release**: Release the full solution but only to a carefully chosen subset of users who are most likely to benefit. Validates with the highest-signal audience first.

For each provisional approach, define: what assumption it tests, what you'll learn, and what the next step is if it succeeds or fails.

#### Step 10: Build the Experimentation Roadmap

Organize the prioritized solutions into a sequenced roadmap:

For each solution on the roadmap, define:
- **E**xperiment name and hypothesis
- **V**ariables being tested (what changes between control and solution)
- **E**valuation metrics (primary, secondary, tradeoff, leading indicators)
- **L**evel of effort (engineering days, design days, dependencies)
- **Y**ield expected (estimated impact on outcome metric)
- **N**ext steps (what happens if it wins? If it loses? If null?)

Sequence considerations:
- Run no-brainers first to build momentum and credibility
- Sequence dependent tests (don't test monetization if activation is broken)
- Balance quick wins with big bets — a portfolio approach
- Account for resource constraints and team capacity

### Step 11: Generate the Experimentation Strategy Document

```
# Experimentation Strategy: [Initiative Name]
Date: [date]
Author: [PM name]
Growth area: [acquisition / retention / engagement / monetization]

## Strategic Opportunity

### Growth Model Context
[Which part of the growth system this targets — acquisition loop, engagement loop, monetization model — and why it's the priority]

### Customer Problem
- **What**: [specific problem]
- **Who**: [user segment]
- **Where**: [moment in the journey]
- **Why**: [root cause]
- **Evidence**: [data points, user insights, or signals that validate this problem]

### Success Metrics
- **Outcome metrics**: [1-2 metrics that define success]
- **Intermediate metrics**: [2-3 leading indicators]
- **Description metrics**: [context metrics]

### Prioritization Rationale
[Why this opportunity over alternatives — impact potential, differentiation, order of operations]

### Strategic Narrative
> [The one-paragraph story: who has what problem, where, why, what improves if we fix it, why now]

## Solution Portfolio

### Solution 1: [Name]
- **Type**: [simplify / enhance / reorder / restructure / add / reinvent]
- **Hypothesis**: If we [change], then [who] will [behavior], resulting in [metric improvement] because [rationale]
- **ICE Score**: Impact [X] · Confidence [X] · Ease [X] = [total]
- **Risk category**: [no-brainer / quick win / big bet]
- **Provisional approach**: [if applicable — painted door / wizard of oz / limited feature / targeted release]
- **Evaluation metrics**:
  - Primary: [metric]
  - Secondary: [metric]
  - Tradeoff: [metric to watch]
  - Leading indicator: [early signal]
- **Estimated effort**: [eng days, design days, dependencies]
- **Next if win**: [what happens]
- **Next if loss**: [what to iterate on]

### Solution 2: [Name]
[same structure]

### Solution 3: [Name]
[same structure]

## Experimentation Roadmap

| Priority | Solution | Type | ICE | Effort | Dependencies | Target start |
|----------|----------|------|-----|--------|--------------|-------------|
| 1 | [name] | [type] | [score] | [days] | [deps] | [date] |
| 2 | [name] | [type] | [score] | [days] | [deps] | [date] |
| 3 | [name] | [type] | [score] | [days] | [deps] | [date] |

## Open Questions
[Assumptions that need validation, unknowns that could change the approach]
```

## Common Mistakes

1. **Skipping the growth model**: Jumping to solutions without understanding where in the system the problem lives. This leads to local optimizations that don't compound.

2. **Vague customer problems**: "Users don't convert" is not a customer problem. Push until you can name the specific friction, the specific user, and the specific moment.

3. **Solution-first thinking**: Starting with "let's test a new onboarding flow" instead of "what's preventing users from reaching their first value moment?" The solution should follow from the problem, not the other way around.

4. **All optimization, no innovation**: A portfolio of tiny UI tweaks will produce diminishing returns. Include at least one bold bet that could produce breakthrough learning.

5. **Ignoring order of operations**: Testing monetization improvements when activation is broken. Fix upstream problems before optimizing downstream.

6. **Single-solution ideation**: Generating one idea and building it. Great teams generate 10+ ideas and choose the best 3-4 to test.

7. **No tradeoff metrics**: Every solution can have unintended negative effects. If you don't define what to watch for, you won't notice when it happens.

8. **Skipping provisional solutions for big bets**: Investing months in building a complex feature without first validating the core assumption with a lighter test.

## Key Principle

The goal of experimentation strategy is not to find the right answer — it's to find the right question. A well-defined strategic opportunity with clear metrics and a diverse solution portfolio will produce valuable learning regardless of whether individual tests win or lose. The strategy compounds; individual test results don't.
