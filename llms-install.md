# Installing the Shager MCP server (for AI agents)

Shager is a hosted MCP server. Do not clone, build or run anything.

1. Add a remote MCP server named `shager`:
   - Transport: Streamable HTTP
   - URL: `https://app.shager.ai/api/mcp`
   - No headers, no environment variables.

   For Cline, the entry in `cline_mcp_settings.json` is:

   ```json
   {
     "mcpServers": {
       "shager": {
         "type": "streamableHttp",
         "url": "https://app.shager.ai/api/mcp"
       }
     }
   }
   ```

2. Connect. The server answers `401` with a `WWW-Authenticate` header that points to its OAuth metadata. Your client registers itself (Dynamic Client Registration, PKCE S256) and opens a browser window.

3. Ask the user to sign in to Shager in that window and approve. If they have no Shager account yet, they can create one there.

4. Check it worked: call `whoami`, then `list_workspaces`.

If the client cannot do OAuth, ask the user for an API key from the Shager app (Account, then "Connect an agent") and send it as `Authorization: Bearer shgr_...`.

Some actions (many accounts at once, posting within minutes, removing an account, team changes) return `needs_confirmation` with a `confirm_url`. Show that link to the user and retry after they approve. Never try to approve it yourself.
