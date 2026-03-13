# pmflow

Product Management workflows for early-career PMs, packaged as a [Claude plugin](https://docs.claude.com).

11 structured skills that guide you through the core PM loop: understand the problem, validate with users, specify the solution, communicate with stakeholders, run experiments, and analyze data. Each skill is an interactive workflow — it asks questions, challenges weak thinking, and produces a shareable document at the end.

## Skills

### Discovery & Validation

| Skill | Command | What it does |
|-------|---------|-------------|
| Manager Briefing | `/pmflow:manager-briefing` | Extracts context from your manager about a new project. Produces a document with hypotheses for strategic fit, user value, and business value — making assumptions explicit before validation. |
| Interview Guide | `/pmflow:interview-guide` | Generates a customized interview script using the Trail Guide framework (Warm-up → Build → Peak). Every question is stress-tested against anti-bias filters to ensure you get real behavioral data, not polite opinions. |
| Interview Debrief | `/pmflow:interview-debrief` | Two modes. **Mode 1**: debrief a single interview — classifies data quality (real signals vs. noise), tags observations, recommends whether to continue or adjust. **Mode 2**: synthesize across all interviews + passive feedback sources (NPS, reviews, support tickets) into a User Value Map. |

### Specification

| Skill | Command | What it does |
|-------|---------|-------------|
| PRD | `/pmflow:prd` | Creates or updates a PRD with 10 sections: problem, audience, strategy, solution, requirements, metrics, scope, design decisions, risks, and open questions. Runs a consistency check against prior artifacts (manager briefing, interview synthesis) before generating. |
| Decision | `/pmflow:decision` | Thought partner for product micro-decisions. Structures options, evaluates trade-offs, gives a clear recommendation — then plays devil's advocate against its own recommendation to surface blind spots. Optionally produces a shareable decision memo. |

### Storytelling & Communication

| Skill | Command | What it does |
|-------|---------|-------------|
| Story Builder | `/pmflow:story-builder` | Builds a compelling product narrative (character → problem → result → action → ask). Includes story readiness checks, timing evaluation, and a simulated audience reaction from the key decision-maker. |
| Comms Plan | `/pmflow:comms-plan` | Designs the full communication strategy: maps every audience, adapts the story for each, plans the pre-sell sequence, selects format and channel, and prepares reactive talking points. Includes executive writing templates (inverted pyramid, decision memo, blocker escalation). |

### Experimentation

| Skill | Command | What it does |
|-------|---------|-------------|
| Experiment Strategy | `/pmflow:experiment-strategy` | Goes from a growth goal to a prioritized experimentation roadmap. Maps your growth model, defines customer problems, generates solutions across a spectrum (simplify → reinvent), applies behavioral lenses (friction, motivation, social, habit), and prioritizes with ICE scoring. |
| Experiment Design | `/pmflow:experiment-design` | Full test lifecycle: defines parameters (baseline, MDE, sample size), plans user assignment, monitors without peeking, calls the test at significance, segments results, and plans iteration. Emphasizes statistical rigor. |
| Experiment Review | `/pmflow:experiment-review` | Turns experiment results into real impact. Gets decision-maker buy-in, plans full vs. partial rollout, measures actual impact (holdout tests, backoff tests), communicates results, and manages the experimentation program. |

### Data

| Skill | Command | What it does |
|-------|---------|-------------|
| Data Insights | `/pmflow:data-insights` | Guides exploratory data analysis from question to insight. Helps formulate sharp data questions, load and clean data (CSV, Excel, or database), run analyses with visualizations, verify accuracy, interpret findings in context, and produce an actionable insights document. Adapts to the PM's data fluency level. |

## Recommended Flow

Each skill works independently, but they connect naturally into a PM workflow:

```
Discovery           Specification        Communication        Experimentation      Data
─────────           ─────────────        ─────────────        ───────────────      ────
manager-briefing    prd                  story-builder        experiment-strategy   data-insights
      ↓               ↑                       ↓                     ↓              (anytime)
interview-guide     decision ←──────→   comms-plan           experiment-design
      ↓            (anytime)                                       ↓
interview-debrief ──→                                        experiment-review
```

**Starting a new project?**
`manager-briefing` → `interview-guide` → `interview-debrief` → `prd`

**Need to sell the idea?**
`story-builder` → `comms-plan`

**Ready to experiment?**
`experiment-strategy` → `experiment-design` → `experiment-review`

**Stuck on a call?**
`decision` works anytime, for any micro-decision.

**Need to understand the numbers?**
`data-insights` works anytime — investigate a metric drop, explore user behavior, or validate a hypothesis with data.

## Document Formats

Every skill that produces a document asks for your preferred format: **docx** (default), **md**, or **pdf**. The output is a shareable, stakeholder-ready document — not just a chat response.

## Install

### From GitHub (Cowork / Claude Desktop)

Add `https://github.com/pe-menezes/pmflow` as a marketplace in the Plugins settings.

### From Claude Code CLI

```bash
claude plugin add https://github.com/pe-menezes/pmflow
```

### Manual

Clone the repo and point Claude to the directory:

```bash
git clone https://github.com/pe-menezes/pmflow.git
claude --plugin-dir /path/to/pmflow
```

No external dependencies required. All skills are plain Markdown — no code, no API keys, no configuration.

## How It Works

Each skill is a `SKILL.md` file in the `skills/` directory. When you invoke a skill (e.g., `/pmflow:prd`), Claude reads the file and follows its instructions as an interactive workflow. The skill guides the conversation, asks the right questions, challenges weak answers, and produces a structured output.

Skills are designed to be opinionated — they embed PM best practices directly into the workflow so you don't have to remember them. For example, the interview guide stress-tests every question against anti-bias filters, and the decision helper automatically argues against its own recommendation.

## Skills Reference

For a detailed guide on each skill (when to use it, what it asks, what it produces), see **[SKILLS.md](SKILLS.md)**.

## Philosophy

pmflow is built on a few beliefs about PM work:

**Structured thinking beats raw effort.** Most PM mistakes come from skipping steps, not from lack of hard work. Each skill enforces a structure that catches common errors — like writing a PRD that contradicts the user research, or running interviews that only produce polite opinions.

**Documents are thinking tools, not paperwork.** The document at the end of each skill isn't the point — the thinking process that produces it is. The document is a byproduct you can share with your team.

**Challenge > compliance.** Every skill pushes back on vague inputs, weak hypotheses, and comfortable assumptions. If the PM says "small businesses" as their target audience, the skill will ask them to get specific enough to describe where to physically find those people.

## Contributing

Contributions are welcome. If you have ideas for new skills, improvements to existing ones, or bug fixes, open an issue or pull request.

When contributing a skill, follow the existing pattern: a `SKILL.md` file with YAML frontmatter (name, description, version) and a structured Markdown body with steps, templates, common mistakes, and a key principle.

## License

MIT — see [LICENSE](LICENSE).
