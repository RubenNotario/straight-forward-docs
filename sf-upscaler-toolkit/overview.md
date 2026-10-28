# SF Upscaler Toolkit - Overview

**SF Upscaler Toolkit** (`SFUpscaler`) is a complete graphics settings menu for Unreal Engine: display, quality and upscaling options in one screen, with Epic TSR, NVIDIA DLSS and AMD FSR behind one Blueprint API and saved user settings.

---

## 🎯 Key Features

- 🖥️ **Ready-made Settings Menu:** `USFGraphicsSettingsWidget` builds a PC-game style options screen with tabs (Display, Graphics, Upscaling) and one `< value >` row per setting. Style it, no Blueprint code needed.
- ⚙️ **Every Typical Option:** window mode, resolution, VSync, frame rate limit, quality preset (Low to Cinematic) and the 10 Unreal scalability groups, plus Auto Detect (hardware benchmark) and Reset to Defaults.
- 🖼️ **One API, Three Upscalers:** `SetAndApplyUpscalerMode(Type, Mode)` for TSR, DLSS and FSR, including Native AA (DLAA).
- ✨ **NVIDIA Ray Reconstruction and Multi Frame Generation:** only the multipliers the GPU supports are offered, and Reflex is enabled automatically.
- 🔴 **AMD FSR 4 / FSR 3:** built on the official AMD FSR Upscaling plugin 4.x. FSR 4 (ML) is used on Radeon RX 7000 / 9000 and FSR 3 on any other GPU; FSR Frame Generation turns on Radeon Anti-Lag 2 when its plugin is installed.
- 📊 **Performance Overlay:** FPS and frame times (game, render, GPU) drawn by the menu itself, never hidden behind it.
- 💾 **Persistent Settings:** `USFUpscalerSettings` extends Game User Settings, so every choice is saved with the rest of your options.
- 🔗 **No Hard Dependency:** DLSS is driven through NVIDIA's own Blueprint libraries via reflection. The plugin compiles and runs without them; unsupported rows are simply disabled.

---

## 📦 Included Example Content

| Asset | Description |
| :--- | :--- |
| `Levels/HowToUse` | Demo room with the SETTINGS menu (TAB shows / hides it). |
| `Widgets/UI/WBP_SFDemoMenu` | The settings screen: child of `SFGraphicsSettingsWidget`, SF style. |
| `Widgets/UI/WBP_SFOptionRow` | One `Label  < Value >` row: child of `SFOptionRowWidget`. |
| `Blueprints/HowToUse/BP_SFDemoMenuController` | Creates the menu and toggles it with TAB. |

**Supported engine version:** Unreal Engine 5.8.
