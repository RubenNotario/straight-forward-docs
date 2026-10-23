# SF Toasts - Overview

**SF Toasts** (`StraightForwardToasts`) is a notification and modal popup system for Unreal Engine managed by `UScreenMessageSubsystem` (a **World Subsystem**).

---

## 🎯 Key Features

- 🔔 **Floating Toast Notifications:** Display customizable notification messages on six screen anchors (`TopLeft`, `TopCenter`, `TopRight`, `BottomLeft`, `BottomCenter`, `BottomRight`).
- ⏱️ **Smooth Fade Controls:** Configurable Fade-In, Display Duration, and Fade-Out timing.
- 💬 **Interactive Modal Popups:** Display centered modal popups with automatic background darkening and optional game pausing.
- 📐 **Automatic Layout Stacking:** Messages stack neatly without overlapping, handled by `UMessageLayoutWidget`.

---

## 📦 Included Example Content

| Asset | Description |
| :--- | :--- |
| `Levels/HowToUse` | Demo room: achievement toast, all screen positions, stacked queue and a paused modal popup. |
| `Blueprints/HowToUse/BP_ToastsDemoController` | Every node used by the room. |
| `Widgets/WBP_ToastMessage` / `WBP_PopupModal` | Ready-to-use toast and popup widgets in SF colors. |

**Supported engine version:** Unreal Engine 5.8.
