---
type: Topic
title: "Zero-downtime migrations"
description: "Expand, write to both, backfill, compare, switch, contract. The one thing you haven't settled is dual writes or backfill first."
aliases: ["Dual writes", "Expand and contract"]
related: ["/topics/idempotency.md"]
sources:
  - id: sources-mock-1
    resource: "/sources/mock-1.md"
    title: "Why I'm leading the ledger migration"
  - id: meetings-mock-2
    resource: "/meetings/mock-2.md"
    title: "Ledger migration kickoff"
  - id: sources-mock-5
    resource: "/sources/mock-5.md"
    title: "Expand and contract migrations"
  - id: sources-mock-6
    resource: "/sources/mock-6.md"
    title: "Ledger migration plan"
  - id: meetings-mock-6
    resource: "/meetings/mock-6.md"
    title: "Ledger migration sync"
  - id: meetings-mock-8
    resource: "/meetings/mock-8.md"
    title: "Ledger migration sync"
generated:
  by: "workflow:update-topics:anthropic/claude-opus-5-5"
  at: "2026-11-03T17:40:00Z"
stale_after: "2026-12-03T17:40:00Z"
---

You're running the ledger migration the expand and contract way: let the Ledger take the old data, write to both, copy the history, compare, switch, and only then drop the old tables.[^sources-mock-1][^sources-mock-5] Expand is done and dual writes are ready in staging.[^meetings-mock-6][^meetings-mock-8] What you still haven't settled is whether dual writes or the backfill comes first, and you've given yourself until 10 November.[^meetings-mock-8]

## Current understanding

- The steps: expand, dual writes, backfill, compare, cutover, contract. Contract goes last, after a quiet period.[^sources-mock-5][^sources-mock-6]
- Comparing means building every invoice both ways each night. Owen signs off only after two weeks of every account matching.[^meetings-mock-2][^sources-mock-6]
- Backfill in batches you can re-run.[^sources-mock-5]
- Expand is done: imported entries are marked `origin: legacy`, so finance can tell them apart.[^meetings-mock-6]
- Backfilling two years took Dev about three hours on the staging copy.[^meetings-mock-6]
- First comparison on staging: 397 of 400 accounts matched. The other 3 were a cent off, because the old tables round once per invoice and the Ledger rounds every label.[^meetings-mock-8]
- Working back from cutover on 24 November, shadow invoices have to start by 10 November.[^meetings-mock-2][^sources-mock-6][^meetings-mock-8]

## Contradictions

- **Dual writes or backfill first.** The expand and contract write-up says dual writes first, so nothing written mid-backfill slips through.[^sources-mock-5] Dev wants to backfill first while the Ledger is quiet, then turn on dual writes and run a catch-up, so the backfill doesn't fight live writes.[^meetings-mock-2] On 3 November Dev still leaned that way.[^meetings-mock-8] Nothing you've written settles it yet.

## Open questions

- Should shadow invoices allow a cent of rounding, or should old invoices be rounded the old way?[^meetings-mock-8]

## See also

- [Idempotency](idempotency.md)
- [Ledger migration](../projects/ledger-migration.md)
- [Dev Okafor](../people/dev-okafor.md) and [Owen Brandt](../people/owen-brandt.md)
