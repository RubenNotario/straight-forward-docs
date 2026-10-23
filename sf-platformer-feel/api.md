# SF Platformer Feel - C++ & Blueprint API

---

## 🐺 `UCoyoteTimeComponent`

| Property | Default | Description |
| :--- | :--- | :--- |
| `CoyoteTimeDuration` | `0.2 s` | Grace period after walking off a ledge. |
| `JumpZVelocityOverride` | `0` | Jump velocity for coyote jumps (`0` = movement component value). |
| `JumpBufferDuration` | `0.15 s` | Max time between the press and landing for a buffered jump. |

- **`TryCoyoteJump()`** *(bool)*: Performs the late jump if still inside the window (once per ledge).
- **`RegisterJumpInput()`**: Stores the press time for the jump buffer.
- **`OnBufferedJumpTriggered`**: Fired on landing when a buffered press is valid.

---

## 🪙 `APickupBase`

| Property | Description |
| :--- | :--- |
| `PickupMesh`, `OverlapSphere` | Components (overlap with Pawns). |
| `ScoreValue` (100), `PickupIdentifier` (`GenericPickup`) | Gameplay data. |
| `PickupVFX`, `PickupSFX` | Optional Niagara system and sound. |
| `bShouldRespawn`, `RespawnTime` (5 s) | Hide + respawn instead of destroying. |
| `MeshHeightOffset` (50) | Mesh height above the actor origin (`SetMeshHeightOffset`). |

- **`OnPickup(Picker)`** *(BlueprintNativeEvent)*: Your gameplay logic (score, inventory...).
- **`RespawnPickup()`**: Shows it again manually.

---

## 🌈 `AParabolaSpawnerActor`

`ActorClassToSpawn`, `NumberOfActors`, `ApexPoint` / `EndPoint` (3D widgets, relative), `bShouldRespawn`, `RespawnTime`.
