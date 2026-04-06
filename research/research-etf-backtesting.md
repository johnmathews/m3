# Dual Momentum with UCITS ETFs: Backtesting Deep Dive

_Research date: 4 Apr 2026_

## Executive Summary

For a retail investor in the Netherlands managing a €2,000 portfolio, implementing Gary Antonacci's Dual Momentum
strategy using DEGIRO's Core Selection ETFs offers a compelling, low-maintenance approach.

Key findings:

- **The Edge is Real but Compressing:** GEM historically delivered ~17% CAGR (1974-2013) with -22.7% max drawdown.
  Post-publication (2014-2023) CAGR dropped to ~6%, with max drawdown of -33.7%. 2022 showed vulnerability when equities
  and bonds declined simultaneously (-12.1% TAA aggregate drawdown).
- **12-Month Lookback is Standard but Fragile:** Highest CAGR in historical backtests, but Newfound Research (2019)
  showed severe specification fragility — a single month change produced a 21.5pp difference in annual return. An
  ensemble of lookbacks (6-12 months) may be more robust.
- **"Free" Trading Still Has Frictions:** DEGIRO Core Selection charges €1 handling fee per trade on Tradegate, plus
  bid-ask spreads.
- **Recent Regimes Favored US Dominance:** 2023-2025 — strategy would have parked in SXR8 (CSPX) with zero turnover,
  capturing 26%, 26%, 18% annual returns (USD terms; EUR returns differ due to FX movements).

## ETF Universe (DEGIRO Core Selection)

| ETF                                                                    | Tradegate Ticker | LSE Ticker | ISIN           | TER   | Inception |
| ---------------------------------------------------------------------- | ---------------- | ---------- | -------------- | ----- | --------- |
| iShares Core S&P 500 UCITS ETF USD Acc                                  | **SXR8**         | CSPX       | IE00B5BMR087   | 0.07% | 2010      |
| iShares Core MSCI World UCITS ETF USD Acc                               | **EUNL**         | SWDA       | IE00B4L5Y983   | 0.20% | 2009      |
| iShares Core Global Aggregate Bond UCITS ETF EUR Hedged Acc             | **EUNA**         | AGGH       | IE00BDBRDM35   | 0.10% | 2017      |

All are accumulating (dividends reinvested internally). **Use Tradegate tickers on DEGIRO** for Core Selection pricing
(€1/trade). Using LSE tickers routes to the London Stock Exchange at €3+/trade plus GBP currency conversion.

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

### Antonacci's Global Equities Momentum (1974-2013, in-sample)

| Metric                    | GEM     | Relative Only | Absolute Only | S&P 500 |
| :------------------------ | :------ | :------------ | :------------ | :------ |
| **CAGR**                  | 17.4%   | 13.4%         | 12.3%         | 11.4%   |
| **Annual Std Dev**        | 11.5%   | 14.4%         | 11.2%         | 14.2%   |
| **Sharpe Ratio**          | 0.96    | 0.64          | 0.70          | 0.52    |
| **Worst Calendar Year**   | -17.8%  | —             | —             | —       |
| **Max Drawdown**          | -22.7%  | -54.6%        | -29.6%        | -51.0%  |
| **% Profit Months**       | 69%     | 65%           | 67%           | 64%     |

_Note: The -17.8% figure is the worst single calendar year, not the peak-to-trough max drawdown (-22.7%). An independent
2000-2026 backtest (Extradash) shows 9.8% CAGR with -33.7% max drawdown, indicating significant post-publication decay._

### Crisis performance

- **2000-2002 dot-com:** GEM posted positive cumulative return (+18.7%) — the absolute momentum filter moved to bonds
  successfully.
- **2007-2009 GFC:** GEM drawdown approximately -17% — meaningful but far less than the S&P 500's -51%.
- **2022 rate hikes:** TAA strategies suffered -12.1% aggregate drawdown (equities AND bonds fell simultaneously). This
  exposed the structural risk of positive stock-bond correlation in an inflationary regime.

_Note: Earlier versions of this document cited -2.8% and -7.1% for the dot-com and GFC drawdowns. Those figures came from
AllocateSmartly's aggregate analysis of 70+ TAA strategies, not GEM specifically._

### Post-publication performance decay (critical)

The edge has compressed **substantially** since publication in 2014. Price Action Lab (2023) documented:

- **CAGR dropped from ~17% to ~6%** (a 66% decline)
- **Volatility increased 29%**
- **Max drawdown (-33.7%) matched the S&P 500** — eliminating the risk-adjusted advantage

Causes: (1) stock-bond correlation shifted from negative to positive after 2020, reducing the protective power of the
bond allocation; (2) possible overfitting of the 12-month lookback to the in-sample period; (3) crowding as the strategy
became widely known; (4) whipsaw losses in faster-moving markets.

## Lookback Period Sensitivity

| Lookback                 | CAGR  | Std Dev | Sharpe | Worst Drawdown |
| :----------------------- | :---- | :------ | :----- | :------------- |
| **12-month**             | 15.5% | 11.6%   | 0.95   | -17.8%         |
| **9-month**              | 13.9% | 11.4%   | 0.83   | -20.7%         |
| **6-month**              | 14.6% | 10.9%   | 0.93   | -21.6%         |
| **Composite (3/6/9/12)** | 14.3% | 10.2%   | 0.95   | -17.7%         |

**Caveat on lookback "optimality":** While 12-month wins in historical backtests, Newfound Research (2019) demonstrated
severe specification fragility: a single month change in lookback produced a 21.5 percentage point difference in annual
return. ReSolve Asset Management found that an **ensemble of lookbacks (6-12 months)** dominated nearly all individual
specifications in drawdown management. The composite row above hints at this — similar Sharpe, better drawdown. Consider
implementing an ensemble rather than betting on a single lookback period.

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
| **Backtrader** | Event-driven, granular       | Low-Moderate      | Moderate-High | Legacy (no releases since ~2019, needs patching for Python 3.10+) |
| **Zipline**    | Institutional pipelines      | Low               | High          | Archived (community fork: Zipline-Reloaded) |
| **NautilusTrader** | Production-grade execution | Very High (Rust core) | Moderate  | Active (free, recommended for validation) |
| **Freqtrade**  | Crypto bot + backtesting     | Moderate          | Moderate      | Active (best for crypto satellite) |

**Recommendation:** `vectorbt` for parameter sensitivity testing; `bt` for simple readable monthly logic; `NautilusTrader`
for realistic execution modeling before live deployment; `Freqtrade` for the crypto satellite (CCXT integration, backtest-
to-live pipeline, Telegram control).

## Data Sources

| Source                       | Coverage                           | Notes                                        |
| ---------------------------- | ---------------------------------- | -------------------------------------------- |
| **Yahoo Finance (yfinance)** | SWDA.L, CSPX.L, AGGH.L, EUNL.DE, SXR8.DE | Free; see data quality caveats below |
| **justETF**                  | TER, fund size, type verification  | Reference data, not time series              |
| **EOD Historical Data**      | Clean corporate action adjustments | Paid; worth it for serious backtesting       |
| **Norgate Data**             | Survivorship-bias-free             | Paid; gold standard                          |

For longer history, use underlying index data (MSCI World, S&P 500 Net TR).

### yfinance data quality caveats (as of 2025)

- **`Adj Close` column removed:** `auto_adjust=True` is now the default; all OHLC prices are automatically adjusted.
  Scripts relying on a separate `Adj Close` column will break.
- **Dividend data corruption:** Yahoo reports dividends + capital gain distributions summed together, causing
  over-adjusted prices and inflated historical returns.
- **Stock split adjustment errors:** Yahoo sometimes fails to apply splits correctly. Use `repair=True` and the built-in
  price repair module.
- **European ticker gaps:** Multiple reports of missing historical data for Euronext-listed tickers. Use multiple exchange
  suffixes (.AS, .L, .DE) and cross-validate.
- **Yahoo paywalling (March 2025):** Some historical data restricted to premium subscribers.
- **Survivorship bias:** yfinance only fetches currently listed tickers. Delisted ETFs are invisible. Partially mitigated
  for M3 because the universe is 2-3 large, liquid ETFs unlikely to be delisted.
- **Recommendation:** Always use `repair=True`; cross-validate against justETF factsheets or iShares provider data; pin
  your yfinance version; consider paid data (EOD Historical Data, Norgate) before deploying real capital.

## Realistic Return Expectations

After accounting for spreads, slippage, signal lag, €1 handling fees, and post-publication performance decay:

| Metric                        | Expected Range |
| ----------------------------- | -------------- |
| **CAGR**                      | 5–9%           |
| **Max Drawdown**              | 20–35%         |
| **Trades/Year**               | 1–3            |
| **Longest Underwater**        | 12–24 months   |
| **Years Underperforming B&H** | ~30–40%        |

_Note: These ranges are more conservative than Antonacci's in-sample results, reflecting the documented post-publication
performance decay (CAGR ~6% from 2014-2023). The 7-11% range cited in earlier versions of this document was based on
in-sample performance minus estimated frictions, which overstated realistic expectations._

## 2023-2025 Walk-through

### Signal history

- Early 2023: Both SXR8 (CSPX) and EUNL (SWDA) recovered above 12-month lookback → absolute momentum positive
- SXR8 12m return > EUNL 12m return → allocate 100% SXR8
- This signal held continuously through 2024 and 2025

### Returns captured

| Year | CSPX Return (USD) | CSPX Return (EUR, approx) | SWDA Return (USD) | GEM Position | Trades            |
| ---- | ------------------ | ------------------------- | ------------------ | ------------ | ----------------- |
| 2023 | 26.12%             | ~22%                      | 24.27%             | SXR8 (CSPX)  | 1 (initial entry) |
| 2024 | 25.73%             | ~34%                      | 19.11%             | SXR8 (CSPX)  | 0                 |
| 2025 | 18.05%             | varies                    | 21.03%             | SXR8 (CSPX)  | 0                 |

_Note: USD and EUR returns diverge significantly due to EUR/USD movements. A Dutch investor's actual returns are
EUR-denominated. The momentum signal itself can differ depending on which currency is used for the lookback calculation —
this is an implementation detail that must be decided and kept consistent._

**Key insight:** Zero turnover for 2+ years. The strategy captured the US tech rally while paying minimal fees (~€1 for
the initial entry). In 2025, SWDA actually outperformed — but the strategy correctly held SXR8 based on the 12-month
lookback at each monthly check.

## When Dual Momentum Fails

1. **Whipsaw markets:** Sideways oscillation around the SMA triggers false signals (buy high, sell low)
2. **Synchronous declines:** When equities AND bonds fall together (2022), the bond "safe harbor" fails. Since 2020,
   stock-bond correlation has shifted from negative to positive — this is a structural regime change, not a one-off.
   Consider whether a money market fund or cash is a better safe harbor than EUNA (AGGH) in the current regime.
3. **V-shaped recoveries:** 12-month lookback is slow — misses first 2-3 months of new bull markets
4. **The regret problem:** Sitting in EUNA while markets rally is psychologically brutal
5. **Post-publication decay:** GEM's edge has compressed significantly since 2014 (CAGR ~6% vs ~17% in-sample). This
   pattern is common with published strategies — a combination of crowding, regime change, and possible overfitting.
6. **Cash drag (DEGIRO-specific):** SXR8 trades at ~€575/share. With €1,400 for the ETF core, buying 2 shares = €1,150
   invested with €250 (17.9%) in uninvested cash earning 0% on DEGIRO. Consider Trade Republic (fractional shares from
   €1, 2% interest on cash) to eliminate this drag.

## Implementation Checklist

1. Last trading day of each month: pull closing prices for SXR8, EUNL, EUNA (Tradegate tickers)
2. Calculate 12-month return for SXR8 and EUNL (skip most recent month)
3. **Absolute filter:** Are both negative? → 100% EUNA (or consider money market fund / cash given current bond-equity
   correlation regime)
4. **Relative filter:** If positive, which is higher? → 100% in the winner
5. **Execute:** First trading day of new month, limit orders only
6. **Do not check mid-month. Do not override the system.**

## References

- Antonacci, G. "Extended Backtest of Global Equities Momentum" — optimalmomentum.com
- Antonacci, G. "Whither Fragility? Dual Momentum GEM" — optimalmomentum.com
- AllocateSmartly, "TAA Performance During the 2022 Bear Market" — allocatesmartly.com
- DEGIRO ETF Core Selection — degiro.com
- justETF profiles: CSPX (IE00B5BMR087), SWDA (IE00B4L5Y983), AGGH (IE00BDBRDM35)
- vectorbt.dev, bt (pmorissette/bt), NautilusTrader (nautilustrader.io), Freqtrade (freqtrade.io)
- Price Action Lab (2023), "Dual Momentum Post-Publication Performance" — priceactionlab.com
- Newfound Research (2019), "Fragility Case Study: Dual Momentum GEM" — blog.thinknewfound.com
- ReSolve Asset Management, "Global Equity Momentum: Executive Summary" — investresolve.com
- Extradash, "GEM 2000-2026 Backtest" — extradash.com
