# Strategy: LDC + MACD Hybrid v1

## Overview

**Entry logic:** Lorentzian Classification (ML-based k-NN)  
**Exit logic:** MACD histogram slope flip  
**Risk management:** ATR-based stop-loss + optional fixed USDT stop

## Key Features

### Entries
- **Lorentzian Distance Classification** (8 neighbors, 2000 bars lookback)
- 5 normalized features: RSI(14), WT(10,11), CCI(20), ADX(20), RSI(9)
- Kernel filter: Rational Quadratic (h=8, r=8, regression=25)

### Filters
- **Volatility filter** (enabled)
- **Regime filter** (threshold 0.1) — trend strength
- **ADX filter** (threshold 16, enabled) — avoid choppy markets
- **SMA(195) filter** (enabled) — directional bias

### Exits
- **MACD (34/89/9)** — Fibonacci-tuned, exits on histogram slope flip (global)
- **Entry hold period**: locks exits for first N bars (disabled by default)

### Risk Management
- **ATR Stop Loss** (14-period, 2x multiplier) — adaptive based on volatility
- **Fixed USDT SL** (optional, $100 default) — hard cap on loss per trade
- Combined mode: uses tighter of ATR/Fixed when both enabled

## Parameters

| Parameter | Default | Notes |
|-----------|---------|-------|
| Neighbors | 8 | k-NN neighbor count |
| Max Bars Back | 12000 | Lookback window (TV limit: 10000) |
| Regime Threshold | 0.1 | Higher = stricter trend filter |
| ADX Threshold | 16 | Min ADX to enter trade |
| MACD Fast/Slow | 34/89 | Fibonacci pair |
| ATR Length | 14 | Stop-loss ATR period |
| ATR Multiplier | 2.0 | SL distance in ATRs |

## Performance (Feb 2-18, 2026, 2m timeframe)

**Metrics:**
- Total P&L: +563 USDT (+0.56%)
- Profit Factor: 1.207
- Win Rate: 37.04% (50/135)
- Max Drawdown: 0.63%
- Total Trades: 135

**Commission:** 0.04% (taker fees assumed)

### Analysis
- ✅ Positive PF despite low win rate (good R:R)
- ⚠️ High trade frequency → commission drag (135 trades / 16 days)
- ⚠️ Short test period — needs longer validation
- 📊 Equity curve: strong start (trending market), gradual decay (choppy phase)

## Recommended Improvements

1. **Higher timeframe** (5m or 15m) → less noise, fewer commissions
2. **Trailing stop** instead of fixed ATR SL → let winners run
3. **LDC bar color exits** instead of MACD → faster, more aligned with entries
4. **Stronger ADX filter** (20+) → avoid ranging markets
5. **Longer backtest** (6+ months) → validate across market regimes

## Usage

1. Copy `ldc_macd_v1.pine` to TradingView Pine Editor
2. Apply to BTC/USDT Perpetual 2m chart (Binance)
3. Adjust commission in Properties to match your VIP level
4. Backtest on 6+ months before live deployment

## Dependencies

Requires TradingView libraries:
- `jdehorty/MLExtensions/2`
- `jdehorty/KernelFunctions/2`

---

**Version:** 1.0  
**Last Updated:** 2026-02-19  
**Status:** Experimental — requires extended validation
