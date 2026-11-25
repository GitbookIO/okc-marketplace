---
type: Team
title: Shipping Core
description: Owns quoting, labels and the public Shipments API.
lead: Lena Ito
channel: '#team-shipping-core'
systems: [/systems/label-service.md, /systems/rates-engine.md, /systems/shipments-api.md]
sources:
  - id: systems-label-service
    resource: /systems/label-service.md
    title: Label Service
  - id: systems-rates-engine
    resource: /systems/rates-engine.md
    title: Rates Engine
  - id: systems-shipments-api
    resource: /systems/shipments-api.md
    title: Shipments API
generated:
  by: workflow:update-teams:anthropic/claude-opus-5-5
  at: 2026-11-05T13:00:00Z
stale_after: 2026-12-05T13:00:00Z
---

Shipping Core owns the path from a quote to a label: the public Shipments API, the Rates Engine and Label Service. Carrier reliability is its main topic, after two label outages in two weeks.

## Systems

- [Label Service](/systems/label-service.md): production. ([Label Service](../systems/label-service.md))
- [Rates Engine](/systems/rates-engine.md): production. ([Rates Engine](../systems/rates-engine.md))
- [Shipments API](/systems/shipments-api.md): production. ([Shipments API](../systems/shipments-api.md))

## What's changing

- Carrier label calls time out after 8 seconds, so one slow carrier can't hold every worker. ([Label Service](../systems/label-service.md))
- Carrier rates are cached for 60 minutes instead of 15. ([Rates Engine](../systems/rates-engine.md))
- Multi-parcel quotes are batched, down from 1.4 seconds to 280 ms. ([Rates Engine](../systems/rates-engine.md))
- List shipments pages with a cursor. ([Shipments API](../systems/shipments-api.md))

## Needs attention

- The rate cache drifts from Rate quotes under 300 ms, which requires rates to expire after 15 minutes. ([Rates Engine](../systems/rates-engine.md))
