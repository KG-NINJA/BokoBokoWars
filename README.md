# Crown Rescue March

An original low-poly tactical rescue auto-battle game built with Three.js and Vite.

## Run

```bash
npm install
npm run dev
```

Build with `npm run build` and preview with `npm run preview`.

## Controls

- `WASD` / Arrow keys: move the King
- `E`: rescue an adjacent captured, downed, or isolated ally
- `Space`: toggle nearby loyal allies between follow and advance
- `Q`: recall nearby loyal allies
- `H`: order nearby loyal allies to hold
- `R`: restart after victory or defeat
- Mouse hover: inspect a unit
- Touch: on-screen direction pad plus Rescue, Advance, Follow, and Hold buttons

## Rules

Break prison gates to free captured allies, keep them near the King for morale, and advance on the eastern fortress. Gates have their own HP and defense and are attacked automatically in range. Downed and isolated allies are still rescued with `E`. Combat is automatic and deterministic. Damage uses attack, matchup, morale, fatigue, terrain, defense, and terrain defense. Loyal adjacent soldiers absorb half of incoming King damage. Healers restore nearby allies.

All allied and enemy units display an overhead level and XP gauge.

Movement is camera-relative: `W`/Up moves toward the depth of the screen, `S`/Down moves toward the foreground, and `A`/`D` move screen-left/right. Loyal allied retainers level up immediately whenever they defeat an enemy; the King and enemies still level every three victories.

While following, retainers form ahead of the King toward the fortress. Shields, spears, and soldiers occupy the front; archers and healers remain closer to the rear, leaving the King at the back of the formation.

Unvisited battlefield tiles are hidden by a permanent exploration shroud. The King reveals four tiles around him; rescued active allies reveal two. Enemies, prisons, and the fortress remain hidden until their tile is explored.

Some trees and rocks are retainers trapped by transformation magic. When the King or a loyal active retainer reaches an adjacent tile, the object automatically returns to its original allied unit. Intact prison gates and transformed objects are hard movement blockers and cannot be crossed.

The soundtrack is an original two-voice martial loop synthesized with Web Audio. The first key press or click plays a short victory-call start jingle, then transitions into the BGM loop. Combat generates synthesized weapon impacts plus slash-and-spark hit effects; no external audio assets are required.

Hex Sorcerers are fragile 3 HP enemy casters with four-tile range. Their spells deal light damage and have a 2% chance per hit to permanently transform the target into a frog. Frog units remain controllable but are reduced to 1 attack, 0 defense, 0.7 speed, and melee range.

The AI strategist button is an optional browser-only commentary feature. When Chrome Built-in AI `LanguageModel` or `ai.languageModel` is available and already ready locally, it asks for a short Japanese strategist line using only compact battle context. Unsupported browsers or not-yet-downloaded models automatically use rule-based comments. AI output never changes combat, movement, win/loss, rewards, or saves.

Destroy the fortress or defeat its commander to win. The battle is lost if the King dies.

## Tuning

Global values and terrain costs are in `src/data/balance.js`. Unit stats and type matchup multipliers are in `src/data/unitTypes.js`. The map and unit placements are defined in `src/game/Map.js` and `src/game/World.js`.
