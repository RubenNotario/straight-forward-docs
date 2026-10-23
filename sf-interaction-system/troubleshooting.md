# SF Interaction System - Troubleshooting

---

### ❓ Nothing gets focused
**Solution:**
Enable `bDrawDebug` on the Interactor. The interactable must have a component that **blocks** the Interactor `CollisionChannel` (`Visibility` by default) within `TraceDistance`.

---

### ❓ `OnInteractHoldProgress` never reaches 1
**Behavior Explanation:**
`Progress` is the time held in **seconds**, not a 0-1 ratio. Compare it with your own hold duration.

---

### ❓ Focus works but `OnInteract` never fires
**Solution:**
`Try Interact` must be called from your input. Also check `CanInteract` / `bIsInteractable` returns `true`.
