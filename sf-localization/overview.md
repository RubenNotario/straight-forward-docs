# SF Localization - Overview

**SF Localization** (`StraightForwardLocalization`) is a lightweight, data driven runtime localization system based on thematic Data Tables.

---

## 🎯 Key Features

- 🌍 **GameInstance Subsystem:** `USFLocalizationSubsystem` survives level changes.
- 🗂️ **Thematic Tables:** split texts by topic (menus, items, dialogs) and register only what you need.
- 🔤 **One Column Per Language:** `SetLanguage("ES")` reads the `ES` column of every table.
- 🧩 **SFLocalizedText Widget:** a Text Block that only needs a `TextID` and refreshes itself on language change.
- ⚡ **Cached Lookups:** reflection results are cached per row struct.

---

## 📦 Included Example Content

| Asset | Description |
| :--- | :--- |
| `Levels/HowToUse` | Demo room with EN / ES / FR buttons and a live HUD panel. |
| `Data/DT_SFDemoTexts` | Example table (`FSFLocalizationRow`). |
| `Widgets/WBP_LocalizedPanel` | Panel built with `SFLocalizedText` widgets. |
| `Blueprints/HowToUse/BP_LocalizationDemoController` | Every node used by the room. |

**Supported engine version:** Unreal Engine 5.8.
