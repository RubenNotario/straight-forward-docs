# SF Virtual Cursor - C++ & Blueprint API

---

## 🎮 `USFVirtualCursorSubsystem` (Engine Subsystem)

- **`EnableVirtualCursor()`**: Registers the input pre-processor.
- **`DisableVirtualCursor()`**: Unregisters it.
- **`SetCursorSpeed(NewSpeed)`**: Pixels per second at full stick deflection (default `800`). Kept between enable / disable calls.
- **`IsVirtualCursorEnabled()`** *(bool)*.
- **`GetCursorSpeed()`** *(float)*.

---

## 🕹️ Controls

| Input | Action |
| :--- | :--- |
| Gamepad Left Stick | Moves the cursor (dead zone 0.2). |
| Gamepad Face Button Bottom (A / Cross) | Left mouse click (press + release). |
