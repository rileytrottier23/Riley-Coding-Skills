---
name: vibe-design-loop
description: Run a structured Discover → Define → Deliver loop to push AI-generated UI/visual design past the default "AI slop" look — inject real variety before committing to a direction, score iterations with a fresh-context critic subagent against real reference images, then run a subtractive polish pass. Trigger whenever building or improving vibe-coded UI, a landing page, an app screen, or any visual design where the first draft feels generic, templated, or "like every other AI-generated site" — including when asked to make something look more premium, distinctive, or polished, or before shipping a design.
---

# Vibe Design Loop

Most AI-generated UI looks the same: purplish gradient with text-left/graphic-right, warm-cream-and-serif, or near-black-with-one-accent-color. That's not because the model can't do better — an LLM predicts the most likely next token, and "most likely" converges on the safest, most average-looking choice at every decision point. Getting past that takes deliberately injecting variety and judgment the model won't supply on its own.

This is a process skill, not a style guide. It composes with `frontend-design` (which covers palette/type/layout principles and the AI-tell calibration) by wrapping a Discover → Define → Deliver loop around whatever that skill, or any coding agent, produces.

## When to run this

- Before locking in a visual direction for something new — run Discover first, don't build on the first draft that comes out.
- Before calling any vibe-coded UI "done" — run at least one Define (critic) pass.
- Whenever a design feels like "every other AI site," feels safe or generic, or the human says "make it feel more premium / less AI."

## Discover: get real variety before you commit

Don't ask the model for "something unique" — it fakes randomness (same palette, same layout, different filler words). Force actual variety instead, with one of two moves:

**Seed strings.** Have the agent generate a random string and derive the design from *that*, rather than from its own priors.

> Build me [a landing page / a screen / a UI] for [subject]. Follow this procedure:
> 1. Generate a long, random alphanumeric string using a shell script.
> 2. Define the creative direction (color scheme, layout, typography, etc.) based on the string — look beyond the surface for subpatterns, numbers, anything that inspires you.
> 3. Use your judgment to bring this direction to life and make it look great.
>
> Don't reveal the string in the design; it's only for your inspiration.

**Ambitious, taste-anchored prompts.** Name an outside inspiration — a video game, an interior-design style, an art movement — rather than an adjective like "clean" or "modern." If you don't have an inspiration yet, widen the option set before narrowing:
1. Ask for many shallow ideas: "List as many bold, distinct design directions as you can, one line each. Go broad, not deep."
2. React to the ones that land — say what you like and don't, and let the agent sharpen just those.
3. Only then ask it to write the actual build prompt for the one you picked.

Generate 3-4 divergent directions this way before choosing one. Don't build on the first thing that comes out.

## Define: score it with a critic that isn't grading its own homework

The agent that built the design can't judge it objectively — it's defending its own choices and can't easily "zoom out." Use a **separate, fresh-context subagent** as a critic instead. Dispatch it with the `Agent` tool so it's genuinely a different context, not a follow-up message in the same thread.

Rules that make this actually work — skip any of these and the loop degrades into noise:

- **Fresh context every round.** The critic sees only the current screenshot, never the code, the build history, or its own earlier critiques.
- **Objective, concrete criteria over vibes.** "Judge if it looks beautiful, not AI-generated" produces wildly inconsistent results. "Rank against these professional examples" produces a real signal.
- **Reference images matter more than the prompt.** Point the critic at real comparison material — screenshots you like, files dropped in this skill's `references/` folder, or a category browse of [LandingHero](https://www.landinghero.ai/library) — and tell it to treat them as a baseline/moodboard, not something to copy outright.
- **Cap the iterations.** Without a stopping rule the critic can nitpick forever and burn tokens chasing an unreachable bar. Run 2-3 rounds, check whether the score is still climbing, and only extend if it clearly is.
- **Don't put the passing score inside the critic's own prompt.** Keep "what counts as done" external to what the critic sees, so its scoring stays honest rather than tuned to hit a number.
- **Bigger model for the critic than the builder is fine and often better** — taste is an expensive judgment call made rarely; execution is cheap and made often.

Full copy-paste prompt template and the iteration loop: `references/critic-prompt.md`.

## Deliver: cut, don't add

AI adds; it rarely subtracts. The clearest tell that something is AI-generated is elements that don't earn their place: glow effects on things that don't need to glow, labels next to things the visual already communicates, custom form controls that look worse than native ones.

Before calling a design done, run one explicit removal pass and ask of each element:

- Is this decorative but not load-bearing? Cut it.
- Is this a custom component doing what a native/built-in one already does, worse? Swap it back.
- Is this text explaining something the visual already shows? Cut it.
- Does this look "safe" rather than deliberate — a choice that could belong to any product? Replace or cut it.

Restraint reads as premium. If nothing gets cut on this pass, you didn't look hard enough.

## References folder

Drop screenshots, competitor UI, or [LandingHero](https://www.landinghero.ai/library) captures you like into `references/` and point the critic at them for that project or category. No references yet? Fall back to: "imagine how a top design studio would execute this aesthetic, then judge against that bar" — weaker than real images, but still better than no anchor.

## Never

- Never let the same context both build and grade the design — that's not a critic, that's the builder agreeing with itself.
- Never run the critic loop with no stopping condition.
- Never hardcode an image/video-generation API key into shipped code. Put it in a gitignored file (e.g. `.env.agents`) and note in `CLAUDE.md`/`AGENTS.md` that it's dev-only, not for the product.
- Never treat a design skill's install count as a taste signal. Popularity and output quality are unrelated — run any third-party design skill's output through this loop's critic before trusting it.
