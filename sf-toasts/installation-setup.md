# SF Toasts - Installation & Setup

Follow these steps to install **Straight Forward Toasts** in your Unreal Engine project.

---

## 🛍️ Option A: Fab / Unreal Engine Marketplace (Recommended)

1. Acquire the plugin on **Fab** (Epic Games Launcher).
2. Click **Install to Engine** and select your desired Unreal Engine version.
3. Open your project and navigate to **Edit > Plugins**.
4. Search for **Straight Forward Toasts** and check **Enabled**.
5. Restart the editor when prompted.

---

## 📁 Option B: Manual Installation (Project Plugins Folder)

If installing from a standalone ZIP or source download:

1. Create a `Plugins/` folder in your project root directory if it does not exist.
2. Copy the `StraightForwardToasts` folder into `YourProject/Plugins/`:
   ```
   YourProject/
   └── Plugins/
       └── StraightForwardToasts/
   ```
3. Enable **Straight Forward Toasts** in **Edit > Plugins > UI**.

---

## ⚙️ Subsystem Lifetime

`UScreenMessageSubsystem` is a World Subsystem. It instantiates automatically when the world loads and builds the layout canvas overlay when the first message or popup is triggered.
