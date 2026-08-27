# SF Steam Online Sessions - Troubleshooting

Common issues and solutions when working with Unreal Engine Online Subsystem & Steam.

---

### ❓ Steam Overlay is not appearing in Play in Editor (PIE)
**Solution:**
- Steam Overlay requires a standalone build or launching via **Play > Standalone Game**.
- Ensure the official desktop Steam client is running on your machine before launching the project.

---

### ❓ `CreateSession` or `JoinGameSession` fails silently
**Solution:**
- Always ensure any previous session is cleanly destroyed before creating or joining a new one. Call `DestroySession()` and wait for `OnDestroySessionCompleteEvent` before initiating a new session.
- Ensure the GameMode has `bUseSeamlessTravel = true` and that maps specify `?listen` when hosting.

---

### ❓ Sessions cannot be found between two different PCs
**Solution:**
1. If using default `SteamDevAppId=480` (Spacewar), both players **must be in the same download region** in Steam Settings (`Settings > Downloads > Download Region`).
2. Verify both builds share the exact same `ProjectID` parameter in `FSFSteamSessionSettings` and `FSFSteamSearchSettings`.
3. Check Windows Firewall to ensure UDP port 27015 / P2P traffic is not blocked.

---

### ❓ `GetSteamAvatar` returns null
**Solution:**
- Ensure the target `PlayerState` has connected via Steam (has a valid `UniqueNetId`).
- Avatars are fetched asynchronously from Steam API servers; the subsystem automatically caches loaded textures to protect against Garbage Collector destruction.
