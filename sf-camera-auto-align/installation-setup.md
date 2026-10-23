# SF Camera Auto Align - Installation & Setup

Follow these steps to install **Straight Forward Camera Auto Align** in your Unreal Engine project.

---

## 🛍️ Option A: Fab / Unreal Engine Marketplace (Recommended)

1. Acquire the plugin on **Fab** (Epic Games Launcher).
2. Click **Install to Engine** and select your desired Unreal Engine version.
3. Open your project and navigate to **Edit > Plugins**.
4. Search for **Straight Forward Camera Auto Align** and check **Enabled**.
5. Restart the editor when prompted.

---

## 📁 Option B: Manual Installation (Project Plugins Folder)

1. Create a `Plugins/` folder in your project root directory if it does not exist.
2. Copy the `StraightForwardCameraAutoAlign` folder into `YourProject/Plugins/`:
   ```
   YourProject/
   └── Plugins/
       └── StraightForwardCameraAutoAlign/
   ```
3. Launch Unreal Engine and verify the plugin is active under **Edit > Plugins > Camera > Straight Forward Camera Auto Align**.

---

## 🧑‍💻 C++ Projects (Optional)

Add the module to your `YourProject.Build.cs`:
```csharp
PublicDependencyModuleNames.Add("StraightForwardCameraAutoAlign");
```

---

## ⚙️ Basic Setup

Open your character Blueprint ➔ **Add Component** ➔ **Camera Auto Align**. Tune `AutoAlignDelay` and `AlignInterpolationSpeed`. No other setup is required.
