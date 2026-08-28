# SF Steam Online Sessions - C++ & Blueprint API
 
All multiplayer functionality is exposed via `USFOSMultiplayerSessionsSubsystem` (accessible automatically in Blueprints and C++ as a **GameInstance Subsystem**).

![SF Steam Online Sessions - Blueprint Nodes Overview](../.gitbook/assets/sf-steam-sessions-blueprint-nodes.png)

---

## 📦 Data Asset: `USFSteamSessionDataAsset`

A primary data asset to centralize and configure multiplayer project settings, lobby maps, gameplay levels, and predefined game modes.

| Property | Type | Default | Description |
| :--- | :--- | :--- | :--- |
| **`ProjectID`** | `FString` | `"StraightForwardMultiplayerV1"` | Unique identifier to isolate matchmaking between different projects. |
| **`LobbyLevel`** | `TSoftObjectPtr<UWorld>` | `None` | Soft object pointer to the gathering/lobby level where sessions are created. |
| **`GameplayLevels`** | `TArray<FSFGameplayLevelEntry>` | `Empty` | List of selectable gameplay levels (with display names, thumbnails, descriptions). |
| **`GameModes`** | `TArray<FSFGameModeEntry>` | `Empty` | List of predefined game modes (e.g. `"Free For All"`, `"Co-Op"`). |
| **`ExtraCustomData`** | `TMap<FString, FString>` | `Empty` | Default key-value pairs advertised to Steam. |

### Data Asset Helper Functions (BlueprintPure)
- **`GetLobbyLevelPath()`**: Returns package path of the lobby level.
- **`GetGameplayLevelPath(Index)`**: Returns package path of the gameplay level at specified index.
- **`GetGameplayLevelNames()`**: Returns array of names for all gameplay levels (for ComboBoxes).
- **`GetGameModeNames()`**: Returns array of names for all configured game modes (for ComboBoxes).
- **`GetGameplayLevelEntry(Index, OutEntry)`**: Returns the level entry struct.

---

## 🧱 Structs & Configuration
 
### `FSFSteamSessionSettings`
Clean configuration struct for creating sessions.
 
| Property | Type | Default | Description |
| :--- | :--- | :--- | :--- |
| **`MaxPlayers`** | `int32` | `4` | Maximum number of allowed players in the session. |
| **`MapPath`** | `FString` | `""` | Optional map URL/path to launch via ServerTravel upon creation. |
| **`ProjectID`** | `FString` | `"StraightForwardMultiplayerV1"` | Unique identifier to isolate matchmaking between different projects. |
| **`CustomData`** | `TMap<FString, FString>` | `Empty` | Key-value pairs advertised to Steam (e.g. `"ServerName"`, `"GameMode"`). |

---

### `FSFSteamSearchSettings`
Configuration struct for querying Steam sessions.
 
| Property | Type | Default | Description |
| :--- | :--- | :--- | :--- |
| **`MaxSearchResults`** | `int32` | `20` | Maximum number of search results to return. |
| **`ProjectID`** | `FString` | `"StraightForwardMultiplayerV1"` | Matches only sessions created with this Project ID. |
| **`SearchFilters`** | `TMap<FString, FString>` | `Empty` | Key-value filters to match against published session `CustomData`. |

---

## 🛠️ Main Subsystem Functions

### `CreateSessionFromDataAsset`
Creates a Steam multiplayer session using the provided Data Asset configuration and travels to `LobbyLevel`.
- **`SessionConfig`** *(USFSteamSessionDataAsset\*)*: The Data Asset containing map and mode definitions.
- **`MaxPlayers`** *(int32, default=4)*: Player limit.
- **`SelectedGameMode`** *(FString, default="Default")*: Selected game mode name (automatically saved to `CustomData["GameMode"]`).
- **`SelectedGameplayLevelIndex`** *(int32, default=0)*: Selected map index from Data Asset (automatically saved to `CustomData["SelectedLevelIndex"]` and `CustomData["SelectedLevelName"]`).
- **`AdditionalCustomData`** *(TMap<FString, FString>, advanced)*: Optional runtime key-value pairs (e.g. Server Name).

### `StartMatchFromCurrentSession`
Called by the Host in the Lobby. Automatically retrieves the map selected at session creation and executes seamless `ServerTravel` (`?listen`) to transition all players to the gameplay arena.
- **`SessionConfig`** *(USFSteamSessionDataAsset\*)*

### `StartMatchFromDataAsset`
Allows the Host to dynamically switch and travel to any specific map index from the Data Asset.
- **`SessionConfig`** *(USFSteamSessionDataAsset\*)*
- **`GameplayLevelIndex`** *(int32, default=0)*

### `CreateSession`
Standard function to host a session directly without Data Assets.
- **`MaxPlayers`** *(int32, default=4)*
- **`MapPath`** *(FString, default="")*
- **`ProjectID`** *(FString, default="StraightForwardMultiplayerV1")*

### `CreateSessionWithSettings`
Creates a Steam multiplayer session using the `FSFSteamSessionSettings` struct.
- **`Settings`** *(FSFSteamSessionSettings)*: Session configuration. In Blueprints, can be split using **Split Struct Pin**.

### `FindSessions`
Standard search for available public online sessions matching the `ProjectID`.
- **`MaxSearchResults`** *(int32, default=20)*
- **`ProjectID`** *(FString, default="StraightForwardMultiplayerV1")*

### `FindSessionsWithSettings`
Searches for available public online sessions matching specific search settings and custom key-value filters.
- **`SearchSettings`** *(FSFSteamSearchSettings)*

### `FindFriendSessions`
Searches exclusively for active sessions hosted by the local player's Steam friends.

### `JoinGameSession`
Connects the local player to a selected session from search results.
- **`SessionResult`** *(FBlueprintSessionResult)*: The target session result.

### `ShowFriendInviteUI`
Opens the native Steam Overlay friend invitation modal (1-click invitation).

### `DestroySession`
Destroys the active multiplayer session and cleanly unbinds networking handles.

### `ChangeSessionLevel`
Executes server travel (`?listen`) to switch maps for the server and all connected clients.
- **`MapPath`** *(FString)*: Path to the target level.

---

## 🎨 Helper Functions (BlueprintPure)

### Active Local Session Helpers
- **`GetCurrentSessionCustomData(Key)`**: Retrieves a metadata value (`"SelectedLevelName"`, `"GameMode"`, etc.) from the active session. Works for both Host and connected Clients in the Lobby.
- **`GetAllCurrentSessionCustomData()`**: Returns all metadata key-value pairs of the active session.

### Search Result Helpers (for Server Browsers)
- **`GetSessionHostName(FBlueprintSessionResult)`**: Returns the host player's Steam username.
- **`GetSessionPing(FBlueprintSessionResult)`**: Returns connection ping in ms.
- **`GetSessionPlayerCount(FBlueprintSessionResult, OutCurrent, OutMax)`**: Returns active and maximum player capacities.
- **`GetSessionCustomData(FBlueprintSessionResult, Key)`**: Retrieves a specific custom string published by the host in `CustomData`.
- **`GetAllSessionCustomData(FBlueprintSessionResult)`**: Returns the entire `TMap<FString, FString>` of custom metadata for the session.

### Steam Profile Helpers
- **`GetSteamAvatar(APlayerState* PlayerState)`**: Returns a `UTexture2D*` containing the player's Steam profile picture, cached and protected against Garbage Collection.

---

## 📢 Assignable Delegates (Async Event Callbacks)

Subscribe to these event dispatchers in your Blueprints (using **Assign** or **Bind Event to...**) to respond to asynchronous Steam networking operations:

| Delegate / Event | Parameters | When it Fires & Recommended Usage |
| :--- | :--- | :--- |
| **`OnCreateSessionCompleteEvent`** | `bool bWasSuccessful` | Fires after `CreateSession` or `CreateSessionFromDataAsset` completes. If true, the session is active and listening; if false, handle the error (e.g. notify player). |
| **`OnFindSessionsCompleteEvent`** | `bool bWasSuccessful`, `TArray<FBlueprintSessionResult> Results` | Fires after a public session search finishes. Pass `Results` to populate your Server Browser list widget. |
| **`OnFindFriendSessionsCompleteEvent`** | `bool bWasSuccessful`, `TArray<FBlueprintSessionResult> Results` | Fires after querying active lobbies hosted by Steam Friends. |
| **`OnJoinSessionCompleteEvent`** | `bool bWasSuccessful` | Fires after attempting to connect via `JoinGameSession`. On success, the client automatically executes ClientTravel to the host. |
| **`OnDestroySessionCompleteEvent`** | `bool bWasSuccessful` | Fires after `DestroySession` completes. Ideal place to call `Open Level` to return the player cleanly to the Main Menu. |

---

## 💡 Testing & PIE Guidelines

> [!IMPORTANT]
> **Steam Testing Requirement:**  
> Steam Online Subsystem features (Steam Overlay, Friend Invites, Avatars, and Matchmaking) require:
> 1. The official desktop **Steam Client** must be running and logged in on your machine.
> 2. You must test via **Play > Standalone Game** (or in packaged builds). Standard PIE (Selected Viewport) runs in a non-Steam emulation environment.
> 3. If testing multiplayer across 2 PCs using default `AppID 480` (Spacewar), both Steam accounts must be set to the **same Download Region** in Steam Settings (`Settings > Downloads > Download Region`).


