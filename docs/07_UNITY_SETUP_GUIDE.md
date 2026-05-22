# 🛠 Unity Setup Guide — Aetherloom

## 1. Prerequisites

- Unity Hub installed
- Unity **6 LTS (6000.4.4f1)** installed via Unity Hub
- Git installed
- ~30 GB free disk for project + cache + sector lightmaps
- Steam client installed (for testing P2P)

## 2. Clone & open

```bash
git clone https://github.com/Abdulmalek-Agents/aetherloom.git
cd aetherloom
```

In Unity Hub: **Add → Open existing project → select `aetherloom/`**.

## 3. Set render pipeline (URP)

Project Settings → Graphics → Scriptable Render Pipeline → assign `URP_Default` asset at `Assets/_Project/Settings/URP_Default.asset`.

## 4. Install required packages

Window → Package Manager → verify/install:
- URP (latest LTS)
- Burst (latest)
- Mathematics
- Collections
- Cinemachine
- Timeline
- New Input System
- Localization
- Addressables

## 5. Install Mirror + Facepunch.Steamworks

- **Mirror**: Asset Store → import to `Assets/_ThirdParty/Mirror/`
- **Facepunch.Steamworks**: Download from `https://github.com/Facepunch/Facepunch.Steamworks`; place in `Assets/_ThirdParty/Steamworks/`
- Configure Mirror Transport → `FizzySteamworks` transport for P2P over Steam

## 6. Import Asset Store packs

Log into Unity Asset Store with the Inventix account. Import from Package Manager → My Assets:

| Pack | Destination |
|---|---|
| Fantasy Castle Environment | `Assets/_ThirdParty/FantasyCastle` |
| The Medieval Castle | `Assets/_ThirdParty/MedievalCastle` |
| Stylized Dungeons | `Assets/_ThirdParty/StylizedDungeons` |
| BoZo Modular Characters | `Assets/_ThirdParty/BoZo` |
| Fantasy Monsters Bundle | `Assets/_ThirdParty/FantasyMonsters` |
| Stylized Fantasy Creatures #2 | `Assets/_ThirdParty/StylizedCreatures2` |
| Anime Powers Pack | `Assets/_ThirdParty/AnimePowers` |
| Magic Arsenal | `Assets/_ThirdParty/MagicArsenal` |
| Spells Pack | `Assets/_ThirdParty/SpellsPack` |
| 100 Special Skills Effects | `Assets/_ThirdParty/SpecialSkillsFX` |
| Character Controller Pro | `Assets/_ThirdParty/CharacterControllerPro` |
| Traversal Pro | `Assets/_ThirdParty/TraversalPro` |
| Animation Composer System | `Assets/_ThirdParty/AnimationComposer` |
| Cutscene Engine | `Assets/_ThirdParty/CutsceneEngine` |
| Skill Tree Builder | `Assets/_ThirdParty/SkillTreeBuilder` |
| Heat UI | `Assets/_ThirdParty/Heat` |
| Lumen Light FX 2 | `Assets/_ThirdParty/LumenFX2` |

## 7. Toon shader (Month 1 critical commission)

The toon shader is COMMISSIONED — not asset-store. Once delivered, place in `Assets/_Project/Shaders/Toon/` and assign as default material at `Materials/Toon/M_ToonBase.mat`.

Gate: Month 3 perf test. Toon shader must hold 60fps on Steam Deck with full Sector 1 load + 2 players + boss.

## 8. Wire prefabs

1. Open `Scenes/Bootstrap.unity`. Press Play — title card.
2. Open `Scenes/Vestibule.unity`. Drag `Prefabs/Player/Player_Cassia.prefab` + `Prefabs/Loom/Loom.prefab`.
3. Open `Scenes/Sector_01_EchoesOfPelion.unity`. Drag arena spawners + Stag-Crowned boss.
4. Press Play. Cassia spawns in Vestibule. Walk to Loom → tutorial begins.

## 9. Test co-op locally

- Open 2 Unity Editor instances (or build standalone)
- Instance A: Steam Lobby → Host
- Instance B: Steam Lobby → Join Friend (A appears in list)
- Both spawn in Vestibule; cooperation begins

## 10. Build targets

- PC (Windows/Mac/Linux): IL2CPP scripting backend, LZ4HC compression
- PS5: Unity PS5 SDK (separate licence)
- Xbox Series: Unity Xbox SDK
- Switch 2: Unity Switch SDK
- Steam Deck: Verified profile (Phase 7)

## 11. No proxy server, no API key, no internet required

For solo play, no Steam connection required. For co-op, Steam Lobbies are used (Steamworks API; no separate proxy).

## 12. Troubleshooting

| Symptom | Fix |
|---|---|
| Pink materials | Project not on URP — re-assign in Graphics settings |
| Network desync | Verify Mirror authority assigned to host; FizzySteamworks transport selected |
| Frame rate <60fps | Profile with Unity Profiler; suspect first: VFX particle count or unbatched draws |
| Toon shader looks wrong | Confirm M_ToonBase is assigned at material level + GPU instancing enabled |
