# SF Toasts - Installation & Setup

Follow these steps to install **StraightForwardToasts**.

---

## 📁 1. Plugin Placement

1. Copy the `StraightForwardToasts` folder into your project's `Plugins/` directory:
   ```
   YourProject/
   └── Plugins/
       └── StraightForwardToasts/
   ```
2. Enable **Straight Forward Toasts** in **Edit > Plugins > UI**.

---

## ⚙️ 2. Subsystem Lifetime

`UScreenMessageSubsystem` is a World Subsystem. It instantiates automatically when the world loads and builds the layout canvas overlay when the first message or popup is triggered.
