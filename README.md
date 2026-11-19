# WhatsDownNow MCP server

Is it down, or is it just you? Live outage status for 210+ apps, AI APIs and cloud services, over MCP.

- Endpoint (Streamable HTTP, no auth): `https://whatsdownnow.com/mcp`
- Docs: https://whatsdownnow.com/developers · OpenAPI: https://whatsdownnow.com/openapi.json
- Registry name: `com.whatsdownnow/status`

## Tools
| Tool | What it does |
|---|---|
| `get_status(slug)` | One service's current verdict (up / degraded / down) with the official status text and our probe result |
| `list_services(query?, category?)` | Find a service by name, or discover slugs |
| `check_stack(slugs[])` | Check several dependencies at once; returns an overall verdict and `ready` true/false |
| `create_alert_stack(services, webhook_url?, email?, …)` | Get outage alerts by webhook, Slack, Discord or email. Returns a private manage_link once |
| `get_alert_stack(stack_id, token)` | Read a stack: services, live status, channels, recent deliveries |
| `update_alert_stack(stack_id, token, …)` | Add or remove services, or add an email or webhook |
| `send_test_alert(stack_id, token)` | Send a sample alert to every active channel |
| `rotate_alert_stack_key(stack_id, token)` | Issue a new manage link; the old token and link stop working immediately |
| `delete_alert_stack(stack_id, token)` | Delete a stack and stop its alerts |
| `list_incidents(slug)` | Recent incidents and verdict changes |

## Connect
```json
{ "mcpServers": { "whatsdownnow": { "url": "https://whatsdownnow.com/mcp" } } }
```
Claude Code: `claude mcp add --transport http whatsdownnow https://whatsdownnow.com/mcp`

Verdicts combine official status pages with our own HTTP checks about every 11 minutes. Service names belong to their owners; WhatsDownNow is not affiliated with them. The server code is closed source; this repo holds the public listing metadata.

## Status badges

`[![ChatGPT status](https://whatsdownnow.com/badge/chatgpt.svg)](https://whatsdownnow.com/status/chatgpt)`

Security issues: see [SECURITY.md](SECURITY.md).
