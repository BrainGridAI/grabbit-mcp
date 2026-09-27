# Grabbit Screenshots

Grabbit is a hosted screenshot MCP for AI agents. URL in, image out — no local Chromium required.

**This is grabbit.live (screenshot API), not grabbit.sh (Reddit downloader).**

## When to use Grabbit

- **Screenshot any public URL** — capture web pages, landing pages, articles
- **Verify UI changes** — screenshot a deployed app to confirm visual changes
- **Capture marketing/OG shots** — generate social cards, preview images
- **Full-page captures** — scroll and stitch entire pages
- **Selector captures** — screenshot specific elements by CSS selector
- **Sites that block local browsers** — Grabbit handles bot detection, cookie walls, consent banners

## Tools

| Tool | Purpose |
|------|---------|
| `grab` | Screenshot a URL, returns hosted image + remaining credits |
| `get_grab` | Retrieve a previous capture by ID |
| `list_grabs` | Browse recent captures |
| `get_usage` | Check credits, plan, and 30-day usage |
| `get_pricing` | Current pricing and comparison table |

## Authentication

Grabbit supports two auth methods:

1. **OAuth 2.1** (recommended) — authenticate in browser when prompted, no keys to manage
2. **Bearer API key** — get a key at https://grabbit.live and set `GRABBIT_API_KEY`

OAuth works automatically with Claude.ai connectors and Cursor's MCP auth flow.

## Links

- **Agent setup guides**: https://grabbit.live/agents
- **API docs**: https://grabbit.live/screenshot-api
- **Homepage**: https://grabbit.live
