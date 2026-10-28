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

### ❓ Tab or gamepad input stops working after clicking the menu
**Solution:**
A focused button consumes Tab for UI navigation. Untick **Is Focusable** on the menu buttons (the included widgets already do).
