# SF Localization - C++ & Blueprint API

---

## 🌍 `USFLocalizationSubsystem`

- **`RegisterThematicTable(Table)`**: Adds a Data Table to the search list (searched in registration order).
- **`SetLanguage(LanguageCode)`**: Case-insensitive language code; broadcasts `OnLanguageChanged`.
- **`GetLocalizedText(TextID)`** *(FString)*: Text in the current language, or `MISSING: <TextID>`.
- **`GetCurrentLanguage()`** *(FString)*: Default `"EN"`.
- **`OnLanguageChanged`**: Fired after every language change.

---

## 🧾 `FSFLocalizationRow`

Ready-to-use row struct with `FString` columns `EN`, `ES`, `FR`, `DE`, `IT`, `PT`. Any other C++ row struct works if its properties are named after the language codes (`FString`, `FName` or `FText`).

---

## 🧩 `USFLocalizedText` (UMG)

Text Block with a **`TextID`** property. Updates on construction and on every `OnLanguageChanged`. Shows the ID itself in the designer.
