# SF Combat System - Overview

**SF Combat System** (`StraightForwardCombatSystem`) is a modular melee combat framework built from independent Actor Components and data assets.

---

## 🎯 Key Features

- 🧩 **Modular Components:** `USFCombatComponent` (actions + state machine), `USFStatsComponent` (health / stamina), `USFHitDetectionComponent` (sweep traces), `USFTargetingComponent` (lock-on).
- 📊 **Data Driven Weapons:** `USFWeaponDataAsset` holds combo montages, block / dodge / hit montages, damage and stamina costs.
- 🎬 **Animation Driven Timing:** `SF Hitbox`, `SF Combo Window` and `SF Parry Window` Anim Notify States.
- 🛡️ **Defense:** Block with damage mitigation, parry window that staggers the attacker, dodge with invulnerability.
- ✨ **Skills:** `USFSkillDataAsset` with cooldowns and stamina costs.
- 🤖 **AI Ready:** Behavior Tree tasks `SF Attack` and `SF Block For Duration`.
- 🎯 **ISFDamageable:** any actor **or component** can receive SF damage.

---

## 📦 Included Example Content

| Asset | Description |
| :--- | :--- |
| `Levels/HowToUse` | Third Person demo room with two training dummies. Left Mouse attacks, Right Mouse blocks. |
| `Combat/AM_SFUnarmed_Attack_01..03` | Attack montages with Hitbox and Combo Window notify states. |
| `Combat/DA_SFUnarmedWeapon` | Unarmed weapon data asset (3-hit combo). |
| `Blueprints/HowToUse/BP_CombatDemoController`, `BP_SFTrainingDummy` | Component setup, input and a damage receiver example. |

**Supported engine version:** Unreal Engine 5.8.
