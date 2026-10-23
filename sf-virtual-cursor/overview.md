# SF Virtual Cursor - Overview

**SF Virtual Cursor** (`StraightForwardVirtualCursor`) lets players drive the mouse cursor with a gamepad, so any mouse-driven UMG interface becomes playable on controller without rewriting navigation.

---

## 🎯 Key Features

- 🎮 **Left Stick ➔ Cursor:** a Slate input pre-processor moves the real OS cursor.
- 🖱️ **A / Cross ➔ Left Click:** every UMG widget works unchanged.
- 🌐 **Engine Subsystem:** works in menus, between levels and while paused.
- ⚙️ **Adjustable Speed** with a built-in dead zone.

---

## 📦 Included Example Content

| Asset | Description |
| :--- | :--- |
| `Levels/HowToUse` | Demo room with enable / disable and speed buttons. |
| `Widgets/WBP_CursorTestMenu` | Clickable test menu shown while the cursor is enabled. |
| `Blueprints/HowToUse/BP_VirtualCursorDemoController` | Every node used by the room. |

**Supported engine version:** Unreal Engine 5.8.
