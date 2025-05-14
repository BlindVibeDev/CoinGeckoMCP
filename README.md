[![MseeP.ai Security Assessment Badge](https://mseep.net/pr/blindvibedev-coingeckomcp-badge.png)](https://mseep.ai/app/blindvibedev-coingeckomcp)

# 🚀 CoinGecko API Server MCP

<div align="center">

![Version](https://img.shields.io/badge/version-1.0.0-blue)
![License](https://img.shields.io/badge/license-MIT-green)
![Node](https://img.shields.io/badge/node-%3E%3D%2014.0.0-brightgreen)
![Express](https://img.shields.io/badge/express-4.x-lightgrey)

**Seamless cryptocurrency data access for AI systems and applications**

[Features](#✨-key-features) • [Quick Start](#🚀-quick-start) • [Installation](#📦-installation) • [Configuration](#⚙️-configuration) • [API Reference](#📚-api-reference) • [MCP Integration](#🤖-ai-integration-mcp) • [Pro API](#💎-pro-api-benefits) • [Troubleshooting](#🔧-troubleshooting) • [License](#📄-license)

</div>

## 🌟 Overview

The CoinGecko API Server MCP is a powerful, production-ready Node.js solution that provides seamless access to cryptocurrency market data through an elegant RESTful API and MCP (Marketplace Component Program) interface. It bridges AI systems like Claude with real-time crypto data while handling all the complexities of API rate limits, fallbacks, and error handling.

<div align="center">
  <img src="https://www.coingecko.com/assets/coingecko-logo-white-ea42ded10e4d604886deac6b8449b2b2230a0df0d0c6edd2c3b4587da9038cff.png" alt="CoinGecko Logo" width="300"/>
</div>

## ✨ Key Features

- **🔄 Dual API Support**: Seamlessly integrates with both CoinGecko Free and Pro APIs
- **🧠 AI Integration**: Full implementation of the MCP protocol for AI assistants
- **🛡️ Intelligent Fallback**: Automatically switches between APIs to prevent rate limiting
- **⚡ Optimized Performance**: Efficient request handling and response caching
- **📊 Comprehensive Data**: Access to all essential cryptocurrency metrics
- **🔌 Simple Interface**: Intuitive RESTful endpoints and JSON-RPC methods
- **🚦 Robust Error Handling**: Clear error messages with appropriate status codes
- **🧩 Easy Deployment**: Minimal configuration with guided setup process
- **📘 Extensive Documentation**: Clear usage instructions and examples

## 🚀 Quick Start

```bash
# Option 1: Install and run with npx
npx coingecko-api-server

# Option 2: Clone and install manually
git clone https://github.com/yourusername/coingecko-api-server.git
cd coingecko-api-server
npm install
npm run setup
npm start
```

## 📦 Installation

### Option 1: Using npx (Recommended)

The quickest way to get started:

```bash
npx coingecko-api-server
```

This will:
1. 📥 Download and install the server
2. 🧰 Run an interactive setup wizard
3. 🔑 Ask for your CoinGecko API key (optional)
4. 🚀 Start the server automatically

### Option 2: Manual Installation

For more control over the installation process:

```bash
# Clone the repository
git clone https://github.com/yourusername/coingecko-api-server.git
cd coingecko-api-server

# Install dependencies
npm install

# Run the setup script
npm run setup

# Start the server
npm start
```

## ⚙️ Configuration

The server is configured using environment variables in the `.env` file:

| Variable | Description | Default |
|----------|-------------|---------|
| `PORT` | Server port | `3000` |
| `COINGECKO_API_KEY` | CoinGecko Pro API key (optional) | - |
| `CACHE_DURATION` | Cache duration in seconds | `60` |
| `LOG_LEVEL` | Logging level (error, warn, info, debug) | `info` |

## 📚 API Reference

### RESTful Endpoints

#### Basic Endpoints
- `GET /api/ping` - Check API server status

#### Price Data
- `GET /api/simple/price` - Get price data for specified coins
  - Query params: `ids`, `vs_currencies`, `include_market_cap`, `include_24hr_vol`, `include_24hr_change`, `include_last_updated_at`, `precision`

#### Coin Data
- `GET /api/coins/markets` - Get market data for coins
  - Query params: `vs_currency`, `ids`, `category`, `order`, `per_page`, `page`, `sparkline`, `price_change_percentage`

#### Market Data
- `GET /api/global` - Get global cryptocurrency data
- `GET /api/search/trending` - Get trending coins

### Examples

**Get Bitcoin Price in USD:**
```bash
curl "http://localhost:3000/api/simple/price?ids=bitcoin&vs_currencies=usd"
```

**Response:**
```json
{
  "bitcoin": {
    "usd": 45678.12
  }
}
```

**Get Top 5 Cryptocurrencies by Market Cap:**
```bash
curl "http://localhost:3000/api/coins/markets?vs_currency=usd&order=market_cap_desc&per_page=5&page=1"
```

## 🤖 AI Integration (MCP)

This server implements the Marketplace Component Program (MCP) protocol, enabling AI systems like Claude to access cryptocurrency data.

### MCP Integration Points

1. **JSON-RPC Endpoint**: `/rpc` - Handles method calls from AI clients
2. **Schema Definition**: `/mcp/schema` - Defines available tools and parameters

### Available MCP Methods

- `ping` - Check API status
- `getPrice` - Get price data for specified cryptocurrencies
- `getSupportedVsCurrencies` - Get list of supported currencies
- `getCoinMarkets` - Get market data for coins
- `getGlobal` - Get global cryptocurrency data
- `getTrending` - Get trending coins

For detailed integration instructions, see [MCP_INTEGRATION.md](MCP_INTEGRATION.md).

## 💎 Pro API Benefits

This server supports both the CoinGecko Pro API and the free API:

| Feature | Free API | Pro API |
|---------|----------|---------|
| Rate Limit | ~30 calls/minute | ~500 calls/minute |
| API Throttling | Yes | No |
| Support | Community | Priority |
| Data Freshness | 10-30 minutes | 1-2 minutes |
| Price | Free | Subscription |

For more details about the Pro API setup, see [USING_COINGECKO_PRO.md](USING_COINGECKO_PRO.md).

## 🔧 Troubleshooting

| Issue | Solution |
|-------|----------|
| Rate limiting errors | Consider upgrading to Pro API or adjust your request frequency |
| Connection refused | Ensure the server is running on the specified port |
| Authentication errors | Check your API key in the .env file |
| Missing data | Verify the parameters in your request |

## 🧪 Development

```bash
# Run in development mode with hot reload
npm run dev

# Run tests
npm test

# Build for production
npm run build
```

## 🔄 How It Works

The server acts as a middleware between your applications and the CoinGecko API:

1. **Request Routing**: Handles incoming requests from RESTful and JSON-RPC clients
2. **API Selection**: Chooses between Free and Pro APIs based on configuration
3. **Rate Limit Management**: Implements intelligent request throttling
4. **Response Processing**: Formats and returns data in a consistent structure
5. **Error Handling**: Provides detailed error information for troubleshooting

## 📱 Use Cases

- **AI-Powered Financial Advisors**: Enable AI systems to access real-time crypto data
- **Investment Dashboards**: Build cryptocurrency dashboards with reliable data access
- **Portfolio Trackers**: Create applications to monitor crypto holdings
- **Market Analysis Tools**: Develop tools for technical and fundamental analysis
- **Trading Bots**: Power automated trading systems with market data

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- [CoinGecko](https://www.coingecko.com/) for the comprehensive cryptocurrency data API
- [Anthropic](https://www.anthropic.com/) for Claude AI and the MCP program
- The open-source community for their invaluable contributions

---

<div align="center">

**[⬆ Back to top](#-coingecko-api-server-mcp)**

Made with ❤️ by [Your Organization]

</div> 
