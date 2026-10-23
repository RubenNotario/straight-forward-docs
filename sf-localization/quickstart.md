# SF Localization - Quickstart Example

---

1. Create `DT_Menu` (row struct `SFLocalizationRow`):
   | Row | EN | ES |
   | :--- | :--- | :--- |
   | `Menu_Play` | Play | Jugar |
   | `Menu_Quit` | Quit | Salir |
2. Game Instance **Init**: `Register Thematic Table (DT_Menu)` ➔ `Set Language (SavedLanguage)`.
3. Main menu widget: two **SF Localized Text** with Text ID `Menu_Play` and `Menu_Quit`.
4. Language buttons: `Set Language ("ES")` - every SF Localized Text updates instantly.

> 💡 Open `Levels/HowToUse` in the plugin content to try it in play mode.
