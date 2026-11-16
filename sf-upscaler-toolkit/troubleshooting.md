# SF Upscaler Toolkit - Troubleshooting

---

### ❓ Calls do nothing
**Solution:**
`GameUserSettingsClassName` is not set. Add the ini line from **Installation & Setup** and restart the editor. The log shows a `LogSFUpscaler` warning in this case.

---

### ❓ `Is DLSS Supported` / `Is FSR Supported` returns false
**Solution:**
Enable the vendor plugin in your project. Hardware support is decided by the vendor plugin itself.

---

### ❓ TSR did not change the resolution (older versions)
**Solution:**
Fixed in the current version: TSR now sets `r.AntiAliasingMethod 4` and the screen percentage of the selected mode.

---

### ❓ Resolution, window mode or Frame Generation do nothing in PIE
**Solution:**
Play In Editor renders inside the editor viewport, which keeps its own resolution and screen percentage. Test those options in **Standalone** or a packaged build.

---

### ❓ A Frame Generation multiplier is missing
**Solution:**
Only the multipliers the GPU and driver support are listed (multi frame generation needs newer RTX GPUs). Unsupported rows are disabled instead of failing.

---

### ❓ The FPS counter does not match the NVIDIA / AMD overlay
**Solution:**
With Frame Generation the game only renders part of the frames. The overlay shows the frames presented on screen first (the vendor overlay number) and the rendered ones below. Without Frame Generation both should match.

---

### ❓ Lighting method is locked on "Off (quality Low)"
**Solution:**
Unreal disables Lumen when Global illumination or Reflections are on Low. Raise both to Medium or above.

---

### ❓ "Lumen (hardware RT)" is not offered
**Solution:**
Enable **Support Hardware Ray Tracing** in Project Settings > Rendering (`r.RayTracing=True`) and use a GPU with ray tracing support. Characters may look flat or tinted in mirror reflections: Lumen shades them from its surface cache, which has no cards for skeletal meshes.

---

### ❓ Tab or gamepad input stops working after clicking the menu
**Solution:**
A focused button consumes Tab for UI navigation. Untick **Is Focusable** on the menu buttons (the included widgets already do).

---

### ❓ A menu option has no effect (e.g. Lighting method or Lumen)
**Solution:**
Older versions applied settings with a priority below `DefaultEngine.ini`, so project values silently won. Fixed: every option is now applied with `SetByCode` priority. Only the console can override it.

---

### ❓ An option is greyed out
**Solution:**
The plugin only offers what the PC can run:
- **NVIDIA DLSS:** needs the DLSS plugin and an NVIDIA GeForce RTX GPU.
- **DLSS Frame Generation:** RTX 40 series or newer; x3 / x4 need an RTX 50 series.
- **Ray Reconstruction:** needs DLSS plus hardware ray tracing (Lighting method: Lumen hardware RT).
- **AMD FSR:** needs the FSR plugin; works on any modern GPU (FSR 4 on Radeon RX 7000 / 9000, FSR 3 elsewhere).
- **Hardware ray tracing:** needs a GPU with ray tracing support, DirectX 12 and **Support Hardware Ray Tracing** in Project Settings.

---

### ❓ The GPU hangs (DXGI_ERROR_DEVICE_HUNG) after switching to Hit Lighting reflections
**Solution:**
Changing `r.Lumen.HardwareRayTracing.LightingMode` while a level is running can hang the GPU. Set **Ray Lighting Mode** in the [Configuration Profile](configuration-profile.md) instead: it is applied once at startup, never at runtime.

---

### ❓ Profile options marked (restart) do nothing in PIE
**Solution:**
Startup-only options are applied when the game starts, not in Play In Editor (the editor keeps its own renderer settings). Test them in **Standalone** or a packaged build. Runtime options can be previewed with **Apply Runtime Options Now**.

---

### ❓ The profile is ignored in a packaged build
**Solution:**
The active and default profiles are cooked automatically. Check the log for `LogSFUpscaler: configuration profile ... could not be loaded` and that **Project Settings > Plugins > SF Upscaler Toolkit > Profile** points to an existing asset.
