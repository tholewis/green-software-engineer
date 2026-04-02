# Green Software Engineer — Agent Guide

## What Is an Agent?

In Claude Code, an **agent** is a separate Claude instance that runs in its own
isolated context window. Think of it as a specialised coworker you can summon by
name. You invoke it explicitly, it does its work autonomously, and its output is
returned to your main conversation without polluting your working context.

---

## What Does This Agent Do?

The `green-software-engineer` agent acts as an on-call sustainability consultant
embedded in your development workflow. It is grounded in the [Green Software
Foundation's](https://greensoftware.foundation) principles, patterns, and the
ISO-certified SCI standard.

**Use it when you want to:**

| Scenario | Example invocation |
|---|---|
| Get sustainability advice on a design decision | `@green-software-engineer what's the greenest way to handle image uploads at scale?` |
| Review a piece of code for carbon inefficiency | `@green-software-engineer review this API handler for carbon hotspots` |
| Understand the SCI scoring formula | `@green-software-engineer how would I calculate an SCI score for this microservice?` |
| Compare architectural approaches on sustainability | `@green-software-engineer is polling or websockets more carbon-efficient?` |
| Audit infrastructure config | `@green-software-engineer audit this Terraform config for over-provisioning` |

---

## The Agent's Knowledge

### GSF's 8 Core Principles

| Principle | What it means in practice |
|---|---|
| **Carbon** | Emit as little CO₂ equivalent as possible per unit of work |
| **Electricity** | Use the minimum energy to accomplish the task |
| **Carbon Intensity** | Prefer regions and times when the grid runs on renewables |
| **Embodied Carbon** | Account for the carbon cost of manufacturing hardware, not just operating it |
| **Energy Proportionality** | Run servers at high utilisation; idle hardware still consumes energy |
| **Networking** | Every byte moved costs energy — minimise data in transit |
| **Demand Shaping** | Shift or reduce workloads to match green energy availability |
| **Measurement & Optimisation** | Measure first; you cannot optimise what you don't track |

### The SCI Formula (ISO 21031:2024)

```
SCI = ((E × I) + M) / R
```

- **E** — Energy consumed by the software (kWh)
- **I** — Carbon intensity of that energy (gCO₂eq/kWh), location and time-based
- **M** — Embodied carbon of the hardware being used
- **R** — Functional unit (per request, per user, per transaction, etc.)

The agent can help you define your functional unit, identify measurement approaches,
and interpret your SCI score relative to industry benchmarks.

---

## How to Invoke the Agent

```
@green-software-engineer <your question or code>
```

You can paste code directly into the message, reference a file, or simply ask a
conceptual question. The agent runs in its own context, so it won't carry state
between invocations — give it the context it needs each time.

**Tip:** For a full codebase audit, ask it to review specific files or paste
the relevant sections rather than the whole project at once.

---

## Agent vs Skill — When to Use Which

| | Agent (`@green-software-engineer`) | Skill (`/green-review`) |
|---|---|---|
| **Best for** | Q&A, architecture advice, deep audits | Passive enforcement while coding |
| **Invoked by** | You, explicitly | Claude automatically, or you via `/green-review` |
| **Context** | Own isolated context window | Your main conversation |
| **Runs when** | You call it | Claude detects you're writing backend code |
| **Output style** | Conversational, advisory | Structured checklist with severity ratings |

Use the **agent** when you want a conversation or a considered opinion.
Use the **skill** for a quick structured pass over code you just wrote.

---

## File Location

```
your-project/
└── .claude/
    └── agents/
        └── green-software-engineer.md   ← this agent
```

To make the agent available **across all your projects**, place it in your global
Claude Code config instead:

```
~/.claude/agents/green-software-engineer.md
```

---

## References

- [Green Software Foundation](https://greensoftware.foundation)
- [GSF Green Software Patterns](https://patterns.greensoftware.foundation)
- [SCI Specification](https://sci.greensoftware.foundation)
- [Green Software Practitioner Course](https://learn.greensoftware.foundation)
- [SCI for AI Standard](https://greensoftware.foundation/stories/sci-for-ai/)
