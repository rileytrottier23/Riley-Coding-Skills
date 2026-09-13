# Anti Slop — Miqdad Badjuber

Six skills from [miqdadbadjuber/anti-slop](https://github.com/miqdadbadjuber/anti-slop), by **Miqdad
Badjuber**. Vendored at upstream `11dc5c1` (v3.2.7), synced 2026-09-13.

Anti Slop is a filter, not a style guide: 38 rules across three tiers that stop an AI coding agent from
shipping generic output — bland UI, cliché copy, decorative comments — without dictating specific colors,
fonts, or layouts. A mandatory PASS/FAIL "Delivery Gate" runs before anything ships.

## What was and wasn't vendored

Only the `skills/` tree came across — the six skill folders, including the two Python contrast-checker
scripts under `antislop-human/`. Upstream also ships a standalone `antislop.md` (the same core content as
the `antislop` skill below, packaged for manual paste into any chat) and installers for other agent
runtimes (Cursor, Codex, Antigravity, a `npx antislop-ai` CLI). None of that packaging is vendored — this
repo is skills-only, and the `antislop` skill folder below already carries the full core.

## License

**MIT** — see [`LICENSE`](./LICENSE), preserved from upstream (Copyright (c) 2026 Miqdad Badjuber).

## The skills

| Skill | What it does |
|---|---|
| [antislop](./antislop) | The core filter — load it whenever building or editing UI, copy, or code that should read as crafted rather than generated. |
| [antislop-ui](./antislop-ui) | UI/visual depth: color, layout, components, decoration, motion. |
| [antislop-code](./antislop-code) | Code-comment hygiene — strips generic AI-slop comments, keeps the ones that carry real information. |
| [antislop-copywriting](./antislop-copywriting) | Copy and text depth: headlines, CTAs, tone, anti-AI-writing patterns. |
| [antislop-human](./antislop-human) | Accessibility depth: contrast, keyboard, focus, states — includes a runnable contrast checker. |
| [antislop-layoutmobile](./antislop-layoutmobile) | Responsive-layout depth: breakpoints, grids, overflow, tap targets. |

Each of the five depth skills references the core's rules by number (`R-XX`) rather than duplicating them
— load `antislop` alongside whichever depth skill(s) the task touches.

Not a live mirror — a pinned snapshot. Updating means a fresh vendor commit against a newer upstream SHA,
never an edit in place, so the diff always shows what changed upstream.
