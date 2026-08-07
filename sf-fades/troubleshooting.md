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
The default Z-order for `UScreenFadeWidget` is set very high (e.g. 10,000). If custom UI elements draw over it, ensure their Viewport Z-Order is set lower than 10,000.
