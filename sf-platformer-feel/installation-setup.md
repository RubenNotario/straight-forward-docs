# SF Platformer Feel - Installation & Setup

Follow these steps to install **Straight Forward Platformer Feel** in your Unreal Engine project.

---

## 🛍️ Option A: Fab / Unreal Engine Marketplace (Recommended)

1. Acquire the plugin on **Fab** (Epic Games Launcher).
2. Click **Install to Engine** and select your desired Unreal Engine version.
3. Open your project and navigate to **Edit > Plugins**.
4. Search for **Straight Forward Platformer Feel** and check **Enabled**.
5. Restart the editor when prompted.

---

## 📁 Option B: Manual Installation (Project Plugins Folder)

1. Create a `Plugins/` folder in your project root directory if it does not exist.
2. Copy the `StraightForwardPlatformerFeel` folder into `YourProject/Plugins/`:
   ```
   YourProject/
   └── Plugins/
       └── StraightForwardPlatformerFeel/
   ```
3. Launch Unreal Engine and verify the plugin is active under **Edit > Plugins > Gameplay > Straight Forward Platformer Feel**.

---

## 🧑‍💻 C++ Projects (Optional)

Add the module to your `YourProject.Build.cs`:
```csharp
PublicDependencyModuleNames.Add("StraightForwardPlatformerFeel");
```

---

## ⚙️ Basic Setup

1. Add a **Coyote Time Component** to your character.
2. In your Jump input (Pressed): if **Can Jump** ➔ `Jump`; else if **Try Coyote Jump** returns false ➔ `Register Jump Input`.
3. Bind **On Buffered Jump Triggered** ➔ `Jump`.
