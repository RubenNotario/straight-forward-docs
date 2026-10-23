# SF Camera Auto Align - Troubleshooting

---

### ❓ The camera aligns to the shoulder instead of behind
**Solution:**
Use `AlignToVisualMeshForward` and set `VisualMeshYawOffset` to `90` or `-90` depending on your mesh orientation.

---

### ❓ The camera fights the player
**Solution:**
Increase `AutoAlignDelay` (1.5 - 3 s) and lower `AlignInterpolationSpeed`.
