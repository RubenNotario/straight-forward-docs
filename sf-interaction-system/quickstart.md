# SF Interaction System - Quickstart Example

A light switch that the player can toggle with **E**.

---

## 💡 Interactive Lamp

1. Create an Actor Blueprint `BP_Lamp` with a **Static Mesh**, a **Point Light** and an **Interactable Component**.
2. Set `InteractText` = `"Toggle lamp"`.
3. Select the Interactable Component ➔ **On Interact Event** ➔ `Toggle Visibility (Point Light)`.

## 🎮 Player Input

1. In your character, add an **Interactor Component**.
2. Interact input **Pressed** ➔ `Try Interact`. **Released** ➔ `Stop Interact`.

## ⏳ Hold To Open

1. Bind **On Interact Hold Progress Event** on a chest.
2. `If Progress >= 1.5 and not Opened` ➔ open it and set `Opened = true`.

> 💡 Open `Levels/HowToUse` in the plugin content to try the three examples in play mode.
