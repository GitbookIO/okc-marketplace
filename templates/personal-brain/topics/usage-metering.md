---
type: Topic
title: "Usage metering"
description: "A label counts when it's bought, minus voids within 24 hours. Where a month ends depends on who you ask."
status: draft
related: ["/topics/api-design.md"]
sources:
  - id: meetings-mock-9
    resource: "/meetings/mock-9.md"
    title: "Bramble & Co usage billing beta call"
  - id: sources-mock-13
    resource: "/sources/mock-13.md"
    title: "Metering: what counts as a label bought"
generated:
  by: "workflow:update-topics:anthropic/claude-opus-5-5"
  at: "2026-11-06T17:20:00Z"
stale_after: "2026-12-06T17:20:00Z"
---

Metering counts a label when it's bought, and a label voided within 24 hours isn't billed, so a month's count can go down after the fact. ([Metering: what counts as a label bought](../sources/mock-13.md)) Where the month ends is the part nobody agrees on. ([Bramble & Co usage billing beta call](../meetings/mock-9.md), [Metering: what counts as a label bought](../sources/mock-13.md))

## Current understanding

- A label counts when it's bought. ([Metering: what counts as a label bought](../sources/mock-13.md))
- Voided within 24 hours means not billed, and the usage page has to show the count going down. ([Metering: what counts as a label bought](../sources/mock-13.md))
- The beta's first invoices come with a CSV of every label bought. ([Metering: what counts as a label bought](../sources/mock-13.md))

## Contradictions

- **Where a month ends.** Owen wants every invoice to close at midnight UTC, the same for everyone. ([Metering: what counts as a label bought](../sources/mock-13.md)) Bramble's finance team closes the month on Amsterdam time, so a label bought at 00:30 on 1 December in Rotterdam is November for Acme and December for Bramble. ([Bramble & Co usage billing beta call](../meetings/mock-9.md), [Metering: what counts as a label bought](../sources/mock-13.md))

## Open questions

- Show both months, or tell beta customers it's UTC? ([Metering: what counts as a label bought](../sources/mock-13.md))

## See also

- [API design](api-design.md)
- [Usage-based billing](../projects/usage-based-billing.md)
- [Owen Brandt](../people/owen-brandt.md) and [Felix Grant](../people/felix-grant.md)
