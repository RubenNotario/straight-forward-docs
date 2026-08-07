# SF Timers - Installation & Setup

Follow these steps to install **Straight Forward Timers** in your Unreal Engine project.

---

## 🛍️ Option A: Fab / Unreal Engine Marketplace (Recommended)

1. Acquire the plugin on **Fab** (Epic Games Launcher).
2. Click **Install to Engine** and select your desired Unreal Engine version.
3. Open your project and navigate to **Edit > Plugins**.
4. Search for **Straight Forward Timers** and check **Enabled**.
5. Restart the editor when prompted.

---

## 📁 Option B: Manual Installation (Project Plugins Folder)

If installing from a standalone ZIP or source download:

1. Create a `Plugins/` folder in your project root directory if it does not exist.
2. Copy the `StraightForwardTimers` folder into `YourProject/Plugins/`:
   ```
   YourProject/
   └── Plugins/
       └── StraightForwardTimers/
   ```
3. Launch Unreal Engine and verify the plugin is active under **Edit > Plugins > Systems > Straight Forward Timers**.

---

## ⚙️ Subsystem Lifetime

`ULevelTimerSubsystem` inherits from `UTickableWorldSubsystem`.
- It initializes automatically when a world level loads.
- Timers are automatically cleaned up when traveling between levels, avoiding memory leaks and stray background loops.
