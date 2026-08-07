# SF Timers - Installation & Setup

Follow these steps to install **StraightForwardTimers**.

---

## 📁 1. Plugin Placement

1. Copy the `StraightForwardTimers` folder into your project's `Plugins/` directory:
   ```
   YourProject/
   └── Plugins/
       └── StraightForwardTimers/
   ```
2. Launch Unreal Engine and verify the plugin is active under **Edit > Plugins > Systems > Straight Forward Timers**.

---

## ⚙️ 2. Subsystem Lifetime

`ULevelTimerSubsystem` inherits from `UTickableWorldSubsystem`.
- It initializes automatically when a world level loads.
- Timers are automatically cleaned up when traveling between levels, avoiding memory leaks and stray background loops.
