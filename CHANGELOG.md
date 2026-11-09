# Changelog

Newest first.

- 2026-11-09 — Re-synced vendored `antislop` 941b153 (v3.2.25) → 3b75daa (v3.2.27): `antislop-copywriting`
  adds three patterns (temporal runway clichés, theatrical takeaways, title case in list items) and
  `antislop-human`'s contrast MCP server rejects malformed hex colours. 27 skills total.

- 2026-11-08 — `mine/vibe-design-loop`: runs Impeccable's rule-based slop detector (CLI only, no hook,
  no live mode) before each critic round, and asks the critic for a ranked critique plus a P0-P3 audit,
  borrowed from Impeccable's `critique` and `audit` commands (pbakaus/impeccable, Apache 2.0). 27 skills total.

- 2026-11-02 — Re-synced three vendored collections to upstream. `obra-superpowers` b36e082 (v6.3.0) →
  22f0b46 (v7.0.2): brainstorming rebuilt (fewer questions, asks why first, a builder check replaces the
  spec reviewer), `executing-plans` now runs inline in the current session, new SDD/plan helper scripts,
  and `systematic-debugging` no longer ships its pressure-test prompts. `anthropic` f379e5a → ca45fc4:
  `claude-api`, `frontend-design` and `mcp-builder` updated. `antislop` 11dc5c1 (v3.2.7) → 941b153
  (v3.2.25): core, UI, copywriting and accessibility skills updated, with new reference files. Same 14
  superpowers skills as before (upstream's new `diagnosing-superpowers` not pulled). 27 skills total.

- 2026-09-25 — Added `mine/vibe-design-loop`. 27 skills total.
- 2026-09-25 — Added `mine/code-cowork-handoff`, the first first-party skill here. New
  `riley-coding-skills` plugin for `mine/`. 26 skills total.
- 2026-09-13 — Added `vendored/miqdadbadjuber-antislop` (6, MIT), a filter that stops AI coding agents
  from shipping generic UI, copy, and code comments, plus a mandatory delivery gate. New `antislop`
  plugin. 25 skills total.
- 2026-08-23 — Created from the split of Riley-Claude-Skills into three domain repos. Holds the
  coding/engineering bucket, all vendored for now: `obra-superpowers` (14, MIT) and the engineering
  Anthropic skills (mcp-builder, webapp-testing, web-artifacts-builder, frontend-design, claude-api;
  5, Apache 2.0). `mine/` is empty, reserved for first-party coding skills. 19 skills total.
