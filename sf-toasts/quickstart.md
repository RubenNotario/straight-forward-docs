# SF Toasts - Quickstart Example

Examples of displaying Toast notifications and modal popups in Blueprint.

---

## 🔔 Displaying an Achievement Toast

1. Get `ScreenMessageSubsystem`.
2. Call `ShowMessage`:
   - `WidgetClass`: Select your `WBP_ToastMessage` (or standard fade widget).
   - `Text`: `"Achievement Unlocked: Master Explorer!"`
   - `Position`: `TopRight`
   - `FadeInTime`: `0.5`
   - `Duration`: `3.0`
   - `FadeOutTime`: `0.5`

---

## 💬 Displaying a Pause / Confirmation Popup

1. Call `ShowPopup`:
   - `WidgetClass`: Select your `WBP_PopupModal`.
   - `Text`: `"Are you sure you want to quit to main menu?"`
   - `bPauseGame`: `true`
2. The subsystem darkens the background, pauses the game and gives the mouse to the UI until **Close** is clicked.
3. To continue your flow afterwards, bind **On Popup Closed** on the returned widget.

> 💡 `Widgets/WBP_ToastMessage` and `Widgets/WBP_PopupModal` are included in the plugin content.
