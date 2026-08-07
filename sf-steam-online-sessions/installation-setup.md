# SF Steam Online Sessions - Installation & Setup

Follow these steps to integrate **StraightForwardOnlineSessions** into your Unreal Engine project.

---

## 📁 1. Plugin Placement

1. Copy the `StraightForwardOnlineSessions` folder into your project's `Plugins/` directory:
   ```
   YourProject/
   └── Plugins/
       └── StraightForwardOnlineSessions/
   ```
2. Regenerate your Visual Studio project files (if using C++) and launch the editor.
3. Verify in **Edit > Plugins** that **Straight Forward Online Sessions** is enabled.

---

## ⚙️ 2. Project & Engine Configuration

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

## 📦 3. Build.cs Dependencies (C++ Projects)

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
