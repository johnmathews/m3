# 260406 - LLM Alpha Generation Research

## What was done

Conducted comprehensive web research on how LLMs are being used to discover and generate trading alpha, covering 8 areas: sentiment analysis, fundamental analysis, agent frameworks, alternative data, regime detection, academic research (2024-2026), risks/limitations, and practical tools.

## Key decisions and findings

### The most important finding: data contamination undermines most published results

The "Profit Mirage" paper (2025) is the single most important result. It shows that LLM trading agents' backtested returns collapse on post-training data:
- Sharpe Ratio decays 51-62%
- Total Return decays 50-72%
- Models memorize S&P 500 closing prices with <1% error within training window

The FINSABER benchmark (20 years, 100+ symbols) shows LLM strategies do not outperform buy-and-hold long-term. They are too conservative in bull markets and too aggressive in bear markets.

### What genuinely works (with caveats)

1. **GPT-4 for earnings direction prediction** outperforms human analysts (60.35% vs 52.71%). This is robust because they tested on out-of-sample data outside GPT's training window.
2. **Alpha-GPT for alpha factor mining** ranked top-10 out of 41,000 teams in a real competition. This is genuine because it was evaluated on live, forward-looking data.
3. **LLM sentiment analysis** outperforms traditional NLP (bag-of-words, dictionaries) for financial text classification.

### What is mostly hype (for now)

1. Multi-agent trading systems claiming 20%+ excess returns (tested over 3 months on 3 stocks)
2. Autonomous LLM trading agents (StockBench shows most fail to beat buy-and-hold)
3. Any backtest using data within the model's training window

### Practical implications for M3

- Use LLMs as **research tools**, not trading agents
- Sentiment analysis could serve as a **secondary confirmation signal** for monthly ETF rebalancing ($5-20/month API cost)
- **Never trust LLM backtests on historical data** without verification against post-training-cutoff data
- Multi-agent frameworks are over-engineered for a 2k EUR account

## Research artifacts

- Full report: `research/research-llm-alpha-generation.md`
- Contains 40+ sources with links to papers, frameworks, and tools
