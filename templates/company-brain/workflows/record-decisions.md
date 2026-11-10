---
title: Record decisions
description: Record each decision made in a meeting or discussion, with its options, reasons and who decided.
icon: scale-balanced
on: '{meetings,discussions}/**'
commit: branch
files:
  '**': read-only
  decisions: read-write
  log.md: read-write
---

You record decisions in `decisions/`, so the reasons behind them outlive the meeting or thread they came from and don't live only in people's heads.

**Change only what's out of date.** If every file that triggered this run is already cited in `sources` on the pages you'd write, and those pages already say what it says, change nothing: write no file and add no line to `log.md`. That's what happens when this repo is created with all of Acme's example data, since the example records it ships with are already written up.

For each Meeting or Discussion record that triggered this run:

1. Read it, and the decisions in `decisions/` from the last 180 days.
2. Find each decision in it. A decision is a choice between options that the people who could make it agreed on: a price, a commitment to a customer, a policy, what to build first. A proposal nobody agreed to yet is a decision with `state: proposed`. Questions, status updates and action items aren't decisions. If there's no decision, write nothing.
3. If a decision page for the same choice exists, update it. Otherwise create `decisions/<YYYY-MM-DD>-<slug>.md`, dated the day it was decided, like `decisions/2026-10-14-price-usage-billing-per-label.md`. A new proposed decision gets `status: draft`, which people remove once it's agreed and reviewed.
4. Frontmatter from `types/Decision.md`: `type: Decision`, `title` (the choice, as a statement), `description` (one line), `state`, `decided_on`, `deciders` (the people who agreed, by name, as the record names them), `supersedes` (an earlier decision this one replaces, if it does), `sources` (with `resource` as the bundle path and `id` as `<folder>-<filename without .md>`), `generated` (the workflow signature you were given, `at` now) and `stale_after` (180 days later). Leave out `systems`.
5. Body:
   - `## Decision`: what was decided, in one or two sentences.
   - `## Options considered`: a Mermaid `flowchart TD` from the question to each option, with the chosen one styled, then one line per option.
   - `## Reasons`: why this option won, in the deciders' own reasoning, with footnotes.
   - `## Consequences`: what changes because of it, and what it rules out. Link the customer or project pages it affects, if they exist.
   - `## Who decided`: the deciders and the date.

If a new decision replaces an older one, set the older page's `state` to `superseded`.

Finally, if you changed any file, add one line to `log.md` under today's `## YYYY-MM-DD` heading (create it at the top if missing):
`- **Record** <n> decisions from <n> meetings and discussions, by record-decisions.`
