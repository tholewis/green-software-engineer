# Discovered Commands

**Discovered:** 2026-05-18

## Build / Test / Benchmark
**None.** This is a documentation-only repository. No build system, test suite, or benchmarking infrastructure exists.

## Lint / Format
**None configured.** No `.editorconfig`, no `.prettierrc`, no `markdownlint` config. Markdown files follow GitHub-flavored markdown conventions informally.

## Profiling
**N/A** — no code to profile.

## CI Files Reviewed
- `.github/workflows/efficiency-improver.md` (source) and `.lock.yml` (auto-generated) — this is the only workflow

## Notes
- Sandbox environment has `python3` and `node` available; `Pillow` (`pip install Pillow`) installs cleanly when image measurement is needed.
- `cwebp` / `avifenc` / `ImageMagick` are **not** preinstalled.
