# Funding Capture Strategy — Delta Exchange (1 Trade/Day)

**Validated funding-capture backtest strategy for Delta Exchange India perpetual futures.**

## 📊 Result Summary

| Metric | Value |
|--------|-------|
| Coins | 66 (per-chunk top 30) |
| Trades | 162 (exactly 1/day) |
| Win rate | 75.9% |
| Net PnL | +$80.62 (40% on $200) |
| Max Drawdown | -2.24% |
| Monthly positive | 7/7 (100%) |
| Risk-Reward | 1.28 |
| Walk-forward | PASS (OOS 76.2% win, 4/4 months) |

## 🧠 Strategy Logic

- **Funding NEGATIVE → LONG** | **Funding POSITIVE → SHORT**
- Entry = (T−1 min) candle OPEN, Exit = (T+1 min) candle OPEN
- T = funding time (UTC), 200 USDT fixed notional
- Fee 0.05% on exit only
- Net% = Price PnL + Funding PnL − 0.05%
- **Priority:** C6 (1.0%+) → C5 → C4 → C3 → C2 → C1
- **1 trade/day** — best coin per day by chunk priority + star score

## 📁 Chunks (|funding|)

| Chunk | Range | BE Win Rate |
|-------|-------|-------------|
| C1 | 0.1–0.2% | 63.2% |
| C2 | 0.2–0.4% | 58.5% |
| C3 | 0.4–0.6% | 59.1% |
| C4 | 0.6–0.8% | 48.1% |
| C5 | 0.8–1.0% | 50.8% |
| C6 | 1.0%+ | 51.7% |

## ⭐ Selection Criteria (Watchlist)

- Win rate ≥ break-even (per chunk)
- Net PnL > 0
- Min 4 trades
- Wilson score (sample-safe win rate) + Profit Factor + DD penalty
- Star rating 5★→1★ per chunk × coin

## 📂 Files

| File | Description |
|------|-------------|
| `s5_final_trades.csv` | 162 trades (date, symbol, chunk, side, entry/exit, PnL) |
| `s5_final_coins.csv` | 66 coins (chunk, coin, score) |
| `s5_equity_dd_rr.png` | Equity + Drawdown + RR/monthly chart |
| `walkforward_funding.json` | Walk-forward validation (in-sample/out-of-sample) |
| `grid_strategies_result.json` | 5 strategies comparison (S1–S5) |
| `GRID_5STRATEGIES_REPORT.md` | Strategy grid report |
| `final_watchlist_v3.csv` | 79-coin watchlist (star rating) |
| `funding_watchlist_final.csv` | 79-coin final watchlist |
| `FUNDING_CAPTURE_STRATEGY.md` | Full strategy documentation |

## ⚠️ Disclaimer

Backtest only. Past performance ≠ future results. Leverage >10x carries high risk. Not financial advice.
