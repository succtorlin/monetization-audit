# monetization-audit

**An agent skill that turns "how could this project make money?" into a scanned inventory, sourced market research, a gap analysis, and action specs an agent can execute.**

Most monetization advice fails in one of two ways: it's generated from the model's memory of your project instead of the project itself, or it ends at "you could build a SaaS" — a recommendation nobody can act on. This skill forbids both.

## The discipline

Every claim traces to either **a file in the repo** or **a dated source on the internet**. Analysis that cites neither is opinion and gets cut.

Four phases, each with an enforced output contract:

1. **Scan the project, not the pitch** — inventory sellable surfaces from the repo and running state (dead code and flag-gated demos don't count; consumers and routes are verified), existing monetization infrastructure (its absence is an explicit finding, and it usually is absent), distribution state, and the compliance artifacts the target market will demand.
2. **Research with receipts** — comparable products and their actual pricing, the category's dominant monetization pattern, regulatory or procurement **forcing functions** that compel buying, and distribution channels. Every finding carries a URL and access date; prior knowledge without a source is a hypothesis to verify, not a finding.
3. **Gap analysis** — diff the two in both directions: opportunity gaps (the market pays for X, the project has X, nothing connects them) and execution gaps (what's missing to actually *charge* — billing, tiers, license, compliance artifact, case study). Ranked by distance-to-revenue, not by size of opportunity.
4. **Action specs, not recommendations** — every proposal is a spec with numbered agent steps naming files and commands, evidence citations (minimum two independent sources for anything that gates real work), measurable verification, and a mandatory **human-only** list: account creation, payment setup, legal signoff, and publish decisions are never silently absorbed by the agent.

Two kinds of spec are legal: **product specs** (the deliverable is sold) and **enabler specs** (the deliverable unblocks a sale — a conformance report, a case study, a pricing page — with the revenue hypothesis naming the *downstream* sale).

## Built with TDD for documentation

This skill was written against a documented baseline failure (an audit that scanned nothing, researched nothing, and produced advice), then tested by having a fresh agent execute it against a real production codebase. The test agent's six ambiguity reports were each resolved and re-verified. The output-format rules in the skill are the ones that survived that loop.

## Companions

Pairs with [skill-productizer](https://github.com/SpaceZephyr/skill-productizer)'s 13-forms taxonomy (the vocabulary for Phase 4's `Form:` line) and [productize-real-assets](https://github.com/succtorlin/productize-real-assets) (cross-project personal asset inventory). This skill is the per-project deep audit.

## Install

```bash
git clone https://github.com/succtorlin/monetization-audit.git
cp -r monetization-audit/skills/monetization-audit ~/.claude/skills/
```

## Use

Once installed, Claude picks it up on prompts like:

- *"How can this project make money?"*
- *"What monetization opportunities are we missing?"*
- *"Research pricing and competitors for this product"*
- *"Turn this codebase into a revenue plan I can act on"*

Bounded runs are supported — "just run the scan phase" produces the Phase 1 inventory with the scope stated, no full report required.

## Output

A dated report at `docs/monetization/<YYYY-MM-DD>-audit.md` in the audited project, containing all four phase outputs. The report is the deliverable; chat is just the summary.

## License

MIT — see [LICENSE](LICENSE).
