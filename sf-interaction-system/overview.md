# SF Interaction System - Overview

**SF Interaction System** (`UniversalInteractionSystem`) is a decoupled interaction framework for Unreal Engine built on one interface and two components.

The player owns an `UInteractorComponent` that traces from the camera (or the mouse cursor) and talks to anything implementing `IInteractableInterface`. Interactive actors only expose events; the player never needs to know their class.

---

## 🎯 Key Features

- 🔌 **Interface Driven:** `IInteractableInterface` on actors or components (`UInteractableComponent` implements it for you).
- 🎯 **Focus Detection:** Camera Center or Mouse Cursor detection with Line, Sphere or Box traces and a configurable channel.
- 👆 **Tap & Hold:** `OnInteract` on press and `OnInteractHoldProgress` every frame while the key is held.
- 👀 **Focus Events:** `OnBeginFocus` / `OnEndFocus` for highlights and prompts, with `GetInteractText` for the HUD.
- 🧱 **Ready Trigger Actor:** `AInteractableTriggerBase` with a box and an `OnInteract` dispatcher for Level Blueprint scripting.

---

## 📦 Included Example Content

| Asset | Description |
| :--- | :--- |
| `Levels/HowToUse` | First Person demo room: lamp (tap), focus cube, chest (hold 1.5 s) and a debug trace toggle. |
| `Blueprints/HowToUse/BP_InteractionDemoController` | Adds the Interactor to the player and maps **E** to Try / Stop Interact. |
| `Blueprints/HowToUse/BP_Interactable*` | One Blueprint per use case, using only Interactable Component events. |

**Supported engine version:** Unreal Engine 5.8.
