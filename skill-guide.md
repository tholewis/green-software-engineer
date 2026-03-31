# Green Software Review — Skill Guide

## What Is a Skill?

In Claude Code, a **skill** is a reusable instruction set that Claude discovers and
loads dynamically when it's relevant to the current task. Think of it as a playbook
Claude reads before tackling a specific type of work — it shapes how Claude behaves
without you having to ask.

Skills live in `.claude/skills/` as a directory containing a `SKILL.md` file.
They can also bundle supporting scripts, templates, or reference files alongside
the instructions.

---

## What Does This Skill Do?

The `green-review` skill turns green software principles into a **passive guardrail**
in your development workflow. When Claude detects you're writing backend code —
a new API endpoint, a database query, a cloud configuration, a background job — it
automatically loads this skill and performs a sustainability check as part of its
response.

You can also invoke it explicitly at any time with `/green-review`.

---

## When the Skill Auto-Triggers

Claude will automatically load this skill when it sees you working on:

| Code type | Examples |
|---|---|
| API handlers | REST endpoints, GraphQL resolvers, webhooks |
| Database queries | SQL, ORM queries, migrations |
| Cloud / infrastructure config | Terraform, Pulumi, CloudFormation, Kubernetes manifests |
| Background jobs | Cron jobs, queues, workers |
| Data pipelines | ETL scripts, stream processors |
| Caching logic | Cache-aside patterns, TTL configuration |

It will **not** auto-trigger for UI-only changes, documentation edits, or test-only
files — those don't carry direct carbon impact at the infrastructure level.

---

## The Review Checklist

Every review works through five categories:

### ⚡ Energy Efficiency
Looks for: tight loops, eager computation that could be lazy, expensive operations
on the critical path, idle polling instead of event-driven patterns.

### 🌐 Network Efficiency
Looks for: oversized payloads, unnecessary data transfer, avoidable round trips,
missing CDN or edge caching for static content.

### 🗄️ Compute & Storage
Looks for: N+1 queries, missing indexes, redundant computation that could be cached,
inefficient storage formats, data retained past its useful life.

### ☁️ Cloud & Infrastructure
Looks for: over-provisioned resources, always-on services that could scale to zero,
deployment regions with high-carbon grids, workloads that could use spot instances,
batch jobs that could be time-shifted to greener grid windows.

### 🔋 Hardware & Embodied Carbon
Looks for: low-utilisation instances that are always on, self-managed VMs that could
be replaced with managed/serverless alternatives.

---

## Output Format

For every issue found, the skill produces a structured finding:

```
[PRINCIPLE] Short title
Severity: 🔴 High / 🟡 Medium / 🟢 Low
Problem: One sentence describing the inefficiency.
Suggestion: Concrete fix or alternative approach.
```

Followed by a **Summary**:
- Count of issues by severity
- The single highest-priority fix
- Whether an SCI baseline measurement is warranted

If the code is already well-optimised, the skill says so explicitly — it does not
invent findings.

---

## Explicit Invocation

To run a green review on demand at any point:

```
/green-review
```

You can also paste code or describe what you've built in the same message:

```
/green-review [paste code here]
```

---

## Severity Guide

| Severity | Meaning | Example |
|---|---|---|
| 🔴 High | Significant carbon impact; fix before shipping | Unindexed query on hot path called thousands of times/sec |
| 🟡 Medium | Noticeable impact; worth addressing in current sprint | Polling every 5s instead of using a webhook |
| 🟢 Low | Minor inefficiency; fix when convenient | JSON response includes fields the client never reads |
| ✅ Already Green | Pattern is already well-optimised | Properly configured autoscaling with scale-to-zero |

---

## Agent vs Skill — When to Use Which

| | Skill (`/green-review`) | Agent (`@green-software-engineer`) |
|---|---|---|
| **Best for** | Passive enforcement while coding | Q&A, architecture advice, deep audits |
| **Invoked by** | Claude automatically, or you via `/green-review` | You, explicitly |
| **Output style** | Structured checklist with severity ratings | Conversational, advisory |
| **Context** | Your main conversation | Own isolated context window |

Use the **skill** as your always-on guardrail.
Use the **agent** when you want a dialogue or a considered recommendation.

---

## File Location

```
your-project/
└── .claude/
    └── skills/
        └── green-software/
            └── SKILL.md   ← this skill
```

To make the skill available **across all your projects**, place it in your global
Claude Code config instead:

```
~/.claude/skills/green-software/SKILL.md
```

---

## Adding Supporting Files

Skills can bundle extra resources in the same directory. For example, you could add:

```
.claude/skills/green-software/
├── SKILL.md              ← core instructions (required)
├── sci-calculator.md     ← SCI formula reference Claude can read
├── patterns-reference.md ← quick lookup of GSF patterns
└── scripts/
    └── estimate-sci.py   ← optional helper script
```

Claude will load these files on demand when they're relevant to the review.

---

## References

- [Green Software Foundation](https://greensoftware.foundation)
- [GSF Green Software Patterns](https://patterns.greensoftware.foundation)
- [SCI Specification](https://sci.greensoftware.foundation)
- [Green Software Practitioner Course](https://learn.greensoftware.foundation)
