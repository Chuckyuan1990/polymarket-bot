# polymarket-bot
Polymarket Bitcoin prediction market arbitrage bot using Chainlink Data Streams
BTC Polymarket Arbitrage Bot (Rust Edition)![Rust](https://img.shields.io/badge/rust-%23000000.svg?style=for-the-badge&logo=rust&logoColor=white)
![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)A high-performance, low-latency trading bot written in Rust for exploring opportunities in Polymarket's Bitcoin Up or Down prediction markets.The bot monitors real-time market data, estimates probabilities using a combination of volatility inputs and probabilistic modeling, and executes trades when favorable conditions are detected. It incorporates basic trend analysis and selected technical indicators to refine decision-making.Disclaimer: This project is for educational and research purposes only. Cryptocurrency and prediction market trading involves significant risk. The author is not responsible for any financial losses. Use at your own risk and ensure compliance with local regulations.FeaturesReal-time price monitoring from major cryptocurrency exchanges via WebSocket.
Volatility estimation and probabilistic opportunity detection.
Integration with Polymarket CLOB for market data and order execution (supports both proxy and EOA modes).
Lightweight trend and momentum filters for improved signal quality.
Configurable parameters (trade size, thresholds, intervals).
Comprehensive logging for analysis and debugging.

Strategy OverviewThe core approach involves comparing real-time price movements with estimated fair probabilities derived from market volatility data. Opportunities are identified when temporary mispricings appear in the prediction market relative to spot price behavior.Additional layers include lightweight trend analysis (e.g., short-term momentum) and common technical indicators to help filter signals and reduce exposure to false positives. The system aims to operate conservatively, focusing on high-confidence setups in short-duration markets.Exact implementation details are intentionally kept abstract to encourage personal exploration and adaptation.Installationbash

git clone https://github.com/yourusername/btc-polymarket-arbitrage-bot.git
cd btc-polymarket-arbitrage-bot
cargo build --release

Dependencies are managed via Cargo (tokio for async, tungstenite for WebSocket, reqwest for HTTP, etc.).ConfigurationCopy .env.example to .env and fill in your credentials:env

BINANCE_WS_URL=wss://stream.binance.com:443/ws/btcusdt@trade
DERIBIT_API_URL=https://www.deribit.com/api/v2
POLYMARKET_PRIVATE_KEY=your_private_key_here
POLYMARKET_API_KEY=your_api_key
POLYMARKET_API_SECRET=your_api_secret
POLYMARKET_API_PASSPHRASE=your_passphrase
TRADE_SHARES=10
PRICE_THRESHOLD=5.0
PRICE_CHECK_INTERVAL=2.0
TEST_MODE=true

Security Note: Use a dedicated test wallet with limited funds. Enable TEST_MODE=true for simulation (no real orders).Runningbash

cargo run --release

The bot will connect to exchanges, monitor markets, and log detected opportunities. Real orders are placed only when TEST_MODE=false.PerformanceLatency: Typically under 100ms end-to-end (WebSocket + async processing).
CPU-efficient with no garbage collection pauses.
Designed for stable, long-running operation on modest hardware.

ContributingContributions, issues, and feature requests are welcome. Feel free to fork and experiment.LicenseMIT License – see LICENSE for details.Happy trading (responsibly)! 

