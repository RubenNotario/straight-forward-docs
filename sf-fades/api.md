# SF Fades - C++ & Blueprint API

All fade functionality is accessible via `UScreenFadeSubsystem`.

---

## 🛠️ Functions Reference

### `FadeOut`
Fades the screen out to a solid color.
- **`Color`** *(FLinearColor)*: Target color (e.g., Black, White).
- **`Duration`** *(float)*: Fade duration in seconds.
- **`bBlockInput`** *(bool)*: If `true`, disables Player Controller input during the fade.

### `FadeIn`
Fades the screen in from its current color back to full visibility.
- **`Duration`** *(float)*: Fade duration in seconds.
- **`bBlockInput`** *(bool)*: If `true`, input remains blocked during the fade-in.

### `FadeOutWithMaterial`
Fades the screen using a dynamic material interface (e.g. noise dissolve, wipe transition).
- **`Material`** *(UMaterialInterface*)*: Material asset used for the transition.
- **`Duration`** *(float)*: Fade duration in seconds.
- **`bBlockInput`** *(bool)*: Whether to block player input.
- **`ParameterName`** *(FName)*: Scalar parameter name in the material driven from 0 to 1 (Default: `"FadeAmount"`).

### `FadeInWithMaterial`
Fades the screen back in using the current active transition material.

### `StopFade`
Instantly halts any ongoing fade transition and resets viewport alpha.

---

## 📢 Delegates & Properties

- **`OnFadeComplete`**: Dynamic multicast event dispatcher fired when any fade finishes.
- **`FadeWidgetClass`**: `TSubclassOf<UScreenFadeWidget>` property to customize the overlay widget.
