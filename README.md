# OKC marketplace

Agent plugins and repository templates for OKC.

```text
.agents/plugins/marketplace.json
plugins/
└── <name>/
    ├── assets/
    ├── plugin.json
    └── mcp.json
```

- `.agents/plugins/marketplace.json` lists the plugins, their paths, and categories.
- `plugins/<name>/plugin.json` defines the plugin's identity, description, provider, and display metadata.
- `plugins/<name>/mcp.json` defines its hosted HTTPS MCP server connection.
- `plugins/<name>/assets/` contains the logo referenced by the plugin manifest.

Plugin paths in the catalog are relative to the repository root.
