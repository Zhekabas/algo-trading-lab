# Algo Trading Lab 🎯

Algorithmic trading strategies and backtests for cryptocurrency futures markets.

## Overview

This repository contains trading strategies, backtests, and research for BTC/USDT perpetual futures on Binance.

**Primary focus:**
- Timeframes: 2m - 30m (intraday/scalping)
- Market: BTC/USDT Perpetual (Binance)
- Strategy types: Machine learning (Lorentzian Classification), momentum, mean reversion

## Structure

```
├── strategies/          # Pine Script strategy implementations
├── backtests/          # Backtest results and analysis
├── research/           # Experimental features and optimization
└── docs/               # Documentation and notes
```

## Current Work

- **LDC + MACD Hybrid**: Lorentzian Classification entries with MACD-based exits
- **Risk Management**: ATR-based and fixed USDT stop-loss implementations
- **Filter Optimization**: Regime, volatility, and ADX filters for cleaner signals

## Tech Stack

- **Platform**: TradingView (Pine Script v6)
- **Analysis**: Python (in progress)
- **Backtesting**: TradingView Strategy Tester

## Disclaimer

This is educational and experimental work. Not financial advice.

---

**Status**: Active development
