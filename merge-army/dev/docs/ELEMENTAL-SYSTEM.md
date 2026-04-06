# Merge Army — Elemental System Design

**File:** ELEMENTAL-SYSTEM.md
**Version:** 1.0
**Created:** 2026-01-06
**Project:** Merge Army

---

## Overview

Enemies have elemental affinities that create rock-paper-scissors dynamics:
- **Fire enemies** weak to Frost (3x damage), resist Fire (50%), immune to Burn
- **Frost enemies** weak to Fire (2x damage), resist Frost (50%), immune to Slow
- **Neutral enemies** no resistances or weaknesses

**Strategic Impact:** Players must scout enemy compositions and adapt tower choices.

---

## Enemy Types

### 1. Basic (Neutral)
| Stat | Value |
|------|-------|
| **HP** | 50 |
| **Speed** | 1.0 (normal) |
| **Element** | Neutral |
| **Weakness** | None |
| **Resistance** | None |
| **Immunity** | None |
| **Visual** | Green blob, simple |
| **First Appearance** | Level 1 (tutorial) |

### 2. Fast (Neutral)
| Stat | Value |
|------|-------|
| **HP** | 30 |
| **Speed** | 2.0 (very fast) |
| **Element** | Neutral |
| **Weakness** | None |
| **Resistance** | None |
| **Immunity** | None |
| **Visual** | Yellow streak, motion blur |
| **First Appearance** | Level 2 |

### 3. Molten (Fire) 🔥
| Stat | Value |
|------|-------|
| **HP** | 80 |
| **Speed** | 0.7 (slow) |
| **Element** | Fire |
| **Weakness** | **3x damage from Frost/Ice towers** |
| **Resistance** | **50% less damage from Fire towers** |
| **Immunity** | **Burn effect (takes 0 burn damage)** |
| **Visual** | Glowing red/orange, lava cracks, fire particles |
| **First Appearance** | Level 3 |
| **Sound** | Low rumble, crackling fire |

### 4. Frost (Ice) ❄️
| Stat | Value |
|------|-------|
| **HP** | 60 |
| **Speed** | 1.0 (normal) |
| **Element** | Ice |
| **Weakness** | **2x damage from Fire towers** |
| **Resistance** | **50% less damage from Frost/Ice towers** |
| **Immunity** | **Slow effect (moves at full speed)** |
| **Visual** | Blue/white ice crystal, frost trail |
| **First Appearance** | Level 3 |
| **Sound** | Cracking ice, wind chime |

### 5. Boss (Varies)
| Stat | Value |
|------|-------|
| **HP** | 500-1000 |
| **Speed** | 0.5 (very slow) |
| **Element** | Varies by level (Fire, Frost, or Neutral) |
| **Weakness** | Depends on element |
| **Resistance** | Depends on element |
| **Immunity** | Depends on element |
| **Visual** | Huge, unique design per element |
| **First Appearance** | Level 5 (final boss) |

---

## Damage Multiplier Table

| Attacker → | Neutral Tower | Fire Tower | Frost Tower |
|------------|---------------|------------|-------------|
| **Neutral Enemy** | 1.0x | 1.0x | 1.0x |
| **Molten (Fire)** | 1.0x | 0.5x | **3.0x** |
| **Frost (Ice)** | 1.0x | **2.0x** | 0.5x |

### Examples
```
Arrow Tower (neutral) vs. Molten: 10 damage × 1.0x = 10 damage
Flame Tower (fire) vs. Molten: 8 damage × 0.5x = 4 damage
Ice Tower (frost) vs. Molten: 5 damage × 3.0x = 15 damage ⭐

Arrow Tower (neutral) vs. Frost: 10 damage × 1.0x = 10 damage
Flame Tower (fire) vs. Frost: 8 damage × 2.0x = 16 damage ⭐
Ice Tower (frost) vs. Frost: 5 damage × 0.5x = 2.5 damage
```

---

## Tower Elemental Classification

### Fire Towers 🔥
- Flame (Tier 1)
- Flame Arrow (Tier 2)
- Flame Cannon (Tier 2)
- Frost Flame (Tier 2)
- Inferno Arrow (Tier 3)
- Volcano Cannon (Tier 3)
- Phoenix Storm (Tier 3)

**Effect:** Deal 2x damage to Frost enemies, 0.5x to Molten enemies, apply Burn (unless immune)

### Frost Towers ❄️
- Ice (Tier 1)
- Frost Arrow (Tier 2)
- Freeze Cannon (Tier 2)
- Frost Flame (Tier 2)
- Blizzard Arrow (Tier 3)
- Arctic Cannon (Tier 3)
- Phoenix Storm (Tier 3)

**Effect:** Deal 3x damage to Molten enemies, 0.5x to Frost enemies, apply Slow (unless immune)

### Neutral Towers ⚪
- Arrow (Tier 1)
- Cannon (Tier 1)
- Multi Arrow (Tier 2)

**Effect:** No elemental multipliers (always 1.0x), no status immunities bypassed

**Note:** Some towers have dual elements (e.g., Frost Flame = both Fire + Frost, Phoenix Storm = both). Use the element that favors the enemy (check both, apply best multiplier).

---

## Status Effect Rules

### Burn 🔥
- **Base Effect:** 3-8 damage/sec for 3 seconds
- **Immune:** Molten (Fire) enemies
- **Vulnerable:** Frost enemies take normal burn damage (no multiplier)
- **Stacking:** Refreshes duration (doesn't stack damage)
- **Visual:** Orange/red glow, fire particles
- **Sound:** Crackling fire

### Slow ❄️
- **Base Effect:** 50-80% speed reduction for 1 second
- **Immune:** Frost (Ice) enemies
- **Vulnerable:** Molten enemies take normal slow (no extra effect)
- **Stacking:** Refreshes duration (doesn't stack)
- **Visual:** Blue frost, ice crystals on enemy
- **Sound:** Freezing sound, wind

---

## Code Implementation

### Enemy Class
```dart
enum EnemyElement { neutral, fire, ice }

enum TowerElement { none, fire, ice }

class Enemy {
  double hp;
  final double maxHP;
  final EnemyElement element;
  final double baseSpeed;
  
  // Status effects
  bool isBurning = false;
  double burnDamagePerSec = 0;
  double burnTimeRemaining = 0;
  
  bool isSlowed = false;
  double slowMultiplier = 1.0;
  double slowTimeRemaining = 0;
  
  // Apply damage with elemental multipliers
  void takeDamage(double damage, {TowerElement? attackElement}) {
    double multiplier = _getElementMultiplier(attackElement);
    double finalDamage = damage * multiplier;
    hp -= finalDamage;
    
    // Visual feedback
    if (multiplier > 1.0) {
      showDamageNumber(finalDamage, color: Colors.green); // Weakness hit
    } else if (multiplier < 1.0) {
      showDamageNumber(finalDamage, color: Colors.grey); // Resisted
    }
  }
  
  // Get damage multiplier based on attacker's element
  double _getElementMultiplier(TowerElement? attackElement) {
    if (attackElement == null) return 1.0;
    
    switch (element) {
      case EnemyElement.fire: // Molten enemy
        if (attackElement == TowerElement.ice) return 3.0; // 3x weak to frost
        if (attackElement == TowerElement.fire) return 0.5; // 50% resist fire
        return 1.0;
      
      case EnemyElement.ice: // Frost enemy
        if (attackElement == TowerElement.fire) return 2.0; // 2x weak to fire
        if (attackElement == TowerElement.ice) return 0.5; // 50% resist frost
        return 1.0;
      
      case EnemyElement.neutral: // Basic/Fast
        return 1.0; // No resistances/weaknesses
    }
  }
  
  // Apply burn (does nothing if immune)
  void applyBurn(double dps, double duration) {
    if (element == EnemyElement.fire) return; // Immune to burn
    
    isBurning = true;
    burnDamagePerSec = max(burnDamagePerSec, dps);
    burnTimeRemaining = duration;
  }
  
  // Apply slow (does nothing if immune)
  void applySlow(double multiplier, double duration) {
    if (element == EnemyElement.ice) return; // Immune to slow
    
    isSlowed = true;
    slowMultiplier = multiplier;
    slowTimeRemaining = duration;
  }
  
  void update(double dt) {
    // Burn damage
    if (isBurning && element != EnemyElement.fire) {
      hp -= burnDamagePerSec * dt;
      burnTimeRemaining -= dt;
      if (burnTimeRemaining <= 0) isBurning = false;
    }
    
    // Slow duration
    if (isSlowed && element != EnemyElement.ice) {
      slowTimeRemaining -= dt;
      if (slowTimeRemaining <= 0) {
        isSlowed = false;
        slowMultiplier = 1.0;
      }
    }
  }
  
  double getSpeed() {
    return baseSpeed * slowMultiplier;
  }
  
  // Get visual indicator for element
  String getElementEmoji() {
    switch (element) {
      case EnemyElement.fire: return '🔥';
      case EnemyElement.ice: return '❄️';
      case EnemyElement.neutral: return '';
    }
  }
}
```

### Tower Class (Elemental Classification)
```dart
class Tower {
  final TowerType type;
  final TowerElement element;
  final TowerElement? secondaryElement; // For hybrid towers
  
  // Get the best element for this enemy
  TowerElement getEffectiveElement(Enemy enemy) {
    // If tower has dual elements, use the one that's strong against enemy
    if (secondaryElement != null) {
      double primaryMult = getElementMultiplier(element, enemy);
      double secondaryMult = getElementMultiplier(secondaryElement!, enemy);
      
      return secondaryMult > primaryMult ? secondaryElement! : element;
    }
    
    return element;
  }
  
  double getElementMultiplier(TowerElement towerElement, Enemy enemy) {
    switch (enemy.element) {
      case EnemyElement.fire:
        if (towerElement == TowerElement.ice) return 3.0;
        if (towerElement == TowerElement.fire) return 0.5;
        return 1.0;
      
      case EnemyElement.ice:
        if (towerElement == TowerElement.fire) return 2.0;
        if (towerElement == TowerElement.ice) return 0.5;
        return 1.0;
      
      case EnemyElement.neutral:
        return 1.0;
    }
  }
}

// Tower elemental classifications
const towerElements = {
  TowerType.arrow: TowerElement.none,
  TowerType.cannon: TowerElement.none,
  TowerType.ice: TowerElement.ice,
  TowerType.flame: TowerElement.fire,
  
  TowerType.frostArrow: TowerElement.ice,
  TowerType.multiArrow: TowerElement.none,
  TowerType.flameArrow: TowerElement.fire,
  TowerType.freezeCannon: TowerElement.ice,
  TowerType.flameCannon: TowerElement.fire,
  TowerType.frostFlame: TowerElement.ice, // Use ice as primary (or check both)
  
  TowerType.blizzardArrow: TowerElement.ice,
  TowerType.infernoArrow: TowerElement.fire,
  TowerType.arcticCannon: TowerElement.ice,
  TowerType.stormCannon: TowerElement.ice,
  TowerType.volcanoCannon: TowerElement.fire,
  TowerType.phoenixStorm: TowerElement.fire, // Has both, use fire for burn
};
```

---

## Level Design with Elementals

### Level 1 (Tutorial)
- **Enemies:** 100% Basic (Neutral)
- **Teaches:** Placement, shooting, basic merge
- **No elementals yet**

### Level 2
- **Enemies:** 70% Basic, 30% Fast (all Neutral)
- **Teaches:** Merge hybrids, fast enemy pressure
- **Still no elementals**

### Level 3 (Elemental Introduction)
- **Enemies:** 50% Basic, 25% Molten, 25% Frost
- **Teaches:** Elemental weaknesses (UI hint: "Molten weak to Ice!")
- **First test:** Can player adapt tower choices?

### Level 4
- **Enemies:** 30% Basic, 35% Molten, 35% Frost
- **Challenge:** Mixed elemental composition
- **Strategy:** Bring both Fire + Frost towers

### Level 5 (Boss)
- **Wave 1-4:** Mixed elementals
- **Boss:** Molten OR Frost (random, or player choice)
- **Test:** Did player prepare the right towers?

---

## UI/UX Considerations

### Enemy Health Bar
- **Molten:** Red/orange HP bar with fire icon 🔥
- **Frost:** Blue/white HP bar with ice icon ❄️
- **Neutral:** Green HP bar, no icon
- **Weakness hint:** Show "Weak to Fire!" when player hovers over Frost enemy (first appearance only)

### Damage Numbers
- **Normal damage:** White number
- **Weakness hit (2x-3x):** Green number, bigger font, "CRITICAL!" text
- **Resisted (0.5x):** Grey number, smaller font, "RESISTED" text
- **Immune:** "IMMUNE" text, no damage number

### Tower Selection UI
- Show elemental icon on tower cards (🔥 / ❄️ / ⚪)
- Tooltip: "Strong vs. Frost enemies" or "Strong vs. Molten enemies"

### Tutorial Hints
- First Molten spawn: "💡 Tip: Ice towers deal 3x damage to Molten enemies!"
- First Frost spawn: "💡 Tip: Fire towers deal 2x damage to Frost enemies!"
- First Burn immunity: "💡 Tip: Molten enemies are immune to Burn!"
- First Slow immunity: "💡 Tip: Frost enemies are immune to Slow!"

---

## Strategy Guide (For Players)

### vs. Molten Enemies (Fire)
**DO:**
- ✅ Use Ice towers (3x damage!)
- ✅ Use Frost hybrids (Frost Arrow, Freeze Cannon)
- ✅ Focus fire with neutral towers (Arrow, Cannon)

**DON'T:**
- ❌ Use pure Flame towers (50% damage, burn immune)
- ❌ Rely on burn damage (does nothing)

### vs. Frost Enemies (Ice)
**DO:**
- ✅ Use Flame towers (2x damage!)
- ✅ Use Flame hybrids (Flame Arrow, Flame Cannon)
- ✅ Burn them (no slow, but burn works)

**DON'T:**
- ❌ Use pure Ice towers (50% damage, slow immune)
- ❌ Rely on slow effects (does nothing)

### Mixed Waves (Molten + Frost)
**Best Towers:**
- Neutral towers (Arrow, Cannon, Multi Arrow) — no resistances
- Dual-element hybrids (Frost Flame, Phoenix Storm) — can hit both weaknesses
- Bring both Fire AND Frost towers — swap based on priority target

**Pro Strategy:**
- Identify the BIGGEST threat (highest HP or closest to base)
- Use the counter-element tower for that target
- Use neutral towers for everything else

---

## Balance Notes

### Why This System Works
1. **No "best" tower:** Each tower has counters
2. **Scouting matters:** Players must check enemy composition
3. **Adaptation rewarded:** Players who swap towers succeed
4. **Discovery fun:** Learning weaknesses through play
5. **Boss prep:** Build the right towers BEFORE boss wave

### Potential Balance Issues
- **Molten too tanky?** 80 HP + 50% fire resist = feels unkillable to fire
  - **Fix:** Ensure players have Frost towers available before Molten spawn
- **Frost too fast?** Immune to slow = zooms past defenses
  - **Fix:** Give Frost enemies lower HP (60 vs. 80 for Molten)
- **Neutral towers obsolete?** No resistances = always safe choice
  - **Fix:** Make hybrids significantly stronger to incentivize elemental risk

### Testing Checklist
- [ ] Can players beat Level 3 without knowing elementals? (should be hard but possible)
- [ ] Are tutorial hints clear enough?
- [ ] Do damage numbers clearly show resist/weakness?
- [ ] Is Phoenix Storm (dual-element) viable vs. both types?
- [ ] Does boss feel fair (right element available)?

---

## Enemy Wave Compositions

### Level 1 (Tutorial)
```
Wave 1: 5 Basic
Wave 2: 5 Basic
Wave 3 (Boss): 1 Basic (100 HP, teaches boss mechanic)
```

### Level 2
```
Wave 1: 8 Basic
Wave 2: 5 Basic + 3 Fast
Wave 3: 4 Basic + 6 Fast
Wave 4 (Boss): 1 Fast (200 HP, very fast!)
```

### Level 3 (Elemental Intro)
```
Wave 1: 6 Basic + 2 Molten
Wave 2: 4 Basic + 4 Frost
Wave 3: 3 Molten + 3 Frost
Wave 4 (Boss): 1 Molten (400 HP, weak to Ice!)
```

### Level 4
```
Wave 1: 5 Basic + 5 Molten
Wave 2: 5 Basic + 5 Frost
Wave 3: 4 Molten + 4 Frost + 2 Fast
Wave 4 (Boss): 1 Frost (500 HP, weak to Fire!)
```

### Level 5 (Final)
```
Wave 1: 5 Molten + 5 Frost
Wave 2: 3 Molten + 3 Frost + 4 Fast
Wave 3: 2 Molten + 2 Frost + 6 Basic
Wave 4 (Boss): 1 Elemental Titan (800 HP, random element)
  - Fire Titan: Weak to Ice, immune to Burn
  - Frost Titan: Weak to Fire, immune to Slow
```

---

**Designer Notes:** The elemental system transforms Merge Army from "build strongest towers" into "build RIGHT towers." This is the difference between a generic TD and a strategic puzzle. Make sure the UI telegraphs weaknesses clearly — players should feel smart for exploiting them, not frustrated for guessing wrong.

**Priority:** Damage numbers and immunity text MUST be crystal clear. Players learn through feedback.
