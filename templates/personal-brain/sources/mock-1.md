---
type: Source
title: "Why I'm leading the ledger migration"
resource: "mock://sources/1"
kind: note
captured_at: "2026-09-28T19:40:00Z"
author: Maya Chen
---

## Summary

Why Maya is starting the ledger migration: usage-based invoices need credits, refunds and invoice history in the Ledger, the cutover has to land before the beta on 1 December, and she plans to run the backfill herself because the riskiest part should stay with the lead.

## Note

Starting the ledger migration this week. Writing down why before I forget.

Usage-based billing charges per label. The Ledger has every charge, but credits, refunds and two years of invoices still live in the old billing tables, which only know monthly totals per account. Usage invoices should come from one place, so all of it moves into the Ledger and invoices switch over. Has to happen before the beta on 1 December.

Rough shape, the expand and contract way: make the Ledger accept the old entries, write to both, copy the history, compare, switch, then drop the old tables.

I'm going to run the backfill myself. It's the riskiest step, and the riskiest part should stay with whoever leads the project. If it goes wrong I want it to be on me.
