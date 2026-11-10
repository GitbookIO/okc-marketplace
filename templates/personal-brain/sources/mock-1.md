---
type: Source
title: "Why I'm leading the ledger migration"
resource: "mock://sources/1"
kind: note
captured_at: "2026-09-28T19:40:00Z"
author: Maya Chen
---

## Summary

Starting the ledger migration. Credits, refunds and two years of invoices have to move into the Ledger so usage invoices come from one place, before the beta on 1 December. I'm doing the backfill myself, since the riskiest part should stay with the lead.

## Note

Ledger migration, day one. Writing down the why before I forget it.

Usage billing is per label. The Ledger has every charge, but credits, refunds and two years of invoices still live in the old billing tables, and those only know monthly totals per account. So all of it moves into the Ledger and invoices switch over. Has to land before the beta on 1 Dec. No slack.

Shape, the expand and contract way: Ledger accepts old entries → write to both → copy history → compare → switch → drop old tables.

I'm doing the backfill myself. Riskiest step, and the riskiest part should stay with whoever leads. If it goes wrong I want it to be on me.
