# SF Timers - Quickstart Example

Example implementation of a 60-second challenge countdown with a HUD timer widget.

---

## ⏱️ Blueprint Setup

1. **Start the Countdown:**
   - On Game/Level Start, get `LevelTimerSubsystem`.
   - Call `StartCountdown(FName("MatchTimer"), 60.0f)`.

2. **Update UMG HUD Text Widget:**
   - In your HUD Widget's `Tick` or timer event:
   - Call `Get Level Timer Subsystem` ➔ `Get Formatted Time("MatchTimer")`.
   - Bind output `FString` directly to your Text Block widget.

3. **Handle Match Finish:**
   - Bind to `OnTimerFinished`.
   - Filter by `TimerName == "MatchTimer"`.
   - Trigger Game Over / End Level logic!
