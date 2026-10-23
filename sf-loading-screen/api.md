# SF Loading Screen - C++ & Blueprint API

---

## 📚 Blueprint Library (`USFLoadingScreenBPLibrary`)

- **`SetNextLoadingTip(TipText)`**: Tip used by the next loading screen only.
- **`PlayLoadingScreen()`**: Shows the loading screen without a map change.
- **`StopLoadingScreen()`**: Hides it.
- **`IsLoadingScreenActive()`** *(bool)*.

---

## ⚙️ Project Settings (`USFLoadingScreenSettings`)

| Setting | Default | Description |
| :--- | :--- | :--- |
| `bEnableLoadingScreen` | `true` | Master switch. |
| `MinimumLoadingScreenDisplayTime` | `2 s` | Minimum visible time. |
| `bAutoCompleteWhenLoadingCompletes` | `true` | Hide automatically after loading (respecting the minimum time). |
| `DefaultLoadingTitle` | - | Title text. |
| `LoadingTips` | 3 sample tips | Random tip per transition. |
| `BackgroundImages` | - | One is chosen per transition. |
| `bShowThrobber` | `true` | Animated circular throbber. |
| `MoviePaths` / `bMoviesAreSkippable` | - / `false` | Movies in `Content/Movies` (no extension). |
