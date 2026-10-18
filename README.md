# Altivo Jets MCP server

<!-- mcp-name: io.github.prateek7779-maker/altivo-mcp -->

Live private jet empty legs and charter estimates for any AI assistant. Free, public, no API key.

```text
https://altivojets.com/mcp/
```

Altivo Jets is a private jet and helicopter charter broker in India, the United States, the United Kingdom, France, Germany, Italy, the UAE, Brazil, Canada, Switzerland, Mexico and Saudi Arabia. Every flight is operated by a licensed operator. This server lets an assistant search live empty legs, estimate a full charter in the local currency of the departure market, browse routes, aircraft sizes and licensed operators, and send a quote request to the Altivo desk.

This repository holds the install manifests. Each one points at the hosted endpoint; nothing runs on your machine.

## Install

| Client | How |
| --- | --- |
| Claude (claude.ai, desktop) | Settings, Connectors, Add custom connector, paste the URL, leave authentication empty |
| VS Code (one click) | [Install in VS Code](https://vscode.dev/redirect/mcp/install?name=altivo&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Faltivojets.com%2Fmcp%2F%22%7D) |
| Claude Code | `claude mcp add --transport http altivo https://altivojets.com/mcp/` |
| Claude Code plugin (server plus a skill) | `claude plugin marketplace add prateek7779-maker/altivo-mcp` then `claude plugin install altivo@altivo` |
| ChatGPT | Developer mode, add connector, paste the URL |
| Cursor | `~/.cursor/mcp.json`: `{ "mcpServers": { "altivo": { "url": "https://altivojets.com/mcp/" } } }` |
| VS Code | `code --add-mcp '{"name":"altivo","type":"http","url":"https://altivojets.com/mcp/"}'` |
| Gemini CLI | `gemini extensions install https://github.com/prateek7779-maker/altivo-mcp` |

## Tools

| Tool | Type | What it does |
| --- | --- | --- |
| `search_empty_legs` | Read | Live empty legs by origin, destination, dates, passengers, market and price ceiling. Up to 20 results with whole-aircraft price, estimated taxes, all-in estimate and booking link |
| `get_empty_leg` | Read | One leg by reference |
| `booking_handoff` | Read | The altivojets.com page where the traveller sends the request; creates no booking |
| `get_charter_estimate` | Read | Indicative charter price by aircraft size, one way or return, in local currency, with flight time and the recommended size |
| `list_routes` | Read | Popular routes by market with from prices and live legs |
| `list_aircraft` | Read | Aircraft sizes with the market's hourly rates and the models flown there |
| `find_operators` | Read | Licensed operators from the regulators' published lists |
| `list_markets` | Read | Countries served, currencies and regulators |
| `request_quote` | Write | Sends the trip and the traveller's contact details to the Altivo desk. No payment, no booking |

Operators are not named on empty legs; the operator is named on the desk's quote. Prices are for the whole aircraft.

## Limits

30 tool calls a minute and 10 quote requests an hour per IP. Connecting and listing tools are free. At most 4 tool calls per batch. Over a limit the server answers HTTP 429 with JSON-RPC error `-32029` and `RateLimit-*` headers. Partners with a key get higher limits: hello@altivojets.com.

## More

- Developer guide: https://altivojets.com/developers/
- Feeds: https://altivojets.com/feeds/empty-legs.json and https://altivojets.com/feeds/empty-legs.xml
- Discovery: https://altivojets.com/.well-known/mcp.json and https://altivojets.com/llms.txt

MIT licence for the manifests in this repository.
