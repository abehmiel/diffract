---
name: diffract
description: Decide whether to adopt an external source (paper, library, tool, technique) into the current codebase. Triggers on "should we use X", "is X worth adopting", "diffract this", "adopt or pass", or a shared URL with an adoption question. Runs a four-pass diffractive reading (Haraway/Barad) and forces a verdict of adopt / adopt-differently / watch / pass. Skip for bug fixes, how-to questions inside an already-adopted dependency, or routine upgrades.
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
5. Offer to save the result to `docs/diffract/YYYY-MM-DD-<slug>.md`. Propose the exact filename; write the file verbatim only if the user confirms.

The full prompt and output format live in `commands/diffract.md`. For the philosophical grounding (what diffraction is, why it beats comparison for adoption decisions), see `METHODOLOGY.md`.

## Anti-slop checklist

Before you submit the output, verify:

- [ ] Each pass either contains non-obvious insight or explicitly says `no non-obvious refraction here`.
- [ ] Every claim about the code has a `file:line` citation.
- [ ] The matrix has at least one `adopt differently` row.
- [ ] The verdicts are drawn only from `adopt now` / `adopt differently: <how>` / `watch: <trigger>` / `pass: <why>`.
- [ ] The final line is one action for this week, not a roadmap.
