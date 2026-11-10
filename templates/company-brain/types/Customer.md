---
type: Type
title: Customer
icon: building
description: What Acme knows about a customer, across sales, support and engineering.
schema:
  type: object
  properties:
    account:
      type: string
      pattern: '^/accounts/[^/]+\.md$'
      description: CRM account it is refined from.
    owner:
      type: string
      description: Account owner at Acme.
    health:
      type: string
      enum: [healthy, watch, at risk]
      description: How the relationship is going.
    renewal_date:
      type: string
      format: date
      description: Next renewal.
---

A Customer page joins the account, its deals, meetings, support threads and issues into one current picture.

- **Layer:** concept. Written by refinement workflows, which cite the records they read in `sources` and set `generated`. People review every change on its branch.
- **Folder:** `customers/`
- **Filenames:** `customers/<slug>.md`, matching the account, like `customers/northline.md`.
- **Refined from:** Accounts, deals, meetings, support threads and issues.

Example frontmatter:

```yaml
type: Customer
title: Northline Freight
account: /accounts/northline.md
health: watch
```
