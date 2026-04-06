# Verification of Momentum Strategy Claims

_Research completed 2026-04-06_

## Summary

Web research was conducted to verify specific claims in `research-etf-momentum.md` and related momentum investing assertions. Each claim is evaluated below with source citations and a verdict.

---

## Claim 1: Antonacci's GEM delivered 15.8% CAGR with -17.8% max drawdown since 1950

**Verdict: PARTIALLY VERIFIABLE, LIKELY OVERSTATED**

The exact figures 15.8% CAGR and -17.8% max drawdown could not be directly confirmed from any publicly accessible source. Antonacci's performance data is presented as images/charts on his website, making exact extraction difficult. What the sources do confirm:

- **1974-2013 period (from Antonacci's book):** GEM CAGR was **17.43%** with a max drawdown of **22.72%** and worst single year of **-17.84%**. The "-17.8%" figure in the claim may be confusing "worst single year" with "max drawdown" -- these are different metrics. ([einvestingforbeginners.com](https://einvestingforbeginners.com/global-equities-momentum-ansh/))
- **1950-2018 extended backtest:** Antonacci reports GEM outperformed the S&P 500 by 440 basis points annually. If the S&P 500 returned ~10.5% CAGR over that period, GEM would be ~15% CAGR, roughly consistent with 15.8%. ([optimalmomentum.com](https://www.optimalmomentum.com/extended-backtest-of-global-equities-momentum/))
- **2000-2026 period:** An independent backtest on Extradash shows GEM with a **9.79% CAGR** and **-33.73% max drawdown** over 2000-2026. ([extradash.com](https://extradash.com/en/strategies/programs/117/dual-momentum-gem-2000-to-2026/))
- **ReSolve Asset Management** examined 1,226 GEM specifications from 1950-2018 and found the median strategy lost an average of 17.4% across its 5 worst drawdowns. ([investresolve.com](https://investresolve.com/global-equity-momentum-executive-summary/))

**Key concern:** The 15.8% CAGR figure likely applies to a specific historical period (possibly 1974-2013) and not the full 1950-present range. The max drawdown of -17.8% appears to be the worst single calendar year, not the peak-to-trough drawdown, which was -22.72% in the original backtest and -33.73% in an independent 2000-2026 test.

---

## Claim 2: 12-month lookback is optimal vs 6 or 9-month alternatives

**Verdict: CONTESTED -- DEPENDS ON DEFINITION OF "OPTIMAL"**

- Antonacci uses a 12-month lookback and cites academic support: it performed best in Jegadeesh & Titman (1993) and Moskowitz et al. (2012). ([quantifiedstrategies.com](https://www.quantifiedstrategies.com/dual-momentum-trading-strategy/))
- However, **Newfound Research (Corey Hoffstein, 2019)** demonstrated significant "specification fragility." In 2010, a 10-month lookback returned +12.2% while a 9-month lookback returned **-9.31%** -- a 21.5 percentage point swing from a single month change. This fragility is a serious concern. ([blog.thinknewfound.com](https://blog.thinknewfound.com/2019/01/fragility-case-study-dual-momentum-gem/))
- Newfound's recommendation: diversify across lookback periods (6-12 months) to reduce specification risk rather than betting on a single lookback being "optimal."
- Robot Wealth's quant review noted that "the 'default' lookback window of 12-months is conveniently the best lookback period available," calling this a "sign of caution" regarding potential overfitting. ([robotwealth.com](https://robotwealth.com/dual-momentum-review/))

---

## Claim 3: Faber's 10-month SMA reduced max drawdown from 46% to <10% (1973-2012)

**Verdict: CONFIRMED**

This is well-documented in Faber's paper "A Quantitative Approach to Tactical Asset Allocation" and its updates:

- The 5-asset portfolio (S&P 500, 10-year Treasuries, MSCI EAFE, GSCI Commodities, REITs) with buy-and-hold had a max drawdown of **-46.0%**. The 10-month SMA timing model reduced this to **-9.5%**. ([mebfaber.com](https://mebfaber.com/wp-content/uploads/2016/05/SSRN-id962461.pdf), [allocatortraining.com](https://allocatortraining.com/wp-content/uploads/2023/06/A-Quantitative-Approach-to-Tactical-Asset-Allocation.pdf))
- Annualized return: timing model 10.5% vs. buy-and-hold 9.9%.
- Volatility: timing model 7.0% vs. buy-and-hold 10.3%.
- Only one down year of less than -1% since 1973.

---

## Claim 4: GEM drawdown in 2000-2002 was only -2.8%, in 2007-2008 only -7.1%

**Verdict: THESE ARE TAA AGGREGATE FIGURES, NOT GEM-SPECIFIC**

This is a critical misattribution. The -2.8% (2000-2002) and -7.1% (2007-2008) figures come from **AllocateSmartly's aggregate analysis of ~70+ TAA strategies**, not from Antonacci's GEM specifically:

- AllocateSmartly reported: "TAA's max drawdown in 2022 (-12.1%) was significantly worse than in either 2000-02 (-2.8%) or 2007-08 (-7.1%)." ([allocatesmartly.com](https://allocatesmartly.com/tactical-asset-allocation-performance-during-the-2022-bear-market/))
- For GEM specifically during 2000-2002: Global markets dropped 49%, and Dual Momentum "remained largely flat." In 2001-2002, GEM had a **cumulative positive return of +18.7%** while the S&P 500 lost -33.7%. ([financialwisdomtv.com](https://www.financialwisdomtv.com/post/dual-momentum))
- For GEM during 2007-2009: Global markets dropped 56%, and Dual Momentum fell approximately **-17%** (not -7.1%). The original backtest shows a max drawdown of -22.72% for the full period. ([turingtrader.com](https://www.turingtrader.com/portfolios/antonacci-dual-momentum/))

**The -2.8% and -7.1% figures are real but describe the average TAA strategy universe, not GEM alone.** GEM likely did better in 2000-2002 (positive return) but worse in 2007-2008 (around -17%).

---

## Claim 5: 2022 TAA strategies suffered -12.1% aggregate drawdown

**Verdict: CONFIRMED**

This is directly from AllocateSmartly's analysis of their tracked universe of 70+ TAA strategies:

- Aggregate TAA max drawdown in 2022: **-12.1%**
- Strategies with low exposure to rising rates: -8.0%
- Strategies with high exposure to rising rates: -17.3%
- The failure was caused by TAA's reliance on bonds (IEF, TLT) as defensive assets. Bonds failed to offset equity losses in a rising rate environment. ([allocatesmartly.com](https://allocatesmartly.com/tactical-asset-allocation-performance-during-the-2022-bear-market/))

---

## Claim 6: CSPX returned 26%, 26%, 18% in 2023-2025

**Verdict: APPROXIMATELY CORRECT (in USD)**

Multiple sources confirm CSPX (USD-denominated, accumulating share class) returns:

- **2023:** 26.12% (confirmed via Yahoo Finance, Morningstar)
- **2024:** 25.73% (confirmed -- the document's "26%" is a rounding)
- **2025:** 18.05% (confirmed via multiple sources)

These align closely with S&P 500 total returns: 26.3% (2023), 25.0% (2024), 17.9% (2025). ([slickcharts.com](https://www.slickcharts.com/sp500/returns), [finance.yahoo.com](https://finance.yahoo.com/quote/CSPX.L/performance/))

**Note:** In EUR terms (relevant for Dutch investors), returns differ significantly due to USD/EUR movements. Alphacubator reports EUR-denominated returns of 22.28% (2023) and 33.87% (2024). ([alphacubator.com](https://www.alphacubator.com/analysis/CSPX.AS))

---

## Has Dual Momentum's Edge Degraded Since Publication?

**Verdict: YES, SIGNIFICANTLY**

This is the most important finding of this research.

**Pre-publication (1974-2013):**
- CAGR: 17.43%
- Volatility: 12.64%
- Max drawdown: -22.72%

**Post-publication (2014-2021):**
- CAGR: **5.89%** (a 66% drop in annual returns)
- Volatility: **16.36%** (a 29% increase in volatility)
- Max drawdown: **-33.72%** (worse than the entire pre-publication history)

([linkedin.com - Aissaoui](https://www.linkedin.com/pulse/dual-momentum-pre-post-publication-performance-abdennour-aissaoui), [priceactionlab.com](https://www.priceactionlab.com/Blog/2023/03/dual-momentum/))

**Price Action Lab analysis (2014-2023):**
- GEM CAGR dropped to **6.3%** vs SPY's **10.8%**
- GEM max drawdown matched SPY at **-33.7%**
- The strategy went from outperforming to significantly underperforming on a risk-adjusted basis.

Explanations offered:
1. **Regime change:** The stock-bond correlation shifted from negative to positive after 2020, breaking a core assumption of the strategy.
2. **Selection bias:** The 12-month lookback was the "best" historically, but this may reflect overfitting.
3. **Whipsaw losses:** In 2018-2021, the strategy reportedly entered stocks during drawdowns and bonds during rallies -- the exact opposite of its design intent.

---

## Recent Academic Research (2024-2025)

### Momentum Factor Still Persistent
- A 150-year study (1866-2024) found momentum turned $1 into over $10,000, annualizing at ~8-9%. This is "not an artifact of a particular methodology." ([CFA Institute, Dec 2025](https://blogs.cfainstitute.org/investor/2025/12/17/momentum-investing-a-stronger-more-resilient-framework-for-long-term-allocators/))
- A forthcoming 2026 Journal of Portfolio Management paper examines 4,000+ portfolio specifications and finds Sharpe ratios ranging 0.38-0.94 depending on implementation.

### Key Nuances
- **Crash risk remains severe:** Traditional price momentum has experienced max drawdowns of **-88%**. Volatility scaling can nearly halve this. ([CFA Institute](https://blogs.cfainstitute.org/investor/2025/12/17/momentum-investing-a-stronger-more-resilient-framework-for-long-term-allocators/))
- **Crowding risk is growing:** More capital chasing momentum strategies creates crowded positions that can unwind sharply. ([ScienceDirect](https://www.sciencedirect.com/science/article/pii/S0378426625001992))
- **Multidimensional approach superior:** Combining 11 momentum signals (not just price) delivers better risk-adjusted returns. Single-signal strategies like GEM are more fragile.
- **2024 was strong for momentum:** US Momentum's rolling 12-month excess return hit the 96th percentile over 50 years. ([SSGA](https://www.ssga.com/us/en/intermediary/insights/what-drove-momentums-strong-2024-and-what-it-could-mean-for-2025))
- **2025 YTD more mixed:** As of March 2025, dual momentum models showed Conservative +1.41%, Moderate -0.58%, Aggressive -3.68%.

---

## Criticism of Dual Momentum from Reputable Sources

### Newfound Research (2019) -- Specification Fragility
The most rigorous critique. Showed that minor changes to lookback period produce dramatically different outcomes. A single month change in lookback led to a 21.5 percentage point difference in annual return for 2010. Recommendation: diversify across specifications. ([blog.thinknewfound.com](https://blog.thinknewfound.com/2019/01/fragility-case-study-dual-momentum-gem/))

### ReSolve Asset Management (2019) -- Craftsman's Perspective
Examined 1,226 GEM specifications. Found the "ensemble" (average of all lookbacks) dominated nearly all individual specifications in drawdown management. Challenged the idea that any single lookback is reliably optimal. ([investresolve.com](https://investresolve.com/global-equity-momentum-executive-summary/))

### Robot Wealth -- Quant's Review
Noted concentration risk (100% in one asset), the suspiciously convenient optimality of the 12-month lookback, and difficulty of psychological adherence during underperformance periods. ([robotwealth.com](https://robotwealth.com/dual-momentum-review/))

### A Wealth of Common Sense (Ben Carlson, 2015)
Raised concerns about: backtesting limitations, underperformance since 2009, concentration risk (all-in on one asset class), psychological difficulty of dramatic allocation shifts, and whipsaw risk. ([awealthofcommonsense.com](https://awealthofcommonsense.com/2015/07/my-thoughts-on-gary-antonaccis-dual-momentum/))

### Morningstar -- Tactical Allocation Funds
Broader category analysis: "most tactical-allocation funds have been on the wrong foot more often than not." The average tactical fund badly underperformed a 60/40 portfolio over the decade ended April 2023. ([morningstar.com](https://www.morningstar.com/funds/why-tactical-allocation-funds-failedagain))

### Price Action Lab (2023)
Documented the sharp post-publication performance decay: returns dropped 66%, volatility increased 29%, and max drawdown exceeded the pre-publication worst. Attributed to regime change and selection bias. ([priceactionlab.com](https://www.priceactionlab.com/Blog/2023/03/dual-momentum/))

---

## Implications for the Research Document

The research document (`research-etf-momentum.md`) is broadly sound in its strategic framework but would benefit from these corrections:

1. **Temper the performance expectations.** Post-publication GEM has delivered ~6% CAGR with worse drawdowns than buy-and-hold S&P 500. The 17% CAGR figure is pre-publication and likely unrepeatable.
2. **Correct the drawdown attribution.** The -2.8% and -7.1% figures are TAA aggregates from AllocateSmartly, not GEM-specific numbers.
3. **Add lookback diversification.** Rather than using a single 12-month lookback, using an ensemble of 6-12 month lookbacks (per Newfound Research) materially reduces specification fragility.
4. **Acknowledge the bond regime risk.** The 2022 failure of bonds as a safe haven is structural, not temporary. If stock-bond correlation remains positive, dual momentum's core hedge mechanism is impaired.
5. **CSPX return figures are correct** in USD terms (~26%, ~26%, ~18% for 2023-2025). For a Dutch investor, EUR-denominated returns will differ.
