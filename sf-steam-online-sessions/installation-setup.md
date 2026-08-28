# SF Steam Online Sessions - Installation & Setup

Follow these steps to install and configure **Straight Forward Steam Sessions** in your Unreal Engine project.

---

## 🛍️ Option A: Fab / Unreal Engine Marketplace (Recommended)

1. Acquire the plugin on **Fab** (Epic Games Launcher).
2. Click **Install to Engine** and select your desired Unreal Engine version.
3. Open your Unreal Engine project and navigate to **Edit > Plugins**.
4. Search for **Straight Forward Steam Sessions** and check **Enabled**.
5. Restart the editor when prompted.

---

## 📁 Option B: Manual Installation (Project Plugins Folder)

If installing from a standalone ZIP or repository build:

1. Create a `Plugins/` folder in your project root directory if it does not exist.
2. Copy the `StraightForwardOnlineSessions` folder into `YourProject/Plugins/`:
   ```
   YourProject/
   └── Plugins/
       └── StraightForwardOnlineSessions/
   ```
3. Regenerate Visual Studio project files (if using C++) and launch the editor.
4. Verify the plugin is enabled in **Edit > Plugins**.

---

## ⚙️ Project & Engine Configuration

Ensure Steam Online Subsystem and SteamSockets are configured in your project's `Config/DefaultEngine.ini`:

```ini
[/Script/Engine.GameEngine]
!NetDriverDefinitions=ClearArray
+NetDriverDefinitions=(DefName="GameNetDriver",DriverClassName="/Script/SteamSockets.SteamSocketsNetDriver",FallbackDriverClassName="/Script/OnlineSubsystemUtils.IpNetDriver")

[OnlineSubsystem]
DefaultPlatformService=Steam

[OnlineSubsystemSteam]
bEnabled=true
SteamDevAppId=480
bInitServerOnClient=true

[/Script/SteamSockets.SteamSocketsNetDriver]
NetConnectionClassName="/Script/SteamSockets.SteamSocketsNetConnection"
```

---

## 📦 Build.cs Dependencies (C++ Projects)

If referencing the subsystem from C++, add the module to your project's `YourProject.Build.cs`:

```csharp
PublicDependencyModuleNames.AddRange(new string[] {
    "Core",
    "CoreUObject",
    "Engine",
    "InputCore",
    "StraightForwardOnlineSessions",
    "OnlineSubsystem",
    "OnlineSubsystemSteam",
    "OnlineSubsystemUtils"
});
```
