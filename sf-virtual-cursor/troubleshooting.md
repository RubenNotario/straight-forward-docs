# SF Virtual Cursor - Troubleshooting

---

### ❓ The cursor moves but clicks do nothing
**Solution:**
Use **Game And UI** or **UI Only** input mode so clicks reach UMG widgets.

---

### ❓ The left stick keeps moving the cursor in gameplay
**Solution:**
Call `Disable Virtual Cursor` when returning to gameplay.

---

### ❓ `Set Cursor Speed` had no effect (older versions)
**Solution:**
Fixed in the current version: the speed is stored and applied when the cursor is enabled.
