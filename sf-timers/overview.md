# SF Timers - Overview

**SF Timers** (`StraightForwardTimers`) is a clean, multi-instance timer management plugin for Unreal Engine.

Powered by `ULevelTimerSubsystem` (a **World Subsystem**), it provides high-performance chronometer (stopwatch) and countdown timer handling per world level without needing tick loops or complex time calculation logic.

---

## 🎯 Key Features

- ⏱️ **Dual Modes:** Full support for both **Stopwatches** (counting up) and **Countdowns** (counting down to 0).
- 🏷️ **Multi-Timer Management:** Run and track multiple named timers concurrently (e.g. `"SpeedrunTimer"`, `"BombCountdown"`, `"MatchTimer"`).
- 🔤 **Built-in String Formatting:** Get pre-formatted strings (`MM:SS.d` like `05:12.3`) or component integer breakdowns (Minutes, Seconds, Deciseconds).
- 📢 **Event Broadcasters:** Assignable delegates for `OnTimerFinished` (when countdown reaches 0) and `OnTimerPaused`.
- 🖥️ **Ready HUD Widget:** `ULevelTimerWidget` displays any named timer with zero Blueprint logic.

---

## 📦 Included Example Content

| Asset | Description |
| :--- | :--- |
| `Levels/HowToUse` | Demo room with stopwatch, 10 s countdown, query and reset buttons, plus two live HUD timers. |
| `Blueprints/HowToUse/BP_TimersDemoController` | Every node used by the room (including `OnTimerFinished` filtered by name). |
| `Widgets/WBP_LevelTimer` / `WBP_CountdownTimer` | `ULevelTimerWidget` children bound to `"Stopwatch"` and `"Countdown"`. |

**Supported engine version:** Unreal Engine 5.8.
