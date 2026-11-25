---
name: webhooks
description: How to change Webhooks safely. Use when working on webhook delivery, retries, ordering, queue partitions or payload signatures.
type: Skill
system: /systems/webhooks.md
sources:
  - id: systems-webhooks
    resource: /systems/webhooks.md
    title: "Webhooks"
  - id: specs-mock-2
    resource: /specs/mock-2.md
    title: "Webhook delivery guarantees"
  - id: prs-mock-4
    resource: /prs/mock-4.md
    title: "Deliver retries from a parallel worker pool"
  - id: prs-mock-5
    resource: /prs/mock-5.md
    title: "Partition the delivery queue by shipment"
  - id: prs-mock-6
    resource: /prs/mock-6.md
    title: "Cap delivery retries at 5 attempts"
  - id: incidents-mock-2
    resource: /incidents/mock-2.md
    title: "Webhook deliveries fell 40 minutes behind"
  - id: runbooks-webhook-delivery-backlog
    resource: /runbooks/webhook-delivery-backlog.md
    title: "Webhook delivery backlog"
  - id: decisions-2026-10-17-cap-webhook-retries-at-5
    resource: /decisions/2026-10-17-cap-webhook-retries-at-5.md
    title: "Cap webhook retries at 5 attempts"
generated:
  by: workflow:system-skills:anthropic/claude-opus-5-5
  at: 2026-11-09T07:00:00Z
---

## What it is

Webhooks delivers shipment events to the endpoints customers register, signs every payload, and retries failed deliveries. Customers build their own shipment timelines from these events. ([Webhooks](../../systems/webhooks.md))

## Rules from specs

- Open drift: Webhook delivery guarantees requires up to 8 retries over 24 hours, but retries stop after 5 over about 2 hours, as Platform decided on 17 October. Ask Platform which one holds before touching retry config. ([Webhook delivery guarantees](../../specs/mock-2.md), [Cap delivery retries at 5 attempts](../../prs/mock-6.md), [Cap webhook retries at 5 attempts](../../decisions/2026-10-17-cap-webhook-retries-at-5.md))
- Every event is delivered at least once. ([Webhook delivery guarantees](../../specs/mock-2.md))
- Events for one shipment arrive in the order they happened. Keep the queue partitioned by shipment ID. ([Webhook delivery guarantees](../../specs/mock-2.md), [Partition the delivery queue by shipment](../../prs/mock-5.md))
- Sign the exact bytes sent, with HMAC SHA-256 in the `Acme-Signature` header. ([Webhook delivery guarantees](../../specs/mock-2.md))

## How changes are made here

- Delivery code lives in `src/delivery/`. Ordering is tested in `test/delivery/order.test.ts`. ([Partition the delivery queue by shipment](../../prs/mock-5.md))
- Retry limits live in `config/retry.yaml`, not in code. ([Cap delivery retries at 5 attempts](../../prs/mock-6.md))
- Pull requests say which incident or decision they follow. ([Deliver retries from a parallel worker pool](../../prs/mock-4.md), [Cap delivery retries at 5 attempts](../../prs/mock-6.md))

## Before you merge

- Run the ordering test. A worker pool without partitions delivered events out of order for three weeks. ([Deliver retries from a parallel worker pool](../../prs/mock-4.md), [Partition the delivery queue by shipment](../../prs/mock-5.md))
- Think about a burst of three times the usual tracking volume. One consumer fell 40 minutes behind on 14 October. ([Webhook deliveries fell 40 minutes behind](../../incidents/mock-2.md))
- If deliveries fall behind after a deploy, add consumers until the queue stops growing. ([Webhook delivery backlog](../../runbooks/webhook-delivery-backlog.md))
