# SF Upscaler Toolkit - Configuration Profile

The **Configuration Profile** (`USFUpscalerProfile`) is a Data Asset that gathers in one place the rendering options that normally live in `.ini` files or console commands: first-launch defaults, upscaler tuning, Lumen reflections, ray tracing, the layout of the settings menu and any extra console variable. Every option explains itself in its tooltip, and every category has a read-only **About** text.

---

## 🧭 Where to Set It

**Project Settings > Plugins > SF Upscaler Toolkit > Profile** (`USFUpscalerDeveloperSettings`, stored in `DefaultGame.ini`).

- Leave it empty to use **`DA_SFUpscaler_Default`** shipped with the plugin (`SFUpscaler/Settings`). It has every override off, so it changes nothing until you edit it.
- To make your own: duplicate `DA_SFUpscaler_Default`, or **Content Browser > right click > Miscellaneous > Data Asset > SFUpscalerProfile**, then select it in Project Settings.
- **Packaging:** the selected profile and the default one are added to every cook automatically. No **Additional Asset Directories to Cook** entry is needed.

---

## ⚖️ How Values Are Applied

- **Override checkboxes:** each engine option has a checkbox. Unticked keeps the engine / project value; ticked applies the profile value.
- **Priority:** profile values are set with `SetByCode` priority, above `DefaultEngine.ini`, device profiles and the scalability groups. The console can still override them for debugging.
- **Player choices win:** the **Defaults** category is only used the first time a player starts the game (and after **Reset to Defaults**). Once a player saves their own settings, the profile never changes them.
- **Runtime options** are applied when the game starts and every time the settings are applied (`Apply Settings`, any change in the menu).
- **Options marked (restart)** are startup-only: applied once at `PostEngineInit`, before the first level loads, and **never** while the game runs. Test them in **Standalone** or a packaged build, not in PIE (the editor keeps its own renderer settings). If a startup variable is already read-only, it is skipped with a warning.
- **Missing variables** (vendor plugin not installed, unsupported hardware) are skipped and logged once in `LogSFUpscaler`.

---

## 🎯 Defaults (first launch)

| Property | Effect |
| :--- | :--- |
| `DefaultUpscaler` | Upscaler selected on first launch (`None` = native resolution with the project anti-aliasing). Unsupported choices appear greyed out in the menu. |
| `DefaultUpscalerMode` | Quality mode for that upscaler. An upscaler with mode `Off` starts in `Quality`. |
| `DefaultFrameGeneration` | Frame Generation multiplier. `Off` is recommended: it adds latency, let players opt in. |
| `DefaultDLSSPreset` | DLSS model (`Auto` lets NVIDIA pick per mode). |
| `DefaultFSRVersion` | `Auto` (FSR 4 on Radeon RX 7000 / 9000, FSR 3 elsewhere) or `FSR3`. |
| `bRunAutoDetectOnFirstLaunch` | Runs the hardware benchmark on first launch and applies the recommended scalability levels. |

---

## 🖼️ Upscaler Tuning (runtime)

| Property | Console variable / effect |
| :--- | :--- |
| `MinScreenPercentage` / `MaxScreenPercentage` | Clamp the internal resolution of **Epic TSR** (25-100%). DLSS and FSR pick their own render scale per mode and are not clamped. |
| `TSRHistoryScreenPercentage` | `r.TSR.History.ScreenPercentage` (100-200). 200 keeps detail sharper and more stable at a higher GPU and memory cost. Replaces the value set by the Anti-Aliasing quality level. |
| `FSRSharpness` | `r.FidelityFX.FSR.Sharpness` (0-1). Around 0.2-0.4 brings back detail in Performance modes. Needs the AMD FSR plugin. |
| `bAlwaysEnableLatencyReduction` | Keeps NVIDIA Reflex and AMD Anti-Lag 2 (`r.AMD.AntiLag2`) on even without Frame Generation. Off: they are only forced on while Frame Generation runs. |

> 💡 DLSS sharpness is not exposed: current NVIDIA DLSS plugins have no sharpness console variable.

---

## 💡 Lumen Reflections

| Property | Console variable / effect |
| :--- | :--- |
| `RayLightingMode` **(restart)** | `r.Lumen.HardwareRayTracing.LightingMode`: `Surface Cache` (0, fastest), `Hit Lighting for Reflections` (2, mirror-quality reflections) or `Hit Lighting (GI and Reflections)` (1, highest cost). Only matters with hardware ray tracing on. Startup-only because switching it while a level runs can hang the GPU. |
| `ReflectionsDownsampleFactor` | `r.Lumen.Reflections.DownsampleFactor`. 1 is full resolution; 2 roughly halves the tracing cost with blurrier reflections. |
| `bReflectionScreenTraces` | `r.Lumen.Reflections.ScreenTraces`. Traces against the screen first for sharper contact detail. |
| `MaxRoughnessToTrace` | `r.Lumen.Reflections.MaxRoughnessToTrace` (0-1). Rougher surfaces use the GI instead of reflection rays; lower is cheaper. Overrides Post Process Volume settings. |

---

## 🔦 Ray Tracing

| Property | Console variable / effect |
| :--- | :--- |
| `bSkeletalMeshesInRayTracing` **(restart)** | `r.RayTracing.Geometry.SkeletalMeshes`. Off saves GPU time and memory, but characters disappear from ray traced reflections and shadows. |
| `bAllowRayTracedShadows` | Lets the hardware ray tracing option turn on `r.RayTracing.Shadows`. Off keeps shadow maps / Virtual Shadow Maps even with ray tracing on. Applied at runtime. |

These only take effect when **Support Hardware Ray Tracing** is enabled in Project Settings > Rendering and the player turns hardware ray tracing on.

---

## 🖥️ Menu

| Property | Effect |
| :--- | :--- |
| `HiddenOptions` | Rows `SFGraphicsSettingsWidget` never shows (e.g. Path Tracing). Hidden options keep their saved value; sections left empty disappear. |
| `FrameRateLimits` | Values offered by the Frame rate limit row (0 = Unlimited). Empty uses the built-in list: Unlimited, 30, 60, 90, 120, 144, 165, 240. |

---

## 🧰 Advanced

`ExtraCVars` is a list of extra console variables (`CVar`, `Value`, `Startup Only (restart)`, `Note`), applied with the same priority as the named options. Tick **Startup Only** for variables the renderer reads once.

---

## ▶️ Apply Runtime Options Now

The **Apply Runtime Options Now** button (Profile category of the asset) applies the runtime options to the running editor or game, so you can preview tuning in the viewport. Startup-only options are never touched: restart (or launch Standalone) to see them.
