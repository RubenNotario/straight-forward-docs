# SF Procedural System - Quickstart Example

An endless runner lane.

---

1. Create `BP_Platform` (mesh) and `BP_Obstacle`.
2. Place a **Procedural Linear Spawner** at the start of the level:
   - `SpawnableList`: Platform (weight 3, preload 12), Obstacle (weight 1, preload 4).
   - `GenerationDirection = (1,0,0)`, `Spacing = 220`, `SpacingVariance = 60`, `BoundsVariance = (0,260,0)`.
   - `SpawnDistance = 1800`, `RecycleDistance = 1200`.
3. Press Play: items appear ahead of the player and disappear behind.

## ♻️ Pooling Your Own Actors

Add an **Object Pool Manager** to any actor and replace `Spawn Actor` / `Destroy Actor` with `Get Actor From Pool` / `Return Actor To Pool`.

> 💡 Open `Levels/HowToUse` in the plugin content to see it in play mode.
