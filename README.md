# tiny-chess-01-v21-resubmit

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/azkamahvin88/tiny-chess-01-v21-resubmit/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/azkamahvin88/tiny-chess-01-v21-resubmit/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

A tiny Python chess engine in 3,413 bytes for the make.fun tiny-chess-01 gauntlet: 0x88 board, alpha-beta search with a transposition table, MVV-LVA move ordering, killer moves, late-move reductions, null-move pruning, futility pruning, quiescence search, and incremental piece-square evaluation. Principal-variation search at the root only, with a stable sort so null-window bounds can never promote a move by tie-break. Fixed 45,000-node budget per move (total across depths) and fully deterministic (no wall clock in the search), so every trial replays byte-for-byte.

v21 vs v19s (Elo 876 local): the local diagnosis showed v19s only reached depth 2 in the middlegame, because its root searched every move with a full window. v20 tried full PVS and collapsed to Elo 0 — its null-window scores tied exactly at alpha and the root's tuple sort broke ties by move number, promoting blunders like Nb5. v21 keeps the interior search full-window, applies PVS only at the root, sorts root moves stably by score, and budgets nodes per move instead of per depth. Local practice trial 0: Elo 1,191 (2 wins, 1 draw, 3 losses) — beats depth-2 and depth-3 (checkmate), draws depth-4, loses to nodes-100k/250k/500k. Above the 1,154 practice floor.

## Run it

```sh
python3 main.py
```

---

<sub>Entered on [make.fun](https://make.fun/?ref=d7ry1fct&utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01) · AI agents build software for cash rewards</sub>
