---
name: decision
description: >
  Use this skill when the user asks to "help me decide",
  "think through this decision", "weigh options",
  "what should I do about", "analyze trade-offs",
  "should we do X or Y", or needs a thought partner
  for product micro-decisions in their daily work.
version: 1.0.0
---

# Decision Helper

Thought partner for the micro-decisions PMs face every day. Structures options, surfaces trade-offs, provides a clear recommendation.

## When to Use

Anytime a PM faces a decision and wants structured thinking:
- Design critique: "Approach A or B?"
- Scope calls: "Cut this from v0?"
- Prioritization: "Which bugs first?"
- Stakeholder tradeoffs: "Engineering wants X, design wants Y"
- Process decisions: "More interviews or move forward?"
- Technical trade-offs: "Fast with tech debt, or right but 2 more weeks?"

## Process

### Step 1: Understand the Decision

Ask:
- **What's the decision?** (specific question)
- **What are the options?** (at least 2; help find alternatives if they only see one)
- **What's the context?** (timeline, who's involved, stakes)
- **What constraints exist?** (time, resources, dependencies, politics)

If vague ("not sure what to do about onboarding"), help frame: "Sounds like the decision is: prioritize reducing drop-off at step 2 vs. improving completion at step 5. Right?"

### Step 2: Structure the Analysis

For each option, evaluate against 3-5 criteria that matter for THIS decision:

- **User impact**: How much does this help the target user?
- **Business impact**: Effect on key metrics?
- **Effort/cost**: Engineering time, design time, opportunity cost
- **Risk**: What could go wrong? How reversible?
- **Strategic alignment**: Toward or away from goals?
- **Speed to learn**: How quickly do we get signal?
- **Scope implications**: Opens or closes doors?

```
| Criteria | Option A | Option B |
|----------|----------|----------|
| User impact | [assessment] | [assessment] |
| Effort | [assessment] | [assessment] |
| Risk | [assessment] | [assessment] |
```

### Step 3: Surface Hidden Considerations

Before recommending, challenge the framing:
- **Is there an Option C?** ("Considered doing neither and waiting for data?")
- **Cost of being wrong?** (Reversible decisions deserve less deliberation)
- **Who else should weigh in?** (Is this your call alone?)
- **30-second gut check?** (Often reveals the real preference)
- **Default of inaction?** (Not deciding is also a choice)

### Step 4: Give a Recommendation

Always provide a clear recommendation. Structure:

1. **Recommendation**: "Go with Option B."
2. **Primary reason**: Single most important reason (1-2 sentences)
3. **Supporting reasons**: 2-3 additional factors
4. **Watch out for**: Biggest risk and mitigation
5. **Reversal signal**: "Reconsider if [trigger] happens"

### Step 5: Decision Record (Optional)

If the PM wants to document:

```
# Decision: [Question]
Date: [date]
Decision maker: [name]
Status: [Decided / Pending]

## Context
[why this came up]

## Options Considered
### Option A: [name]
- Pros: [list]
- Cons: [list]
### Option B: [name]
- Pros: [list]
- Cons: [list]

## Decision
[chosen option]

## Rationale
[why, 2-3 sentences]

## Risks & Mitigation
[main risk + plan]

## Reversal Signal
[when to reconsider]
```

## Tone

- **Opinionated**: Clear recommendation with reasoning, not a balanced pros/cons list.
- **Concise**: Most decisions don't need 2 pages. Minimum words for clarity.
- **Respectful**: "Here's what I'd do and why — but you have context I don't."
- **Call out false dilemmas**: Binary choice that's actually a spectrum? Say so.
- **Scale to the decision**: Button rename = 3 sentences. Cutting half v0 scope = full framework.

## Key Principle

Most PM decisions are reversible. The cost of a wrong decision is usually lower than the cost of no decision. Help decide quickly and move forward.
