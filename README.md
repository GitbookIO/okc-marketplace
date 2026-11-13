# OKC marketplace

Agent plugins, workflow recipes, and repository templates for GitBook Knowledge.

```text
.agents/plugins/marketplace.json
.gitbook/templates.json
.gitbook/recipes.json
plugins/
└── <name>/
    ├── assets/
    ├── plugin.json
    └── mcp.json
recipes/
└── <name>.md
templates/
├── base/
├── blank/
└── <name>/
```

- `.agents/plugins/marketplace.json` lists the plugins, their paths, and categories.
- `plugins/<name>/plugin.json` defines the plugin's identity, description, provider, and display metadata.
- `plugins/<name>/mcp.json` defines its hosted HTTPS MCP server connection.
- `plugins/<name>/assets/` contains the logo referenced by the plugin manifest.

Plugin paths in the catalog are relative to the repository root.

## Templates

- `.gitbook/templates.json` lists the templates people can create a repo from: name, local source path, title, description and icon.
- `templates/<name>/` is the template itself, copied as it is into a new repo. Its `template.yaml` holds the questions the app asks, and each answer can leave files out. The app never copies `template.yaml` itself.
- `templates/base/` is the skeleton new templates start from, with placeholders. `templates/blank/` is base filled in for a general-purpose repo. Neither is listed.

## Workflow recipes

- `.gitbook/recipes.json` lists recipes by stable `name` and Markdown `path`, relative to the repository root.
- `recipes/<name>.md` contains the workflow frontmatter and instructions. The frontmatter supplies its title, category, trigger, permissions, and optional description and icon.
- GitBook Knowledge imports metadata and source from the same commit. Updating a named recipe preserves its catalog identity; removing it from the manifest removes it from subscribers’ catalogs.
