# Research Gaps & Alternatives: Supplementary Findings

_Research date: 6 Apr 2026_

This document addresses six specific gaps identified in the existing M3 research documents.
All findings are based on web research conducted in April 2026, not training data.

---

## 1. Alternatives to Dual Momentum for Small European Accounts

### Are there better options than dual momentum for a EUR 2,000 account?

Short answer: Dual momentum remains the most practical choice for a EUR 2,000 UCITS-only
account. Alternatives exist but introduce complexity, higher costs, or access barriers that
make them unsuitable at this scale.

### Managed Futures / Trend-Following ETFs

Europe finally received its first UCITS managed futures ETF in March 2025: the **iMGP DBi
Managed Futures Fund R USD UCITS ETF** (ISIN: LU2951555585, ticker: DBMF:FP), with a TER
of 0.75%. This replicates the same strategy as the US-listed DBMF. A second product, the
**iMGP DBi Managed Futures Ex-Commodities Fund R USD UCITS ETF (MFA8)**, was also launched
as Europe's first Article 8 (SFDR) managed futures ETF, also at 0.75% TER.

**Assessment for EUR 2,000 account:**
- The 0.75% TER is 4-10x higher than the core UCITS ETFs used in the dual momentum strategy
  (CSPX at 0.07%, SWDA at 0.20%)
- These ETFs struggled in 2025 due to lack of clear market trends and high uncertainty
- They are useful as a diversifier but not as a primary strategy at this account size
- Not currently in DEGIRO's Core Selection, meaning EUR 3 per trade + EUR 2.50 exchange fee

**Key US-listed products (not available to EU retail under PRIIPs):** DBMF, KMLM, CTA (now
over USD 1 billion AUM). The Simplify CTA ETF took in over USD 570 million in net new assets
in 2025 alone, showing strong institutional and retail demand in the US.

### Risk Parity / All Weather Portfolio

The classic Dalio-style allocation (30% stocks, 55% bonds, 7.5% gold, 7.5% commodities) can
be implemented with UCITS ETFs. In March 2025, State Street and Bridgewater launched the
**SPDR Bridgewater All Weather ETF (ALLW)** at 0.85% TER with approximately 1.8x leverage
via futures -- but this is US-listed and unavailable to EU retail.

**DIY UCITS implementation** requires 4-5 ETFs:
- Equities: Xtrackers MSCI World UCITS ETF (0.19% TER)
- Bonds: iShares Core Global Aggregate Bond UCITS ETF (0.10% TER)
- Gold: iShares Physical Gold ETC
- Commodities: various UCITS commodity ETFs

**Assessment for EUR 2,000 account:**
- Splitting EUR 2,000 across 4-5 positions creates impractically small positions (EUR 150 in
  commodities, EUR 400 in stocks)
- Without fractional shares (DEGIRO does not support them), rounding errors dominate
- Monthly rebalancing across 4+ positions at EUR 1 per trade generates EUR 48-60/year in fees
- Risk parity requires periodic rebalancing based on volatility estimates, adding complexity
- The 2022 experience showed that when equities and bonds fall simultaneously, risk parity
  suffers the same failure mode as dual momentum's bond safe haven

### Multi-Factor ETFs

European investors can access multi-factor ETFs such as the **iShares STOXX Europe Equity
Multifactor UCITS ETF** (ISIN: IE00BG13YL86, TER 0.25%, EUR 178M AUM) which combines
Momentum, Quality, Value, and Small Size factors. Single-factor ETFs also exist, such as the
**iShares Edge MSCI Europe Momentum Factor UCITS ETF (IEFM)**.

**Assessment for EUR 2,000 account:**
- A single multi-factor ETF is a "set and forget" approach -- less alpha but also less effort
- Does not provide the crisis protection of dual momentum's absolute momentum filter
- Could serve as one of the equity legs in the dual momentum universe (replacing or
  supplementing SWDA)
- The factor premium has been compressing since publication of the original academic research

### Accelerating Dual Momentum

The Engineered Portfolio variant of dual momentum picks between S&P 500 and International
Small Caps when markets have positive momentum, falling back to US Treasury bonds when
negative. It requires only a single ETF position at any time, making it viable from
approximately EUR 1,000.

**Critical limitation for European investors:** The outperformance of Accelerating Dual
Momentum disappeared when the US-listed VINEX fund was replaced with comparable European
UCITS small-cap ETFs. This is a known issue documented in community backtests.

### Verdict

Dual momentum with 2-3 DEGIRO Core Selection ETFs remains optimal for EUR 2,000:
- Single position at a time = no fragmentation
- EUR 0-1 per trade = negligible fee drag
- Monthly check = minimal time commitment
- Crisis protection via absolute momentum filter

Consider adding managed futures exposure only when the account grows past EUR 10,000 and the
iMGP UCITS products gain more track record.

Sources:
- [HedgeNordic: Europe Gets Its Managed Futures UCITS ETF](https://hedgenordic.com/2025/03/europe-gets-its-managed-futures-ucits-etf-with-imgp-dbi-launch/)
- [iMGP DBi Managed Futures Fund UCITS ETF on justETF](https://www.justetf.com/en/etf-profile.html?isin=LU2951555585)
- [All Seasons Portfolio EU](https://allseasonsportfolio.eu/portfolio-compositions/)
- [iShares STOXX Europe Equity Multifactor UCITS ETF on justETF](https://www.justetf.com/en/etf-profile.html?isin=IE00BG13YL86)
- [Engineered Portfolio: Accelerating Dual Momentum](https://engineeredportfolio.com/2018/05/02/accelerating-dual-momentum-investing/)
- [TuringTrader: Accelerating Dual Momentum](https://www.turingtrader.com/portfolios/ep-accelerating-dual-momentum/)
- [ETF Trends: Managed Futures ETFs Rising](https://www.etftrends.com/managed-futures-etfs-rising-tiversification-call/)
- [Return Stacked: Managed Futures Trend Following](https://www.returnstacked.com/managed-futures-trend-following/)

---

## 2. Commission-Free ETF Platforms in Europe (Beyond DEGIRO)

### Platform Comparison for Netherlands-Based Investors (2026)

| Feature | DEGIRO | Trade Republic | Scalable Capital | BUX |
|:---|:---|:---|:---|:---|
| **HQ / Regulator** | Netherlands / AFM+DNB | Germany / BaFin | Germany / BaFin | Netherlands / AFM |
| **Available in NL** | Yes | Yes (since 2022) | Yes | Yes |
| **ETF trade fee** | EUR 1 (Core Selection via Tradegate) or EUR 3 + EUR 2.50/yr per exchange | EUR 1 flat per trade | EUR 0 for PRIME ETFs >= EUR 250, else EUR 0.99 | EUR 0 (Zero Orders, max 3/month), EUR 1.99 (market/limit) |
| **ETF savings plans** | Free execution | Free execution, from EUR 1/month | Free execution, from EUR 1/month | Available, fractional support |
| **Fractional shares** | **No** | **Yes** (from EUR 1) | **Yes** | **Yes** |
| **Number of ETFs** | ~1,500 (Core Selection on Tradegate); 5,000+ total | ~2,700 | 2,000+ in savings plans | Limited selection |
| **Interest on cash** | No | 2% annual (no stated cap) | Varies by plan | No |
| **Deposit protection** | EUR 100k (DNB) + EUR 20k investor compensation | EUR 100k per client | EUR 100k | EUR 100k (DGS) + EUR 20k investor compensation |
| **Subscription fee** | None (free plan) or EUR 4.99/month (PRIME+) | None | None (FREE) or subscription for PRIME+ | EUR 2.99/month (EUR 36/year) |
| **Debit card** | No | Yes | No | No |

### Key Findings

**Trade Republic** is the strongest alternative for a small Dutch account:
- Fractional shares from EUR 1 solve the "whole shares only" problem that plagues DEGIRO at
  EUR 2,000
- Free automated ETF savings plans eliminate the need for manual monthly rebalancing
- 2% interest on uninvested cash provides a return while waiting for signals
- EUR 1 per manual trade is competitive
- Regulatory oversight by BaFin with EUR 100k deposit protection

**Scalable Capital** recently launched in the Netherlands and offers:
- Free ETF savings plans from EUR 1/month
- EUR 0 trading on PRIME ETFs (Amundi, iShares, Xtrackers) for orders >= EUR 250
- Weekly, bi-weekly, monthly, or quarterly scheduling

**BUX** is a Dutch-licensed (AFM) alternative but has drawbacks:
- EUR 36/year subscription fee is 1.8% drag on a EUR 2,000 account
- "Zero Orders" are limited to 3 per month and execute end-of-day (between 16:00-17:00 CET)
- Cannot transfer assets to other providers due to fractional share restrictions
- BUX engages in securities lending as a revenue source

### Important Caveat: "Zero-Commission" Is Not Zero Cost

As documented by Banker on Wheels, the EU banned Payment for Order Flow (PFOF) under MiFID
II revisions. Brokers like Trade Republic, Scalable Capital, and others previously routed
orders to specific private exchanges (gettex, Lang & Schwarz) where a single market maker per
instrument leads to wider spreads and lower transparency. The hidden cost via spread widening
can exceed the saved commission, especially for less liquid instruments.

**Recommendation:** For the dual momentum strategy (monthly trades, highly liquid ETFs), the
spread cost difference is likely negligible. But for any higher-frequency strategy, compare
total execution cost (commission + spread) rather than commission alone.

### DEGIRO Core Selection Update (October 2025)

Since October 2025, DEGIRO expanded its Core Selection to approximately 1,500 ETFs on
Tradegate (previously around 100 ETFs). The fee structure changed:
- EUR 1 handling cost for the first order per ETF per calendar month
- Subsequent same-direction orders above EUR 1,000 in the same ETF are free
- All Core Selection ETFs must be traded on Tradegate
- Tradegate operates 07:30-22:00, but spreads widen outside 09:00-17:30
- Research suggests trades above EUR 2,000 may become more expensive on Tradegate vs.
  reference exchanges

Sources:
- [EU Personal Finance: DEGIRO vs Trade Republic 2026](https://www.eupersonalfinance.eu/articles/degiro-vs-trade-republic)
- [DEGIRO vs Scalable Capital 2026](https://jeangalea.com/degiro-vs-scalable-capital/)
- [Trade Republic NL: Fractional Trading](https://support.traderepublic.com/en-nl/1420-How-do-I-trade-fractions)
- [Scalable Capital Netherlands](https://nl.scalable.capital/en)
- [BUX Review 2026](https://investingintheweb.com/reviews/bux-review/)
- [Curvo: BUX Review](https://curvo.eu/article/bux-review)
- [Curvo: DEGIRO Core Selection](https://curvo.eu/article/degiro-core-selection-etf)
- [Banker on Wheels: PFOF Is Dead, Conflict of Interest Is Worse](https://www.bankeronwheels.com/pfof-and-quote-driven-venues/)
- [Best ETF Brokers in Netherlands 2026](https://www.ucits-etfs.com/reviews/the-best-etf-brokers-in-netherlands-august-2025/)
- [Trade Republic NL](https://traderepublic.com/en-nl)

---

## 3. Practical Limitations of Backtesting with yfinance Data

### Known Data Quality Issues (Documented on GitHub)

**1. Adjusted Close column removal (auto_adjust change):**
The `Adj Close` column was removed from yfinance's default output. With `auto_adjust=True`
(now the default), all OHLC prices are automatically adjusted for splits and dividends. Users
requiring both adjusted and unadjusted prices must set `auto_adjust=False`. This change has
caused confusion and broken existing backtesting scripts that relied on the separate `Adj
Close` column.

**2. Dividend data corruption:**
Yahoo Finance reports the sum of dividends AND capital gain distributions in the dividend
column, which is incorrect. This causes the Adjusted Close calculation to over-adjust prices,
producing inflated historical return calculations. This is a Yahoo Finance upstream issue, not
a yfinance bug. (GitHub issue [#2666](https://github.com/ranaroussi/yfinance/issues/2666))

**3. Stock split adjustment errors:**
Yahoo sometimes fails to apply stock splits to historical prices, or applies pre-split
dividends to post-split prices, resulting in double-adjustment. The yfinance library added a
`repair=True` option and a dedicated price repair module that fetches 1-day data, repairs it,
then resamples for multi-day intervals. (GitHub issue [#1531](https://github.com/ranaroussi/yfinance/issues/1531))

**4. Missing price data for European tickers:**
Multiple reports of missing historical data for Euronext-listed tickers. Dates that show
prices on the exchange's own historical page are absent from Yahoo Finance. This affects
backtesting accuracy for European ETFs specifically. (GitHub issue [#2607](https://github.com/ranaroussi/yfinance/issues/2607))

**5. Yahoo Finance Premium paywalling (March 2025):**
Yahoo Finance appeared to restrict some historical data downloads to premium subscribers (Gold
plan). The issue manifested as "possibly delisted; no price data found" errors. Workarounds
included upgrading yfinance to v0.2.58+ and disabling ad blockers (Pi-hole was a known
trigger). The situation remains fluid. (GitHub issue [#2340](https://github.com/ranaroussi/yfinance/issues/2340))

### Survivorship Bias

yfinance can only fetch data for currently listed tickers. Delisted ETFs, merged funds, and
closed share classes are invisible. Academic research shows this can overstate annual returns
by 1-4% and inflate Sharpe ratios dramatically (one example showed Sharpe going from 0.09 to
0.66 when delisted assets were excluded).

For the M3 dual momentum strategy, survivorship bias is partially mitigated because:
- The universe is only 2-3 highly liquid, well-established ETFs (CSPX, SWDA, AGGH)
- These ETFs are unlikely to be delisted given their size (billions in AUM)
- For pre-inception backtesting, index data is used (as documented in research-etf-backtesting.md)

However, survivorship bias remains a real concern if the universe is ever expanded to include
smaller or thematic ETFs.

### European ETF-Specific Issues

- **Ticker symbol complexity:** European ETFs trade on multiple exchanges with different
  tickers (e.g., IWDA.AS for Amsterdam, IWDA.L for London, EUNL.DE for Xetra). yfinance
  requires the exchange suffix, and data quality varies by exchange.
- **Currency complications:** A EUR-denominated ETF on Euronext Amsterdam may show different
  returns than the same ETF in USD on the London Stock Exchange. Backtests must use consistent
  currency.
- **Lower data reliability:** European exchange data on Yahoo Finance historically has more
  gaps and errors than US exchange data.

### Recommendations for M3 Backtesting

1. **Always use `repair=True`** when fetching data via yfinance
2. **Cross-validate** yfinance data against at least one other source (justETF, the ETF
   provider's own factsheet, or the exchange's historical data page)
3. **Use index data** for periods before ETF inception rather than relying on proxy tickers
4. **Consider paid data** (EOD Historical Data, Norgate) for any strategy that will manage
   real capital -- the cost is trivial relative to potential losses from bad data
5. **Pin yfinance version** in requirements to avoid breaking changes from auto_adjust behavior

Sources:
- [Why Adj Close Disappeared in yfinance](https://medium.com/@josue.monte/why-adj-close-disappeared-in-yfinance-and-how-to-adapt-6baebf1939f6)
- [yfinance GitHub Issue #2666: Dividends data incorrect](https://github.com/ranaroussi/yfinance/issues/2666)
- [yfinance GitHub Issue #1531: Stock split repair](https://github.com/ranaroussi/yfinance/issues/1531)
- [yfinance GitHub Issue #2607: Missing price data](https://github.com/ranaroussi/yfinance/issues/2607)
- [yfinance GitHub Issue #2340: Premium subscription requirement](https://github.com/ranaroussi/yfinance/issues/2340)
- [yfinance GitHub Issue #2070: Adjusted Close vs Total Return](https://github.com/ranaroussi/yfinance/issues/2070)
- [yfinance Price Repair documentation](https://ranaroussi.github.io/yfinance/advanced/price_repair.html)
- [Survivorship Bias in Backtesting (Luxalgo)](https://www.luxalgo.com/blog/survivorship-bias-in-backtesting-explained/)

---

## 4. VectorBT Maintenance Status & Python Backtesting Landscape (2026)

### VectorBT Open Source

- **Latest release:** v0.28.5 (released around early 2026, with v0.28.4 on January 26, 2025
  adding pandas 2.0 and modern Python support via pyproject.toml migration)
- **License:** Apache 2.0 with Commons Clause (free to use, but cannot sell products
  primarily based on the software)
- **Maintenance:** Healthy. Bug fixes and Python version compatibility updates continue. New
  features are community-driven via pull requests.
- **Key limitation:** The open-source version does not receive the advanced execution modeling,
  portfolio callbacks, or infrastructure features available in PRO.

### VectorBT PRO

- **Pricing:** USD 20/month (early adopter price, will increase) or USD 500 lifetime for
  GitHub updates
- **Status:** Actively developed with priority maintenance
- **v1.2.0 (October 2025):** Added native tick-level resolution and slippage models matching
  Binance real fills within 0.3%
- **Key features over open source:** Advanced execution modeling, DuckDB/Parquet integration,
  production-oriented tooling

### Correction to Existing Research

The `research-etf-backtesting.md` document lists Backtrader as "Active" and Zipline as
"Archived." This needs updating:

| Framework | Status in Existing Doc | Actual Status (2026) | Notes |
|:---|:---|:---|:---|
| **vectorbt (open source)** | Active | Active (maintenance mode) | Bug fixes only; new features via community PRs |
| **vectorbt PRO** | Not mentioned | Active (priority development) | USD 20/month or USD 500 lifetime |
| **Backtrader** | Active | **Legacy/Archived** | No releases since ~2019; Python 3.10+ requires manual patching; community forks (Backtrader2) fragment ecosystem |
| **Zipline** | Archived | Partially revived as **Zipline-Reloaded** | Community-maintained fork; best for Pipeline API factor research |
| **bt** | Active | Active (mature/stable) | Good for simple monthly rebalancing logic |
| **NautilusTrader** | Not mentioned | **Active (recommended)** | Rust core + Python API; free; production-grade execution semantics |
| **Backtesting.py** | Not mentioned | Active | Lightweight single-asset prototyping with Bokeh visualizations |
| **PyBroker** | Not mentioned | Active | ML-first framework with Numba acceleration and walkforward validation |
| **Freqtrade** | Not mentioned | Active | Crypto-focused bot; CCXT exchange integration; open source |
| **pysystemtrade** | Not mentioned | Active | Systematic futures; risk-budgeting; Interactive Brokers connectivity |

### Recommended Workflow for M3

The 2026 consensus is a **phased approach**:

1. **Discovery phase (current M3 stage):** Use vectorbt (open source) for rapid signal
   validation and parameter sensitivity testing. Its vectorized approach enables running
   thousands of backtests in seconds.
2. **Validation phase:** For strategies that pass initial screening, re-test with more
   realistic execution modeling. NautilusTrader is the gold standard here (free, open source,
   Rust-compiled core for speed).
3. **Deployment phase:** For the simple dual momentum strategy, even `bt` or a custom pandas
   script is sufficient. The monthly rebalancing cadence does not require sophisticated
   execution modeling.

For the crypto satellite, **Freqtrade** remains the best option for integrated backtesting
through to live bot deployment with CCXT exchange connectivity.

Sources:
- [Python Backtesting Landscape 2026](https://python.financial/)
- [VectorBT GitHub Releases](https://github.com/polakowo/vectorbt/releases)
- [VectorBT PRO](https://vectorbt.pro/)
- [VectorBT PRO Pricing](https://vectorbt.pro/become-a-member/)
- [AutoTradeLab: Backtrader vs NautilusTrader vs VectorBT vs Zipline-Reloaded](https://autotradelab.com/blog/backtrader-vs-nautilusttrader-vs-vectorbt-vs-zipline-reloaded)
- [DEV.to: Backtrader vs VnPy vs Qlib (2026)](https://dev.to/linou518/backtrader-vs-vnpy-vs-qlib-a-deep-comparison-of-python-quant-backtesting-frameworks-2026-3gjl)
- [Snyk Advisor: vectorbt](https://snyk.io/advisor/python/vectorbt)

---

## 5. EU MiCA Regulation Impact on Retail Crypto Trading in the Netherlands

### Timeline

- **December 30, 2024:** MiCA entered into force. AFM issued the EU's first CASP (Crypto-Asset
  Service Provider) licenses on day one to MoonPay, BitStaete, ZBD, and Hidden Road.
- **June 30, 2025:** Netherlands transitional period ended (shorter than the EU-wide July 1,
  2026 deadline). All Dutch CASPs had to be MiCA-compliant by this date.
- **2026:** The Netherlands accounts for over 20% of all EU MiCA licenses issued, second only
  to Germany.

### What MiCA Means for M3's Crypto Satellite

**Exchange compliance:**
- Approximately 130-140 CASP licenses have been issued EU-wide, representing significant
  market consolidation from the hundreds of thousands of VASPs that previously operated
- Both Bitvavo (DNB-registered) and Kraken (EU-compliant) have secured MiCA authorization
- Only exchanges holding MiCA authorization or operating via EU passporting may serve Dutch
  users

**Retail investor protections:**
- 14-day cooling-off period for crypto purchases made directly from the offeror (no fees, no
  questions asked for withdrawal)
- CASPs must provide fair, clear, and transparent marketing communications
- Conflict-of-interest management requirements
- Complaint-handling procedures mandatory

**What MiCA does NOT do (relevant gaps):**
- MiCA does not impose specific leverage limits on spot crypto trading
- Leverage limits come from MiFID II for crypto derivatives/CFDs:
  - Crypto CFDs: maximum 2:1 leverage for retail investors
  - Non-major forex: 20:1
  - Major forex: 30:1
- Negative balance protection is mandatory for retail clients
- Margin closeout at 50% equity

**Reporting requirements (from January 2026):**
- Crypto service providers must report client data to the Belastingdienst
- This does not change the Box 3 treatment but makes enforcement automatic
- M3's crypto satellite documentation already accounts for this (maintain year-end records)

**Impact assessment for M3:**
- **Low direct impact.** The chosen exchanges (Bitvavo, Kraken) are compliant.
- The main practical effect is increased confidence in platform stability and fund safety.
- No new restrictions on the strategies described in the crypto satellite research.
- The reporting requirement means the Belastingdienst will independently verify crypto
  holdings, so accurate record-keeping is even more important.

Sources:
- [Sumsub: MiCA Regulation and EU Crypto Rules 2026](https://sumsub.com/blog/crypto-regulations-in-the-european-union-markets-in-crypto-assets-mica/)
- [InnReg: MiCA Regulation Updated Guide 2026](https://www.innreg.com/blog/mica-regulation-guide)
- [ComplyFactor: MiCA VASP & CASP Crypto Regulations in Netherlands](https://complyfactor.com/mica-vasp-casp-crypto-regulations-in-netherlands/)
- [ComplyFactor: MiCA Regulation Guide 2026](https://complyfactor.com/mica-regulation-guide-2026-eu-crypto-asset-framework-explained/)
- [Skadden: MiCA Update -- Six Months in Application](https://www.skadden.com/insights/publications/2025/07/mica-update-six-months-in-application)
- [CoinLaw: EU MiCA Regulations Statistics](https://coinlaw.io/eu-mica-regulations-statistics/)
- [News of Israel: Trading Regulation in Netherlands 2026](https://www.newsofisrael.com/regulation/trading-regulation-in-netherlands-2026-retail-safety-guide/)
- [Lightspark: Is Crypto Legal in Netherlands 2026](https://www.lightspark.com/knowledge/is-crypto-legal-in-netherlands)

---

## 6. Fractional Shares: DEGIRO Support and Strategic Implications

### DEGIRO: No Fractional Shares

DEGIRO does not offer fractional share trading and there is no indication this will change.
You must buy whole units. This has concrete implications for a EUR 2,000 account:

**Example with current prices (approximate, April 2026):**
- CSPX trades at approximately EUR 550-600 per share
- SWDA trades at approximately EUR 95-100 per share
- AGGH trades at approximately EUR 5 per share

With EUR 2,000 and CSPX at EUR 575:
- You can buy 3 shares = EUR 1,725 invested, EUR 275 uninvested (13.75% cash drag)
- On any given month, the signal might require switching from CSPX to SWDA:
  selling 3 x CSPX (EUR 1,725) and buying ~17 SWDA shares (EUR 1,700), leaving EUR 25 cash

With AGGH at EUR 5 per share, the rounding problem is negligible.

**Cash drag impact:** Uninvested cash earns nothing on DEGIRO (unlike Trade Republic's 2%
interest). Over a year, 5-15% average cash drag on EUR 2,000 reduces effective capital by
EUR 100-300.

### Platforms That Support Fractional Shares

| Platform | Minimum Investment | Fractional ETF Support | Savings Plan |
|:---|:---|:---|:---|
| **Trade Republic** | EUR 1 | Yes | Yes, automated, free |
| **Scalable Capital** | EUR 1 | Yes (in savings plans) | Yes, free |
| **BUX** | EUR 10 | Yes | Yes |
| **DEGIRO** | Whole shares only | No | Free execution but whole shares only |

### Would Fractional Shares Change the Strategy?

**Yes, materially, for a EUR 2,000 account.**

1. **Elimination of cash drag:** Invest 100% of capital every month, not 85-95%.
2. **Smoother rebalancing:** Switch from one ETF to another without rounding losses.
3. **Savings plan automation:** Set up a monthly EUR 1,400 (or whatever the ETF core
   allocation is) automated investment plan that executes the dual momentum signal without
   manual intervention. Trade Republic's savings plans execute free.
4. **Lower barrier to diversification:** If the strategy is ever expanded to hold 2-3
   positions, fractional shares make a 50/30/20 split across three ETFs possible at EUR 2,000.

### Strategic Recommendation

Consider using **Trade Republic as the primary broker** instead of (or alongside) DEGIRO for
the ETF core strategy:

**Advantages over DEGIRO:**
- Fractional shares solve the cash drag problem
- Free automated savings plans for hands-off execution
- 2% interest on uninvested cash (EUR 40/year on EUR 2,000 while fully in cash -- relevant
  when the absolute momentum filter moves to bonds)
- EUR 1 per manual trade (same as DEGIRO Core Selection)

**Disadvantages vs. DEGIRO:**
- Fewer ETFs available (~2,700 vs. DEGIRO's ~5,000+ total)
- Regulated by BaFin (Germany), not AFM/DNB (Netherlands) -- still solid but not local
- Trade Republic routes to specific exchanges (Lang & Schwarz), potentially wider spreads
- Platform is simpler / less customizable than DEGIRO
- DEGIRO is publicly listed (Frankfurt Stock Exchange) providing more transparency

**Hybrid approach:** Use Trade Republic for the automated monthly ETF savings plan (fractional
shares, free execution) and DEGIRO for any expansion into broader ETF universe or manual
trading where exchange choice matters.

**Important caveat for the dual momentum strategy:** The savings plan approach works if the
signal stays constant (buy the same ETF each month). When the signal changes (e.g., switch
from CSPX to AGGH), you need to: (1) cancel the existing savings plan, (2) sell the current
holding, (3) set up a new savings plan for the new ETF. This requires manual intervention
once a month when the signal changes, which happens 1-3 times per year on average.

Sources:
- [DEGIRO: Does DEGIRO offer fractional shares?](https://www.degiro.com/uk/helpdesk/orders/does-degiro-offer-fractional-shares)
- [InvestingInTheWeb: DEGIRO Fractional Shares Alternatives](https://investingintheweb.com/brokers/degiro-fractional-shares/)
- [Trade Republic NL: How do I trade fractions?](https://support.traderepublic.com/en-nl/1420-How-do-I-trade-fractions)
- [EU Personal Finance: Trade Republic Review 2026](https://www.eupersonalfinance.eu/articles/trade-republic-review)
- [EU Personal Finance: DEGIRO vs Trade Republic 2026](https://www.eupersonalfinance.eu/articles/degiro-vs-trade-republic)
- [BrokerChooser: DEGIRO Fractional Share Conditions](https://brokerchooser.com/broker-reviews/degiro-review/degiro-fractional-shares)
- [Curvo: DEGIRO Core Selection](https://curvo.eu/article/degiro-core-selection-etf)
