# M3 — Money Making Machine

A systematic trading project: research, backtest, deploy, and learn.

## Context & Motivation

John wants to explore systematic (algorithmic) trading as a long-term project. The goals are:

1. **Learn quantitative finance** — strategy design, backtesting methodology, risk management, market microstructure.
2. **Build real infrastructure** — a durable, maintainable system that can grow over time.
3. **Generate profit** — modest and realistic expectations, starting small and scaling only what's proven.

The project uses NanoClaw and Claude Code as development and research assistants — for strategy ideation, code
generation, data analysis, and documentation.

## Constraints

| Constraint           | Detail                                                                                              |
| -------------------- | --------------------------------------------------------------------------------------------------- |
| **Starting capital** | €2,000 maximum                                                                                      |
| **Acceptable risk**  | To be defined — but capital preservation matters at this scale                                      |
| **Time commitment**  | Part-time / hobby project alongside a day job                                                       |
| **Infrastructure**   | Self-hosted on John's home server (TrueNAS, LXC containers, Docker)                                 |
| **Broker fees**      | Must be factored into every strategy — fees destroy small-account edges                             |
| **Data costs**       | Willing to pay for subscriptions, but prefer free sources initially                                 |
| **Regulatory**       | Dutch tax law — Box 3 (vermogensbelasting) for holdings, income tax if classified as active trading |

## Background

### The small-account problem

With €2,000, transaction costs dominate. A €3 commission on a €200 position is 1.5% — the strategy needs to clear that
just to break even. This rules out high-frequency approaches and pushes toward:

- Longer holding periods (swing/position trading, weekly/monthly rebalancing)
- Low-fee brokers (DEGIRO, Interactive Brokers)
- Asset classes with zero/low commissions (crypto, commission-free ETFs)

### What edges exist for retail traders?

Professional quants have speed, data, and capital advantages. Retail edges tend to be:

- **Patience** — holding through volatility that institutions can't tolerate
- **Niche markets** — small-cap stocks, altcoins, illiquid instruments that big funds ignore
- **Simplicity** — trend-following and momentum strategies that work but are "too boring" for active managers
- **No benchmark pressure** — no clients demanding quarterly performance vs S&P 500

### Realistic return expectations

| Strategy type           | Annual return (after costs) | Notes                            |
| ----------------------- | --------------------------- | -------------------------------- |
| ETF momentum/rotation   | 10–20%                      | Well-documented, low maintenance |
| Stock factor strategies | 10–25%                      | Requires more data and research  |
| Crypto systematic       | 20–50%+                     | Higher risk, higher variance     |
| Combined portfolio      | 15–25%                      | Diversification benefit          |

On €2,000 this translates to €200–500/year in the early phase. The real value is in building the system and skills.

## Choices Discussed

### 1. Asset classes

| Option                  | Pros                                                         | Cons                                                | Verdict         |
| ----------------------- | ------------------------------------------------------------ | --------------------------------------------------- | --------------- |
| **Crypto**              | Zero/low fees, 24/7 markets, free data APIs, high volatility | Exchange risk, brutal drawdowns, messy NL taxes     | ✅ Include      |
| **ETFs (long-only)**    | Proven factors, diversified, simple tax, decades of research | Slow at €2k, limited to market hours, some fees     | ✅ Include      |
| **Individual stocks**   | More opportunity, factor investing                           | Higher fees per trade, more research needed         | ⏳ Later phase  |
| **Forex**               | Very liquid, low spreads                                     | Highly efficient market, hard to find edge          | ❌ Skip for now |
| **Options/derivatives** | Leverage, defined risk                                       | Complex, not beginner-friendly, margin requirements | ❌ Skip for now |

### 2. Portfolio structure

**Decision: Hybrid core-satellite approach**

- **Core (70% — ~€1,400):** Long-only ETF momentum/rotation strategy. Monthly rebalance. Low maintenance, proven, minimal
  fees. The stable foundation.
- **Satellite (30% — ~€600):** Crypto systematic strategy. More active (daily/weekly signals). Higher risk and reward.
  The learning lab.

Rationale:

- The two are largely uncorrelated — diversification benefit
- Different timeframes keep complexity manageable
- If the crypto strategy fails, only 30% of a small account is affected
- Same infrastructure serves both — one backtesting engine, one dashboard, one journal

### 3. Paper trading first

**Decision: Yes — mandatory paper trading phase**

All strategies must pass a minimum 3–6 month paper trading validation before any real capital is deployed. Paper trading
means:

- Running strategies against live market data
- Simulating trades including realistic fees, slippage, and spread
- Tracking P&L, drawdowns, and risk metrics as if real
- No real money at risk

### 4. Data sources

**Decision: Start free, pay later if needed**

| Source                   | Asset class         | Cost                    | Quality                      |
| ------------------------ | ------------------- | ----------------------- | ---------------------------- |
| Yahoo Finance (yfinance) | Stocks, ETFs        | Free                    | Good for daily/weekly        |
| Alpha Vantage            | Stocks, ETFs, Forex | Free tier (25 req/day)  | Decent                       |
| CoinGecko                | Crypto              | Free tier               | Good for daily               |
| Binance API              | Crypto              | Free                    | Excellent for all timeframes |
| DEGIRO/IBKR API          | Stocks, ETFs        | Broker account required | Real-time with account       |

Paid sources to consider later: Polygon.io, Tiingo, Quandl/Nasdaq Data Link.

### 5. Broker selection

**Decision: Deferred until live deployment**

Leading candidates:

- **DEGIRO** — low fees, NL-based, good ETF selection (some commission-free), limited API
- **Interactive Brokers** — professional-grade API, low fees at scale, more complex
- **Binance/Kraken** — for crypto, good APIs, low fees

### 6. Tech stack

**Decision: Python-based, self-hosted**

- **Language:** Python (dominant in quant finance, best library ecosystem)
- **Backtesting:** Backtrader, Zipline, or VectorBT (to be evaluated)
- **Data:** pandas, numpy
- **Dashboards:** Streamlit or Grafana
- **Storage:** SQLite or PostgreSQL for trade logs, parquet files for market data
- **Scheduling:** Cron / NanoClaw scheduled tasks
- **Version control:** Git
- **Documentation:** Markdown files in the project repo

## Decisions Made

| #   | Decision                                                    | Rationale                                      |
| --- | ----------------------------------------------------------- | ---------------------------------------------- |
| 1   | Start with paper trading only                               | Validate before risking real money             |
| 2   | Hybrid portfolio: 70% ETF core, 30% crypto satellite        | Diversification + learning                     |
| 3   | Free data sources first                                     | Keep costs at zero until strategies are proven |
| 4   | Python tech stack                                           | Best ecosystem for quant finance               |
| 5   | Self-hosted on home infrastructure                          | John already has the setup, keeps costs down   |
| 6   | Skip forex, options, derivatives for now                    | Focus on what's accessible and learnable       |
| 7   | All strategies must account for realistic fees and slippage | No fantasy backtests                           |

## Architecture Principles

These guide all technical decisions:

- **Durable** — data and state survive restarts, crashes, and upgrades
- **Maintainable** — clean code, clear separation of concerns, good tests
- **Extendable** — easy to add new strategies, data sources, asset classes
- **Auditable** — every trade decision is logged with reasoning, every backtest is reproducible
- **Discoverable** — well-documented, easy to navigate, clear naming conventions

## Documentation Structure (planned)

```
m3/
├── README.md              ← this file
├── journal/               ← learning journal (what I studied, what I learned)
├── devlog/                ← development journal (what was built, decisions made)
├── dictionary.md          ← glossary of quant/trading terms
├── strategies/            ← strategy definitions and research
├── backtests/             ← backtest results and analysis
├── data/                  ← market data (cached/downloaded)
├── dashboards/            ← dashboard configs
├── src/                   ← source code
│   ├── data/              ← data fetching and processing
│   ├── strategies/        ← strategy implementations
│   ├── backtest/          ← backtesting engine
│   ├── portfolio/         ← portfolio management
│   └── utils/             ← shared utilities
└── docs/                  ← technical documentation
```

## Next Steps

1. **Research phase** — study existing momentum/trend-following strategies for ETFs and crypto
2. **Set up backtesting environment** — choose and configure a backtesting framework
3. **Implement first strategy** — simple ETF momentum rotation as a baseline
4. **Build data pipeline** — fetch and store historical data from free sources
5. **Paper trading infrastructure** — simulate live execution with realistic costs
6. **Dashboard** — visualise portfolio, P&L, and strategy signals
