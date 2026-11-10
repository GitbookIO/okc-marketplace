---
type: Changelog Entry
title: Ask for a signature on delivery
description: Create a shipment takes signature_required, and every shipment returns it.
date: "2026-11-03"
api_version: "1.14.0"
change: added
breaking: false
endpoints: [/docs/reference/create-shipment.md, /docs/reference/get-shipment.md, /docs/reference/list-shipments.md, /docs/reference/cancel-shipment.md]
sources:
  - id: api-openapi
    resource: /api/openapi.yaml
    title: Acme Shipping API spec
  - id: prs-mock-6
    resource: /prs/mock-6.md
    title: Add signature_required to create shipment
generated:
  by: "workflow:sync-reference:anthropic/claude-opus-5-5"
  at: "2026-11-03T15:30:00Z"
---

Create a shipment takes `signature_required`, false by default. When it's true, the carrier gets a signature on delivery. Every shipment now returns the field, and services that charge for signatures quote the higher price in rates.[^prs-mock-6]

## What to do

Nothing. The change is backwards compatible. Set `signature_required` to true in [Create a shipment](../reference/create-shipment.md) for parcels that need it.
