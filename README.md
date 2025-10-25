# Crypto Market Intelligence & Execution Tool

This project combines live market data, macro signals, social/news sentiment, regime detection, price forecasting, and optional trade execution into one research workflow.

## Features
- **Live OHLCV data:** Pulls recent candles from multiple crypto exchanges (Binance, Bybit, KuCoin, OKX, etc.) using `ccxt`.
- **Macro context:** Fetches SPX, VIX, DXY, oil, gold, yields from Yahoo Finance / FRED to gauge risk-on vs risk-off.
- **Sentiment engine:** Scrapes crypto headlines, Reddit posts, RSS feeds, Google Trends, optional Twitter/CryptoPanic, and scores them with VADER sentiment.
- **Market state modeling:**
  - Computes volatility, moving averages, trend, RSI.
  - Clusters behavior (KMeans) into regimes like BULL / BEAR / CHOP.
  - Labels phases like ACCUMULATION, MARKUP, DISTRIBUTION, MARKDOWN.
- **Forecasting:** Runs a Monte Carlo simulation (GBM + seasonal cycle component) to generate possible future price paths and P10/P50/P90 bands.
- **Decision layer:** Produces a BUY / SELL / HOLD suggestion with confidence, and calculates stop-loss / take-profit levels based on current conditions.
- **Visualization:** Interactive Plotly charts for price, sentiment, macro, forecast cone, and correlation heatmap.
- **Executor:** Can simulate or (if enabled and confirmed by the user) send a market order via `ccxt`. Defaults to safety-first / confirmation-required.

## Security / Privacy
- API keys (exchange, Twitter, Reddit, etc.) are **not** hardcoded. They are loaded from environment variables like `EXCHANGE_API_KEY`, `TWITTER_BEARER_TOKEN`, etc.
- Do not commit any real credentials or `.env` files.
- Live trading only happens if you explicitly confirm in the console.

This code is for research and education only. Not investment advice.
