# SF Localization - Troubleshooting

---

### ❓ Texts show `MISSING: <ID>`
**Solution:**
The row name does not exist in any registered table, or the table has no column named after the current language code.

---

### ❓ My User Defined Struct does not work as row struct
**Solution:**
Blueprint structs store properties with generated internal names, so the language columns are not found. Use `FSFLocalizationRow` or a C++ struct.
