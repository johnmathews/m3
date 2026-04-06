# AI Agents and Scheduled Autonomous AI for Trading & Financial Analysis

**Research date:** 2026-04-06
**Focus:** Practical, current (2025-2026) implementations for retail traders with small accounts

---

## 1. AI Agent Frameworks for Trading

### Major Frameworks (2025-2026)

**TradingAgents** (UCLA/MIT, open-source) is the most relevant framework specifically built for trading. Architecture mimics a professional trading firm:
- 4 specialized analysts (fundamental, sentiment, news, technical) run concurrently
- Bull/bear researcher agents debate opportunities (dialectical review)
- Trader agents synthesize insights and execute
- Risk management team monitors exposure
- Fund manager provides final approval

Backtested performance (June-Nov 2024): AAPL +26.62% vs buy-and-hold -5.23%, GOOGL +24.36% vs +7.78%, AMZN +23.21% vs +17.10%. Sharpe ratios of 5.6-8.2. Version 0.2.3 (March 2026) supports GPT-5.x, Gemini 3.x, Claude 4.x, Grok 4.x.

Source: [TradingAgents](https://tradingagents-ai.github.io/) | [GitHub](https://github.com/TauricResearch/TradingAgents)

**General-purpose frameworks applied to trading:**

| Framework | Stars | Strengths | Trading Fit |
|-----------|-------|-----------|-------------|
| LangChain/LangGraph | 75k+ | Most token-efficient, Swiss Army knife for custom pipelines | Best for building custom analysis chains |
| CrewAI | 280% growth in 2025 | Role-based multi-agent orchestration | Good for analyst team setups, but 3x token overhead vs LangChain |
| AutoGPT | 167k+ | Long-running autonomous tasks, minimal human intervention | Overkill for structured trading tasks |
| Microsoft AutoGen | Enterprise-grade | Human-in-the-loop, reliable | Good for compliance-heavy setups |
| n8n | Low-code | Visual workflows, cron scheduling, 800+ integrations | **Best for retail traders** — no-code scheduled analysis |

Sources: [o-mega framework comparison](https://o-mega.ai/articles/langgraph-vs-crewai-vs-autogen-top-10-agent-frameworks-2026) | [Alphamatch frameworks](https://www.alphamatch.ai/blog/top-agentic-ai-frameworks-2026)

**Other trading-specific projects:**
- **FinMem** — Layered memory + profiling for stock trading; won 2024 IJCAI FinLLM challenge
- **StockAgent** — Multi-agent system simulating investor behavior
- **MarketSenseAI 2.0** — RAG-powered stock analysis (see Section 5 for results)
- **FinGPT** — Open-source financial LLM; strong at sentiment (F1: 87.6%) but weak at stock prediction (accuracy: 45-53%)

Source: [FlowHunt LLM bot comparison](https://www.flowhunt.io/blog/llm-trading-bots-comparison/)

### Verdict for M3

For a small retail account, the heavyweight multi-agent frameworks (TradingAgents, CrewAI) are interesting research but overkill for a 2,000 EUR portfolio. **n8n + a scheduled LLM call** is the pragmatic choice for automating research workflows without excessive complexity or cost.

---

## 2. Scheduled AI Analysis Workflows

### How People Are Setting Up Recurring AI Analysis

**n8n (most popular for retail):**
Pre-built workflow templates exist for exactly this use case:
- "Automate stock trades with AI-driven technical analysis & Alpaca Trading" — scheduled cron trigger, fetches market data, runs LLM analysis, outputs to Google Sheets or Telegram
- "Automated multi-agent trading analysis with GPT-5, Telegram, Coinbase & Notion" — multi-agent architecture with risk management
- Architecture: Trigger (cron/webhook) -> Data fetch (API nodes) -> LLM analysis (AI Agent node) -> Output (Telegram/Sheets/Notion)

Source: [n8n AI Agent integrations](https://n8n.io/integrations/agent/) | [n8n Alpaca template](https://n8n.io/workflows/7240-automate-stock-trades-with-ai-driven-technical-analysis-and-alpaca-trading/)

**Claude Code Scheduled Tasks (native option):**
Three scheduling tiers available as of 2026:

| Method | Runs On | Persistent | Min Interval |
|--------|---------|-----------|--------------|
| Cloud tasks (`/schedule`) | Anthropic cloud | Yes | 1 hour |
| Desktop tasks | Local machine | Yes | 1 minute |
| `/loop` (session-scoped) | Local machine | No (dies with session) | 1 minute |

Cloud tasks can run unattended without your machine on. Desktop tasks persist across restarts and have access to local files/MCP servers. Standard 5-field cron expressions supported.

Source: [Claude Code scheduled tasks docs](https://code.claude.com/docs/en/scheduled-tasks)

**GitHub Actions (free tier, durable):**
`schedule` trigger with cron syntax. Good for: daily pre-market analysis, weekly strategy review, monthly rebalance signal. Free for public repos, 2000 min/month for private repos.

Source: [Claude Code GitHub Actions guide](https://smartscope.blog/en/generative-ai/claude/claude-code-scheduled-automation-guide/)

### Practical Workflow Examples

**Daily pre-market briefing:**
1. Cron fires at 07:00 CET (before European open)
2. Fetch overnight US close, Asian session, futures, VIX
3. LLM summarizes: "Regime status, key levels, news catalysts, position review"
4. Output to Telegram/email

**Weekly strategy review:**
1. Saturday morning cron
2. Fetch weekly returns, sector rotation data, momentum scores
3. LLM compares current signals vs strategy rules
4. Generates rebalance recommendation if threshold exceeded

**Monthly ETF rebalance signal (directly relevant to M3 core):**
1. First trading day of month
2. Fetch 12-month total returns for SXR8, EUNL, EUNA and risk-free rate
3. LLM applies dual momentum logic, checks for look-ahead bias
4. Outputs: hold/switch signal with reasoning

---

## 3. Claude API / Anthropic for Financial Analysis

### Anthropic's Official Push

Anthropic launched **Claude for Financial Services** in July 2025, with partnerships with Deloitte and PwC. Features include compliance automation, audit trails, and institutional support.

Claude 4 models outperform other frontier models on Vals AI's Finance Agent benchmark. Specific strengths:
- Monte Carlo simulations and risk modeling
- SEC filing analysis and earnings call interpretation
- Code generation for backtesting (pandas, NumPy, vectorbt, backtrader)
- Structured report generation with low hallucination rates

Source: [Anthropic Financial Services](https://www.anthropic.com/news/claude-for-financial-services) | [Claude for trading guide](https://blog.pickmytrade.trade/claude-4-1-for-trading-guide/)

### Practical Claude Trading Use Cases

From the PickMyTrade guide:
- **Backtesting code generation**: "Write Python to backtest a daily MA crossover on SPY from 2010-2024 with 10 bps costs and walk-forward validation"
- **Risk modeling**: Monte Carlo simulations, stress tests
- **Sentiment analysis**: Process news feeds for bullish/bearish signals
- **Workflow automation**: Connect to data providers via API

**Critical limitations:**
- Hallucination risk: Can fabricate prices or metrics — always cross-check
- Overfitting vulnerability: Must use walk-forward validation
- Not for direct execution: Human approval required
- Data privacy: Don't paste broker credentials

Source: [Claude 4.1 trading guide](https://blog.pickmytrade.trade/claude-4-1-for-trading-guide/) | [Thoughtworks analysis](https://www.thoughtworks.com/en-us/insights/blog/generative-ai/claude-financial-services-what-need-know)

### Alpha Arena Competition Results (Real Money)

Six frontier LLMs each given $10,000 real capital for crypto trading:

| Model | Return | Final Balance |
|-------|--------|---------------|
| Qwen | +22.88% | $12,288 |
| DeepSeek V3.1 | +4.76% | $10,476 |
| Claude Sonnet 4.5 | -32.6% | $6,740 |
| Grok 4 | -47.7% | $5,226 |
| Gemini 2.5 Pro | >-50% | <$5,000 |
| GPT-5 | >-50% | <$5,000 |

**4 out of 6 models failed to beat simple buy-and-hold Bitcoin.** Even the winners experienced dramatic swings (DeepSeek peaked at +130% before crashing). This is the most honest real-money test available.

Source: [Alpha Arena competition](https://www.euclideanai.com/blog/llm-crypto-trading)

---

## 4. LLM-Powered Monitoring and Alerting

### Fed Language / Central Bank Monitoring

An IMF working paper (2025) built a full NLP pipeline using GPT-4o to score Federal Reserve Monetary Policy Reports on a -2 (dovish) to +2 (hawkish) scale. Covered 26 reports from 2013-2025. Uses LangChain + FAISS for retrieval, semantic chunking on natural boundaries.

Source: [IMF Working Paper](https://www.imf.org/-/media/files/publications/wp/2025/english/wpiea2025109-print-pdf.pdf) | [MDPI Fed analysis](https://www.mdpi.com/2227-7390/13/20/3255)

### Sentiment-Augmented Trading Signals

Research demonstrates practical signal generation:
- **SAPPO framework**: Sentiment-augmented PPO increases Sharpe ratio from 1.55 to 1.90 by incorporating real-time news sentiment into reinforcement learning allocation
- **MarketSenseAI**: News Agent runs daily article aggregation and summarization, feeding into signal generation

Source: [ACL Anthology SAPPO](https://aclanthology.org/2025.realm-1.12/) | [Frontiers LLM equity survey](https://www.frontiersin.org/journals/artificial-intelligence/articles/10.3389/frai.2025.1608365/full)

### Anomaly and Regime Detection

Active research areas in 2025-2026:
- Park (2024): Multi-agent framework for automated anomaly detection in financial markets
- Koa et al. (2024): "Temporal Relational Reasoning" using LLMs to detect portfolio crashes via human-like temporal reasoning
- BIS Working Paper 1291: Central banks using LLMs to monitor potential market stress drivers

Source: [BIS Working Paper](https://www.bis.org/publ/work1291.pdf) | [Frontiers survey](https://www.frontiersin.org/journals/artificial-intelligence/articles/10.3389/frai.2025.1608365/full)

### Practical Alert System for M3

A realistic monitoring setup for a small account:
1. **Daily**: LLM scans news for BTC/ETH regime signals (exchange flows, whale movements, regulatory news)
2. **Weekly**: Summarize ETF momentum status, flag any cross-under/cross-over events
3. **Event-driven**: Fed meeting days, ECB decisions, major macro releases — LLM scores hawkish/dovish shift
4. **Anomaly**: Volume spikes, correlation breakdowns, VIX regime changes

Cost estimate: 1-2 LLM calls/day with Haiku = pennies/day (see Section 7).

---

## 5. Practical Retail Implementations

### Documented Case: 3-Month AI Trading Agent (Real Results)

Laurentiu Raducu built and documented an AI trading agent over 3 months (June-December 2025):

**Architecture:**
- Perplexity API for web scanning/stock discovery
- QuantiQ.live for financial metrics
- GPT-4o for investment analysis
- Alpaca API for trade execution
- Also: Congress trade tracking, Reddit sentiment, Google Trends, FRED macro data

**Results (3 months, small/mid-cap US stocks):**

| Stock | Return |
|-------|--------|
| RKLB | +110% |
| EBMT | +14.8% |
| GIL | +11.9% |
| IONS | +9.4% |
| TSBK | +5.4% |
| OVLY | +5.3% |
| RGCO | +0.9% |
| ADNT | -14.5% |
| BBWI | -23.1% |

**What worked:**
- Web-based discovery via Perplexity caught emerging trends (data centers, policy shifts)
- Multi-factor analysis (financial + sentiment + technical + macro) improved decisions
- Hedging with inverse ETFs during geopolitical shocks
- Alternative data (Congress trades, vessel tracking) outperformed raw technical indicators

**What didn't work:**
- Context overload caused GPT hallucinations
- News signals weren't truly real-time
- Small-cap illiquidity problems
- Early portfolios lacked diversification

Launched as SaaS at $15/month. Source: [Medium article](https://laurentiu-raducu.medium.com/i-created-an-ai-trading-agent-heres-what-it-did-after-one-month-3d6c54c68445)

### MarketSenseAI 2.0 (Academic, Backtested)

The most rigorous backtested LLM trading system published:

**S&P 100 (2023-2024):** 125.9% cumulative return vs 73.5% index. Sharpe 2.76. Win rate 77%. Alpha 8-10.6%.
**S&P 500 (2024):** 25.8% equally-weighted vs 12.8% benchmark. Alpha 17.6-18.9%.

Architecture: 5 LLM agents (news, fundamentals, dynamics, macro, signal) using GPT-4o + Pinecone vector DB + RAG pipeline processing SEC filings, earnings calls, and institutional macro reports.

**Cost to replicate:** GPT-4o API, Pinecone subscription, SEC EDGAR API (free), RapidAPI for earnings transcripts. Non-trivial engineering effort.

Source: [MarketSenseAI 2.0 paper](https://arxiv.org/abs/2502.00415)

### AI Agents on Prediction Markets (Polymarket)

Polystrat (Olas protocol) launched February 2026:
- 4,200+ trades in first month
- Up to 376% returns on individual trades
- 59-64% win rate in tech-specific markets
- 37% of Polystrat agents reported positive P&L
- 30%+ of Polymarket wallets now use AI agents

Source: [CoinDesk](https://www.coindesk.com/tech/2026/03/15/ai-agents-are-quietly-rewriting-prediction-market-trading)

### Critical Counter-Evidence

A rigorous study extending LLM trading evaluations from 6-month windows to 20 years (2004-2024) found:
- **LLM strategies (FinMem, FinAgent) lost their edge entirely over 20 years**
- In bull markets: LLMs were excessively conservative, missing gains
- In bear markets: LLMs were too aggressive, suffering disproportionate losses
- Traditional buy-and-hold consistently outperformed
- Previous positive results suffered from survivorship bias, look-ahead bias, and data-snooping bias

**This is the most important finding in the entire research.** Short-term backtests are deeply misleading.

Source: [arXiv: LLM investing long run](https://arxiv.org/html/2505.07078v1)

---

## 6. Edge Cases for Small Accounts

### Where Small Accounts Might Have an Advantage

1. **Niche market analysis / information synthesis**: LLMs can process information faster than a solo retail trader can manually. The edge isn't in the model's "predictions" but in the speed and breadth of information processing for research.

2. **Micro-cap / small-cap research**: The Raducu agent (Section 5) specifically targeted small/mid-caps where analyst coverage is thin. LLMs can scan SEC filings, Reddit, and news for companies that institutions ignore. But: illiquidity is a real problem even at small account sizes.

3. **Crypto narrative tracking**: LLMs excel at monitoring social sentiment across Reddit, Twitter/X, Telegram. Grok integrates directly with X for real-time crypto sentiment. Useful for the M3 satellite strategy (BTC/ETH trend-following).

4. **Prediction markets**: Polymarket AI agents operate with small capital. 30%+ of wallets use AI agents. This is a genuinely new arena where retail can compete, though fees and spreads erode returns.

### Where Small Accounts Are Disadvantaged

1. **Execution speed**: Institutional bots execute in 1-2ms; retail in 100x+ longer. By the time a retail bot reacts, the opportunity is gone.
2. **Fixed costs**: API subscriptions, data feeds, and trading fees consume a larger percentage of small balances.
3. **Market saturation**: Institutional algorithms handle ~70% of trading volume; most retail advantages are already arbitraged away.
4. **Bot maintenance**: "A bot left alone for 48 hours in the current high-volatility environment is almost guaranteed to hit its Stop Loss."

Source: [CoinCub bot assessment](https://coincub.com/blog/are-crypto-trading-bots-worth-it/) | [BingX LLM guide](https://bingx.com/en/learn/article/how-to-use-llms-for-crypto-trading-research)

### Honest Assessment for M3

The LLM advantage for a 2,000 EUR account is **not in autonomous trading**. It is in:
- **Research automation**: Daily briefings, earnings analysis, macro summaries at near-zero marginal cost
- **Code generation**: Backtesting frameworks, data pipelines, strategy logic
- **Discipline enforcement**: Systematic checklists, avoiding emotional decisions
- **Monitoring**: Alerts for regime changes, momentum crossovers, news events

These are "decision support" uses, not "autonomous alpha generation."

---

## 7. Cost-Benefit Analysis

### LLM API Costs for Trading Analysis

**Current pricing (April 2026):**

| Model | Input/1M tokens | Output/1M tokens | Best For |
|-------|-----------------|-------------------|----------|
| Claude Opus 4.6 | $5.00 | $25.00 | Deep strategic analysis |
| Claude Sonnet 4.5 | $3.00 | $15.00 | Balanced analysis |
| Claude Haiku 4.5 | $1.00 | $5.00 | Daily monitoring, classification |
| DeepSeek V3 | $0.14 | $0.28 | High-volume sentiment scanning |
| Phi-4 Mini Flash | $0.03 | $0.06 | Real-time classification |

**Cost optimization:**
- Batch API: 50% discount (non-urgent, 24-hour processing)
- Prompt caching: 90% savings on repeated context (5-min TTL)
- Combined: Up to 95% reduction on eligible workloads

Source: [Claude API pricing](https://costgoat.com/pricing/claude-api) | [LLM pricing comparison](https://costgoat.com/compare/llm-api)

### Tiered Architecture for Cost Control

The "6-tier" approach from RocketEdge matches task complexity to model cost:

| Task | Recommended Tier | Cost |
|------|-----------------|------|
| Monthly strategic deep-dive | Opus 4.6 | $5/$25 per 1M tokens |
| Weekly backtesting/research | DeepSeek R1 | $0.55/$2.19 per 1M tokens |
| Daily quantitative calculations | Phi-4 Reasoning | $0.07/$0.14 per 1M tokens |
| Daily sentiment parsing | Qwen 2.5 or DeepSeek V3 | $0.12-0.14/$0.28-0.39 per 1M tokens |
| Real-time classification | Phi-4 Mini Flash | $0.03/$0.06 per 1M tokens |

Source: [RocketEdge 6-tier fix](https://rocketedge.com/2026/03/15/your-ai-agent-bill-is-30x-higher-than-it-needs-to-be-the-6-tier-fix/)

### Realistic Monthly Cost Estimate for M3

**Minimal viable setup (research copilot only):**

| Activity | Frequency | Model | Estimated Tokens | Monthly Cost |
|----------|-----------|-------|-----------------|--------------|
| Daily market briefing | 22 trading days | Haiku 4.5 | ~50K tokens/day | ~$5.50 |
| Weekly strategy review | 4/month | Sonnet 4.5 | ~100K tokens/week | ~$6.40 |
| Monthly rebalance analysis | 1/month | Sonnet 4.5 | ~150K tokens | ~$2.70 |
| Ad-hoc deep research | 2-3/month | Sonnet 4.5 | ~200K tokens | ~$3.60 |
| **Total** | | | | **~$18/month** |

**With DeepSeek for daily tasks:**

| Activity | Model | Monthly Cost |
|----------|-------|--------------|
| Daily briefing | DeepSeek V3 | ~$0.60 |
| Weekly review | Claude Sonnet | ~$6.40 |
| Monthly rebalance | Claude Sonnet | ~$2.70 |
| Ad-hoc research | Claude Sonnet | ~$3.60 |
| **Total** | | **~$13/month** |

**With Claude subscription instead of API:**
- Claude Pro: $20/month (generous usage limits, no token counting)
- Claude Max: $100/month (5x Pro usage)

For a casual research setup, **Claude Pro at $20/month is likely the sweet spot** — simpler than API management, includes web search, artifacts, and projects features.

### Is It Worth It for a 2,000 EUR Account?

**The math:**
- Annual LLM cost: ~$150-240/year ($13-20/month)
- That's 7.5-12% of a 2,000 EUR portfolio
- To break even on LLM costs alone, the AI-assisted strategy would need to generate 7.5-12% more returns than a manual approach
- **At this account size, the LLM cost is a significant drag on performance**

**The honest answer:** At 2,000 EUR, the primary value of LLM tools is **education and skill development**, not direct alpha generation. The cost is justified if:
1. You're building skills and systems that scale as the account grows
2. The analysis time saved lets you focus on strategy refinement
3. You'd be paying for market data/research subscriptions anyway (~$10-30/month)
4. The automated monitoring catches something you'd otherwise miss

**The LLM should NOT be making trading decisions autonomously** for this account. The Alpha Arena results (4/6 models lost money on crypto) and the long-run study (LLMs fail to outperform over 20 years) make this clear.

### Data Feed Costs (Additive)

| Source | Cost | Coverage |
|--------|------|----------|
| yfinance | Free | ETFs, stocks (delayed, quality issues) |
| Alpha Vantage | Free tier / $50/mo premium | Stocks, sentiment, earnings transcripts |
| EODHD | Free tier / $20/mo | Global markets, fundamentals |
| Finnhub | Free tier | Real-time stocks, news, sentiment |
| CCXT (exchange APIs) | Free | Crypto via Bitvavo/Kraken directly |

Source: [Alpha Vantage](https://www.alphavantage.co/best_stock_market_api_review/) | [EODHD](https://eodhd.com/)

---

## NanoClaw Implementation Plan for M3

NanoClaw is a self-hosted AI assistant that runs Claude agents in isolated containers with a built-in scheduler. Each
scheduled task gets full agent capabilities: Bash, WebSearch, WebFetch, browser automation (Chromium), and file I/O.
Tasks can send results via WhatsApp/Telegram. This makes it ideal for the monitoring and alerting workflows below.

### Phase 1: Research augmentation (start immediately, no automation)

Use Claude Code interactively. The 1M token context window (Opus 4.6) can hold entire research papers + codebase +
historical data in a single session.

| Task | How | Frequency |
|------|-----|-----------|
| Read and critique academic papers | Claude Code + WebFetch | As needed |
| Backtest code generation | Claude Code writes vectorbt/bt scripts | As needed |
| Parameter sensitivity analysis | Claude Code generates sweep code | Per strategy |
| Risk scenario modeling | Claude Code + Monte Carlo scripts | Per strategy |

### Phase 2: Automated monitoring via NanoClaw (after backtesting framework is built)

Schedule recurring NanoClaw tasks for market monitoring. These tasks don't trade — they inform manual rebalancing.

**ETF Core — Monthly rebalance assistant** (cron: `0 18 L * *` — last day of month, 6pm):

```
Prompt: "Calculate 12-month total returns for SXR8 (S&P 500) and EUNL (MSCI World) using
Yahoo Finance data. Check if the best performer's return is positive (absolute momentum filter).
Compare against an ensemble of 6, 9, and 12-month lookbacks. Check if the 10-month SMA is
breached. Summarize: (1) current signal, (2) whether signal changed from last month, (3) any
divergence between lookback periods, (4) recommended action. Save results to the working
directory and send summary to the group."
```

**Macro regime monitor** (cron: `0 7 * * 1` — every Monday 7am):

```
Prompt: "Search for this week's key macro events (Fed/ECB decisions, CPI releases, employment
data). Analyze recent financial news headlines for regime signals (risk-on/risk-off, hawkish/
dovish shifts). Check the VIX level and credit spreads. Flag if any indicators suggest the
current trend regime may be changing. Send a brief summary to the group."
```

**Crypto sentiment scanner** (cron: `0 8 * * *` — daily 8am):

```
Prompt: "Search for Bitcoin and Ethereum news and social media sentiment from the last 24
hours. Identify: (1) dominant narrative themes, (2) any emerging narratives not yet in
mainstream coverage, (3) unusual on-chain activity mentioned in crypto news, (4) overall
sentiment direction (bullish/bearish/neutral). Compare against the current trend-following
signal. Flag any major divergences. Send summary to the group."
```

**Weekly strategy health check** (cron: `0 9 * * 6` — Saturday 9am):

```
Prompt: "Review the current M3 portfolio state. For the ETF core: check if the monthly signal
is still valid, calculate current drawdown from peak, check if any lookback periods are
diverging. For the crypto satellite: check if the weekly trend signal is still valid, calculate
performance vs BTC buy-and-hold. Flag any anomalies. Send summary to the group."
```

Estimated API cost: ~$3-8/month using Haiku for daily tasks and Sonnet for weekly tasks.

### Phase 3: Sentiment-augmented signals (after paper trading validates base strategies)

Add an LLM sentiment overlay to the mechanical trend-following signals:

**For the ETF core** (before monthly rebalance):
- Fetch and analyze the most recent Fed/ECB meeting minutes
- Scan financial news for top holdings of the current ETF
- Check bond market stress indicators (yield curve, credit spreads)
- Generate a confidence score to modulate position sizing (not override the signal)

**For the crypto satellite** (before weekly trades):
- Analyze crypto Twitter/X sentiment for BTC and ETH
- Identify emerging narratives (protocol launches, regulatory news, whale activity)
- Check correlation regime (BTC correlated with equities or decoupled?)
- "Trend signal + positive sentiment" = full position; "mixed/negative" = reduced position

### Phase 4: Narrative-driven crypto alpha (experimental)

Crypto markets are uniquely narrative-driven. An LLM + NanoClaw system can potentially identify narratives before they
manifest in price:

1. **Daily narrative scan:** NanoClaw task scans crypto Twitter/X, Reddit, key Telegram channels for emerging themes
2. **Narrative classification:** Strength (how many sources), novelty (new or recycled), historical analogy, time horizon
3. **Signal generation:** Strong novel narrative aligned with trend = increase position; strong negative = reduce/exit

This is speculative and should only be attempted with a small fraction of the satellite allocation after paper trading.

---

## Summary: What's Practical for M3

### Recommended Approach

1. **Use Claude Max as a research copilot**, not an autonomous trader
2. **Set up scheduled monitoring via NanoClaw:**
   - Daily: Crypto sentiment scan (Haiku, ~$0.25/day)
   - Weekly: Macro regime monitor + strategy health check (Sonnet, ~$1.50/week)
   - Monthly: Full rebalance signal for core ETF strategy (Sonnet, ~$2.70/month)
3. **Use LLM for code generation:** Backtesting frameworks, data pipelines, monitoring scripts
4. **Do NOT let the LLM execute trades autonomously.** The evidence strongly suggests this loses money in the long run.
5. **Keep incremental API costs under $15/month** — Claude Max is a sunk cost (paid regardless of M3)

### What the Evidence Actually Supports

| Use Case | Evidence Level | Verdict |
|----------|---------------|---------|
| Autonomous LLM trading | Strong negative (20-year study, Alpha Arena) | Do not do this |
| Multi-agent research systems | Promising backtests, no long-run validation | Interesting for learning, not for live capital |
| Sentiment analysis | Academically validated, marginal edge | Useful as one input, not a standalone strategy |
| Research acceleration | Universally positive | **Primary use case for retail** |
| Code/backtest generation | Universally positive | **Primary use case for retail** |
| Scheduled monitoring/alerts | Practical and cheap | **Worth implementing for M3** |
| Fed/ECB language monitoring | Academically validated | Useful for macro regime awareness |

### Key Risks

1. **Hallucination**: LLMs fabricate prices, metrics, and data. Always verify against primary sources.
2. **Overfitting**: Short backtests are deeply misleading. The 20-year study demolished previously-reported LLM advantages.
3. **Cost drag**: At 2,000 EUR, every euro spent on tools is a euro not compounding.
4. **Complexity trap**: Building a multi-agent trading system is interesting engineering but not a trading edge.
5. **Latency**: LLM inference is too slow for anything time-sensitive. Institutional algos will front-run you.
