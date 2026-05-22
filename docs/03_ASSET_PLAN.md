# 🎨 Asset Plan — Aetherloom

> Net coverage from Inventix existing inventory: **~75%**. The remaining ~25% is commissioned to maintain stylized 3D coherence.

## 1. Existing inventory used

| Asset | Used for | Critical |
|---|---|---|
| **Fantasy Castle Environment** ($129.99) | Vestibule hub + Sector 6 (Loom's Heart) | 🔴 Yes |
| **The Medieval Castle** ($54.99) | Sector 2 (Drowned Agora) re-painted | 🔴 Yes |
| **Stylized Dungeons** ($50) | Sector 3 (Ember Catacombs) | 🔴 Yes |
| **Medieval Village Megapack** | Vestibule outer streets | 🟡 Helpful |
| **BoZo Modular Characters Fantasy** ($40) | Vestibule NPCs (Pythia, the Weaver) | 🔴 Yes |
| **Fantasy Monsters Bundle** ($99.50) | Skeletons, goblins (re-painted marble revenants) | 🔴 Yes |
| **Stylized Fantasy Creatures #2** ($149.99) | Bosses (Selvanos stag, manticore base for Mourner) | 🔴 Yes |
| **Anime Powers Pack** ($30) | Loom Charge bursts, thread-pull VFX | 🔴 Yes |
| **Magic Arsenal** ($30) | Sword + dagger + bow + shield models | 🔴 Yes |
| **Spells Pack** ($59.99) | Enemy abilities (boss spells, AoE) | 🔴 Yes |
| **100 Special Skills Effects Pack** ($24.99) | Ability VFX library | 🔴 Yes |
| **Ultimate Mesh FX** ($35) | Enemy dissolve, thread-sever effect | 🟡 Helpful |
| **Realistic Blood VFX** ($40) | Combat impact decals (stylized, restrained) | 🟡 Helpful |
| **Volumetric Blood Fluids** ($30) | Boss kill volumetric effect | 🟡 Helpful |
| **Character Controller Pro** ($28.99) | Player movement + ability state machine | 🔴 Yes |
| **Traversal Pro** ($45) | Vault / climb / ledge | 🟡 Helpful |
| **Animation Composer System** ($39.99) | Layered upper/lower body anims | 🔴 Yes |
| **Cutscene Engine** ($35) | Boss intros, thread-tie cinematic, finale | 🔴 Yes |
| **Skill Tree Builder** ($15) | Loom interaction backbone | 🔴 Yes |
| **Heat UI** ($69.99) | Main menu, HUD, lobby | 🔴 Yes |
| **Bamao Pack Fantasy GUI** ($25) | In-game overlays | 🟡 Helpful |
| **Lumen Light FX 2** ($35) | Vestibule lantern glow, dramatic god rays | 🔴 Yes |
| **VoluSmokeFX** ($25) | Atmospheric smoke (Catacombs, Storm Causeway) | 🟡 Helpful |
| **Screenspace VFX** ($30) | Damage flash, low-HP vignette | 🔴 Yes |

**Inventory value applied: ~$1,300 across 24 assets.** Already owned.

## 2. Networking + co-op stack

| Tool | Source | Cost |
|---|---|---|
| **Mirror** | Free (Asset Store) | $0 |
| **Facepunch.Steamworks** | Free | $0 |
| **Steam Lobbies** | Steamworks | $0 |
| **Mirror authoritative-host pattern** | Internal implementation | $0 |

## 3. Commissioned art / audio (Elena + Sora + Rin + Naomi)

| Gap | Description | Cost |
|---|---|---|
| **Custom toon shader** | URP-extension toon shader with ramp + outline + softstep | $1,500 |
| **Twin character models + rigs** | Cassia + Lior; ~40 animation clips each | $4,000 |
| **6 unique boss models + 30 anims** | Stag-Crowned, Auctioneer, Forge-Wretch, Aether-Tyrant, Mourner, Weaver | $6,000 |
| **Usurper God final boss** | Cinematic-quality model + multi-phase animation | $2,500 |
| **OST (12 tracks)** | Mediterranean lyre + chorus + percussion + finale | $3,500 |
| **Bespoke combat SFX (~150 sounds)** | Weapons, hits, abilities, footstep variants | $1,500 |
| **Voice acting (~600 lines, 8 actors)** | Twins + 6 NPCs + 7 bosses | $5,000 |
| **Steam capsule + key art (3 illustrations)** | Marketing-ready hero art | $1,500 |

**Commission total: ~$25,500.** Within the $350–500k team-budget envelope.

## 4. Visual coherence rule (Cycle 2 required change — Sora + Elena)

**Look-lock by Month 3.** A single Vestibule + Sector 1 + Stag-Crowned boss is built to final-quality visual standard by Month 3. After approval, all subsequent sectors strictly follow the locked style guide. **No style drift permitted.** Diego V's go/no-go gate: toon shader prototype performs at 60fps on Steam Deck with full sector load.

## 5. Folder organisation

```
Assets/_Project/
├── Art/{Player,Bosses,Enemies,Environments,VFX,UI,Loom}
├── Audio/{Music,SFX,Ambient,Voice}
├── Animations/{Player,Bosses,Enemies}
├── Materials/{Toon,Loom,Environment}
├── Shaders/Toon
├── Prefabs/{Player,Bosses,Enemies,Environment,Loom,UI,VFX}
├── Scenes/
├── Data/{Sectors,Threads,Weapons,Bosses,Enemies,DialogueNodes,LineBanks}
└── Scripts/{Core,Combat,Loom,Networking,Dialogue,UI,Save,Performance}
```

## 6. Performance tweaks (Diego V's plan)

- Toon shader uses GPU instancing for all repeated props.
- Boss VFX uses `VisualEffectGraph` (Unity URP-VFX) with LOD scaling.
- Object pooling for all combat VFX + projectiles.
- Mirror network tick at 30Hz for non-critical, 60Hz for player + boss.
- Each sector pre-baked lightmap + reflection probes.
- Performance budget: 60fps on Steam Deck OLED with both players + 24 enemies + boss + VFX.

## 7. Licence audit ✅

Unity Asset Store EULA covers all listed packs. Commissioned art is work-for-hire with explicit commercial-use buyout. Mirror MIT-licensed. Facepunch.Steamworks MIT-licensed. **Asset binaries are NOT redistributed in this repo.**

## 8. Post-purchase checklist

- [ ] Confirm all Asset Store packs accessible to all team members
- [ ] Commission toon shader (Month 1 — critical path)
- [ ] Commission character artist for twins (Month 1)
- [ ] Commission boss artist (Month 4)
- [ ] Commission composer (Month 6)
- [ ] Build Player_Cassia.prefab + Player_Lior.prefab
- [ ] Build Loom.prefab with thread-tying interaction
- [ ] Build StagCrowned_Boss.prefab (2-phase Animator)
- [ ] Set up Mirror + Steam Lobby authentication flow
- [ ] Author 6 SectorDataSO + 30 ThreadDataSO + 7 BossDataSO
- [ ] Author 14 NPC DialogueNodeSO trees
