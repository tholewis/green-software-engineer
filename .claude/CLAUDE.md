# Green Software Engineer Project

This project provides a Claude Code agent and skill for embedding Green Software Foundation sustainability practices into development workflows.

## What's in this repo

- `.claude/agents/green-software-engineer.md` — A subagent specialising in sustainability reviews, carbon-aware architecture, and SCI scoring. Invoke with `@green-software-engineer`.
- `.claude/skills/green-software/SKILL.md` — A passive skill that auto-triggers on backend code changes (API endpoints, DB queries, cloud config, background jobs). Also invokable with `/green-review`.
- `.claude/agents/ingeniero-software-verde.md` — Spanish subagent for the same sustainability workflows. Select it with `@` or invoke it manually with `@agent-ingeniero-software-verde`.
- `.claude/skills/revision-verde/SKILL.md` — Spanish sustainability review skill. Invoke with `/revision-verde`.

## How to use these in another project

Copy the `.claude/` folder into the target project, or place the files under `~/.claude/` for global availability across all projects.

## Documentation

| File | Description |
|---|---|
| [`README.md`](../README.md) | Overview, quick start, and agent vs skill comparison |
| [`README.es.md`](../README.es.md) | Spanish overview, installation, attribution, and quick start |
| [`docs/agent-guide.md`](../docs/agent-guide.md) | Full reference for `@green-software-engineer` — use cases, SCI formula, invocation syntax |
| [`docs/agent-guide.es.md`](../docs/agent-guide.es.md) | Spanish reference for `ingeniero-software-verde` |
| [`docs/skill-guide.md`](../docs/skill-guide.md) | Full reference for `/green-review` — auto-trigger rules, checklist, output format |
| [`docs/skill-guide.es.md`](../docs/skill-guide.es.md) | Spanish reference for `/revision-verde` |
| [`docs/llms.txt`](../docs/llms.txt) | AI-optimized summary of this project for LLM consumption |
| [`docs/llms.es.txt`](../docs/llms.es.txt) | AI-optimized Spanish summary |

## References

- [Green Software Foundation](https://greensoftware.foundation)
- [GSF Patterns Library](https://patterns.greensoftware.foundation)
- [SCI Specification](https://sci.greensoftware.foundation)
