# Workflows

Each Markdown file in this folder is a workflow, except this README. Its frontmatter says when it runs and what it may touch, and its body is the prompt the agent follows.

There are two layers:

- **Ingest workflows** (`ingest-*.md`) turn source events into records, one file per event. They read a connection or `inbox/`, write only record folders and `log.md`, and commit to the branch that triggered them.
- **Refinement workflows** read across records and keep the concept pages current. They write only concept folders and `log.md`, watch `main`, and put every change on its own branch for review. Comment on that branch and the same workflow revises its work.

Every run appends one line to `log.md`.

{{WORKFLOW_TABLE: one row per workflow with its layer, trigger and what it writes.}}
