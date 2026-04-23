# diffract

> Read new sources through your codebase — and your codebase through them — to make sharp adoption decisions.

`diffract` is a Claude Code plugin (slash command + skill) for teams that need to decide, fast, whether a new paper / library / framework / technique is worth adopting. It's a **four-pass diffractive reading** plus an **implementation tradeoff matrix** with forced verdicts: `adopt now` / `adopt differently` / `watch` / `pass`. No hedging.

The framing is borrowed from feminist epistemology (Karen Barad, Donna Haraway). The goal is practical: produce the non-obvious insight that plain compare-and-contrast reliably misses.

## Why

The agentic-AI tooling landscape is expanding faster than any small team can evaluate. "Read every paper" is not a strategy. "Adopt nothing until it's obvious" is a strategy for falling behind. Most "should we use this?" conversations end in a pros-and-cons list that feels thorough and converts to no decision.

This plugin forces a different shape:

- **Read the source through the codebase, then the codebase through the source.** Each direction surfaces things the other misses.
- **Name the entanglements, not the differences.** Where are you and the source *already* intra-acting — through shared lineage, shared constraints, shared failure modes — independent of adoption?
- **Name the cut.** Adoption is a cut. Non-adoption is also a cut. Both have exclusions. Name them.
- **Force a verdict.** No hedging. `unknown — need <X>` beats a guess, but "it depends" is not a valid answer.

See [`METHODOLOGY.md`](./METHODOLOGY.md) for the philosophical grounding (what diffraction is, why it beats comparison) and [`commands/diffract.md`](./commands/diffract.md) for the full prompt.

## Install

### Claude Code plugin marketplace

```
/plugin marketplace add abehmiel/diffract
/plugin install diffract@diffract
```

(Replace `abehmiel/diffract` with wherever this repo lives.)

### Manual install

Copy the `commands/` and `skills/` directories into a `.claude/` folder at the root of the repo (or your vault) you want to diffract against:

```
your-repo/
└── .claude/
    ├── commands/
    │   └── diffract.md
    └── skills/
        └── diffract/
            └── SKILL.md
```

Or install user-wide by copying into `~/.claude/commands/` and `~/.claude/skills/`.

## Usage

Inside Claude Code, in the repo you want to diffract against:

```
/diffract https://arxiv.org/abs/2510.01234
/diffract github.com/anthropics/claude-agent-sdk
/diffract "adopt Temporal for our durable workflows"
```

Or just ask naturally — the skill will auto-trigger:

```
Should we adopt DSPy for our retrieval pipeline?
Is claude-agent-sdk worth picking up given what we already have?
```

## Output shape

Each run produces:

1. A two-sentence read of what the source *actually* proposes (not what it markets).
2. **Pass 1** — source through codebase. (3–6 bullets, or `no non-obvious refraction here`.)
3. **Pass 2** — codebase through source. (3–6 bullets.)
4. **Pass 3** — 2–4 named entanglements. (What cut does adoption make? What becomes intelligible, what becomes marginalized?)
5. **Pass 4** — the agential cut. Both the cut adoption makes and the cut non-adoption makes.
6. **Implementation tradeoff matrix.** At minimum three rows including `do nothing`, an `adopt differently` variant, and a full-adopt variant. Columns: effort, reversibility, team fit, strategic leverage, competitive asymmetry, distraction tax, honest verdict.
7. **One sentence recommending one action for this week.** Not a roadmap. One action.

## Who this is for

- Small teams (1–10 engineers) shipping in a fast-moving domain who can't afford to adopt every shiny tool.
- Teams whose adoption decisions have real compliance / reliability / brand downside — the cost of a bad "adopt now" isn't just dev-days.
- Teams that already feel the pros-and-cons-list failure mode and want a sharper instrument.

If you have 200 engineers and a dedicated platform team, you probably have enough slack to evaluate things the slow way. This plugin is not for you.

## Not the right tool for

- Bug fixes or patches inside an already-adopted dependency.
- Tactical implementation questions inside a chosen framework.
- Routine dependency upgrades.

Diffraction is about the choice to adopt. Not how to use.

## Credits

The philosophical move here is not ours. Diffraction as method comes from Donna Haraway (*The Promises of Monsters*, 1992; much of her later work) and is developed rigorously by Karen Barad (*Meeting the Universe Halfway*, 2007). What this plugin contributes is the operational form — four passes, a forced-verdict tradeoff matrix, and anti-slop discipline — that makes the methodology usable in a software engineering workflow.

Any unclarity or reduction in that operationalization is ours, not theirs.

## License

MIT. See [`LICENSE`](./LICENSE).
