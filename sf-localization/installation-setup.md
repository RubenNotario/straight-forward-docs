# SF Localization - Installation & Setup

Follow these steps to install **Straight Forward Localization** in your Unreal Engine project.

---

## 🛍️ Option A: Fab / Unreal Engine Marketplace (Recommended)

1. Acquire the plugin on **Fab** (Epic Games Launcher).
2. Click **Install to Engine** and select your desired Unreal Engine version.
3. Open your project and navigate to **Edit > Plugins**.
4. Search for **Straight Forward Localization** and check **Enabled**.
5. Restart the editor when prompted.

---

## 📁 Option B: Manual Installation (Project Plugins Folder)

1. Create a `Plugins/` folder in your project root directory if it does not exist.
2. Copy the `StraightForwardLocalization` folder into `YourProject/Plugins/`:
   ```
   YourProject/
   └── Plugins/
       └── StraightForwardLocalization/
   ```
3. Launch Unreal Engine and verify the plugin is active under **Edit > Plugins > Localization > Straight Forward Localization**.

---

## 🧑‍💻 C++ Projects (Optional)

Add the module to your `YourProject.Build.cs`:
```csharp
PublicDependencyModuleNames.Add("StraightForwardLocalization");
```

---

## ⚙️ Basic Setup

1. Create a **Data Table** with row structure **SFLocalizationRow** (columns `EN`, `ES`, `FR`, `DE`, `IT`, `PT`).
2. On game start: `Get SF Localization Subsystem` ➔ `Register Thematic Table (YourTable)` ➔ `Set Language ("EN")`.
3. In UMG, use **SF Localized Text** and set its **Text ID** to a row name.
