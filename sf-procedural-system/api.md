# SF Procedural System - C++ & Blueprint API

---

## ♾️ `AProceduralLinearSpawner`

| Property | Default | Description |
| :--- | :--- | :--- |
| `SpawnableList` | - | Array of `FSpawnableActorDef` (`ActorClass`, `SpawnWeight`, `PreloadCount`, `SpawnOffset`). |
| `GenerationDirection` | `(0,0,1)` | Axis of generation (normalized on BeginPlay). |
| `Spacing` / `SpacingVariance` | `200` / `0` | Distance between items along the axis. |
| `BoundsVariance` | `(0,400,0)` | Random offset per axis. |
| `SpawnDistance` | `1000` | How far ahead of the reference actor items are spawned. |
| `RecycleDistance` | `1500` | How far behind items are returned to the pool. |
| `ReferenceActor` | Player Pawn 0 | Actor whose progress drives generation. |
| `PoolManager` | - | Built-in `UObjectPoolManager`. |

- **`PreloadPools()`**: Creates `PreloadCount` hidden instances per class (called on BeginPlay).
- **`SpawnNextItem()`**: Spawns the next item manually.
- **`OnActorSpawned(Actor)`**: Fired for every spawned / reused item.

Distances are measured from the spawner location, so it can be placed anywhere in the level.

---

## ♻️ `UObjectPoolManager` (Actor Component)

- **`GetActorFromPool(ActorClass, SpawnTransform)`** *(AActor)*: Reuses a hidden instance or spawns a new one.
- **`ReturnActorToPool(Actor)`**: Hides it and disables collision and tick.

---

## 🔁 `IPoolableActorInterface`

- **`OnSpawnFromPool()`** / **`OnReturnToPool()`**: Reset health, timers, VFX... when an actor is reused.
