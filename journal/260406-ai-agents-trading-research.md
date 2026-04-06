# AI Agents for Trading Research

**Date:** 2026-04-06

## What Was Done

Comprehensive web research on using AI agents and scheduled autonomous AI tasks for trading and financial analysis. Covered 7 areas: agent frameworks, scheduled workflows, Claude/Anthropic for finance, LLM monitoring/alerting, retail implementations, small account edges, and cost-benefit analysis.

## Key Decisions / Takeaways

### The big finding: autonomous LLM trading does not work long-term

A rigorous study extending LLM trading evaluations from 6 months to 20 years (2004-2024) found that previously reported advantages **disappear entirely** at longer horizons. LLMs are too conservative in bull markets and too aggressive in bear markets. Short backtests are misleading due to survivorship, look-ahead, and data-snooping biases.

The Alpha Arena real-money crypto competition confirmed this: 4 out of 6 frontier LLMs (including Claude Sonnet 4.5 and GPT-5) **lost money**, failing to beat simple buy-and-hold Bitcoin.

### What does work: LLM as research copilot

- Research acceleration and code generation are universally positive use cases
- Sentiment analysis provides marginal but academically validated edge as one input among many
- Scheduled monitoring/alerts are cheap and practical
- Fed/ECB language analysis is validated by IMF and academic research

### Cost reality for a 2,000 EUR account

- Minimal viable LLM setup: ~13-20 EUR/month
- That's 7.5-12% of portfolio annually just for analysis tools
- Justified only as skill-building investment that scales with account growth
- Claude Pro ($20/month) is simpler than API management for this scale

### Practical next steps for M3

1. Use Claude (Pro or Sonnet API) as research copilot, not autonomous trader
2. Set up scheduled analysis: daily BTC/ETH briefing, weekly momentum scores, monthly rebalance signal
3. Use LLM for backtesting code generation (vectorbt, bt)
4. Keep total recurring costs under 20 EUR/month
5. Do NOT pursue autonomous trading — the evidence is strongly against it

## Sources

Full research with all sources saved to `research/research-ai-agents-trading.md`.
