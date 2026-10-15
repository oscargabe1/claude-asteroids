# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project

Asteroids clone in plain HTML5 Canvas + vanilla JS. No dependencies, bundler, package.json, linter or tests. README and code comments are in Spanish.

## Running

Open `index.html` directly in a browser, or serve with `npx serve .` (http://localhost:3000). There is no build step.

## Architecture

All game logic lives in a single script, `game.js` (loaded by `index.html`, canvas fixed at 800x600 via `W`/`H`). Sections, in order:

- **Input**: `keys` (held) and `justPressed` (edge-triggered). Read edge-triggered input with `pressed(code)`, which consumes the flag (used for shooting and restart on `Space`).
- **Utils**: `wrap` (toroidal screen wrap), `dist`, `rand`, `randInt`.
- **Entities**: `Bullet`, `Asteroid`, `Ship`, `Particle` classes. Each has `update(dt)` and `draw()` and a `dead` flag; dead entities are filtered out of arrays each frame. Asteroid size is 1–3, indexed into the `RADII`/`SPEEDS`/`POINTS` tables (note the index-to-size mapping: larger size = bigger radius, slower, fewer points). `Asteroid.split()` returns the child fragments.
- **Game state**: module-level `let` globals (`ship`, `bullets`, `asteroids`, `particles`, `score`, `lives`, `level`, `state`). `state` is `'playing' | 'dead' | 'gameover'`; `update(dt)` branches on it. `initGame()` resets everything; `nextLevel()` fires when `asteroids` is empty.
- **Loop**: `requestAnimationFrame` loop calls `update(dt)` then `draw()`; `dt` is in seconds.

Collision is circle-based using `dist` against radii (ship vs asteroid uses `a.radius * 0.82`). Bullet-vs-asteroid collisions collect fragments in `newAsteroids` and merge after the loop.
