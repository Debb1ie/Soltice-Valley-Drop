<div align="center">

```
███████╗ ██████╗ ██╗     ███████╗████████╗██╗ ██████╗███████╗
██╔════╝██╔═══██╗██║     ██╔════╝╚══██╔══╝██║██╔════╝██╔════╝
███████╗██║   ██║██║     ███████╗   ██║   ██║██║     █████╗
╚════██║██║   ██║██║     ╚════██║   ██║   ██║██║     ██╔══╝
███████║╚██████╔╝███████╗███████║   ██║   ██║╚██████╗███████╗
╚══════╝ ╚═════╝ ╚══════╝╚══════╝   ╚═╝   ╚═╝ ╚═════╝╚══════╝

██╗   ██╗ █████╗ ██╗     ██╗     ███████╗██╗   ██╗
██║   ██║██╔══██╗██║     ██║     ██╔════╝╚██╗ ██╔╝
██║   ██║███████║██║     ██║     █████╗   ╚████╔╝
╚██╗ ██╔╝██╔══██║██║     ██║     ██╔══╝    ╚██╔╝
 ╚████╔╝ ██║  ██║███████╗███████╗███████╗   ██║
  ╚═══╝  ╚═╝  ╚═╝╚══════╝╚══════╝╚══════╝   ╚═╝
```

**✦ An Adventure of Light & Shadow ✦**

![HTML5](https://img.shields.io/badge/HTML5-Canvas-E34F26?style=flat-square&logo=html5&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-Vanilla-F7DF1E?style=flat-square&logo=javascript&logoColor=black)
![No Dependencies](https://img.shields.io/badge/Dependencies-Zero-brightgreen?style=flat-square)
![Responsive](https://img.shields.io/badge/Responsive-Desktop%20%7C%20Tablet%20%7C%20Mobile-8855cc?style=flat-square)
![License](https://img.shields.io/badge/License-MIT-blue?style=flat-square)
![Game Jam](https://img.shields.io/badge/June%20Solstice-Game%20Jam%202026-ff9940?style=flat-square)

*A pixel-art RPG adventure built entirely in a single HTML file — no frameworks, no build tools, no dependencies.*

</div>

---

##  Overview

**Solstice Valley** is a top-down pixel-art action RPG playable directly in any browser. The valley's balance of day and night has been shattered — you must collect Sun and Moon Fragments, complete quests from the locals, and defeat the ancient **Shadow Boss** to restore harmony.

Built for the **June Solstice Game Jam 2026** as a fully self-contained single-file game: one `.html` file, zero dependencies, runs anywhere.

---

##  Features

| | |
|---|---|
|  **Dynamic Day/Night Cycle** | A full 60-second cycle shifts the sky from dawn through noon, dusk, and deep night — with stars, a travelling sun & moon, night fog, and lantern glows |
|  **Hand-crafted World** | 30×20 tile map with forests, houses, a stone keep, shrines, and a wishing well |
|  **4-Stage Quest Line** | Talk to Elder Mira → collect Sun Fragments → collect Moon Fragments → defeat the Shadow Boss |
|  **4 Unique NPCs** | Elder Mira, Brom, Lyra, and Pip each have context-aware dialogue that evolves with your quest progress |
|  **Combo Combat** | Chain attacks within 0.7s to build combo multipliers (up to ×5) for bonus damage and visual flair |
|  **Dash System** | Invincibility frames during dash — time it right to slip through enemy attacks |
|  **Shadow Wisps + Boss** | Wisps spawn in waves; the Shadow Boss enters Phase 2 at 50% HP, speeding up and attacking faster |
|  **Levelling & Drops** | Defeat enemies for XP, level up to gain max HP and attack power, collect Heart and Crystal drops |
|  **Fully Responsive** | Adapts seamlessly across desktop (keyboard + overlaid HUD), tablet, and mobile (on-screen d-pad + action buttons, auto-detected by touch support) |
|  **Particle System** | Hit sparks, dash trails, combo bursts, ambient night fireflies, and a full fireworks finale on victory |
|  **Screen Shake** | Camera shake on hits, boss spawn, and powerful attacks for satisfying game feel. |

---

##  Controls

### Desktop
| Key | Action |
|-----|--------|
| `W A S D` or `Arrow Keys` | Move |
| `Z` or `X` | Attack |
| `Space` | Dash (grants invincibility frames) |
| Walk near an NPC | Auto-trigger dialogue |

### Mobile / Tablet
| Control | Action |
|---------|--------|
| D-Pad | Move |
| `ATTACK` button | Strike |
| `DASH` button | Dodge with invincibility |
| Walk near NPC | Auto-talk |

> **Pro tip:** Chain 3+ attacks within 0.7 seconds to trigger a ⚡ Combo — dealing +2 bonus damage and a golden burst effect.

---

##  How to Play

```
1. Open index.html in any modern browser
2. Press SPACE / ENTER or tap the screen to begin
3. Walk north to find Elder Mira at the well (look for the ❗ marker)
4. Collect 5 ☀ Sun Fragments scattered across the fields
5. Return to Elder Mira, then seek out Brom to the west
6. Collect 5 ☽ Moon Fragments (they glow silver — easier to spot at night)
7. Return to Brom to unlock the final quest
8. Head south — the Shadow Boss awaits near the dark shrines
9. Dodge its projectiles with DASH, attack in quick combos to deal max damage
10. Collect the Solstice Crystal it drops to complete your journey
```

###  Ranking System

| Score | Rank |
|-------|------|
| < 200 | Wanderer |
| 200–399 | Apprentice |
| 400–599 | Valley Hero |
| 600–999 | Solstice Knight |
| 1000+ | **Eternal Guardian ✦** |

---

##  Project Structure

```
solstice-valley/
└── index.html          ← The entire game (HTML + CSS + JS, ~1200 lines)
```

Yep, that's it. One file. No `node_modules`. No build step. Just open it.

---

##  Technical Architecture

The game is built on a hand-rolled engine inside a single `<canvas>` element:

```
Game Loop (requestAnimationFrame)
├── update(dt)
│   ├── Player movement + collision (AABB tile-based)
│   ├── Dash + invincibility frame timers
│   ├── Fragment & drop collection
│   ├── Enemy AI (aggro range → pursue, else wander)
│   ├── Boss Phase 2 trigger + projectile attacks
│   ├── Quest stage machine (0 → 1 → 1.5 → 2 → 2.5 → 3 → 4)
│   ├── NPC proximity dialogue triggers
│   └── Particle system tick
└── drawGame(t)
    ├── Sky gradient (9-stop interpolation across day/night cycle)
    ├── Star field + sun/moon arc
    ├── Tile map (grass, paths, trees, houses, shrines, well)
    ├── Fragments, drops, enemies, NPCs, player (all pixel-art sprites)
    ├── Particle rendering (sparks, trails, floaty damage numbers)
    └── Night overlay + lantern radial gradients
```

### Key Design Decisions

- **Single-file architecture** — zero build tooling, instant shareability, works offline
- **Fixed logical resolution** (`480×320`) scaled up via `canvas.style` — crisp pixel-art at any display size
- **Touch detection via JS** (`navigator.maxTouchPoints`) rather than CSS media queries, so the HUD adapts correctly inside iframes and embedded contexts
- **Delta-time physics** — movement and timers are frame-rate independent
- **Tile map as a 2D number array** — simple, readable, and trivially editable

---

##  Getting Started

### Play instantly (no install)

Just download and double-click:

```bash
# Clone the repo
git clone https://github.com/yourusername/solstice-valley.git

# Open in browser — that's literally it
open solstice-valley/index.html
```

Or serve it locally if your browser blocks local file access:

```bash
# Python
python -m http.server 8000

# Node
npx serve .

# Then visit http://localhost:8000
```

---

##  Map Legend

| Tile | Value | Description |
|------|-------|-------------|
| `0` | Grass | Walkable open field |
| `1` | Path | Stone/dirt walkable path |
| `2` | Tree | Solid — blocks movement |
| `3` | Flower | Decorative grass tile |
| `4` | House | Solid building tile |
| `5` | Well | Wishing well (Elder Mira's meeting point) |
| `6` | Shrine | Dark shrine — Shadow energy emanates at night |
| `7` | Altar | Golden altar — the heart of the valley |

---

## 🛠️ Modding & Customisation

The game is designed to be easy to hack. Everything lives in clearly commented sections:

**Change the map** — edit the `MAP` array (30 columns × 20 rows of tile IDs):
```js
const MAP = [
  [2,0,0,0,2,2, ...],  // row 0
  ...
];
```

**Add NPCs** — push to `NPC_DEFS` with your own `questLines` object:
```js
{ id: 'myNPC', x: 10*TILE+8, y: 8*TILE+8,
  name: 'Zara', color: '#ff8844',
  questLines: { 0: ["Hello traveller!"] } }
```

**Tune the boss** — adjust `hp`, `speed`, and `attackTimer` in `spawnBoss()`:
```js
enemies.push({ type:'boss', hp:25, speed:38, attackTimer:2.5, ... });
```

**Change day length** — one constant:
```js
const DAY_LEN = 60; // seconds per full cycle
```

---


##  Roadmap

- [ ] Sound effects & chiptune soundtrack
- [ ] Save/load via `localStorage`
- [ ] Second map area (the Shadow Realm)
- [ ] Inventory system with equippable items
- [ ] Additional boss phases
- [ ] Multiplayer (WebSocket co-op)
- [ ] Mobile haptic feedback on hits

---

##  License

MIT — do whatever you like with it. A credit back would be appreciated but isn't required.

---

<div align="center">

Made with ☀️ and ☽ for the **June Solstice Game Jam 2026**

*"The valley shines bright once more."*

</div>
