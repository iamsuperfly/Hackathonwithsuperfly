# Liar’s Dice — Complete Classic Rules + FHE Adaptation Notes

**Also known as**: Perudo, Dice Bluff, etc.  
**Players**: 2–6 (best with 3+)  
**Dice**: Usually 5 dice per player + one opaque cup per player  
**Goal**: Be the last player with at least one die remaining.

---

## Core Rules (standard multi-player version)

### Setup
- Each player receives 5 dice and one opaque cup.
- Decide starting player (highest roll of 2 dice, rock-paper-scissors, or agreement).

### Round Structure
1. **Roll and Hide**: All players simultaneously shake their 5 dice in their cups and carefully invert the cups so the dice are hidden under the cups. Each player may look at their own dice at any time but must keep them hidden from others.
2. **Opening Bid**: The starting player makes a bid claiming a certain quantity of a specific face value across *all* dice on the table (including opponents’ hidden dice). Example: “Three 5s” means “I claim there are at least three dice showing 5 among all players’ dice.”
3. **Raising the Bid**: Subsequent players must either:
   - Raise the bid (higher quantity of the same face, or same/higher quantity of a higher face), or
   - Challenge the previous bid (“Liar!”, “Open!”, “Call!”).
4. **Challenge Resolution**:
   - All players reveal their dice.
   - Count the actual number of the bid face (some variants treat 1s as wild).
   - If the actual count is **≥** the bid → bidder was correct → challenger loses one die.
   - If the actual count is **<** the bid → bidder was lying → bidder loses one die.
5. Player who loses a die starts the next round (or previous winner starts — house rule).
6. Continue until only one player has dice left. That player wins.

### Common Variants
- **1s as wild**: Ones can count as any face (except when the bid is specifically on 1s in some rulesets).
- **Spot On**: Additional challenge option claiming the bid is exactly correct (higher risk/reward).
- **Common hand**: Shared set of dice passed around (less common for on-chain).
- **Drinking game versions**: Loser drinks; same core bluffing mechanic.

### Bidding Rules (typical)
- Must increase either the quantity or the face value (or both).
- Cannot decrease the quantity when keeping the same face, etc. Exact raising rules vary slightly by edition.

---

## Why This Fits Zama / FHE Perfectly

The entire game revolves around private information: each player’s dice under their cup are hidden from everyone else. On a public blockchain this would be impossible without encryption.

**FHE advantages**:
- Each player’s dice rolled on-chain using `FHE.randEuint8()` (or similar) and stored encrypted.
- Only the owner can decrypt their own dice (via `FHE.allow` to their address).
- When a challenge occurs, the contract can count matching faces across all encrypted dice without revealing individual dice.
- Only the final true/false result of the challenge (or the exact count if desired) is publicly decrypted.
- Loser loses a die (state update remains confidential where needed).

**Existing examples / inspiration**:
- “Sealed Bluff” (AzrarM on X) — Liar’s Dice on Zama FHEVM for this exact Season 5.
- Various JS Liar’s Dice implementations for logic reference.

---

## Sources for Rules
- UltraBoardGames, Geeky Hobbies, WikiHow, Group Games 101, Dice Game Depot, The Gamer (Liar’s Bar), House of Games, etc.

*Compiled from standard published rulesets. Variants exist — choose one consistent ruleset for implementation.*
