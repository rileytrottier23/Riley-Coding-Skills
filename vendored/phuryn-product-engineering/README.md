# Product Engineering — Paweł Huryn

One skill from [phuryn/product-engineering](https://github.com/phuryn/product-engineering), by **Paweł
Huryn** (The Product Compass). Vendored at upstream `e7d9e7e`, synced 2026-11-25.

## What was and wasn't vendored

Only `agent-harness/skills/windows-agent-shell` came across, with its scripts, references and receipts.
It covers the traps a coding agent hits on Windows: Git Bash path rewriting, PowerShell quoting and
encoding, CRLF, and Claude Code auto mode on Windows. The other packs (product, ai-shipping, agent-teams,
app-stack, work-humanizer) are not vendored. A few lines point to skills from those packs
(`guardrail-hooks`, `test-harness`); they aren't installed here.

## License

**MIT** — see [`LICENSE.md`](./LICENSE.md), preserved from upstream (Copyright (c) 2026 Pawel Huryn).

## The skills

| Skill | What it does |
|---|---|
| [windows-agent-shell](./windows-agent-shell) | Windows shell traps for coding agents: paths, quoting, encoding, line endings, auto mode. |
