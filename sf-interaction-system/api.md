# SF Interaction System - C++ & Blueprint API

---

## 🧍 `UInteractorComponent` (player)

### Properties
| Property | Type | Default | Description |
| :--- | :--- | :--- | :--- |
| `DetectionMode` | `EInteractDetectionMode` | `CameraCenter` | `CameraCenter` (FPS/TPS) or `MouseCursor` (top-down, point & click). |
| `TraceType` | `EInteractTraceType` | `Line` | `Line`, `Sphere` or `Box`. |
| `TraceDistance` | float | `500` | Trace length in cm. |
| `TraceRadius` | float | `20` | Sphere radius / box half extent. |
| `CollisionChannel` | `ECollisionChannel` | `Visibility` | Channel used by the trace. |
| `bDrawDebug` | bool | `false` | Draws the trace every frame. |

### Functions
- **`TryInteract()`**: Calls `OnInteract` on the focused interactable and starts the hold counter.
- **`StopInteract()`**: Stops the hold counter (call on key release).
- **`GetFocusedInteractable()`** *(UObject)*: Current focused actor or component.

---

## 🧩 `IInteractableInterface`

| Function | Description |
| :--- | :--- |
| `CanInteract(Interactor)` *(bool)* | Return `false` to ignore focus and interaction (locked doors, cooldowns). |
| `OnInteract(Interactor)` | Fired by `TryInteract`. |
| `OnBeginFocus(Interactor)` / `OnEndFocus(Interactor)` | Fired when the trace starts / stops hitting the object. |
| `OnInteractHoldProgress(Interactor, Progress)` | Fired every frame while held. **Progress is the time held in seconds.** |
| `GetInteractText()` *(FText)* | Prompt text for your HUD. |

---

## 🧱 `UInteractableComponent`

Implements the interface and re-broadcasts it as Blueprint events.
- **`bIsInteractable`** *(bool)*: Returned by `CanInteract`.
- **`InteractText`** *(FText)*: Returned by `GetInteractText` (Default: `"Interact"`).
- **Events:** `OnInteractEvent`, `OnBeginFocusEvent`, `OnEndFocusEvent`, `OnInteractHoldProgressEvent`.

---

## 📦 `AInteractableTriggerBase`

Actor with `TriggerBox` (BlockAllDynamic) + `InteractableComponent`. Broadcasts **`OnInteract(Interactor)`**, ideal for Level Blueprint scripting. Override `OnInteractTriggered` in C++ subclasses.
