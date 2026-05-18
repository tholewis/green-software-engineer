# Efficiency Improver — Repo Notes

## Repository Type
**Documentation/configuration-only repository.** Contains:
- `.claude/agents/green-software-engineer.md` — Claude Code subagent definition (markdown)
- `.claude/skills/green-software/SKILL.md` — Claude Code skill definition (markdown)
- `docs/*.md` — reference documentation
- `docs/green-software-with-ai.jpeg` — 482 KB hero image used in README.md
- `README.md` — main readme
- `.github/workflows/efficiency-improver.md` — this workflow's source-of-truth definition (large lock.yml is auto-generated, do NOT touch)

**No application code.** No Python/JS/Go/Rust source files. No tests. No package manager configs.

## What "Efficiency" Means Here
For this repo, the proxy metrics are:
- **Network transfer size**: README hero image, doc page weight when consumed by humans or LLMs
- **Token efficiency**: How concise the agent/skill markdown files are when loaded into Claude's context — every load consumes tokens

Traditional code-level / data / runtime metrics don't apply — there is nothing to execute.

## Image Quality Measurements (2026-05-18)
Source: `docs/green-software-with-ai.jpeg` — 482,060 bytes, 724x1086, JPEG
- WebP q=85 (method=6): 317,520 bytes — 34.1% smaller, PSNR-safe single re-encode
- WebP q=80 (method=6): 266,494 bytes — 44.7% smaller, still high quality
- JPEG q=85 optimize+progressive: 303,797 bytes — 37.0% smaller, drop-in replacement
- Re-encoded JPEG PSNR vs original at q=85: 32.55 dB (acceptable, ≥30 dB)

Original DQT[0] sum ≈ 475 → estimated original encoding quality ~75-80.

## GSF Principles Most Relevant Here
- **Networking** — minimise bytes transferred (hero image is the dominant payload)
- **Measurement & Optimisation** — establish baselines before changing assets
