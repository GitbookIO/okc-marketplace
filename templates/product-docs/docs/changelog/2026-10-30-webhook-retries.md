---
type: Changelog Entry
title: Webhook retries stop after 5 attempts
description: Failed webhook deliveries are retried 5 times over about 2 hours, down from 8 times over 24 hours.
date: "2026-10-30"
api_version: "1.13.0"
change: changed
breaking: false
endpoints: [/docs/reference/create-webhook-endpoint.md]
sources:
  - id: api-openapi
    resource: /api/openapi.yaml
    title: Acme Shipping API spec
  - id: prs-mock-5
    resource: /prs/mock-5.md
    title: Cap delivery retries at 5 attempts
generated:
  by: "workflow:sync-reference:anthropic/claude-opus-5-5"
  at: "2026-10-30T12:30:00Z"
---

A failed delivery is retried 5 times over about 2 hours, with growing gaps, and then marked as failed. It used to be retried 8 times over 24 hours.[^prs-mock-5]

## What to do

If your endpoint can be down for more than 2 hours, you'll miss the events sent in that time. Alert on failed deliveries, and catch up with [Get a shipment](../reference/get-shipment.md) and [Get tracking](../reference/get-tracking.md). See [Create a webhook endpoint](../reference/create-webhook-endpoint.md).
