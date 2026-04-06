# Supplementary Research: Gaps & Alternatives

_Date: 2026-04-06_

## What was done

Conducted web research on six specific gaps identified in the existing M3 research documents.
All findings sourced from live web searches, not training data. Results written to
`/research-gaps-and-alternatives.md`.

## Key decisions / insights

1. **Dual momentum confirmed as best fit for EUR 2,000.** Managed futures UCITS ETFs now
   exist in Europe (iMGP DBi, launched March 2025) but at 0.75% TER they are too expensive
   for the core strategy. Risk parity requires 4-5 positions, impractical at this scale.
   Multi-factor ETFs are "set and forget" but lack crisis protection.

2. **Trade Republic is a serious contender over DEGIRO.** Fractional shares (from EUR 1),
   free savings plans, and 2% interest on cash address the key weaknesses of DEGIRO for a
   small account. The cash drag from whole-share-only trading on DEGIRO is 5-15% at EUR 2,000.
   Consider a hybrid: Trade Republic for ETF core, DEGIRO for broader universe.

3. **yfinance has real data quality problems.** Dividend data corruption (sums dividends +
   capital gains), missing European ticker data, stock split double-adjustments, and a March
   2025 paywall scare. Must use `repair=True`, cross-validate against other sources, and pin
   the yfinance version. For real capital deployment, paid data (EOD Historical Data) is worth
   the cost.

4. **Backtrader is dead, not "Active" as stated in existing docs.** No releases since ~2019,
   Python 3.10+ issues. VectorBT open source is in maintenance mode (bug fixes only).
   NautilusTrader is the new production-grade standard (free, Rust core). Update the framework
   comparison table in `research-etf-backtesting.md`.

5. **MiCA has low direct impact on M3.** Both Bitvavo and Kraken are MiCA-compliant. The
   Netherlands had an early compliance deadline (June 2025). Main practical change: from
   January 2026 crypto providers report to Belastingdienst automatically. No new trading
   restrictions for retail spot crypto.

6. **DEGIRO expanded Core Selection in October 2025** to ~1,500 ETFs on Tradegate (was ~100).
   Fee is now EUR 1 per first trade per ETF per month. This is a positive change that reduces
   the risk of the strategy's ETFs being removed from the selection.

## Open questions

- Should the project switch primary broker from DEGIRO to Trade Republic for the ETF core?
  Need to verify that CSPX, SWDA, and AGGH are all available on Trade Republic NL.
- The existing `research-etf-backtesting.md` framework table needs updating (Backtrader
  status, add NautilusTrader, add PRO distinction for vectorbt).
- Should paid data be budgeted now, or only after paper trading validates the strategy?
