# SF Procedural System - Overview

**SF Procedural System** (`SFProceduralGeneration`) provides endless linear generation and a lightweight object pool for Unreal Engine. It was extracted from *Jump or Die*, where it drives the infinite tower.

---

## 🎯 Key Features

- ♾️ **Linear Spawner:** `AProceduralLinearSpawner` spawns items ahead of a reference actor and recycles them behind it, in any direction.
- ♻️ **Object Pooling:** `UObjectPoolManager` reuses actors instead of Spawn / Destroy (no GC spikes).
- 🎲 **Weighted Spawn List:** per class weight, preload count and offset.
- 📏 **Spacing & Variance:** random spacing and per-axis bounds variance.
- 🔁 **Poolable Interface:** optional `OnSpawnFromPool` / `OnReturnToPool` hooks to reset state.

---

## 📦 Included Example Content

| Asset | Description |
| :--- | :--- |
| `Levels/HowToUse` | Demo room with an endless lane generated along the corridor. |
| `Blueprints/HowToUse/BP_SFDemoPoolBlock` / `BP_SFDemoPoolPillar` | Pooled actors (weights 3 : 1). |
| `Blueprints/HowToUse/BP_ProceduralDemoController` | Runtime spacing changes, manual steps and direct pool usage. |

**Supported engine version:** Unreal Engine 5.8.
