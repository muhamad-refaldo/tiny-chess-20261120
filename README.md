# Tiny Chess — a 4KB chess engine

[![make.fun](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/c/tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/muhamad-refaldo/tiny-chess-20261120/rank.svg)](https://make.fun/c/tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/muhamad-refaldo/tiny-chess-20261120/reward.svg)](https://make.fun/c/tiny-chess-01)

A chess engine in a single `main.py` of at most 4,096 bytes, written from
scratch in pure Python 3 stdlib for the
[make.fun tiny-chess-01 bounty](https://make.fun/c/tiny-chess-01).

It plays the house gauntlet through the trial environment (`MAKEFUN_ENV_URL`):
negamax alpha-beta with iterative deepening to a fixed node budget,
quiescence search, a transposition table, killer moves, a history heuristic,
null-move pruning, late move reductions, and game-history repetition
detection. The evaluation is material plus piece-square tables, pawn
structure (passed, doubled and isolated pawns), rook placement and king
safety.

The source is stored compressed (LZMA + base85) so the whole engine fits
in 4,096 bytes; `main.py` unpacks and runs it. Deterministic: the search
uses a fixed node budget, never a clock, so a replayed trial plays the
same moves. The readable source is `engine.py` in the build directory;
`main.py` is packed from it with the kit's `makefun compress`.

## Local results (practice trials, 6 games each)

| trial | Elo | result |
|-------|-----|--------|
| trial-0 | 1654 | 5 won, 0 drawn, 1 lost |
| trial-1 | 1451 | 4 won, 0 drawn, 2 lost |
| trial-2 | 1279 | 3 won, 0 drawn, 3 lost |

Mean 1461, above the house baseline (~1365).

## License

MIT. See [LICENSE](LICENSE).
