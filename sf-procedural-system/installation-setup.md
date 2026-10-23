# SF Procedural System - Installation & Setup

Follow these steps to install **SFProceduralGeneration** in your Unreal Engine project.

---

## 🛍️ Option A: Fab / Unreal Engine Marketplace (Recommended)

1. Acquire the plugin on **Fab** (Epic Games Launcher).
2. Click **Install to Engine** and select your desired Unreal Engine version.
3. Open your project and navigate to **Edit > Plugins**.
4. Search for **SFProceduralGeneration** and check **Enabled**.
5. Restart the editor when prompted.

---

## 📁 Option B: Manual Installation (Project Plugins Folder)

1. Create a `Plugins/` folder in your project root directory if it does not exist.
2. Copy the `SFProceduralGeneration` folder into `YourProject/Plugins/`:
   ```
   YourProject/
   └── Plugins/
       └── SFProceduralGeneration/
   ```
3. Launch Unreal Engine and verify the plugin is active under **Edit > Plugins > Gameplay > SFProceduralGeneration**.

---

## 🧑‍💻 C++ Projects (Optional)

Add the module to your `YourProject.Build.cs`:
```csharp
PublicDependencyModuleNames.Add("SFProceduralGeneration");
```

---

## ⚙️ Basic Setup

1. Drop a **Procedural Linear Spawner** in your level.
2. Fill **Spawnable List** (class, weight, preload count, offset) and set **Generation Direction** (e.g. `(0,0,1)` for vertical climbers).
3. Leave **Reference Actor** empty to follow Player Pawn 0, or set it at runtime.
