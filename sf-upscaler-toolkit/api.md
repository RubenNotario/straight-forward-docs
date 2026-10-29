# SF Upscaler Toolkit - C++ & Blueprint API

---

## 🖥️ Settings Menu (`USFGraphicsSettingsWidget`)

Create a Widget Blueprint with this parent class. Only two things are required:

- **`RowsBox`** *(any panel, e.g. a Scroll Box)*: rows of the active tab are created here.
- **`Row Class`** *(class default)*: a Widget Blueprint child of `SFOptionRowWidget` with `LabelText`, `ValueText` (TextBlock), `PrevButton` and `NextButton` (Button).

Optional widgets, bound by name: `TabDisplay` / `TabGraphics` / `TabUpscaling` (Button) with `<Tab>Text` and `<Tab>Line`, `DescriptionTitle`, `DescriptionText`, `SupportText`, `StatsText` (TextBlock), `AutoDetectButton`, `ResetButton` (Button).

`StatsText` only gives the performance overlay its font and colour: the overlay is drawn in its own viewport layer (top left corner) so it stays visible while the menu is hidden.

| Class default | Description |
| :--- | :--- |
| `Row Class` | Row widget created for every option. |
| `Default Tab` | Tab shown when the menu opens. |
| `Section Title Color` / `Section Title Font` | Look of the section titles (GENERAL, LIGHTING, NVIDIA DLSS...). |
| `Description Min Height` | Height reserved for the description of the hovered row, so the row list does not move under the cursor (0 = off). |
| `Active Tab Color` / `Inactive Tab Color` | Tab text and underline colours. |

| Function / Event | Description |
| :--- | :--- |
| `ShowTab(Tab)` | Shows Display, Graphics or Upscaling. |
| `StepOption(Option, Direction)` | Moves an option to its previous (-1) or next (+1) value and applies it. |
| `AutoDetect()` | Runs the hardware benchmark and applies the recommended quality levels. |
| `ResetToDefaults()` | Restores and applies the default settings. |
| `OnSettingChanged(Option)` | Blueprint event after every change. |

> 💡 Untick **Is Focusable** on the menu buttons so a click never steals Tab or gamepad input from the game.

| Tab | Section | Options |
| :--- | :--- | :--- |
| Display | | Window mode, Resolution, VSync, Frame rate limit, Performance overlay |
| Graphics | General | Quality preset, View distance, Anti-aliasing *(disabled while an upscaler is active)*, Textures |
| Graphics | Lighting | Global illumination, Reflections, Shadows, Lighting method *(Off / Lumen software / Lumen hardware RT)* |
| Graphics | Effects | Post processing, Effects, Foliage, Shading |
| Upscaling | Upscaler | Upscaler |
| Upscaling | NVIDIA DLSS | Quality mode, DLSS preset, Ray Reconstruction, Frame Generation |
| Upscaling | AMD FSR | Quality mode, FSR version, Frame Generation |
| Upscaling | Epic TSR | Quality mode |

---

## 🚀 Quick Set Library (`USFUpscalerLibrary`)

- **`SetAndApplyUpscalerMode(Type, Mode)`**, **`SetAndApplyFrameGeneration(Multiplier)`**, **`SetAndApplyRayReconstruction(bEnabled)`**, **`SetAndApplyFSRVersion(Version)`**, **`SetAndApplyDLSSPreset(Preset)`**, **`SetAndApplyHardwareRayTracing(bEnabled)`**: set, apply and save.
- **`IsDLSSSupported()`**, **`IsFSRSupported()`**, **`IsFSR4Supported()`**, **`IsFrameGenerationSupported()`**, **`IsRayReconstructionSupported()`**, **`IsHardwareRayTracingSupported()`** *(bool)*.
- **`IsUpscalerModeSupported(Type, Mode)`**, **`IsFrameGenerationModeSupported(Multiplier)`** *(bool)*.
- **`GetSupportedUpscalers()`**, **`GetSupportedModes(Type)`**, **`GetSupportedFrameGeneration(Type)`**: ready-made option lists for your own menus.

---

## 💾 `USFUpscalerSettings` (Game User Settings)

- **`GetSFUpscalerSettings()`**: Returns the settings object (requires the ini setup).
- **`Set/GetUpscalerType`**, **`Set/GetUpscalerMode`**, **`Set/GetFrameGenerationMultiplier`**, **`Set/GetRayReconstructionEnabled`**, **`Set/GetDLSSPreset`**, **`Set/GetFSRVersion`**, **`ApplyUpscalerSettings()`**.
- **`Set/GetLumenEnabled`** *(Off switches GI and reflections to screen space; On restores the project's own method)*, **`Set/GetHardwareRayTracingEnabled`**, **`ApplyRayTracingSettings()`**.
- Standard **`Apply Settings`** also re-applies the upscaler and the lighting method. All Game User Settings functions (resolution, scalability...) keep working.

---

## 🎨 Enums

| `ESFUpscalerType` | `ESFUpscalerMode` | `ESFFrameGenerationMultiplier` |
| :--- | :--- | :--- |
| `None`, `DLSS`, `FSR`, `TSR` | `Off`, `Auto`, `DLAA` (Native AA), `Quality`, `Balanced`, `Performance`, `UltraPerformance` | `Off`, `x2` to `x6` |

| `ESFDLSSPreset` | `ESFFSRVersion` |
| :--- | :--- |
| `Auto` (NVIDIA's pick per mode), `K` / `J` (transformer), `M` / `L` (DLSS 4.5 second generation transformer) | `Auto` (FSR 4 on RX 7000 / 9000, FSR 3 elsewhere), `FSR3` |

NVIDIA has retired the CNN presets: every current DLSS preset is a transformer model.

**TSR screen percentage:** Quality 66.7%, Balanced 58%, Performance 50%, Ultra Performance 33.3%, Auto / Native AA 100%. DLSS uses the optimal percentage reported by NVIDIA for each mode (100% for DLAA).
