# Riley Coding Skills

Coding and engineering Claude skills — TDD, debugging, planning, code review, MCP building, and
frontend/webapp tooling. Versioned here rather than left in a chat history. Part of a three-repo skills
library alongside [riley-pm-skills](https://github.com/rileytrottier23/riley-pm-skills) and
[riley-thinking-skills](https://github.com/rileytrottier23/riley-thinking-skills).

Each skill is a folder containing a `SKILL.md`: an instruction set Claude loads when the skill's
description matches what you are asking for. They work in Claude Projects, Claude Code, and Cowork.

**This repo is also a plugin marketplace** — 19 skills installable in one step. See [Install](#install).

## Layout: `mine/` vs `vendored/`

- **[`mine/`](./mine)** — skills I wrote. MIT ([LICENSE](./LICENSE)). Empty for now; first-party coding
  skills will land here.
- **[`vendored/`](./vendored)** — skills by other people, pinned to an upstream commit and kept under
  their original license. Nothing in here is my work; each folder credits its author.

## Install

```
/plugin marketplace add rileytrottier23/riley-coding-skills
/plugin install superpowers@riley-coding-skills
```

**Claude desktop app / Cowork:** Customize → Plugins → Personal plugins → **+** → Add marketplace →
Add from a repository → `rileytrottier23/riley-coding-skills`

Two plugins, install whichever you want:

| Plugin | Skills | What's in it |
|---|---|---|
| `superpowers` | 14 | Jesse Vincent's coding-agent methodology — TDD, debugging, planning, code review, git worktrees (MIT) |
| `anthropic-coding-skills` | 5 | Anthropic's engineering skills — MCP building, webapp testing, web artifacts, frontend design, Claude API (Apache 2.0) |

> The `superpowers` plugin is named exactly `superpowers` on purpose: its skills cross-reference each
> other as `superpowers:<skill>`, and that only resolves when the installed plugin carries that name.

## Vendored skills (`vendored/`)

| Collection | Author | Skills | License |
|---|---|---|---|
| [obra-superpowers](./vendored/obra-superpowers) | [Jesse Vincent](https://github.com/obra/superpowers) | 14 | MIT |
| [anthropic](./vendored/anthropic) | [Anthropic](https://github.com/anthropics/skills) | 5 | Apache 2.0 |

Each vendored folder is a pinned snapshot, not a live mirror. Updating means a fresh vendor commit
against a newer upstream SHA — never an edit in place — so the diff always shows what changed upstream.

## Using them without the marketplace

Every skill is still a plain folder. Copy the whole directory into your `skills/` directory for Claude
Code, or zip it and upload it under Customize → Skills. Claude triggers it from the description in its
frontmatter — you don't need to invoke it by name.

## License

MIT — see [LICENSE](./LICENSE). Applies to [`mine/`](./mine) only. [`vendored/`](./vendored) keeps each
upstream author's own license (`obra-superpowers` MIT, `anthropic` Apache 2.0), which governs.
