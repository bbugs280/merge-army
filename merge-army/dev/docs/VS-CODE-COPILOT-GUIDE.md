# Merge Army — VS Code Copilot Setup Guide

**File:** VS-CODE-COPILOT-GUIDE.md
**Version:** 1.0
**Created:** 2026-01-06
**Project:** Merge Army

---

## Quick Start (5 minutes)

### Step 1: Clone the Repo
```bash
git clone https://github.com/bbugs280/merge-army
cd merge-army
```

### Step 2: Create Flutter Project
```bash
flutter create .
```

### Step 3: Open in VS Code
```bash
code .
```

### Step 4: Install VS Code Extensions
Press `Cmd+Shift+X` and install:
- **Flutter** (by Dart Code)
- **Dart** (by Dart Code)
- **GitHub Copilot** (by GitHub)
- **GitHub Copilot Chat** (by GitHub)
- **Flutter Widget Snippets** (optional)

### Step 5: Install Dependencies
```bash
flutter pub add flame flame_audio firebase_core firebase_auth firebase_database riverpod shared_preferences in_app_purchase
```

---

## VS Code Copilot Prompts for Merge Army

### Phase 1: Project Setup

**Prompt 1 — Initialize Flame Game:**
```
Create a Flutter + Flame game setup for a tower defense game called "Merge Army".
- Main.dart with MaterialApp and GameWidget
- MergeArmyGame class extending Flame Game
- Basic game loop (update, render)
- Grid-based placement system (10x8 grid)
- Base with 100 HP that enemies walk toward
Include comments explaining each part.
```

**Prompt 2 — Create Tower Base Class:**
```
Create a Tower class for a tower defense game with hybrid merge system:
- TowerType enum: arrow, cannon, ice, flame, frostArrow, multiArrow, flameArrow, freezeCannon, flameCannon, frostFlame, blizzardArrow, infernoArrow, arcticCannon, stormCannon, volcanoCannon, phoenixStorm
- TowerTier enum: tier1, tier2, tier3
- position (Vector2), damage, attackSpeed, range
- slowsEnemy (bool), appliesBurn (bool), burnDamagePerSec (double), burnDurationSec (double)
- projectileCount (int), splashDamage (bool), splashRadius (double)
- update() method for targeting enemies
- shoot() method that creates projectiles with burn effect
Use Flame's PositionComponent as base class.
Add Dart doc comments.
```

**Prompt 3 — Create Enemy Class (Elemental System):**
```
Create an Enemy class with elemental affinities:
- EnemyElement enum: neutral, fire, ice
- HP, speed, maxHP, baseSpeed
- enemyType: basic, fast, molten (fire), frost (ice)
- Elemental multipliers: Molten takes 3x from Ice, 0.5x from Fire; Frost takes 2x from Fire, 0.5x from Ice
- Immunities: Molten immune to Burn, Frost immune to Slow
- takeDamage(damage, attackElement) with multiplier calculation
- applyBurn() and applySlow() that check immunity
- update() for movement, burn damage, slow duration
Include path following with waypoints.
```

---

### Phase 2: Tower Merge System

**Prompt 4 — Merge Logic (HYBRID SYSTEM):**
```
Create a MergeSystem class for hybrid tower merging:
- mergeTowers(Tower a, Tower b) method
- Validation: requires 2 DIFFERENT tower types of SAME tier
- Recipe system: Arrow+Ice=FrostArrow, Arrow+Cannon=MultiArrow, Ice+Cannon=FreezeCannon
- Tier 2→3: FrostArrow+MultiArrow=BlizzardArrow, etc.
- Returns new hybrid Tower or null if invalid merge
- Cannot merge same tower types (Arrow+Arrow = nothing)
Add unit tests for all merge combinations.
```

**Prompt 5 — Merge UI:**
```
Create a tower selection UI for merge mechanic:
- Long press to select a tower
- Show selection indicator (glow/highlight)
- Allow selecting up to 3 towers
- Show merge button when 3 identical towers selected
- Show merge animation on success
Use Flutter widgets overlaying the Flame game.
```

---

### Phase 3: Co-op System

**Prompt 6 — Local Co-op Input:**
```
Create a multi-touch input system for local co-op:
- Support 2 simultaneous players on same device
- Each player can place towers independently
- Use GestureDetector with multiple pointers
- Show which player is which (color coding)
- Shared game state (lives, timer, enemies)
```

**Prompt 7 — Firebase Sync:**
```
Create a Firebase Realtime Database sync system:
- Sync tower positions, types, tiers
- Sync enemy positions and HP
- Sync shared lives and timer
- Update frequency: 10-20 times per second
- Handle connection state (connecting, connected, disconnected)
- Use StreamBuilder for real-time updates
```

---

### Phase 4: Level System

**Prompt 8 — Wave Manager:**
```
Create a WaveSystem class:
- Define enemy waves (enemy type, count, spawn interval)
- Spawn enemies at entry point
- Track wave progress
- Trigger boss wave at end
- Call onWaveComplete() callback
Use data-driven design with JSON level configs.
```

**Prompt 9 — Level Data Structure:**
```
Create a LevelConfig class:
- levelNumber, gridLayout, enemyPath
- List<WaveConfig> waves
- startingLives, timeLimit
- rewards (coins on completion)
Load from JSON files in assets/levels/ folder.
```

---

## VS Code Keyboard Shortcuts (Mac)

| Action | Shortcut |
|--------|----------|
| **Copilot Suggestions** | `Tab` to accept, `Esc` to dismiss |
| **Copilot Chat** | `Cmd+Shift+P` → "Copilot Chat" |
| **Run Flutter App** | `F5` or `Cmd+Shift+5` |
| **Hot Reload** | `Cmd+S` (auto on save) or `R` in terminal |
| **Find File** | `Cmd+P` |
| **Find in Files** | `Cmd+Shift+F` |
| **Terminal** | `Ctrl+` ` (backtick) |
| **Format Code** | `Shift+Option+F` |

---

## Recommended Folder Structure

```
merge-army/
├── lib/
│   ├── main.dart                    # App entry
│   ├── game/
│   │   ├── tower_defense_game.dart  # Flame Game class
│   │   ├── components/
│   │   │   ├── tower.dart
│   │   │   ├── enemy.dart
│   │   │   ├── projectile.dart
│   │   │   ├── grid.dart
│   │   │   └── ui/
│   │   ├── systems/
│   │   │   ├── wave_system.dart
│   │   │   ├── merge_system.dart
│   │   │   ├── pathfinding.dart
│   │   │   └── collision.dart
│   │   └── levels/
│   │       ├── level_1.dart
│   │       └── ...
│   ├── services/
│   │   ├── firebase_service.dart
│   │   ├── multiplayer_service.dart
│   │   └── save_service.dart
│   ├── models/
│   │   ├── tower_model.dart
│   │   ├── enemy_model.dart
│   │   └── game_state.dart
│   └── ui/
│       ├── main_menu.dart
│       ├── level_select.dart
│       └── hud.dart
├── assets/
│   ├── images/
│   ├── audio/
│   └── levels/
├── test/
│   ├── tower_test.dart
│   ├── merge_system_test.dart
│   └── ...
└── pubspec.yaml
```

---

## Copilot Best Practices for This Project

### ✅ Do:
1. **Be specific** — "Create a Tower class with these 5 properties..." not "make a tower"
2. **Provide context** — Paste relevant code before asking for additions
3. **Iterate** — Accept partial suggestions, then ask Copilot to continue
4. **Use comments as prompts** — Write `// TODO: Create merge animation` then let Copilot fill it
5. **Ask for tests** — "Write unit tests for this merge function"

### ❌ Don't:
1. **Don't accept blindly** — Review Copilot code for bugs
2. **Don't over-rely** — Understand what the code does
3. **Don't ignore errors** — Fix Flutter/Dart errors immediately

---

## Debugging with Copilot

**When you hit a bug, ask Copilot:**
```
I'm getting this error: [paste error]
In this file: [paste relevant code]
What's wrong and how do I fix it?
```

**Example:**
```
Error: The method 'mergeTowers' isn't defined for the type 'MergeSystem'.
Here's my MergeSystem class: [paste code]
Fix this.
```

---

## Testing Checklist (Ask Copilot to Help)

- [ ] Tower placement works on all grid cells
- [ ] Towers auto-target nearest enemy
- [ ] Projectiles hit enemies and deal damage
- [ ] Merge requires exactly 3 identical towers
- [ ] Merged tower has correct stats (+50% per tier)
- [ ] Enemies follow path correctly
- [ ] Wave spawning works
- [ ] Lives decrease when enemies reach exit
- [ ] Win condition triggers after boss wave
- [ ] Lose condition triggers at 0 lives
- [ ] Timer tracks completion time
- [ ] Local co-op: 2 players can play simultaneously
- [ ] Online co-op: state syncs between devices

---

## Daily Workflow

### Morning (15 min)
1. Pull latest: `git pull`
2. Review yesterday's code
3. Ask Copilot: "What should I work on next based on the PRD?"

### Coding Session (1-2 hours)
1. Open relevant file
2. Write comment describing what you want
3. Let Copilot suggest code
4. Review, edit, test
5. Hot reload to see changes

### End of Session (10 min)
1. Run tests: `flutter test`
2. Commit: `git add -A && git commit -m "What you did"`
3. Push: `git push`
4. Update status.md with progress

---

## Common Copilot Patterns

### Pattern 1: "Continue this code"
```dart
// Create 5 tower types with different stats
// Arrow: basic damage, fast attack
// Cannon: splash damage, slow attack
// Ice: slow effect, medium damage
// Lightning: chain damage, medium attack
// Heal: heals nearby towers, no damage
[Let Copilot continue]
```

### Pattern 2: "Refactor this"
Select code → `Cmd+Shift+P` → "Copilot: Refactor this"
```
Make this code more readable and add error handling.
```

### Pattern 3: "Explain this"
Select code → `Cmd+Shift+P` → "Copilot: Explain this"
```
Explain how this merge system works.
```

### Pattern 4: "Write tests"
```
Write unit tests for the MergeSystem.mergeTowers() method.
Test valid merges, invalid merges (wrong count, wrong type, wrong tier).
```

---

## Next Steps

1. **Clone repo** → `git clone https://github.com/bbugs280/merge-army`
2. **Open VS Code** → `code merge-army`
3. **Install extensions** (Flutter, Dart, Copilot)
4. **Run `flutter create .`**
5. **Start Issue #1** — Use Copilot Prompt #1 above

**Stuck?** Paste the error here and I'll help debug.

---

**Builder out.** Happy coding! 🚀
