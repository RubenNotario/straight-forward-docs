# SF Loading Screen - Troubleshooting

---

### ❓ Nothing appears in Play In Editor
**Behavior Explanation:**
The engine Movie Player is disabled in PIE. Use **Standalone Game** or a packaged build.

---

### ❓ Movies do not play in the packaged build
**Solution:**
Add `Content/Movies` to **Project Settings ➔ Packaging ➔ Additional Non-Asset Directories to Package**.
