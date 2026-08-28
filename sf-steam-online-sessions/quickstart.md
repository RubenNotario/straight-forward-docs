# SF Steam Online Sessions - Quickstart Guide

This guide demonstrates the **Data Asset & Full Lobby Flow** (Recommended), the **1-Click Friends Workflow**, and the **Custom Server Browser Workflow**.

---

## 📦 Workflow 1: Data Asset & Full Lobby Flow (Recommended)

The most organized and extensible workflow for production games with multiple maps, game modes, and pre-match lobbies.

### 1. Create your Data Asset
1. In Content Browser: **Right Click** ➔ **Miscellaneous** ➔ **Data Asset** ➔ select **`SFSteamSessionDataAsset`**.
2. Name it `DA_SteamSessionConfig`.
3. In its Details panel, configure:
   - **Project ID**: Your game's unique ID (e.g. `"MyGameV1"`).
   - **Lobby Level**: Drag-and-drop your pre-game gathering map (e.g. `LobbyLevel`).
   - **Gameplay Levels**: Add your playable maps with display names and thumbnails.
   - **Game Modes**: Add mode names (e.g. `"Cooperative"`, `"Deathmatch"`).

### 2. Host the Session (Main Menu)
1. In your Main Menu widget, call `Get SFOSMultiplayerSessionsSubsystem` ➔ `CreateSessionFromDataAsset`.
2. Connect your `DA_SteamSessionConfig`, `MaxPlayers` (from UI), `SelectedGameMode` (from ComboBox), and `SelectedGameplayLevelIndex` (from ComboBox).
3. The subsystem automatically registers metadata and executes `ServerTravel` to your `LobbyLevel`.

### 3. Display Info & Start Game (Lobby)
1. **Show Match Info (Host & Clients):**
   - Call `GetCurrentSessionCustomData("SelectedLevelName")` to display the chosen map name.
   - Call `GetCurrentSessionCustomData("GameMode")` to display the selected game mode.
2. **Start Match (Host Only):**
   - On the Host's "Start Game" button, call `Get SFOSMultiplayerSessionsSubsystem` ➔ `StartMatchFromCurrentSession(DA_SteamSessionConfig)`.
   - All players in the lobby will seamlessly travel together to the gameplay map.

### 4. Leaving the Match & Clean Teardown
1. On the "Exit Session" button (in Lobby or Pause Menu), call `Get SFOSMultiplayerSessionsSubsystem` ➔ `DestroySession`.
2. Bind to `OnDestroySessionCompleteEvent` and call `Open Level` to return the player safely back to your `MenuLevel`.

---

## ⚡ Workflow 2: Frictionless Friends Lobby (1-Click)

For casual/co-op games where players only want to host and invite Steam friends:

### 1. Hosting & Inviting Friends
1. In your Main Menu UI Blueprint, get the subsystem:
   - `Get Game Instance` ➔ `Get SFOSMultiplayerSessionsSubsystem`.
2. Call `CreateSession(MaxPlayers = 4, MapPath = "/Game/Maps/LobbyMap")`.
3. When the session is created, call `ShowFriendInviteUI()` to open the native Steam Overlay invite dialog immediately!

### 2. Joining Friends
1. Call `FindFriendSessions()`.
2. Bind to `OnFindFriendSessionsCompleteEvent`.
3. Display the friend lobbies in a list. When the player clicks one, call `JoinGameSession(SelectedResult)`.

---

## 🚀 Workflow 3: Custom Metadata & Server Browser

For games requiring custom search filters and arbitrary metadata:

### 1. Hosting with Custom Data
1. In Blueprint, drag out `CreateSessionWithSettings` from `SFOSMultiplayerSessionsSubsystem`.
2. Right-click the `Settings` pin and choose **Split Struct Pin**.
3. In the `CustomData` map pin, add your custom parameters:
   - `"ServerName"` ➔ `"Ruben's Arena"`
   - `"Difficulty"` ➔ `"Hardcore"`

### 2. Searching & Filtering
1. Call `FindSessionsWithSettings` using `FSFSteamSearchSettings`.
2. Add filters to `SearchFilters` (e.g. `"Difficulty"` ➔ `"Hardcore"`).
3. On `OnFindSessionsCompleteEvent`, populate your server browser using helper nodes:
   - `GetSessionHostName(Result)` ➔ Display host name.
   - `GetSessionPing(Result)` ➔ Display latency.
   - `GetSessionPlayerCount(Result)` ➔ Display player count (`"3/4"`).
   - `GetSessionCustomData(Result, "ServerName")` ➔ Display server name.
4. Call `JoinGameSession(Result)` when the player clicks **Join**.

