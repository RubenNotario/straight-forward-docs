# SF Toasts - C++ & Blueprint API

Main message and modal popup functions on `UScreenMessageSubsystem`.

---

## 🛠️ Main Subsystem Functions

### `ShowMessage`
Displays a floating Toast message on the screen.
- **`WidgetClass`** *(TSubclassOf<UFadeMessageWidget>)*: Custom toast widget class (or default).
- **`Text`** *(FText)*: Message body text.
- **`Position`** *(EMessageScreenPosition)*: Screen corner/edge position enum (`TopLeft`, `TopRight`, `BottomLeft`, `BottomRight`, `Center`).
- **`FadeInTime`** *(float)*: Fade-in duration in seconds (Default: 1.0s).
- **`Duration`** *(float)*: Visible hold time in seconds (Default: 2.0s).
- **`FadeOutTime`** *(float)*: Fade-out duration in seconds (Default: 1.0s).
- **Returns**: Pointer to the created `UFadeMessageWidget`.

---

### `ShowPopup`
Displays a centered modal dialogue popup.
- **`WidgetClass`** *(TSubclassOf<UPopupWidget>)*: Popup widget class.
- **`Text`** *(FText)*: Body text content.
- **`bPauseGame`** *(bool)*: If `true`, pauses game execution while the popup is visible (Default: `true`).
- **Returns**: Pointer to the created `UPopupWidget`.

---

## 🎨 Enums & Structs

### `EMessageScreenPosition`
- `TopLeft`
- `TopCenter`
- `TopRight`
- `BottomLeft`
- `BottomCenter`
- `BottomRight`
- `Center`
