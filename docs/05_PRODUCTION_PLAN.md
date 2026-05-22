# 📅 Production Plan — Aetherloom

> 24-month ship plan. Phases are ordered. The single critical-path action is hiring a combat designer in Phase 1.

## Team (7–9 people)

| Role | FT/PT | Duration |
|---|---|---|
| Lead designer / programmer | FT | 24 months |
| **Combat designer** | FT | 18 months (Phase 1–6) — **critical path** |
| 3D environment artist | FT | 18 months (Phase 2–7) |
| 3D character artist + animator | FT | 18 months (Phase 2–7) |
| Technical artist (shaders + perf) | FT | 12 months (Phase 1–4) |
| VFX artist | PT | 12 months (Phase 3–7) |
| Composer | Commission | 4 months total (Phase 3–6) |
| Sound designer | PT | 8 months (Phase 4–7) |
| QA tester | FT | Final 4 months (Phase 6–7) |

**Total team cost over 24 months: ~$320–480k.** Plus ~$25k in commissioned assets (shader, OST, VA, key art). Total: **$345–505k**.

## Phase plan (24 months)

### Phase 1 — Foundation + Combat Designer Hire
*Output: combat designer in seat; toon-shader prototype; pre-prod doc finalised*

- **Hire combat designer** (Day 1 critical path — Diego's Cycle 2 mandate)
- Set up Unity 6 LTS URP project; Service Locator; Save service
- Commission toon shader (deliverable Month 2)
- Implement Mirror + Steam Lobby skeleton; round-trip latency test
- Pre-production design doc revisions
- Internal milestone: toon shader on a single character at 60fps Steam Deck

### Phase 2 — Vertical Slice (Run One)
*Output: Vestibule + Echoes of Pelion + Stag-Crowned boss playable solo and 2-player*

- Build Vestibule scene (Loom centerpiece)
- Build Sector 1 (Echoes of Pelion) 4 arenas
- Commission twin character models + 80 anims total
- Build Stag-Crowned boss
- Implement Loom thread system (diegetic in-world)
- Implement light + heavy + dodge + Loom Charge ability for one weapon
- Net code: 2-player play-through end-to-end
- **Look-lock at Month 3** (Sora + Elena + Diego V's go/no-go)
- Internal milestone: Run One fully playable

### Phase 3 — Sectors 2–3
*Output: ~6h playable build*

- Build Sector 2 (Drowned Agora) + Auctioneer boss
- Build Sector 3 (Ember Catacombs) + Forge-Wretch boss
- Author 12 more enemy variants
- Implement 4 weapons (2 per twin)
- Commission Phase 1 OST (4 tracks)
- Implement Loom Thread expansion (12 threads available)

### Phase 4 — Steam page + wishlist push + Sectors 4–5
*Output: Steam page live, 8,000 wishlists target*

- Build Sector 4 (Storm Causeway) + Aether-Tyrant boss
- Build Sector 5 (Garden of Names) + Mourner boss
- Publish Steam page
- Coordinate creator outreach (Olexa, Retromation, ManlyBadassHero for narrative angle, Splattercatgaming)
- TikTok shorts (2/week from this point)
- Reddit AMAs: r/Roguelites + r/HadesTheGame + r/childrenofmorta
- Internal milestone: 8,000 wishlists

### Phase 5 — Steam Next Fest + Sector 6
*Output: Public demo (Run One, 30 min), 18,000 wishlists target*

- Polish vertical slice demo
- Submit to Steam Next Fest
- Live coverage with creators
- Build Sector 6 (Loom's Heart) + Weaver boss
- Commission OST Phase 2 (4 more tracks)
- Internal milestone: 18,000 wishlists

### Phase 6 — Finale + Polish
*Output: complete game build*

- Build Finale (Usurper's Cradle) + Usurper God boss
- Commission OST Phase 3 (4 final tracks)
- Commission voice acting (~600 lines)
- Implement 30 meta-progression Loom Threads
- Implement Doom Threads (challenge mode)
- Implement cosmetics (60 total)

### Phase 7 — Accessibility + Cert + Launch Prep
*Output: cert-ready build*

- Full accessibility pass (Priya's spec)
- Story / Standard / Loomtrial difficulty tuning
- Steam Deck verified submission
- PS5 + Xbox Series + Switch 2 cert prep (parallel)
- Closed beta with 200 testers from r/Roguelites + Hades community
- Localisation: EN at launch + queue ES/DE/FR/JP for post-launch

### Phase 8 — Launch
*Output: Day 1 PC release; console releases staggered*

- Steam Day 1 1.0 launch at $24.99
- Game Pass Day-1 (target — publisher pipeline supports this)
- Live community moderation (Amara)
- PS5 + Xbox launches +90 days post-PC
- Switch 2 launch +180 days post-PC
- Patch hotfixes; balance pass at Week 2 and Week 6

### Phase 9 — Post-launch (3 months tail beyond 24 months)
*Output: 2 free updates + paid DLC*

- Free Update 1: 4 new Loom Threads + balance pass
- Free Update 2: 2 new weapons + 8 new cosmetics
- Paid DLC 1: "The Twelfth Sector" ($9.99, new sector + boss + 8 threads)

## Risk register

| Risk | Mitigation |
|---|---|
| **Combat designer hire fails** | This is the #1 critical path. If no hire by Month 2, scope-shift to slower, parry-focused combat (less specialist-dependent). |
| Look-lock fails Month 3 | Diego V + Sora + Elena gate; if fail, drop custom toon shader and use Unity built-in URP stylized lighting. |
| Hades 2 1.0 timing collision | Monitor monthly; can shift launch ±120 days |
| Mirror network bugs | Pre-budget 4 weeks of network polish in Phase 5 |
| Console cert delays | Stagger launches — PC first, console +90/+180 |
| Wishlist below 12,000 at Phase 5 end | Marketing escalation: paid ads + publisher signing pivot |

## Budget breakdown

| Item | Cost |
|---|---|
| Lead designer/programmer (24 mo FT) | $96,000 |
| Combat designer (18 mo FT) | $90,000 |
| 3D environment artist (18 mo FT) | $75,000 |
| 3D character artist + animator (18 mo FT) | $75,000 |
| Technical artist (12 mo FT) | $60,000 |
| VFX artist (12 mo PT) | $30,000 |
| Sound designer (8 mo PT) | $25,000 |
| QA (4 mo FT) | $16,000 |
| **Subtotal team** | **$467,000** |
| Commissioned toon shader | $1,500 |
| Commissioned OST (12 tracks) | $3,500 |
| Voice acting (8 actors, ~600 lines) | $5,000 |
| Key art + marketing capsule | $1,500 |
| Bespoke combat SFX | $1,500 |
| **Subtotal commissions** | **$13,000** |
| Marketing (Next Fest, paid ads) | $5,000 |
| Console SDKs / cert fees | $5,000 |
| Contingency 10% | $49,000 |
| **Total** | **~$539,000** |

At the upper edge of the $350–500k envelope; achievable by trimming PT roles or extending PT durations into FT contracted equivalents. Honest range: **$350–540k**.
