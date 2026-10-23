# SF Camera Auto Align - Overview

**SF Camera Auto Align** (`StraightForwardCameraAutoAlign`) recenters a third person camera behind the character after a period without camera input, like modern action games.

Part of the **SF Core Toolkit**.

---

## 🎯 Key Features

- 🎥 **One Component:** `UCameraAutoAlignComponent` for characters with a Spring Arm or controller-driven camera.
- 🖱️ **Automatic Input Detection:** no input wiring; manual camera movement restarts the delay.
- 🧭 **Three Modes:** actor forward, visual mesh forward (ALS / Lyra style rigs) or movement direction.
- ↕️ **Optional Pitch Reset** to a default angle.
- 🔀 **Runtime Toggle:** disable during aiming, cutscenes or lock-on.

---

## 📦 Included Example Content

| Asset | Description |
| :--- | :--- |
| `Levels/HowToUse` | Third Person demo room with buttons for each mode, pitch reset and on/off. |
| `Blueprints/HowToUse/BP_CameraAutoAlignDemoController` | Adds the component at runtime and reconfigures it. |

**Supported engine version:** Unreal Engine 5.8.
