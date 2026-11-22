# AI Orderflow Scanner

Live app (GitHub Pages) plus an optional 24/7 cloud scanner (GitHub Actions).

## 1. Put the app online (about 3 minutes, works from a phone browser)
1. Create a new **public** repository on GitHub and upload everything in this folder (keep the `docs` and `.github` folders).
2. Settings > Pages > Source: **Deploy from a branch**, branch **main**, folder **/docs**. Save.
3. Open `https://YOUR-NAME.github.io/YOUR-REPO/`. In Settings inside the app, paste your Claude API key to use the AI scan.

The app shows live candle open, high, low and close, a countdown to bar close, a TradingView chart, DOM, heat map, footprint, volume profile and VWAP.

## 2. Optional: 24/7 scanner with Telegram alerts (GitHub Actions)
Repo > Settings > Secrets and variables > Actions. Secret `ANTHROPIC_API_KEY` is required; `TELEGRAM_BOT_TOKEN`, `TELEGRAM_CHAT_ID`, `METAAPI_TOKEN`, `METAAPI_ACCOUNT_ID` are optional.
Variables (all optional): `HL_COIN`, `SYMBOL`, `TF`, `RISK_MODE` (pct or lot), `RISK_VALUE`, `MAX_LOT`, `MIN_CONF`, `MAX_TRADES_PER_DAY`, `COOLDOWN_MIN`, `CONTRACT_OZ`, `PAUSED` (set to 1 to pause), `EXECUTE` (leave unset to scan and alert only).
Run Actions > scan > Run workflow once. The latest signal then shows on the app's Signals tab.
GitHub runs schedules on a best-effort basis and can delay them by several minutes, so do not rely on it for auto-execution.

## Notes
- The TradingView chart is TradingView's free embed. TradingView does not give its price data to outside code, so the engine numbers (candles, depth, trades) come from Hyperliquid's public feed.
- Analytics only, not financial advice.
