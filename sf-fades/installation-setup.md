# SF Fades - Installation & Setup

Follow these steps to install **Straight Forward Fades** in your Unreal Engine project.

---

## 🛍️ Option A: Fab / Unreal Engine Marketplace (Recommended)

1. Acquire the plugin on **Fab** (Epic Games Launcher).
2. Click **Install to Engine** and select your desired Unreal Engine version.
3. Open your project and navigate to **Edit > Plugins**.
4. Search for **Straight Forward Fades** and check **Enabled**.
5. Restart the editor when prompted.

---

## 📁 Option B: Manual Installation (Project Plugins Folder)

If installing from a standalone ZIP or source download:

1. Create a `Plugins/` folder in your project root directory if it does not exist.
2. Copy the `StraightForwardFades` folder into `YourProject/Plugins/`:
   ```
   YourProject/
   └── Plugins/
       └── StraightForwardFades/
   ```
3. Launch Unreal Engine and verify the plugin is active in **Edit > Plugins > UI > Straight Forward Fades**.

---

## ⚙️ Subsystem Lifetime & Customization

Because `UScreenFadeSubsystem` is a `UGameInstanceSubsystem`, **no manually placed actors or viewport widgets are required**. The subsystem automatically initializes when the game boots and creates overlay widgets on-demand.

If you wish to override the visual fade widget:
- Create a UMG Widget blueprint inheriting from `UScreenFadeWidget`.
- Set `FadeWidgetClass` on `UScreenFadeSubsystem` during GameInstance or Blueprint initialization.
