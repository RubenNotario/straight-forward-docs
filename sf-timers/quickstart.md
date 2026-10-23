# SF Timers - Quickstart Example

Example implementation of a 60-second challenge countdown with a HUD timer widget.

---

## ⏱️ Blueprint Setup

1. **Start the Countdown:**
   - On Game/Level Start, get `LevelTimerSubsystem`.
   - Call `StartCountdown(FName("MatchTimer"), 60.0f)`.

2. **Show it on the HUD (no Blueprint logic):**
   - Create a Widget Blueprint with parent class `LevelTimerWidget`.
   - Add a Text Block named exactly `TimerText`.
   - Set **Target Timer Name** = `MatchTimer` in Class Defaults (or on the `Create Widget` node) and **Add to Viewport**.
   - *Alternative:* in any widget, bind a Text Block to `Get Formatted Time("MatchTimer")`.

3. **Handle Match Finish:**
   - Bind to `OnTimerFinished`.
   - Filter by `TimerName == "MatchTimer"`.
   - Trigger Game Over / End Level logic!
