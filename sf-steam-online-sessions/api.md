# SF Steam Online Sessions - C++ & Blueprint API
 
All multiplayer functionality is exposed via `USFSSMultiplayerSessionsSubsystem` (accessible automatically in Blueprints and C++ as a **GameInstance Subsystem**).

---

## 🧱 Structs & Configuration
 
### `FSFSteamSessionSettings`
Configuration struct for creating sessions. All parameters contain sensible defaults for 1-click usage, while allowing custom metadata.
 
| Property | Type | Default | Description |
| :--- | :--- | :--- | :--- |
| **`MaxPlayers`** | `int32` | `4` | Maximum number of allowed players in the session. |
| **`MatchType`** | `FString` | `"FreeForAll"` | Match type descriptor (e.g. `"FreeForAll"`, `"TDM"`). |
| **`MapPath`** | `FString` | `""` | Optional map URL/path to launch via ServerTravel upon creation. |
| **`ProjectID`** | `FString` | `"SFSteamSessionsV1"` | Unique identifier to isolate matchmaking between different projects. |
| **`bIsLAN`** | `bool` | `false` | If true, hosts as a LAN match instead of Steam. |
| **`bAllowJoinInProgress`**| `bool` | `true` | Allows players to join mid-match. |
| **`bAllowJoinViaPresence`**| `bool` | `true` | Enables joining via Steam Friends list and presence. |
| **`CustomData`** | `TMap<FString, FString>` | `Empty` | Key-value pairs advertised to Steam (e.g. `"MapDisplayName"`, `"GameMode"`, `"ServerName"`). |

---

### `FSFSteamSearchSettings`
Configuration struct for querying Steam sessions.
 
| Property | Type | Default | Description |
| :--- | :--- | :--- | :--- |
| **`MaxSearchResults`** | `int32` | `20` | Maximum number of search results to return. |
| **`ProjectID`** | `FString` | `"SFSteamSessionsV1"` | Matches only sessions created with this Project ID. |
| **`SearchFilters`** | `TMap<FString, FString>` | `Empty` | Key-value filters to match against published session `CustomData`. |

---

## 🛠️ Main Subsystem Functions

### `CreateSession`
Creates a Steam multiplayer session using the provided settings struct.
- **`Settings`** *(FSFSteamSessionSettings)*: Session configuration. In Blueprints, can be split using **Split Struct Pin**.

### `CreateSimpleSession`
Convenience 1-click function to host a standard session without manipulating structs.
- **`MaxPlayers`** *(int32, default=4)*
- **`MatchType`** *(FString, default="FreeForAll")*
- **`MapPath`** *(FString, default="")*
- **`ProjectID`** *(FString, default="SFSteamSessionsV1")*

### `FindSessions`
Searches for available public online sessions matching the specified search settings and optional filters.
- **`SearchSettings`** *(FSFSteamSearchSettings)*

### `FindSimpleSessions`
Convenience function to search for public sessions without extra filters.
- **`MaxSearchResults`** *(int32, default=20)*
- **`ProjectID`** *(FString, default="SFSteamSessionsV1")*

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

- **`GetSessionHostName(FBlueprintSessionResult)`**: Returns the host player's Steam username.
- **`GetSessionPing(FBlueprintSessionResult)`**: Returns connection ping in ms.
- **`GetSessionPlayerCount(FBlueprintSessionResult, OutCurrent, OutMax)`**: Returns active and maximum player capacities.
- **`GetSessionCustomData(FBlueprintSessionResult, Key)`**: Retrieves a specific custom string published by the host in `CustomData`.
- **`GetAllSessionCustomData(FBlueprintSessionResult)`**: Returns the entire `TMap<FString, FString>` of custom metadata for the session.
- **`GetSteamAvatar(APlayerState* PlayerState)`**: Returns a `UTexture2D*` containing the player's Steam profile picture, protected against Garbage Collection.

---

## 📢 Assignable Delegates (Events)

- `OnCreateSessionCompleteEvent(bool bWasSuccessful)`
- `OnFindSessionsCompleteEvent(bool bWasSuccessful, TArray<FBlueprintSessionResult> Results)`
- `OnFindFriendSessionsCompleteEvent(bool bWasSuccessful, TArray<FBlueprintSessionResult> Results)`
- `OnJoinSessionCompleteEvent(bool bWasSuccessful)`
- `OnDestroySessionCompleteEvent(bool bWasSuccessful)`
