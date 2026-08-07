# SF Steam Online Sessions - C++ & Blueprint API

All multiplayer functionality is exposed via `USFOSMultiplayerSessionsSubsystem` (accessible automatically as a **GameInstance Subsystem**).

---

## 🛠️ Main Subsystem Functions

### `CreateSession`
Creates a multiplayer session with custom player limits and match settings.
- **`NumPublicConnections`** *(int32)*: Maximum allowed players.
- **`MatchType`** *(FString)*: Custom match type filter (e.g. `"FreeForAll"`).
- **`MapName`** *(FString)*: Map path to launch upon session creation.
- **`ProjectID`** *(FString)*: Unique project key filter (Default: `"StraightForwardMultiplayerV1"`).

### `FindSessions`
Searches for available public online sessions.
- **`MaxSearchResults`** *(int32)*: Maximum results returned.
- **`ProjectID`** *(FString)*: Matching project key filter.

### `FindFriendSessions`
Searches specifically for sessions hosted by friends on Steam.

### `JoinGameSession`
Joins a selected session from search results.
- **`SessionResult`** *(FBlueprintSessionResult)*: The target session result struct.

### `ShowFriendInviteUI`
Opens the native Steam Overlay friend invitation dialog.

### `DestroySession`
Destroys the active multiplayer session and cleans up settings.

### `ChangeSessionLevel`
Executes server travel to switch to a new level for all connected players.
- **`MapPath`** *(FString)*: Path to target level.

---

## 🎨 Helper Functions

- **`GetSteamAvatar(APlayerState* PlayerState)`**: Returns a `UTexture2D*` containing the player's Steam profile picture.
- **`GetSessionHostName(FBlueprintSessionResult)`**: Returns host player's name.
- **`GetSessionPing(FBlueprintSessionResult)`**: Returns connection ping in ms.
- **`GetSessionPlayerCount(FBlueprintSessionResult, OutCurrent, OutMax)`**: Returns active and total player capacities.

---

## 📢 Assignable Delegates (Events)

- `OnCreateSessionCompleteEvent(bool bWasSuccessful)`
- `OnFindSessionsCompleteEvent(bool bWasSuccessful, TArray<FBlueprintSessionResult> Results)`
- `OnFindFriendSessionsCompleteEvent(bool bWasSuccessful, TArray<FBlueprintSessionResult> Results)`
- `OnJoinSessionCompleteEvent(bool bWasSuccessful)`
- `OnDestroySessionCompleteEvent(bool bWasSuccessful)`
