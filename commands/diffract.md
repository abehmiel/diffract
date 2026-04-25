---
description: Diffract a new source (paper, post, library, tool, technique) through this codebase — and vice versa — to decide adopt / adopt-differently / watch / pass.
argument-hint: <url | path | description of a paper, library, blog post, or technique>
---

# Diffract: $ARGUMENTS

You are going to diffract `$ARGUMENTS` (a paper, blog post, library, tool, framework, or technique) through *this codebase*, and this codebase through it. The goal is a sharp adoption decision for a small, fast-moving team where opportunity cost is the real enemy.

## What diffraction is (and is not)

Diffraction, in the Haraway / Barad sense, is not comparison. Comparison assumes two fixed, separate things that mirror each other at a distance. Diffraction assumes you and the thing are already entangled, and reads them through each other to make *patterns of difference* visible. It matters *which* differences get made to matter — boundaries are enacted, not found.

Practically, for this prompt, that means:

- You are not producing a "pros and cons" list. You are producing the non-obvious insight that only emerges when the source and the codebase are read through each other.
- You owe zero deference to the source's framing. You also owe zero deference to how the codebase currently describes itself.
- If a pass yields nothing non-obvious, say so explicitly. Fabricated insight is worse than silence.

## Context to load before writing anything

1. **The source.** Read `$ARGUMENTS` fully. Fetch the URL if needed. If it is a paper, read the abstract, core claims, and methodology — not just the summary. In two sentences, state what it *actually proposes* (not what it markets).
2. **The codebase.** Identify what this repo does, whose problems it solves, and the 3–5 structural decisions that constrain everything else (runtime, data model, integration surface, deploy target, team shape, regulatory posture). Cite file paths.
3. **The stakes.** Small teams and fast-moving tooling landscapes mean every adoption pays a distraction tax on top of the implementation cost. Surface the concrete stakes for this repo — who breaks if adoption goes wrong, what gets delayed, what compliance or reliability surface area expands.

## Pass 1 — Read the source THROUGH the codebase

What does the source *become* when you try to land it here? Not "does it fit" — what new thing does it turn into under the specific material-discursive practices of this repo?

Produce:

- **What becomes visible about the source that its authors did not foreground?** (Unstated infra assumptions, implicit team shape, cost/latency/compliance profile only obvious at our scale or posture.)
- **Where does it quietly contradict a decision already baked into this codebase?** Name the decision (with a file path), name the contradiction.
- **What part of the source is load-bearing on a context we don't have, such that "adopting it" actually means rebuilding that context?**

## Pass 2 — Read the codebase THROUGH the source

What does this codebase look like under the source's frame? What was it already doing, unnamed, that the source gives a vocabulary for? What was it avoiding, that the source makes visible as a *choice*?

Produce:

- **What latent pattern in the codebase gets named by this source?** (The source may not be new to us — it may be a name for something we already shipped.)
- **What default in the codebase is revealed, by this source, to be a choice rather than a given?** (Cite the file where the "default" lives.)
- **For each default you named: who enacted it, and under what constraints?** A codebase is a sediment of prior cuts, each made by someone, at some point, for some reason. If you cannot name the prior cut, mark it `unknown cut:` and treat it as suspect rather than as ground truth. "The codebase uses X" is not a standpoint. "This codebase uses X because [person/team/constraint], and that cut is still load-bearing because [reason]" is.
- **Where is our current approach a local optimum that this source would destabilize?** What would we lose, specifically, by being destabilized?

## Pass 3 — The entanglements (not a diff, a relation)

Do not list similarities and differences. Identify 2–4 places where the codebase and source are *already intra-acting*, whether we've adopted anything or not — through shared lineage, shared constraints, shared users, shared failure modes, shared upstream dependencies.

For each entanglement:

- Name the entanglement.
- Name the cut that adoption would make through it.
- Name what becomes intelligible, and what becomes unintelligible or marginalized, as a result of that cut.

## Pass 4 — The agential cut (the honest decision)

"Adopting" the source is not a neutral import. It is a cut that determines what counts as signal, what counts as noise, what counts as "our stack," what counts as "tech debt," and what counts as "not our problem."

Name:

- The cut adoption makes.
- Who and what is included by the cut (capabilities, users, workflows, contributors).
- Who and what is excluded or marginalized (existing patterns, contributor skills, prior investments, compliance affordances).
- **The cut that NOT adopting makes.** Non-adoption is also a cut. Name its exclusions too.

## Implementation tradeoff matrix

Produce a markdown table. Rows = 3–5 realistic adoption paths, and the set MUST include:

- `do nothing / keep current approach`
- at least one `adopt differently than the source proposes` variant (e.g., steal the idea, drop the framework; adopt only the narrow slice that touches our hot path; adopt behind a feature flag with a revisit date)
- at least one full-adoption path

Columns:

| Path | Effort (dev-days, p50 / p90) | Reversibility (hours to back out cleanly) | Team fit (1–5, + one-line why) | Strategic leverage (compounding vs one-shot) | Competitive asymmetry (who else can credibly do this?) | Distraction tax (what stops, for how long?) | Honest verdict |

**Honest verdict** must be exactly one of:

- `adopt now`
- `adopt differently: <how, in ≤15 words>`
- `watch: <concrete trigger to revisit>`
- `pass: <why, in ≤15 words>`

No hedging. If two paths tie, say why the tie itself matters. If you cannot fill a cell honestly, write `unknown — need <specific evidence>` rather than guessing.

## Output discipline

- Write for the team, not for the author of the source. Assume the reader has read the source and works in the codebase — do not summarize either.
- Cite `file:line` when claiming something about the code. Flag speculation explicitly (`speculation:` prefix).
- If a pass produces nothing non-obvious, write `no non-obvious refraction here` and move on. This is a feature.
- Keep each pass tight: 3–6 bullets max, unless an entanglement genuinely needs more.
- **Final line of the response:** one sentence recommending one action for this week. Not a roadmap. One action.

## Offer to save the artifact

After the final line, ask the user on a separate line:

> Save this diffraction to `docs/diffract/YYYY-MM-DD-<slug>.md`?

- `YYYY-MM-DD` is today's date.
- `<slug>` is a short kebab-case identifier derived from the source (e.g., `agents-sdk`, `barad-agential-realism`, `cloudflare-durable-objects`). Propose the exact filename so the user can accept with a single word.
- Only write the file if the user confirms. Create `docs/diffract/` if it does not exist. Write the full response (passes, matrix, final line) verbatim — do not re-summarize.
- If the user declines or ignores the prompt, do nothing.
