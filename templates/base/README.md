# {{TEMPLATE_TITLE}}

{{ONE_PARAGRAPH: what this repo does, who it's for, and what keeps it current.}}

## How it works

Workflows turn source events into records, one file per event. Refinement workflows read across records and keep the concept pages current. Every change a refinement makes lands on its own branch for review.

{{WORKFLOW_MAP: a fenced mermaid block with `flowchart LR`: sources on the left, then record folders, then concept folders, with each workflow as an edge label.}}

## Try it

{{TWO_MINUTE_DEMO: numbered steps, starting from a fresh repo with example data.}}

## Connections

Each ingest workflow reads one tool through the connection named in its `on.connector`. A connection made from a plugin in the marketplace takes the plugin's name, so adding the plugin is enough. Every ingest workflow ships, and one whose connection doesn't exist never runs, so connect only the tools you use. Connect two tools for the same records, like two issue trackers, and both run side by side. You can always drop material into `inbox/`.

{{CONNECTIONS: one line per connection name and the workflows that use it, then a line naming the connections that aren't marketplace plugins yet.}}

## Removing the example data

{{EXAMPLE_REMOVAL: what to delete on a branch: every mock-* record by folder, other example records by path, and everything in each concept folder. Then how to remove one kind only, and what to keep.}}

## Folders

{{FOLDERS: every concept folder with one line each, then the record folders.}}

- `inbox/`: drop pasted text or files here. Ingest inbox sorts them into records and moves the originals to `archive/`.
- `archive/`: inbox items that have been processed.
- `types/`: one definition per type, with the fields it uses.
- `workflows/`: the workflows that keep this repo current.
- `index.md`: a map of every folder, with what each holds.
- `log.md`: one line per workflow run, newest first.
