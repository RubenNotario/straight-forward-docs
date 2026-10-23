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
