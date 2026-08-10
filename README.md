# BuzzRadr MCP Server

Remote [MCP](https://modelcontextprotocol.io) server for **BuzzRadr AI Pulse** — a live AI trend radar. Gives any MCP client real-time access to trending AI topics with "why trending" signals, daily digests, and source health.

- **Endpoint:** `https://buzzradr.com/api/mcp` (Streamable HTTP)
- **Auth:** none — public, read-only, no API key
- **Live site:** https://buzzradr.com/hot

## Tools

| Tool | What it does |
|---|---|
| `get_daily_digest` | Top ~12 trending topics for a vertical as a daily briefing — title, AI summary, why-it-matters reason, heat score, platforms, trusted-source count |
| `list_trends` | Search/list trending topics with filters: `keywords`, `platforms`, `sort=hot\|time`, `limit`, `locale=en\|zh` |
| `get_topic` | Full detail for one topic by `topicId` |
| `get_source_health` | Ingestion health of the radar's sources |

Verticals: `ai` (flagship), `jobs`, `finance`, `real-estate`, `world-cup-2026`.

## Connect

**Claude Code**

```bash
claude mcp add --transport http buzzradr https://buzzradr.com/api/mcp
```

**Any MCP client** (generic config)

```json
{
  "mcpServers": {
    "buzzradr": {
      "type": "streamable-http",
      "url": "https://buzzradr.com/api/mcp"
    }
  }
}
```

**claude.ai / Claude Desktop** — add a custom connector with URL `https://buzzradr.com/api/mcp`.

## Try it

Ask your agent:

- "What's trending in AI today?"
- "Anything hot about Claude or agents right now?"
- "Give me the daily AI digest in Chinese."

## Related

- **Agent skill** (REST-based, for agents without MCP): [buzzradr/ai-hot](https://github.com/buzzradr/ai-hot) — `npx skills add buzzradr/ai-hot`
- **RSS:** `https://buzzradr.com/api/public/hot/rss?vertical=ai`
- **OpenAPI:** `https://buzzradr.com/openapi.yaml`

## Registry manifest

[`server.json`](./server.json) is the manifest published to the [official MCP registry](https://registry.modelcontextprotocol.io) as `io.github.buzzradr/mcp`.
