# SF Steam Online Sessions - Installation & Setup

Follow these steps to install and configure **Straight Forward Online Sessions** in your Unreal Engine project.

---

## 🛍️ Option A: Fab / Unreal Engine Marketplace (Recommended)

1. Acquire the plugin on **Fab** (Epic Games Launcher).
2. Click **Install to Engine** and select your desired Unreal Engine version.
3. Open your Unreal Engine project and navigate to **Edit > Plugins**.
4. Search for **Straight Forward Online Sessions** and check **Enabled**.
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

Ensure Steam Online Subsystem is configured in your project's `Config/DefaultEngine.ini`:

```ini
[/Script/Engine.GameEngine]
+NetDriverDefinitions=(DefName="GameNetDriver",DriverClassName="OnlineSubsystemSteam.SteamNetDriver",DriverClassNameFallback="OnlineSubsystemUtils.IpNetDriver")

[OnlineSubsystem]
DefaultPlatformService=Steam

[OnlineSubsystemSteam]
bEnabled=true
SteamDevAppId=480
bAllowP2PPacketRelay=true
P2PConnectionTimeout=90

[/Script/OnlineSubsystemSteam.SteamNetDriver]
NetConnectionClassName="OnlineSubsystemSteam.SteamNetConnection"
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
    "OnlineSubsystemUtils"
});
```
