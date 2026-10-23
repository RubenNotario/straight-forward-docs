# SF Toasts - Troubleshooting

---

### ❓ Toasts overlap each other on screen
**Solution:**
Ensure your `WidgetClass` passed to `ShowMessage` inherits from `UFadeMessageWidget` so the layout subsystem can calculate item bounds inside `UMessageLayoutWidget`.

---

### ❓ Game remains paused after closing a Popup
**Solution:**
The Button must be named exactly `CloseButton`: `UPopupWidget` binds its click in C++ to unpause, restore Game Only input and broadcast `OnPopupClosed`. If the popup is removed any other way, it also unpauses when destroyed.

---

### ❓ `ShowMessage` / `ShowPopup` returns None and nothing appears
**Solution:**
`WidgetClass` is required. Pick a Widget Blueprint whose parent is `FadeMessageWidget` (toasts) or `PopupWidget` (popups), with the required named widgets.

---

### ❓ The background is not darkened behind the popup
**Solution:**
Fixed in the current version (the backdrop now uses a concrete widget class). Update the plugin.
