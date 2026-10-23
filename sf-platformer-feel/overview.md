# SF Platformer Feel - Overview

**SF Platformer Feel** (`StraightForwardPlatformerFeel`) adds the small forgiving mechanics that make platformers feel responsive, plus collectible helpers. Extracted from *Kinetic Roll*.

---

## 🎯 Key Features

- 🐺 **Coyote Time:** jump for a short window after walking off a ledge.
- ⌨️ **Jump Buffer:** a jump pressed just before landing is executed on touchdown.
- 🧩 **One Component:** `UCoyoteTimeComponent` for any `ACharacter`, event driven (no Tick).
- 🪙 **Pickup Base:** respawnable collectible with score value, identifier, VFX, SFX and `OnPickup`.
- 🌈 **Parabola Spawner:** lays out collectibles along an arc edited with 3D widgets.

---

## 📦 Included Example Content

| Asset | Description |
| :--- | :--- |
| `Levels/HowToUse` | Third Person demo room with ledges (coyote time), a step (buffer) and a coin arc. |
| `Blueprints/HowToUse/BP_PlatformerDemoController` | `HandleJumpPressed` shows the full coyote + buffer jump logic. |
| `Blueprints/HowToUse/BP_SFDemoCoin` | `PickupBase` child with respawn and `OnPickup`. |

**Supported engine version:** Unreal Engine 5.8.
