# Fog of War Chess (Dark Chess / Implicit Fog)

Classic incomplete-information chess. You only see the squares your own pieces can legally reach (plus the squares they stand on). Everything else is fog. Opponent pieces and moves stay hidden until they interact with your vision or capture something you own.

**Why this fits Zama Season 5 Confidential Gaming**  
Normal chess is complete information — the full board is public. Fog of war makes the true board state private. On a transparent chain everyone would just read the contract and see the opponent’s pieces. FHE keeps the true piece positions encrypted; each player only decrypts what their own pieces can see. Captures and vision updates are resolved on ciphertext. The game only works because the state can stay encrypted.

It turns chess into a game of peak curiosity and information warfare: you are constantly probing, bluffing, and trying to reconstruct the opponent’s board from limited observations. Kings can be captured with no check warning. Castling can happen out of, through, or into “check” because neither side necessarily knows the king is attacked.

## Rules (Mistboard / standard Dark Chess variant)

Invented 1989 by Jens Bæk Nielsen and Torben Osted. Implicit-fog version: no umpire, no separate scan action. Visibility is derived from where your pieces can legally move under normal chess rules.

### Visibility
- Each side sees the squares its own pieces could legally move to + the squares they currently occupy.
- Everything else is fog (hidden).
- Vision moves with the pieces. When a piece moves, previously covered squares go dark unless another piece still sees them; newly reached squares light up.
- A piece’s vision ends where its movement ends (e.g. a rook on d7 sees b7 and h7 but not a7 if blocked).

### Win condition
- Capture the opponent’s king. No check, no checkmate, no warning. The game ends the moment a king is captured.

### Draws
- Threefold repetition (same true position three times, same side to move, same castling/en-passant rights).
- 50-move rule (fifty full moves with no pawn move or capture).
- Side with no legal moves at all (every piece blocked) draws.
- No insufficient-material draw. You must move even if every move walks into attack.

### Special cases
- **Castling**: Allowed out of, through, or into check (because the king may be attacked without either side knowing).
- **Pawn vision**: Pawns see forward push squares only when empty. They see diagonal squares only when an enemy piece is actually there to capture. Blocked pawn squares are not revealed in the Mistboard ruleset.
- **En passant**: The capturing pawn sees the enemy pawn on the adjacent square for that one-move window. Pass on it and the chance is gone.
- **Promotion**: Normal (usually to queen; some implementations force queen).

### What stays public vs encrypted
- Public: whose turn it is, game status, move history of visible interactions, stake if any.
- Encrypted: true positions and types of all opponent pieces outside your vision. Your own pieces are known to you.

## FHE Adaptation Pattern (Zama fhEVM)

- Store each piece (type + color + square or a compact board encoding) as encrypted values (`euint8` / `euint16` etc.).
- On a move attempt: contract validates legality against the mover’s known pieces and encrypted opponent pieces (using FHE comparisons, selects, and conditionals).
- Visibility / observation: after a move, compute the new vision set for the mover on ciphertext and only allow that player to decrypt the revealed squares/pieces.
- Captures: when a piece lands on an encrypted opponent piece, resolve the capture on ciphertext and reveal only the result to the relevant player(s).
- King capture: special check that ends the game; reveal the capture outcome with proof.
- Use `FHE.allow` / `FHE.allowThis` for ACL so only the owner can user-decrypt their private view. Public decryption only for final outcomes or agreed reveals.
- Randomness not required for core rules, but can be used for optional variants (e.g. fogged starting positions).
- Timeouts / turn timers can be added the same way as in other confidential games.

**Frontend**: React + Vite + wagmi/viem + Zama SDK. Board UI shows only the player’s visible squares; fog covers the rest. Move input is normal algebraic or click; contract rejects illegal moves.

## Resources (open source / playable)

- Mistboard (play live + rules): https://mistboard.com/rules/dark-chess and https://mistboard.com
- Misty engine (open-source fog-of-war chess engine, exact belief enumeration + GT-CFR): https://github.com/brianhliou/misty
- Kriegspiel.org platform (related hidden-information chess, multiple rulesets): https://kriegspiel.org and https://github.com/Kriegspiel
- Other implementations: https://github.com/AHAPX/dark-chess , https://github.com/c0nrad/darkchess , https://github.com/tsujp/tikan (Noir/ZK version)

## Older Zama note
A previous-season PoC called “Shadow Arena” explored fog-of-war style chess on FHE (Builder Track / Season 2 era). No public Season 5 submission of this concept was found at time of writing. This is a classic real game that has not been saturated for the current confidential gaming track.

## Why it is peak curiosity
You never have a complete picture. Every move is a probe. You can set traps, sacrifice vision to hide a piece, or castle into unknown danger. Opponents must reason about possible boards consistent with what they have observed. The psychological and information-asymmetry layer is stronger than standard chess while still using rules people already understand.
