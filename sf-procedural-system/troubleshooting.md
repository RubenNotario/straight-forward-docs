# SF Procedural System - Troubleshooting

---

### ❓ Items keep spawning without stopping (older versions)
**Solution:**
Fixed in the current version: progress is now measured relative to the spawner, so it works anywhere in the level. Update the plugin.

---

### ❓ Reused actors keep their previous state
**Solution:**
Implement `IPoolableActorInterface` and reset state in `OnSpawnFromPool`.

---

### ❓ Hitches during the first seconds
**Solution:**
Increase `PreloadCount` so enough instances exist before generation starts (about `(SpawnDistance + RecycleDistance) / Spacing`).
