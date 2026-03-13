# Changelog

## 1.4.0 (2026-03-13)

Improvements to 7 existing skills based on PM best practices analysis. Prepared for open source release.

### Skill improvements

- **decision**: Added mandatory devil's advocate step that steel-mans the counter-argument after every recommendation. Expanded decision record template with Goal, Options Explicitly Rejected, Counter-argument Considered, Impact, and Next Steps with owners.
- **interview-guide**: Added 4-point anti-bias stress test that validates every generated question (allows negation, past vs. future, people-pleaser resistant, no fishing). Added signal strength hierarchy (strongest → noise) embedded in the output document.
- **interview-debrief**: Mode 2 (synthesis) now accepts passive feedback sources — NPS comments, app reviews, support tickets, cancellation reasons, sales notes, community feedback. Cross-source validation is flagged explicitly.
- **story-builder**: Added audience reaction simulation step. After building the story, simulates how the primary decision-maker will receive it: first impression, top 3 objections in their voice, what they need to hear to say yes, and what language to avoid.
- **comms-plan**: Added three executive writing templates — inverted pyramid (for updates), decision memo (for approvals), blocker escalation (for unblocking) — with structure, rationale, and guidance on when to use each.
- **prd**: Added consistency check step before document generation. Validates the PRD against manager briefing, interview synthesis, experiment results, and internal consistency (requirements → problem statement traceability, metrics → problem alignment).
- **experiment-strategy**: Expanded behavioral framework from 2 dimensions (friction/motivation) to 4 lenses: friction reduction, motivation triggers (loss aversion, progress, curiosity gaps, immediate value), social influence (proof, accountability, network effects, referral triggers), and habit formation (trigger reliability, variable reward, investment, routine fit). Every solution must be tagged with its behavioral lens.

### Documentation

- Rewrote README.md for open source (covers all 10 skills, recommended flow, install methods, philosophy)
- Added SKILLS.md — detailed reference for each skill (when to use, what it asks, what it produces, how it connects)
- Updated CHANGELOG.md with full version history

### Housekeeping

- Bumped version to 1.4.0 across plugin.json and marketplace.json
- Updated .gitignore

## 1.3.0 (2026-03-12)

Added output format question to all skills. Every skill now asks for the user's preferred format (docx, md, or pdf) with docx as default.

Added marketplace.json for Cowork plugin distribution.

## 1.2.0 (2026-03-11)

Added 5 new skills expanding pmflow from core PM loop to storytelling, communication, and experimentation:

- **story-builder**: Compelling product narrative construction with readiness checks and elevator pitch
- **comms-plan**: Communication strategy with audience mapping, pre-sell sequence, and format/channel selection
- **experiment-strategy**: Growth model mapping, customer problem scoping, solution ideation, and experimentation roadmapping
- **experiment-design**: Full A/B test lifecycle from design through statistical analysis
- **experiment-review**: Productizing wins, measuring actual impact, and experimentation program management

## 1.0.0 (2026-03-10)

Initial release with 5 core skills:

- **manager-briefing**: Structured manager briefing for new projects
- **interview-guide**: Trail Guide interview script generator
- **interview-debrief**: Interview synthesis and User Value Map
- **prd**: PRD generator and updater (10 sections)
- **decision**: Micro-decision thought partner
