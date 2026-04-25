# Diffractive Reading for Adoption Decisions

A methodology for deciding whether a new external source — a paper, library, blog post, framework, or technique — is worth adopting into a codebase you already care about. Borrowed from feminist epistemology (Donna Haraway, Karen Barad) and operationalized as a Claude Code slash command and skill.

## The Problem

The agentic-AI tooling landscape is expanding faster than any small team can evaluate. "Read every paper" is not a strategy. "Adopt nothing until it's obvious" is a strategy for falling behind. We need a repeatable way to decide, per source: **adopt now, adopt differently, watch, or pass** — with a bias toward the "adopt differently" move (steal the idea, drop the framework) that usually fits a small team best.

The failure mode this resists is the familiar one: pros-and-cons lists, a paragraph of hedged "it depends," and no decision. Those outputs *feel* thorough and are cheap to produce. They don't convert to action.

## Why Diffraction (Not Comparison)

Comparison assumes two fixed, separate things that mirror each other at a distance: "here's our codebase, here's the paper, here are the similarities and differences." It treats both as stable objects with clean surfaces.

Diffraction, in Barad's sense, assumes the codebase and the source are already entangled — through shared lineage, shared constraints, shared users, shared upstream dependencies, shared failure modes — and reads them *through each other* to surface patterns of difference that neither side could articulate alone.

The practical payoff is the insight a comparison would miss:

- A latent pattern in the codebase the source names for the first time. (You already built it; now you have a word for it.)
- A default in the codebase the source reveals to be a *choice* rather than a given.
- A load-bearing assumption in the source that only becomes visible when you try to land it at your scale, your compliance posture, your team's cognitive budget.

These are the insights that change what you do. "Both have retries and state machines" is not.

## The Four Passes

### Pass 1 — Read the source THROUGH the codebase

What does the source *become* when refracted through your material practices? Not "does it fit" — what new thing does it turn into when you try to land it here?

- What becomes visible about the source that its authors did not foreground? (Unstated infra assumptions, implicit team shape, cost/latency/compliance profile only obvious at your scale.)
- Where does it quietly contradict a decision already baked into this repo? Name the decision (cite a file path). Name the contradiction.
- What part of the source is load-bearing on a context you don't have, such that "adopting it" actually means rebuilding that context?

### Pass 2 — Read the codebase THROUGH the source

What does the codebase look like under the source's frame? What was it already doing, unnamed, that the source gives a vocabulary for? What was it avoiding, that the source makes visible as a *choice*?

- What latent pattern gets named by this source? (The source may not be new — it may be a name for what you already shipped.)
- What default in the codebase is revealed, by this source, to be a choice rather than a given?
- For each default you named: who enacted it, and under what constraints? If you cannot name a prior cut — a specific decision, made by someone, at some point, for some reason — you are treating a sediment of prior decisions as a given. Name the cut or mark it `unknown cut:`. "The codebase uses X" is not a standpoint. "This codebase uses X because [person/team/constraint], and that cut is still load-bearing because [reason]" is.
- Where is the current approach a local optimum that this source would destabilize? What would you lose by being destabilized?

### Pass 3 — The entanglements (not a diff, a relation)

Do not list similarities and differences. Identify 2–4 places where the codebase and source are *already intra-acting*, independent of adoption — through shared lineage, shared constraints, shared users, shared failure modes, shared upstream dependencies. These are the load-bearing places where adoption would not be "adding a new thing" but *re-cutting* an existing entanglement.

For each entanglement: name the entanglement, name the cut adoption would make, name what becomes intelligible or unintelligible as a result.

### Pass 4 — The agential cut

Barad: boundaries are enacted, not found. Adoption is not a neutral import. It is a cut that determines what counts as signal, what counts as noise, what counts as "our stack," what counts as "tech debt," and what counts as "not our problem."

Name:

- The cut adoption makes.
- Who and what is included by the cut.
- Who and what is excluded or marginalized.
- The cut that *not* adopting makes. Non-adoption is also a cut.

## The Implementation Tradeoff Matrix

Forces at least three adoption paths, including `do nothing / keep current approach` and at least one `adopt differently than the source proposes` variant. Columns cover effort (p50/p90 dev-days), reversibility (hours to back out), team fit, strategic leverage, competitive asymmetry, distraction tax, and an honest verdict constrained to four values:

- `adopt now`
- `adopt differently: <how>` (≤15 words)
- `watch: <concrete trigger to revisit>`
- `pass: <why>` (≤15 words)

Hedging is disallowed. `unknown — need <specific evidence>` is the correct answer when a cell can't be filled honestly.

## Anti-Slop Discipline

Three rules make or break the output:

- **`no non-obvious refraction here`** is an allowed and encouraged output for a given pass. Synthetic insight is worse than acknowledged silence.
- **File:line citations** for every claim about the code. `speculation:` prefix when extrapolating.
- **Final line is one sentence recommending one action for this week.** Not a roadmap. Not a quarter plan. One action.

## When to Use It

- A teammate shares a paper / repo / thread and asks "should we use this?"
- A new agentic harness or SDK crosses the team's radar and competes for attention with existing work.
- Before adding a dependency that would change your material practices — a new agent framework, a new orchestration layer, a new data plane.
- As a deliberate monthly practice against 2–3 of the most interesting recent sources, to keep the team's adoption pipeline honest.

## When Not to Use It

- Evaluating a bug fix or a patch to an existing dependency. The cut has already been made.
- Tactical implementation questions inside an already-chosen framework. Diffraction is about the *choice to adopt*, not the *how to use*.
- Sources with no credible claim to reshape any of your load-bearing decisions. The full four passes will produce thin output and waste the team's attention.

## Credits

The philosophical work here is not ours. What follows names what we borrowed and from whom.

**Donna Haraway** introduced diffraction as a feminist alternative to reflection. Where reflection reproduces the same image at a distance, diffraction tracks difference — it asks what patterns emerge when waves (of light, of meaning, of knowledge) pass through and interfere with each other. The move appears in "The Promises of Monsters" (1992) and is further developed in *Modest_Witness@Second_Millennium* (1997). Haraway draws the optics metaphor partly from Trinh T. Minh-ha, whose work on non-appropriative, non-reflective modes of knowing (*Woman, Native, Other*, 1989) established that how you look determines what can be seen — and whose seeing is erased. Haraway's situated knowledges — the argument that partial, located perspectives are the condition of genuine objectivity, not an obstacle to it — is where Passes 1 and 2 of this methodology draw their justification. Reading the source *through* the codebase and the codebase *through* the source is only coherent if you accept that there is no view from nowhere, only situated views that can be held accountable.

**Karen Barad** gives us agential realism, intra-action, and the agential cut (*Meeting the Universe Halfway*, 2007). Intra-action: entities do not pre-exist their relations and then interact; they are constituted through their entanglements. The agential cut: boundaries between things are enacted by specific material-discursive practices, not found in nature. Barad's framework draws on Niels Bohr's philosophy-physics — specifically Bohr's insistence that the apparatus of measurement is not separable from what is measured, and that phenomena (not objects) are the primary units of ontological analysis. Pass 3 (entanglements) and Pass 4 (the agential cut) are direct translations of Barad's concepts into adoption-decision form.

**Sandra Harding** (*Whose Science? Whose Knowledge?*, 1991) and **Patricia Hill Collins** (*Black Feminist Thought*, 1990) established that standpoint — where you are located in systems of power — is an epistemological resource, not just a bias to be corrected. Strong objectivity requires examining background assumptions and the social relations that produce them. The four passes assume this: a codebase is not a neutral artifact, and neither is the person evaluating an external source against it.

**What this operationalization loses.** Haraway and Barad are doing feminist science studies. The political stakes of their work are explicit: who gets to produce knowledge, whose practices are rendered invisible by dominant epistemic frameworks, what accountability for knowledge-making looks like under conditions of unequal power. This plugin converts those stakes into a software adoption workflow. That is itself a reduction. The agential cut in Pass 4 asks "who and what is excluded" — but the exclusions that matter most to Barad are not library dependencies. Using this methodology will not make an adoption decision feminist. It will, at best, make it more honest about what the decision enacts and what it forecloses.

We name that reduction not as a disclaimer but as a location: this tool operates at a particular scale with particular constraints, and those constraints are themselves a cut. Any unclarity or distortion in the operationalization is ours. The source material is precise.
