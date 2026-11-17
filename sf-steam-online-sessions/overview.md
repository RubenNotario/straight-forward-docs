# SF Steam Online Sessions - Overview

**Straight Forward Steam Sessions** is a lightweight, production-ready, and unopinionated Unreal Engine plugin designed to wrap Unreal's Online Subsystem (OSS) and Steam Online Subsystem into a clean, easy-to-use GameInstance Subsystem (`USFOSMultiplayerSessionsSubsystem`).

Built under the **Straight Forward Solid Systems** philosophy, it provides decoupled, modular building blocks: developers can create 1-click frictionless friend lobbies or build advanced server browsers with arbitrary custom metadata without touching C++.

---

## 🎯 Key Features

- 🌐 **Unopinionated & Flexible Hosting:** Host simple 1-click lobbies or pass custom metadata dictionaries (`CustomData`) such as map names, game modes, and custom modifiers.
- 🔍 **Custom Matchmaking & Search Filters:** Filter public sessions using `SearchFilters` or query global Steam lobbies with zero boilerplate.
- 👥 **Steam Friends & Overlay Invites:** Search exclusively for Steam friend games and open the native Steam Overlay friend invitation dialog with 1 click.
- 🖼️ **Steam Player Avatars (GC-Protected):** Fetch player Steam profile pictures directly into `UTexture2D` widgets for custom lobby menus, cached and safe against Garbage Collection.
- 🔄 **Async Event Delegates:** Dynamic multicast delegates for creation, discovery, friend search, joining, and destruction of sessions.
- ✈️ **Clean Server Travel:** Built-in helper to execute seamless server travel with `?listen` for all connected players. The demo shows a travel indicator (amber spinner + "Changing level...") to every player before the map changes.
- ⏸️ **Demo Pause Menu:** the gameplay levels include a pause menu (TAB or ESC) with **Resume** and **Main Menu**; Main Menu leaves the session and returns to the menu, even when no session is active.
- 🏠 **Automatic LAN Fallback:** if the Steam client is not available, the Online Subsystem falls back to `NULL` and sessions are created and searched as LAN matches (useful for local testing).
- 🛡️ **Zero Bloat & Production Ready:** Zero unnecessary tick, fully event-driven, leak-free RAII memory management, and zero forced workflow restrictions.

---

## 📸 Blueprint API Visual Overview

![SF Steam Online Sessions - Blueprint Nodes Overview](../.gitbook/assets/sf-steam-sessions-blueprint-nodes.png)

> [!TIP]
> **Explore Nodes Directly in Unreal Engine:**  
> The entire organized Blueprint node graph pictured above is laid out inside the **Level Blueprint** of the included **`HowToUse`** showcase level (`/StraightForwardOnlineSessions/Levels/HowToUse`). You can open it in the editor to inspect, zoom in, and copy-paste nodes directly into your project.

---

## 📦 Included Example Content

| Asset | Description |
| :--- | :--- |
| `Levels/HowToUse` | Documentation room (panels, Docs / Contact buttons) and the node graph in its Level Blueprint. Default map of the sample project. |
| `Levels/Menu` | Main menu: host (Data Asset flow), server browser and friend sessions. **Exit** quits the game. |
| `Levels/Lobby` | Pre-match lobby with player list, Steam avatars and host-only Start Game. |
| `Levels/GameplayLevel1` / `GameplayLevel2` | Selectable gameplay maps. A floor trigger in each one changes the session to the other map. |
| `SFAssets/Overview` | Showcase room with a trigger that travels to `GameplayLevel1`. |
| `Blueprints/Data/SFSession_DataAsset` | Example `USFSteamSessionDataAsset` (lobby, levels, game modes). |
| `Blueprints/MainMenu`, `Lobby`, `Gameplay` | Game modes, player controllers and characters for each stage. `GM_Gameplay` / `GM_Lobby` contain `BeginTravelFeedback` (see [ChangeSessionLevel](api.md#changesessionlevel)). |
| `Widgets/` | `WBP_MainMenu`, `WBP_LobbyUI`, `WBP_GameplayUI` (pause menu and travel indicator), `WBP_SessionItem`, `WBP_UserList`, `WBP_UserItem`, `WBP_UserName`. |

**Demo controls:** TAB or ESC opens the pause menu in the gameplay levels (Resume / Main Menu). Quit from **Exit** in the main menu.

**Supported engine version:** Unreal Engine 5.8. **Platform:** Windows (Win64). Steam features need the Steam client running (see [Installation & Setup](installation-setup.md#packaging-checklist)).
