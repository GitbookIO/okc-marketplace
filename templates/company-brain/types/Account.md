---
type: Type
title: Account
icon: address-card
description: A company record from a CRM, one file per account.
schema:
  type: object
  properties:
    domain:
      type: string
      description: Company web domain.
    owner:
      type: string
      description: Account owner at Acme.
    tier:
      type: string
      description: Plan or segment, like enterprise or growth.
    lifecycle_stage:
      type: string
      description: CRM lifecycle stage, like customer or opportunity.
  required: [domain]
---

An account is the CRM's view of a company. Deals, meetings, support threads and issues link to it, and the Customer page is refined from all of them.

- **Layer:** record. Written by ingest workflows, one file per source event. Refinements read records and never edit them.
- **Folder:** `accounts/`
- **Filenames:** `accounts/<slug>.md`, like `accounts/northline.md`, so other records can link to it by name. `resource` keeps the CRM URL, or `mock://accounts/<n>` for mocks.
- **Ingested from:** HubSpot, Salesforce, Attio, Pipedrive.

Example frontmatter:

```yaml
type: Account
title: Northline Freight
resource: mock://accounts/1
domain: northline.example
owner: Sam Reyes
tier: enterprise
lifecycle_stage: customer
```
