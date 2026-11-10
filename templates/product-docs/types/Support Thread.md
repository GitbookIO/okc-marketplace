---
type: Type
title: Support Thread
icon: headset
description: A customer conversation from a support tool, one file per thread.
schema:
  type: object
  properties:
    account:
      type: string
      pattern: '^/accounts/[^/]+\.md$'
      description: Customer account that asked.
    state:
      type: string
      enum: [open, snoozed, closed]
      description: Whether the conversation is still open.
    opened_at:
      type: string
      format: date-time
      description: When the customer wrote in.
    closed_at:
      type: string
      format: date-time
      description: When the thread was closed.
    area:
      type: string
      description: Product area the question is about.
    channel:
      type: string
      description: Where it came in, like email or chat.
  required: [state, opened_at]
---

A support thread keeps what a customer asked and what they were told. Docs gaps and Customer pages are refined from these.

- **Layer:** record. Written by ingest workflows, one file per source event. Refinements read records and never edit them.
- **Folder:** `support/`
- **Filenames:** `support/<source>-<id>.md`, like `support/intercom-88412.md`. Mocks are `support/mock-<n>.md` with `resource: mock://support/<n>`.
- **Ingested from:** Intercom, Pylon, Plain, Zendesk, Front, Freshdesk, Help Scout.

Example frontmatter:

```yaml
type: Support Thread
title: Webhook retries arrive out of order
resource: mock://support/5
account: /accounts/northline.md
state: closed
opened_at: 2026-11-02T08:40:00Z
area: webhooks
```
