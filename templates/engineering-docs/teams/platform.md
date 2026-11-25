---
type: Team
title: Platform
description: Owns tracking events and webhook delivery.
lead: Tomás Silva
channel: '#team-platform'
systems: [/systems/tracking-events.md, /systems/webhooks.md]
sources:
  - id: systems-tracking-events
    resource: /systems/tracking-events.md
    title: Tracking Events
  - id: systems-webhooks
    resource: /systems/webhooks.md
    title: Webhooks
generated:
  by: workflow:update-teams:anthropic/claude-opus-5-5
  at: 2026-11-07T10:00:00Z
stale_after: 2026-12-07T10:00:00Z
---

Platform owns how carrier tracking updates come in and how shipment events go out to customers. This month it fixed out-of-order webhooks and made stalled carrier feeds recover on their own.

## Systems

- [Tracking Events](/systems/tracking-events.md): production.
- [Webhooks](/systems/webhooks.md): production.

## What's changing

- [Webhook events for one shipment arrive in order again](../systems/webhooks.md), through a queue partitioned by shipment.
- [Failed webhook deliveries stop after 5 attempts](../systems/webhooks.md) over about 2 hours.
- [Raw carrier events are kept for 14 days](../systems/tracking-events.md) so dropped updates can be replayed.
- [Carrier feed pollers refresh their token](../systems/tracking-events.md) and restart on auth errors.

## Needs attention

- [Webhook retries drift](../systems/webhooks.md) from Webhook delivery guarantees, which requires 8 retries over 24 hours.
