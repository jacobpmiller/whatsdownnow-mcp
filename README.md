# WhatsDownNow MCP server

Is it down, or is it just you? Live outage status for 110+ apps, AI APIs and cloud services, over MCP.

- Endpoint (Streamable HTTP, no auth): `https://whatsdownnow.com/mcp`
- Docs: https://whatsdownnow.com/developers · OpenAPI: https://whatsdownnow.com/openapi.json
- Registry name: `com.whatsdownnow/status`

## Tools
| Tool | What it does |
|---|---|
| `get_status(slug)` | One service's current verdict (up / degraded / down) with the official status text and our probe result |
| `list_services(category?)` | Discover service slugs |
| `check_stack(slugs[])` | Check several dependencies at once; returns an overall verdict and `ready` true/false |
| `create_alert_stack(services, webhook_url?, email?, …)` | Get outage alerts by webhook, Slack, Discord or email |
| `list_incidents(slug)` | Recent incidents and verdict changes |

## Connect
```json
{ "mcpServers": { "whatsdownnow": { "url": "https://whatsdownnow.com/mcp" } } }
```
Claude Code: `claude mcp add --transport http whatsdownnow https://whatsdownnow.com/mcp`

Verdicts combine official status pages with our own HTTP checks about every 10 minutes. Service names belong to their owners; WhatsDownNow is not affiliated with them. The server code is closed source; this repo holds the public listing metadata.

## Status badges

`[![ChatGPT status](https://whatsdownnow.com/badge/chatgpt.svg)](https://whatsdownnow.com/status/chatgpt)`

Security issues: see [SECURITY.md](SECURITY.md).
