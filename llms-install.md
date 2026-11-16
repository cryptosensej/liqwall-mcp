# Installing the Liqwall MCP server (for AI agents such as Cline)

Liqwall is a **remote** MCP server. There is nothing to clone, build or run locally: add the URL to the MCP client settings.

- URL: `https://liqwall.com/mcp`
- Transport: Streamable HTTP
- Four tools work without an account and without a key: `liquidation_map`, `liquidations`, `derivatives`, `fear_greed`.
- Four more tools (`market`, `coin`, `series`, `candles`) need a Liqwall API key, sent as a header. Keys are created in the Liqwall
  terminal (Account → API). Never put the key in the URL.

## Cline

Open Cline → MCP Servers → Remote Servers (or edit `cline_mcp_settings.json`) and add:

```json
{
  "mcpServers": {
    "liqwall": {
      "type": "streamableHttp",
      "url": "https://liqwall.com/mcp"
    }
  }
}
```

With an API key (optional, for the keyed tools):

```json
{
  "mcpServers": {
    "liqwall": {
      "type": "streamableHttp",
      "url": "https://liqwall.com/mcp",
      "headers": {
        "Authorization": "Bearer YOUR_LIQWALL_API_KEY"
      }
    }
  }
}
```

## Check that it works

Ask: "Where are the largest BTC liquidation clusters right now?" — the agent should call `liquidation_map` and answer with price levels.

Full documentation: https://liqwall.com/docs/mcp
