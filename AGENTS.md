# AGENTS.md

## Project
Asteroids clone: vanilla HTML5 Canvas game, no frameworks, no bundler, no dependencies, no tests, no lint. Single source of truth is `game.js`.

## Run / verify
- No build step. Open `index.html` in a browser, or serve locally with `npx serve .` (then `http://localhost:3000`).
- There is no automated verification; "testing" means manually playing in a browser. Always re-check the game loop after edits (`requestAnimationFrame` at `game.js:414`).

## Architecture
- Everything lives in one global-scope file (`'use strict'`, top-level consts/lets/classes) — no modules, no imports. New code must keep the same style.
- `W`/`H` (800×600) are duplicated: defined in `game.js:5` and as `<canvas width height>` attributes in `index.html`. Keep them in sync.
- Game states are a string const `state`: `'playing' | 'dead' | 'gameover'` (`game.js:241`).
- Asteroid properties are indexed by `size` (1–3) via the parallel arrays `RADII`/`SPEEDS`/`POINTS` at `game.js:61`. Index 0 is a dummy; any new size needs entries in all three arrays plus a `split()` path.
- All entities use the `dead` flag + `.filter()` pattern for removal; `update(dt)` and `draw()` are the two methods per class.

## Conventions
- Code identifiers are in English; UI strings (HUD, overlays) and comments are in Spanish. Match whichever you are touching.
- `dt` is delta-seconds, clamped to 0.05 max in the loop.

## Gotchas
- README describes features (power-ups, "estrella fugaz") that are NOT in `game.js` yet. The code is the truth; don't assume README features exist.
- Canvas coords are world-space with toroidal wrapping via `wrap()` — entities must wrap on `W`/`H`, never die at screen edges.
