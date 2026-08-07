# SF Timers - C++ & Blueprint API

All timer management functions are available on `ULevelTimerSubsystem`.

---

## 🛠️ Main Control Functions

### `StartTimer`
Starts or resumes a stopwatch timer counting upwards from zero.
- **`TimerName`** *(FName)*: Identifier tag for the timer (Default: `"DefaultTimer"`).

### `StartCountdown`
Starts a countdown timer counting down to 0.
- **`TimerName`** *(FName)*: Identifier tag.
- **`StartSeconds`** *(float)*: Initial countdown time in seconds.

### `PauseTimer`
Pauses execution of a running timer without clearing its elapsed time.
- **`TimerName`** *(FName)*: Identifier tag.

### `StopTimer`
Stops a timer.
- **`TimerName`** *(FName)*: Identifier tag.
- **`bReset`** *(bool)*: If `true`, resets current time back to 0 (or start time).

### `ResetTimer`
Resets a specific timer to 0 without deleting its entry from memory.

### `RemoveTimer`
Completely removes a timer entry from active memory.

---

## 🔍 Getter Functions

- **`GetCurrentTimeInSeconds(TimerName)`** *(float)*: Returns current raw seconds elapsed/remaining.
- **`GetFormattedTime(TimerName)`** *(FString)*: Returns formatted time string formatted as `MM:SS.d` (e.g. `"03:45.2"`).
- **`GetTimeComponents(TimerName, OutMinutes, OutSeconds, OutDeciseconds)`**: Returns integer values breakdown.
- **`IsTimerRunning(TimerName)`** *(bool)*: Returns `true` if active and running.

---

## 📢 Assignable Delegates

- **`OnTimerFinished(FName TimerName)`**: Broadcasted when a countdown timer reaches 0.
- **`OnTimerPaused(FName TimerName)`**: Broadcasted when a timer is paused.
