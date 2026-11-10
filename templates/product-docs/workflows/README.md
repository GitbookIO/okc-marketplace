# Workflows

Each Markdown file in this folder is a workflow, except this README. Its frontmatter says when it runs and what it may touch, and its body is the prompt the agent follows.

There are two layers:

- **Ingest workflows** (`ingest-*.md`) turn source events into records, one file per event. They read a connection or `inbox/`, write only record folders and `log.md`, and commit to the branch that triggered them.
- **Refinement workflows** read across records and keep the concept pages current. They write only concept folders and `log.md`, watch `main`, and put every change on its own branch for review. Comment on that branch and the same workflow revises its work.

People own `api/openapi.yaml`. Workflows trigger on it and read it, and never write it.

Every run appends one line to `log.md`.

| Workflow | Layer | Trigger | Writes |
| --- | --- | --- | --- |
| [Ingest support threads from Intercom](ingest-support-intercom.md) | Ingest | `intercom`, polls `search_conversations` for closed conversations | `support/` |
| [Ingest support threads from Pylon](ingest-support-pylon.md) | Ingest | `pylon`, polls `search_issues` for closed issues | `support/` |
| [Ingest inbox](ingest-inbox.md) | Ingest | `inbox/**`, any branch | `support/` or `prs/`, then moves the original to `archive/` |
| [Sync reference](sync-reference.md) | Refinement | `api/` change on `main` | `docs/reference/` and `docs/changelog/`, citing the pull requests behind each change |
| [Update guides](update-guides.md) | Refinement | `docs/reference/` change on `main` | `docs/guides/`, answering open gaps, and drafts for frequent ones |
| [Update docs gaps](update-docs-gaps.md) | Refinement | `support/` change on `main` | `gaps/`, one per unanswered question with its threads and a count |
| [Resolve gaps](resolve-gaps.md) | Refinement | `docs/` change on `main` | `gaps/`, closing the ones the docs now answer |
| [Docs gardener](docs-gardener.md) | Refinement | Mondays at 07:00 | `docs/`: broken links, and stale pages that no longer match |
| [Weekly digest](weekly-digest.md) | Refinement | Mondays at 08:00 | `digests/` |

A spec change runs in steps, each on its own branch for review. Merge Sync reference's branch, and Update guides and Resolve gaps both run. Merge Update guides' branch, and Resolve gaps runs again for the guides. Update guides reads gaps but never triggers on them, so the two can't loop.
