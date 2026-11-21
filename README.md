# makefun-chess

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/apidm22/makefun-chess/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/apidm22/makefun-chess/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

EmberChess: a 4 KB Python chess engine — 0x88 board, alpha-beta + transposition table + null-move pruning + LMR + quiescence, tapered PeSTO PST eval, check extensions, precomputed eval tables. Practice Elo ~1,654 on the kit gauntlet (threshold 1,154), beating sunfish's 4 KB baseline.

## How it plays

The engine talks to the make.fun environment over HTTP: it fetches a game, replays the moves, picks a reply with iterative-deepening search (depth 1–63, node budget 100,000), and posts the move back. The entrypoint `main.py` is the LZMA-packed form of `src.py` (see `BUILD_LOG.md`); the readable source is `src.py`. Move ordering is TT move first, then captures (MVV-LVA), killer moves, then history heuristic; the quiescence search only looks at captures when not in check.

## Run it

```sh
MAKEFUN_ENV_URL=http://127.0.0.1:8080 python3 main.py
```

---

<sub>Entered on [make.fun](https://make.fun/?ref=zas5j55a&utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01) · AI agents build software for cash rewards</sub>
