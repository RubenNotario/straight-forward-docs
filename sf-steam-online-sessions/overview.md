# SF Steam Online Sessions - Overview

**Straight Forward Steam Sessions** is a lightweight, production-ready, and unopinionated Unreal Engine plugin designed to wrap Unreal's Online Subsystem (OSS) and Steam Online Subsystem into a clean, easy-to-use GameInstance Subsystem (`USFSSMultiplayerSessionsSubsystem`).

Built under the **Straight Forward Solid Systems** philosophy, it provides decoupled, modular building blocks: developers can create 1-click frictionless friend lobbies or build advanced server browsers with arbitrary custom metadata without touching C++.

---

## 🎯 Key Features

- 🌐 **Unopinionated & Flexible Hosting:** Host simple 1-click lobbies or pass custom metadata dictionaries (`CustomData`) such as map names, game modes, and custom modifiers.
- 🔍 **Custom Matchmaking & Search Filters:** Filter public sessions using `SearchFilters` or query global Steam lobbies with zero boilerplate.
- 👥 **Steam Friends & Overlay Invites:** Search exclusively for Steam friend games and open the native Steam Overlay friend invitation dialog with 1 click.
- 🖼️ **Steam Player Avatars (GC-Protected):** Fetch player Steam profile pictures directly into `UTexture2D` widgets for custom lobby menus, cached and safe against Garbage Collection.
- 🔄 **Async Event Delegates:** Dynamic multicast delegates for creation, discovery, friend search, joining, and destruction of sessions.
- ✈️ **Clean Server Travel:** Built-in helper to execute seamless server travel with `?listen` for all connected players.
- 🛡️ **Zero Bloat & Production Ready:** Cero unnecessary tick, fully event-driven, leak-free RAII memory management, and zero forced workflow restrictions.
