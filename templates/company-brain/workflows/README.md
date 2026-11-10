# Workflows

Each Markdown file in this folder is a workflow, except this README. Its frontmatter says when it runs and what it may touch, and its body is the prompt the agent follows.

There are two layers:

- **Ingest workflows** (`ingest-*.md`) turn source events into records, one file per event. They read a connection or `inbox/`, write only record folders and `log.md`, and commit to the branch that triggered them.
- **Refinement workflows** read across records and keep the concept pages current. They write only concept folders and `log.md`, watch `main`, and put every change on its own branch for review. Comment on that branch and the same workflow revises its work.

Every run appends one line to `log.md`.

| Workflow | Layer | Trigger | Writes |
| --- | --- | --- | --- |
| [Ingest meetings from Fireflies](ingest-meetings-fireflies.md) | Ingest | `fireflies`, polls `fireflies_get_transcripts` | `meetings/` |
| [Ingest meetings from Granola](ingest-meetings-granola.md) | Ingest | `granola`, polls `search_meetings` from a fixed date | `meetings/` |
| [Ingest support threads from Intercom](ingest-support-intercom.md) | Ingest | `intercom`, polls `search_conversations` for closed conversations | `support/` |
| [Ingest support threads from Pylon](ingest-support-pylon.md) | Ingest | `pylon`, polls `search_issues` for closed issues | `support/` |
| [Ingest accounts from HubSpot](ingest-accounts-hubspot.md) | Ingest | `hubspot`, polls `search_crm_objects` for companies by last change | `accounts/` |
| [Ingest deals from HubSpot](ingest-deals-hubspot.md) | Ingest | `hubspot`, polls `search_crm_objects` for deals by last change | `deals/` |
| [Ingest issues from Linear](ingest-issues-linear.md) | Ingest | `linear`, polls `list_issues` by last update | `issues/` |
| [Ingest discussions from Slack](ingest-discussions-slack.md) | Ingest | `slack`, polls `slack_read_channel` for one chosen channel | `discussions/` |
| [Ingest inbox](ingest-inbox.md) | Ingest | `inbox/**`, any branch | `meetings/` or `discussions/`, then moves the original to `archive/` |
| [Update customers](update-customers.md) | Refinement | `accounts/`, `deals/`, `meetings/`, `support/` or `issues/` change on `main` | `customers/`, with drafts for new customers |
| [Update projects](update-projects.md) | Refinement | `issues/` or `meetings/` change on `main` | `projects/`, with drafts for new projects |
| [Record decisions](record-decisions.md) | Refinement | `meetings/` or `discussions/` change on `main` | `decisions/`, each with its options, reasons and who decided |
| [Update teams](update-teams.md) | Refinement | `projects/` change on `main` | `teams/`, from the Project pages each team runs |
| [Staleness sweep](staleness-sweep.md) | Refinement | Mondays at 07:00 | The `## Needs review` section of each Team page |
| [Weekly digest](weekly-digest.md) | Refinement | Mondays at 08:00 | `digests/` |

A meeting runs in steps, each on its own branch for review. Merge the branch with the new Meeting record, and Update customers, Update projects and Record decisions each open a branch. Merge Update projects' branch, and Update teams follows. Staleness sweep writes only its own section of the Team pages, and Update teams keeps it as it is.
