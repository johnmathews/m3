# ETF Momentum Strategy Research

_Deep research completed 2026-04-04_

## Executive Summary

Momentum investing is a robust, academically validated strategy, but implementing it with a small €2,000 account in the
Netherlands requires strict cost control and risk management. The primary threat to a small momentum portfolio is not a
lack of edge, but the friction of trading costs, bid-ask spreads, and sudden market reversals (momentum crashes).

For a €2,000 account, traditional cross-sectional momentum (buying the top decile of a large universe) is unviable due to
high turnover and commission drag. Instead, the optimal approach is a **Dual Momentum** strategy utilizing a highly
concentrated universe of low-cost UCITS ETFs (via DEGIRO's Core Selection on Tradegate, €1/trade). By combining a
12-month relative momentum ranking with a 10-month Simple Moving Average (SMA) absolute momentum filter, investors can
capture the momentum premium while drastically reducing drawdowns and keeping trading costs minimal (~€24/year for monthly
rotation). Furthermore, with the 2026 Dutch Box 3
tax-free allowance set at €59,357, tax drag is a non-issue for this account size, allowing total focus on gross return
optimization and cost reduction.

## Evidence Base

The academic foundation for momentum is extensive and demonstrates persistence across time periods, geographies, and
asset classes.

### The Academic Edge

The momentum premium was formally documented by Jegadeesh and Titman (1993), who found that buying past winners and
selling past losers generated significant abnormal returns. Specifically, a portfolio formed on the basis of returns
realized in the past 6 months generated an average cumulative return of 9.5% over the next 12 months [1]. This was later
incorporated into standard asset pricing models via Carhart's four-factor model.

Further research by AQR (Asness, Moskowitz, Pedersen) in "Value and Momentum Everywhere" confirmed that momentum is not
isolated to US equities; it is a pervasive factor across international markets, including Europe, and across different
asset classes [2].

### Time-Series Momentum and Crash Risk

Moskowitz, Ooi, and Pedersen (2012) documented "time series momentum" (absolute momentum or trend following) across 58
liquid futures markets, showing strong average returns and positive performance during crisis periods [3]. However,
momentum is not without risk. Daniel and Moskowitz (2016) identified "momentum crashes," which typically occur during
market rebounds when past losers suddenly surge [4]. To mitigate this, Barroso and Santa-Clara (2015) demonstrated that
managing the volatility of momentum strategies virtually eliminates these crashes and nearly doubles the Sharpe ratio
[5].

## Strategy Design Choices

For a retail investor using UCITS ETFs, strategy design must balance theoretical purity with practical execution.

### Momentum Implementations Compared

| Approach              | Mechanism                                              | Crisis Behavior                                             | Complexity for €2k                                      |
| :-------------------- | :----------------------------------------------------- | :---------------------------------------------------------- | :------------------------------------------------------ |
| **Relative Momentum** | Ranks assets against each other (e.g., top 3 of 10)    | Vulnerable to market-wide crashes; stays fully invested     | High (requires frequent trading and multiple positions) |
| **Absolute Momentum** | Compares asset to its own history (e.g., 10-month SMA) | Moves to cash/bonds during downtrends, reducing drawdowns   | Low (simple binary rules)                               |
| **Dual Momentum**     | Combines relative ranking with absolute trend filter   | Highly defensive in crises; captures upside in bull markets | Medium (optimal balance of risk and return)             |

_Takeaway: Dual momentum is the superior choice for small accounts, as the absolute momentum filter protects capital
during severe bear markets, while relative momentum concentrates capital in the strongest trends._

### Lookback Periods and Rebalancing

Gary Antonacci's Dual Momentum approach typically utilizes a 12-month lookback period for both absolute and relative
momentum [6] [7]. Meb Faber's Global Tactical Asset Allocation (GTAA) research heavily utilizes a 10-month Simple Moving
Average (SMA) for trend following [8]. For a €2,000 account, a monthly check using a 12-month lookback (often skipping
the most recent month to avoid short-term reversal effects) is standard, but trading should only occur when signals
change to minimize turnover.

## Historical Performance Benchmarks

Simple momentum and trend-following rules have historically provided equity-like returns with bond-like drawdowns.

### Drawdown Reduction

Meb Faber's research on a simple 10-month SMA timing model applied to a 5-asset global portfolio from 1973-2012 showed
remarkable risk reduction. While a buy-and-hold approach suffered a maximum drawdown of 46%, the timing model reduced the
maximum drawdown to less than 10% [8]. The system kept the investor invested approximately 70% of the time [8].

### Out-of-Sample Performance

In the out-of-sample period from 2006 to 2012 (which includes the 2008 financial crisis), Faber's timing model
outperformed a buy-and-hold allocation by over two percentage points per year, with significantly lower volatility and
drawdowns [8]. Antonacci's dual momentum rules also historically shifted to bonds during major equities downturns,
preserving capital when it mattered most [6].

## Cost and Tax Engineering

With only €2,000, transaction costs can easily destroy the momentum edge.

### Broker Fee Reality (DEGIRO vs. IBKR)

| Broker                      | Fee Structure                                                    | Impact on Monthly Rotation (1 Buy, 1 Sell) |
| :-------------------------- | :--------------------------------------------------------------- | :----------------------------------------- |
| **DEGIRO (Core Selection)** | €1.00 handling fee per trade, Tradegate only [9]                  | ~€24.00 / year (1.2% drag on €2k)          |
| **DEGIRO (Non-Core)**       | €2.00 commission + €1.00 handling = €3.00 per trade [9]          | ~€72.00 / year (3.6% drag on €2k)          |
| **Interactive Brokers**     | Tiered: 0.05% (min €1.25) + exchange fees [10]                   | ~€48.00 / year (2.4% drag on €2k)          |
| **Trade Republic**          | €1.00 per manual trade; free via savings plan [14]               | €0–24 / year depending on automation       |

_Note: DEGIRO overhauled Core Selection on October 1, 2025 — expanded to ~1,500 ETFs on Tradegate, eliminated the Fair
Use Policy, and set a flat €1 handling fee per trade. The old "€0 under fair use" terms no longer apply._

_Note: Trade Republic offers fractional shares from €1 and free automated ETF savings plans. At €2k, DEGIRO's lack of
fractional shares creates significant cash drag (CSPX trades at ~€575/share, leaving up to 17% uninvested earning 0%).
Trade Republic also pays ~2% interest on uninvested cash. Consider Trade Republic as primary or complementary broker._

_Takeaway: A €2,000 account MUST use a low-cost broker. DEGIRO Core Selection (€1/trade on Tradegate) or Trade Republic
(€1/trade or free via savings plan) are the viable options. Paying €72/year on non-Core ETFs creates an insurmountable
3.6% performance drag._

### Dutch Box 3 Tax Implications (2026)

For 2026, the Dutch Belastingdienst has set the _heffingsvrij vermogen_ (tax-free wealth allowance) at €59,357 per person
(€118,714 for fiscal partners) [11]. The _forfaitair rendement_ (fictitious return) for investments (_beleggingen en
andere bezittingen_) is set at 6.00% [11]. Because a €2,000 account is well below the €59,357 threshold, Box 3 taxes will
not apply. Investors can trade without worrying about realizing capital gains or optimizing for dividend leakage beyond
standard UCITS efficiency.

## Risk Playbook

Even with minimal commissions, momentum strategies face structural risks.

- **Momentum Crashes:** As noted by Daniel and Moskowitz, momentum strategies can crash violently when bear markets
  suddenly reverse [4]. An absolute momentum filter (moving to cash/bonds when the 10-month SMA is breached) is mandatory
  to avoid holding toxic assets into a crash.
- **Bond-Equity Correlation Regime Change:** Since 2020, stock-bond correlation has shifted from negative to positive,
  driven by inflation dynamics. This is not a one-off (as in 2022) but a structural regime change. When the absolute
  momentum filter moves to AGGH during equity declines, bonds may fall simultaneously — breaking the core hedge mechanism
  of dual momentum. Consider whether a money market fund or cash position is a better "safe harbor" than bonds in the
  current regime.
- **Whipsaw in Sideways Markets:** Trend-following systems suffer "whipsaw" losses in oscillating markets. To mitigate
  this, use longer lookbacks (10-12 months) rather than short-term (1-3 months) signals, which trigger too frequently.
- **Implicit Costs (Spreads):** Even low-commission ETFs have bid-ask spreads. Trading highly liquid ETFs during optimal
  hours is critical.

## Implementation Blueprint: Low-Cost Dual Momentum Portfolio (DEGIRO Core Selection)

This blueprint is designed specifically for a €2,000 account on DEGIRO, using Tradegate tickers for Core Selection
pricing (€1/trade). The same ISINs trade on LSE and Euronext under different tickers — using the wrong exchange means
paying €3+/trade plus potential currency conversion fees.

1. **Universe Selection:** Select 3-4 highly liquid ETFs from DEGIRO's Core Selection on Tradegate [12].
   - _US Equities:_ iShares Core S&P 500 UCITS ETF — **SXR8** on Tradegate (ISIN: IE00B5BMR087; LSE ticker: CSPX)
   - _Global Equities:_ iShares Core MSCI World UCITS ETF — **EUNL** on Tradegate (ISIN: IE00B4L5Y983; LSE ticker: SWDA)
   - _Safe Haven/Bonds:_ iShares Core Global Aggregate Bond UCITS ETF — **EUNA** on Tradegate (ISIN: IE00BDBRDM35; LSE
     ticker: AGGH)
2. **Signal Generation (Monthly):** On the last trading day of the month, calculate the 12-month total return for the
   equity ETFs.
3. **Absolute Filter:** Check if the 12-month return of the best-performing equity ETF is greater than the return of a
   risk-free proxy (or simply > 0). Alternatively, check if its price is above its 10-month SMA.
4. **Execution:** If the absolute filter is positive, invest 100% of the €2,000 in the top-ranked equity ETF. If
   negative, invest 100% in the bond ETF (AGGH).

## Execution Best Practices

Execution timing matters. An evaluation of Xetra showed that implicit transaction costs at the best time of day are up to
30 percent lower than at the worst time [13].

- **Order Types:** Always use limit orders to control execution price and avoid market-maker exploitation during volatile
  periods.
- **Time of Day:** Trade when the underlying markets of the ETF are open. For US-focused ETFs (like SXR8), trade between
  15:30 CET and 17:30 CET when both European and US markets are active, ensuring the tightest bid-ask spreads.
- **Exchange:** Always use Tradegate for Core Selection pricing. Verify the ticker before placing orders — buying "CSPX"
  routes to LSE (€3+ per trade + GBP conversion), while "SXR8" routes to Tradegate (€1/trade, EUR-denominated).

## Tools

For a retail investor, complex software is unnecessary. Free tools like Yahoo Finance combined with a simple Excel
spreadsheet or a basic Python script (using `pandas` and `yfinance`) are sufficient to calculate 12-month returns and
10-month SMAs once a month.

**yfinance data quality caveats:** As of 2025, yfinance has known issues: `auto_adjust=True` is now the default (the
separate `Adj Close` column was removed), dividend data can be corrupted (Yahoo sums dividends + capital gain
distributions), and European tickers sometimes have gaps. Always use `repair=True`, cross-validate against justETF
factsheets or iShares provider data, and pin your yfinance version.

## Key Practitioners and Resources

- **Gary Antonacci:** Pioneer of Dual Momentum; his book and blog (_Optimal Momentum_) detail the 12-month lookback rules
  [6].
- **Meb Faber:** His paper "A Quantitative Approach to Tactical Asset Allocation" is the definitive guide to using the
  10-month SMA for risk reduction [8].
- **Andreas Clenow:** Author of _Stocks on the Move_, providing practical frameworks for systematic momentum.
- **AQR Capital Management:** Read their extensive research on "Value and Momentum Everywhere" and "Fact, Fiction and
  Momentum Investing" for rigorous academic backing [2].

## References

1. Jegadeesh & Titman (1993) —
   [Returns to Buying Winners and Selling Losers](https://www.bauer.uh.edu/rsusmel/phd/jegadeesh-titman93.pdf)
2. Asness, Moskowitz, Pedersen —
   [Fact, Fiction and Momentum Investing](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=2435323)
3. Moskowitz, Ooi, Pedersen (2012) — [Time Series Momentum](http://docs.lhpedersen.com/TimeSeriesMomentum.pdf)
4. Daniel & Moskowitz (2016) — [Momentum Crashes](https://www.kentdaniel.net/papers/published/jfe_16.pdf)
5. Barroso & Santa-Clara (2015) —
   [Momentum Has Its Moments](https://www.sciencedirect.com/science/article/abs/pii/S0304405X14002566)
6. Antonacci —
   [Extended Backtest of Global Equities Momentum](https://www.optimalmomentum.com/extended-backtest-of-global-equities-momentum/)
7. Antonacci — [Dual Momentum Investing](https://clame.nyu.edu/HomePages/E0A338/312653/DualMomentumInvesting.pdf)
8. Faber —
   [Protective Asset Allocation (PAA)](https://papers.ssrn.com/sol3/Delivery.cfm/SSRN_ID2764043_code1935527.pdf?abstractid=2759734)
9. DEGIRO — [Tarievenoverzicht](https://www.degiro.nl/data/pdf/Tarievenoverzicht.pdf)
10. Interactive Brokers —
    [Commissions Stock Europe](https://www.interactivebrokers.com/en/pricing/commissions-stocks-europe.php)
11. Belastingdienst —
    [Box 3-inkomen 2026](https://www.belastingdienst.nl/wps/wcm/connect/nl/box-3/content/berekening-box-3-inkomen-2026)
12. DEGIRO — [ETF Kernselectie](https://www.degiro.nl/tarieven/etf-kernselectie)
13. Deutsche Börse —
    [Xetra: Europe's Largest Trading Venue for ETFs](https://deutsche-boerse.com/resource/blob/252862/79c101abf9d17f5935767142f96c068d/brochure-xetra-europes-largest-trading-platform-for-etfs-data.pdf)
14. Trade Republic — [Kosten](https://traderepublic.com/nl-nl/kosten)
