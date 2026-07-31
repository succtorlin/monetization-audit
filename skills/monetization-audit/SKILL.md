---
name: monetization-audit
description: Use when asked how a project could make money, whether monetization opportunities are being missed, to research pricing or competitors for an existing codebase, or to turn a project into a revenue plan with concrete executable next steps.
---

# Monetization Audit

## Overview

Scan what a project actually is, research what its market actually pays for,
diff the two, and emit **action specs an agent can execute** — not advice.

Core principle: every claim traces to either a file in the repo or a dated
source on the internet. Analysis that cites neither is opinion and gets cut.

## When to use

- "How can this project make money?" / "What monetization are we missing?"
- Pricing, packaging, or competitor research for something that already exists
- Turning an audit's findings into work an agent can start immediately

When NOT to use: picking which *skill* to productize (use skill-productizer —
its 13-forms taxonomy is the vocabulary for Phase 4 here); inventorying
personal assets across projects (use productize-real-assets).

## Phase 1 — Scan the project, not the pitch

Inventory from the repo and running state, never from memory or the README's
self-description. Record file paths as evidence.

- **Sellable surfaces**: features, data assets/pipelines, integrations, APIs,
  reports/exports. Check each is *live*, not aspirational — dead code and
  flag-gated demos are not assets (verify consumers/routes exist).
- **Monetization infrastructure already present**: billing/payments code,
  auth tiers, usage metering, license files, pricing pages. Usually the
  answer is "none" — say so explicitly; absence is a finding.
- **Distribution state**: deployed where, public repos, install paths,
  existing users/tenants (count them from the DB if reachable).
- **Compliance/procurement artifacts** the target market will demand
  (security posture, accessibility conformance, data-handling docs).

Output: an asset table `asset | evidence (path) | live? | monetized?` for the
sellable surfaces, then the other three categories as labelled subsections
beneath it (they don't fit the table's columns — don't force them).
`live?` values: `yes` / `no` / `partial (one-line why)` — partial covers the
common case of a shipped spine with an unmerged enhancement.

## Phase 2 — Research with receipts

Web-research the market. **Every finding gets a URL and an access date;
prior knowledge without a source is a hypothesis to verify, not a finding.**

- 2–4 comparable products: their pricing model, tiers, and actual numbers
- The category's dominant monetization pattern (seat / usage / outcome /
  services) and any known failures of that pattern
- Forcing functions: regulation, procurement requirements, platform policy
  changes that *compel* buying (verify status and dates — "in force since"
  beats "upcoming")
- Distribution channels: marketplaces, directories, communities where this
  category's buyers already are

Output: findings table `claim | source URL | date checked | confidence`.

## Phase 3 — Gap analysis

Diff Phase 1 against Phase 2 in both directions:

- **Opportunity gaps**: market pays for X, project has X, nothing connects
  them (no packaging, no page, no listing)
- **Execution gaps**: what's missing to charge money — billing, tiers,
  license, compliance artifact, case study
- **Moat check**: which assets are hard to copy (data, verified results,
  install base) vs commodity

Rank by distance-to-revenue, not by size of opportunity.

## Phase 4 — Action specs, not recommendations

Each proposal becomes a spec an agent can execute. Format:

Two kinds of spec are legal:

- **Product spec** — the deliverable is itself sold (one of the 13 forms)
- **Enabler spec** — the deliverable unblocks a sale but isn't sold
  (compliance artifact, case study, pricing page, marketplace listing).
  Its Form line reads `enabler → unblocks <form>` and its revenue
  hypothesis names the *downstream* sale and its date, not a direct one.

```markdown
### AS-<n>: <imperative title>
- Form: <one of skill-productizer's 13 forms | enabler → unblocks <form>>
- Revenue hypothesis: who pays, for what, first plausible dollar date
  (for enablers: the downstream sale this unblocks)
- Evidence: Phase 2 finding IDs — minimum 2 independent sources for any
  spec that gates real work; single-source specs are marked low-confidence
- Deliverable: the concrete artifact (file, page, package, listing draft)
- Agent steps: numbered; each names a file to write or command to run
- Human-only steps: account creation, payment setup, legal signoff,
  publishing decisions — listed separately, never silently absorbed
- Verification: how we know it worked (measurable)
- Effort: S / M / L
```

The human-only list is mandatory: an agent must not create accounts, enter
payment credentials, or publish on someone's behalf — specs that need those
mark them for the human and sequence agent work around them.

## Output

One dated report: `docs/monetization/<YYYY-MM-DD>-audit.md` in the project
(or the path the user names), containing all four phase outputs. The report
is the deliverable; chat is just the summary.

Bounded runs (a single phase, a dry run, "just the scan") are fine — state
the scope at the top of whatever is produced and skip the report file; the
report contract applies to full audits only.

## Common mistakes

| Mistake | Fix |
|---|---|
| Auditing from conversation memory | Phase 1 reads the repo; cite paths |
| Market claims from training data | No URL + date → not a finding |
| "You could build a SaaS" advice | Every proposal is an AS-spec or it's cut |
| Counting dead/demo code as assets | Verify consumers and routes exist |
| Ignoring what's needed to *charge* | Execution gaps are first-class findings |
| Ranking by opportunity size | Rank by distance-to-revenue |
