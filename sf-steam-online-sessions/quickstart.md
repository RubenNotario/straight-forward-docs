# SF Steam Online Sessions - Quickstart Example

Here is a step-by-step example of how to host and join a session in Blueprints.

---

## 1. Hosting a Session

1. In your Main Menu UI Blueprint, get the **SFOSMultiplayer Sessions Subsystem**:
   - `Get Game Instance` ➔ `Get SFOSMultiplayerSessionsSubsystem`.
2. Bind to `OnCreateSessionCompleteEvent`.
3. Call `CreateSession`:
   - `NumPublicConnections`: `4`
   - `MatchType`: `"FreeForAll"`
   - `MapName`: `"/Game/Maps/LobbyMap"`
4. When `OnCreateSessionCompleteEvent` fires with `bWasSuccessful = true`, open the lobby level using `Open Level (by Name)` or server travel.

---

## 2. Searching & Joining a Session

1. Call `FindSessions(100, "StraightForwardMultiplayerV1")`.
2. Bind to `OnFindSessionsCompleteEvent`.
3. Populate your UMG ScrollBox / List View with the returned `Results` array.
4. When the player clicks a session item, call `JoinGameSession` passing the selected `FBlueprintSessionResult`.
5. On `OnJoinSessionCompleteEvent` success, Unreal will automatically connect the client controller to the host IP!
