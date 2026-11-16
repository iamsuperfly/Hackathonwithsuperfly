# Blackjack — Complete Standard Rules + FHE Adaptation Notes

**Also known as**: 21  
**Players**: 1+ vs the Dealer (house)  
**Goal**: Get a hand total closer to 21 than the dealer without going over 21.

---

## Core Rules (American-style with hole card)

### Card Values
- 2–10: Face value
- Jack, Queen, King: 10
- Ace: 1 or 11 (player’s choice; “soft” hand when Ace counts as 11)

### Deal
1. Players place bets.
2. Each player receives 2 cards face up.
3. Dealer receives 2 cards: one face up (upcard), one face down (**hole card**).

### Player Actions
- **Hit**: Take another card.
- **Stand**: Keep current total.
- **Double Down**: Double the bet and take exactly one more card.
- **Split**: If dealt a pair, split into two hands (with additional bet).
- **Surrender** (where offered): Forfeit half the bet and end the hand early.
- **Insurance** (when dealer shows Ace): Side bet that dealer has blackjack (pays 2:1).

### Dealer Rules
- Dealer has no choices.
- Must hit on 16 or less.
- Stands on 17 or higher (S17 = stands on soft 17; H17 = hits soft 17 — varies by table).

### Outcomes
- Player busts (>21) → player loses immediately.
- Dealer busts → all remaining players win.
- Higher total closer to 21 wins.
- Tie (push) → bet returned.
- Natural Blackjack (Ace + 10-value on first two cards) usually pays 3:2.

### Peek
If dealer shows Ace or 10, they usually peek at the hole card for blackjack before players act.

---

## Why This Fits Zama / FHE Perfectly

The dealer’s hole card is the classic hidden information. Players must make decisions without knowing the full dealer hand. On a public blockchain the hole card would be visible.

**FHE advantages**:
- Dealer’s hole card generated and stored encrypted.
- Player cards can be encrypted and only decryptable by the player.
- Contract can compute totals, bust checks, and dealer’s mandatory hit/stand logic entirely on encrypted values.
- Only the final outcome (win/loss/push) and necessary reveals are decrypted.
- On-chain encrypted randomness for card draws.

**Existing examples**:
- Cipher21 (manoahLinks) — Confidential Blackjack on Zama Protocol.
- Various FHE Blackjack implementations and casino platforms (e.g., skycasino).

---

## Sources for Rules
- Wizard of Odds, Blackjack Duck, BlackjackInfo, Casino.com, BestOnlineCasino, Wizard of Vegas, etc.

*Standard casino rules. Table-specific rules (H17/S17, number of decks, double/split restrictions, etc.) can be chosen for the on-chain version.*
