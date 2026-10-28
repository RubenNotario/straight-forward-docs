# SF Upscaler Toolkit - C++ & Blueprint API

---

## 🖥️ Settings Menu (`USFGraphicsSettingsWidget`)

Create a Widget Blueprint with this parent class. Only two things are required:

- **`RowsBox`** *(any panel, e.g. a Scroll Box)*: rows of the active tab are created here.
- **`Row Class`** *(class default)*: a Widget Blueprint child of `SFOptionRowWidget` with `LabelText`, `ValueText` (TextBlock), `PrevButton` and `NextButton` (Button).

Optional widgets, bound by name: `TabDisplay` / `TabGraphics` / `TabUpscaling` (Button) with `<Tab>Text` and `<Tab>Line`, `DescriptionTitle`, `DescriptionText`, `SupportText`, `StatsText` (TextBlock), `AutoDetectButton`, `ResetButton` (Button).

| Function / Event | Description |
| :--- | :--- |
| `ShowTab(Tab)` | Shows Display, Graphics or Upscaling. |
| `StepOption(Option, Direction)` | Moves an option to its previous (-1) or next (+1) value and applies it. |
| `AutoDetect()` | Runs the hardware benchmark and applies the recommended quality levels. |
| `ResetToDefaults()` | Restores and applies the default settings. |
| `OnSettingChanged(Option)` | Blueprint event after every change. |

> 💡 Untick **Is Focusable** on the menu buttons so a click never steals Tab or gamepad input from the game.

| Tab | Options |
| :--- | :--- |
| Display | Window mode, Resolution, VSync, Frame rate limit, Performance overlay |
| Graphics | Quality preset, View distance, Anti-aliasing, Shadows, Global illumination, Reflections, Post processing, Textures, Effects, Foliage, Shading |
| Upscaling | Upscaler, Quality mode, FSR version, Ray Reconstruction, Frame Generation |

---

## 🚀 Quick Set Library (`USFUpscalerLibrary`)

- **`SetAndApplyUpscalerMode(Type, Mode)`**, **`SetAndApplyFrameGeneration(Multiplier)`**, **`SetAndApplyRayReconstruction(bEnabled)`**, **`SetAndApplyFSRVersion(Version)`**: set, apply and save.
- **`IsDLSSSupported()`**, **`IsFSRSupported()`**, **`IsFSR4Supported()`**, **`IsFrameGenerationSupported()`**, **`IsRayReconstructionSupported()`** *(bool)*.
- **`IsUpscalerModeSupported(Type, Mode)`**, **`IsFrameGenerationModeSupported(Multiplier)`** *(bool)*.
- **`GetSupportedUpscalers()`**, **`GetSupportedModes(Type)`**, **`GetSupportedFrameGeneration(Type)`**: ready-made option lists for your own menus.

---

## 💾 `USFUpscalerSettings` (Game User Settings)

- **`GetSFUpscalerSettings()`**: Returns the settings object (requires the ini setup).
- **`Set/GetUpscalerType`**, **`Set/GetUpscalerMode`**, **`Set/GetFrameGenerationMultiplier`**, **`Set/GetRayReconstructionEnabled`**, **`ApplyUpscalerSettings()`**.
- Standard **`Apply Settings`** also re-applies the upscaler. All Game User Settings functions (resolution, scalability...) keep working.

---

## 🎨 Enums

| `ESFUpscalerType` | `ESFUpscalerMode` | `ESFFrameGenerationMultiplier` |
| :--- | :--- | :--- |
| `None`, `DLSS`, `FSR`, `TSR` | `Off`, `Auto`, `DLAA` (Native AA), `Quality`, `Balanced`, `Performance`, `UltraPerformance` | `Off`, `x2` to `x6` |

**TSR screen percentage:** Quality 66.7%, Balanced 58%, Performance 50%, Ultra Performance 33.3%, Auto / Native AA 100%. DLSS uses the optimal percentage reported by NVIDIA for each mode (100% for DLAA).
