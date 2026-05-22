# 📜 Game Design Document — Aetherloom

> **GDD v1.1** — approved by Creative Director after 18-expert Cycle 2 review (14/18 clean, 4 approved-with-notes, 4 required changes applied).

## 1. High-concept

You are **Cassia** and **Lior** — twin demigods bound to the **Aetherloom**, the celestial tapestry that weaves mortal fate. The Loom has been **broken** by a usurper god. Threads spool loose. Mortals' fates run wild. You delve into the Loom's broken sectors, fight the dream-mythic beings that have escaped, and **re-weave the threads** — except every weave is permanent, and what you weave for yourself bleeds into your sibling's runs.

**Player fantasy:** *I am the demigod weaving fate with my sibling, even when they're not with me.*

**Emotional journey:** Bewilderment (Loom is alive, talking to you) → mastery (combat clicks) → weight (your weave changed your sibling's last run) → catharsis (re-weaving the foundational thread of the world).

**Pillars (do not violate):**
1. **Combat feel above all.** 3D Hades-tier responsiveness is the table-stakes.
2. **2-player drop-in is sacred** — solo and co-op must be equally playable; no co-op-locked content.
3. **The Loom is diegetic.** Threads appear in-world as visible silken lines you can touch and weave — NOT just a menu (Cycle 2 required change).
4. **Stylized 3D, not realism.** Mediterranean dreamscape: ochre cliffs, lapis sea, white marble, gold thread.
5. **Permadeath is partial.** Death costs your current run's weave; meta-progression preserves the Loom's structure.

## 2. Core game loop

```
Vestibule (hub) → Pick sector + weapon + 0–3 starting threads
↓
Descend into sector (3–6 arenas + 1 boss)
↓
Each arena: defeat enemies → choose 1-of-3 Loom upgrades
↓
Boss: defeat → receive Sector Thread (permanent)
↓
Return to Vestibule → weave Sector Thread into Loom → it affects your sibling's next run
↓
Next run
```

## 3. Player verbs (each twin)

| Verb | Input | Notes |
|---|---|---|
| Move / sprint | WASD / left stick | Stamina-free sprint; tight 3D movement |
| Dodge / dash | Space / B | I-frames; cooldown 1s |
| Light attack | LMB | 3-hit combo |
| Heavy attack | RMB hold | Charged; breaks enemy poise |
| Special ability | Q | Weapon-specific; consumes Loom Charge |
| Loom Weave | E | Pull a visible thread in-world to bend an enemy's behaviour briefly (interrupt, redirect) |
| Lock-on | Mouse middle / right stick click | Cycles target |
| Heal | R | Limited charges per run |
| Talk to sibling (banter) | T | Hand-authored `DialogueNodeSO` |
| Pause | Esc | Solo only; co-op pauses are votes |

**Twin asymmetry:** Cassia is sword + shield (block focus, parry windows). Lior is twin daggers + bow (dash-cancel, ranged). Both are equally viable; pure preference.

## 4. The Loom (post-Cycle 2: diegetic)

The Loom is a **physical tapestry in the Vestibule hub**, plus **threads visible in every sector** as glowing silken lines that drift in-world. When you weave a Sector Thread, you literally walk to the Loom and tie a knot — the camera pushes in for a held cinematic frame.

### What threads do

- **Fate threads**: change which boss spawns in your sibling's next sector run
- **Echo threads**: leave an upgrade-shadow in a future arena (your sibling can pick it up)
- **Bond threads**: grant your sibling a one-time revive or shared dash
- **Doom threads**: harder enemy variants spawn for both of you (locked behind challenge runs)

You choose 1–3 threads per run. Threads persist for your sibling whether or not they were in the run.

## 5. Progression

| System | Run start | Late-game ceiling |
|---|---|---|
| Weapons per twin | 1 base | 4 per twin (8 total) |
| Loom Threads available | 6 | 36 |
| Meta upgrades (Vestibule shrine) | 0 | 30 |
| Sectors unlocked | 1 | 6 + finale |
| Boss kills banked | 0 | 7 |
| Cosmetics | 0 | 60 (24 per twin + 12 shared) |

## 6. Sector structure (6 sectors + finale)

| # | Sector | Theme | Boss |
|---|---|---|---|
| **1** | *Echoes of Pelion* | Marble forest + ruined temple (tutorial sector) | The Stag-Crowned (Selvanos) |
| 2 | *The Drowned Agora* | Sunken marketplace | The Auctioneer (Talos-shape) |
| 3 | *Ember Catacombs* | Lava-tinged tombs | The Forge-Wretch (Hephaestion) |
| 4 | *The Storm Causeway* | Aerial bridges + thunder | The Aether-Tyrant (Boreas) |
| 5 | *Garden of Names* | Cozy oasis; quietest arena; ambush combat | The Mourner (Antigone) |
| 6 | *The Loom's Heart* | Inside the tapestry itself | The Weaver (penultimate boss) |
| Finale | *The Usurper's Cradle* | Astral plane | The Usurper God |

## 7. Vertical slice — *Run One: Echoes of Pelion*

**Goal:** Onboard the twins, the Loom, the weave; deliver the first boss. **Duration:** 25–40 min (solo or co-op).

**Cinematic moment (Marcus's Cycle 2 ask):** the first thread-tie at the Loom. Cassia (or Lior) approaches the broken tapestry. A loose thread floats up. The camera pushes in. The thread ties itself with a soft *click*. Sound design: held breath → silken whisper → single tone. Trailer's hero shot.

**Flow:**
1. Vestibule intro: the twins wake to find the Loom broken. Choose weapon. Touch a free thread → first weave tutorial.
2. Descent into Echoes of Pelion. 4 arenas.
3. Arena 1: 6 enemies (marble revenants). Tutorialise light, heavy, dodge.
4. Arena 2: 8 enemies + first elite. Tutorialise heavy-attack-poise-break.
5. Arena 3: 10 enemies + Loom thread visible — player can pull it to redirect an enemy.
6. Arena 4: 12 enemies + first Loom-Charge ability use.
7. Boss: **The Stag-Crowned** — 2-phase fight; phase 2 introduces a Loom Tether the player must sever.
8. Victory: return to Vestibule. First Sector Thread (Echoes-Thread) hangs in the air. Player walks to Loom + ties.

**Objectives (in MissionDataSO):**
- `r1_first_strike` (1)
- `r1_first_dodge` (1)
- `r1_first_heavy` (1)
- `r1_clear_arenas` (4)
- `r1_pull_loom_thread` (1)
- `r1_use_loom_charge` (1)
- `r1_defeat_stag_crowned` (1)
- `r1_weave_first_thread` (1)
- `r1_optional_find_echo` (1, optional, lore unlock)

## 8. Combat detail

**Stamina-free movement.** Dodge is cooldown-gated, not stamina-gated — keeps run flow uninterrupted (Hades model). Loom Charge replaces the "mana" role. 

**Poise:** player has 60; enemies vary 30–200. Heavy attacks chip poise. Parrying breaks enemy poise instantly.

**Damage formula:** `dmg = base * (1 + skillBonus + threadBonus) * crit`.

**Death:** drop the run's accumulated threads at the death spot. Reclaim by reaching it. Die again before reclaiming = the threads return to the Loom, ready for next run (no permanent loss — cozier than Hades).

## 9. Co-op specifics

- **Steam P2P (Mirror)** with Steam Lobbies.
- **Drop-in/drop-out** at any Vestibule.
- **Solo parity**: every encounter is balanced for 1–2 players; HP scales 1.0 → 1.6 with 2 players, enemy count scales 1.0 → 1.4.
- **Friendly fire**: off by default; off in toggle.
- **Shared death state**: if both twins are downed simultaneously, run ends. One twin can revive the other (cost: 1 Loom Charge).

## 10. UI

| Screen | Asset |
|---|---|
| Main menu | Heat UI (custom Mediterranean re-skin) |
| Vestibule hub | Custom 3D scene with Loom centerpiece |
| HUD | Heat UI minimal lower-third |
| Loom (in-hub) | Skill Tree Builder driving a custom 3D thread-tying interaction |
| Co-op lobby | Heat UI + Steam Lobby integration |

## 11. Audio (Hiroshi)

12-track OST commissioned. Identity: **Mediterranean lyre + chorus + percussion** (think *Hades* meets *Assassin's Creed Odyssey* meets *Hollow Knight*). Hero-track: "The First Knot." Boss themes are 4-bar variations of the sector theme — cohesion across re-runs.

## 12. Accessibility (Cycle 2 required change — Priya)

- **Difficulty options**: Story / Standard / Loomtrial. Story = +50% I-frames, -30% enemy damage, unlimited revives.
- **Auto-aim assist** (toggle, gradient strength).
- **Hold-to-toggle** for sprint / block.
- **Colourblind ability palette** (each ability has a primary shape + colour cue).
- **One-handed control layout** (Xbox Adaptive Controller mapping confirmed).
- **Subtitled boss intros + sibling banter** (always-on toggle).
- **Reduced-motion option** for camera shake + Loom particle drift.

## 13. Visual identity (Elena + Sora)

**Stylized 3D toon-shaded Mediterranean dreamscape.** Palette locked Month 3 (Cycle 2 required change): ochre, lapis, marble white, gold thread, oxblood for blood. References: *Hades* (palette warmth), *Hollow Knight* (silhouette clarity), *Hi-Fi Rush* (toon shader), *Cult of the Lamb* (mood). Custom toon shader commissioned Month 1 — Diego V's go/no-go at Month 3.

## 14. Cut-list (if scope slips)

1. Sector 5 (Garden of Names) folds into a sub-area of Sector 4.
2. 4 of 8 weapons (per twin, 2 each minimum).
3. PS5 + Xbox launches deferred to +90 days post-PC.
4. Switch port deferred to +180 days.
5. Doom Threads (challenge layer) folded into a single "Loom Madness" mode.

**Never cut:** the Loom hub, Stag-Crowned boss, the first thread-tie cinematic, 2-player drop-in.

✅ **Approved by Creative Director + 18-expert Cycle 2 (with 4 required changes applied).**
