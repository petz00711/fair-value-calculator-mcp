# Security policy

## Reporting a vulnerability

Send the details and steps to reproduce to office@fairvalue-calculator.com. Please do not open a public issue for a security problem.

## Scope

This repository holds manifests, documentation and one skill. It runs no local code: the MCP server is the hosted endpoint `https://www.fairvalue-calculator.com/mcp`, and the plugins and the Gemini CLI extension only point your client at it.

## Credentials

Nothing here contains credentials. Clients sign in over OAuth with a Fair Value Calculator account; the token stays in your client.

## Tools that write

Most tools only read stock data. The watchlist and alert tools write to the signed-in user's own watchlist. No tool places trades or moves money.
