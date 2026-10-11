# Stick Hunter

A browser-first, landscape-oriented 2D stick-figure arena brawler, based on the supplied GDD/TDD v0.3.

## Current milestone

**Phase 1 vertical slice:** playable local scrapyard sandbox with Three.js orthographic rendering, keyboard and touch controls, combat, pickups, bomb fuse/explosion, laser hazard, knockback, respawns, a match clock, and CPU sparring dummies. Game rules/configuration are separated from rendering. This is not yet online multiplayer; Firebase + WebRTC host-authoritative networking is the next major vertical slice.

## Requirements

- Node.js 20+ and npm
- Modern browser with WebGL

## Run

```bash
npm install
npm run dev
```

Open the local URL Vite prints. For production build:

```bash
npm run build
npm run typecheck
npm test
npm run preview
```

## Controls

- Move: A/D or ←/→
- Jump: Space / W / ↑
- Dash: Shift
- Attack: J or left mouse button
- Pick up / drop: E
- Throw held bomb: K or right mouse button
- Escape: settings / resume

On touch devices use the left movement pad and large action buttons. Landscape is recommended.

## Architecture

- `apps/client/src/rendering.ts`: Three.js renderer and procedural art.
- `apps/client/src/game.ts`: local sandbox simulation and gameplay loop.
- `apps/client/src/input.ts`: normalized keyboard, pointer, and multitouch input.
- `packages/game-core`: plain-data rules that can later run in the room creator's browser.
- `packages/shared-config`: centralized tuning.
- `tests`: rule-level automated tests.

## Important scope/trust note

The current build is a **local playable prototype**, not the finished multiplayer MVP. Online matches in the specification are **host-authoritative**, not server-authoritative: the room creator's browser resolves game outcomes and can manipulate them. The next milestone should implement Firebase Anonymous Auth + RTDB room/signaling records and WebRTC DataChannels; RTDB must never carry per-frame combat state. Do not claim universal WebRTC connectivity: restrictive NATs may need a separately approved TURN relay.

No Firebase project, billing account, or deployment has been created. The project remains designed for Firebase Spark, with no paid service silently introduced.
