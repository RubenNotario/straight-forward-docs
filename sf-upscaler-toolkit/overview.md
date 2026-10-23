# SF Upscaler Toolkit - Overview

**SF Upscaler Toolkit** (`SFUpscaler`) wraps Epic TSR, NVIDIA DLSS and AMD FSR behind one Blueprint API with saved user settings.

---

## 🎯 Key Features

- 🖼️ **One API, Three Upscalers:** `SetAndApplyUpscalerMode(Type, Mode)` for TSR, DLSS and FSR.
- 🚀 **Frame Generation:** x2 / x3 / x4 multipliers (DLSS 4, FSR interpolation) with Reflex enabled automatically.
- 💾 **Persistent Settings:** `USFUpscalerSettings` extends Game User Settings, so choices are saved with the rest of your options.
- 🔍 **Support Queries:** show only what the machine can run.
- 🔗 **No Hard Link:** vendor plugins are detected at runtime through their console variables.

---

## 📦 Included Example Content

| Asset | Description |
| :--- | :--- |
| `Levels/HowToUse` | Demo room with TSR / DLSS / FSR / native buttons and a support report on start. |
| `Blueprints/HowToUse/BP_UpscalerDemoController` | Every node used by the room. |

**Supported engine version:** Unreal Engine 5.8.
