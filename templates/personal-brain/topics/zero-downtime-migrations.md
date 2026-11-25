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

You're [running the ledger migration](../sources/mock-1.md) the [expand and contract way](../sources/mock-5.md): let the Ledger take the old data, write to both, copy the history, compare, switch, and only then drop the old tables. [Expand is done](../meetings/mock-6.md) and [dual writes are ready in staging](../meetings/mock-8.md). What you still haven't settled is whether dual writes or the backfill comes first, and you've given yourself until 10 November.

## Current understanding

- The steps: [expand, dual writes, backfill, compare, cutover, contract](../sources/mock-5.md). Contract goes last, after [a quiet period](../sources/mock-6.md).
- [Comparing means building every invoice both ways each night](../sources/mock-6.md). [Owen signs off only after two weeks of every account matching](../meetings/mock-2.md).
- [Backfill in batches you can re-run](../sources/mock-5.md).
- [Expand is done](../meetings/mock-6.md): imported entries are marked `origin: legacy`, so finance can tell them apart.
- [Backfilling two years took Dev about three hours](../meetings/mock-6.md) on the staging copy.
- First comparison on staging: [397 of 400 accounts matched](../meetings/mock-8.md). The other 3 were a cent off, because the old tables round once per invoice and the Ledger rounds every label.
- Working back from [cutover on 24 November](../meetings/mock-2.md), [shadow invoices](../sources/mock-6.md) have to start by [10 November](../meetings/mock-8.md).

## Contradictions

- **Dual writes or backfill first.** [The expand and contract write-up](../sources/mock-5.md) says dual writes first, so nothing written mid-backfill slips through. [Dev wants to backfill first](../meetings/mock-2.md) while the Ledger is quiet, then turn on dual writes and run a catch-up, so the backfill doesn't fight live writes. On 3 November [Dev still leaned that way](../meetings/mock-8.md). Nothing you've written settles it yet.

## Open questions

- Should [shadow invoices allow a cent of rounding](../meetings/mock-8.md), or should old invoices be rounded the old way?

## See also

- [Idempotency](idempotency.md)
- [Ledger migration](../projects/ledger-migration.md)
- [Dev Okafor](../people/dev-okafor.md) and [Owen Brandt](../people/owen-brandt.md)
