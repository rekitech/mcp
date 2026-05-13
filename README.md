# Reki MCP

Connect Claude to **Reki**, a funding copilot for French startups (CIR, JEI, PI R&D, BPI, France 2030, Eurostars).

This repo is a Claude plugin marketplace that ships one plugin: `reki-mcp`. It packages the Reki MCP server configuration plus a skill that tells Claude when to call it.

> You need a Reki account and an API key to use this plugin. Sign up and create a key at <https://mcp.reki.eu/settings/api-keys>.

## Install

### Claude Code

```bash
/plugin marketplace add rekitech/mcp
/plugin install reki-mcp@reki
```

Claude Code will prompt for your `rk_live_…` API key during install and store it in the OS keychain.

### Claude Desktop / Cowork

Open the sidebar → **Customize → Plugins → Add plugin**, then paste:

```
rekitech/mcp
```

Same prompt for your API key, same keychain storage.

### Codex / Cursor / other MCP clients (manual setup)

The plugin format is Claude-specific, but the underlying MCP server is the same. Copy this snippet into your client's MCP config, replacing `<YOUR_KEY>` with your `rk_live_…` token:

```json
{
  "mcpServers": {
    "reki": {
      "type": "http",
      "url": "https://api.reki.eu/api/mcp/v1/mcp",
      "headers": {
        "Authorization": "Bearer <YOUR_KEY>"
      }
    }
  }
}
```

## How to use

Once installed, just ask Claude in natural language. Examples:

- "Je suis dirigeant d'une startup française, SIREN 552081317. À quoi suis-je éligible côté financements publics ?"
- "Rédige-moi un dossier pour le PI R&D."
- "Audite mon dossier avant que je dépose."
- "Prépare-moi un brief pour mon RDV avec un chargé d'affaires BPI."

The `using-reki` skill bundled with the plugin tells Claude when to route a question through Reki. Multi-turn conversations stay coherent for ~30 minutes of inactivity — no need to repeat context.

## What's inside

```
.
├── .claude-plugin/
│   └── marketplace.json          ← this repo as a Claude marketplace
└── plugins/
    └── reki-mcp/
        ├── .claude-plugin/
        │   └── plugin.json       ← plugin manifest + userConfig prompt
        ├── .mcp.json             ← MCP server config (HTTP transport)
        └── skills/
            └── using-reki/
                └── SKILL.md      ← when/how Claude should call ask_reki
```

## License

MIT — see [LICENSE](./LICENSE).
