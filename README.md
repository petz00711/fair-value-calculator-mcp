# Fair Value Calculator MCP server

Hosted [Model Context Protocol](https://modelcontextprotocol.io/) server of
[Fair Value Calculator](https://www.fairvalue-calculator.com). It lets an AI assistant look up
what a listed stock is worth according to our valuation models, instead of estimating a number
from memory.

This repository holds the documentation and the registry manifest (`server.json`). The server
itself is a hosted service; there is nothing to install or run locally, and its source code is
not part of this repository.

| | |
|---|---|
| Endpoint | `https://www.fairvalue-calculator.com/mcp` |
| Transport | Streamable HTTP |
| Authentication | OAuth 2.1 with dynamic client registration. A free account is enough. |
| Registry name | `com.fairvalue-calculator/fair-value` |
| Setup guides | <https://www.fairvalue-calculator.com/integrations> |
| Overview | <https://www.fairvalue-calculator.com/mcp> |

## What it covers

Fair value per share, valuation status and a quality score for 40,000+ listed stocks worldwide.
The fair value is blended from several valuation models on reported fundamentals and is
recalculated daily. Method and limits: <https://www.fairvalue-calculator.com/methodology>.

The numbers are model estimates, not prices and not investment advice. Where the data does not
support a figure, the server returns the verdict without a number instead of a weak estimate.

## Tools

| Tool | What it does |
|---|---|
| `resolve_stock` | Turns a name, ticker or ISIN into the matching listing, up to five matches. |
| `get_stock_preview` | Verdict, distance to fair value in bands and quality score for one stock, without the exact number. |
| `get_stock_verdict` | Fair value per share with currency, distance to the price, verdict, quality score and data level, with a link to the full analysis. |
| `compare_stocks` | Several stocks side by side with the same values. |
| `screen_stocks` | Stocks matching criteria: minimum distance to fair value, minimum quality, sector, region. |
| `get_watchlist` | Reads the watchlist of the signed-in account. |
| `add_to_watchlist` | Adds a stock to the watchlist. |
| `remove_from_watchlist` | Removes a stock from the watchlist. |
| `set_watchlist_alerts` | Switches the e-mail alerts of the account's watchlist on or off (Pro). |
| `suggest_watchlist_stocks` | Suggests up to eight stocks that fit the saved watchlist: priced below fair value, high quality score, not held yet, ranked with their correlation to the stocks already on it; can also suggest a replacement of similar size for one stock. Changes nothing (Pro, not offered in ChatGPT yet). |

The three tools that change the watchlist or alerts ask for separate consent during sign-in.

Free accounts get the verdict tools with monthly limits; exact fair values for all stocks,
comparisons of up to five stocks, alerts and watchlist suggestions are part of Pro. Current limits and prices:
<https://www.fairvalue-calculator.com/pro>.

## Connect

In any client that supports remote MCP servers, add the endpoint and sign in when prompted:

```
https://www.fairvalue-calculator.com/mcp
```

Claude Code:

```
claude mcp add --transport http fair-value-calculator https://www.fairvalue-calculator.com/mcp
```

Codex:

```
codex mcp add fair-value-calculator --url https://www.fairvalue-calculator.com/mcp
```

Cursor (`.cursor/mcp.json`):

```json
{"mcpServers":{"fair-value-calculator":{"url":"https://www.fairvalue-calculator.com/mcp"}}}
```

VS Code: run "MCP: Add Server", choose HTTP and paste the endpoint.

This repository is also a Cursor plugin (`plugins/fair-value-calculator`), which registers the same endpoint.

Gemini CLI (this repository is also a Gemini CLI extension, `gemini-extension.json`):

```
gemini extensions install https://github.com/petz00711/fair-value-calculator-mcp
```

Step-by-step guides for Claude, ChatGPT, Claude Code, Cursor, VS Code and Codex:
<https://www.fairvalue-calculator.com/integrations>.

## Example questions

- "What is Apple worth according to Fair Value Calculator?"
- "Which European technology stocks are undervalued right now?"
- "Compare Microsoft, Alphabet and Meta."
- "Add Nestlé to my watchlist."

## Open data

Monthly market valuation datasets (CC BY 4.0):
<https://github.com/petz00711/fvc-open-data>, DOI
[10.5281/zenodo.21639205](https://doi.org/10.5281/zenodo.21639205).

## Support

Questions and problem reports: office@fairvalue-calculator.com, or open an issue here.

## License

The documentation and manifest in this repository are licensed under
[CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). The hosted service is proprietary and
is used under the terms at <https://www.fairvalue-calculator.com/legal.php?doc=agb&lang=en>.
