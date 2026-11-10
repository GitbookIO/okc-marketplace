---
type: Topic
title: "Zero-downtime migrations"
description: "Expand, write to both, backfill, compare, switch, contract, with the order of dual writes and backfill still open for the ledger migration."
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

The ledger migration follows expand and contract: let the new place accept old data, write to both, copy the history, compare, switch, and only then remove the old place.[^sources-mock-1][^sources-mock-5] The expand step is done and dual writes are ready in staging.[^meetings-mock-6][^meetings-mock-8] Whether dual writes or the backfill comes first is still open, and has to be decided by 10 November.[^meetings-mock-8]

## Current understanding

- The steps are expand, dual writes, backfill, compare, cutover and contract. Contract comes last, after a quiet period.[^sources-mock-5][^sources-mock-6]
- Comparing before switching means building every invoice both ways each night. Finance signs off only after two weeks of every account matching.[^meetings-mock-2][^sources-mock-6]
- Backfills should run in batches that can be re-run.[^sources-mock-5]
- Expand is done: the Ledger accepts imported entries marked `origin: legacy`, so they can be told apart.[^meetings-mock-6]
- A backfill of two years of history took about three hours on the staging copy.[^meetings-mock-6]
- The first comparison on staging data matched 397 of 400 accounts. The 3 that didn't were a cent off, because the old tables round once per invoice and the Ledger rounds every label.[^meetings-mock-8]
- The schedule works backwards from the cutover: shadow invoices must start by 10 November for a cutover on 24 November.[^meetings-mock-2][^sources-mock-6][^meetings-mock-8]

## Contradictions

- **Dual writes or backfill first.** The expand and contract write-up says to turn on dual writes first, so nothing written during the backfill is missed.[^sources-mock-5] Dev's plan is to backfill first while the Ledger is quiet, then turn on dual writes and run a catch-up for the gap, so the backfill doesn't fight live writes.[^meetings-mock-2] On 3 November Dev still leaned toward backfill first.[^meetings-mock-8] No record settles it yet.

## Open questions

- Should shadow invoices allow for a cent of rounding, or should invoices already sent be rounded the old way?[^meetings-mock-8]

## See also

- [Idempotency](idempotency.md)
- [Ledger migration](../projects/ledger-migration.md)
- [Dev Okafor](../people/dev-okafor.md) and [Owen Brandt](../people/owen-brandt.md)
