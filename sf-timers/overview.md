# SF Timers - Overview

**SF Timers** (`StraightForwardTimers`) is a clean, multi-instance timer management plugin for Unreal Engine.

Powered by `ULevelTimerSubsystem` (a **World Subsystem**), it provides high-performance chronometer (stopwatch) and countdown timer handling per world level without needing tick loops or complex time calculation logic.

---

## 🎯 Key Features

- ⏱️ **Dual Modes:** Full support for both **Stopwatches** (counting up) and **Countdowns** (counting down to 0).
- 🏷️ **Multi-Timer Management:** Run and track multiple named timers concurrently (e.g. `"SpeedrunTimer"`, `"BombCountdown"`, `"MatchTimer"`).
- 🔤 **Built-in String Formatting:** Get pre-formatted strings (`MM:SS.d` like `05:12.3`) or component integer breakdowns (Minutes, Seconds, Deciseconds).
- 📢 **Event Broadcasters:** Assignable delegates for `OnTimerFinished` (when countdown reaches 0) and `OnTimerPaused`.
