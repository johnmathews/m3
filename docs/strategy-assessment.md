# Strategy Assessment — Prioritized Techniques

Reviewed April 2026 after completing the research phase. Ranks all evaluated strategies by
conviction level and identifies what to build first.

## Tier 1: High Conviction

### ETF Dual Momentum (Core, 70%)

The core allocation. Academically validated momentum premium with dual (relative + absolute)
filters. Post-publication decay is real (5-9% CAGR vs historical 17%), but the absolute momentum
filter provides genuine crash protection.

**Key refinements identified:**

1. **Ensemble lookback (6-12 months):** Newfound Research (2019) showed a 21.5pp return difference
   from a single month change in lookback window. Ensembling across 6-12 month lookbacks is the
   single highest-value refinement to reduce specification fragility.
2. **Trade Republic over DEGIRO for the core:** Fractional shares + 2% cash interest solves
   DEGIRO's 5-15% cash drag problem. On a EUR 1,400 core, cash drag of EUR 70-210 sitting idle
   matters more than the lookback window choice.
3. **Tradegate tickers only:** SXR8, EUNL, EUNA. LSE tickers (CSPX, SWDA, AGGH) route to
   expensive venues on DEGIRO.

**Expected performance:** 5-9% CAGR, 20-35% max drawdown, 1-3 trades/year.

### BTC Trend-Following (Satellite, 30%)

Zarattini et al. (2025) provides the strongest quantitative evidence in the entire research set:
ensemble trend model on BTC achieved 30% CAGR, 1.58 Sharpe, 19% max drawdown.

**Key decisions:**

1. **BTC only, drop ETH.** At EUR 600, splitting between two assets creates position sizes where
   fees eat the edge.
2. **Weekly rebalance, maker-only on Bitvavo (0.15%).** The fee constraint forcing weekly
   rebalancing is actually a feature — prevents overtrading.
3. **Simple moving average filter.** 20-day SMA is evidence-backed. Ensemble of 5-30 day lookbacks
   is optimal but weekly check frequency makes the longer end more practical.

**Expected performance:** 20-50%+ but with 50%+ drawdowns. Edge vs buy-and-hold is unproven.

## Tier 2: Promising But Secondary

### Narrative-Contrarian Signal (LLM-Assisted Research)

CoinGecko data shows massive divergence between narrative popularity and profitability: AI tokens
were most discussed but returned -50.2%; RWA was least discussed but returned +185.8%. This is the
only LLM application where there is a differentiated information asymmetry worth tracking.

Not a strategy yet — track as a weekly "attention vs. performance divergence" report using Claude.

### Scheduled LLM Monitoring

Monthly rebalance signal calculation, macro regime context, crypto sentiment scans. The value is
discipline enforcement (preventing discretionary intervention), not alpha generation.

## Tier 3: Correctly Rejected

| Strategy | Reason |
| --- | --- |
| Autonomous LLM trading | 4/6 frontier models lost money in Alpha Arena; "Profit Mirage" paper shows 51-62% Sharpe decay on post-training data |
| Mean reversion on crypto | RSI-based strategies are "basically worthless" on BTC (3 trades over 6 years) |
| Risk parity | Requires 4-5 positions, impractical at EUR 2k; failed in 2022 when bonds fell with equities |
| Multi-factor ETFs | No crisis protection from absolute momentum filter |
| Managed futures UCITS | 0.75% TER too expensive vs 0.07-0.20% core ETFs |
| Funding rate arbitrage | Requires perpetual futures, higher capital, edge compressing |

## Implementation Priority

1. ETF core backtest using `bt` for monthly logic, validate in NautilusTrader
2. Finalize broker: Trade Republic for core, DEGIRO as backup for broader universe
3. BTC satellite: 20-day SMA filter, weekly check, maker-only on Bitvavo — paper trade 3+ months
4. Build monitoring dashboard (Grafana) before trading system — forces correct data pipeline
5. LLM monitoring as scheduled tasks once backtesting framework exists

## Core Insight

The real edge at EUR 2k is the system (data pipeline, monitoring, disciplined execution, cost
control) that scales as the account grows. Returns follow account size — the infrastructure and
skill-building is the primary investment.
