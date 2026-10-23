# SF Interaction System - Installation & Setup

Follow these steps to install **Universal Interaction System** in your Unreal Engine project.

---

## 🛍️ Option A: Fab / Unreal Engine Marketplace (Recommended)

1. Acquire the plugin on **Fab** (Epic Games Launcher).
2. Click **Install to Engine** and select your desired Unreal Engine version.
3. Open your project and navigate to **Edit > Plugins**.
4. Search for **Universal Interaction System** and check **Enabled**.
5. Restart the editor when prompted.

---

## 📁 Option B: Manual Installation (Project Plugins Folder)

1. Create a `Plugins/` folder in your project root directory if it does not exist.
2. Copy the `UniversalInteractionSystem` folder into `YourProject/Plugins/`:
   ```
   YourProject/
   └── Plugins/
       └── UniversalInteractionSystem/
   ```
3. Launch Unreal Engine and verify the plugin is active under **Edit > Plugins > Gameplay > Universal Interaction System**.

---

## 🧑‍💻 C++ Projects (Optional)

Add the module to your `YourProject.Build.cs`:
```csharp
PublicDependencyModuleNames.Add("UniversalInteractionSystem");
```

---

## ⚙️ Basic Setup

1. **Player:** add an **Interactor Component** to your character. Call **Try Interact** when the interact key is pressed and **Stop Interact** when it is released.
2. **Interactive actors:** add an **Interactable Component** and bind its events (`On Interact Event`, `On Begin Focus Event`...). Alternatively implement `IInteractableInterface` directly on the actor.
3. **Collision:** the interactable needs a component that blocks the trace channel used by the Interactor (`Visibility` by default).
