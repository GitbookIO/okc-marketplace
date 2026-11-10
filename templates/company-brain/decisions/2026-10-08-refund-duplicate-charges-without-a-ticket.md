---
type: Decision
title: Refund duplicate charges without waiting for a ticket
description: "Every label charged twice on 2 October is refunded, whether or not the customer asked."
state: accepted
decided_on: 2026-10-08
deciders: [Hana Novak, Maya Chen, Owen Brandt]
sources:
  - id: discussions-mock-1
    resource: "/discussions/mock-1.md"
    title: "Do we wait for tickets before refunding duplicate charges?"
generated:
  by: "workflow:record-decisions:anthropic/claude-opus-5-5"
  at: "2026-10-08T16:00:00Z"
stale_after: "2027-04-06T16:00:00Z"
---

## Decision

Every label charged twice on 2 October is refunded without waiting for the customer to ask, and each affected account gets an email.[^discussions-mock-1]

## Options considered

```mermaid
flowchart TD
  q["Who gets a refund for the duplicate charges?"]
  q --> o0["Everyone, without a ticket"]
  q --> o1["Only customers who ask"]
  style o0 stroke-width:3px
```

- **Everyone, without a ticket**: Acme knows exactly which charges were duplicates.
- **Only customers who ask**: most customers would never get their money back.

## Reasons

- Acme knows exactly which charges were duplicates, and waiting for tickets means most people never get their money back.[^discussions-mock-1]
- It's about 3,100 dollars across 41 accounts.[^discussions-mock-1]

## Consequences

- Payments refunds all 41 accounts and emails each one. Support doesn't need a ticket to start a refund.[^discussions-mock-1]

## Who decided

Hana Novak, Maya Chen and Owen Brandt, on 8 October 2026.
