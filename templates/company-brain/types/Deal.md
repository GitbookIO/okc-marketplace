---
type: Type
title: Deal
icon: handshake
description: A sales opportunity from a CRM, one file per deal.
schema:
  type: object
  properties:
    account:
      type: string
      pattern: '^/accounts/[^/]+\.md$'
      description: Account the deal is with.
    stage:
      type: string
      description: Pipeline stage as the CRM names it.
    close_date:
      type: string
      format: date
      description: Expected or actual close date.
    kind:
      type: string
      enum: [new, renewal, expansion]
      description: New business, renewal or expansion.
    amount:
      type: number
      description: Deal value.
      minimum: 0
    currency:
      type: string
      description: Currency of the amount, like USD.
  required: [account, stage]
---

A deal is one opportunity with an account. An account has many over time: the first sale, renewals, more teams.

- **Layer:** record. Written by ingest workflows, one file per source event. Refinements read records and never edit them.
- **Folder:** `deals/`
- **Filenames:** `deals/<source>-<id>.md`, like `deals/hubspot-901233.md`. Mocks are `deals/mock-<n>.md` with `resource: mock://deals/<n>`.
- **Ingested from:** HubSpot, Salesforce, Attio, Pipedrive.

Example frontmatter:

```yaml
type: Deal
title: Northline renewal 2027
resource: mock://deals/3
account: /accounts/northline.md
stage: negotiation
close_date: 2026-12-15
kind: renewal
```
