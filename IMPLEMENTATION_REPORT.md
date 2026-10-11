# Stick Hunter — implementation report

## Delivered
- Phase 1 playable local sandbox scaffold built from the GDD: Three.js orthographic side-on scrapyard, platforms, procedural stick fighters, HUD, keyboard and multitouch controls, movement/jump/coyote-time/jump buffer, dash, punch/sword hit checks, pickup/drop, bomb fuse/throw/explosion, laser warning/active cycle, damage/knockback, KOs, respawns, local sparring dummies, pause/restart, and generated sound cues.
- Shared configuration and plain-data game-core rules are separated from rendering and input.
- Basic unit tests cover input normalization, spawn protection, and KO attribution.
- Responsive landscape-first UI, reduced-motion preference handling, mute toggle, and visible status showing that networking is not yet connected.

## Verification
- `tsc --noEmit -p packages/game-core/tsconfig.json` passed.
- `npm install --no-audit --no-fund` timed out in this environment; dependencies were not installed.
- Consequently Vite production build, full client typecheck, Vitest suite, and browser/device playtests could not be run here. Do not treat those as passing.

## Deviations and limitations
- This is the first local gameplay vertical slice, not the complete GDD MVP. It does not yet include Rapier 2D, Firebase Anonymous Auth/Realtime Database, WebRTC DataChannels, online Quick Play/private rooms, protocol runtime validation, production Firebase rules/deployment, or multi-client authority. Character/platform collision is a lightweight custom 2D controller for the initial playable slice.
- Sparring dummies are local prototype AI and are not remote players.
- Visual and audio effects are procedural placeholders; no external asset packs are required.
- No Firebase project was created and no billing/deployment action was taken.

## Next recommended milestone
Phase 2: introduce Rapier 2D for the host simulation and build the shared protocol + Firebase RTDB signaling + WebRTC host/guest handshake. Keep RTDB control-plane-only. Add security rules before public testing and clearly label authority as host-authoritative (not server-authoritative). Do not promise TURN coverage without an explicitly approved provider/cost.
