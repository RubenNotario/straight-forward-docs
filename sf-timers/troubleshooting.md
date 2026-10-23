# SF Timers - Troubleshooting

---

### ❓ Timer pauses when the game is paused
**Behavior Explanation:**
`ULevelTimerSubsystem` inherits from `UTickableWorldSubsystem` with `IsTickableWhenPaused()` returning `false` by design, so in-game countdowns automatically pause during pause menus.

---

### ❓ `GetFormattedTime` returns `"00:00.0"`
**Solution:**
Check that the `TimerName` passed to `GetFormattedTime` matches the exact string name used when calling `StartTimer` or `StartCountdown`. (Names are case-sensitive).

---

### ❓ The HUD widget does not compile: "A required widget binding TimerText was not found"
**Solution:**
`ULevelTimerWidget` uses `BindWidget`. Add a **Text Block** named exactly `TimerText` to your Widget Blueprint.

---

### ❓ Timers reset after `Open Level`
**Behavior Explanation:**
Timers belong to the world. Save the value (`GetCurrentTimeInSeconds`) in your Game Instance before travelling and restore it with a new countdown if needed.
