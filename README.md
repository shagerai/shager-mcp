# Shager MCP server

<img src="assets/logo.png" width="96" alt="Shager logo" align="right">

[Shager](https://shager.ai) runs your social media for you: write one post, send it to all your accounts, each network at its own hour, then answer comments and see what worked. This repo connects it to your AI agent.

There is nothing to install or run. Shager is a hosted MCP server:

```
https://app.shager.ai/api/mcp
```

The first time your agent connects, a Shager window opens in your browser. Sign in, choose what the agent may do, and you're done. No API key to copy, no password goes to the agent.

## What your agent can do

- **Publish:** drafts, scheduled posts and threads to Facebook, Instagram, TikTok, YouTube, X, LinkedIn, Pinterest, Threads, Bluesky, Mastodon, Telegram, Tumblr and Google Business Profile. Different text per network, a first comment, photos and videos. Facebook, Instagram, Threads and Google Business Profile open to everyone as each network finishes its review of Shager.
- **Check before it posts:** each network's limits (length, video size, aspect ratio) are checked before anything goes out.
- **Comments:** read, reply, hide or delete comments on your posts.
- **Auto-replies:** reply to a keyword in a comment with a private message, a link or a file, the way lead magnets work.
- **Results:** views, likes, comments, shares, saves, link clicks and follower growth, per post, account and network.
- **Clients and teams:** separate workspaces per client, approval links for clients, team roles.

Anything big waits for you: posting to many accounts at once, posting in the next few minutes, removing an account or changing your team sends you a link to approve first.

## Connect

### Claude Code

```bash
claude mcp add --transport http shager https://app.shager.ai/api/mcp
```

Or as a plugin:

```
/plugin marketplace add shagerai/shager-mcp
/plugin install shager@shager
```

### Cursor

Install Shager from the Cursor Marketplace, or add `mcp.json` from this repo to `~/.cursor/mcp.json`.

### VS Code (GitHub Copilot)

```bash
code --add-mcp '{"name":"shager","type":"http","url":"https://app.shager.ai/api/mcp"}'
```

### Gemini CLI

```bash
gemini extensions install https://github.com/shagerai/shager-mcp
```

### Cline, Windsurf, Goose, Zed and any other MCP client

Add a remote (Streamable HTTP) server with the URL `https://app.shager.ai/api/mcp`. The client signs in with OAuth on its own. The exact steps for agents are in [llms-install.md](llms-install.md).

### ChatGPT and Claude

Shager is in the ChatGPT app directory and in Claude's connector directory. Search for "Shager".

### Agents without OAuth

Make an API key in the Shager app (Account, then "Connect an agent") and send it as `Authorization: Bearer shgr_...`. The REST API covers the same actions: [OpenAPI](https://app.shager.ai/api/v1/openapi.json).

## Links

- Guide for agents: https://shager.ai/agents
- For developers (REST, webhooks, OpenAPI): https://shager.ai/agents#developers
- Help: https://shager.ai/help
- Privacy: https://shager.ai/privacy
- Contact: hello@shager.ai

This repo holds only the connection files. The server itself is run by Shager.

MIT license.
