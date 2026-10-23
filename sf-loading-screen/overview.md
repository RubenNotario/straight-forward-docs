# SF Loading Screen - Overview

**SF Loading Screen** (`StraightForwardLoadingScreen`) shows an animated loading screen on every map load, rendered by the Movie Player so it keeps animating while the game thread is busy.

---

## 🎯 Key Features

- ⚡ **Automatic:** hooks `PreLoadMap` / `PostLoadMap`; no Blueprint needed.
- 🧵 **Multithreaded Slate UI:** smooth throbber and text while the level loads.
- 🗂️ **Data Driven:** title, random tips, background images, movies and minimum display time from Project Settings.
- 💬 **Contextual Tips:** `SetNextLoadingTip` overrides the random tip for the next transition.
- 🕹️ **Manual Control:** show / hide it without a map change.

---

## 📦 Included Example Content

| Asset | Description |
| :--- | :--- |
| `Levels/HowToUse` | Demo room: automatic travel, custom tip, manual show / hide and status. |
| `Blueprints/HowToUse/BP_LoadingScreenDemoController` | Every node used by the room. |

**Supported engine version:** Unreal Engine 5.8.
