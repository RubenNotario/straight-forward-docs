# SF Upscaler Toolkit - C++ & Blueprint API

---

## 🚀 Quick Set Library (`USFUpscalerLibrary`)

- **`SetAndApplyUpscalerMode(Type, Mode)`**: Sets, applies and saves.
- **`SetAndApplyFrameGeneration(Multiplier)`**: Sets, applies and saves.
- **`IsDLSSSupported()`**, **`IsFSRSupported()`**, **`IsFrameGenerationSupported()`** *(bool)*.

---

## 💾 `USFUpscalerSettings` (Game User Settings)

- **`GetSFUpscalerSettings()`**: Returns the settings object (requires the ini setup).
- **`Set/GetUpscalerType`**, **`Set/GetUpscalerMode`**, **`Set/GetFrameGenerationMultiplier`**, **`ApplyUpscalerSettings()`**.
- Standard **`Apply Settings`** also re-applies the upscaler.

---

## 🎨 Enums

| `ESFUpscalerType` | `ESFUpscalerMode` | `ESFFrameGenerationMultiplier` |
| :--- | :--- | :--- |
| `None`, `DLSS`, `FSR`, `TSR` | `Off`, `Auto`, `Quality`, `Balanced`, `Performance`, `UltraPerformance` | `Off`, `x2`, `x3`, `x4` |

**TSR screen percentage:** Quality 66.7%, Balanced 58%, Performance 50%, Ultra Performance 33.3%, Auto 100% (TSR as anti-aliasing).
