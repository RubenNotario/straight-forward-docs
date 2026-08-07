# SF Fades - Installation & Setup

Follow these steps to install **StraightForwardFades**.

---

## 📁 1. Plugin Placement

1. Copy the `StraightForwardFades` folder into your project's `Plugins/` directory:
   ```
   YourProject/
   └── Plugins/
       └── StraightForwardFades/
   ```
2. Launch Unreal Engine and verify the plugin is active in **Edit > Plugins > UI > Straight Forward Fades**.

---

## ⚙️ 2. Automatic Subsystem Initialization

Because `UScreenFadeSubsystem` is a `UGameInstanceSubsystem`, **no manually placed actors or viewport widgets are required**. The subsystem automatically initializes when the game boots and creates the overlay widget on-demand.

---

## 🎨 3. (Optional) Custom Fade Widget Class

If you wish to override the visual fade widget:
- Create a UMG Widget blueprint inheriting from `UScreenFadeWidget`.
- Set `FadeWidgetClass` on the `UScreenFadeSubsystem` in your GameInstance or Blueprint initialization.
