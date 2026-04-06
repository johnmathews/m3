# Crypto Satellite Research Verification

_Date: 2026-04-06_

Independent web research to verify and extend the claims in `research-crypto-satellite.md`. Each claim is evaluated against recent (2024-2026) academic and practitioner evidence.

---

## Claim 1: Trend-following (weekly MA) historically reduces drawdowns vs buy-and-hold for crypto

### Verdict: CONFIRMED -- strong evidence, but nuances matter

The strongest recent evidence comes from Zarattini, Pagani, and Barbon (April 2025), "Catching Crypto Trends: A Tactical Approach for Bitcoin and Altcoins." Their ensemble Donchian-channel trend model on BTC (2015-2025) achieved:

- **CAGR:** 30% (vs. passive BTC buy-and-hold with 80%+ drawdowns)
- **Sharpe ratio:** 1.58
- **Sortino ratio:** 2.03
- **Max drawdown:** 19% (vs. 80%+ for buy-and-hold)
- **Alpha vs. BTC:** 14% annualized

For a diversified top-20 crypto portfolio, the same framework delivered a net-of-fees Sharpe of 1.57 and max drawdown of only 11%, with 10.8% annualized alpha vs. BTC.

Important caveats:
- The study tested at 10, 25, and 50 bps transaction cost levels. At 10 bps (the reported net figure), results held well. At higher fee levels typical of small retail accounts (15-25 bps maker), returns erode.
- **Shorter lookback periods (5-30 days) showed the strongest risk-adjusted returns**, not the weekly/monthly timeframes the research document implies. The study used daily closing prices, not weekly candles.
- A separate QuantifiedStrategies backtest (2015-2021, no fees) found a 20-day EMA strategy on BTC achieved 126% CAGR vs. 94% buy-and-hold, with max drawdown of 39% vs. 83%.
- A Palazzi (2025) paper in the Journal of Futures Markets also found that active trading strategies can beat passive approaches in crypto.

**What the research document gets right:** Trend-following does reduce drawdowns dramatically in crypto. This is well-supported.

**What it gets wrong or oversimplifies:** The document implies weekly rebalancing is optimal. The academic evidence points to shorter lookbacks (5-30 day) being stronger. Weekly cadence is justified by fee constraints at the EUR 600 level, but this is a practical compromise, not the academic optimum. The document should acknowledge this tradeoff explicitly.

### Sources
- [Zarattini et al. - Catching Crypto Trends (SSRN)](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=5209907)
- [QuantifiedStrategies - Trend Following and Momentum on Bitcoin](https://www.quantifiedstrategies.com/trend-following-and-momentum-on-bitcoin/)
- [QuantifiedStrategies - Crypto Trend Trading Strategy](https://www.quantifiedstrategies.com/crypto-trend-trading-strategy-for-bitcoin/)
- [Palazzi (2025) - Trading Games: Beating Passive Strategies in the Bullish Crypto Market](https://onlinelibrary.wiley.com/doi/full/10.1002/fut.70018)

---

## Claim 2: Mean reversion (RSI < 30) shows "mixed results" across backtests

### Verdict: CONFIRMED -- actually worse than "mixed"; evidence leans negative

QuantifiedStrategies backtested RSI-based mean reversion on BTC (2015-2021) and found:
- The "best" setup (RSI(25) < 30 entry, > 80 exit) had a profit factor of 1.95 and 20.84% CAGR, but generated **only 3 trades** over 6+ years -- statistically meaningless.
- When sorted by number of trades (for statistical significance), the profit factor "diminishes a lot."
- The author's explicit conclusion: "RSI as a contrarian indicator is basically worthless on Bitcoin."
- Similar weak results were found for Ethereum and Dogecoin.

A separate systematic review found that BTC-neutral residual mean reversion strategies achieved ~2.3 Sharpe post-2021, but this is a sophisticated pairs/statistical arbitrage approach, not simple RSI dip-buying.

**What the research document gets right:** "Mixed results" is accurate in the most charitable interpretation.

**What it understates:** The evidence is worse than "mixed" for simple RSI mean reversion. It essentially does not work on BTC/ETH in a statistically meaningful way. The document recommends allocating 20-30% to mean reversion, which seems poorly supported by the evidence. If mean reversion is included, it should probably be a very small allocation with explicit acknowledgment that the edge is unproven.

### Sources
- [QuantifiedStrategies - Bitcoin RSI Trading Strategy](https://www.quantifiedstrategies.com/bitcoin-rsi/)
- [Stoic.ai - Mean Reversion Trading in Crypto](https://stoic.ai/blog/mean-reversion-trading-how-i-profit-from-crypto-market-overreactions/)

---

## Claim 3: Funding-rate arbitrage returns 15-25% annualized normally

### Verdict: PARTIALLY CONFIRMED -- but heavily compressed and inaccessible at EUR 600

Recent data (2024-2025):
- Average annualized return from funding rate arbitrage was **14.39% in 2024**, rising to **19.26% in 2025** as average funding rates stabilized at 0.015% per 8-hour period (50% increase from 2024).
- One academic study (ScienceDirect, August 2025) found returns up to 115.9% over six months under optimal conditions, but this represents peak scenarios, not typical performance.
- Average funding rate in 2024 was just 0.0173%, with a maximum of 0.1308% -- dramatic compression from 2017-2021 levels (which saw sustained 0.2-0.3% rates).
- Cross-platform arbitrage adds 3-5% annualized on top.

**What the research document gets right:** The 15-25% range is broadly correct for 2024-2025 averages.

**What it correctly identifies as a barrier:** The document already flags that this strategy requires EUR 1,000-2,000+ minimum capital, margin/derivatives access, and is high complexity. This is appropriate. At EUR 600, this is not viable.

**Additional risk not mentioned:** Institutional capital has dramatically compressed funding rates over 2023-2025. The "15-25% normally" figure may represent a historical average that is declining as the market matures and more capital chases this arbitrage. The 2024 average (14.39%) was already at the low end of the stated range.

### Sources
- [Gate.io - Perpetual Contract Funding Rate Arbitrage Strategy in 2025](https://www.gate.com/learn/articles/perpetual-contract-funding-rate-arbitrage/2166)
- [ScienceDirect - Exploring Risk and Return Profiles of Funding Rate Arbitrage](https://www.sciencedirect.com/science/article/pii/S2096720925000818)
- [Bitget - Funding Rate Arbitrage Decoded](https://www.bitget.com/news/detail/12560604395607)

---

## Claim 4: stETH yields ~2.5% APR

### Verdict: OUTDATED -- current yield is higher (~3.2-3.3%)

As of early 2026:
- **Ethereum staking base yield:** 2.84% (consensus layer rewards)
- **Total yield including MEV and priority fees:** ~3.3% APY
- **Lido stETH APR:** approximately 3.2% after Lido's 10% fee on rewards
- 35.9 million ETH is staked (28.91% of total supply), secured by ~1.1 million active validators
- Lido holds 8.7 million ETH (24.2% market share of staking)

The staking yield is mathematically linked to the number of active validators and decreases as total stake increases. The rate has generally trended between 3-4% throughout 2025-2026.

**What the research document gets wrong:** The stated 2.5% APR is too low by approximately 0.7-0.8 percentage points. The current figure is closer to 3.2-3.3%. This is a minor inaccuracy but worth correcting.

**Practical note for EUR 600:** The document correctly flags that Ethereum L1 DeFi/staking has high gas friction at small scale. On L2 or through exchange staking products, the yield is accessible but still modest in absolute terms (roughly EUR 20/year on EUR 600).

### Sources
- [Datawallet - Ethereum Staking Statistics & Trends in 2026](https://www.datawallet.com/crypto/ethereum-staking-statistics-and-trends)
- [Lido Finance](https://stake.lido.fi/)
- [Coin Bureau - Lido Finance Review 2026](https://coinbureau.com/review/lido-finance-review)
- [CoinLaw - ETH Staking Statistics 2026](https://coinlaw.io/eth-staking-statistics/)

---

## Claim 5: BTC-S&P500 correlation has increased since 2020

### Verdict: PARTIALLY CONFIRMED -- but the picture is much more dynamic than stated

The correlation story has shifted dramatically and is no longer a simple "increasing" trend:

- **2020-2024:** Correlation generally increased, especially after the Bitcoin spot ETF approval in January 2024. At one point in early 2025, the rolling correlation reached **+0.88**.
- **Late 2025:** Correlation dropped sharply to **-0.299** with S&P 500 and **-0.24** with Nasdaq, driven by U.S. tariff escalations and trade war fears.
- **2026:** A Binance Research study found Bitcoin's correlation with global monetary easing indices flipped from +0.21 (pre-ETF) to **-0.778** in 2026, suggesting Bitcoin is evolving from a "macro lagging receiver" to a "leading pricer."

The relationship is regime-dependent and unstable:
- During "risk-on" periods, BTC correlates positively with equities
- During trade-war/tariff stress in late 2025, BTC decoupled significantly
- Structural factors (ETF flows, halving cycles, institutional adoption) have changed the dynamics

**What the research document gets right:** Correlation did increase post-2020, and during stress crypto often moves with equities.

**What it misses:** The late 2025/early 2026 decoupling is significant and contradicts the simple "increased since 2020" narrative. The correlation is highly regime-dependent. For portfolio construction purposes, you cannot rely on crypto providing diversification during equity drawdowns -- but you also cannot assume it will always move in lockstep. The document's assumption that "the two are largely uncorrelated" (from readme.md, re: ETF core vs crypto satellite) needs revisiting.

### Sources
- [MEXC News - Bitcoin's Correlation with Equities Hits 2025 Lows](https://www.mexc.com/news/270276)
- [Nasdaq - Bitcoin Performance Analysis Shows Strong Correlation With S&P 500](https://www.nasdaq.com/articles/bitcoin-performance-analysis-shows-strong-correlation-sp-500)
- [Bitcoin Magazine - Bitcoin Is Decoupling](https://bitcoinmagazine.com/bitcoin-for-corporations/bitcoin-is-decoupling-doesnt-care-about-tariffs)
- [Yahoo Finance / Binance Research - Bitcoin Price Is Decoupling in 2026](https://finance.yahoo.com/markets/crypto/articles/binance-case-study-bitcoin-price-150357229.html)
- [AInvest - Bitcoin's Re-Emerging Correlation with Risk Assets](https://www.ainvest.com/news/bitcoin-emerging-correlation-risk-assets-means-2025-2026-investors-2512/)

---

## Claim 6: CCXT, Freqtrade, and Jesse are recommended trading tools

### Verdict: REASONABLE -- but the landscape has evolved

The three recommended tools remain legitimate choices in 2026, but the ecosystem has grown:

**CCXT** (unified exchange API library):
- Still the standard for connecting to multiple exchanges via a single interface. No serious competitor has emerged. Good choice.

**Freqtrade:**
- 25,000+ GitHub stars, actively maintained since 2017
- Python-based, supports machine learning-driven optimization
- Telegram/WebUI control
- Large community and extensive documentation
- Still one of the top 2-3 open-source crypto trading bots

**Jesse:**
- 5,000+ GitHub stars, active development
- Now includes JesseGPT (AI-assisted strategy writing/debugging)
- Supports live trading on Binance, Bybit, and major exchanges
- Cleaner API than Freqtrade for developer-oriented users

**Notable alternatives not mentioned in the document:**

| Tool | GitHub Stars | Key Differentiator |
|:-----|:-------------|:-------------------|
| **OctoBot** | 4,000+ | Modular "tentacles" architecture, web UI, cloud hosting option, no-code possible |
| **Hummingbot** | Large community | Best for market making, supports 35+ CEXs and DEXs, TWAP/VWAP execution |
| **Superalgos** | -- | Visual strategy design environment |
| **Passivbot** | -- | Self-hosted, Python, grid/DCA strategies |
| **VectorBT** | Active | Not a trading bot but a backtesting framework; excellent for parameter sweeps and strategy research |

**For this project specifically:** Given the tech stack (Python, self-hosted, small account), Freqtrade remains the strongest fit. It has the largest community, best documentation, and native support for the exchanges being considered. Jesse is a good secondary option for its cleaner code architecture. OctoBot is worth considering if you want lower-code strategy iteration.

**Important note on Bitvavo support:** Most open-source bots do not directly support Bitvavo. CCXT does support Bitvavo, so custom strategies via CCXT would work. Third-party services like Cryptohopper support Bitvavo. Freqtrade uses CCXT under the hood, so Bitvavo integration is possible but may require configuration.

### Sources
- [Freqtrade GitHub](https://github.com/freqtrade/freqtrade)
- [Jesse](https://jesse.trade/)
- [Gainium - 6 Best Open Source Crypto Trading Bots in 2026](https://gainium.io/best/open-source)
- [Medium - AI-Integrated Crypto Trading Platforms Comparison](https://medium.com/@gwrx2005/ai-integrated-crypto-trading-platforms-a-comparative-analysis-of-octobot-jesse-b921458d9dd6)
- [Bitget - Best Open-Source Crypto Trading Bots on GitHub 2026](https://www.bitget.com/academy/crypto-trading-bots-10)
- [Bitvavo - Crypto Trading Bots Help Center](https://support.bitvavo.com/hc/en-us/sections/18376338597649-Crypto-Trading-Bots-Asset-management)

---

## Important Risks and Considerations the Document Misses

### 1. Counterparty/Exchange Risk is Underweighted

The document mentions splitting across Bitvavo and Kraken for counterparty diversification, which is good. But it does not discuss the scale of the threat:

- **Bybit hack (February 2025):** $1.4-1.5 billion stolen from a cold wallet via a supply chain attack on Safe{Wallet}. North Korea (Lazarus Group) attributed. This was the world's 3rd-largest exchange.
- **Total crypto stolen in 2025:** over $2.1 billion -- second-worst year on record.
- **January 2026 alone:** $127 million in exploits reported.
- Even multisig cold wallets were compromised through third-party service provider attacks.

At EUR 600, total loss of exchange funds would be painful but not catastrophic. However, the document should explicitly address: (a) not leaving more funds on an exchange than needed for active trading, and (b) considering hardware wallet storage for any funds not actively in play.

### 2. MiCA Regulatory Impact

The document mentions Dutch Box 3 tax correctly but does not discuss MiCA (Markets in Crypto-Assets Regulation):

- MiCA Phase 2 took effect December 30, 2024, covering CASPs (Crypto Asset Service Providers).
- **Bitvavo secured its MiCA license from the AFM in June 2025.**
- **Kraken obtained a MiCA license from Ireland in 2025.**
- All grandfathering periods expire across EU member states by **July 2026**.
- MiCA has driven massive consolidation: fewer than 500 unregulated VASPs expected to remain active by 2026.
- Retail investor participation grew 27% as consumer confidence improved under regulation.

Both recommended exchanges are MiCA-compliant, which is good. But the regulatory landscape is shifting fast, and the document should note that any exchange choice should be re-verified for MiCA compliance.

### 3. Overfitting and Backtest Reliability

The document warns about "no fantasy backtests" in the CLAUDE.md, which is excellent. But the research document itself cites backtest results without sufficiently caveating:

- **Survivorship bias in crypto:** Backtests that only include currently-traded assets exclude failed projects, inflating historical returns.
- **Overfitting:** Optimizing strategy parameters to historical data produces strategies that look great on paper but fail live. The Zarattini et al. paper addresses this with ensemble methods, but simpler strategies are more prone.
- **Regime change:** Crypto markets in 2015-2020 (low institutional participation, high retail speculation) behaved very differently from 2024-2026 (ETF flows, institutional arbitrage, compressed funding rates). Past backtests may not predict future performance.
- **Live performance gap:** Even well-designed strategies typically underperform backtests due to execution realities.

### 4. The Correlation Diversification Assumption is Fragile

The readme states the ETF core and crypto satellite "are largely uncorrelated -- diversification benefit." As documented in Claim 5 above, this is no longer reliably true. During the specific scenario where diversification matters most (broad market stress), crypto has repeatedly moved in tandem with equities since 2020. The late 2025 decoupling is encouraging but not guaranteed to persist.

### 5. Kraken Explicitly Allows Trading Bots

This is a positive finding worth noting. Kraken's official documentation states: "Clients are welcome to use trading bots to trade our markets." They provide REST API, WebSocket API (v1 and v2), and example bot code in Python and Node.js. Bitvavo also has an API gateway that supports automated trading.

### 6. The EUR 600 Capital Constraint is Even More Binding Than Stated

The fee analysis in the document is solid, but does not account for:
- **Minimum order sizes:** Some exchange pairs have minimum order amounts that may be a binding constraint when position sizing with 1% risk per trade on a EUR 600 account (i.e., EUR 6 risk per trade).
- **Spread costs:** The fee analysis focuses on maker/taker fees but does not quantify bid-ask spreads, which can add 0.05-0.20% per trade for BTC/EUR and more for ETH/EUR on smaller exchanges.
- **Withdrawal fees:** If moving funds between exchanges for counterparty diversification, withdrawal fees (especially for ETH) can be significant relative to EUR 600.

### Sources
- [The Block - From Bybit to GMX: The 10 Biggest Crypto Hacks of 2025](https://www.theblock.co/post/380992/biggest-crypto-hacks-2025)
- [D'Cent Wallet - The $1.5B Bybit Hack](https://store.dcentwallet.com/blogs/post/bybit-hack-2025-exchange-security)
- [SSRN - The $1.4 Billion Bybit Hack: Cybersecurity Failures](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=5150171)
- [CoinDesk - Bitvavo Secures MiCA License](https://www.coindesk.com/policy/2025/06/27/bitvavo-secures-a-mica-license-from-the-netherlands)
- [ESMA - Markets in Crypto-Assets Regulation](https://www.esma.europa.eu/esmas-activities/digital-finance-and-innovation/markets-crypto-assets-regulation-mica)
- [InnReg - MiCA Regulation Guide 2026](https://www.innreg.com/blog/mica-regulation-guide)
- [Kraken - Does Kraken Allow Trading Bots?](https://support.kraken.com/articles/360001373983-does-kraken-allow-trading-bots-)
- [Gainium - Common Backtesting Problems and Solutions](https://gainium.io/blog/common-backtesting-problems)
- [Stoic.ai - How to Backtest Crypto Trading Strategies](https://stoic.ai/blog/backtesting-trading-strategies/)

---

## Exchange Claims Verification (Fee Schedules, Regulatory Status, API Limits)

Research conducted 2026-04-06 using live web sources.

### Claim: Binance withdrew from the Dutch market in 2023 after failing to secure DNB registration

**Verdict: CONFIRMED**

Binance announced its exit from the Dutch market in June 2023 after failing to obtain registration with De Nederlandsche Bank (DNB). From July 17, 2023, existing Dutch users were restricted to withdrawals only -- no new purchases, trades, or deposits. As of March 2026, Binance remains unavailable in the Netherlands. There is no indication that Binance has returned or plans to return to the Dutch market.

Sources:
- [The Block - Binance exits the Netherlands](https://www.theblock.co/post/235084/binance-exits-the-netherlands)
- [Silicon Canals - Binance to exit the Dutch market](https://siliconcanals.com/binance-to-exit-the-dutch-market/)
- [PureVPN - How to Access Binance in the Netherlands (March 2026)](https://www.purevpn.com/crypto/binance-with-a-vpn/netherlands) (confirms still unavailable)

---

### Claim: Bitvavo is DNB-registered with maker/taker fees of 0.15%/0.25%, free SEPA deposits/withdrawals

**Verdict: CONFIRMED -- fees and regulatory status are accurate**

**Regulatory status:**
- Bitvavo has been registered with DNB since November 2020.
- In June 2025, Bitvavo became the first Dutch exchange to receive a MiCA (MiCAR) license from the AFM (Authority for the Financial Markets), allowing it to serve users across all 30 EEA countries.
- Bitvavo is currently the largest EUR spot exchange worldwide.
- DNB public register entry: [R163129](https://www.dnb.nl/en/public-register/information-detail/?registerCode=WFTBI&relationNumber=R163129)

**Fees (verified against current fee schedule):**

| 30-day Volume | Maker Fee | Taker Fee |
|:---|:---|:---|
| EUR 0+ | 0.15% | 0.25% |
| EUR 100,000+ | 0.10% | 0.20% |
| EUR 250,000+ | 0.08% | 0.16% |
| EUR 500,000+ | 0.06% | 0.12% |
| EUR 1,000,000+ | 0.05% | 0.10% |
| EUR 2,500,000+ | 0.04% | 0.08% |
| EUR 5,000,000+ | 0.04% | 0.06% |
| EUR 10,000,000+ | 0.00% | 0.05% |
| EUR 25,000,000+ | 0.00% | 0.02% |
| EUR 100,000,000+ | 0.00% | 0.01% |
| EUR 500,000,000+ | 0.00% | 0.01% |

The base tier of 0.15%/0.25% as stated in the research document is correct.

Additional: Stablecoin pairs (USDC/EUR, USDT/EUR) have reduced fees: maker up to 0% and taker up to 0.01%.

**SEPA transfers:**
- EUR deposits via SEPA: FREE (up to EUR 5,000,000 per transaction)
- EUR withdrawals via SEPA: FREE (for amounts exceeding EUR 1; a EUR 0.50 fee applies to smaller withdrawals)

The document's claim of "Free / Free" is accurate for practical purposes.

Sources:
- [Bitvavo - DNB Registration](https://support.bitvavo.com/hc/en-us/articles/4405243980945-Bitvavo-registered-with-the-Dutch-Central-Bank-DNB)
- [DNB Public Register - Bitvavo B.V.](https://www.dnb.nl/en/public-register/information-detail/?registerCode=WFTBI&relationNumber=R163129)
- [TradingFinder - Bitvavo Review 2026 (full fee table)](https://tradingfinder.com/exchanges/bitvavo/)
- [Bitvavo - Reduced fees for stablecoin pairs](https://bitvavo.com/en/news/reducedfees-usdc-usdt)
- [CoinDesk - Bitvavo Secures MiCA License](https://www.coindesk.com/policy/2025/06/27/bitvavo-secures-a-mica-license-from-the-netherlands)

---

### Claim: Kraken is EU-compliant with maker/taker fees of 0.16%/0.26%, free SEPA deposits

**Verdict: FEES ARE WRONG -- base tier is 0.25%/0.40%, not 0.16%/0.26%. SEPA deposits are free; SEPA withdrawals cost EUR 1.**

**Regulatory status:**
- Kraken obtained a MiCA license from the Central Bank of Ireland in 2025.
- Kraken went live in all 30 EEA countries under MiCA on August 12, 2025.
- Kraken previously held VASP registration in the Netherlands.
- Describing Kraken as "EU-compliant" is accurate but understates it -- Kraken is now fully MiCA-licensed via EU passporting from Ireland.

**Fees (verified against Kraken official fee schedule page):**

| 30-day Volume (USD) | Maker Fee | Taker Fee |
|:---|:---|:---|
| $0+ | **0.25%** | **0.40%** |
| $10,000+ | 0.20% | 0.35% |
| $50,000+ | 0.14% | 0.24% |
| $100,000+ | 0.12% | 0.22% |
| $250,000+ | 0.10% | 0.20% |
| $500,000+ | 0.08% | 0.18% |
| $1,000,000+ | 0.06% | 0.16% |
| $2,500,000+ | 0.04% | 0.14% |
| $5,000,000+ | 0.02% | 0.12% |
| $10,000,000+ | 0.00% | 0.10% |
| $100,000,000+ | 0.00% | 0.08% |
| $500,000,000+ | 0.00% | 0.05% |

**THE RESEARCH DOCUMENT STATES 0.16%/0.26% -- THIS IS INCORRECT.** The actual base tier is 0.25% maker / 0.40% taker. The 0.16%/0.26% figures do not correspond to any published tier. Some third-party review sites have reported 0.16%/0.26% but the official Kraken fee schedule page clearly shows 0.25%/0.40% as the base. This is a significant error that affects the fee comparison analysis.

**SEPA transfers:**
- EUR deposits via SEPA: FREE (minimum EUR 1, 0-3 business days or instant)
- EUR withdrawals via SEPA: EUR 1 fee (minimum EUR 2 withdrawal, 0-5 business days)
- SEPA Instant available via Banking Circle

The document states "Free / 1-2 EUR" for SEPA -- this is approximately correct (free deposit, EUR 1 withdrawal).

Sources:
- [Kraken - Fee Schedule (official)](https://www.kraken.com/features/fee-schedule)
- [Kraken - Cash deposit options, fees, minimums](https://support.kraken.com/articles/360000381846-cash-deposit-options-fees-minimums-and-processing-times-)
- [Kraken - Cash withdrawal options, fees, minimums](https://support.kraken.com/articles/360000423043-cash-withdrawal-options-fees-minimums-and-processing-times-)
- [Kraken Blog - Now live across all 30 EEA countries under MiCA](https://blog.kraken.com/news/all-30-eea-countries-mica)
- [Kraken Blog - MiCA license from Central Bank of Ireland](https://blog.kraken.com/news/mica-license-central-bank-of-ireland)

---

### Claim: Coinbase Advanced has maker/taker fees of 0.40%/0.60%, was fined by DNB in 2023

**Verdict: FEES ARE WRONG -- base tier is 0.60%/1.20%, not 0.40%/0.60%. DNB fine is confirmed.**

**Regulatory status:**
- Coinbase obtained DNB registration on September 22, 2022.
- DNB imposed a fine of EUR 3,325,000 on January 18, 2023, for Coinbase providing crypto services without registration from November 15, 2020 to August 24, 2022.
- The fine was increased because Coinbase had enjoyed a competitive advantage by not paying supervisory fees during the unregistered period.
- Coinbase is now also MiCA-licensed for EU operations.

**Fees (verified against multiple sources including Coinbase official help page):**

| Tier | 30-day Volume (USD) | Maker Fee | Taker Fee |
|:---|:---|:---|:---|
| Intro 1 (Base) | $0+ | **0.60%** | **1.20%** |
| Intro 2 | $1,000+ | 0.35% | 0.75% |
| Advanced 1 | $10,000+ | 0.25% | 0.40% |
| Advanced 2 | $50,000+ | 0.15% | 0.25% |
| Advanced 3 | $500,000+ | 0.10% | 0.20% |
| Advanced 4 | $1,000,000+ | 0.07% | 0.16% |
| Advanced 5 | $15,000,000+ | 0.05% | 0.14% |
| Advanced 6 | $50,000,000+ | 0.02% | 0.10% |
| Advanced 7 | $100,000,000+ | 0.00% | 0.08% |
| Advanced 8 | $250,000,000+ | 0.00% | 0.05% |

**THE RESEARCH DOCUMENT STATES 0.40%/0.60% -- THIS IS INCORRECT.** The actual base tier (Intro 1, $0 volume) is 0.60% maker / 1.20% taker. The figures 0.40%/0.60% do not exactly match any single tier -- 0.40% taker appears in Advanced 1 ($10K+ volume) but paired with 0.25% maker, not 0.40%. The document's stated fees dramatically understate the actual cost for a new/low-volume user. For a EUR 600 account, Coinbase Advanced is even more expensive than the document suggests.

**DNB fine:** Confirmed. EUR 3,325,000 (approximately $3.6M), announced January 26, 2023.

Sources:
- [TokenEcho - Coinbase Advanced Trade Fees Explained 2026](https://tokenecho.io/guides/coinbase-advanced-trade-fees/)
- [Bitbo - Coinbase vs Coinbase Advanced 2026](https://bitbo.io/buy/coinbase-vs-advanced/)
- [DNB - Administrative fine on Coinbase Europe Limited](https://www.dnb.nl/en/general-news/enforcement-measures-2023/dnb-imposes-administrative-fine-on-coinbase-europe-limited-for-providing-crypto-services-without-the-legally-required-registration-until-22-september-2022/)
- [Decrypt - Dutch Central Bank Fines Coinbase $3.6M](https://decrypt.co/120040/dutch-central-bank-fines-coinbase-3-6m-non-compliance)
- [NL Times - Dutch central bank fines Coinbase over EUR 3.3M](https://nltimes.nl/2023/01/26/dutch-central-bank-fines-coinbase-eu33-million-ignoring-aml-terror-financing-rules)

---

### Claim: Bitvavo API limit is ~1,000 weight/min, Kraken uses a call-counter system

**Verdict: CONFIRMED -- both are accurate**

**Bitvavo API rate limits (from official docs at docs.bitvavo.com):**
- Default rate limit: 1,000 weight points per minute
- Each REST or WebSocket request costs a specific number of weight points (e.g., create order = 1 point)
- Rate limit info returned via HTTP headers: `bitvavo-ratelimit-limit`, `bitvavo-ratelimit-remaining`, `bitvavo-ratelimit-resetat`
- Exceeding the limit: authenticated users blocked for 1 minute (by API key); unauthenticated users blocked for 15 minutes (by IP)
- HTTP 429 response with errorCode 105
- WebSocket sessions limited to 5,000 messages per second
- Higher limits available on request for high-volume traders

**Kraken API rate limits (from official docs at docs.kraken.com):**
- Uses a "call counter" system (confirmed)
- Counter starts at 0; most calls increment by 1; ledger/trade history calls increment by 2
- AddOrder and CancelOrder use a separate limiter
- Maximum counter values by verification tier:
  - Starter: max 15, decay -0.33/sec
  - Intermediate: max 20, decay -0.5/sec
  - Pro: max 20, decay -1/sec
- If counter exceeds max, subsequent calls are rate limited

Both descriptions in the research document are accurate.

Sources:
- [Bitvavo API Docs - Rate Limits](https://docs.bitvavo.com/docs/rate-limits/)
- [Kraken API Center - Spot REST Rate Limits](https://docs.kraken.com/api/docs/guides/spot-rest-ratelimits/)
- [Kraken Support - API Rate Limits](https://support.kraken.com/articles/206548367-what-are-the-api-rate-limits-)

---

### Other Exchanges Worth Considering for Dutch Residents

**Exchanges not mentioned in the research document:**

**Finst (Dutch, AFM-regulated):**
- Netherlands-based exchange, registered with DNB (R189158)
- Flat 0.15% trading fee (no maker/taker distinction), no hidden spreads
- 340+ cryptocurrencies, free SEPA deposits/withdrawals
- First Dutch exchange with Proof of Reserves
- Trustpilot rating: 3.9/5 (245 reviews)
- **Limitation: No public trading API found.** Not suitable for algorithmic/automated trading
- Could be an alternative to Bitvavo for manual trading

**Crypto.com:**
- Obtained DNB registration on July 28, 2023
- Was fined EUR 2,850,000 by DNB for operating without registration from November 2020 to November 2022
- Available in NL; has an API for trading
- Fee structure competitive but more complex than Bitvavo

**DEGIRO (crypto trading via brokerage):**
- Launched direct crypto trading in NL in September 2025
- Limited to BTC and ETH initially
- Not suitable for algorithmic trading; more for stock investors wanting crypto exposure

**Binance: Still not available to Dutch residents.** No plans to return have been announced.

**Other MiCA-licensed exchanges accessible to Dutch users via EU passporting:**
- OKX, Bybit, and others have obtained MiCA licenses from various EU regulators
- However, for the project's specific needs (low fees, API access, EUR/SEPA), Bitvavo and Kraken remain the strongest choices

Sources:
- [Finst - About](https://finst.com/en/company)
- [Finst - Fee Schedule (PDF)](https://finst.com/api/documents/public/legal/fee-schedule/fee-schedule_en.pdf)
- [Crypto.com - Registration Approval in NL](https://crypto.com/en/company-news/crypto-com-secures-registration-approval-in-the-netherlands)
- [DNB - Fine for Foris DAX MT Limited (Crypto.com)](https://www.dnb.nl/en/general-news/enforcement-measures-2024/fine-for-foris-dax-mt-limited-crypto-com-for-having-provided-crypto-services-without-the-required-registration-until-2-august-2023-in-the-netherlands/)
- [DutchReview - Best crypto exchanges in the Netherlands 2026](https://dutchreview.com/expat/best-crypto-exchanges-in-the-netherlands/)
- [Coincub - Best Crypto Exchanges Netherlands 2026](https://coincub.com/countries/netherlands/)

---

## Summary of Recommended Changes to research-crypto-satellite.md

| # | Issue | Severity | Recommendation |
|:--|:------|:---------|:---------------|
| 1 | **Kraken base fees stated as 0.16%/0.26%** | **High** | **Correct to 0.25%/0.40% (official fee schedule). This changes the fee comparison significantly.** |
| 2 | **Coinbase Advanced base fees stated as 0.40%/0.60%** | **High** | **Correct to 0.60%/1.20% (Intro 1 base tier). Coinbase is even more expensive than stated.** |
| 3 | **Fee analysis table uses wrong Kraken/Coinbase fees** | **High** | **Recalculate round-trip costs and annual fee drag with correct base fees** |
| 4 | stETH yield stated as ~2.5% APR | Minor | Update to ~3.2-3.3% APY |
| 5 | Mean reversion allocated 20-30% despite weak evidence | Moderate | Reduce allocation or add explicit caveat that evidence is weak |
| 6 | BTC-S&P500 correlation described as simply "increased since 2020" | Moderate | Add nuance about late 2025 decoupling and regime-dependence |
| 7 | No mention of MiCA regulatory framework | Minor | Add note that both exchanges are MiCA-licensed (Bitvavo via AFM, Kraken via CBI) |
| 8 | Counterparty risk section lacks recent hack data | Moderate | Add Bybit hack ($1.4B, Feb 2025) as a concrete example |
| 9 | Trend-following evidence implies weekly is optimal | Minor | Clarify that weekly is a fee-driven compromise, not the academic optimum |
| 10 | No mention of overfitting/backtest reliability risks | Moderate | Add section on survivorship bias, regime change, and live performance gap |
| 11 | Funding rate arb returns may be declining | Minor | Note institutional compression trend |
| 12 | Missing spread costs and minimum order size analysis | Minor | Add to fee analysis section |
| 13 | Tooling section missing OctoBot and Hummingbot | Minor | Add as notable alternatives |
| 14 | Kraken regulatory status understated as "EU-compliant" | Minor | Update to "MiCA-licensed via Central Bank of Ireland, serves all 30 EEA countries" |
| 15 | Finst not mentioned as potential alternative | Minor | Consider adding Finst (0.15% flat fee, Dutch, no API though) |
| 16 | DNB fine amount for Coinbase not specified | Minor | Add: EUR 3,325,000 fine announced Jan 2023 |

### Corrected Fee Comparison Table

Using verified base tier fees, the corrected fee analysis at EUR 600 scale should be:

| Venue | Base Maker/Taker | Round-Trip Maker | Round-Trip Taker | Weekly Trading Annual Fee Drag (Taker) |
|:---|:---|:---|:---|:---|
| **Bitvavo** | 0.15% / 0.25% | 0.30% | 0.50% | ~26.0% (52 trades) |
| **Kraken** | **0.25% / 0.40%** | **0.50%** | **0.80%** | **~41.6% (52 trades)** |
| **Coinbase Adv.** | **0.60% / 1.20%** | **1.20%** | **2.40%** | **~124.8% (52 trades)** |

This correction **strengthens** the document's recommendation of Bitvavo as primary exchange. The fee gap between Bitvavo and Kraken is much larger than originally stated (0.25% round-trip taker difference, not 0.02%). Coinbase Advanced at base tier is essentially unusable for active trading on a small account.
