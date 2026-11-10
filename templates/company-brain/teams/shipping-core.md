---
type: Team
title: Shipping Core
description: "Builds the carrier integrations behind rates, labels and shipments."
lead: Lena Ito
channel: "#team-shipping-core"
sources:
  - id: projects-carrier-failover
    resource: "/projects/carrier-failover.md"
    title: Carrier failover
  - id: projects-saturday-delivery
    resource: "/projects/saturday-delivery.md"
    title: Saturday delivery
generated:
  by: "workflow:update-teams:anthropic/claude-opus-5-5"
  at: "2026-11-07T10:00:00Z"
stale_after: "2026-12-07T10:00:00Z"
---

Shipping Core is shipping carrier failover before Black Friday, mostly for Kestrel Outdoor, and planning Saturday delivery for Tidewater Pharmacy.[^projects-carrier-failover][^projects-saturday-delivery]

## Projects

- [Carrier failover](../projects/carrier-failover.md): active, target 20 November 2026.[^projects-carrier-failover]
- [Saturday delivery](../projects/saturday-delivery.md): planned, target 1 February 2027.[^projects-saturday-delivery]

## Customers

- [Kestrel Outdoor](../customers/kestrel.md): Carrier failover.
- [Tidewater Pharmacy](../customers/tidewater.md): Saturday delivery.

## Risks

- If the failover test on 20 November slips, there's a week left before Black Friday.[^projects-carrier-failover]
- Nobody is assigned to failover alerting yet.[^projects-carrier-failover]
- Parcelline covers only two of Tidewater's three regions on Saturdays.[^projects-saturday-delivery]

## Needs review

- [Tidewater Pharmacy](../customers/tidewater.md): past its review date since 7 November, last written by update-customers.
