# SF Toasts - Troubleshooting

---

### ❓ Toasts overlap each other on screen
**Solution:**
Ensure your `WidgetClass` passed to `ShowMessage` inherits from `UFadeMessageWidget` so the layout subsystem can calculate item bounds inside `UMessageLayoutWidget`.

---

### ❓ Game remains paused after closing a Popup
**Solution:**
Ensure your custom popup close button calls `OnPopupClosed` or unpauses the Game Instance via `Set Game Paused (false)` when dismissed.
