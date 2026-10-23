# SF Fades - Troubleshooting

---

### ❓ Custom Material fade is not animating
**Solution:**
Ensure your material contains a Scalar Parameter named `"FadeAmount"` (or specify your custom parameter name in the `ParameterName` pin of `FadeOutWithMaterial`).

---

### ❓ Player input remains blocked after fade ends
**Solution:**
If `bBlockInput` was set to `true` during `FadeOut`, ensure you call `FadeIn` (or `StopFade`) when the transition is finished to restore input focus to the player controller.

---

### ❓ Fade widget is rendered behind other UI elements
**Solution:**
The fade widget is added to the viewport with Z-Order `9999`. If custom UI elements draw over it, ensure their Viewport Z-Order is lower than `9999` (or higher, if they must stay visible during the transition).

---

### ❓ Material fade renders as a solid black screen
**Solution:**
Fixed in the current version: the fade image tint is reset to white when a material is assigned, so the material controls color and opacity. If you use a custom `UScreenFadeWidget`, do not tint the `FadeImage` yourself while a material fade is active.

---

### ❓ My material fade covers the screen instantly
**Solution:**
The subsystem drives the scalar parameter from `0` to `1`. Make the material **Opacity** depend on it (Material Domain: **User Interface**, Blend Mode: **Translucent**). See `Materials/M_SF_FadeGradient` in the plugin content for a working wipe example.
