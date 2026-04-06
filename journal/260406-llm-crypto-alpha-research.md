# LLM + AI for Crypto Trading Alpha - Research Session

**Date**: 2026-04-06

## What was done

Conducted extensive web research (20+ searches, 15+ page fetches) on using LLMs and AI for cryptocurrency trading alpha, covering seven specific areas: sentiment analysis, on-chain data interpretation, narrative tracking, tokenomics analysis, automated research agents, published backtests/live results, and specific tools.

## Key decisions and findings

### The most important finding

A rigorous 20-year backtest across 100+ symbols (arXiv, 2025) found that LLM trading strategies produce **statistically insignificant alpha** (p > 0.34) when survivorship bias, look-ahead bias, and data-snooping bias are controlled for. Buy-and-Hold Sharpe ratios (0.315-0.703) consistently beat LLM agents (FinMem: -0.228 to 0.025, FinAgent: -0.076 to 0.241). This is the single most important finding in this research.

### Corroborating live evidence

The Alpha Arena real-money competition gave 6 frontier LLMs $10k each to trade crypto perpetuals. Only 2 of 6 beat BTC buy-and-hold. Claude Sonnet 4.5 lost 33%, GPT-5 lost 40%, Gemini lost 50%+. Even the winner (Qwen 3 Max, +22.88%) experienced wild swings (peaked at +100% before settling).

### Where LLMs DO add value

1. **Research acceleration**: Summarizing whitepapers, cross-referencing sentiment, analyzing governance proposals.
2. **Sentiment as one signal among many**: Multi-agent architectures combining LLM sentiment with technical/on-chain signals show Sharpe improvements of 0.3-0.5 in academic settings.
3. **Narrative attention measurement**: CoinGecko 2025 data shows massive divergence between narrative popularity and profitability (AI tokens: most discussed, -50.2%; RWA: least discussed, +185.8%). LLMs could power a contrarian strategy based on this. Unexplored research gap.

### Polymarket bots are not what they seem

The viral "Claude bot turned $1 into $3.3M" stories are latency arbitrage, not LLM prediction. Claude wrote the bot code; it doesn't make trading decisions. 92.4% of Polymarket bots are unprofitable.

## Impact on M3 project

For our $600 crypto satellite strategy:
- **Use LLMs as research copilot only** (weekly sentiment check, narrative context).
- **Do NOT build autonomous LLM trading agents** -- evidence clearly shows they underperform simple trend-following.
- **Keep the mechanical trend-following system as primary decision-maker.**
- Potential future research: backtest a narrative-contrarian strategy using LLM-measured attention divergence.

## Research document

Full findings written to `/research/research-llm-crypto-alpha.md`.
