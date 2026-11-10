---
type: Changelog Entry
title: Choose the label format
description: "Buy a label takes label_format: pdf_4x6, pdf_a4 or zpl."
date: "2026-11-06"
api_version: "1.15.0"
change: added
breaking: false
endpoints: [/docs/reference/buy-label.md]
sources:
  - id: api-openapi
    resource: /api/openapi.yaml
    title: Acme Shipping API spec
  - id: prs-mock-8
    resource: /prs/mock-8.md
    title: Let callers choose the label format
generated:
  by: "workflow:sync-reference:anthropic/claude-opus-5-5"
  at: "2026-11-06T12:45:00Z"
---

Buy a label takes `label_format`: `pdf_4x6`, the default and the only format until now, `pdf_a4`, or `zpl` for thermal printers. The label says which format its file is in.[^prs-mock-8]

## What to do

Nothing. The change is backwards compatible. Pass `label_format` to [Buy a label](../reference/buy-label.md) to get another format.
