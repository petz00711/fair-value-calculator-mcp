# Fair Value Calculator for Cursor

Connects Cursor to the hosted MCP server of [Fair Value Calculator](https://www.fairvalue-calculator.com).
Nothing is installed locally: the plugin only registers the endpoint
`https://www.fairvalue-calculator.com/mcp`. On first use Cursor opens a sign-in page (OAuth);
a free account is enough.

Tools: `resolve_stock`, `get_stock_preview`, `get_stock_verdict`, `compare_stocks`, `screen_stocks`,
`get_watchlist`, `add_to_watchlist`, `remove_from_watchlist`, `set_watchlist_alerts`,
`suggest_watchlist_stocks`.
What each one does, limits of the free tier and example questions are in the
[main README](../../README.md).

The numbers are model estimates, not prices and not investment advice.
