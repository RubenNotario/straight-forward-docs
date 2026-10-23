# SF Platformer Feel - Troubleshooting

---

### ❓ Coyote jump never triggers
**Solution:**
It only works after **walking off** a ledge (not after a normal jump) and only within `CoyoteTimeDuration`. Make sure you call `Try Coyote Jump` when `Can Jump` is false.

---

### ❓ Buffered jump never fires
**Solution:**
Call `Register Jump Input` on air presses and bind `On Buffered Jump Triggered` to `Jump`.

---

### ❓ Pickups are not collected
**Solution:**
The overlap sphere only overlaps **Pawn** objects. Check your character capsule object type.
