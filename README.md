# Liqwall MCP server — live crypto liquidations, funding and Hyperliquid data

[Liqwall](https://liqwall.com/?src=github) is a trading terminal that shows what stands behind the price: liquidations, stop orders and whale positions on Hyperliquid, walls in the order books of all large exchanges, funding and open interest.

This is its remote MCP server. Add one URL and your assistant answers questions about the crypto market with live data:

```
https://liqwall.com/mcp
```

Streamable HTTP. Four tools work without an account and without a key. Read-only: no trading, no wallets, no transfers.

## Tools without a key

| Tool | What it returns |
|---|---|
| `liquidation_map` | Where forced liquidations stand around the current price of one market: long liquidations below the price, short liquidations above it, and the largest levels with their distance from the price. Two views: Hyperliquid (more than 60 markets, among them BTC, ETH, SOL, HYPE, gold, oil and stocks) and large exchanges together (Binance, OKX, Bybit, Hyperliquid, Gate). |
| `liquidations` | How much was liquidated over the last hour and the last 24 hours, longs against shorts, for the whole market or one coin, by coin and by exchange, and the largest liquidations of the hour. |
| `derivatives` | Funding rate (Binance and the average across exchanges), open interest in dollars with its 24-hour change, the share of long accounts and the positioning of top traders, for one coin or the ten largest. |
| `fear_greed` | The crypto Fear and Greed Index from 0 to 100 for the whole market or for BTC, ETH, SOL, with the values a day, a week and a month ago. |

Every answer is a snapshot with the time of the data and a link to the Liqwall page that shows the same data as a live chart.

Six more tools work with a Liqwall API key: market overview, coin summary, indicator series, price levels, Hyperliquid whales and candles — order books of 14 exchanges, walls, options, the positions and orders of large Hyperliquid accounts, indicator history. Details: [liqwall.com/docs/mcp](https://liqwall.com/docs/mcp?src=github).

## Connect

**Claude** (claude.ai, Claude Desktop): Settings → Connectors → Add custom connector → paste `https://liqwall.com/mcp`.

**ChatGPT** (developer mode): add a custom connector with the URL `https://liqwall.com/mcp`, authentication: none.

**Cursor, VS Code, Windsurf and other MCP clients**:

```json
{
  "mcpServers": {
    "liqwall": {
      "url": "https://liqwall.com/mcp"
    }
  }
}
```

**With an API key** (more tools): send the key in the `Authorization: Bearer <key>` header or in `X-API-Key`. The key is in your Liqwall account → API.

## Questions to try

- Where are the nearest liquidation levels for BTC above and below the price?
- How much was liquidated in crypto over the last 24 hours, longs or shorts?
- Show the liquidation map of ETH on the large exchanges.
- What is the funding rate and open interest of SOL right now?
- Is the crypto market fearful or greedy today?

## Live pages

The same data as live charts, free and without sign-up:

- [Hyperliquid liquidation map](https://liqwall.com/liquidation-map?src=github) — BTC, ETH, SOL, HYPE and 57 more markets
- [Liquidation heatmap by exchange](https://liqwall.com/liquidation-heatmap?src=github) — Binance, OKX, Bybit together
- [Exchange liquidation map](https://liqwall.com/exchange-liquidation-map/btc?src=github)
- [Crypto liquidations today](https://liqwall.com/liquidations?src=github)
- [Order book heatmap](https://liqwall.com/liquidity-heatmap?src=github) and [the order books of all exchanges in one ladder](https://liqwall.com/orderbook?src=github)
- [Hyperliquid whales](https://liqwall.com/whales?src=github)
- [Funding rates](https://liqwall.com/funding-rates?src=github), [open interest](https://liqwall.com/open-interest?src=github), [long/short ratio](https://liqwall.com/long-short-ratio?src=github)
- [Crypto Fear and Greed Index](https://liqwall.com/fear-greed-index?src=github)
- [Market map](https://liqwall.com/market-map?src=github) and [screener](https://liqwall.com/screener?src=github)
- [All free Liqwall data](https://liqwall.com/crypto-data?src=github)

The full terminal with 80+ Liqwall indicators: [liqwall.com/chart](https://liqwall.com/chart?src=github).

## Listings

- Official MCP Registry: `com.liqwall/market-data`
- [Glama](https://glama.ai/mcp/connectors/com.liqwall/market-data)

## About

The server is a hosted service operated by Liqwall; this repository holds its documentation. Questions and support: [@Liqwallsupportbot](https://t.me/Liqwallsupportbot) on Telegram, hello@liqwall.com.
