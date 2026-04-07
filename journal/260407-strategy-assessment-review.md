# Strategy Assessment and Prioritization Review

**Date:** 2026-04-07

## What happened

Conducted a comprehensive review of all research documents to produce a prioritized strategy
assessment. The research phase is complete — this session synthesized findings into actionable
implementation priorities.

## Key conclusions

### Tier 1 (high conviction, build these)

1. **ETF dual momentum with ensemble lookback (6-12mo):** The 21.5pp sensitivity to a single month
   change in lookback window (Newfound Research, 2019) makes ensembling the highest-value
   refinement. Post-publication decay is real (5-9% CAGR) but the absolute momentum filter still
   provides genuine crash protection.

2. **Trade Republic over DEGIRO for the core:** Fractional shares + 2% cash interest solves the
   5-15% cash drag problem. At EUR 1,400, broker choice matters more than lookback window tuning.

3. **BTC-only satellite (drop ETH):** At EUR 600, splitting two assets creates position sizes where
   fees eat the edge. Zarattini et al. (2025) — 30% CAGR, 1.58 Sharpe, 19% max DD — is the
   strongest quantitative evidence in the research set, and it's for BTC specifically.

### Tier 2 (promising, secondary)

4. **Narrative-contrarian signal:** CoinGecko data showing AI tokens most discussed (-50.2%) vs RWA
   least discussed (+185.8%) is an unexploited information asymmetry. Track as a weekly LLM-assisted
   report, not a live strategy yet.

5. **Scheduled LLM monitoring:** Monthly signal calculation, macro context, sentiment scans. Value
   is discipline enforcement, not alpha.

### Correctly rejected

Autonomous LLM trading, mean reversion on crypto, risk parity, multi-factor ETFs, managed futures
UCITS, and funding rate arbitrage — all rejected for well-documented reasons.

## Implementation order

1. ETF core backtest using `bt` for monthly logic, validate in NautilusTrader
2. Finalize broker (Trade Republic for core, DEGIRO as backup)
3. BTC satellite: 20-day SMA, weekly, maker-only Bitvavo — paper trade 3+ months
4. Monitoring dashboard (Grafana) before trading system
5. LLM monitoring tasks once backtesting framework exists

## Core insight

At EUR 2k, the real edge is the system (pipeline, monitoring, execution discipline, cost control)
that scales with account growth. Returns follow account size.

## Artifacts created

- `docs/strategy-assessment.md` — full prioritized strategy document
- Updated `.gitignore` with `*.pem` and `vault_password` patterns
