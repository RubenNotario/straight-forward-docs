# SF Upscaler Toolkit - Overview

**SF Upscaler Toolkit** (`SFUpscaler`) is a complete graphics settings menu for Unreal Engine: display, quality and upscaling options in one screen, with Epic TSR, NVIDIA DLSS and AMD FSR behind one Blueprint API and saved user settings.

---

## 🎯 Key Features

- 🖥️ **Ready-made Settings Menu:** `USFGraphicsSettingsWidget` builds a PC-game style options screen with tabs (Display, Graphics, Upscaling), titled sections and one `< value >` row per setting. Style it, no Blueprint code needed.
- 🧭 **Clear Upscaling Tab:** only the options of the selected upscaler are listed, under its own section (NVIDIA DLSS, AMD FSR or Epic TSR). Anti-aliasing is greyed out while an upscaler replaces it.
- ⚙️ **Every Typical Option:** window mode, resolution, VSync, frame rate limit, quality preset (Low to Cinematic) and the 10 Unreal scalability groups, plus Auto Detect (hardware benchmark) and Reset to Defaults.
- 🖼️ **One API, Three Upscalers:** `SetAndApplyUpscalerMode(Type, Mode)` for TSR, DLSS and FSR, including Native AA (DLAA).
- ✨ **NVIDIA Ray Reconstruction and Multi Frame Generation:** only the multipliers the GPU supports are offered, and Reflex is enabled automatically.
- 🧠 **DLSS Preset:** pick the DLSS AI model (Auto, or transformer presets K, J and the DLSS 4.5 second generation M, L).
- 💡 **Lighting Method:** Off (screen space), Lumen (software) or Lumen (hardware ray tracing), switched at runtime. Locked to Off while Global illumination or Reflections are on Low, the same rule Unreal applies.
- 🔴 **AMD FSR 4 / FSR 3:** built on the official AMD FSR Upscaling plugin 4.x. FSR 4 (ML) is used on Radeon RX 7000 / 9000 and FSR 3 on any other GPU; FSR Frame Generation turns on Radeon Anti-Lag 2 when its plugin is installed.
- 📊 **Performance Overlay:** FPS and frame times (game, render, GPU) in their own viewport layer: they stay on screen while the menu is hidden. With Frame Generation it shows the frames presented on screen (what the NVIDIA / AMD overlays count) and the rendered ones below.
- 💾 **Persistent Settings:** `USFUpscalerSettings` extends Game User Settings, so every choice is saved with the rest of your options.
- 🔗 **No Hard Dependency:** DLSS is driven through NVIDIA's own Blueprint libraries via reflection. The plugin compiles and runs without them; unsupported rows are simply disabled.

---

## 📦 Included Example Content

| Asset | Description |
| :--- | :--- |
| `Levels/HowToUse` | Demo level with the SETTINGS menu. Controls: TAB menu, V first / third person, P pause, ESC quit (packaged demo). |
| Comparison room | Inside `HowToUse`: mirror, glass, thin fence, fast spinner, particles and small text, the cases where upscalers differ. |
| `Widgets/Splash/WBP_SFSplash` | Boot logo sequence of the demo. Click or Space skips to the next logo. |
| `Widgets/UI/WBP_SFDemoMenu` | The settings screen: child of `SFGraphicsSettingsWidget`, SF style. |
| `Widgets/UI/WBP_SFOptionRow` | One `Label  < Value >` row: child of `SFOptionRowWidget`. |
| `Blueprints/HowToUse/BP_SFDemoMenuController` | Creates the menu and toggles it with TAB, pauses with P. |

**Supported engine version:** Unreal Engine 5.8.
