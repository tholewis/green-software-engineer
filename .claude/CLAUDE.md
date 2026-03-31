# Green Software Engineer Project

This project provides a Claude Code agent and skill for embedding Green Software Foundation sustainability practices into development workflows.

## What's in this repo

- `.claude/agents/green-software-engineer.md` — A subagent specialising in sustainability reviews, carbon-aware architecture, and SCI scoring. Invoke with `@green-software-engineer`.
- `.claude/skills/green-software/SKILL.md` — A passive skill that auto-triggers on backend code changes (API endpoints, DB queries, cloud config, background jobs). Also invokable with `/green-review`.

## How to use these in another project

Copy the `.claude/` folder into the target project, or place the files under `~/.claude/` for global availability across all projects.

## References

- [Green Software Foundation](https://greensoftware.foundation)
- [GSF Patterns Library](https://patterns.greensoftware.foundation)
- [SCI Specification](https://sci.greensoftware.foundation)
