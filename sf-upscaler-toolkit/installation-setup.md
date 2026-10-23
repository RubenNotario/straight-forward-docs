# SF Upscaler Toolkit - Installation & Setup

Follow these steps to install **SFUpscaler** in your Unreal Engine project.

---

## 🛍️ Option A: Fab / Unreal Engine Marketplace (Recommended)

1. Acquire the plugin on **Fab** (Epic Games Launcher).
2. Click **Install to Engine** and select your desired Unreal Engine version.
3. Open your project and navigate to **Edit > Plugins**.
4. Search for **SFUpscaler** and check **Enabled**.
5. Restart the editor when prompted.

---

## 📁 Option B: Manual Installation (Project Plugins Folder)

1. Create a `Plugins/` folder in your project root directory if it does not exist.
2. Copy the `SFUpscaler` folder into `YourProject/Plugins/`:
   ```
   YourProject/
   └── Plugins/
       └── SFUpscaler/
   ```
3. Launch Unreal Engine and verify the plugin is active under **Edit > Plugins > Rendering > SFUpscaler**.

---

## 🧑‍💻 C++ Projects (Optional)

Add the module to your `YourProject.Build.cs`:
```csharp
PublicDependencyModuleNames.Add("SFUpscaler");
```

---

## ⚙️ Required Setup

Add this to `Config/DefaultEngine.ini`, otherwise every call is ignored (a warning is logged):
```ini
[/Script/Engine.Engine]
GameUserSettingsClassName=/Script/SFUpscaler.SFUpscalerSettings
```

Enable the **NVIDIA DLSS** and / or **AMD FSR** plugins if you want to offer them. TSR works without extra plugins.
