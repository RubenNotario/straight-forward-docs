# SF Combat System - Quickstart Example

A 3-hit unarmed combo against a training dummy.

---

## 🧍 Player

1. Add **SF Stats**, **SF Hit Detection** and **SF Combat** to your character.
2. Hit Detection: `Set Weapon Mesh Component (Mesh)`, `StartSocketName = lowerarm_r`, `EndSocketName = hand_r`, `TraceRadius = 30`.
3. Combat: `DefaultWeapon = DA_SFUnarmedWeapon`.
4. Input: Attack ➔ `Do Light Attack`. Block pressed ➔ `Start Block`, released ➔ `Stop Block`.

## 🎯 Training Dummy

1. Actor with a mesh (collision profile **PhysicsActor** or **Pawn**), **SF Stats** and **SF Combat** components.
2. Bind **On Health Changed** / **On Death** on the Stats component for feedback.

> 💡 Open `Levels/HowToUse` in the plugin content to try the combo in play mode.
