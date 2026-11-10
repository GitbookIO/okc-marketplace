---
type: Pull Request
title: Cap delivery retries at 5 attempts
resource: "mock://prs/5"
number: 211
repository: acme/webhooks
state: merged
author: tomas-silva
merged_at: "2026-10-30T11:00:00Z"
systems: [/systems/webhooks.md]
---

A failed delivery is now retried 5 times over about 2 hours, with growing gaps, then marked as failed. It used to be 8 times over 24 hours. Endpoints that stayed down for a day were filling the queue.

## Changed files

- `src/delivery/retry.ts`
- `config/retry.yaml`
