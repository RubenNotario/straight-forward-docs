# SF Timers - Troubleshooting

---

### ❓ Timer pauses when the game is paused
**Behavior Explanation:**
`ULevelTimerSubsystem` inherits from `UTickableWorldSubsystem` with `IsTickableWhenPaused()` returning `false` by design, so in-game countdowns automatically pause during pause menus.

---

### ❓ `GetFormattedTime` returns `"00:00.0"`
**Solution:**
Check that the `TimerName` passed to `GetFormattedTime` matches the exact string name used when calling `StartTimer` or `StartCountdown`. (Names are case-sensitive).
