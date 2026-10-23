# SF Fades - Overview

**SF Fades** (`StraightForwardFades`) is a lightweight Unreal Engine plugin that provides seamless, asynchronous screen fade-in and fade-out transitions.

Driven by `UScreenFadeSubsystem` (a **GameInstance Subsystem**), fade transitions persist seamlessly across level loads and UI state changes.

---

## 🎯 Key Features

- 🎨 **Solid Color & Material Fades:** Smoothly fade to any `FLinearColor` or drive complex dissolve effects with custom post-process/UI Materials.
- ⏸️ **Tickable When Paused:** Fades continue updating smoothly even when `Set Game Paused` is true.
- 🔒 **Optional Input Blocking:** Automatically block player input during transitions to prevent unwanted actions during screen transitions.
- 📢 **Completion Delegates:** Event dispatcher (`OnFadeComplete`) fires when a fade transition reaches 100% completion.

---

## 📦 Included Example Content

| Asset | Description |
| :--- | :--- |
| `Levels/HowToUse` | Walkable demo room (Third Person template) with one button per use case: color fade, material fade, `OnFadeComplete` + teleport, damage flash. |
| `Blueprints/HowToUse/BP_FadesDemoController` | Every node used by the room, one event graph per use case. |
| `Materials/M_SF_FadeGradient` | UI material (SF purple to blue wipe) driven by `FadeAmount`. |

**Supported engine version:** Unreal Engine 5.8.
