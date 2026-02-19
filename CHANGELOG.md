# Changelog

All notable changes to this project will be documented in this file.

## [Unreleased]

### Planned
- Trailing stop implementation
- LDC bar color exit mode comparison
- 5m/15m timeframe optimization
- Extended backtest validation (6+ months)

## [1.0.0] - 2026-02-19

### Added
- Initial LDC + MACD hybrid strategy implementation
- Lorentzian Classification ML entries (8 neighbors, 5 features)
- MACD (34/89/9) Fibonacci-tuned exits
- ATR-based adaptive stop-loss (14-period, 2x multiplier)
- Fixed USDT stop-loss option ($100 default)
- Volatility, Regime, ADX filters
- SMA(195) directional bias filter
- Kernel trend filter (Rational Quadratic, h=8, r=8)
- Entry hold period (locks exits for N bars after entry)
- Combined exit modes: MACD / LDC bar color / Keltner
- Project structure: strategies/, backtests/, research/, docs/
- Documentation and backtest results (Feb 2-18, 2m)

### Technical
- Pine Script v6
- TradingView Strategy Tester
- Dependencies: jdehorty/MLExtensions/2, jdehorty/KernelFunctions/2

### Performance (Feb 2-18, 2m)
- Net Profit: +563 USDT (+0.56%)
- Profit Factor: 1.207
- Win Rate: 37.04%
- Max DD: 0.63%
- Total Trades: 135

### Known Issues
- Short test period (16 days) — needs extended validation
- High trade frequency causes commission drag on 2m timeframe
- Performance degrades in choppy/ranging markets
- MACD exits may be too slow for mean reversion

---

Format: [Keep a Changelog](https://keepachangelog.com/)  
Versioning: [Semantic Versioning](https://semver.org/)
