# SF Loading Screen - Installation & Setup

Follow these steps to install **Straight Forward Loading Screen** in your Unreal Engine project.

---

## 🛍️ Option A: Fab / Unreal Engine Marketplace (Recommended)

1. Acquire the plugin on **Fab** (Epic Games Launcher).
2. Click **Install to Engine** and select your desired Unreal Engine version.
3. Open your project and navigate to **Edit > Plugins**.
4. Search for **Straight Forward Loading Screen** and check **Enabled**.
5. Restart the editor when prompted.

---

## 📁 Option B: Manual Installation (Project Plugins Folder)

1. Create a `Plugins/` folder in your project root directory if it does not exist.
2. Copy the `StraightForwardLoadingScreen` folder into `YourProject/Plugins/`:
   ```
   YourProject/
   └── Plugins/
       └── StraightForwardLoadingScreen/
   ```
3. Launch Unreal Engine and verify the plugin is active under **Edit > Plugins > UI > Straight Forward Loading Screen**.

---

## 🧑‍💻 C++ Projects (Optional)

Add the module to your `YourProject.Build.cs`:
```csharp
PublicDependencyModuleNames.Add("StraightForwardLoadingScreen");
```

---

## ⚙️ Basic Setup

Configure it in **Project Settings ➔ Plugins ➔ Straight Forward Loading Screen**. Any `Open Level` / server travel now shows the loading screen.

> ⚠️ The Movie Player does not run in PIE. Test with **Standalone Game** or a packaged build.
