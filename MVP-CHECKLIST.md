# Merge Army — MVP Feature Checklist

**File:** MVP-CHECKLIST.md
**Version:** 1.0
**Created:** 2026-04-06
**Project:** Merge Army
**Target:** 8 weeks to MVP

---

## MVP Definition

**Goal:** A playable, fun tower defense game with the core merge mechanic.
**NOT MVP:** Co-op, online features, 16+ towers, elemental system, multiple levels

**MVP Mantra:** "One level, 4 towers, merge works, win/lose clear"

---

## Phase 1: Core Loop (Week 1-2) — MUST HAVE ✅

### 1.1 Grid & Placement
- [ ] 10x8 grid renders on screen
- [ ] Tap grid cell to place tower
- [ ] Tower costs coins (start with 200, towers cost 50)
- [ ] Cannot place on occupied cell
- [ ] Cannot place if insufficient coins

### 1.2 Base System
- [ ] Base at one end of map (bottom)
- [ ] Base has 100 HP
- [ ] HP bar displays (green 100-70, yellow 69-40, red 39-0)
- [ ] Enemies deal 10 damage when reaching base

### 1.3 Enemy System (1 Type)
- [ ] Basic enemy spawns at top
- [ ] Enemy walks toward base along path
- [ ] Enemy has 50 HP
- [ ] Enemy dies when HP = 0 (disappears)
- [ ] Enemy damages base when reaching it

### 1.4 Tower System (1 Type)
- [ ] Arrow Tower (green, basic damage)
- [ ] Tower auto-targets nearest enemy in range (100 pixels)
- [ ] Tower shoots projectile every 1 second
- [ ] Projectile deals 10 damage
- [ ] Tower has 100 pixel range

### 1.5 Wave System
- [ ] Wave spawns 10 enemies over 30 seconds
- [ ] Wave counter displays (Wave 1/1)
- [ ] Wave complete when all enemies defeated

### 1.6 Win/Lose Conditions
- [ ] VICTORY screen: All enemies defeated + base HP > 0
- [ ] GAME OVER screen: Base HP = 0
- [ ] Both screens have "Replay" button
- [ ] Both screens have "Menu" button

### 1.7 Basic UI
- [ ] Top bar: Wave counter, coins, base HP
- [ ] Bottom bar: Tower selection (Arrow button)
- [ ] Coin counter updates when placing tower
- [ ] Kill counter (optional but nice)

---

## Phase 2: Merge Mechanic (Week 3-4) — MUST HAVE ✅

### 2.1 Basic Merge (Same Tower)
- [ ] Drag one tower onto another tower
- [ ] Merge requires 2 towers of SAME type (Arrow + Arrow)
- [ ] Merge produces Tier 2 tower (2x damage, bigger sprite)
- [ ] Merge animation (0.3s glow + scale up)
- [ ] Invalid merge preview (red highlight if can't merge)

### 2.2 Multiple Tower Types (3 More)
- [ ] Cannon Tower (red, 25 damage, slow attack 0.5/sec)
- [ ] Ice Tower (blue, 5 damage, slows enemy 50% for 1s)
- [ ] Flame Tower (orange, 8 damage, burn 3 dmg/sec for 3s)

### 2.3 Hybrid Merge (Different Towers)
- [ ] Arrow + Ice = Frost Arrow (damage + slow)
- [ ] Arrow + Cannon = Multi Arrow (3 projectiles)
- [ ] Arrow + Flame = Flame Arrow (damage + burn 5 dmg/sec 3s)
- [ ] Ice + Cannon = Freeze Cannon (splash + slow)
- [ ] Ice + Flame = Frost Flame (slow + burn)
- [ ] Cannon + Flame = Flame Cannon (splash + burn)

### 2.4 Merge UI/UX
- [ ] Drag-to-merge interaction (intuitive)
- [ ] Ghost preview when hovering over valid merge target
- [ ] Merge result preview (show what tower you'll get)
- [ ] Merge success feedback (flash + sound + particle)
- [ ] Merge fail feedback (red flash + return to position)

---

## Phase 3: Content (Week 5-6) — MUST HAVE ✅

### 3.1 Levels (5 Total)
- [ ] Level 1: Tutorial (10 Basic enemies, teaches placement)
- [ ] Level 2: 15 enemies (Basic + Fast), teaches merge
- [ ] Level 3: 20 enemies (introduce Molten - fire element)
- [ ] Level 4: 25 enemies (introduce Frost - ice element)
- [ ] Level 5: Boss wave (1 big enemy, 500 HP)

### 3.2 Enemy Types (4 Total)
- [ ] Basic: 50 HP, normal speed, neutral element
- [ ] Fast: 30 HP, 2x speed, neutral element
- [ ] Molten: 80 HP, slow, fire element (weak to Ice 3x, immune to Burn)
- [ ] Frost: 60 HP, normal, ice element (weak to Fire 2x, immune to Slow)

### 3.3 Elemental System
- [ ] Damage multipliers (3x weak, 0.5x resist, 2x weak)
- [ ] Immunity system (Burn immune, Slow immune)
- [ ] Visual indicator (element icon above enemy HP bar)
- [ ] Tutorial hints ("Molten weak to Ice!")

### 3.4 Progression
- [ ] Star rating (3 stars: 80+ HP, 2 stars: 50-79 HP, 1 star: 1-49 HP)
- [ ] Level unlock (earn stars to unlock next level)
- [ ] Level select screen (5 levels, locked/unlocked state)

---

## Phase 4: Polish (Week 7-8) — MUST HAVE ✅

### 4.1 Visual Polish
- [ ] Tower sprites (4 basic + 6 hybrid + 3 ultimate = 13 unique sprites)
- [ ] Enemy sprites (4 types: Basic, Fast, Molten, Frost)
- [ ] Projectile sprites (arrow, cannonball, ice shard, fireball)
- [ ] Merge animation (swirl + flash + scale)
- [ ] Death animation (enemy poof/fade)
- [ ] Base hit animation (screen shake)

### 4.2 Audio
- [ ] Background music (looping, 2-3 min track)
- [ ] Tower shoot SFX (4 types: arrow, cannon, ice, flame)
- [ ] Merge SFX (success sound)
- [ ] Enemy death SFX
- [ ] Base damage SFX
- [ ] UI click SFX

### 4.3 UI/UX Polish
- [ ] Main menu (Play, Settings, Credits)
- [ ] Settings screen (music volume, SFX volume)
- [ ] Pause menu (Resume, Restart, Menu)
- [ ] Damage numbers (pop up when enemy hit)
- [ ] Weakness/resist text ("CRITICAL!" / "RESISTED")
- [ ] Tutorial overlays (first time hints)

### 4.4 Performance
- [ ] 60 FPS on iPhone 11+ / equivalent Android
- [ ] No crashes during 10-minute play session
- [ ] Load time < 3 seconds per level
- [ ] No memory leaks (test with 100+ enemies)

### 4.5 Save System
- [ ] Save progress (stars, unlocked levels)
- [ ] Save persists between app restarts
- [ ] Reset progress option (in Settings)

---

## Phase 5: Launch Prep (Week 8) — MUST HAVE ✅

### 5.1 Testing
- [ ] Playtest with 10 players (friends/family)
- [ ] Collect feedback (fun rating, difficulty, bugs)
- [ ] Fix critical bugs (crashes, progression blockers)
- [ ] Balance tuning (enemy HP, tower damage, economy)

### 5.2 Store Assets
- [ ] App icon (1024x1024)
- [ ] Screenshots (5-8 per platform)
- [ ] App description (150-300 words)
- [ ] Keywords (tower defense, merge, strategy)

### 5.3 Technical
- [ ] iOS build (TestFlight ready)
- [ ] Android build (Play Beta ready)
- [ ] Privacy policy (required for app stores)
- [ ] Analytics (Firebase or simple event tracking)

---

## NOT in MVP (Post-Launch) ❌

### Multiplayer
- [ ] Local co-op (2 players, 1 device)
- [ ] Online co-op (remote play via Firebase)
- [ ] Leaderboards (fastest clear times)

### Additional Content
- [ ] Tier 3 ultimate towers (6+ towers)
- [ ] More than 5 levels
- [ ] Endless mode
- [ ] Daily challenges

### Monetization
- [ ] In-app purchases (tower skins, extra levels)
- [ ] Ads (rewarded videos, interstitials)
- [ ] Premium version (no ads)

### Advanced Features
- [ ] Tower skins (cosmetic only)
- [ ] Achievements (complete X levels, merge 100 times)
- [ ] Social features (friend codes, gift system)

---

## MVP Success Criteria

**Functional:**
- ✅ All 5 levels playable start-to-finish
- ✅ Merge system works (6 hybrid towers)
- ✅ Elemental system works (4 enemy types)
- ✅ Win/lose conditions clear
- ✅ No crashes or game-breaking bugs

**Fun:**
- ✅ Playtesters rate 7/10 or higher for "fun"
- ✅ Playtesters understand merge in < 2 minutes
- ✅ Playtesters want to replay levels for better stars

**Technical:**
- ✅ 60 FPS on target devices
- ✅ < 100 MB download size
- ✅ No critical bugs (crashes, progression blockers)

---

## Priority Order (If Time Runs Short)

**P0 (Must Ship):**
1. Core loop (place → shoot → win/lose)
2. Merge system (at least 3 hybrids)
3. 3 levels (tutorial, mid, boss)
4. No crashes

**P1 (Should Ship):**
5. All 5 levels
6. All 6 hybrid towers
7. Elemental system
8. Star progression

**P2 (Nice to Have):**
9. Tier 3 ultimate towers
10. Audio polish
11. Visual effects
12. Settings menu

**P3 (Post-Launch):**
13. Co-op multiplayer
14. Leaderboards
15. Monetization
16. Extra levels

---

## Timeline Summary

| Phase | Duration | Features |
|-------|----------|----------|
| **Phase 1:** Core Loop | Week 1-2 | Grid, 1 tower, 1 enemy, win/lose |
| **Phase 2:** Merge | Week 3-4 | Merge system, 4 tower types, 6 hybrids |
| **Phase 3:** Content | Week 5-6 | 5 levels, 4 enemy types, elementals |
| **Phase 4:** Polish | Week 7 | Visual, audio, UI, performance |
| **Phase 5:** Launch | Week 8 | Testing, store assets, builds |

**Total:** 8 weeks to MVP

---

**Designer Notes:** MVP means "Minimum" — resist feature creep. If Merge Army is fun with just Phase 1-3, ship it. Add co-op and Tier 3 towers post-launch based on player feedback.

**Rule:** If a feature isn't in this checklist, it's NOT in MVP. No exceptions without owner approval.
