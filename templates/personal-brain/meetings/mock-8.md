---
type: Meeting
title: "Ledger migration sync"
resource: "mock://meetings/8"
date: 2026-11-03
attendees: [Maya Chen, Dev Okafor, Owen Brandt]
project: "/projects/ledger-migration.md"
duration_minutes: 45
---

## Summary

- Dual writes are ready in staging. The first shadow invoices on staging data matched for 397 of 400 accounts.
- The other 3 were a cent off: the old tables round once per invoice, the Ledger rounds every label.
- Owen says rounding per label is right, but invoices already sent can't change. Open: how shadow invoices should compare the two.
- The order of dual writes and backfill is still open. Maya and Dev decide by 10 November, so shadow invoices can start in production that day.

## Transcript

**Dev Okafor:** Dual writes are in staging. Shadow invoices ran last night on the staging copy: 397 of 400 accounts match.

**Owen Brandt:** And the other three?

**Dev Okafor:** One cent each. The old tables round once per invoice. The Ledger rounds every label.

**Owen Brandt:** Per label is right. That's how customers will see usage invoices. But the invoices we already sent can't change.

**Maya Chen:** So either the comparison allows for rounding, or old invoices get rounded the old way. Let's work out which.

**Maya Chen:** And we still haven't decided the order. Dual writes first or backfill first.

**Dev Okafor:** I still lean backfill first.

**Maya Chen:** Shadow invoices need to run in production by the 10th for Owen's two weeks. So we decide by then.

**Owen Brandt:** Two weeks from the 10th is the 24th. Tight, but fine.
