# Tower Defense Y — Product Requirements Document

**File:** PRD-v1.0.md
**Version:** 1.0
**Created:** 2026-01-06
**Status:** DRAFT
**Project:** Tower Defense Y
**Author:** Planner (AI Agent)

---

## Executive Summary

Merge Army is a simple tower defense game where enemies walk toward your base. Place towers to stop them. Merge 3 towers to make them stronger. Survive all waves to win.

**Core Loop:** Place → Merge → Defend → Win
**Target:** iOS + Android
**Timeline:** MVP in 6-8 weeks (simplified scope)
**Team:** 1-2 developers (Wayne + Vincent)

**Design Principle:** Simple enough to learn in 30 seconds, deep enough to master.

---

## Core Gameplay Loop

1. **Start Level** — Enemies spawn and walk toward your base
2. **Place Towers** — Tap grid to place basic towers
3. **Merge Towers** — Drag 2 DIFFERENT towers together → 1 HYBRID tower
4. **Defend Base** — Towers auto-shoot enemies; stop them from reaching base
5. **Win** — Defeat all enemy waves (base HP > 0)
6. **Lose** — Base HP reaches 0 (too many enemies reached it)

**Simple Rules:**
- Enemies walk from spawn → base
- Towers shoot enemies automatically
- 2 DIFFERENT towers = merge → 1 hybrid tower with combined effects
- Survive all waves = WIN
- Base destroyed = GAME OVER

**Merge Examples:**
- Arrow + Ice = Frost Arrow (damage + slow)
- Arrow + Cannon = Multi Arrow (shoots 3 arrows at once)
- Ice + Cannon = Freeze Cannon (splash + slow)

---

## Key Features (MVP Scope)

### 1. Tower System (HYBRID MERGE)

**4 Basic Towers** (Tier 1 — buy with coins):
| Tower | Damage | Attack Speed | Special | Cost |
|-------|--------|--------------|---------|------|
| **Arrow** | Medium (10) | Fast (1.0/sec) | Single target | 50 |
| **Cannon** | High (25) | Slow (0.5/sec) | Splash damage (area) | 50 |
| **Ice** | Low (5) | Medium (0.8/sec) | Slows enemy 50% for 1 sec | 50 |
| **Flame** | Low-Medium (8) | Medium (0.8/sec) | Burn: 3 damage/sec for 3 sec (9 total) | 50 |

**Flame Tower Details:**
- Burn effect stacks (2 Flame hits = 6 damage/sec for 3 sec)
- Burn damage ignores armor (if armor mechanic added later)
- Visual: Enemy glows orange/red with fire particles
- Strong vs. fast enemies (DoT kills them even if they reach base)

**6 Hybrid Towers** (Tier 2 — merge 2 different basics):
| Hybrid | Recipe | Damage | Special |
|--------|--------|--------|---------|
| **Frost Arrow** | Arrow + Ice | Medium (12) | Slows enemy 50% for 1 sec |
| **Multi Arrow** | Arrow + Cannon | Medium (10 x3) | Shoots 3 arrows at once |
| **Flame Arrow** | Arrow + Flame | Medium (10) + Burn | Burn: 5 damage/sec for 3 sec (15 total) |
| **Freeze Cannon** | Ice + Cannon | High (25) | Splash + slows 50% for 1 sec |
| **Flame Cannon** | Cannon + Flame | High (25) + Burn | Splash + Burn: 5 damage/sec for 3 sec |
| **Frost Flame** | Ice + Flame | Medium (10) | Slow 50% + Burn: 4 damage/sec for 3 sec |

**New Flame Hybrids:**
- **Flame Arrow:** Single target + strong burn (best vs. bosses)
- **Flame Cannon:** AoE + burn (best vs. groups)
- **Frost Flame:** Slow + burn (enemies can't escape the fire!)

**6+ Ultimate Towers** (Tier 3 — merge 2 different Tier 2):
| Ultimate | Recipe | Damage | Special |
|----------|--------|--------|---------|
| **Blizzard Arrow** | Frost Arrow + Multi Arrow | High (15 x3) | Slows + multi-shot |
| **Arctic Cannon** | Frost Arrow + Freeze Cannon | Very High (35) | Splash + strong slow (80%) |
| **Storm Cannon** | Multi Arrow + Freeze Cannon | Extreme (25 x3) | Multi-shot + splash + slow |
| **Inferno Arrow** | Flame Arrow + Multi Arrow | High (12 x3) + Burn | 3 arrows + Burn: 5 dmg/sec 3sec |
| **Volcano Cannon** | Flame Cannon + Freeze Cannon | Extreme (40) + Burn | Splash + Burn + slow 50% |
| **Phoenix Storm** | Frost Flame + Flame Arrow | Very High (20) + Burn | Slow + Burn: 8 dmg/sec 3sec (24 total) |

**Flame-Based Ultimates:**
- **Inferno Arrow:** 3 burning arrows = massive DoT (best single-target DPS)
- **Volcano Cannon:** AoE explosion + burn + slow (best crowd control)
- **Phoenix Storm:** Perma-slow + massive burn damage (execution tower)

**Merge Rules:**
- Drag 2 DIFFERENT towers together → hybrid tower
- Hybrid = combined effects of both parents
- Can merge Tier 1 + Tier 1 → Tier 2
- Can merge Tier 2 + Tier 2 (different types) → Tier 3
- Cannot merge same tower type (Arrow + Arrow = nothing)
- Merged tower appears where you dropped them
- Cost to place basic towers: 50 coins each
- Hybrid towers cannot be bought — only merged

### 2. Economy (SIMPLE)
- **Starting Coins:** 200 per level
- **Tower Cost:** 50 coins (basic), hybrids are free (just merge)
- **Earn Coins:** Kill enemies (5-15 coins per kill based on enemy type)
- **Goal:** Build strong hybrid towers before boss wave

### 3. Base & Win/Lose
- **Base HP:** Start with 100 HP
- **Enemy Damage:** Each enemy deals 10 damage when reaching base
- **Win:** Defeat all enemy waves AND base HP > 0
- **Lose:** Base HP reaches 0 → GAME OVER screen

**Visual Feedback:**
- Base shows HP bar (green → yellow → red)
- Screen shake when base takes damage
- "GAME OVER" text when base destroyed
- "VICTORY" text when all waves defeated

### 2. Base & Win/Lose (CLARIFIED)
- **Base HP:** Start with 100 HP
- **Enemy Damage:** Each enemy deals 10 damage when reaching base
- **Win:** Defeat all enemy waves AND base HP > 0
- **Lose:** Base HP reaches 0 → GAME OVER screen

**Visual Feedback:**
- Base shows HP bar (green → yellow → red)
- Screen shake when base takes damage
- "GAME OVER" text when base destroyed
- "VICTORY" text when all waves defeated

### 3. Level Design (MVP)
- **5 Levels** (increasing difficulty):
  - Level 1: Tutorial (10 enemies, teaches placement + merge)
  - Level 2-4: More enemies, mixed types
  - Level 5: Boss wave (big enemy, lots of HP)

- **4 Enemy Types** (elemental system):
  | Enemy | HP | Speed | Element | Weakness | Resistance | Immunity |
  |-------|-----|-------|---------|----------|------------|----------|
  | **Basic** | 50 | Normal | Neutral | None | None | None |
  | **Fast** | 30 | Fast | Neutral | None | None | None |
  | **Molten** 🔥 | 80 | Slow | Fire | 3x from Frost | 50% less from Fire | Burn |
  | **Frost** ❄️ | 60 | Normal | Ice | 2x from Fire | 50% less from Frost | Slow |

**Elemental Strategy:**
- Molten enemies: Use Frost towers (3x damage!), avoid Flame towers
- Frost enemies: Use Flame towers (2x damage!), avoid Ice towers
- Neutral enemies: All towers work normally
- Mix tower types to handle different enemy compositions

### 4. Progression (SIMPLE)
- **Stars:** Earn 1-3 stars per level based on base HP remaining
  - 3 stars: 80+ HP left
  - 2 stars: 50-79 HP left
  - 1 star: 1-49 HP left
- **Unlock:** New levels by earning stars (no coins, no shop)
- **Replay:** Replay levels to get better star rating

### 5. Co-op (OPTIONAL FOR MVP)
- **Phase 1:** Single player only (ship faster)
- **Phase 2:** Add local co-op (2 players, 1 device)
- **Phase 3:** Online co-op (stretch goal)

**Decision:** Start with single-player. Add co-op after core loop is fun.

---

## User Stories

### As a player, I want to:
1. Tap to place towers on the grid
2. Drag 3 towers together to merge them
3. See towers shoot enemies automatically
4. Watch my base HP bar and protect it
5. Win by defeating all enemy waves
6. See "VICTORY" screen when I win
7. See "GAME OVER" screen when base is destroyed
8. Replay levels to get more stars

**That's it. Keep it stupid simple.**

---

## Acceptance Criteria (MVP)

### Core Gameplay
- [ ] Can tap grid to place towers
- [ ] Can drag 3 same-tier towers to merge them
- [ ] Merged tower is bigger + shoots stronger
- [ ] Towers auto-shoot nearest enemy
- [ ] Enemies walk from spawn → base
- [ ] Enemies deal damage to base when reaching it

### Win/Lose Conditions
- [ ] Base starts with 100 HP
- [ ] Base HP shows as visible bar (green → yellow → red)
- [ ] Win screen: "VICTORY" when all waves defeated + base HP > 0
- [ ] Lose screen: "GAME OVER" when base HP = 0
- [ ] Can replay level after win or lose

### Levels
- [ ] 5 levels with increasing enemy count
- [ ] 2 enemy types (Basic, Fast)
- [ ] Level 1 is tutorial (teaches placement + merge)
- [ ] Level 5 has boss enemy (big HP)
- [ ] Earn 1-3 stars based on remaining base HP

### UI/UX
- [ ] Main menu with "Play" button
- [ ] Level select screen (5 levels)
- [ ] In-game: grid, base HP bar, wave counter
- [ ] Victory/Game Over screens with "Replay" and "Menu" buttons
- [ ] Simple enough for a 10-year-old to understand in 30 seconds

### Performance
- [ ] 60 FPS on iPhone 11+ / equivalent Android
- [ ] No crashes during 10-minute play session
- [ ] Save progress between sessions

---

## Technical Requirements

### Platform
- **Primary:** iOS 14+, Android 10+
- **Secondary:** Consider iPad/tablet optimization

### Backend
- **Authentication:** Firebase Auth (anonymous + optional accounts)
- **Multiplayer:** Firebase Realtime Database or Photon
- **Leaderboards:** Firebase or PlayFab
- **Analytics:** Firebase Analytics

### Engine Options (Builder will recommend)
- **Option A: Unity**
  - Pros: Best TD assets, proven multiplayer, cross-platform
  - Cons: Larger build size, heavier engine
  
- **Option B: Flutter + Flame Engine**
  - Pros: Lightweight, single codebase, fast iteration
  - Cons: Less TD-specific assets, newer engine

**Decision:** Builder to evaluate and recommend by [date]

---

## Monetization (TBD)

**Recommended Model:** Hybrid F2P
- **Free:** Base game with 5 levels, 5 towers
- **IAP:** 
  - Unlock tower skins ($0.99-$2.99)
  - Extra levels ($1.99 per pack)
  - No pay-to-win (all towers earnable through play)
- **Optional:** Remove ads ($2.99 one-time)

**Final decision:** Owner to confirm after MVP testing

---

## Risks & Mitigations

| Risk | Impact | Mitigation |
|------|--------|------------|
| Co-op desync ruins experience | High | Extensive testing, rollback system |
| Merge mechanic feels clunky | High | Prototype early, iterate on UX |
| Levels too easy/hard | Medium | Playtest with 10+ couples, adjust |
| Monetization feels predatory | Medium | Keep cosmetic-only, no pay-to-win |
| Performance issues on older devices | Medium | Target iPhone 11+ as minimum |

---

## Timeline (SIMPLIFIED MVP)

| Phase | Duration | Deliverables |
|-------|----------|--------------|
| **Week 1-2:** Core Loop | 2 weeks | Grid, tower placement, enemy walking, base HP |
| **Week 3-4:** Merge + Combat | 2 weeks | Tower merging, shooting, win/lose conditions |
| **Week 5-6:** Levels + UI | 2 weeks | 5 levels, menus, victory/game over screens |
| **Week 7-8:** Polish + Test | 2 weeks | Bug fixes, playtest with 10 players, performance |

**MVP Target:** Week 8 (single-player, 5 levels, core loop complete)

**Phase 2 (Post-MVP):**
- Local co-op (2 players, 1 device)
- Online co-op
- More tower types, more levels

---

## Success Metrics (Post-Launch)

- **Retention:** 40% D1, 20% D7, 10% D30
- **Session Length:** 10-15 minutes average
- **Co-op Rate:** 70%+ of sessions are 2-player
- **Rating:** 4.5+ stars on App Store / Play Store
- **Revenue:** $2-5 ARPPU (if F2P model)

---

## Open Questions

1. **Engine:** Unity vs. Flutter? (Builder to recommend)
2. **Art Style:** Pixel art, low-poly 3D, or 2D cartoon?
3. **Audio:** Original music or royalty-free assets?
4. **Online Co-op:** Required for MVP or can launch with local-only first?
5. **Pricing:** F2P, premium ($4.99), or hybrid?

---

## Next Steps

1. **Builder:** Create technical design doc (engine recommendation, architecture)
2. **Builder:** Set up GitHub repo, create issues from this PRD
3. **Owner:** Approve PRD, confirm engine choice, art style
4. **Builder:** Start core tower system prototype

---

**Planner signing off.** Ready to hand off to Builder for technical design.
