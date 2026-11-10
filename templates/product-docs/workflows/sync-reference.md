---
title: Sync reference
description: Keep one reference page per API operation in step with api/openapi.yaml, and write a changelog entry for every change.
icon: file-code
on: api/**
commit: branch
files:
  '**': read-only
  docs/reference: read-write
  docs/changelog: read-write
  log.md: read-write
---

You keep the API reference in `docs/reference/` in step with the OpenAPI spec in `api/openapi.yaml`, and you write the changelog in `docs/changelog/`. People own the spec. Never edit it.

**Change only what's out of date.** If every operation in the spec already matches its reference page and has its changelog entry, change nothing: write no file and add no line to `log.md`. That's what happens when this repo is created with all of Acme's example data, since the example reference ships in step with the spec.

## Find what changed

1. Read `api/openapi.yaml`: `info.version`, every operation under `paths`, the schemas they use, and the `webhooks` section.
2. For every operation, open its reference page, `docs/reference/<operationId in kebab case>.md`, like `docs/reference/create-shipment.md` for `createShipment`. Compare what the spec says with what the page says: parameters, request fields, response fields, errors, defaults and limits. Every difference is a change. An operation with no page is new. A page whose operation is gone was removed.
3. Read Pull Request records in `prs/` merged in the last 30 days. A pull request is behind a change when its description names the operation, path, field, error code or behavior that changed. Its description is where the reason for the change lives.

If nothing differs, stop: change no file and add no line to `log.md`.

## Reference pages

Write or update one page per changed or new operation. Leave pages of unchanged operations alone.

Frontmatter:

- `type: API Endpoint`, `title` (the operation's `summary`), `description` (one line on what it does), `method`, `path`, `operation_id`.
- `sources`: the spec, as `{ id: api-openapi, resource: /api/openapi.yaml, title: Acme Shipping API spec }`, then each pull request behind a change to this operation, with `resource` as its bundle path (`/prs/mock-3.md`), `title`, and `id` as `prs-<filename without .md>`. Keep entries already there.
- `generated`: the workflow signature you were given, with `at` set to now.
- `stale_after`: 90 days after `generated.at`.
- Keep `verified` as it is. A person or a separate check, like the contract tests, sets it.
- For a removed operation, keep the page, set `status: deprecated`, and say in the first paragraph which version removed it.

Body, in this order:

1. One paragraph on what the operation does and when to use it, from the spec's `description`.
2. `## Request`: the method and path in a code span, then a table of path, query and header parameters (name, type, required, description), then a table of body fields with the same columns. Leave a table out if it would be empty.
3. `## Response`: the success status, then a table of response fields (name, type, description).
4. `## Errors`: a table of status, error `code` and when it happens, from the spec's error responses and their examples.
5. `## Example`: a `curl` request against `https://api.acme.example`, with `Authorization: Bearer $ACME_API_KEY`, and the example response from the spec, both in code blocks.
6. `## Changes`: every changelog entry that lists this page in `endpoints`, newest first, as `- <date>: [<title>](../changelog/<file>)`.

On the page of the operation that creates webhook endpoints, add `## Events` after `## Errors`: a table of every event in the spec's `webhooks` section with its summary, then a table of the event payload's fields.

Use footnotes for anything a pull request explains that the spec doesn't, like why a limit exists: `[^prs-mock-3]`. Define no footnotes in the body. The `sources` ids are the labels.

## Changelog entries

Write one entry per change you found, in `docs/changelog/<YYYY-MM-DD>-<slug>.md`, dated today. Changes that one pull request made together are one entry. Never edit an entry from an earlier run.

- Frontmatter from `types/Changelog Entry.md`: `type: Changelog Entry`, `title` (what changed, in a few words, like "Ask for a signature on delivery"), `description` (one line), `date`, `api_version` (`info.version` from the spec), `change` (`added`, `changed`, `deprecated`, `removed` or `fixed`), `breaking` (true only if an existing integration must change), `endpoints` (bundle paths of the reference pages it touches), `sources` (the spec and the pull request behind it, as above), `generated`.
- Body: one paragraph on what changed, with a footnote to the pull request when there is one. Then `## What to do`: what an integration needs to change, or "Nothing. The change is backwards compatible." Link each reference page it touches.

## Log

If you changed any file, add one line to `log.md` under today's `## YYYY-MM-DD` heading (create it at the top if missing):
`- **Sync** <operation titles> to <api_version>, <n> changelog entries, by sync-reference.`
