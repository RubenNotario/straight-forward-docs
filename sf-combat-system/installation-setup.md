# SF Combat System - Installation & Setup

Follow these steps to install **Straight Forward Combat System** in your Unreal Engine project.

---

## 🛍️ Option A: Fab / Unreal Engine Marketplace (Recommended)

1. Acquire the plugin on **Fab** (Epic Games Launcher).
2. Click **Install to Engine** and select your desired Unreal Engine version.
3. Open your project and navigate to **Edit > Plugins**.
4. Search for **Straight Forward Combat System** and check **Enabled**.
5. Restart the editor when prompted.

---

## 📁 Option B: Manual Installation (Project Plugins Folder)

1. Create a `Plugins/` folder in your project root directory if it does not exist.
2. Copy the `StraightForwardCombatSystem` folder into `YourProject/Plugins/`:
   ```
   YourProject/
   └── Plugins/
       └── StraightForwardCombatSystem/
   ```
3. Launch Unreal Engine and verify the plugin is active under **Edit > Plugins > Gameplay > Straight Forward Combat System**.

---

## 🧑‍💻 C++ Projects (Optional)

Add the module to your `YourProject.Build.cs`:
```csharp
PublicDependencyModuleNames.Add("StraightForwardCombatSystem");
```

---

## ⚙️ Basic Setup

1. Add **SF Stats**, **SF Hit Detection** and **SF Combat** components to your character (Combat finds the others on BeginPlay).
2. Create an **SF Weapon Data Asset**: add your attack montages to `LightAttackCombos` (and `HeavyAttackCombos`).
3. In each attack montage add **SF Hitbox** over the active frames and **SF Combo Window** near the end.
4. Set the weapon as `DefaultWeapon` on the Combat component (or call `Equip Weapon`).
5. Your character Anim Blueprint must play montages on `DefaultSlot`.
