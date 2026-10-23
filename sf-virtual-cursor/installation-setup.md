# SF Virtual Cursor - Installation & Setup

Follow these steps to install **Straight Forward Virtual Cursor** in your Unreal Engine project.

---

## 🛍️ Option A: Fab / Unreal Engine Marketplace (Recommended)

1. Acquire the plugin on **Fab** (Epic Games Launcher).
2. Click **Install to Engine** and select your desired Unreal Engine version.
3. Open your project and navigate to **Edit > Plugins**.
4. Search for **Straight Forward Virtual Cursor** and check **Enabled**.
5. Restart the editor when prompted.

---

## 📁 Option B: Manual Installation (Project Plugins Folder)

1. Create a `Plugins/` folder in your project root directory if it does not exist.
2. Copy the `StraightForwardVirtualCursor` folder into `YourProject/Plugins/`:
   ```
   YourProject/
   └── Plugins/
       └── StraightForwardVirtualCursor/
   ```
3. Launch Unreal Engine and verify the plugin is active under **Edit > Plugins > UI > Straight Forward Virtual Cursor**.

---

## 🧑‍💻 C++ Projects (Optional)

Add the module to your `YourProject.Build.cs`:
```csharp
PublicDependencyModuleNames.Add("StraightForwardVirtualCursor");
```

---

## ⚙️ Basic Setup

When a mouse-driven menu opens: `Get SF Virtual Cursor Subsystem` ➔ `Enable Virtual Cursor`, `Set Show Mouse Cursor (true)`, `Set Input Mode Game And UI`. When it closes, call `Disable Virtual Cursor` and restore Game Only input.
