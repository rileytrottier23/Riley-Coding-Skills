# Design Critic — Prompt Template

Use this to dispatch a fresh subagent (e.g. via the `Agent` tool) as an independent design critic. Adapt the bracketed parts; keep the structure — the specificity is what makes the scoring consistent run to run.

---

I want you to critique a UI design. You are seeing this design for the first time — you have no knowledge of how it was built, previous iterations, implementation details, or how much effort went into it. Judge only the attached screenshot(s), on their own merits.

Reference material (treat as a quality baseline / moodboard, not something to copy outright):
[attach 2-4 real reference images — competitor screenshots, LandingHero captures in the same category, or sites you admire]

Evaluate:
1. Think high-level first: overall structure, composition, and whether the design has a distinct point of view — then look at the fine details (spacing, type, color, alignment).
2. Watch for patterns that feel overdone, excessive, or obviously AI-generated: gradients used as filler, the generic hero layout (text-left/graphic-right), decorative elements with no purpose, copy that over-explains. Penalize these specifically.
3. Imagine how a skilled design studio would execute this same aesthetic. Name the single biggest gap between that and what you're looking at.
4. Give tight, specific feedback — name exact elements ("the pink glow behind the progress bar," not "the overall vibe").
5. Be bold and opinionated. Don't default to what's safe or easy to say.

Score the design 1–10 against that studio-level bar.

---

## The iteration loop (run by the builder agent, not the critic)

1. Screenshot the current state.
2. Dispatch the critic fresh — the prompt above, plus the current screenshot and the reference images. New `Agent` call each time; never reuse the critic's context.
3. Apply the critic's specific feedback.
4. Repeat, capped at 3 rounds unless the score is still clearly climbing.
5. Stop when the critic independently scores 9/10+, or when the cap is hit — whichever comes first.

Keep the target score (e.g. "9/10") out of the critic's own prompt. It should score what it sees, not score to satisfy a number it knows you want.
