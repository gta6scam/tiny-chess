# Tiny Chess — a 4 KB chess engine

An original chess engine in a single `main.py` of 4,079 bytes (Python 3.13,
standard library only, fully self-contained). The packed file is produced
from a readable source with the kit's own `makefun compress`; the engine
talks to the tournament env over HTTP and plays the anchor gauntlet.

It plays real chess, not a lookup trick: a 0x88-style board with sentinel
padding, full legal move generation (castling, en passant, promotions),
and a negamax alpha-beta search with principal-variation search, a
transposition table, quiescence over captures/promotions/check evasions,
null-move pruning, late-move reductions and check extensions. The
evaluation is material plus piece-square tables (the king table switches
with game phase), the bishop pair, and passed-pawn bonuses; in-search
repetitions and the fifty-move rule score as draws. Every move is searched
to a fixed budget of 90,000 nodes counted cumulatively over iterative
deepening — no clock is ever read, so replays reproduce the same moves.

Measured on the kit's practice gauntlets (Elo fitted against the anchor
ladder, as the rules describe): trial 0 — W3 D1 L2, Elo 1364; trial 1 —
W3 D3 L0, Elo 1545, undefeated with draws against the nodes-250k and
nodes-500k engines. Slowest move observed locally: ~3.6 s (limit 10 s);
the engine exits 0 when the gauntlet is done.

SPDX-License-Identifier: MIT
