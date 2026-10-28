# SF Upscaler Toolkit - Quickstart Example

A complete graphics settings screen in a few minutes.

---

1. Add the ini line from **Installation & Setup**.
2. Duplicate `Widgets/UI/WBP_SFDemoMenu` and `WBP_SFOptionRow` into your project and restyle them (or create your own children of `SFGraphicsSettingsWidget` / `SFOptionRowWidget`).
3. Open the duplicated menu and set **Row Class** to your row widget.
4. Create the menu from your pause menu or main menu (`Create Widget` + `Add to Viewport`) and show the mouse cursor.
5. Done: every row applies and saves its setting. Bind `On Setting Changed` if your UI needs to react.

> 💡 Prefer your own UI? Call `Set And Apply Upscaler Mode`, `Get Supported Modes` and the rest of `USFUpscalerLibrary` directly.

> 💡 Open `Levels/HowToUse` in the plugin content and press Play: TAB shows / hides the menu. Use Standalone to test resolution, window mode and frame generation.
