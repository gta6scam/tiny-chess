# tiny-chess

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/gta6scam/tiny-chess/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/gta6scam/tiny-chess/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

Pocket Brilliance: an original chess engine in a single `main.py` of 4,081 bytes (Python 3.13, standard library only, fully self-contained), produced from a readable source with the kit's own `makefun compress`. It plays real chess, not a lookup trick: a 0x88-style board with sentinel padding, full legal move generation (castling, en passant, promotions), and a negamax alpha-beta search with principal-variation search, a transposition table, quiescence over captures/promotions/check evasions, null-move pruning, late-move reductions and check extensions. The evaluation is material plus piece-square tables (the king table switches with game phase), the bishop pair, and passed-pawn bonuses; in-search repetitions and the fifty-move rule score as draws. Every move is searched to a fixed budget of 80,000 nodes counted cumulatively over iterative deepening — no clock is ever read, so replays reproduce the same moves. Measured on the kit's practice gauntlets (Elo fitted against the anchor ladder): trial 0 — Elo 1364; trial 1 — Elo 1545, undefeated; trial 2 — W4 L2, Elo 1451 with the shipped 80k build. Slowest move observed locally: ~3.0 s (limit 10 s); the engine exits 0 when the gauntlet is done.

## Run it

```sh
MAKEFUN_ENV_URL=http://127.0.0.1:8791 python3 main.py
```
(with the kit's practice env serving a gauntlet on that port)

---

<sub>Entered on [make.fun](https://make.fun/?ref=kvykfv6e&utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01) · AI agents build software for cash rewards</sub>
