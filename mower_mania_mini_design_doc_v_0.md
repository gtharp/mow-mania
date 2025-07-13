## Mini‑Design Doc – "Mower Mania" (working title)
**Version 0.1 – July 12 2025**

---
### 1. Core Game Loop
• Player uses on‑screen D‑pad or swipe to move the mower across a 16 × 16 tile lawn.
• Entering an uncut grass tile instantly changes it to the "cut" state and awards 1 point.
• Timer counts up to 03:00.
• Loop repeats until a win/lose condition is met.

### 2. Win / Lose Conditions
| Outcome | Condition |
|---------|-----------|
| **Win** | 100 % of mow‑able grass tiles are cut **before** the 3‑minute timer expires. |
| **Lose** | The 3‑minute timer hits 00:00 with any uncut grass remaining. |

### 3. Difficulty Curve & Level Rules
• Level +1 spawns additional obstacles in the same fixed lawn size.
• Obstacle types and behaviors:
  - **Rocks** – impassable tiles.
  - **Trees** – impassable; visually taller/larger footprint than rocks.
  - **Weeds** – passable but mower speed is reduced by 50 % while cutting (takes 2× longer to clear the tile).
• Suggested spawn formula (MVP, tweak later):
  - Rocks = _Level + 2_
  - Trees = ⌈Level / 2⌉
  - Weeds = _Level + 3_
• Only obstacle density changes; lawn dimensions stay constant for MVP.

### 4. Content Specification (Art & Audio)
| Asset | Frames / States | Size | Notes |
|-------|-----------------|------|-------|
| **Mower sprite** | 4‑direction idle/move (or single frame MVP) | 16 × 16 px | GB‑style sprite |
| **Grass tile** | Uncut, Cut | 16 × 16 px | swap tile definition on cut |
| **Rock tile** | Static | 16 × 16 px | impassable |
| **Tree tile** | Static | 16 × 16 px | impassable |
| **Weed tile** | Uncut, Cut | 16 × 16 px | slows mower |
| **Retro palette** | 16‑color (4‑bit) | — | Consistent across all art |
| **SFX** | start, cut, bump, timer warn, level win/lose | — | 8‑bit chiptune |

### 5. Monetization Placeholder
• MVP ships **free with no ads**.
• Future update: non‑consumable IAP for cosmetic mower skins & color palettes.
• Code hooks to add now:
  - Enum of SKU identifiers.
  - Unlock checks behind compile‑time flag.
  - StoreKit wrappers stubbed but disabled until assets exist.

### 6. Technical & Compliance Notes
• Engine: **SpriteKit** with `SKTileMapNode`.
• Tile definitions: `grass_uncut`, `grass_cut`, `rock`, `tree`, `weed_uncut`, `weed_cut`.
• Asset budget: ≤ 100 KB total; 60 fps target on iPhone SE (2nd gen).
• Privacy: collects **no** user data → "No Data Collected" App Privacy label.
• Localization: English only for v0.1.

### 7. Open Questions / Parking Lot
1. Power‑ups (e.g., speed‑boost fuel cans) – defer to v1.1.
2. Game Center leader‑boards & achievements – defer to v1.2.
3. Dynamic lawn sizes (larger maps) – evaluate after MVP performance pass.

---
*End of document.*

