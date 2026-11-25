---
type: Person
title: "Dev Okafor"
description: "Builds the ledger migration with you, and owns its backfill."
organization: Acme
aliases: ["Dev"]
sources:
  - id: meetings-mock-2
    resource: "/meetings/mock-2.md"
    title: "Ledger migration kickoff"
  - id: sources-mock-5
    resource: "/sources/mock-5.md"
    title: "Expand and contract migrations"
  - id: sources-mock-6
    resource: "/sources/mock-6.md"
    title: "Ledger migration plan"
  - id: meetings-mock-3
    resource: "/meetings/mock-3.md"
    title: "Idempotent charges review"
  - id: meetings-mock-6
    resource: "/meetings/mock-6.md"
    title: "Ledger migration sync"
  - id: sources-mock-9
    resource: "/sources/mock-9.md"
    title: "Handing the backfill to Dev"
  - id: sources-mock-10
    resource: "/sources/mock-10.md"
    title: "Retries: the RFC and what shipped"
  - id: meetings-mock-8
    resource: "/meetings/mock-8.md"
    title: "Ledger migration sync"
  - id: sources-mock-13
    resource: "/sources/mock-13.md"
    title: "Metering: what counts as a label bought"
generated:
  by: "workflow:update-people:anthropic/claude-opus-5-5"
  at: "2026-11-06T17:20:00Z"
stale_after: "2027-01-05T17:20:00Z"
---

Dev works with you on Payments: [dual writes](../sources/mock-6.md), [metering](../sources/mock-13.md), and since 21 October the [ledger migration's backfill](../sources/mock-9.md).

## Recent conversations

- 6 November, your notes on [Metering: what counts as a label bought](../sources/mock-13.md): Dev's metering counts a label when it's bought.
- 3 November, [Ledger migration sync](../meetings/mock-8.md): dual writes are ready in staging, and 397 of 400 accounts matched. Dev still leans backfill first.
- 24 October, your notes on [Retries: the RFC and what shipped](../sources/mock-10.md): per Dev, billing shipped 3 retries 10 seconds apart, not the RFC's 5.
- 21 October, [Handing the backfill to Dev](../sources/mock-9.md): you handed Dev the backfill, with a week of pairing and an agreed review.
- 20 October, [Ledger migration sync](../meetings/mock-6.md): the Ledger takes imported entries, and a backfill test over two years took about three hours.
- 12 October, [Idempotent charges review](../meetings/mock-3.md): a lock per purchase wouldn't stop a webhook arriving twice, and the Ledger should return the first entry instead of an error.
- 7 October, your notes on [Expand and contract migrations](../sources/mock-5.md): Dev's backfill-first order is the opposite of the expand and contract write-up.
- 6 October, [Ledger migration kickoff](../meetings/mock-2.md): Dev proposed backfill first, then dual writes, then a catch-up run.

## Open commitments

- You and Dev decide [dual writes or backfill first](../meetings/mock-8.md), by 10 November.

## Topics

- [Zero-downtime migrations](../topics/zero-downtime-migrations.md)
- [Idempotency](../topics/idempotency.md)
- [Delegation](../topics/delegation.md)
