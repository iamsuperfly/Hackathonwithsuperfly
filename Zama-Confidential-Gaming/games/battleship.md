# Battleship — Complete Classic Rules + FHE Adaptation Notes

**Players**: 2  
**Age**: 7+  
**Time**: ~20–40 minutes  
**Goal**: Sink all five of the opponent’s ships before they sink yours.

---

## Official / Classic Rules Summary

Each player has two 10×10 grids:
- **Ocean grid** (lower / own fleet): where you place your ships secretly
- **Target grid** (upper / tracking): where you record your shots against the opponent

Rows are labeled A–J, columns 1–10.

### Fleet (standard sizes — 17 squares total)

| Ship          | Length (squares) | Notes                          |
|---------------|------------------|--------------------------------|
| Carrier       | 5                | Largest                        |
| Battleship    | 4                |                                |
| Cruiser / Destroyer | 3           | Name varies by edition         |
| Submarine     | 3                |                                |
| Destroyer / Patrol Boat | 2       | Smallest                       |

**Placement rules**:
- Ships placed horizontally or vertically only (never diagonally)
- Cannot overlap
- Whether ships may touch edge-to-edge is often left to house rules (official rules usually allow it)

### Setup
1. Each player secretly places their five ships on their ocean grid.
2. Boards are oriented so the opponent cannot see the placements.
3. Decide who goes first (youngest, coin flip, etc.).

### Gameplay
1. On your turn, call one coordinate (e.g., “D-4” or “B7”).
2. Opponent checks their ocean grid and answers truthfully:
   - **“Miss”** — no ship there
   - **“Hit”** — a ship occupies that square (sometimes also names the ship)
3. You mark the result on your target grid (white/green peg for miss, red peg for hit).
4. Opponent marks the shot on their ocean grid.
5. When every square of a ship has been hit, the owner must announce “You sunk my [Ship Name]!”
6. Turns alternate. One shot per turn (classic rules). No bonus shots for hits in standard play.

### Winning
The first player to sink all five of the opponent’s ships wins.

### Variants
- **Salvo**: Fire multiple shots equal to the number of ships you still have afloat.
- Advanced / house rules on touching ships, announcing ship type on hit, etc.

---

## Why This Fits Zama / FHE Perfectly

On a public blockchain the opponent’s ship placements would be fully visible to everyone. The entire point of Battleship is that the fleet is hidden until discovered through shots.

**FHE advantages**:
- Ship placements stored as encrypted values (e.g., encrypted bitmasks or coordinates per ship).
- Shots are public calls of coordinates.
- Contract can compute hit/miss and “sunk” status on encrypted data without revealing the full board.
- Selective decryption: only the relevant hit/miss result is revealed (or the ship type when fully sunk).
- On-chain randomness not strictly required for classic Battleship (pure strategy + deduction), but can be used for variants.

**Potential implementation approach**:
- Represent each player’s board as an encrypted array or set of ship positions.
- Use FHE equality / select operations to check if a called coordinate matches any ship segment.
- Track hits on encrypted counters per ship.
- Reveal only the boolean hit/miss (and sunk announcements) via public decryption when appropriate.

**Existing open-source references** (for logic inspiration, not Zama-native):
- Various Battleship implementations on GitHub (search “battleship solidity” or “battleship-fhevm”).
- Classic paper/board game logic is simple and well-defined.

---

## Sources for Rules
- officialgamerules.org, wargamer.com, battleships.io, Hasbro/Milton Bradley editions, Geeky Hobbies, WikiHow, etc.

*Rules compiled from multiple standard sources. Always verify against a specific edition if exact wording is needed.*
