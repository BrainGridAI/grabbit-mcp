<div align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="assets/grabbit-wordmark-dark.png">
    <img alt="Grabbit" src="assets/grabbit-wordmark.png" width="240">
  </picture>

  <h3>Screenshots as a service, built for AI agents</h3>

  <p>
    <a href="https://registry.modelcontextprotocol.io/v0.1/servers?search=live.grabbit"><img src="https://img.shields.io/badge/MCP%20Registry-live.grabbit%2Fscreenshots-7c3aed" alt="In the official MCP Registry"></a>
    <a href="https://www.npmjs.com/package/grabbit.live"><img src="https://img.shields.io/npm/v/grabbit.live?label=CLI&color=7c3aed" alt="npm CLI version"></a>
    <img src="https://img.shields.io/badge/transport-Streamable%20HTTP-7c3aed" alt="Streamable HTTP transport">
    <a href="LICENSE"><img src="https://img.shields.io/badge/license-MIT-blue" alt="MIT license"></a>
  </p>
</div>

Point your agent at a URL and get back a hosted image, with no local headless
browser to run. Grabbit handles cookie and consent banners, JavaScript-heavy and
full-page captures, and many sites that block a local browser.

| | |
| --- | --- |
| **Endpoint** | `https://mcp.grabbit.live` (Streamable HTTP) |
| **Auth** | OAuth 2.1 (claude.ai connectors work out of the box) or a Bearer API key |
| **Registry name** | `live.grabbit/screenshots` |
| **Setup guides** | https://grabbit.live/agents |

## Tools

| Tool | What it does |
| --- | --- |
| `grab` | Screenshot any public URL and get a hosted image back (inline image + remaining credits) |
| `get_grab` | Fetch a previous capture by id |
| `list_grabs` | Browse your recent captures |
| `get_usage` | Credits, plan, and 30-day usage |
| `get_pricing` | Pricing plus an honest, dated comparison against ScreenshotOne, Urlbox, Browserless, and others |

## Why a hosted screenshot tool

Most agents can already drive a headless browser. It works on simple pages and
quietly fails on the ones that matter: cookie and consent walls, bot detection,
login and paywall gates, and heavy client-rendered pages. Grabbit runs the
capture on hosted infrastructure, so the shot comes back clean and the agent
needs no browser of its own.

> Honest bound: no service captures literally every site. A few hard targets
> behind aggressive IP blocking still resist. Private and internal addresses
> (including localhost) are blocked by SSRF protection.

## Quick start

### Claude Code

```bash
claude mcp add --transport http grabbit https://mcp.grabbit.live
```

Then run `/mcp` and authenticate in the browser (OAuth, no key to paste).
Guide: https://grabbit.live/agents/claude-code

### Cursor

`~/.cursor/mcp.json` (commit a project-scoped `.cursor/mcp.json` to share with your team):

```json
{ "mcpServers": { "grabbit": { "url": "https://mcp.grabbit.live" } } }
```

Guide: https://grabbit.live/agents/cursor

### OpenAI Codex

`~/.codex/config.toml`:

```toml
[mcp_servers.grabbit]
url = "https://mcp.grabbit.live"
bearer_token_env_var = "GRABBIT_API_KEY"
```

Guide: https://grabbit.live/agents/codex

### OpenClaw

Add the hosted MCP server, or wrap the one-line CLI in a skill.
Guide: https://grabbit.live/agents/openclaw

## Cursor Marketplace

Install Grabbit directly from the [Cursor Marketplace](https://cursor.com/marketplace) (when listed), or add manually:

`~/.cursor/mcp.json` (or project-scoped `.cursor/mcp.json`):

```json
{ "mcpServers": { "grabbit": { "url": "https://mcp.grabbit.live" } } }
```

This repo includes Cursor plugin packaging (`.cursor-plugin/plugin.json`, `mcp.json`, skill) for marketplace submission.

## Agent Skills

This repo ships a portable skill folder (`skills/grabbit-screenshots/`) that teaches agents when and how to use the Grabbit hosted screenshot MCP.

### Install via skills.sh

```bash
npx skills add BrainGridAI/grabbit-mcp --skill grabbit-screenshots
```

After public installs, the skill can appear on [skills.sh](https://skills.sh) via install telemetry (no separate submit form).

### Publish to ClawHub

From the repo root:

```bash
clawhub skill publish ./skills/grabbit-screenshots --slug grabbit-screenshots --name "Grabbit Screenshots" --version 1.0.0
```

### Install via OpenClaw / Hermes

The skill is published on ClawHub at https://clawhub.ai/braingrid/skills/grabbit-screenshots

```bash
openclaw skills install @braingrid/grabbit-screenshots
# or
clawhub install grabbit-screenshots
```

Hermes can install the same ClawHub skill (ClawHub is a Hermes skill source) and connect MCP at `https://mcp.grabbit.live`.

## CLI

```bash
npx grabbit.live login        # browser sign-in, keys saved locally
npx grabbit.live nyt.com      # screenshot a URL, hosted image back
npx grabbit.live mcp          # print MCP config for your agent
```

## Pricing

Flat **$0.002** per live capture. Prepaid credits that never reset or expire.
Test keys return free placeholders so you can wire it up before paying. Full
pricing and the comparison table: https://grabbit.live/#pricing

## Links

- **Website**: https://grabbit.live
- **Agent setup guides**: https://grabbit.live/agents
- **API reference**: https://grabbit.live/screenshot-api
- **LLM-readable docs**: https://grabbit.live/llms.txt

---

<sub>The `server.json` in this repo is the manifest published to the official MCP
Registry. Grabbit's source lives in a private repo; this is the public home for
the MCP server's manifest and docs.</sub>
