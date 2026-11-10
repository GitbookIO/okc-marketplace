# Workflows

Each Markdown file in this folder is a workflow, except this README. Its frontmatter says when it runs and what it may touch, and its body is the prompt the agent follows.

There are two layers:

- **Ingest workflows** (`ingest-*.md`) turn what comes in into records, one file per item. They read a connection or `inbox/`, write only record folders and `log.md`, and commit to the branch that triggered them.
- **Refinement workflows** read across records and keep the pages current. They write only page folders and `log.md`, watch `main`, and put every change on its own branch for review. Comment on that branch and the same workflow revises its work.

Every run that changes something appends one line to `log.md`.

| Workflow | Layer | Trigger | Writes |
| --- | --- | --- | --- |
| [Ingest meetings from Granola](ingest-meetings-granola.md) | Ingest | `granola`, polls `search_meetings` from a fixed date | `meetings/` |
| [Ingest meetings from Fireflies](ingest-meetings-fireflies.md) | Ingest | `fireflies`, polls `fireflies_get_transcripts` | `meetings/` |
| [Ingest inbox](ingest-inbox.md) | Ingest | `inbox/**`, any branch | `sources/`, or `meetings/` for meeting notes, then moves the original to `archive/` |
| [Update topics](update-topics.md) | Refinement | `sources/` or `meetings/` change on `main` | `topics/`, with contradictions listed and drafts for new topics |
| [Update projects](update-projects.md) | Refinement | `sources/` or `meetings/` change on `main` | `projects/`, with drafts for new projects |
| [Update people](update-people.md) | Refinement | `sources/` or `meetings/` change on `main` | `people/`, for people named in two or more records |
| [Gardener](gardener.md) | Refinement | Mondays at 07:00 | Merges duplicate topics, fixes links in `topics/`, `people/` and `projects/`, and keeps the Pages section of `index.md` |
| [Weekly review](weekly-review.md) | Refinement | Mondays at 08:00 | `digests/` |

A note runs in steps, each on its own branch for review. Drop it into `inbox/` on a branch, and Ingest inbox writes the record there. Merge it, and Update topics, Update projects and Update people each open a branch. The Gardener edits other workflows' pages only to merge duplicate topics and fix links, and it owns the Pages section of `index.md`.
