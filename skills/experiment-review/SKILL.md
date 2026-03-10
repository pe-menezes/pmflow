---
name: experiment-review
description: >
  Use this skill when the user asks to "productize a test win",
  "get buy-in for implementation", "plan an experiment rollout",
  "measure actual impact", "communicate experiment results",
  "evangelize experimentation", "assess my experimentation program",
  "improve my experimentation process", "build experimentation culture",
  or needs help going from a test result to full implementation,
  measuring real-world impact, or managing experimentation as a program.
version: 1.0.0
---

# Experiment Review

Turn experiment results into real impact. Covers the post-test lifecycle: getting stakeholder buy-in, planning implementation, measuring actual impact versus test impact, communicating results effectively, and managing experimentation as an ongoing program that improves over time.

## When to Use

- **After a winning test**: Need to get buy-in and plan implementation
- **Implementation planning**: Deciding between full and partial rollout
- **Impact measurement**: Need to understand whether test results held up in production
- **Communication**: Need to share results with the team or broader organization
- **Program assessment**: Want to evaluate how the experimentation program is performing
- **Culture building**: Want to strengthen experimentation practices across the organization
- **Maturity check**: Want to understand where the program is and what to invest in next

## Process

### Part 1: Productizing Wins

#### Step 1: Get Decision-Maker Buy-In

A winning test doesn't automatically get implemented. You need to navigate organizational friction. Two types of resistance to prepare for:

**1. Preconceived notions**: Decision makers who "already know" what users want, and the test results contradict their beliefs. Their intuition feels more real than your data.

**2. Risk aversion**: Decision makers who are worried about potential negative effects, even when the data shows a positive result. They focus on what could go wrong, not what the data shows.

**Five principles for building a convincing case:**

1. **Don't assume others understand the data.** Walk them through it. Show the baseline, the change, and the result in plain language. Avoid statistical jargon unless they're fluent in it.

2. **Don't over-inflate the data.** Present conservative estimates. If you round up or cherry-pick the best segment, you'll lose credibility when reality is less rosy.

3. **Don't gloss over red flags.** If there were concerning tradeoff metrics or segments that didn't respond well, address them proactively. This builds trust and prevents surprises.

4. **Don't wait until results come in to think about how to present them.** Build relationships with decision makers early. Share the hypothesis, the test plan, and interim observations. By the time results arrive, they should be invested in the answer.

5. **Don't be constrained to just the data.** Connect the results to the strategic opportunity, the customer problem, the company strategy. Data tells them it works; narrative tells them why it matters.

Use the story-builder skill if the implementation case needs a full narrative for leadership.

#### Step 2: Decide Full vs. Partial Implementation

**Full implementation**: Production-grade solution distributed to all users. Captures maximum value. Usually requires additional engineering to clean up the test version.

**Partial implementation**: Ship the test version as-is to all users, but defer the polish. Captures most of the value faster, but creates technical and experience debt.

**When to go partial:**
- Resource constraints make full implementation slow (months, not weeks)
- 80% of the value comes from 20% of the implementation (the core works; the edge cases can wait)
- Speed matters more than polish right now

**Risks of partial implementation:**
- Inconsistency in the user experience (test version + production version coexist)
- Complexity in the codebase (temporary solutions become permanent)
- Debt compounds — every partial implementation makes the next one riskier

**The implementation plan has two components:**

1. **Initial implementation decision**: How much to build now based on the benefit-cost tradeoff. Chart the relationship between degree of implementation and four factors: benefit captured (high early, diminishing returns), cost (grows with complexity), inconsistency risk (grows with partial approaches), and system complexity (grows with mixed implementations).

2. **Path to full implementation**: A timeline for addressing the debt. If you go partial, commit to a plan that specifies when and how the remaining work gets done. "We'll get to it later" means it never happens.

#### Step 3: Understand Test Impact vs. Actual Impact

The impact you measured in the test is almost certainly not the impact you'll see in production. Five reasons why:

**1. Statistical significance effects**: A test showing a 10% MDE doesn't mean the actual improvement is exactly 10%. It means you can be confident the improvement is at least 10%. The true improvement could be lower — especially if the result was just barely significant.

**2. Novelty effects**: Users react to change itself, not just the quality of the change. A new design gets extra attention simply because it's new. This novelty wears off, and the long-term impact settles lower than the test showed.

**3. Engagement bias**: Users in the test were actively engaging with the product during the test window. They may be more active than the average user who will see the solution after implementation. This can inflate test results.

**4. Confounding factors**: If multiple solutions are implemented close together, they can cannibalize each other's impact. Three tests each showing +5% doesn't mean +15% total — it might be +8% combined.

**5. Pull-forward effects**: Some solutions don't create new behavior — they just make existing behavior happen sooner. A CTA that accelerates paid conversion might show a big short-term win, but long-term conversion converges with the control. Still valuable (earlier revenue), but less than it appears.

**One factor that increases actual impact**: The test version was minimum-viable. The full, polished implementation may perform incrementally better. But this rarely compensates for the five factors above.

#### Step 4: Measure Actual Impact

**Holdout tests**: Keep a small control group that doesn't see the implemented solution. This provides a counterfactual — what would have happened without the change.

*When holdout tests are worth it:*
- Performance marketing (need to know exact ROI per channel to allocate spend)
- Business vs. user tradeoffs (need a solid number on the business value to justify user experience costs)
- Validating leading indicators (need to confirm that the metrics you used as proxies actually predict long-term outcomes)

*When holdout tests aren't worth it:*
- Routine product improvements (the overhead doesn't justify the precision)
- When you'd need to maintain the holdout for months to see meaningful data
- When the holdout creates a bad user experience that could drive churn

*Cumulative holdout tests*: Instead of holding out users per experiment, hold out a group from all changes in a category (e.g., all monetization changes this quarter). Simpler to maintain, measures batch impact, but doesn't attribute to individual tests.

**Alternatives to holdout tests:**

1. **Backoff tests**: Fully implement, then later remove the change from a small group. Easier to run, good at detecting novelty effects, but can frustrate users who lose a feature.

2. **Cohort analysis**: Compare user cohorts from before and after implementation. Track retention curves, conversion curves, or engagement by cohort. Good for retention and monetization. But can be biased by other changes happening simultaneously.

3. **Time-smoothed metrics**: Smooth daily/weekly metrics over 7-day, 28-day, or 90-day windows to see trends before and after implementation. Reduces noise. 7-day smoothing shows weekly patterns, 28-day shows monthly trends, 90-day shows quarterly direction. The right window depends on the metric cycle.

4. **Conservative estimation**: Take the test impact, then discount for known factors:
   - Reduce by estimated confounding factor overlap (e.g., -20% for other initiatives affecting the same metric)
   - Reduce by estimated pull-forward effect (e.g., -20% for short-term acceleration vs. long-term impact)
   - Multiply by (1 - p-value) to risk-adjust for statistical uncertainty
   - This gives a defensible, conservative number to share with the organization

### Part 2: Communicating Results

#### Step 5: Educate the Organization

The learning from experiments is only as valuable as the number of people who can act on it. Three methods, from most detailed to most practical:

**1. Interactive library** (most detailed, least practical)

Capture everything:
- Planning: strategic opportunity, initial evidence, solutions ideated, prioritization criteria
- Solution details: screenshots, build process, platform used
- Test details: launch timing, calling criteria, infrastructure issues, iterations
- Results: learning checklist answers, implementation decision, measured outcomes, user feedback

Make it searchable (keyword search), sortable (by date, metric, outcome, growth area), and standardized (consistent format across all experiments).

**2. Experimentation review sessions** (balanced)

Regular in-person meetings where all experiments — in-progress and completed — get a readout. Not ad hoc, not just for big wins. Every experiment gets airtime.

Keep them disciplined (consistent format), regular (weekly or biweekly), and relevant (only people directly working in experimentation or adjacent growth initiatives).

Format per experiment:
- Hypothesis (1 sentence)
- What we tested (1-2 sentences)
- What we observed (key metrics, 2-3 data points)
- What we learned (the "why" behind the data)
- What's next (implement, iterate, or move on)

**3. Charter principles** (most practical, least detailed)

A short list of foundational learnings that the team has accumulated over time. These are the big, durable insights that should influence every initiative.

Examples:
- "Short-term friction in onboarding drives long-term retention" (so don't keep removing steps)
- "Users need to experience our value prop, not read about it" (so stop writing explanatory emails)
- "One-size-fits-all landing pages don't work across content categories" (so segment by intent)

Charter principles should be foundational (simple but specific), dynamic (updated as new learnings come in), and pervasive (known by everyone on the team, included in onboarding).

#### Step 6: Evangelize Experimentation

Evangelism goes beyond education — it's about building organizational buy-in and participation in experimentation.

**Regular written updates** (baseline — keep the drum beating):
- Use whatever channel the org already uses (Slack, email, wiki)
- Keep it light and scannable — headline, key metric, one insight, link to details
- Give credit to people who helped — engineers, designers, stakeholders from other teams
- Don't over-communicate details; make it easy to follow up for more

**Interactive readouts** (lean in — for significant moments):

When you have a big win, an unexpected learning, or a result that changes how the org thinks about users, do more than a Slack post:

- **Focus on learnings, not actions.** "This is what we learned about user behavior" is more compelling than "this is what we shipped."
- **Connect to the user experience.** Show the user journey, not just the metric change. Engage the right brain alongside the left brain.
- **Make it interactive.** "Before I show the results — how do you think users reacted?" Gamification keeps people engaged and invested.
- **Show how people can get involved.** Lower the barrier to participation. People don't contribute because they don't know how or when.

### Part 3: Managing the Experimentation Program

#### Step 7: Assess Program Maturity

Experimentation programs evolve through three phases. Help the PM identify where they are:

**Phase 1: Individual teams** (early)
- Experimentation happens within one team (usually growth or product)
- Focus on building initial capabilities and getting reps
- Risk: staying siloed, no cross-team learning

Transition signal: the team has a repeatable process, learnings are starting to be useful to other teams.

**Phase 2: Centralized** (growing)
- A dedicated experimentation function serves multiple teams
- Best practices are standardized, tools are shared
- Risk: bottleneck — everyone depends on the central team

Transition signal: demand outpaces central capacity, individual teams start running their own experiments.

**Phase 3: Distributed** (mature)
- Individual teams run their own experiments with shared tools and standards
- Central team becomes a center of excellence — training, tooling, complex stats
- Risk: quality drift, interference between teams' experiments

**Common mistakes at each phase:**
- Phase 1: Experimenting before the product is ready (no product-market fit), expecting ROI immediately, starting with tests that are too big or too small, no data fluency
- Phase 2: Over-centralizing and creating bottlenecks, not investing in training other teams
- Phase 3: Losing quality standards, perverse incentives, not managing test interference

#### Step 8: Evolve the Experiment Portfolio

The mix of experiments should change as the program matures:

**Early (post-PMF)**: Heavy on optimization (low-hanging fruit), light on innovation (big bets). The product is under-optimized, and the team needs reps. But don't abandon big bets entirely — they're the best source of learning.

**Growing**: Shift toward more big bets. Low-hanging fruit dries up. Big bets create macro improvements and, as a side effect, create new low-hanging fruit. Start introducing validation testing — putting product releases through A/B tests before full launch.

**Mature**: Big bets dominate the portfolio. Low-hanging fruit runs in the background (potentially automated). Validation testing becomes standard for all major releases. The divide between what customers want and what you think grows at scale — continuous disruption from within is the only way to stay ahead.

**The experience curve**: As you run more experiments, invest in two types of experience:

1. *Reducing cost per experiment*: Reduce dependencies on other teams (build internal capabilities, use provisional solutions more aggressively, build pre-mortems into the process), invest in infrastructure that empowers self-service experimentation.

2. *Expanding what you can experiment on*: Test all product releases (not just new ideas), test more innovative solutions (not just optimizations), expand to new parts of the product or business.

#### Step 9: Avoid Perverse Incentives

Measuring experimentation is hard, and measuring it wrong creates toxic incentives. Four traps:

**1. Tracking quantifiable value**: Leads to over-investing in measurement, pursuing quick wins over long-term learning, and inflating test results. Instead → use conservative estimation and don't tie team performance to experiment revenue attribution.

**2. Claiming credit independently**: Experimentation is a catalyst for other teams' success, not an independent value creator. Claiming full credit for wins destroys collaboration. Instead → frame experimentation as assists, not goals. Share credit generously.

**3. Reducing success to a single metric**: "Number of tests run" → teams run lots of garbage tests. "Win rate" → teams avoid risky tests. "Total value" → teams game estimates. Instead → use multiple metrics in tandem (see Step 10).

**4. Tracking success rate**: If your win rate is above 50%, you're not being ambitious enough. Failures are the best source of learning. Instead → track learning quality alongside outcomes.

#### Step 10: Evaluate Program Effectiveness

**Quantitative metrics** (measure in pairs to prevent gaming):

| Metric | What it measures | Tradeoff metric |
|--------|-----------------|-----------------|
| Unforced errors over time | Process quality — are we making fewer avoidable mistakes? | (Watch that it doesn't disincentivize trying new infrastructure) |
| Estimated-to-actual accuracy | Planning quality — are estimates of duration, impact, cost getting better? | Pair with ROTI trend |
| Deliverable fulfillment rate | Value delivery — are we hitting the goals we committed to? | Pair with deliverable scope (are goals getting bolder or safer?) |
| Return on Time Invested trend | Efficiency — are we getting more impact per unit of time? | Pair with estimated-to-actual accuracy (are ROTI improvements real or inflated?) |

Measure these with time-smoothing (quarterly trends, not test-by-test). It's more important to see a positive trend than to hit a specific target.

**Qualitative evaluation** (complement the numbers with judgment):

1. **Ability to create valuable learnings**: Categorize each test's learnings as high-value (exposed a major gap between org understanding and user reality), actionable (will directly inform future initiatives), or informative (adds context). Track the distribution over time. More high-value learnings = program is tackling harder, more important questions.

2. **Ability to ideate effective solutions**: Where are solutions coming from? If it's always the same 2-3 people, the program is fragile. Track solution source diversity. Also track what types of solutions are being tested — if it's all optimizations, the program isn't learning enough.

3. **Ability to iterate losses into wins**: How many times does an initiative iterate before producing a win? How many are abandoned without clear learnings? Track the ratio. Great teams turn losses into wins through systematic iteration — not by throwing new ideas at the wall.

#### Step 11: Build Experimentation Culture

Five qualities of a strong experimentation culture — the "5 Ps":

**1. Purpose**: Experimentation is valued as the organization's center of excellence for understanding users. It's everyone's job to understand how experimentation works (invest in training). Frame the experimentation team as facilitators of others' success (assists, not goals).

**2. Participation**: Diverse perspectives from across the organization contribute to opportunity identification, solution ideation, test design, and implementation. To increase participation: reduce friction (communicate early, standardize processes) and increase motivation (make people feel integral, celebrate contributions publicly).

**3. Policies**: Formal organizational support for experimentation: dedicated resources, activities that require experimentation support (e.g., all major releases go through a test), specific communication channels, and experimentation plans tied to team budgets.

**4. Persistence**: Unexpected results are embraced as opportunities, not failures. A program that never produces surprising results isn't learning anything new — it's just confirming what people already believe. Great teams are excited by the unexpected, not uncomfortable with it.

**5. Perception**: The organization actively questions assumptions and seeks to close the gap between intuition and reality. Foster "hypotheticals" — alternative explanations that contradict the current thinking. Healthy skepticism toward intuition, validated through data, without personally offending anyone.

### Step 12: Generate the Experiment Review Document

```
# Experiment Review: [Initiative/Quarter Name]
Date: [date]
Author: [PM name]
Period: [date range]

## Implementation Summary

### [Experiment name]
- **Result**: [Positive / Negative / Null]
- **Decision**: [Implement / Don't implement / Iterate]
- **Implementation type**: [Full / Partial]
- **Path to full**: [timeline if partial]
- **Measured test impact**: [metric: +X%]
- **Estimated actual impact**: [conservative estimate after discounts]
- **Method used to measure**: [holdout / backoff / cohort / time-smoothed / estimation]

## Key Learnings

### High-Value Learnings
[Learnings that exposed a major gap between org understanding and user reality]

### Actionable Learnings
[Learnings that will directly inform upcoming initiatives]

### Informative Learnings
[Learnings that add context to existing knowledge]

## Communication Plan
- Regular update sent: [date, channel]
- Review session held: [date, attendees]
- Charter principles updated: [any new or modified principles]
- Interactive readout: [date, topic — if warranted]

## Program Health

### Quantitative
| Metric | This period | Last period | Trend |
|--------|-------------|-------------|-------|
| Unforced errors | [count] | [count] | [↑↓→] |
| Estimation accuracy | [%] | [%] | [↑↓→] |
| Deliverable fulfillment | [%] | [%] | [↑↓→] |
| ROTI trend | [value] | [value] | [↑↓→] |

### Qualitative
- **Learning quality**: [distribution of high-value / actionable / informative]
- **Solution source diversity**: [who contributed ideas this period]
- **Iteration effectiveness**: [how many losses led to wins through iteration]

### Maturity Assessment
- **Current phase**: [Individual / Centralized / Distributed]
- **Portfolio mix**: [% optimization vs. % big bets vs. % validation]
- **Next investment**: [what capability or infrastructure to build next]

## Next Period Priorities
[What strategic opportunities to pursue, what experiments to run, what program improvements to make]
```

## Common Mistakes

1. **Skipping buy-in**: Assuming a winning test automatically gets implemented. Organizational friction is real — invest in building the case.

2. **Equating test impact with actual impact**: The five factors (statistical significance effects, novelty, engagement bias, confounding, pull-forward) almost always make actual impact lower than test impact. Set expectations accordingly.

3. **Holdout tests by default**: Holdout tests are expensive and complex. Only run them when the specific benefit justifies the cost (performance marketing ROI, business-user tradeoffs, leading indicator validation).

4. **Communication as afterthought**: Learning that sits in unopened documents is worthless. Institutionalize flows of information — regular reviews, searchable libraries, living charter principles.

5. **Measuring the wrong things**: "Number of tests run" and "win rate" create toxic incentives. Measure process quality and value delivery, in pairs, with time-smoothing.

6. **All optimization, no ambition**: If your win rate is consistently above 50%, your tests aren't ambitious enough. A healthy program has a mix of safe optimizations and risky big bets.

7. **No culture investment**: Experimentation can't thrive as a silo. It needs organization-wide purpose, participation, policies, persistence, and perception — the 5 Ps.

## Key Principle

Experimentation doesn't directly create value — it creates the understanding that enables value creation. The ultimate measure of an experimentation program isn't the number of winning tests. It's whether the organization makes better decisions about users, product, and strategy because experimentation exists. Everything in this skill — implementation, measurement, communication, program management — serves that purpose.
