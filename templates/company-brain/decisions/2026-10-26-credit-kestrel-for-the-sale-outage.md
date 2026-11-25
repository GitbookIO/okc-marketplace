---
type: Decision
title: "Credit Kestrel 20% of October's label fees"
description: Kestrel Outdoor gets a credit for the labels that failed during its sale.
state: accepted
decided_on: 2026-10-26
deciders: [Hana Novak, Sam Reyes, Owen Brandt]
sources:
  - id: discussions-mock-3
    resource: "/discussions/mock-3.md"
    title: "What do we offer Kestrel after the sale outage?"
  - id: meetings-mock-5
    resource: "/meetings/mock-5.md"
    title: "Kestrel Outdoor escalation: labels during the sale"
generated:
  by: "workflow:record-decisions:anthropic/claude-opus-5-5"
  at: "2026-10-27T16:00:00Z"
stale_after: "2027-04-25T16:00:00Z"
verified:
  - by: "human:hana@acme.example"
    at: "2026-10-28T09:00:00Z"
---

## Decision

Kestrel Outdoor gets a [credit of 20% of its October label fees](../discussions/mock-3.md) for the labels that failed during its sale on 24 October. Hana Novak [offered it on 27 October](../meetings/mock-5.md), and Kestrel accepted.

## Options considered

```mermaid
flowchart TD
  q["What does Acme offer Kestrel after the sale outage?"]
  q --> o0["20% of October label fees"]
  q --> o1["A free month"]
  q --> o2["Nothing until failover ships"]
  style o0 stroke-width:3px
```

- **20% of October's label fees**: covers the late orders.
- **A free month**: more than the sale cost Kestrel.
- **Nothing until failover ships**: feels like hiding.

## Reasons

- A [free month](../discussions/mock-3.md) is more than the sale cost Kestrel. 20% of October's label fees covers the late orders.
- [Offering nothing until failover ships](../discussions/mock-3.md) would feel like hiding.
- Kestrel's [renewal is in January](../discussions/mock-3.md), and it asked about other carriers in September.

## Consequences

- Acme [promised failover before Black Friday](../meetings/mock-5.md) on 27 November, which [Carrier failover](../projects/carrier-failover.md) is building.
- [Kestrel Outdoor](../customers/kestrel.md) took the credit, and still [wants failover before Black Friday](../meetings/mock-5.md).

## Who decided

Hana Novak, Sam Reyes and Owen Brandt, on 26 October 2026.
