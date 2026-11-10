---
type: Source
title: "Ledger migration plan"
resource: "mock://sources/6"
kind: note
captured_at: "2026-10-09T17:30:00Z"
author: Maya Chen
---

## Summary

My migration plan as sent to Nadia: six steps from expand to contract, cutover on 24 November, shadow invoices from 10 November. I still haven't picked dual writes or backfill first.

## Note

Migration plan, as sent to Nadia.

1. Expand: Ledger accepts imported entries, marked legacy. (Dev)
2. Dual writes: Billing API writes credits and refunds to the old tables AND the Ledger. (Dev)
3. Backfill: two years of credits, refunds and invoices into the Ledger. (me)
4. Shadow invoices: build every invoice both ways, nightly, compare. Owen signs off after two weeks of every account matching.
5. Cutover: invoices read from the Ledger. 24 Nov.
6. Contract: drop the old tables in January.

Working back from the 24th: shadow invoices have to start by 10 Nov.

Still haven't settled 2 vs 3. Dev says backfill first, the write-up says dual writes first. Need to pick before it picks itself.
