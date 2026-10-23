# SF Camera Auto Align - C++ & Blueprint API

---

## 🎥 `UCameraAutoAlignComponent`

| Property | Default | Description |
| :--- | :--- | :--- |
| `AutoAlignDelay` | `3 s` | Time without camera input before aligning. |
| `AlignInterpolationSpeed` | `3` | Interpolation speed back to the target rotation. |
| `AlignmentMode` | `AlignToActorForward` | `AlignToActorForward`, `AlignToVisualMeshForward`, `AlignToMovementDirection`. |
| `VisualMeshYawOffset` | `90` | Yaw correction for rotated meshes (Visual Mesh mode). |
| `bResetPitch` | `false` | Also recenter the vertical angle. |
| `DefaultPitch` | `-10` | Pitch to return to when `bResetPitch` is true. |
| `bIsAutoAlignEnabled` | `true` | Master switch. |

- **`SetAutoAlignEnabled(bEnabled)`** / **`IsAutoAlignEnabled()`**.
- **`ResetCameraInputTimer()`**: Restart the delay manually (optional).
