---
type: Person
title: "Dev Okafor"
description: "Engineer on Payments who builds the ledger migration with Maya and owns its backfill."
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

Dev Okafor works with Maya on Payments. He builds dual writes and metering, and has owned the ledger migration's backfill since 21 October.[^sources-mock-6][^sources-mock-9][^sources-mock-13]

## Recent conversations

- 6 November, in Maya's notes: Dev's metering counts a label when it's bought.[^sources-mock-13]
- 3 November, migration sync: dual writes are ready in staging, and shadow invoices matched 397 of 400 accounts. Dev still leans toward backfill first.[^meetings-mock-8]
- 24 October, in Maya's notes: Dev reported that billing shipped 3 retries 10 seconds apart, not the RFC's 5.[^sources-mock-10]
- 21 October: Maya handed him the backfill, with a week of pairing and an agreed review.[^sources-mock-9]
- 20 October, migration sync: the Ledger accepts imported entries, and a backfill test over two years took about three hours.[^meetings-mock-6]
- 12 October, idempotency review: Dev pointed out that a lock per purchase wouldn't stop a webhook arriving twice, and that the Ledger should return the first entry instead of an error.[^meetings-mock-3]
- 7 October, in Maya's notes: Dev's backfill-first order is the opposite of the expand and contract write-up.[^sources-mock-5]
- 6 October, kickoff: Dev proposed backfilling first, then dual writes, then a catch-up run.[^meetings-mock-2]

## Open commitments

- Dev and Maya decide whether dual writes or the backfill comes first, by 10 November.[^meetings-mock-8]

## Topics

- [Zero-downtime migrations](../topics/zero-downtime-migrations.md)
- [Idempotency](../topics/idempotency.md)
- [Delegation](../topics/delegation.md)
