# Finance / trading cluster

yibie/awesome-jev only listed four finance entries. The attached inventory is larger. Biggest missing ancestor: **jarrodwatts/jev-trader**.

User handle on this session is `nuburo_fx` — this cluster is the one most adjacent to FX/crypto infra. Still: almost everything paper-trades or dry-runs unless you add keys on purpose.

## Two shapes

1. **Sub-second crypto loops**  
   Compress the book into a tiny state → one Choice per tick/block → code places or papers the order.  
   Watts is the ancestor. Hyperliquid, Kraken, Bitget, and the Python market-maker are variations.

2. **Slower equity / options / research desks**  
   Richer evidence (Valyu, tweets, HK panels, NQ L10, options chains) → Jev answers direction or quality → a separate policy owns size and risk.

Repeated design idea: **Jev judges, code trades.**

## Live / intended-live loops

- [jarrodwatts/jev-trader](https://github.com/jarrodwatts/jev-trader) — every Monad block (~300 ms) Jev reads Kuru MON-USDC and answers buy or sell; bot posts a post-only limit one tick inside the touch. Dry-run by default; live needs a private key. ~1.8k★.
- [buberlo/jev-trader](https://github.com/buberlo/jev-trader) — Python rebuild. Jev answers six atomic judgments (regime, direction, toxic flow, liquidity stress, quote environment, inventory pressure). Code owns Avellaneda-Stoikov pricing plus hard risk vetoes.
- [aowang-ai/jev-trade](https://github.com/aowang-ai/jev-trade) — Hyperliquid long/short Choice each round (already in yibie list). Thin namesake: djascorp/jev-trade, skip.
- [maxlibin/moomoo-jev-trader](https://github.com/maxlibin/moomoo-jev-trader) — US equities via Moomoo OpenD every five seconds (up/sideways/down + entry quality), optional confidence-gated send to sim or live.
- [Nachom3/jevTrader](https://github.com/Nachom3/jevTrader) — Rust HFT-shaped trader with Jev as decision maker.

## Paper / backtest desks

- [justinhe16/trade-jev](https://github.com/justinhe16/trade-jev) — NQ L10 Databento days, BUY/SELL/HOLD, stored answers replayable under new stops at no extra API cost
- [tyleree/jevbot](https://github.com/tyleree/jevbot) — Alpaca paper-only options; maths/sizing/risk in code; live backtest loop not finished
- [rthomas24/jev-realtime-trading](https://github.com/rthomas24/jev-realtime-trading) — Electron, up/down/flat every second, never real money
- [zzsong1023/jev-market-reflex](https://github.com/zzsong1023/jev-market-reflex) — Kraken BTC/ETH/SOL compressed state
- [zadescoxp/Jev-Trades](https://github.com/zadescoxp/Jev-Trades) — Yahoo 1-minute candles, simulated portfolio
- [pininkara/Jev-Trades](https://github.com/pininkara/Jev-Trades) — Bitget USDT-perp public candles, no authenticated orders
- [web3w/jev-trader](https://github.com/web3w/jev-trader) — dashboard over Kuru + Hyperliquid, simulated
- [Errr0rrr404/jev-trader](https://github.com/Errr0rrr404/jev-trader) — Robinhood Agentic MCP tape, Jev votes, simulate by default
- [rikkooo/jev-trade](https://github.com/rikkooo/jev-trade) — freeze Jev’s typed view before the outcome, score paper rules
- [adebmbng/jev-trade-prediction](https://github.com/adebmbng/jev-trade-prediction) — 5-minute BTC/ETH long/short/wait
- [Gamma-Software/jev-signals-lab](https://github.com/Gamma-Software/jev-signals-lab) — one snapshot, twelve independent questions, in-code BUY gate
- [UditJain2622004/Jev-Trading](https://github.com/UditJain2622004/Jev-Trading) — SOL grid / buy-the-dip, CSV log
- [IslamBaraka90/jev-typesafe-real-financial-use-cases](https://github.com/IslamBaraka90/jev-typesafe-real-financial-use-cases) — fifty graded demos + daily-candle backtester
- [OpenByteInc/QuantDinger](https://github.com/OpenByteInc/QuantDinger) — pre-existing trading OS; Jev is an optional pre-trade gate in front of its LLM gate, not the product

Already in yibie finance category (keep them): unicodeveloper/jevocks (Jevinik), sosopop/jev_stock, brainstormity/Jev-X-Sentiment-Analysis.

## Do not put in this category

- simonmesmith/jev-banking77-experiment, adilmoujahid/jev-banking77-demo — banking *intent* classification
- kyotofin/tax-doc-classifier — IRS form pages
- Straight Watts forks / empty stubs: jwallio/jev-trader, tradingbotswapmeet/JEV-Trader

## If we clone one finance repo later

Clone Watts first. It is the loop people copy. Then buberlo if you want “six atomic judgments + code owns pricing.”
