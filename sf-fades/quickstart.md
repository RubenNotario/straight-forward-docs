# SF Fades - Quickstart Example

Here is a common scenario: fading out to black before loading a new level, and fading back in once loaded.

---

## 🎬 Level Transition Fade Blueprint Flow

1. **Trigger Fade Out:**
   - Call `Get Screen Fade Subsystem` ➔ `Fade Out`.
   - Set `Color = (0, 0, 0, 1)`, `Duration = 1.0`, `bBlockInput = true`.

2. **Wait for Completion:**
   - Bind to `OnFadeComplete` or use an async delay node set to 1.0 second.

3. **Open Level:**
   - Call `Open Level (by Name)`.

4. **Fade Back In (On Level Loaded):**
   - In the `BeginPlay` of your Level Blueprint or PlayerController, call `Fade In` with `Duration = 1.0`.
