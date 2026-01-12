# Neural Breaker – Swarm Prototype (game_v2.html)

HTML5 canvas prototype of a portrait, lane-based auto-runner with math gates that grow/shrink a swarm. Built with vanilla JS and procedural SFX.

## Play
- Open `game_v2.html` in a modern browser.
- Tap/click DEPLOY to start.
- Drag left/right to steer within the lane. Forward movement is automatic; autofire scales with swarm size.

## Core Systems
- **Math Gates:** Random `+`, `-`, `×`, `÷` gates. At least one “good” gate is guaranteed; division is integer (floor) with min clamp to 0. Colliding a gate instantly applies the operation to troop count.
- **Swarm:** Troop count drives both visuals (up to 80 dots) and fire rate (faster with more units). Swarm spreads out as count grows.
- **Enemies:** Simple walkers; HP scales over time. Bullets damage enemies; contact reduces troops by a fixed loss.
- **Audio:** Procedural tones for growth/shrink and shooting (AudioContext), initialized on start.

## Controls
- Drag on screen to steer horizontally. Release to stop steering. There is no forward control.

## Fail/Restart
- When troops hit zero, an alert shows “MISSION FAILED” and the run auto-resets to PLAY state.

## Known Caveats
- `forEach` with `splice` in gate/enemy collision can skip overlaps if multiple objects collide in one frame; a reverse loop is safer.
- Alert-based game over is blocking and immediately re-enters PLAY after dismissal (no overlay).
- AudioContext must be unlocked by a user gesture (start button); sounds before that are dropped.
