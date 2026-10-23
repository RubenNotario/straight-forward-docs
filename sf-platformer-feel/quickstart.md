# SF Platformer Feel - Quickstart Example

---

## 🐺 Coyote Time + Jump Buffer

1. Character ➔ Add Component ➔ **Coyote Time**.
2. Jump input **Pressed**:
   - `Can Jump` ➔ **true**: `Jump`.
   - **false**: `Try Coyote Jump` ➔ **false**: `Register Jump Input`.
3. Bind **On Buffered Jump Triggered** ➔ `Jump`.

## 🪙 Coins On An Arc

1. Create `BP_Coin` (parent `PickupBase`), set its mesh, `ScoreValue = 10`, `bShouldRespawn = true`.
2. Override **On Pickup** to add score.
3. Place a **Parabola Spawner Actor**: `ActorClassToSpawn = BP_Coin`, `NumberOfActors = 8`, drag the Apex / End widgets.

> 💡 Open `Levels/HowToUse` in the plugin content to try it in play mode.
