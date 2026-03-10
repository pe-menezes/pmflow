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

### Step 3: Generate the Document

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
