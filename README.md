# Green Software Engineer for Claude Code

A Claude Code agent and skill that embeds [Green Software Foundation](https://greensoftware.foundation)
sustainability practices directly into your development workflow.

---

## What's Included

| File | Type | Purpose |
|---|---|---|
| `.claude/agents/green-software-engineer.md` | **Agent** | On-call sustainability consultant for Q&A, architecture advice, and deep code audits |
| `.claude/skills/green-software/SKILL.md` | **Skill** | Passive green review that auto-triggers when writing backend code |

---

## Quick Start

### 1. Copy the `.claude/` folder into your project

```
your-project/
└── .claude/
    ├── agents/
    │   └── green-software-engineer.md
    └── skills/
        └── green-software/
            └── SKILL.md
```

Or for personal use across **all** projects, place them under your global config:

```
~/.claude/
├── agents/
│   └── green-software-engineer.md
└── skills/
    └── green-software/
        └── SKILL.md
```

### 2. Open your project in Claude Code

```bash
claude
```

### 3. Start using them

**Ask the agent a question:**
```
@green-software-engineer what's the greenest way to handle image uploads at scale?
```

**Run an explicit green review:**
```
/green-review
```

**Let the skill work passively** — write a new API endpoint or database query and
Claude will automatically apply the green review checklist before responding.

---

## Agent: `@green-software-engineer`

A senior green software engineer persona grounded in:

- The **8 GSF Principles** (Carbon, Electricity, Carbon Intensity, Embodied Carbon,
  Energy Proportionality, Networking, Demand Shaping, Measurement & Optimisation)
- The **SCI Standard** (ISO 21031:2024) — Software Carbon Intensity formula
- **Green Software Patterns** from patterns.greensoftware.foundation

**Example invocations:**

```
@green-software-engineer review this API handler for carbon efficiency
@green-software-engineer how would I calculate an SCI score for this service?
@green-software-engineer is polling better or worse than websockets from a green perspective?
@green-software-engineer audit this Terraform config for over-provisioning
```

→ Full documentation in [`docs/agent-guide.md`](docs/agent-guide.md)

---

## Skill: `/green-review`

A structured sustainability review checklist that covers:

- ⚡ **Energy Efficiency** — loops, lazy vs eager loading, polling patterns
- 🌐 **Network Efficiency** — payload size, round trips, CDN usage
- 🗄️ **Compute & Storage** — query optimisation, caching, data retention
- ☁️ **Cloud & Infrastructure** — provisioning, scale-to-zero, region selection, time-shifting
- 🔋 **Hardware & Embodied Carbon** — utilisation, managed vs self-managed

**Auto-triggers when writing:** API endpoints, database queries, cloud config,
background jobs, data pipelines, caching logic.

**Severity ratings:** 🔴 High / 🟡 Medium / 🟢 Low / ✅ Already Green

→ Full documentation in [`docs/skill-guide.md`](docs/skill-guide.md)

---

## Agent vs Skill — Quick Reference

| | Agent | Skill |
|---|---|---|
| Invoke with | `@green-software-engineer` | Auto, or `/green-review` |
| Best for | Q&A, architecture, deep audits | Passive guardrail while coding |
| Runs in | Isolated context window | Your main conversation |
| Output | Conversational, advisory | Structured checklist |

---

## References

- [Green Software Foundation](https://greensoftware.foundation)
- [GSF Patterns Library](https://patterns.greensoftware.foundation)
- [SCI Specification](https://sci.greensoftware.foundation)
- [Green Software Practitioner Course](https://learn.greensoftware.foundation)
- [SCI for AI Standard](https://greensoftware.foundation/stories/sci-for-ai/)
- [SOFT Framework](https://greensoftware.foundation/stories/soft-framework/)
