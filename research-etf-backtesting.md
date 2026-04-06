# Dual Momentum with UCITS ETFs: Backtesting Deep Dive

_Research date: 4 Apr 2026_

## Executive Summary

For a retail investor in the Netherlands managing a €2,000 portfolio, implementing Gary Antonacci's Dual Momentum
strategy using DEGIRO's Core Selection ETFs offers a compelling, low-maintenance approach.

Key findings:

- **The Edge is Real but Compressing:** GEM historically delivered 15.8% CAGR with -17.8% max drawdown since 1950.
  However, 2022 showed vulnerability when equities and bonds declined simultaneously (-12.1% TAA aggregate drawdown).
- **12-Month Lookback Remains the Standard:** Highest CAGR and lowest drawdown vs 6 or 9-month alternatives.
- **"Free" Trading Still Has Frictions:** DEGIRO Core Selection charges €1 handling fee per trade, plus bid-ask spreads.
- **Recent Regimes Favored US Dominance:** 2023-2025 — strategy would have parked in CSPX with zero turnover, capturing
  26%, 26%, 18% annual returns.

## ETF Universe (DEGIRO Core Selection)

| ETF                                                                    | Tracks                   | TER   | Inception |
| ---------------------------------------------------------------------- | ------------------------ | ----- | --------- |
| **CSPX** (iShares Core S&P 500 UCITS ETF USD Acc)                      | 500 largest US stocks    | 0.07% | 2010      |
| **SWDA** (iShares Core MSCI World UCITS ETF USD Acc)                   | Developed world equities | 0.20% | 2009      |
| **AGGH** (iShares Core Global Aggregate Bond UCITS ETF EUR Hedged Acc) | Global bonds             | 0.10% | 2017      |

All are accumulating (dividends reinvested internally).

## Backtesting Methodology

### Avoiding common pitfalls

- **Look-ahead bias:** Only use data available on signal date
- **Survivorship bias:** Use index proxies for pre-inception periods
- **Overfitting:** Stick to the published 12-month lookback; don't optimize
- **Walk-forward analysis:** Split data into in-sample (build) and out-of-sample (validate)
- **Monte Carlo simulation:** Shuffle trade sequences to test robustness

### Handling ETF inception dates

- Pre-CSPX: Use S&P 500 Net Total Return index (minus TER)
- Pre-SWDA: Use MSCI World Net TR index (minus TER)
- Pre-AGGH: Use Bloomberg Global Aggregate EUR-hedged TR index (minus TER)
- Splice index data to ETF data at inception

### Dividends

Always use Total Return (dividend-adjusted) data. Accumulating ETFs reinvest internally — price-only data will understate
momentum and trigger false sell signals.

## Published Backtest Results (GEM)

### Antonacci's Global Equities Momentum

| Metric              | GEM    | Relative Only | Absolute Only | S&P 500 |
| :------------------ | :----- | :------------ | :------------ | :------ |
| **CAGR**            | 15.8%  | 13.4%         | 12.3%         | 11.4%   |
| **Annual Std Dev**  | 11.5%  | 14.4%         | 11.2%         | 14.2%   |
| **Sharpe Ratio**    | 0.96   | 0.64          | 0.70          | 0.52    |
| **Worst Drawdown**  | -17.8% | -54.6%        | -29.6%        | -51.0%  |
| **% Profit Months** | 69%    | 65%           | 67%           | 64%     |

### Crisis performance

- **2000-2002 dot-com:** GEM drawdown only -2.8%
- **2007-2008 GFC:** GEM drawdown only -7.1%
- **2022 rate hikes:** TAA strategies suffered -12.1% aggregate drawdown (equities AND bonds fell simultaneously)

### Out-of-sample degradation

The edge has compressed somewhat since publication, largely due to lower structural bond yields reducing the protective
power of the bond allocation.

## Lookback Period Sensitivity

| Lookback                 | CAGR  | Std Dev | Sharpe | Worst Drawdown |
| :----------------------- | :---- | :------ | :----- | :------------- |
| **12-month**             | 15.5% | 11.6%   | 0.95   | -17.8%         |
| **9-month**              | 13.9% | 11.4%   | 0.83   | -20.7%         |
| **6-month**              | 14.6% | 10.9%   | 0.93   | -21.6%         |
| **Composite (3/6/9/12)** | 14.3% | 10.2%   | 0.95   | -17.7%         |

**Verdict:** 12-month wins on CAGR and drawdown. Composite adds complexity for no real improvement.

## Variations and Enhancements

### Absolute filter: SMA vs ROC

- 10-month SMA and 12-month ROC produce highly comparable results
- Pick one and stick with it; the discipline matters more than the method

### Expanding the universe

Adding European equities (STOXX 600), Emerging Markets, REITs, or Gold could diversify but:

- More assets = more trades = more fees
- At €2k, concentration in 1 position is fine
- Consider expanding when account grows past €10k

### Top 1 vs Top 2-3 holdings

- GEM concentrates in top 1 — simpler, proven
- Holding 2-3 requires splitting €2k into tiny positions (impractical)

## Python Backtesting Frameworks

| Framework      | Best For                     | Speed             | Complexity    | Status   |
| :------------- | :--------------------------- | :---------------- | :------------ | :------- |
| **vectorbt**   | Parameter sweeps, vectorized | Very High (Numba) | Moderate      | Active   |
| **bt**         | Simple monthly rebalancing   | Moderate          | Low           | Active   |
| **Backtrader** | Event-driven, granular       | Low-Moderate      | Moderate-High | Active   |
| **Zipline**    | Institutional pipelines      | Low               | High          | Archived |

**Recommendation:** `vectorbt` for parameter sensitivity testing; `bt` for simple readable monthly logic.

## Data Sources

| Source                       | Coverage                           | Notes                                        |
| ---------------------------- | ---------------------------------- | -------------------------------------------- |
| **Yahoo Finance (yfinance)** | SWDA.L, CSPX.L, AGGH.L             | Free; verify Adj Close for accumulating ETFs |
| **justETF**                  | TER, fund size, type verification  | Reference data, not time series              |
| **EOD Historical Data**      | Clean corporate action adjustments | Paid; worth it for serious backtesting       |
| **Norgate Data**             | Survivorship-bias-free             | Paid; gold standard                          |

For longer history, use underlying index data (MSCI World, S&P 500 Net TR).

## Realistic Return Expectations

After accounting for spreads, slippage, signal lag, and €1 handling fees:

| Metric                        | Expected Range |
| ----------------------------- | -------------- |
| **CAGR**                      | 7–11%          |
| **Max Drawdown**              | 15–25%         |
| **Trades/Year**               | 1–3            |
| **Longest Underwater**        | 12–24 months   |
| **Years Underperforming B&H** | ~30–40%        |

## 2023-2025 Walk-through

### Signal history

- Early 2023: Both CSPX and SWDA recovered above 12-month lookback → absolute momentum positive
- CSPX 12m return > SWDA 12m return → allocate 100% CSPX
- This signal held continuously through 2024 and 2025

### Returns captured

| Year | CSPX Return | SWDA Return | GEM Position | Trades            |
| ---- | ----------- | ----------- | ------------ | ----------------- |
| 2023 | 26.12%      | 24.27%      | CSPX         | 1 (initial entry) |
| 2024 | 25.73%      | 19.11%      | CSPX         | 0                 |
| 2025 | 18.05%      | 21.03%      | CSPX         | 0                 |

**Key insight:** Zero turnover for 2+ years. The strategy captured the US tech rally while paying €0 in fees. In 2025,
SWDA actually outperformed — but the strategy correctly held CSPX based on the 12-month lookback at each monthly check.

## When Dual Momentum Fails

1. **Whipsaw markets:** Sideways oscillation around the SMA triggers false signals (buy high, sell low)
2. **Synchronous declines:** When equities AND bonds fall together (2022), the bond "safe harbor" fails
3. **V-shaped recoveries:** 12-month lookback is slow — misses first 2-3 months of new bull markets
4. **The regret problem:** Sitting in AGGH while markets rally is psychologically brutal

## Implementation Checklist

1. Last trading day of each month: pull closing prices for CSPX, SWDA, AGGH
2. Calculate 12-month return for CSPX and SWDA (skip most recent month)
3. **Absolute filter:** Are both negative? → 100% AGGH
4. **Relative filter:** If positive, which is higher? → 100% in the winner
5. **Execute:** First trading day of new month, limit orders only
6. **Do not check mid-month. Do not override the system.**

## References

- Antonacci, G. "Extended Backtest of Global Equities Momentum" — optimalmomentum.com
- Antonacci, G. "Whither Fragility? Dual Momentum GEM" — optimalmomentum.com
- AllocateSmartly, "TAA Performance During the 2022 Bear Market" — allocatesmartly.com
- DEGIRO ETF Core Selection — degiro.com
- justETF profiles: CSPX (IE00B5BMR087), SWDA (IE00B4L5Y983), AGGH (IE00BDBRDM35)
- vectorbt.dev, bt (pmorissette/bt), backtrader.com
