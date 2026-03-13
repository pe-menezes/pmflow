---
name: prd
description: >
  Use this skill when the user asks to "write a PRD",
  "create a product spec", "document product requirements",
  "update my PRD", "write a product requirements document",
  "spec out a feature", or needs to create or update the
  central document that communicates what to build and why
  to design and engineering partners.
version: 1.0.0
---

# PRD (Product Requirements Document)

Generate or update a PRD — the single source of truth that communicates what to build, why, for whom, and how success will be measured.

## When to Use

- **After opportunity validation**: User value and business value validated, ready to specify
- **After feature design**: Update with final design decisions, prototypes, risks
- **From scratch**: Guide the PM through the required thinking even without prior artifacts

## Process

### Step 1: Gather Inputs

Check workspace for existing artifacts:
- Manager briefing (strategic fit, hypotheses)
- User Value Map or interview synthesis
- Funnel analysis or business value analysis
- Design prototypes or mockups
- Existing draft PRD to update

If artifacts exist, pull relevant sections. If nothing exists, guide from scratch.

Also ask: **Output format**: What format for the final document? (docx, md, or pdf). Default: docx.

### Step 2: Build Section by Section

Walk through interactively. Challenge weak or vague answers.

**Section 1: Problem Statement**
- What is the problem? (user's perspective)
- Who has it? (specific audience)
- What happens today without this feature? (pain, workarounds)
- What evidence supports this? (data, interviews, tickets)

Push back if the "problem" is a solution in disguise.

**Section 2: Target Audience**
- Primary user: specific demographics/firmographics + product behaviors
- Secondary users: anyone else affected
- Anti-audience: who is NOT the target for v0

**Section 3: Strategic Context**
- Connection to company/product/team goals
- Why now? Trigger or urgency?
- What happens if we don't build this?

**Section 4: Proposed Solution**
- High-level WHAT (not HOW it's built)
- Key user flows step by step
- Entry points: where/how users access
- Interaction with existing features
- Prototypes or mockups (if available)

**Section 5: Requirements**
- **Functional**: What the feature must do (user-facing behaviors)
- **Non-functional**: Performance, security, accessibility, scalability
- **Edge cases**: Unusual scenarios

Each requirement gets: priority (must-have vs. nice-to-have) and acceptance criteria.

**Section 6: Success Metrics**
- Primary metric: THE one metric for success
- Supporting metrics: Additional signals
- Guardrail metrics: What should NOT get worse
- How and when to measure

**Section 7: Scope & Anti-scope**
- **In scope (v0)**: Closed, specific list
- **Anti-scope**: What does NOT ship (be aggressive)
- **Future considerations**: Intentionally deferred

**Section 8: Design Decisions & Trade-offs**
- Alternatives considered and why rejected
- Key trade-offs made
- What was prototyped, tested, learned

**Section 9: Risks**
- Usability risks (friction, adoption)
- Utility risks (might not solve the problem)
- Technical risks (complexity, dependencies)
- Business risks (timing, competition)
- Each with mitigation plan

**Section 10: Open Questions**
- Unresolved items needing input
- Blocked decisions and by whom

### Step 3: Consistency Check

Before generating the final document, validate the PRD against prior artifacts. This step catches contradictions before they reach design and engineering.

**If a manager briefing exists**, check:
- Does the PRD's problem statement match the user value hypothesis from the briefing?
- Are the success metrics aligned with the business value the manager identified?
- Does the strategic context in the PRD match the strategic fit from the briefing?
- If there are mismatches, they're not necessarily wrong — the PM may have learned something new. But flag them explicitly: "Your PRD says [X], but the manager briefing said [Y]. Is this an intentional update based on what you learned, or an inconsistency to resolve?"

**If interview synthesis or User Value Map exists**, check:
- Does the problem statement reflect what users actually said, or what the PM hoped they'd say?
- Is the target audience consistent with where the strongest signal came from in the interviews?
- Are there interview findings that contradict the proposed solution? (e.g., users described the problem differently than the PRD frames it)
- Did the interviews surface severity evidence that should appear in the PRD's strategic context?

**If experiment results exist**, check:
- Do the success metrics account for learnings from past experiments?
- Is the proposed solution consistent with what was validated?

**Internal consistency check** (always run, even without prior artifacts):
- Does every functional requirement trace back to the problem statement? If a requirement doesn't connect to the stated problem, it's either scope creep or the problem statement is incomplete.
- Do the success metrics actually measure whether the problem was solved? (Not just whether the feature was shipped or used)
- Is anything in "anti-scope" that contradicts a must-have requirement?
- Are there risks listed without mitigation plans?

Present all inconsistencies to the PM before generating the document. Let them resolve each one — update the PRD, update the prior artifact, or acknowledge the deliberate change.

### Step 4: Generate the Document

Produce the document in the user's chosen format (default: docx). If docx, use the docx skill. If pdf, use the pdf skill. If md, write as markdown. Use the following structure:

```
# PRD: [Feature Name]
Author: [PM name]
Date: [date]
Status: [Draft / In Review / Approved]

## 1. Problem Statement
[problem + audience + evidence]

## 2. Target Audience
### Primary
[who]
### Secondary
[who]
### Anti-audience
[who is NOT the target]

## 3. Strategic Context
[goals + why now]

## 4. Proposed Solution
### Overview
[high-level description]
### Key User Flows
[step-by-step]
### Entry Points
[access points]
### Interactions
[what it touches]

## 5. Requirements
### Functional
| # | Requirement | Priority | Acceptance Criteria |
|---|------------|----------|-------------------|
| 1 | [req] | Must-have | [criteria] |

### Non-functional
[performance, security, accessibility]

### Edge Cases
[unusual scenarios]

## 6. Success Metrics
| Metric | Type | Target | Measurement |
|--------|------|--------|------------|
| [metric] | Primary | [target] | [how] |
| [metric] | Guardrail | [threshold] | [how] |

## 7. Scope
### In Scope (v0)
- [item]
### Anti-scope
- [item]
### Future
- [item]

## 8. Design Decisions & Trade-offs
[alternatives, trade-offs, test results]

## 9. Risks
| Risk | Type | Severity | Mitigation |
|------|------|----------|-----------|
| [risk] | [type] | [H/M/L] | [plan] |

## 10. Open Questions
- [ ] [question + owner]
```

## Updating an Existing PRD

1. Read the existing PRD
2. Ask what changed (design decisions, test results, scope changes, risks)
3. Update relevant sections only
4. Add changelog entry with date and summary

## Tone

- **Critical collaborator**: If a section is weak, say so.
- **Push for specificity**: Vague requirements ("make it fast") → specific ("page loads in <2s on 3G")
- **Force anti-scope**: If PM can't say what's OUT, scope isn't defined.
- **Testable requirements**: Every requirement needs acceptance criteria.

## Key Principle

A PRD is the contract between PM, design, and engineering. Every ambiguity becomes a decision someone else makes without your input.
