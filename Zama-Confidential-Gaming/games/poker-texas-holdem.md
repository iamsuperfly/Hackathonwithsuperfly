# Texas Hold’em Poker — Complete Rules + FHE Adaptation Notes

**Players**: 2–10 per table  
**Deck**: Standard 52-card deck (no jokers)  
**Goal**: Win the pot by having the best five-card hand at showdown or by making all other players fold.

---

## Core Structure

Each player receives **2 private hole cards** (face down).  
**5 community cards** are dealt face up in the center (shared by everyone):
- Flop: 3 cards
- Turn: 1 card
- River: 1 card

Players make the **best 5-card poker hand** from their 2 hole cards + the 5 community cards (using both, one, or neither of their hole cards).

### Betting Structure (typical No-Limit)
There are **4 betting rounds**:
1. **Preflop** — after hole cards are dealt
2. **Flop** — after the first 3 community cards
3. **Turn** — after the 4th community card
4. **River** — after the 5th community card

**Forced bets (Blinds)**:
- Small Blind (usually half the big blind) posted by the player left of the dealer button
- Big Blind posted by the next player
- Button rotates clockwise each hand

### Player Actions
On your turn you can typically:
- Fold
- Check (if no bet to call)
- Call
- Bet / Raise (up to all-in in No-Limit)

### Showdown
If two or more players remain after the river betting round, they reveal their hole cards. Best hand wins the pot. If everyone else folds earlier, the last remaining player wins without showing cards.

### Hand Rankings (best to worst)
1. Royal Flush
2. Straight Flush
3. Four of a Kind
4. Full House
5. Flush
6. Straight
7. Three of a Kind
8. Two Pair
9. One Pair
10. High Card

---

## Why This Fits Zama / FHE Perfectly

Hole cards must stay private. On a public blockchain every player’s cards would be visible to everyone, destroying the game.

**FHE advantages**:
- Deal hole cards as encrypted values (`euint8` representing card 0–51).
- Only the owner can decrypt their own hole cards (`FHE.allow`).
- Community cards can be public (or encrypted until revealed if desired).
- Hand evaluation can be performed (or partially performed) on encrypted data for showdown comparison.
- Betting amounts can also be confidential if desired (using confidential tokens).
- On-chain encrypted randomness for fair dealing.

**Implementation notes**:
- Card dealing via encrypted random + modulo 52.
- Selective reveal only at showdown or when a player is forced to show.
- Multiple existing FHE poker explorations exist (Labz docs, various GitHub repos).

---

## Sources for Rules
- UltraGambler, PokerSkill, PokerWired, PokerCoaching, Pokerfuse, World Poker Federation, Sporting News, etc.

*Standard Texas Hold’em rules. Betting limits and exact house rules can be customized.*
