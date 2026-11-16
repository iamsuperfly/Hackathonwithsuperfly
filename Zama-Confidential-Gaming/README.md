# Zama Developer Program Season 5: Confidential Gaming

**Documentation and planning notes for Superfly’s entry.**

This folder contains everything needed to understand the hackathon and the candidate games (Battleship, Liar’s Dice, Texas Hold’em Poker, Blackjack). No code is included here — documentation only.

---

## Quick Links

- **Official announcement**: https://www.zama.org/post/zama-developer-program-mainnet-season-5-confidential-gaming
- **Submission form**: https://forms.zama.org/zama-developer-program-mainnet-season-5-confidential-gaming
- **X post announcing it**: https://x.com/zama/status/2119804779509485847
- **Zama Protocol docs**: https://docs.zama.org/protocol
- **Hardhat template**: https://github.com/zama-ai/fhevm-hardhat-template
- **Encrypted random numbers**: https://docs.zama.org/protocol/solidity-guides/smart-contract/operations/random
- **OpenZeppelin Confidential Contracts**: https://github.com/OpenZeppelin/openzeppelin-confidential-contracts
- **Testnet Confidential Token Registry**: https://docs.zama.org/protocol/protocol-apps/addresses/testnet/sepolia

---

## Folder Contents

| File | Purpose |
|------|---------|
| `hackathon-details.md` | Full extracted official details, requirements, judging, rewards, resources |
| `games/battleship.md` | Complete classic Battleship rules + FHE adaptation notes |
| `games/liars-dice.md` | Complete Liar’s Dice rules + FHE adaptation notes |
| `games/poker-texas-holdem.md` | Complete Texas Hold’em rules + FHE adaptation notes |
| `games/blackjack.md` | Complete Blackjack rules + FHE adaptation notes |
| `fhe-adaptation-notes.md` | Cross-game technical notes on using fhEVM / FHE for these games |
| `resources.md` | All official and useful developer resources in one place |

---

## Core Challenge (summary)

Build a **confidential game** on the Zama Protocol (fhEVM / FHE) deployed to **Sepolia testnet**. The game must only make sense because its state can stay encrypted — something impossible on a fully transparent blockchain.

Key themes from Zama:
- Hidden hands / encrypted game states
- Verifiable fairness (on-chain randomness)
- Games people actually want to play
- FHE working is the entry ticket; fun is the goal

---

## Submission Requirements (must-haves)

1. Smart contract + frontend
2. Clear documentation
3. 3-minute video pitch (**real-person pitch only** — AI-generated video or voice will not be considered)
4. X post introducing the project

**Deployed on Sepolia testnet.** Working demo preferred.

---

## Judging Criteria (high-level)

- Gameplay and UX
- Confidentiality design (does it matter that state is encrypted?)
- Fairness (on-chain randomness + verifiability)
- Functionality (full round playable on Sepolia)
- Demo quality (3-min video)
- Code quality

---

## Rewards

**5,000 cUSDT total** (confidential USD, ERC-7984 powered by Zama Protocol), distributed across up to 3 winners:

- 1st: 2,500 cUSDT
- 2nd: 1,500 cUSDT
- 3rd: 1,000 cUSDT

Distribution may be adjusted based on quality of submissions.

---

## Candidate Games Chosen for Analysis

These are classic real games (not pre-built Zama examples) that benefit from confidentiality:

1. **Battleship** — hidden ship placements
2. **Liar’s Dice** — hidden dice under cups
3. **Texas Hold’em Poker** — private hole cards
4. **Blackjack** — dealer’s hole card + player hands

Full rules and adaptation thinking are in the `games/` subfolder.

---

*Created for Superfly’s planning. Update as the build progresses.*
