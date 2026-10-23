# SF Combat System - C++ & Blueprint API

---

## ⚔️ `USFCombatComponent`

### Actions
- **`DoLightAttack()` / `DoHeavyAttack()`**: Plays the next combo montage. Inside a Combo Window the press is buffered and chained.
- **`StartBlock()` / `StopBlock()`**: Blocking state; the first frames open the parry window.
- **`DoDodge()`**: Consumes stamina, plays `DodgeMontage` with invulnerability.
- **`ExecuteSkill(SkillIndex)`** *(bool)*: Plays a skill from `AssignedSkills` if off cooldown and affordable.
- **`EquipWeapon(Weapon)`**: Switches the weapon data asset and resets the combo.

### State
- **`GetCombatState()`** / **`SetCombatState()`** *(ECombatState)*: `Idle`, `Attacking`, `Blocking`, `Parrying`, `Staggered`, `Dashing`, `ExecSkill`, `Dead`.
- **`CanPerformAction()`** *(bool)*: `Idle`, inside a Combo Window or inside a Cancel Window.
- Actions return to `Idle` automatically when their montage ends.

### Events
- **`OnCombatStateChanged(Old, New)`**, **`OnParrySuccess(Attacker)`**, **`OnBlockSuccess(Attacker)`**.

---

## ❤️ `USFStatsComponent`

| Property | Default | | Function / Event | Description |
| :--- | :--- | :--- | :--- | :--- |
| `MaxHealth` / `CurrentHealth` | `100` | | `ModifyHealth(Delta)` | Positive heals, negative damages. |
| `bEnableStamina` | `true` | | `ModifyStamina(Delta)`, `HasEnoughStamina(Cost)` | Stamina helpers. |
| `MaxStamina` / `CurrentStamina` | `100` | | `IsDead()` | `CurrentHealth <= 0`. |
| `StaminaRegenRate` / `StaminaRegenDelay` | `15` / `1 s` | | `OnHealthChanged`, `OnStaminaChanged`, `OnDeath` | Events. |

---

## 🗡️ `USFHitDetectionComponent`

- **`EnableHitbox()` / `DisableHitbox()`**: Normally driven by the `SF Hitbox` notify state.
- **`SetWeaponMeshComponent(Mesh)`**: Component whose sockets are traced (defaults to the actor root).
- **`StartSocketName` / `EndSocketName`** (Default `Weapon_Start` / `Weapon_End`), **`TraceRadius`** (15), **`TargetObjectTypes`** (Pawn, PhysicsBody).
- **`OnHitDetected(HitActor, HitResult)`**: Once per actor per hitbox window.

---

## 🎯 `USFTargetingComponent`

- **`ToggleTargeting()`**, **`EnableTargeting()`**, **`DisableTargeting()`**, **`CycleTarget(bRight)`**, **`GetSelectedTarget()`**.
- Properties: `TargetRadius` (1200), `MaxTargetAngle` (60), `bRequireLineOfSight` (true).

---

## 📚 Data Assets

**`USFWeaponDataAsset`**: `LightAttackCombos`, `HeavyAttackCombos`, `BlockMontage`, `ParrySuccessMontage`, `DodgeMontage`, `HitStunMontage`, `BaseDamage` (15), `StaminaCostPerAttack` (10), `DodgeStaminaCost` (15), `BlockDamageMitigationRatio` (0.75).

**`USFSkillDataAsset`**: `SkillID`, `SkillName`, `SkillIcon`, `SkillMontage`, `CooldownDuration` (5), `StaminaCost` (25), `DamageMultiplier` (1.5), `KnockbackForce` (300).

---

## 🛡️ `ISFDamageable`

`TakeSFDamage(DamageInfo)` *(EDamageResult: Hit, Blocked, Parried, Evaded, Immune)*, `CanBeTargeted()`, `GetTargetLocation()`. Implemented by `USFCombatComponent`, so any actor with a Combat component can be hit.
