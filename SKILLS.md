# Skills Reference

Detailed guide for every pmflow skill. For each skill: what it does, when to use it, what it asks you, what it produces, and how it connects to other skills.

---

## 1. Manager Briefing

**Command**: `/pmflow:manager-briefing`

**Purpose**: Extract context from your manager about a new project before you start working on it. The output is a structured document that makes your assumptions explicit — so you can validate them later instead of discovering misalignment three weeks in.

**When to use**:
- You just got assigned to a new project and need to understand why it was prioritized
- You're unclear on how this project connects to company strategy
- You want to align with your manager on what success looks like before diving in

**What it asks you**:
- Strategic fit: How does this connect to company mission, strategy, product strategy, and team goals?
- User value: Who is the target user? What problem do they have? Why does it matter? How will we know we've solved it?
- Business value: Who are the stakeholders? What are the success metrics? How does this connect to business outcomes?

**What it produces**: A document with three sections (strategic fit, user value, business value), each framed as hypotheses to validate — not facts to assume.

**Connects to**: The manager briefing feeds directly into `interview-guide` (provides the problem hypothesis to validate) and `prd` (provides strategic context and success metrics).

**Output format**: docx (default), md, or pdf.

---

## 2. Interview Guide

**Command**: `/pmflow:interview-guide`

**Purpose**: Generate a customized user interview script that surfaces real behavioral data — not polite opinions, hypothetical promises, or compliments.

**When to use**:
- After the manager briefing, when you have hypotheses to validate
- Anytime you need to run discovery interviews with users
- When preparing for customer calls and want structured, bias-resistant questions

**What it asks you**:
- Product/company context
- Target user profile
- Problem hypothesis
- Top 3 learning goals (at least one must be a question that could disprove the hypothesis)
- Interview duration (default: 45 min)

**What it produces**: A full interview script using the Trail Guide framework:
- **Warm-up** (5-10 min): rapport building, framing as a learning conversation
- **Build** (10 min): broad context → specific domain behavior
- **Peak** (25-30 min): deep dive into the problem using concrete past behavior

Every question goes through a 4-point anti-bias stress test before inclusion. The document also includes conversation guardrails, a pre-interview checklist, and a signal strength reference (strongest → noise).

**Key feature**: The stress test filter catches questions that lead the interviewee, ask about future intention instead of past behavior, make it easy for people-pleasers to just agree, or fish for a specific answer. If the script has more than 2 weak questions, the skill rewrites them.

**Connects to**: Uses hypotheses from `manager-briefing`. Produces scripts that feed into `interview-debrief`.

**Output format**: docx (default), md, or pdf.

---

## 3. Interview Debrief & Synthesis

**Command**: `/pmflow:interview-debrief`

**Purpose**: Extract real insights from interview notes, separating concrete behavioral evidence from noise (compliments, vague opinions, hypotheticals). Two modes for different stages.

**When to use**:
- **Mode 1** — After each interview: quick debrief to capture insights while fresh (ideally within 30 minutes)
- **Mode 2** — After all interviews: full synthesis to consolidate patterns across interviews and passive feedback sources

**What it asks you**:

*Mode 1 (single debrief)*:
- Raw notes or transcript
- Interview number (e.g., "3 of 6")
- Problem hypothesis and top 3 learning goals

*Mode 2 (synthesis)*:
- All debrief documents
- Additional passive feedback sources: NPS comments, app reviews, support tickets, cancellation reasons, sales notes, community feedback

**What it produces**:

*Mode 1*: A debrief document with user profile, data quality classification (every observation tagged as fact/workaround/commitment/compliment/fluff/idea), hypothesis check (supports/contradicts/new), takeaways (problem/severity/alternatives), conversation quality review, and recommended adjustments for the next interview.

*Mode 2*: A synthesis document with problem clusters (ranked by frequency × severity × workaround quality), segment analysis, alternatives assessment, commitment audit, a refined User Value Map, and a project assessment (proceed/pivot/narrow/kill/more research).

**Key feature**: Mode 2 integrates passive feedback sources (NPS, reviews, tickets) alongside interview data, applying the same data quality framework. Cross-source validation is flagged explicitly — problems that show up in both interviews AND passive feedback are much stronger signals.

**Connects to**: Takes notes from interviews run with `interview-guide`. The User Value Map feeds into `prd` and `story-builder`.

**Output format**: docx (default), md, or pdf.

---

## 4. PRD (Product Requirements Document)

**Command**: `/pmflow:prd`

**Purpose**: Create or update a PRD — the contract between PM, design, and engineering that communicates what to build, why, for whom, and how success is measured.

**When to use**:
- After opportunity validation, ready to specify the solution
- After feature design, to update with final decisions and trade-offs
- From scratch, when the PM needs structured thinking even without prior artifacts

**What it asks you**: Walks through 10 sections interactively, challenging weak or vague answers:
1. Problem statement (pushes back if the "problem" is a solution in disguise)
2. Target audience (primary, secondary, anti-audience)
3. Strategic context (connection to goals, why now)
4. Proposed solution (high-level what, key user flows, entry points)
5. Requirements (functional with acceptance criteria, non-functional, edge cases)
6. Success metrics (primary, supporting, guardrail)
7. Scope & anti-scope (forces what's OUT of v0)
8. Design decisions & trade-offs
9. Risks (usability, utility, technical, business — each with mitigation)
10. Open questions

**What it produces**: A complete PRD document with all 10 sections, ready to share with design and engineering.

**Key feature**: Before generating the document, runs a consistency check against prior artifacts. If the PRD's problem statement contradicts the interview synthesis, or the success metrics don't align with the manager briefing — the skill flags it and asks the PM to resolve the inconsistency before finalizing.

**Connects to**: Pulls context from `manager-briefing`, `interview-debrief` (User Value Map), and experiment results. Feeds into `story-builder` and `comms-plan`.

**Output format**: docx (default), md, or pdf.

---

## 5. Decision Helper

**Command**: `/pmflow:decision`

**Purpose**: Structured thought partner for the micro-decisions PMs face every day. Doesn't just analyze — gives a clear recommendation and then challenges it.

**When to use**:
- Design critique: "Approach A or B?"
- Scope calls: "Cut this from v0?"
- Prioritization: "Which bugs first?"
- Stakeholder trade-offs: "Engineering wants X, design wants Y"
- Process decisions: "More interviews or move forward?"
- Technical trade-offs: "Fast with tech debt, or right but 2 more weeks?"

**What it asks you**:
- What's the decision? (specific question)
- What are the options? (at least 2; helps find alternatives if you only see one)
- Context (timeline, who's involved, stakes)
- Constraints (time, resources, dependencies, politics)

**What it produces**: A structured analysis with:
1. Options evaluated against 3-5 relevant criteria
2. Hidden considerations surfaced (Option C? Cost of being wrong? Who else should weigh in?)
3. Clear recommendation with primary reason, supporting reasons, and reversal signal
4. **Devil's advocate**: the strongest case AGAINST the recommendation, the assumption that would need to be false, and who would disagree and why
5. Optional decision record document (with Goal, Options Explicitly Rejected, Counter-argument Considered, Impact, and Next Steps with owners)

**Key feature**: The devil's advocate step is mandatory — not optional. After every recommendation, the skill steel-mans the counter-argument and asks whether it changes anything. This catches the anchoring bias that makes PMs (especially junior ones) stick with the first viable option.

**Connects to**: Works standalone at any point in the workflow. The decision record is designed to be shareable with stakeholders as-is.

**Output format**: docx (default), md, or pdf.

---

## 6. Story Builder

**Command**: `/pmflow:story-builder`

**Purpose**: Build a compelling product narrative that drives buy-in, alignment, and action. Transforms an idea into a structured story with a clear protagonist, problem, result, action plan, and ask.

**When to use**:
- After the PRD, when you need to sell the idea
- Before a leadership review
- To align a cross-functional team
- To unlock a dependency from another team
- Strategy pitches

**What it asks you**:
- Story readiness (customer interest + business interest + strategic alignment + feasibility)
- Business context for timing evaluation
- Main character (always a person, never "the business")
- The problem (both user and business perspectives)
- The result (both user and business outcomes)
- The action (high-level plan)
- The ask (specific, quantified)
- Who the primary decision-maker is (role, priorities, communication style, biases)

**What it produces**: A complete story document with elevator pitch, readiness assessment, full narrative, supporting content inventory (tangible, emotional, clear, believable), audience simulation, and Q&A prep.

**Key feature**: After building the story, simulates the key decision-maker's reaction — their first impression, top 3 objections (phrased in their voice), what they need to hear to say yes, and what language to avoid. This is personalized to the specific stakeholder, not generic Q&A.

**Connects to**: Pulls evidence from `interview-debrief` and `prd`. Feeds directly into `comms-plan` for the communication strategy.

**Output format**: docx (default), md, or pdf.

---

## 7. Communications Plan

**Command**: `/pmflow:comms-plan`

**Purpose**: Design the full communication strategy to land a product story. Maps audiences, adapts the message for each, plans the pre-sell sequence, and prepares for both proactive and reactive storytelling.

**When to use**:
- After building a story, to plan how to deliver it
- Before a big pitch, to orchestrate the sequence of conversations
- For cross-functional alignment with different audiences and motivations

**What it asks you**:
- The story or initiative being communicated
- The goal (approval, resources, alignment, dependency unlocked)
- Timeline and decision date
- Every relevant audience (leadership, team, dependent stakeholders) with their context, goals, relationship to the story, trust level, and communication style

**What it produces**: A communications plan with:
- Audience map with pre-sell method for each person (co-creation / feedback / advice / pre-read)
- Story adaptation for each audience type
- Communication sequence timeline (pre-sell → pitch → post-decision)
- Format and channel selection
- Reactive storytelling prep (elevator pitch, talking points, Q&A)
- Executive writing templates (inverted pyramid, decision memo, blocker escalation)

**Key feature**: Includes three executive writing templates — inverted pyramid (for updates), decision memo (for approvals), and blocker escalation (for unblocking). Each template has a structure, rationale, and guidance on when to use it. Closes the gap between "knowing what to communicate" and "knowing how to write it."

**Connects to**: Takes the story from `story-builder`. The pre-sell strategy and audience mapping are the core contribution.

**Output format**: docx (default), md, or pdf.

---

## 8. Experiment Strategy

**Command**: `/pmflow:experiment-strategy`

**Purpose**: Go from a growth goal to a prioritized set of testable solutions. Covers the two foundational phases: identifying strategic opportunities (what to test and why) and ideating solutions (how to solve it).

**When to use**:
- Starting a new experimentation initiative
- Growth model mapping (understanding the levers before choosing where to experiment)
- Customer problem scoping
- Solution ideation and prioritization
- Building an experimentation roadmap for a quarter

**What it asks you**:
- Growth model context (acquisition loops, retention loops, monetization, defensibility)
- Customer problem definition (what, who, where, why)
- Outcome metrics, intermediate metrics, description metrics
- Prioritization across multiple opportunities

**What it produces**: An experimentation strategy document with:
- Growth model map
- Customer problem statement
- Metric hierarchy
- Strategic opportunity narrative
- Solution portfolio with each solution tagged by type (simplify → reinvent) and behavioral lens
- ICE scoring and risk categorization (no-brainers, quick wins, big bets, duds)
- Provisional solution approaches (painted door, wizard of oz, limited feature, targeted release)
- Sequenced experimentation roadmap

**Key feature**: The behavioral lenses framework goes beyond simple "friction reduction." Every solution is tagged with which lens it uses — friction reduction, motivation triggers (loss aversion, progress, curiosity gaps, immediate value), social influence (proof, accountability, network effects, referral triggers), or habit formation (trigger reliability, variable reward, investment, routine fit). If the entire portfolio is just friction reduction, the skill pushes for diversity.

**Connects to**: Feeds into `experiment-design` for test mechanics. Uses insights from `interview-debrief` for problem definition.

**Output format**: docx (default), md, or pdf.

---

## 9. Experiment Design

**Command**: `/pmflow:experiment-design`

**Purpose**: Design and run a rigorous experiment from test parameters through result analysis. Handles the statistical mechanics so the PM can focus on learning.

**When to use**:
- Designing an A/B test
- Calculating sample size and test duration
- Planning user assignment and eligibility
- Monitoring a running test
- Calling a test and analyzing results
- Segmenting results and planning iteration

**What it asks you**:
- Baseline metrics and minimum detectable effect (MDE)
- Statistical parameters (p-value, power)
- Test variables and variants
- User eligibility and assignment criteria
- Launch readiness checklist

**What it produces**: A test design document with sample size calculation, ROTI prioritization, build complexity assessment, user assignment plan (eligibility, randomization, level), launch checklist, monitoring guardrails (anti-peeking), call criteria, segmentation plan, and iteration plan.

**Key feature**: Emphasizes statistical rigor — calculates required sample size, enforces stopping rules, and warns against peeking at results before significance is reached.

**Connects to**: Takes prioritized solutions from `experiment-strategy`. Results feed into `experiment-review`.

**Output format**: docx (default), md, or pdf.

---

## 10. Experiment Review

**Command**: `/pmflow:experiment-review`

**Purpose**: Turn experiment results into real-world impact. Bridges the gap between "the test won" and "we shipped it and it actually moved the metric."

**When to use**:
- Getting buy-in to implement a winning test
- Planning full vs. partial rollout
- Measuring actual impact (which often differs from test impact)
- Communicating experiment results to the organization
- Assessing and improving your experimentation program

**What it asks you**:
- Test results and context
- Decision-maker and stakeholder landscape
- Implementation constraints
- Program maturity level

**What it produces**: Three parts:

*Part 1 — Productize*: Decision-maker buy-in strategy, full vs. partial implementation plan, why test impact differs from actual impact (novelty, engagement bias, confounding, pull-forward), actual impact measurement approaches (holdout tests, backoff tests, cohort analysis).

*Part 2 — Communicate*: Results communication strategy (interactive library, review sessions), charter principles for the experimentation program.

*Part 3 — Program*: Maturity assessment (individual → centralized → distributed), portfolio evolution, effectiveness metrics (quantitative + qualitative), culture building (the 5 Ps: purpose, participation, policies, persistence, perception).

**Connects to**: Takes results from `experiment-design`. Program-level insights feed back into `experiment-strategy` for the next cycle.

**Output format**: docx (default), md, or pdf.
