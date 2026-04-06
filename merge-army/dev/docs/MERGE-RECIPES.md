# Merge Army — Tower Merge Recipes (v2.0 with Flame)

**File:** MERGE-RECIPES.md
**Version:** 2.0
**Created:** 2026-01-06
**Updated:** 2026-01-06
**Project:** Merge Army

---

## Quick Reference Card

### Tier 1 → Tier 2 (Basic → Hybrid) — 6 Combinations

```
┌─────────────┬─────────────┬──────────────────────────────────────┐
│   Tower A   │   Tower B   │           Result (Tier 2)            │
├─────────────┼─────────────┼──────────────────────────────────────┤
│   Arrow     │   Ice       │   Frost Arrow (damage + slow)        │
│   Arrow     │   Cannon    │   Multi Arrow (3 projectiles)        │
│   Arrow     │   Flame     │   Flame Arrow (damage + burn)        │
│   Ice       │   Cannon    │   Freeze Cannon (splash + slow)      │
│   Ice       │   Flame     │   Frost Flame (slow + burn)          │
│   Cannon    │   Flame     │   Flame Cannon (splash + burn)       │
└─────────────┴─────────────┴──────────────────────────────────────┘
```

### Tier 2 → Tier 3 (Hybrid → Ultimate) — 6+ Combinations

```
┌─────────────┬─────────────┬──────────────────────────────────────┐
│   Tower A   │   Tower B   │           Result (Tier 3)            │
├─────────────┼─────────────┼──────────────────────────────────────┤
│   Frost     │   Multi     │   Blizzard Arrow (slow + 3 arrows)   │
│   Arrow     │   Arrow     │                                      │
├─────────────┼─────────────┼──────────────────────────────────────┤
│   Frost     │   Flame     │   Inferno Arrow (slow + burn +       │
│   Arrow     │   Arrow     │   3 arrows)                          │
├─────────────┼─────────────┼──────────────────────────────────────┤
│   Frost     │   Freeze    │   Arctic Cannon (strong slow +       │
│   Arrow     │   Cannon    │   splash)                            │
├─────────────┼─────────────┼──────────────────────────────────────┤
│   Multi     │   Freeze    │   Storm Cannon (3 arrows + splash +  │
│   Arrow     │   Cannon    │   slow)                              │
├─────────────┼─────────────┼──────────────────────────────────────┤
│   Flame     │   Freeze    │   Volcano Cannon (splash + burn +    │
│   Cannon    │   Cannon    │   slow)                              │
├─────────────┼─────────────┼──────────────────────────────────────┤
│   Frost     │   Flame     │   Phoenix Storm (slow + massive      │
│   Flame     │   Arrow     │   burn: 8 dmg/sec 3sec)              │
└─────────────┴─────────────┴──────────────────────────────────────┘
```

---

## All Tower Stats

### Tier 1 (Basic Towers) — Cost: 50 coins each

| Tower | Damage | Attack Speed | Range | Special | Visual |
|-------|--------|--------------|-------|---------|--------|
| **Arrow** | 10 | 1.0/sec | 100 | Single target | Green arrow |
| **Cannon** | 25 | 0.5/sec | 120 | Splash (30 radius) | Red cannon |
| **Ice** | 5 | 0.8/sec | 90 | Slow 50% for 1s | Blue crystal |
| **Flame** 🔥 | 8 | 0.8/sec | 95 | Burn: 3 dmg/sec for 3s (9 total) | Orange fire |

### Tier 2 (Hybrid Towers) — Merge only (free)

| Tower | Recipe | Damage | Attack Speed | Range | Special | Visual |
|-------|--------|--------|--------------|-------|---------|--------|
| **Frost Arrow** | Arrow + Ice | 12 | 1.0/sec | 100 | Slow 50% for 1s | Green + Blue swirl |
| **Multi Arrow** | Arrow + Cannon | 10 × 3 | 1.0/sec | 100 | 3 projectiles | Green + Red burst |
| **Flame Arrow** 🔥 | Arrow + Flame | 10 | 1.0/sec | 100 | Burn: 5 dmg/sec 3s (15 total) | Green + Orange flame |
| **Freeze Cannon** | Ice + Cannon | 25 | 0.5/sec | 120 | Splash + Slow 50% | Blue + Red frost |
| **Flame Cannon** 🔥 | Cannon + Flame | 25 | 0.5/sec | 120 | Splash + Burn: 5 dmg/sec 3s | Red + Orange inferno |
| **Frost Flame** 🔥 | Ice + Flame | 10 | 0.8/sec | 95 | Slow 50% + Burn: 4 dmg/sec 3s | Blue + Orange swirl |

### Tier 3 (Ultimate Towers) — Merge only (free)

| Tower | Recipe | Damage | Attack Speed | Range | Special | Visual |
|-------|--------|--------|--------------|-------|---------|--------|
| **Blizzard Arrow** | Frost + Multi | 15 × 3 | 1.0/sec | 110 | 3 projectiles + Slow | White + Green storm |
| **Inferno Arrow** 🔥 | Frost + Flame | 12 × 3 | 1.0/sec | 110 | 3 arrows + Burn: 5 dmg/sec 3s | White + Orange inferno |
| **Arctic Cannon** | Frost + Freeze | 35 | 0.5/sec | 130 | Splash + Slow 80% | White + Blue freeze |
| **Storm Cannon** | Multi + Freeze | 25 × 3 | 0.8/sec | 120 | 3 projectiles + Splash + Slow | Purple storm |
| **Volcano Cannon** 🔥 | Flame + Freeze | 40 | 0.5/sec | 130 | Splash + Burn: 6 dmg/sec 3s + Slow | Red + Orange volcano |
| **Phoenix Storm** 🔥 | Frost Flame + Flame Arrow | 20 | 0.8/sec | 115 | Slow + Burn: 8 dmg/sec 3s (24 total) | Gold + Purple phoenix |

---

## Merge Rules

### ✅ Valid Merges
- 2 DIFFERENT tower types
- Same tier (Tier 1 + Tier 1, or Tier 2 + Tier 2)
- Order doesn't matter (Arrow + Ice = Ice + Arrow)

### ❌ Invalid Merges
- Same tower type (Arrow + Arrow = nothing)
- Different tiers (Tier 1 + Tier 2 = nothing)
- Tower + Empty grid = nothing

### Merge Process
1. Player drags Tower A
2. Hover over Tower B
3. If valid merge: show ghost preview of result
4. Drop Tower A on Tower B
5. Both towers disappear
6. New hybrid tower appears at drop location
7. Play merge animation (swirl + flash + sound)

---

## Flame Tower Mechanics 🔥

### Burn Effect
- **Base Burn:** 3 damage per second for 3 seconds (9 total)
- **Hybrid Burn:** 5-8 damage per second for 3 seconds (15-24 total)
- **Stacking:** Multiple Flame hits refresh duration (don't stack damage)
- **Visual:** Enemy glows orange/red with fire particles
- **Sound:** Crackling fire when burn is applied

### Burn vs. Other Effects
| Effect | Duration | Stacks? | Priority |
|--------|----------|---------|----------|
| Burn | 3 seconds | Refreshes | Always applies |
| Slow | 1 second | Refreshes | Always applies |
| Splash | Instant | N/A | Instant damage |

### Burn Strategy
- **Best vs. Fast Enemies:** DoT kills them even if they reach base
- **Best vs. Bosses:** High HP = more burn ticks = massive damage
- **Combo with Slow:** Slowed enemies take full burn duration
- **Weak vs. Immune:** (Future: add fire-resistant enemies)

---

## Strategy Tips (For Players)

### Early Game (Level 1-2)
- Start with 2-3 Arrow towers (cheap, fast damage)
- Add 1 Flame tower for burn damage
- Save coins for key merges

### Mid Game (Level 3-4)
- **Best Early Hybrid:** Flame Arrow (single-target DPS king)
- **Best Crowd Control:** Flame Cannon (splash + burn)
- **Best Utility:** Frost Flame (slow + burn = perma-damage)

### Late Game (Level 5 + Boss)
- **Best Single-Target:** Phoenix Storm (24 burn damage + slow)
- **Best AoE:** Volcano Cannon (splash + burn + slow)
- **Best Balanced:** Inferno Arrow (3 burning arrows)

### Pro Tips 🔥
- **Burn + Slow = Death:** Slowed enemies can't escape the fire
- **Refresh Burn:** Keep hitting boss to refresh burn timer
- **Flame Placement:** Put Flame hybrids near path bends for max uptime
- **Economy:** Flame towers pay for themselves with burn damage

---

## Code Implementation Notes

### Recipe Lookup Table
```dart
const Map<TowerType, Map<TowerType, TowerType>> mergeRecipes = {
  // Tier 1 → Tier 2
  TowerType.arrow: {
    TowerType.ice: TowerType.frostArrow,
    TowerType.cannon: TowerType.multiArrow,
    TowerType.flame: TowerType.flameArrow,
  },
  TowerType.ice: {
    TowerType.arrow: TowerType.frostArrow,
    TowerType.cannon: TowerType.freezeCannon,
    TowerType.flame: TowerType.frostFlame,
  },
  TowerType.flame: {
    TowerType.arrow: TowerType.flameArrow,
    TowerType.ice: TowerType.frostFlame,
    TowerType.cannon: TowerType.flameCannon,
  },
  TowerType.cannon: {
    TowerType.arrow: TowerType.multiArrow,
    TowerType.ice: TowerType.freezeCannon,
    TowerType.flame: TowerType.flameCannon,
  },
  // Tier 2 → Tier 3 (simplified - check both directions)
  TowerType.frostArrow: {
    TowerType.multiArrow: TowerType.blizzardArrow,
    TowerType.flameArrow: TowerType.infernoArrow,
    TowerType.freezeCannon: TowerType.arcticCannon,
  },
  TowerType.flameArrow: {
    TowerType.multiArrow: TowerType.infernoArrow,
    TowerType.freezeCannon: TowerType.phoenixStorm,
  },
  TowerType.freezeCannon: {
    TowerType.flameCannon: TowerType.volcanoCannon,
  },
  TowerType.frostFlame: {
    TowerType.flameArrow: TowerType.phoenixStorm,
    TowerType.flameCannon: TowerType.volcanoCannon,
  },
  // ... add remaining Tier 2 recipes
};
```

### Burn Effect Implementation
```dart
class Enemy {
  double hp;
  bool isBurning = false;
  double burnDamagePerSec = 0;
  double burnTimeRemaining = 0;
  
  void applyBurn(double dps, double duration) {
    isBurning = true;
    burnDamagePerSec = max(burnDamagePerSec, dps); // Use highest DPS
    burnTimeRemaining = duration; // Refresh duration
  }
  
  void update(double dt) {
    if (isBurning) {
      hp -= burnDamagePerSec * dt;
      burnTimeRemaining -= dt;
      if (burnTimeRemaining <= 0) {
        isBurning = false;
      }
    }
  }
}
```

---

## Visual Design Notes

### Color Coding
- **Arrow:** Green (#4CAF50)
- **Cannon:** Red (#F44336)
- **Ice:** Blue (#2196F3)
- **Flame:** Orange (#FF9800)
- **Frost Flame:** Blue + Orange swirl
- **Flame Cannon:** Red + Orange inferno
- **Tier 3:** Add white/gold glow + particle effects

### Burn Visual
- **Enemy:** Orange/red glow + fire particles
- **UI:** Small flame icon with damage number
- **Sound:** Crackling fire + sizzle

### Size Scaling
- **Tier 1:** 32x32 pixels
- **Tier 2:** 40x40 pixels
- **Tier 3:** 48x48 pixels

---

## Balance Notes

### Why Flame Adds Depth
1. **DoT changes math:** Burn damage adds up over time
2. **Risk/reward:** Burn is great if enemy lives long enough
3. **Boss killer:** High-HP bosses take massive burn damage
4. **Fast enemy counter:** DoT kills fast enemies even if they leak

### Potential Balance Issues
- **Burn might be OP:** 24 damage over 3 sec is huge vs. 100 HP base
  - **Fix:** Cap burn damage or reduce DPS
- **Burn + Slow perma-lock:** Enemies might never move
  - **Fix:** Cap slow at 80%, burn doesn't stack
- **Flame hybrids too strong:** 4 Flame combos might dominate
  - **Fix:** Make Flame hybrids cost more or have lower base damage

### Testing Checklist
- [ ] Is burn damage noticeable but not game-breaking?
- [ ] Are all 6 Tier 2 hybrids viable (not just Flame ones)?
- [ ] Can players afford enough towers before first merge?
- [ ] Is Phoenix Storm (best single-target) achievable by Level 5?
- [ ] Does burn feel satisfying (visual + sound + damage)?

---

## Complete Tower Count

| Tier | Basic | Hybrid | Ultimate | Total |
|------|-------|--------|----------|-------|
| **Tier 1** | 4 | - | - | 4 |
| **Tier 2** | - | 6 | - | 6 |
| **Tier 3** | - | - | 6+ | 6+ |
| **TOTAL** | **4** | **6** | **6+** | **16+** |

**16+ unique towers** to discover and master! 🔥

---

**Designer Notes:** Flame tower transforms Merge Army from "tower defense with merging" into "tower defense with alchemy." Players will experiment to find all 16+ combinations. The burn mechanic adds a time-based damage dimension that rewards strategic positioning and timing.

**Priority:** Make the burn visual JUICY. Fire particles, screen shake on big burn ticks, satisfying sizzle sounds. This is the "wow" factor.
