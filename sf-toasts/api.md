# SF Toasts - C++ & Blueprint API

Main message and modal popup functions on `UScreenMessageSubsystem`.

---

## 🛠️ Main Subsystem Functions

### `ShowMessage`
Displays a floating Toast message on the screen.
- **`WidgetClass`** *(TSubclassOf<UFadeMessageWidget>)*: Toast widget class. **Required** (returns `nullptr` if empty). Must contain a Text Block named `MessageText`.
- **`Text`** *(FText)*: Message body text.
- **`Position`** *(EMessageScreenPosition)*: Screen anchor (`TopLeft`, `TopCenter`, `TopRight`, `BottomLeft`, `BottomCenter`, `BottomRight`).
- **`FadeInTime`** *(float)*: Fade-in duration in seconds (Default: 1.0s).
- **`Duration`** *(float)*: Visible hold time in seconds (Default: 2.0s).
- **`FadeOutTime`** *(float)*: Fade-out duration in seconds (Default: 1.0s).
- **Returns**: Pointer to the created `UFadeMessageWidget`.

---

### `ShowPopup`
Displays a centered modal dialogue popup.
- **`WidgetClass`** *(TSubclassOf<UPopupWidget>)*: Popup widget class. Must contain a Text Block `PopupText` and a Button `CloseButton`.
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

---

## 🧩 Widget Base Classes

| Class | Required bindings (BindWidget) | Notes |
| :--- | :--- | :--- |
| `UFadeMessageWidget` | `MessageText` (Text Block) | Fades in, waits and fades out by itself. Blueprint category: *UI > Message > Widget*. |
| `UPopupWidget` | `PopupText` (Text Block), `CloseButton` (Button) | Handles pause, UI-only input and mouse cursor. **On Popup Closed** fires when Close is clicked. |

## ⚙️ Properties

- **`LayoutWidgetClass`** *(TSubclassOf<UMessageLayoutWidget>)*: Optional override of the layout that hosts the six message queues.
