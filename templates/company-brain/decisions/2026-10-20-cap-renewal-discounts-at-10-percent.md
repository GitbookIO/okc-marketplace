---
type: Decision
title: "Cap renewal discounts at 10% without finance approval"
description: "Sales can give up to 10% off a renewal. Anything more needs Owen Brandt."
state: accepted
decided_on: 2026-10-20
deciders: [Sam Reyes, Owen Brandt]
sources:
  - id: discussions-mock-4
    resource: "/discussions/mock-4.md"
    title: "How far can we go on renewal discounts?"
generated:
  by: "workflow:record-decisions:anthropic/claude-opus-5-5"
  at: "2026-10-20T16:00:00Z"
stale_after: "2027-04-18T16:00:00Z"
---

## Decision

Sales can give up to 10% off a renewal without asking finance. Anything above that needs Owen Brandt's approval, with the account's usage.[^discussions-mock-4]

## Options considered

```mermaid
flowchart TD
  q["How far can sales go on renewal discounts?"]
  q --> o0["Up to 10% without finance"]
  q --> o1["Case by case"]
  style o0 stroke-width:3px
```

- **Up to 10% without finance**: a clear limit sales can say no with.
- **Case by case**: last year's way, where some discounts went to 25%.

## Reasons

- Case by case let some renewals go to 25%, which is too far.[^discussions-mock-4]
- A clear limit helps account managers say no faster.[^discussions-mock-4]

## Consequences

- The renewals for [Northline Freight](../customers/northline.md) and [Kestrel Outdoor](../customers/kestrel.md) follow the limit.[^discussions-mock-4]
- Discounts above 10% go to Owen with the account's usage.[^discussions-mock-4]

## Who decided

Sam Reyes and Owen Brandt, on 20 October 2026.
