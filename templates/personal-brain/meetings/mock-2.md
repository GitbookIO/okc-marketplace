---
type: Meeting
title: "Ledger migration kickoff"
resource: "mock://meetings/2"
date: 2026-10-06
attendees: [Maya Chen, Dev Okafor, Owen Brandt]
project: "/projects/ledger-migration.md"
duration_minutes: 45
---

## Summary

- Phases: the Ledger accepts imported entries, dual writes from the Billing API, a backfill of two years of history, shadow invoices, cutover, then the old tables go.
- Owen signs off on the cutover only after shadow invoices match the old ones for every account for two weeks.
- Dev wants to backfill first, then turn on dual writes, with a catch-up run for the gap. Maya has read it the other way round. Not settled.
- Cutover target: 24 November, which needs shadow invoices running by 10 November.

## Transcript

**Maya Chen:** The goal is one place for every charge, credit and refund. Usage billing invoices per label, and the old tables only know monthly totals.

**Owen Brandt:** Finance needs one thing: invoices can't change. Same totals, to the cent, for every account.

**Maya Chen:** So we build invoices both ways and compare. Shadow invoices.

**Owen Brandt:** For two weeks, every account, before I sign off.

**Dev Okafor:** For the history, I'd backfill first while the Ledger is quiet, then turn on dual writes, then run a short catch-up for whatever landed in between.

**Maya Chen:** I've read it the other way round. Dual writes first, so nothing slips through during the backfill.

**Dev Okafor:** The catch-up covers that, and the backfill doesn't fight live writes.

**Maya Chen:** Let's not settle it today. Cutover on 24 November works if shadow invoices start by the 10th.

**Owen Brandt:** Works for me.
