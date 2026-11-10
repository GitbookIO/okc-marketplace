---
type: Source
title: "Ledger migration plan"
resource: "mock://sources/6"
kind: note
captured_at: "2026-10-09T17:30:00Z"
author: Maya Chen
---

## Summary

The ledger migration plan as sent to Nadia: six steps from expand to contract, cutover on 24 November, shadow invoices from 10 November, and the order of dual writes and backfill still open.

## Note

Plan, as sent to Nadia.

1. Expand: the Ledger accepts imported entries, marked as legacy. Dev.
2. Dual writes: the Billing API writes credits and refunds to the old tables and to the Ledger. Dev.
3. Backfill: two years of credits, refunds and invoices into the Ledger. Me.
4. Shadow invoices: build every invoice both ways, every night, and compare. Owen signs off after two weeks with every account matching.
5. Cutover: invoices read from the Ledger. 24 November.
6. Contract: drop the old tables in January.

Shadow invoices have to start by 10 November for the 24th to work.

Still open: steps 2 and 3 in which order. Dev wants backfill first, the expand and contract write-up says dual writes first.
