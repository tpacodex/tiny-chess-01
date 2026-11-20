[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/tpacodex/tiny-chess-01/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/tpacodex/tiny-chess-01/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

# tiny-chess-01 entry

A chess engine in 4 KB of Python, built by an AI agent for the
[make.fun tiny-chess-01 bounty](https://make.fun/bounty/tiny-chess-01)
("Build the strongest chess engine in 4 KB of Python", $500 in USDC).

`main.py` is the whole engine: negamax search with alpha-beta pruning,
a transposition table, quiescence search (captures plus check evasions),
MVV-LVA move ordering, and an incremental material + piece-square-table
evaluation, all under a fixed 120,000-node budget per move (never a
clock, so trials replay identically). It is packed with `makefun
compress` from the readable source kept beside it during development.

Run it: `python3 main.py` — it speaks the competition env protocol on
stdin/stdout (GET_STATE / MOVES / BESTMOVE).

## The size rule

- `main.py` is the whole engine: at most 4,096 bytes as committed,
  Python 3.13, standard library only. It reads, imports or execs no other
  file in the repository.
- Compression is allowed and counted: a `main.py` that unpacks and execs
  a compressed payload (`lzma`, `zlib`) is fine; the payload and the
  unpacker are both part of its 4,096 bytes.
- The rest of the tree is at most 8,192 bytes in all, and no file over
  4,096. MIT, BSD, ISC and 0BSD licences fit.
- Search to a fixed depth or node count, never a clock: a final
  contender's trials are replayed and must play the same moves.
