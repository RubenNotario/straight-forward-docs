# SF Steam Online Sessions - Quickstart Guide

This guide demonstrates both the **1-Click Simple Friends Workflow** and the **Custom Metadata & Matchmaking Workflow**.

---

## ⚡ Workflow 1: Frictionless Friends Lobby (1-Click)

For casual/co-op games where players only want to host and invite Steam friends:

### 1. Hosting & Inviting Friends
1. In your Main Menu UI Blueprint, get the subsystem:
   - `Get Game Instance` ➔ `Get SFSSMultiplayerSessionsSubsystem`.
2. Call `CreateSimpleSession(MaxPlayers = 4, MatchType = "Coop", MapPath = "/Game/Maps/LobbyMap")`.
3. Bind to `OnCreateSessionCompleteEvent`.
4. When it succeeds, call `ShowFriendInviteUI()` to open the native Steam Overlay invite dialog immediately!

### 2. Joining Friends
1. Call `FindFriendSessions()`.
2. Bind to `OnFindFriendSessionsCompleteEvent`.
3. Display the friend lobbies in a list. When the player clicks one, call `JoinGameSession(SelectedResult)`.

---

## 🚀 Workflow 2: Custom Metadata & Server Browser

For games requiring custom maps, game modes, and search filters:

### 1. Hosting with Custom Data
1. In Blueprint, drag out `CreateSession` from `SFSSMultiplayerSessionsSubsystem`.
2. Right-click the `Settings` pin and choose **Split Struct Pin**.
3. Set `MaxPlayers`, `MapPath`, etc.
4. In the `CustomData` map pin, add your custom parameters:
   - `"MapDisplayName"` ➔ `"Glacial Rift"`
   - `"GameMode"` ➔ `"Team Deathmatch"`
   - `"ServerName"` ➔ `"Ruben's Server"`

### 2. Searching & Filtering
1. Call `FindSessions` using `FSFSteamSearchSettings`.
2. (Optional) Add pairs to `SearchFilters` (e.g. `"GameMode"` ➔ `"Team Deathmatch"`).
3. On `OnFindSessionsCompleteEvent`, populate your server browser.
4. In each server row widget, use the helper nodes:
   - `GetSessionHostName(Result)` ➔ Display host name.
   - `GetSessionPing(Result)` ➔ Display latency.
   - `GetSessionPlayerCount(Result)` ➔ Display player count (`"3/4"`).
   - `GetSessionCustomData(Result, "MapDisplayName")` ➔ Display `"Glacial Rift"`.
   - `GetSessionCustomData(Result, "GameMode")` ➔ Display `"Team Deathmatch"`.
5. Call `JoinGameSession(Result)` when the player clicks **Join**.
