# Merge Army

**Co-op tower defense game for couples — merge towers, race against time**

---

## 🎮 How to Play

1. **Place Towers** — Tap grid to place basic towers (Arrow, Cannon, Ice, Flame)
2. **Merge Towers** — Drag 2 DIFFERENT towers together → hybrid tower with combined powers
3. **Defend Base** — Towers auto-shoot enemies walking toward your base
4. **Win** — Defeat all waves + base HP > 0
5. **Lose** — Base HP = 0 → GAME OVER

---

## 🔥 Merge System

### Tier 1 → Tier 2 (Basic → Hybrid)
```
Arrow + Ice     = Frost Arrow      (damage + slow)
Arrow + Cannon  = Multi Arrow      (3 projectiles)
Arrow + Flame   = Flame Arrow      (damage + burn)
Ice + Cannon    = Freeze Cannon    (splash + slow)
Ice + Flame     = Frost Flame      (slow + burn)
Cannon + Flame  = Flame Cannon     (splash + burn)
```

### Tier 2 → Tier 3 (Hybrid → Ultimate)
```
Frost Arrow + Multi Arrow    = Blizzard Arrow    (slow + 3 arrows)
Frost Arrow + Flame Arrow    = Inferno Arrow     (slow + burn + 3 arrows)
Flame Cannon + Freeze Cannon = Volcano Cannon    (splash + burn + slow)
...and more!
```

**16+ unique towers to discover!**

---

## ❄️🔥 Elemental System

### Enemy Types
| Enemy | HP | Speed | Element | Weakness | Resistance | Immunity |
|-------|-----|-------|---------|----------|------------|----------|
| Basic 🟢 | 50 | Normal | Neutral | — | — | — |
| Fast 🟡 | 30 | Fast | Neutral | — | — | — |
| Molten 🔥 | 80 | Slow | Fire | **3x from Frost** | 50% from Fire | Burn |
| Frost ❄️ | 60 | Normal | Ice | **2x from Fire** | 50% from Frost | Slow |

**Strategy:** Scout enemies and bring the RIGHT towers, not just the strongest!

---

## 📁 Project Structure

```
merge-army/
├── ideas/merge-army/          # Idea validation, decision doc
├── projects/merge-army/
│   ├── planning/
│   │   └── PRD-v1.0.md       # Product requirements
│   ├── dev/docs/
│   │   ├── tech-design-v1.0.md    # Technical architecture
│   │   ├── MERGE-RECIPES.md       # All 16+ tower recipes
│   │   ├── ELEMENTAL-SYSTEM.md    # Enemy types, resistances
│   │   └── VS-CODE-COPILOT-GUIDE.md  # Coding guide
│   └── monitoring/
│       └── status.md         # Project tracker
└── README.md                 # This file
```

---

## 🚀 Getting Started

### Prerequisites
- Flutter SDK (3.x+)
- VS Code with Flutter + Copilot extensions

### Setup
```bash
git clone https://github.com/bbugs280/merge-army.git
cd merge-army
flutter create .
flutter pub add flame flame_audio firebase_core firebase_auth firebase_database riverpod
```

### Run
```bash
flutter run
```

---

## 📋 Development Status

**Current Phase:** Pre-development (design complete)
**Target MVP:** 8 weeks
**Team:** Wayne + Vincent

### Milestones
- [x] Idea validated (7.5/10)
- [x] PRD complete (v1.0)
- [x] Technical design complete
- [x] Merge system designed (16+ towers)
- [x] Elemental system designed
- [ ] Flutter + Flame setup
- [ ] Core prototype (grid, towers, enemies)
- [ ] Merge mechanic implementation
- [ ] 5 levels designed + implemented
- [ ] Playtest (10 players)
- [ ] MVP launch (TestFlight + Play Beta)

---

## 📚 Documentation

| Document | Description |
|----------|-------------|
| [PRD-v1.0.md](projects/merge-army/planning/PRD-v1.0.md) | Product requirements, features, user stories |
| [tech-design-v1.0.md](projects/merge-army/dev/docs/tech-design-v1.0.md) | Technical architecture, Flutter + Flame setup |
| [MERGE-RECIPES.md](projects/merge-army/dev/docs/MERGE-RECIPES.md) | All 16+ tower recipes, stats, strategies |
| [ELEMENTAL-SYSTEM.md](projects/merge-army/dev/docs/ELEMENTAL-SYSTEM.md) | Enemy types, damage multipliers, code |
| [VS-CODE-COPILOT-GUIDE.md](projects/merge-army/dev/docs/VS-CODE-COPILOT-GUIDE.md) | Coding guide with Copilot prompts |
| [status.md](projects/merge-army/monitoring/status.md) | Current progress, milestones, blockers |

---

## 🎯 Core Design Principles

1. **Simple to Learn:** 30 seconds to understand
2. **Deep to Master:** 16+ towers, elementals, strategy
3. **Discovery Fun:** Experiment to find all merge recipes
4. **Meaningful Choices:** Merge now or wait for better combo?
5. **Fair Challenge:** Elementals reward adaptation, not just DPS

---

## 🔧 Tech Stack

- **Engine:** Flutter + Flame
- **Language:** Dart
- **Backend:** Firebase (Auth, Realtime DB, Leaderboards)
- **State:** Riverpod
- **Platform:** iOS + Android

---

## 📞 Team

- **Wayne** — Developer
- **Vincent** — Developer

**Group Chat:** Claw-IdeaFactory (WhatsApp)

---

## 📄 License

Private project — all rights reserved

---

**GitHub:** https://github.com/bbugs280/merge-army
