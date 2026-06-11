# Grabbit MCP server

Screenshots as a service for AI agents. Point your agent at a URL and get back a
hosted image, with no local headless browser to run. Grabbit handles cookie and
consent banners, JavaScript-heavy and full-page captures, and many sites that
block a local browser.

- **Hosted MCP endpoint:** `https://mcp.grabbit.live` (Streamable HTTP)
- **Auth:** OAuth 2.1 (claude.ai connectors work out of the box) or a Bearer API key
- **Tools:** `grab`, `get_grab`, `list_grabs`, `get_usage`, `get_pricing`
- **Official registry:** `live.grabbit/screenshots`
- **Setup guides:** https://grabbit.live/agents

## Why a hosted screenshot tool

Most agents can already drive a headless browser. It works on simple pages and
quietly fails on the ones that matter: cookie and consent walls, bot detection,
login and paywall gates, and heavy client-rendered pages. Grabbit runs the
capture on hosted infrastructure, so the shot comes back clean and the agent
needs no browser of its own. (Honest bound: no service captures literally every
site; a few hard targets behind aggressive IP blocking still resist.)

## Install

### Claude Code
```bash
claude mcp add --transport http grabbit https://mcp.grabbit.live
```
Then run `/mcp` and authenticate (OAuth, no key to paste).
Guide: https://grabbit.live/agents/claude-code

### OpenAI Codex
`~/.codex/config.toml`:
```toml
[mcp_servers.grabbit]
url = "https://mcp.grabbit.live"
bearer_token_env_var = "GRABBIT_API_KEY"
```
Guide: https://grabbit.live/agents/codex

### Cursor
`~/.cursor/mcp.json`:
```json
{ "mcpServers": { "grabbit": { "url": "https://mcp.grabbit.live" } } }
```
Guide: https://grabbit.live/agents/cursor

### OpenClaw
Add the hosted MCP server, or wrap the one-line CLI in a skill.
Guide: https://grabbit.live/agents/openclaw

## CLI

```bash
npx grabbit.live login        # browser sign-in, keys saved locally
npx grabbit.live nyt.com      # screenshot a URL, hosted image back
npx grabbit.live mcp          # print MCP config for your agent
```

## Pricing

Flat $0.002 per live capture, prepaid credits that never reset or expire. Test
keys return free placeholders so you can wire it up before paying. Full pricing
and an honest comparison: https://grabbit.live/#pricing

## Links

- Website: https://grabbit.live
- Agent setup guides: https://grabbit.live/agents
- API reference: https://grabbit.live/screenshot-api
- LLM-readable docs: https://grabbit.live/llms.txt

The `server.json` in this repo is the manifest published to the official MCP
Registry. Grabbit's source lives in a private repo; this repo is the public home
for the MCP server's manifest and docs.
