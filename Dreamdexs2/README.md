# dreamDEX Perps Builder Bounty — Track 2 (MVP)

**Planned build style:** Vektor-style quant terminal (funding-aware + liquidation guard + evidence of live orders).  
No paid credits required for the core path on Tokyo testnet (paper USDso / official SDK).

---

## Build Description (what Superfly will ship)

**Name (working):** Superfly Perps Terminal (or final name TBD)

A live Vercel-hosted quant terminal for dreamDEX Perps on Somnia Tokyo testnet (Hideki, chain ID 50383).

### Core idea (drawn from Vektor by @encrypt_wizard / NetLayer Labs)
A focused trading tool that:
- Runs simple, deterministic strategies (funding-aware grid or funding harvest + basic directional bias)
- Includes a liquidation / margin-health shield that trims or closes before the engine liquidates
- Places **real orders** on Tokyo testnet using a linked bot key (can trade, cannot withdraw)
- Shows live evidence: transaction hashes, fills, and a simple public proof view that re-reads from the indexer/SDK
- Keeps running on the server side after the tab is closed (autopilot-style)

### What it is **not**
- Not a Telegram bot
- Not a full multi-strategy institutional platform
- Not dependent on paid LLM credits for the core trading loop (deterministic logic preferred; any AI is optional/draft-only)

### Target user
Someone who wants a simple, observable way to run funding-aware or risk-guarded perps strategies on dreamDEX testnet and see real orders land.

### Evidence required by judges
- Live perps orders on Tokyo testnet (tx hashes)
- Repo with clear README
- 2–3 X posts tagging @DreamDEXSomnia

---

## Official Requirements (Track 2: MVP)

### What to build
A perps product (trading bot, AI agent, trader tool, or consumer perps app) that places **real orders** on Somnia Tokyo testnet.

Using Somnia Reactivity or Somnia Agents is a plus.

### Must-haves
- MVP places real perps orders on Tokyo testnet
- README explains:
  - What it does
  - Target audience
  - How to run it
  - **X posts** section with links to 2–3 posts about the MVP that tag [@DreamDEXSomnia](https://x.com/DreamDEXSomnia)
- GitHub/GitLab/Bitbucket repository required

### Judging criteria
1. **MVP Potential** — clear user value, credible scope, viral/repeat-use loop, technical execution
2. **Evidence of Building** — live orders on testnet, transaction hashes, repo, demo
3. **Communication** — quality and accuracy of the X posts

### Prizes
- 3 winners × $500 each
  - $300 on announcement
  - $200 after perps mainnet launch (if MVP places orders within 30 days of launch)
- Winners get a technical breakdown post on the dreamDEX X account

### Timeline (UTC)
- Opened: October 19, 2026
- Original deadline: November 1, 2026 23:59
- **Extended deadline: November 15, 2026 ~14:30**
- Results: by November 8 (original) / after extension

### Access
- Pre-whitelisted emails from the previous Event Contracts hackathon can submit
- Others: request via [dreamDEX Discord](https://discord.gg/dreamdex) or [SomniaHacks Telegram](https://t.me/+s_oRMnGpOyQ3ODQ0)

### Testnet funds
- Use Perps Arena balance at [app.testnet.dreamdex.io](https://app.testnet.dreamdex.io) for paper USDso
- Additional funds on request via Discord (restrictions apply)

---

## Official Links & Resources

### Hackathon
- DoraHacks page: https://dorahacks.io/hackathon/dreamdex-perps-bounty/detail
- dreamDEX Discord: https://discord.gg/dreamdex
- SomniaHacks Telegram: https://t.me/+s_oRMnGpOyQ3ODQ0
- dreamDEX X: https://x.com/DreamDEXSomnia

### Developer docs & tools
- Perps on testnet (developers): https://app.testnet.dreamdex.io/docs/developers/perps-testnet
- Perps on testnet (traders): https://app.testnet.dreamdex.io/docs/trading/perps-testnet
- dreamDEX bot kit (includes perp strategies): https://github.com/somnia-chain/dreamdex-bot-kit
- dreamBot Builder: https://app.testnet.dreamdex.io/dreambot-builder
- Link a Bot guide: https://app.testnet.dreamdex.io/docs/trading/common/link-a-bot
- Somnia Markets SDK docs: https://somnia-platform-docs.vercel.app/markets/somnia-markets

### Network (Tokyo / Hideki)
- Chain ID: **50383**
- RPC: https://api.hideki2.infra.testnet.somnia.network
- WebSocket: wss://api.hideki2.infra.testnet.somnia.network/ws
- Indexer (GraphQL): https://hideki-dev.smk.somnia.host/v1/graphql
- Explorer: https://explorer.testnet.somnia.network/tokyo

### Key contracts (from official docs)
- MarginBank, Collateral (USDso), PerpPoolFactory, LiquidationEngine, etc. — pull live addresses from the SDK / market rows.

---

## What the serial winners used that matters here

### From Vektor (@encrypt_wizard / NetLayer Labs — Strike Perps)
- Session / API keys that can trade but **cannot withdraw**
- Deterministic engines (funding-aware grid, funding harvest, liquidation shield)
- Server-side autopilot that continues after the user closes the tab
- Public proof page that re-reads fills from the exchange’s own API (not just screenshots)
- Live mainnet fills + clear evidence
- Tests around the core logic

### From Cadence (@dreyethh — Strike Perps)
- Clear “Ready / Smaller size / Cannot execute” feedback against live state
- Bounded orders with native stops
- Receipts built from the venue’s own fills
- Separation: AI can draft, deterministic code decides and executes
- Live web app + mainnet order IDs

### Practical takeaways for this build
- Use a **linked bot key** in the dreamDEX app (official “Link a Bot” flow)
- Prefer the official `@somnia-chain/markets-sdk` and bot-kit patterns
- Show tx hashes and a simple re-read proof view
- Keep risk logic deterministic and observable
- Deploy the web UI to Vercel; keep order placement on a reliable backend if needed for autopilot

---

## Previous related event (for context)
- dreamDEX Event Contracts Hackathon (Aug–Sep 2026)
- Top 10 winners each received $500 (ForeSight, Harvest-Call, Autoroll, Masayume, DreamPulse, HOUSE, Ropes, Decedo, Lucid, Market Royale)
- Strong patterns: clear user value, real SDK/API integration, live evidence, on-chain automation or polished consumer UX

---

## Notes
- This is documentation only. No implementation is included in this folder.
- Superfly will dictate the final UI.
- Deadline is extended to **November 15, 2026**.
- Pre-whitelisted from the previous hackathon.
