# 🛠 Technical Architecture — Aetherloom

> Unity **6 LTS (6000.4.4f1)** + URP (stylized 3D). 1–2 player co-op via Mirror P2P + Steam Lobbies. Offline-capable solo play.

## 1. Tech stack

| Layer | Choice | Reason |
|---|---|---|
| Engine | Unity 6 LTS 6000.4.4f1 | Studio standard |
| Render | URP | Best stylized 3D pipeline for our scale |
| Custom shader | URP toon shader (commissioned) | Visual identity |
| Networking | **Mirror** (free, MIT) | Authoritative host model, proven |
| Transport | **Facepunch.Steamworks** (free) | Steam P2P |
| Lobby | **Steam Lobbies** | Built-in matchmaking |
| Language | C# 10 + Burst (for boss AI tick) | Standard + perf |
| Data | ScriptableObjects + JSON save | Designer-friendly |
| Save | Custom JSON + Steam Cloud | Run-state + meta-progress |
| Localisation | Unity Localization Package | EN @ launch; +5 langs Year 1 |
| Input | New Input System | KB+M + controller (Xbox + DualSense) |

## 2. Core architecture

### Service Locator + Authoritative Host (Mirror)

```
GameBootstrap
  └─ ServiceLocator
       ├─ RunService          (current run state; sector progress)
       ├─ SaveService         (meta + cosmetics + Threads-woven)
       ├─ NetworkService      (Mirror host/client; Steam Lobby wrapper)
       ├─ LoomService         (which threads have been woven; sibling impact)
       ├─ CombatService       (damage formula, poise rules, AI tick)
       ├─ AbilityService      (Loom Charge consumption + cooldowns)
       ├─ DialogueService    (Pixel Crushers wrapper, scripted)
       ├─ AudioService       (3-layer music + SFX + ambient)
       └─ RuntimePerfService (frame-budget, auto-LOD scaling)
```

### Networking model (authoritative host)

- **Host owns world state** (enemy positions, HP, AI decisions).
- **Clients send inputs** → host validates → broadcasts state.
- **Latency compensation**: client-side prediction for player movement only; abilities are host-validated.
- **Reconnect support**: host disconnects → lobby migrates to client; run state preserved via embedded SaveData.

## 3. Data layer (ScriptableObjects)

- `SectorDataSO` — arenas, enemy spawn tables, boss, music, environment scene reference
- `ThreadDataSO` — thread effect, sibling impact, visual
- `WeaponDataSO` — sword/dagger/bow/shield variant
- `AbilityDataSO` — Loom Charge cost, cooldown, VFX, network behaviour
- `BossDataSO` — multi-phase script, music cues, victory cinematic
- `EnemyDataSO` — HP, poise, AI behaviour
- `DialogueNodeSO` + `LineBankSO` — scripted dialogue (no LLM)

## 4. Loom system (Cycle 2 diegetic)

```
LoomService (singleton on host)
  ├─ ActiveThreads      (per-run picks)
  ├─ WovenThreads       (persistent; cross-twin impact)
  ├─ PendingSiblingImpact (queued effects for the other twin's next run)
  └─ ApplyToNextRun()

LoomVisualController (per scene)
  ├─ Spawns thread-lines in arenas
  ├─ Listens to player.PullThread() input
  └─ Visualises the woven Loom in the Vestibule (3D tapestry geometry)
```

## 5. Combat system

- `PlayerCombatController` runs an `AbilityStateMachine` (Idle, Light1, Light2, Light3, Heavy, Dodge, Ability, Stagger).
- `EnemyAI` uses behaviour-tree (with Burst-compiled tick path on host).
- Damage flow: attack hits collider → host validates window + animation phase → `CombatService.ApplyDamage(source, target, base, modifiers)` → RPC to clients.
- Hit-stop: 50–120ms freeze on hit-confirm (juice for game-feel).
- Camera shake: stylized minimal (Priya's accessibility toggle disables it).

## 6. Save schema (simplified)

```json
{
  "version": 1,
  "meta": {
    "sectorsCleared": ["echoes_pelion"],
    "vestibuleUpgrades": ["first_revive","loom_capacity_2"],
    "cosmetics": {"cassia":["laurel_circlet"],"lior":["twin_dagger_obsidian"]},
    "wovenThreads": [{"id":"thread_echoes_revive","wovenBy":"cassia","siblingAffected":true}]
  },
  "currentRun": {
    "twin": "cassia",
    "sectorId": "drowned_agora",
    "arenaIndex": 2,
    "weapon": "sword_shield",
    "activeThreads": ["agora_echo"],
    "hp": 80,
    "loomCharge": 2
  }
}
```

## 7. Scenes

- `Bootstrap.unity` — service locator, loads MainMenu
- `MainMenu.unity` — title, continue, new run, lobby, settings, credits, cosmetics
- `Vestibule.unity` — the persistent hub with the Loom
- `Sector_01_EchoesOfPelion.unity` through `Sector_06_LoomsHeart.unity`
- `Finale_UsurpersCradle.unity`
- `Credits.unity`

## 8. Performance budget (Diego V)

- 60fps on Steam Deck OLED with 2 players + 24 enemies + boss + VFX
- 120fps on RTX 4070 same load
- Memory <4GB on Steam Deck (cap via Addressables sector-streaming)
- Build size <25GB compressed
- Network: 60Hz player; 30Hz enemies; 10Hz background

## 9. AI in development (NOT runtime)

Claude Code & Claude Agents are used for:
- C# scaffolding (combat state machines, network message handling)
- Boss AI behaviour-tree first-draft (then designer hand-tuned)
- Dialogue tree drafting (writer rewrites for tone)
- Test-case generation for combat balance harness

**Shipping game contains zero runtime LLM calls.** No proxy server, no API key, no internet required (Steam optional).
