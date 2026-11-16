# SF Upscaler Toolkit - Installation & Setup

Follow these steps to install **SFUpscaler** in your Unreal Engine project.

---

## 🛍️ Option A: Fab / Unreal Engine Marketplace (Recommended)

1. Acquire the plugin on **Fab** (Epic Games Launcher).
2. Click **Install to Engine** and select your desired Unreal Engine version.
3. Open your project and navigate to **Edit > Plugins**.
4. Search for **Straight Forward Upscaler Toolkit** and check **Enabled**.
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

---

## 🔌 Optional: NVIDIA DLSS and AMD FSR

Epic TSR and the whole settings menu work out of the box. DLSS and FSR need their own **free plugins from Fab**, which are **not included**:

- **NVIDIA DLSS** (and its Streamline plugins for Frame Generation and Reflex).
- **AMD FSR Upscaling** 4.x (plus **Radeon Anti-Lag 2** for FSR Frame Generation).

Install them, enable them in **Edit > Plugins** and restart the editor. If a plugin is missing, its upscaler simply does not appear in the menu: nothing breaks.

---

## 🧩 Optional: Configuration Profile

To change first-launch defaults, renderer tuning or the menu layout, pick a profile in **Project Settings > Plugins > SF Upscaler Toolkit > Profile** (empty = `DA_SFUpscaler_Default`). See [Configuration Profile](configuration-profile.md).

---

**Platform:** Windows (Win64), Unreal Engine 5.8.
