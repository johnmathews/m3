# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

M3 (Money Making Machine) is a systematic trading project for a €2,000 account. Hybrid core-satellite portfolio:

- **Core (70%, ~€1,400):** Dual Momentum strategy on UCITS ETFs via DEGIRO Core Selection on Tradegate (SXR8, EUNL, EUNA
  — not LSE tickers). €1/trade. Monthly rebalance, 12-month lookback (consider ensemble 6-12mo). Trade Republic is an
  alternative (fractional shares, free savings plans).
- **Satellite (30%, ~€600):** Weekly trend-following on BTC/ETH via Bitvavo (primary, lowest fees) / Kraken (secondary).
  Maker-only orders.

All strategies must pass 3-6 months of paper trading before live deployment.

## Current Phase

Research complete. Next: backtesting framework setup, data pipeline, first strategy implementation (ETF dual momentum).

## Key Constraints

- **Fees dominate at this scale.** Every strategy must model realistic commissions, spreads, and slippage. ETF trades
  must use DEGIRO Core Selection on Tradegate (€1/trade) or Trade Republic. Crypto must use maker orders on Bitvavo
  (0.15%).
- **Dutch Box 3 tax:** €59,357 tax-free allowance — irrelevant at €2k, but track Jan 1 snapshot values.
- **No fantasy backtests.** Always use total return (dividend-adjusted) data. Account for look-ahead bias, survivorship
  bias, and overfitting.

## Tech Stack

- **Python 3.13**, managed with `uv`
- **Backtesting:** vectorbt (parameter sweeps), bt (readable monthly logic), NautilusTrader (execution validation),
  Freqtrade (crypto satellite)
- **Data:** pandas, numpy, yfinance (ETFs), exchange APIs via CCXT (crypto)
- **Storage:** Parquet for market data, SQLite/PostgreSQL for trade logs
- **Dashboards:** Streamlit or Grafana
- **Infrastructure:** Self-hosted (Docker on home server)

## Research Documents

- `research/research-etf-momentum.md` — Academic evidence, cost/tax engineering, implementation blueprint for dual momentum
- `research/research-etf-backtesting.md` — Framework comparison, lookback sensitivity, historical performance, failure modes
- `research/research-crypto-satellite.md` — Exchange selection, fee analysis, strategy candidates, risk management for crypto
  sleeve
- `research/research-gaps-and-alternatives.md` — Alternative brokers, yfinance data quality, MiCA regulation, fractional shares
- `research/research-ai-agents-trading.md` — AI agent frameworks, scheduled LLM workflows, cost analysis, evidence for/against autonomous trading
- `research/research-llm-alpha-generation.md` — LLM-driven alpha generation: sentiment analysis, fundamental analysis, agent
  frameworks, alternative data, regime detection, risks (data contamination, hallucination), practical tools (FinGPT, FinRL,
  MCP-based trading APIs). Key finding: LLMs best used as research assistants, not autonomous traders.
- `research/research-llm-crypto-alpha.md` — Web-researched (2025-2026 sources): LLM/AI for crypto trading alpha. Covers
  sentiment analysis backtests, on-chain + LLM analysis, narrative tracking, tokenomics, automated agents, live trading
  results (Alpha Arena), and specific tools (Kaito, Arkham, AIXBT, Nansen). Key finding: 20-year backtest shows LLMs
  produce statistically insignificant alpha; 4/6 frontier LLMs lost money in live trading competition.
