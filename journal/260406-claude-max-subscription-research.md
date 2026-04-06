# Claude Max Subscription Research for Trading/Research Automation

**Date:** 2026-04-06
**Purpose:** Evaluate Claude Max subscription capabilities relevant to building automated trading research systems.

---

## 1. Claude Max Subscription -- What's Included (2026)

### Pricing Tiers
- **Max 5x**: $100/month -- 5x the usage limits of Pro ($20/month)
- **Max 20x**: $200/month -- 20x the usage limits of Pro

### What You Get
- Access to all Claude models (Opus 4.6, Sonnet 4.6, Haiku 4.5)
- **Claude Code** included (terminal-based coding workflows)
- **Cowork** for delegating complex multi-step tasks in Claude Desktop
- Priority access to newest features and models
- Two weekly usage limits: one across all models, another for Sonnet-only. Both reset 7 days after session start
- **1 million token context window** on Opus 4.6 in Claude Code (no additional configuration or surcharge) -- available since March 2026
- Scheduled tasks (cloud and desktop)
- MCP connector access (Slack, Linear, Google Drive, etc.)

### What Max Does NOT Include
- Max adds no new features beyond Pro -- it is purely a "more usage" tier
- No API credits or programmatic API access (see section 2)

**Sources:**
- [What is the Max plan? | Claude Help Center](https://support.claude.com/en/articles/11049741-what-is-the-max-plan)
- [Max plan | Claude by Anthropic](https://claude.com/pricing/max)
- [Claude Max Plan Complete Guide 2026 | Claude Lab](https://claudelab.net/en/articles/claude-ai/claude-max-plan-complete-guide-2026)

---

## 2. API Access -- Subscription vs. Programmatic Use

### Critical Distinction: Subscription and API Are Separate Products

Claude paid plans (Pro, Max, Team, Enterprise) and the Claude Console/API are **entirely separate billing systems** with no crossover benefits.

- **Subscription** (Max $200/mo): covers claude.ai web, Claude Desktop, Claude mobile apps, and Claude Code CLI
- **API** (pay-per-token): requires separate Claude Console account with prepaid usage credits
- A Max subscription does NOT include API credits or programmatic access

### Can You Use Max Programmatically?

**Officially: No.** The subscription covers only Anthropic's official tools:
- claude.ai (web)
- Claude Desktop app
- Claude Code CLI
- Claude mobile apps

**As of April 4, 2026:** Anthropic officially cut off subscription quota access for third-party tools. Previously, some users exploited OAuth tokens via tools like CLIProxyAPI to route API-format requests through their subscription. This no longer works without paying extra via Anthropic's "extra usage" pay-as-you-go option.

### Practical Implication for Automation

For fully programmatic trading automation (e.g., Python scripts calling Claude API), you must use the Anthropic API with prepaid credits, billed at per-token rates. However, Claude Code's **scheduled tasks** and **skills** provide a semi-programmatic middle ground that runs under your subscription.

**Sources:**
- [Why do I have to pay separately for API? | Claude Help Center](https://support.claude.com/en/articles/9876003-i-have-a-paid-claude-subscription-pro-max-team-or-enterprise-plans-why-do-i-have-to-pay-separately-to-use-the-claude-api-and-console)
- [Using Claude Code with your Pro or Max plan | Claude Help Center](https://support.claude.com/en/articles/11145838-using-claude-code-with-your-pro-or-max-plan)
- [CLIProxyAPI (deprecated)](https://rogs.me/2026/02/use-your-claude-max-subscription-as-an-api-with-cliproxyapi/)

---

## 3. Anthropic API Pricing (Current as of April 2026)

### Standard Per-Token Pricing (per million tokens)

| Model | Input | Output |
|---|---|---|
| **Claude Opus 4.6** | $5.00 | $25.00 |
| **Claude Opus 4.5** | $5.00 | $25.00 |
| Claude Opus 4.1 (older gen) | $15.00 | $75.00 |
| **Claude Sonnet 4.6** | $3.00 | $15.00 |
| **Claude Sonnet 4.5** | $3.00 | $15.00 |
| **Claude Haiku 4.5** | $1.00 | $5.00 |
| Claude Haiku 3.5 | $0.80 | $4.00 |

### Key Cost Optimizations

- **Batch API**: 50% discount on all models (e.g., Opus 4.6 batch: $2.50/$12.50 per MTok)
- **Prompt Caching**:
  - 5-min cache write: 1.25x base input price; cache read: 0.1x base input price
  - 1-hour cache write: 2x base input price; cache read: 0.1x base input price
  - Pays off after 1 read (5-min) or 2 reads (1-hour)
- **Fast Mode** (Opus 4.6 only): 6x standard rates ($30/$150 per MTok) for low-latency
- **Long Context**: No surcharge -- 1M token requests billed at same per-token rate as short requests
- Batch and caching discounts stack

### Cost Estimates for Trading Research

- Analyzing a 100-page 10-K filing (~50K tokens input) with Opus 4.6: ~$0.25 input + output cost
- Analyzing 10 earnings call transcripts (~200K tokens) with Sonnet 4.6: ~$0.60 input + output cost
- Using Batch API for overnight analysis of 50 filings: roughly half the above rates
- Web search: $10 per 1,000 searches (plus token costs)
- Web fetch: no additional cost beyond tokens

**Sources:**
- [Pricing - Claude API Docs](https://platform.claude.com/docs/en/about-claude/pricing)
- [Claude API Pricing 2026 | MetaCTO](https://www.metacto.com/blogs/anthropic-api-pricing-a-full-breakdown-of-costs-and-integration)

---

## 4. Claude Code Capabilities for Automation

### Scheduled Tasks (Most Relevant for Trading Research)

Three scheduling mechanisms:

| Feature | Cloud Tasks | Desktop Tasks | `/loop` |
|---|---|---|---|
| Runs on | Anthropic cloud | Your machine | Your machine |
| Requires machine on | No | Yes | Yes |
| Minimum interval | 1 hour | 1 minute | 1 minute |
| Access to local files | No (fresh clone) | Yes | Yes |
| MCP servers | Connectors per task | Config files + connectors | Inherits from session |
| Persistent | Yes | Yes | No (session-scoped) |

**Cloud scheduled tasks** are the most powerful for unattended automation:
- Run even when your computer is off
- Access all configured MCP connectors (Slack, Linear, Google Drive, etc.)
- Clone GitHub repos at run time
- Can push to `claude/`-prefixed branches
- Environment variables for API keys and secrets
- Setup scripts for installing dependencies
- Available on Pro, Max, Team, and Enterprise plans

**Practical examples for trading:**
- Review and summarize overnight market moves each morning
- Analyze earnings releases and generate memos on a schedule
- Run weekly dependency audits on trading codebase
- Sync documentation after strategy changes merge

### Web Access
- Claude Code can browse the web via Computer Use (controls your Mac like a human)
- Web search and web fetch tools available
- MCP connectors for integrating external services

### Key Limitations
- Cloud tasks clone repos fresh each run (no persistent local state)
- Minimum 1-hour interval for cloud tasks
- No direct API access from subscription -- scheduled tasks are the programmatic workaround

**Sources:**
- [Schedule tasks on the web - Claude Code Docs](https://code.claude.com/docs/en/web-scheduled-tasks)
- [Claude Code March 2026 Features](https://help.apiyi.com/en/claude-code-2026-new-features-loop-computer-use-remote-control-guide-en.html)
- [Schedule recurring tasks in Cowork | Claude Help Center](https://support.claude.com/en/articles/13854387-schedule-recurring-tasks-in-cowork)

---

## 5. Documented Use Cases: Claude for Financial Analysis / Trading

### Anthropic's Official Financial Services Position
- Claude leads every model on the **Finance Agent benchmark** (measuring agentic financial analysis -- multi-step, tool-using work)
- Sonnet 4.6 scores 63.3% on this benchmark
- Anthropic has released purpose-built **financial plugins** for Claude: DCF models, investment committee memos, morning research notes

### Institutional Data Integration
- **Claude in Excel** supports MCP connectors for live data from S&P Global, LSEG, Daloopa, PitchBook, Moody's, and FactSet
- **LSEG MCP server** provides live yield curves, bond reference data, FX spot rates, swap pricing, volatility surfaces, and real-time news

### Open-Source Trading Skills
The **[claude-trading-skills](https://github.com/tradermonty/claude-trading-skills)** repository provides Claude Code skills for:
- Sector analysis, technical analysis, market breadth
- Economic calendar and earnings calendar monitoring
- Backtesting and strategy development
- VCP screener, CANSLIM screener, PEAD screener
- Options strategy advisor, portfolio manager, position sizer
- Market top/bubble detectors, macro regime detection
- Requires: Financial Modeling Prep (FMP) API; optional FINVIZ Elite, Alpaca MCP

### Enterprise Adoption
- **Bridgewater Associates**: Investment Analyst Assistant powered by Claude -- generates Python code, creates data visualizations, iterates through financial analysis
- Claude's NLP processes Fed minutes and social media sentiment, reportedly predicting reversals with 18% better accuracy than baselines

### Key Financial Analysis Capabilities
- Due diligence and market research
- Competitive benchmarking and portfolio deep dives
- Financial modeling with audit trails
- Institutional-quality investment memos and pitch decks
- Earnings analysis and research note generation

**Sources:**
- [Claude for Financial Services | Anthropic](https://www.anthropic.com/news/claude-for-financial-services)
- [Claude for Financial Services Overview | Claude Help Center](https://support.claude.com/en/articles/12219959-claude-for-financial-services-overview)
- [claude-trading-skills | GitHub](https://github.com/tradermonty/claude-trading-skills)
- [Supercharge Claude's Financial Skills With LSEG Data](https://www.lseg.com/en/insights/supercharge-claudes-financial-skills-with-lseg-data)
- [Claude Sonnet 4.6 as Financial Analyst | Linas Substack](https://linas.substack.com/p/claudeinfinance)
- [Build Profitable Futures Strategy with Claude AI | PickMyTrade](https://blog.pickmytrade.io/build-profitable-futures-strategy-claude-ai-2026/)

---

## 6. Context Window Analysis for Financial Documents

### Claude's 1M Token Context Window

- **Opus 4.6 and Sonnet 4.6**: 1 million tokens (generally available)
- **Retrieval accuracy**: 90% across the full 1M window
- **No long-context surcharge**: a 900K-token request costs the same per-token rate as a 9K-token request
- ~750,000 words, or 2,000-3,000 pages of dense text

### Financial Document Sizing (Approximate)

| Document Type | Typical Size | Tokens (approx) |
|---|---|---|
| 10-K Annual Filing (large company) | 100-300 pages | 50K-150K tokens |
| 10-Q Quarterly Filing | 40-80 pages | 20K-40K tokens |
| Earnings Call Transcript | 15-25 pages | 10K-20K tokens |
| Analyst Research Report | 20-50 pages | 15K-35K tokens |
| Full Deal Document Set | 500+ pages | 250K-500K tokens |
| 3 Years of Quarterly Filings (1 company) | ~12 x 40-80 pages | 240K-480K tokens |

### What Fits in 1M Tokens
- An entire company's financial history (multiple years of 10-Ks, 10-Qs, and earnings calls)
- A full M&A deal document set
- Dozens of analyst research reports simultaneously
- Multi-company comparative analysis across several years

### Practical Advantages
- **Eliminates RAG complexity**: For bounded document sets, the full context window removes the need for vector databases and retrieval pipelines
- **Cross-document reasoning**: Can identify trends, contradictions, and patterns across multiple filings in a single pass
- **Complete context**: No risk of missing relevant information due to chunking or retrieval failures

### Limitations
- Very large analyses (e.g., entire sector of 50+ companies across 5 years) would still exceed 1M tokens and require batching or RAG
- Token costs scale linearly with input size (though no surcharge for long context)

**Sources:**
- [Claude's 1M Token Window: Practical Uses | Arsturn](https://www.arsturn.com/blog/mastering-claudes-1-million-token-context-window-a-practical-guide)
- [Claude 1M Token Context Window | MindStudio](https://www.mindstudio.ai/blog/claude-1m-token-context-window-ai-agents)
- [Why Claude's 1M context length is a big deal | Martin Alderson](https://martinalderson.com/posts/why-claudes-new-1m-context-length-is-a-big-deal/)
- [LLMs for Financial Document Analysis | IntuitionLabs](https://intuitionlabs.ai/articles/llm-financial-document-analysis)

---

## Summary: Key Takeaways for M3 Project

1. **Max 20x ($200/mo) is the best subscription tier** for heavy research use -- 20x Pro limits, includes Claude Code with 1M context on Opus 4.6, and scheduled tasks.

2. **Subscription does NOT include API access.** For Python scripts calling Claude directly, you need separate API credits. However, Claude Code scheduled tasks provide a subscription-covered alternative for many automation patterns.

3. **API costs have dropped significantly** with the 4.5/4.6 generation. Opus 4.6 at $5/$25 per MTok is 67% cheaper than Opus 4.1's $15/$75. Batch API halves costs further.

4. **Scheduled tasks are the key automation mechanism** under a subscription. Cloud tasks run on Anthropic infrastructure (even when your machine is off), can access MCP connectors, and run on hourly+ schedules.

5. **Financial analysis is a first-class use case** for Claude, with official financial plugins, LSEG data integration, and benchmark-leading performance on finance agent tasks.

6. **1M token context is more than sufficient** for single-company deep analysis (all filings fit easily). Multi-company sector analysis may require batching but is still very feasible with Sonnet 4.6 at $3/$15 per MTok.

7. **The claude-trading-skills repo** is directly relevant -- provides pre-built skills for technical analysis, screening, backtesting, and market research that work in Claude Code.
