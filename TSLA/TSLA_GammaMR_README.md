# TSLA MACD Rubberband — Gamma Scalp Strategy

Backtest of a systematic short-dated options strategy on TSLA, combining RSI 
extremes with a momentum-reversal MACD variant ("Rubberband") to time entries 
around gamma-driven mean reversion.

## Strategy logic
- **Entry**: RSI at an extreme (≤30 long / ≥76 short) AND MACD in the top/bottom 
  10% of its 156-bar (≈2.5 day) range AND MACD rate-of-change crosses a reversal 
  threshold — catching the inflection point of momentum itself, not a standard 
  MACD/signal line crossover.
- **Exit**: Fixed RSI target (+7/-14 points) OR a 50% stop-loss on the option OR 
  a 60-minute time stop.
- **Instrument**: 6 short-dated (3 DTE) TSLA option contracts, priced via a 
  Black-Scholes pricer (85% IV).
- **Benchmark**: compared against a simple 25-share, 3-day stock hold.

## Results (2018–2024, 143,394 five-minute bars)
251 total trades. Gamma scalp LONG: 85 trades, $7,155 P&L, 63.5% win rate. 
SHORT: 53 trades, $2,353 P&L, 47.2% win rate. Full year-by-year breakdown 
included, showing 2020 and 2022 as the strongest and weakest regimes 
respectively.

## Hypothesis test: does the MACD "dot" filter actually help?
Ran a controlled comparison — entries requiring the MACD rate-of-change 
reversal ("with dot") vs. a looser RSI-only filter with no reversal 
requirement ("no dot"), same 2018–2024 data:
