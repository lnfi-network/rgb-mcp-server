# RGB API MCP Server

A Model Context Protocol (MCP) server that provides integration with RGB Lightning Node APIs. This server enables AI assistants to interact with RGB assets, Lightning Network operations, and Bitcoin on-chain transactions.

<a href="https://glama.ai/mcp/servers/@lnfi-network/rgb-mcp-server">
  <img width="380" height="200" src="https://glama.ai/mcp/servers/@lnfi-network/rgb-mcp-server/badge" alt="RGB Lightning Network Server MCP server" />
</a>

## Features

- **Node Operations**: Check node status, get network information
- **RGB Asset Management**: List assets, check balances, send RGB assets
- **Lightning Network**: Create/pay invoices, manage channels
- **On-chain Transactions**: Generate addresses, send Bitcoin, list transactions
- **Swap Operations**: List and manage asset swaps
# Quick Start

## npx
You can use this server directly with MCP clients like Cursor, Claude Desktop, Trae, or Cherry Studio by running

**Note:** Please replace with your RGB api key:
xxxxxxxxxxxxxxxxxxxx  Or /path/rgbapi.key

## MCP Client Configuration
Add this configuration to your MCP client (e.g., Claude Desktop config):

```bash
{
    "mcpServers": {
        "rgb-mcp-server": {
            "command": "npx",
            "args": [
                "-y",
                "rgb-mcp-server"
            ],
            "env": {
                "RGB_API_BASE_URL": "http://localhost:3000",
                "RGB_API_KEY": "xxxxxxxxxxxxxxxxxxxx" //Optional: RGB api key Or /path/rgbapi.key
            }
        }
    }
}
```

# Development

For developers who want to contribute or use this project:

## Installation

1. Make sure you have Node.js installed (version 16 or higher recommended)
2. Install dependencies:

```bash
npm install rgb-mcp-server
```

## Programmatic Usage

After installing the package, you can use it programmatically in your Node.js application:

```javascript
import { getRGBMcpServer } from "rgb-mcp-server";

// Initialize the RGB MCP server
const rgbMcpServer = await getRGBMcpServer({
    baseUrl: process.env.RGB_API_BASE_URL || 'http://localhost:3000',  // RGB API server URL
    apiKey: process.env.RGB_API_KEY,                                   // Optional: API key for authentication
    timeout: 30000                                                     // Optional: request timeout in ms
});

// Access available tools
const rgbTools = rgbMcpServer._registeredTools;
console.log('Available RGB tools:', Object.keys(rgbTools));
```



### Available Tools

The server provides the following MCP tools:

1. `rgb_get_node_info` - Get RGB node information
2. `rgb_get_node_status` - Get node status and uptime
3. `rgb_list_assets` - List all RGB assets
4. `rgb_get_asset_balance` - Get balance for a specific asset
5. `rgb_send_asset` - Send RGB assets
6. `rgb_generate_address` - Generate new on-chain address
7. `rgb_list_transactions` - List on-chain transactions
8. `rgb_send_bitcoin` - Send Bitcoin to an address
9. `rgb_create_lightning_invoice` - Create Lightning invoice
10. `rgb_pay_lightning_invoice` - Pay Lightning invoice
11. `rgb_list_lightning_channels` - List Lightning channels
12. `rgb_list_swaps` - List available swaps
13. `rgb_create_swap` - Create a new asset swap



## License

MIT