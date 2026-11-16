# FHE Adaptation Notes for Candidate Games

High-level technical thinking for implementing these games on Zama fhEVM / Protocol.

---

## Common Patterns Across Games

1. **Encrypted State**
   - Use `euint8`, `euint16`, etc. for cards, dice faces, board positions, ship segments.
   - Store in mappings or arrays inside the contract.

2. **Selective Access Control**
   - `FHE.allow(ciphertext, playerAddress)` so only the legitimate owner can decrypt their private data (own dice, own hole cards, own ships).
   - Do **not** allow the contract or other players until a deliberate reveal moment.

3. **On-chain Randomness**
   - `FHE.randEuint8()` (or similar) + `FHE.rem` / `FHE.add` to generate fair dice (1–6) or cards (0–51).
   - No external oracles needed for randomness.

4. **Computation on Encrypted Data**
   - Hit/miss checks: `FHE.eq`
   - Counting dice faces: encrypted addition / selection
   - Hand totals / comparisons: encrypted arithmetic + comparisons
   - Conditional logic: `FHE.select`

5. **Controlled Decryption**
   - Public decryption (via gateway / KMS) only for the minimal information needed (hit/miss boolean, challenge result, final winner, sunk announcement).
   - Avoid leaking individual private values unless the game rules require it.

6. **Confidential Tokens (optional)**
   - Use ERC-7984 / cUSDT or custom confidential chips for bets and payouts so bet sizes can also stay private if desired.

---

## Game-Specific Mapping

### Battleship
- Ships: encrypted positions or bitmasks.
- Shot: public coordinate.
- Contract returns encrypted hit/miss → public decrypt the boolean only.
- Sunk detection: encrypted counters per ship.

### Liar’s Dice
- Each player’s 5 dice: encrypted array, allowed only to that player.
- Bid: public (quantity + face).
- Challenge: contract counts matching faces across all encrypted dice → decrypt only the comparison result (or exact count).

### Texas Hold’em
- Hole cards: encrypted, allowed only to owner.
- Community cards: can be public once dealt.
- Showdown: evaluate hands (or compare encrypted ranks) and decrypt only the winner determination.

### Blackjack
- Dealer hole card: encrypted, no allow until stand / end of hand.
- Player cards: encrypted + allow to player.
- Dealer AI (hit until ≥17): runs entirely on encrypted totals.
- Final payout: based on encrypted comparison of totals.

---

## Recommended Starting Points

- Official Hardhat template: https://github.com/zama-ai/fhevm-hardhat-template
- Quick Start Tutorial: https://docs.zama.org/protocol/solidity-guides/getting-started/quick-start-tutorial
- Encrypted random numbers guide: https://docs.zama.org/protocol/solidity-guides/smart-contract/operations/random
- OpenZeppelin Confidential Contracts for tokens if needed.

---

## Practical Tips

- Start with a minimal viable encrypted loop (e.g., deal one encrypted card and let owner decrypt it).
- Write thorough tests in mock mode first.
- Keep the frontend simple: player sees only what they should see after decryption.
- Document the confidentiality design clearly — judges explicitly look for “Would the game break if the state were public?”
- Prioritize fun and UX over maximum complexity.

*These notes are planning aids only. Implementation decisions belong to Superfly.*
