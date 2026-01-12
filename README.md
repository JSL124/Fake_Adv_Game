# Lane Runner MVP

HTML5 canvas prototype for a portrait, lane-based casual action game with math gates, troop clusters, and a simple boss encounter. No external assets or libraries—just `index.html`, `style.css`, and `game.js`.

## Play
- Open `index.html` in a modern desktop or mobile browser.
- Tap/click START to begin. Drag left/right on the screen to swap lanes. The runner auto-moves forward.

## Core Systems
- **Math Gates:** Left/right panels apply `+`, `-`, `×`, or `÷` to your troop count. Values are scaled to keep at least one reasonable choice. Division is rounded down and clamped to minimum 1.
- **Troop Cluster:** Troop count is represented by soldier pictograms (capped at `maxVisibleTroops` for performance) while the count remains exact. More troops increase auto-fire damage.
- **Enemies:** Simple lane walkers with scaling HP.
- **Boss:** Spawns near 85% progress, has HP bar, takes damage proportional to troop count (plus bullet hits), and deals periodic troop damage. If troops reach 0, you fail.

## Controls
- Drag or swipe anywhere on the screen to change lanes. Forward movement is automatic.

## Tuning
Edit the constants at the top of `game.js`:
- `laneCount`, `speed`, `stageLength`, `gateDistances`
- `maxVisibleTroops` (pictogram cap)
- Boss knobs: `bossHP`, `bossDamagePerTick`, `bossTickInterval`, `troopDamageToBossPerSecond`, `bossSpawnAt`
- Gate balance: adjust values inside `makeGatePair()`

## UX / Feedback
- Troop label floats above the cluster with a dark backdrop for readability.
- Popups show gate results and damage taken.
- SFX stubs exist via `playSfx(name)`; wire up WebAudio as needed.

## Files
- `index.html` – markup and HUD/overlay
- `style.css` – layout and HUD styling
- `game.js` – game loop, math gates, troop cluster, enemies, boss logic, drawing

## Known Considerations
- SFX are stubs; no audio is played until you hook WebAudio.
- Overlay text persists between runs (e.g., “Stage Complete” after finishing). If you need a fresh prompt each run, reset the overlay text in `reset()`.
