# SF Combat System - Troubleshooting

---

### ❓ The attack animation does not play
**Solution:**
Your Anim Blueprint needs a `DefaultSlot` node, and the weapon must have montages in `LightAttackCombos`. Check stamina too: attacks are skipped without enough stamina.

---

### ❓ Attacks play but never deal damage
**Solution:**
1. The montage needs an **SF Hitbox** notify state.
2. The sockets must exist on the traced mesh (`Set Weapon Mesh Component`).
3. The target must use an object type listed in `TargetObjectTypes` (Pawn / PhysicsBody by default) and implement `ISFDamageable` (or own an SF Combat component).

---

### ❓ The character gets stuck after one attack (older versions)
**Solution:**
Fixed in the current version: actions now return to `Idle` when their montage ends and buffered combo inputs are consumed. Update the plugin.
