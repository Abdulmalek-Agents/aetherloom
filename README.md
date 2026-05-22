# 🪡 Aetherloom

> *"Two siblings, two weapons, one tapestry. The Loom remembers what you forget."*

A **stylized 3D 2-player drop-in/drop-out co-op action roguelite** in a mythic Mediterranean dreamscape. You and a friend play the twin Loomwardens — demigods bound to the Aetherloom, the tapestry that weaves the fate of mortals. Every run you delve into the Loom's broken sectors, fight stylized mythic enemies in tight 3D arenas, and your two characters' fates are **literally woven together**: the threads you weave in one run alter the upgrades, enemies, and bosses your sibling encounters in their next run.

**Pitch in one line:** *Hades × Children of Morta × Hi-Fi Rush — with a shared-fate co-op twist no one else is doing.*

| | |
|---|---|
| **Genre** | Stylized 3D 2-Player Co-op Action Roguelite |
| **Platforms** | PC (Steam) primary; PS5, Xbox Series S/X, Switch 2 stretch |
| **Engine** | Unity **6 LTS (6000.4.4f1)** + URP (stylized lighting + custom toon shader) |
| **Target frame-rate** | 60 fps on RTX 3060 / Steam Deck OLED; 120 fps on RTX 4070 |
| **Vertical slice scope** | *Run One* — first sector + first boss (Echoes of Pelion) |
| **Designed for** | 6 sectors + finale across 20–30 h main + 60+ h mastery |
| **Team size** | **7–9 people** |
| **Budget** | **$350–500k** (18-expert board sign-off) |
| **Target ship** | **24 months from greenlight** |
| **Runtime AI features** | **None** — fully offline. All companion banter is hand-authored `DialogueNodeSO`. |
| **Networking** | Steam P2P (Mirror) + Steam Lobbies; LAN supported |
| **AI in development** | Claude Code & Claude Agents are used in the studio workflow. |

## Why this game

Hades sold 4M+ at 98% positive; Hades 2 is on a $1B trajectory. The genre is the #1 stylized-3D-indie revenue lane. **The empty quadrant is co-op.** Hades is solo. Ravenswatch is 4-player but unfocused. Wizard of Legend is 2-player but 2D. **Aetherloom is the 2-player drop-in 3D shared-fate roguelite that no one is making.** Children of Morta proved the appetite (1.5M+ sold) but it's 2D and 4-player same-screen. The 3D + 2-player-online + shared-narrative-loom combination is mechanically unique and commercially uncontested.

Details in [`docs/01_IDEATION_AND_TRENDS.md`](docs/01_IDEATION_AND_TRENDS.md).

## What's in this repo

```
aetherloom/
├── README.md                              ← you are here
├── LICENSE                                ← MIT (original code/docs only)
├── CHANGELOG.md
├── .gitignore                             ← Unity-standard
└── docs/
    ├── 00_PORTFOLIO_REVIEW_BOARD.md       ← 18-expert vote + verdict
    ├── 01_IDEATION_AND_TRENDS.md          ← market evidence
    ├── 02_GAME_DESIGN_DOCUMENT.md         ← full GDD
    ├── 03_ASSET_PLAN.md                   ← Unity Asset Store + commission list
    ├── 04_TECHNICAL_ARCHITECTURE.md       ← Unity 3D URP + Mirror co-op
    ├── 05_PRODUCTION_PLAN.md              ← 24-month phase plan
    ├── 06_CRITIC_REVIEW_CYCLES.md         ← 3-cycle critic review (18 experts)
    ├── 07_UNITY_SETUP_GUIDE.md            ← click-by-click setup
    └── 08_MARKETING_PLAN.md               ← wishlist + Steam Next Fest plan
```

## Quick start

1. Read [`docs/07_UNITY_SETUP_GUIDE.md`](docs/07_UNITY_SETUP_GUIDE.md).
2. New Unity **6 LTS (6000.4.4f1)** URP project.
3. Import: Character Controller Pro, Animation Composer System, Anime Powers Pack, Magic Arsenal, Spells Pack, 100 Special Skills FX, Stylized Dungeons, Fantasy Castle Environment, BoZo Modular Characters, Heat UI, Cutscene Engine, Skill Tree Builder — from inventory. Plus must-buy: Mirror (free) + Facepunch.Steamworks (free) + custom toon shader (commission ~$1,500).
4. Open `Scenes/Bootstrap.unity` → Play.

## Status

| Stage | Status |
|---|---|
| 18-expert Cycle 1 vote (concept) | ✅ Approved (avg **8.50/10**) |
| 18-expert Cycle 2 (GDD) | ✅ Approved with 4 required changes (all applied) |
| 18-expert Cycle 3 (architecture + asset + marketing) | ✅ Final Approved (18/18 clean) |
| *Run One* vertical slice implementation | ⏳ Pending Phase 1 |
| Sectors 2–6 + finale outlined | ✅ Data-driven |
| Steam page | ⬜ Schedule for Month 6 |

> Maintained by Abdulmalek-Agents (Inventix Games). PRs welcome.
