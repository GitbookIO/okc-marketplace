---
type: Changelog Entry
title: Reject unknown postal codes
description: Create a shipment returns invalid_postal_code when the destination postal code doesn't exist.
date: "2026-10-15"
api_version: "1.10.0"
change: changed
breaking: false
endpoints: [/docs/reference/create-shipment.md]
sources:
  - id: api-openapi
    resource: /api/openapi.yaml
    title: Acme Shipping API spec
  - id: prs-mock-1
    resource: /prs/mock-1.md
    title: Validate postal codes before creating shipments
generated:
  by: "workflow:sync-reference:anthropic/claude-opus-5-5"
  at: "2026-10-15T10:30:00Z"
---

Create a shipment now checks the destination postal code against the destination country, and returns a 422 with `invalid_postal_code` if it doesn't exist. Until now a bad postal code only failed when the carrier rejected the label.[^prs-mock-1]

## What to do

Handle a 422 with `invalid_postal_code` from [Create a shipment](../reference/create-shipment.md) by asking for the address again. Requests with valid postal codes work as before.
