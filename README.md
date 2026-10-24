# garments-mcp

MCP (Model Context Protocol) server for the Shimanto garments ERP on Odoo 20.
AI clients such as Claude Code, Claude Desktop and Cursor connect to Odoo through it.

## Modules

| Module | Name |
|---|---|
| `muk_mcp` | MuK MCP Server: `/api/mcp` endpoint, MCP keys, tools, prompts, audit log |
| `muk_web_utils` | MuK Web Utils (dependency of `muk_mcp`) |

Both are by [MuK IT](https://www.mukit.at), licensed LGPL-3 (see each module's `LICENSE`).
See [muk_mcp/README.md](muk_mcp/README.md) for configuration and client setup.

## Local changes

- Manifest versions changed from `20.0.x` to `20.1.x` so they install on the Odoo 20.1 server
  (Odoo refuses modules from another version series). Re-apply after updating from MuK.

## Setup

1. Add this folder to `addons_path` in `odoo.conf`, update the apps list and install **MuK MCP Server**.
2. Optional: `pip install pdfminer.six` in Odoo's environment so PDF attachments can be read as text.
3. In Odoo, **Settings → MCP → Connect → Generate Bearer Key**, then add the server to your client, e.g.:

   ```
   claude mcp add --transport http odoo http://localhost:8069/api/mcp --header "Authorization: Bearer YOUR_MCP_KEY"
   ```
