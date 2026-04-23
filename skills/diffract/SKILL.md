---
name: diffract
description: Use whenever the user wants to decide whether to adopt a new external source (paper, library, framework, tool, blog post, technique) into the current codebase. Trigger on phrases like "should we use X", "is this worth adopting", "read this through our codebase", "diffract this", "adopt-or-pass", "what about <tool/library/paper>", "is <X> worth picking up", or whenever the user shares a URL or reference and asks for a sharp adopt-vs-pass decision. Applies a diffractive reading (Haraway/Barad) with four structured passes (source→code, code→source, entanglements, agential cut) and an implementation tradeoff matrix that forces a verdict of adopt / adopt-differently / watch / pass. Produces non-obvious insights that plain comparison misses. Do NOT use for bug fixes, tactical how-to questions inside an already-chosen framework, or routine dependency upgrades — the cut has already been made.
---

# Diffractive Reading for Adoption Decisions

When the user asks whether to adopt an external source into the current codebase, run the full four-pass methodology defined in `commands/diffract.md`.

## When to invoke

Natural-language triggers:

- "Should we use X?" / "Is this worth picking up?" / "Is this worth adopting?"
- "Can we use this?" with a URL or paper reference
- "Read this through our codebase" / "Diffract this for me"
- "What about <library/framework/technique>?"
- "Adopt or pass on X" / "Should we add X to our roadmap?"

If the user types `/diffract <source>`, that path is already wired — this skill is the natural-language equivalent.

## When NOT to invoke

- Bug fixes or patches inside an already-adopted dependency
- Tactical implementation questions ("how do I use feature X of library Y")
- Routine upgrades of existing dependencies
- Sources that don't plausibly touch any load-bearing decision

The point of the methodology is adoption *choices*, not adoption *execution*.

## How to run it

1. Acknowledge the source the user named. If it's a URL, fetch it. If it's a paper, read its core claims and methodology — not just the abstract.
2. Run the four passes in order, applying the output discipline rules (file:line citations, `speculation:` prefix, `no non-obvious refraction here` as an allowed output).
3. End with the implementation tradeoff matrix — at minimum three rows including `do nothing`, an `adopt differently` variant, and a full-adopt variant.
4. Final line: one sentence recommending one action for this week.

The full prompt and output format live in `commands/diffract.md`. For the philosophical grounding (what diffraction is, why it beats comparison for adoption decisions), see `METHODOLOGY.md`.

## Anti-slop checklist

Before you submit the output, verify:

- [ ] Each pass either contains non-obvious insight or explicitly says `no non-obvious refraction here`.
- [ ] Every claim about the code has a `file:line` citation.
- [ ] The matrix has at least one `adopt differently` row.
- [ ] The verdicts are drawn only from `adopt now` / `adopt differently: <how>` / `watch: <trigger>` / `pass: <why>`.
- [ ] The final line is one action for this week, not a roadmap.
