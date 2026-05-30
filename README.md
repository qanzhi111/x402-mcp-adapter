# x402 MCP Adapter

![x402 Protocol](https://img.shields.io/badge/x402-Protocol-7C3AED?style=flat-square)
![MCP Compatible](https://img.shields.io/badge/MCP-Compatible-10B981?style=flat-square)
![Base Chain](https://img.shields.io/badge/Base-Chain-0052FF?style=flat-square)
![License](https://img.shields.io/badge/License-MIT-green?style=flat-square)
![Node.js](https://img.shields.io/badge/Node.js-18+-black?style=flat-square)

A Model Context Protocol (MCP) adapter that enables AI agents to discover and consume the x402 Crypto API. Pay-per-request crypto data powered by USDC on Base chain.

## Features

- 🔌 **MCP Native** - Standard MCP protocol implementation for seamless AI agent integration
- 💰 **x402 Payments** - Automatic micropayments via USDC on Base
- 📊 **Real-time Data** - Live crypto prices, market data, and trending coins
- 🤖 **AI Agent Ready** - Designed for autonomous agent workflows
- 🚀 **Easy Setup** - One-command deployment to Railway, Vercel, or Docker

## Available MCP Tools

| Tool | Description | Parameters |
|------|-------------|------------|
| `btc_price` | Get current Bitcoin (BTC) price | `currency` (optional, default: USD) |
| `eth_price` | Get current Ethereum (ETH) price | `currency` (optional, default: USD) |
| `coin_price` | Get price for any cryptocurrency | `symbol` (required), `currency` (optional) |
| `market_data` | Top coins by market cap | `limit` (optional, default: 10) |
| `trending_coins` | Trending coins by social activity | `limit` (optional, default: 10) |
| `api_status` | Check API health and payment status | none |

## Quick Start

### Prerequisites

- Node.js 18+
- npm or yarn
- A wallet with USDC on Base (for paid endpoints)

### Installation

```bash
# Clone the repository
git clone https://github.com/qanzhi111/x402-mcp-adapter.git
cd x402-mcp-adapter

# Install dependencies
npm install

# Start the MCP server
node mcp-adapter.js
```

The MCP server runs on port 3001 by default. Configure via `PORT` environment variable.

### Environment Variables

| Variable | Default | Description |
|----------|---------|-------------|
| `PORT` | `3001` | Server port |
| `X402_API_BASE` | Railway URL | Backend x402 API endpoint |

## Usage Examples

### With Claude Desktop

Add to your MCP settings (`claude_desktop_config.json`):

```json
{
  "mcpServers": {
    "x402-crypto": {
      "command": "node",
      "args": ["/path/to/x402-mcp-adapter/mcp-adapter.js"],
      "env": {
        "X402_API_BASE": "https://your-api.railway.app"
      }
    }
  }
}
```

### Programmatic Usage

```javascript
// Direct MCP tool calls
const { execSync } = require('child_process');

// The adapter exposes standard MCP endpoints
// POST / - MCP protocol handler
// GET /health - Health check
```

## Deployment

### Railway (Recommended)

[![Deploy on Railway](https://railway.app/button.svg)](https://railway.app/new)

1. Fork this repository
2. Create a new Railway project
3. Connect your GitHub repo
4. Deploy - zero config needed!

### Vercel

```bash
# Install Vercel adapter
npm i -g vercel

# Deploy
vercel
```

### Docker

```bash
# Build image
docker build -t x402-mcp-adapter .

# Run container
docker run -p 3001:3001 x402-mcp-adapter
```

## Pricing

All tool calls are paid via x402 protocol:

| Endpoint | Price | Description |
|----------|-------|-------------|
| `btc_price` | $0.01 | Bitcoin price |
| `eth_price` | $0.01 | Ethereum price |
| `coin_price` | $0.01 | Any coin price |
| `market_data` | $0.02 | Market overview |
| `trending_coins` | $0.02 | Social trending |

Payment is automatic - just hold USDC on Base and you're ready to go.

## Architecture

```
┌─────────────────┐     MCP Protocol      ┌──────────────────────┐
│   AI Agent      │◄────────────────────►│  x402 MCP Adapter    │
│  (Claude, etc)  │                      │  (Port 3001)         │
└─────────────────┘                      └──────────┬───────────┘
                                                    │
                                          HTTP/x402 │
                                                    ▼
                                        ┌──────────────────────┐
                                        │  x402 Crypto API     │
                                        │  (Railway)           │
                                        │  spectacula...       │
                                        └──────────────────────┘
```

## Backend API

The MCP adapter connects to the x402 Crypto API:

- **Base URL**: `https://spectacular-strength-production-0494.up.railway.app`
- **Protocol**: x402 (HTTP 402 + payment headers)
- **Payment**: USDC on Base (Chain ID: 8453)

## Contributing

Contributions welcome! Please open an issue or PR.

## License

MIT

---

<p align="center">
  <strong>Powered by x402</strong><br>
  <a href="https://x402.org">x402 Protocol</a> · <a href="https://github.com/qanzhi111/x402-crypto-api">x402 Crypto API</a>
</p>
