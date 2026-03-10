# pmflow

Product Management workflows for early-career PMs, packaged as a Claude plugin.

Structured frameworks for the core PM loop: understand the problem, validate with users, specify the solution, decide along the way.

## Skills

| Skill | What it does |
|-------|-------------|
| `/manager-briefing` | Extracts context from your manager about a new project. Generates a document with hypotheses for strategic fit, user value, and business value. |
| `/interview-guide` | Generates a customized interview script using the Trail Guide framework (Warm-up → Build → Peak). |
| `/interview-debrief` | Synthesizes interview notes: individual debrief or full synthesis with User Value Map. |
| `/prd` | Creates or updates a complete PRD with 10 sections: problem, audience, requirements, metrics, scope, risks, and more. |
| `/decision` | Thought partner for product micro-decisions: structures options, trade-offs, and gives a clear recommendation. |

## Recommended Flow

Each skill works independently, but they connect naturally:

```
/manager-briefing → /interview-guide → /interview-debrief → /prd
                                                              ↑
                                            /decision (anytime)
```

1. **New project?** Start with `/manager-briefing` to structure hypotheses
2. **Need to validate?** Use `/interview-guide` to prepare the script
3. **Interviews done?** Use `/interview-debrief` to synthesize insights
4. **Time to spec?** Use `/prd` to generate the document
5. **Stuck on a call?** Use `/decision` to think it through

## Install

Install via Claude Code CLI:

```bash
claude plugin install pmflow
```

Or point Claude Code to this directory:

```bash
claude --plugin-dir /path/to/pmflow
```

No external dependencies required.

## License

MIT
