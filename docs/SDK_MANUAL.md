<p align="center">
<!-- Readme Links -->
<a href="https://github.com/BlugDeg/SCOverlay-Updates/blob/main/docs/README.md"><img src="https://img.shields.io/badge/Readme-555?style=for-the-badge" alt="Readme"></a><!--
--><a href="https://github.com/BlugDeg/SCOverlay-Updates/blob/main/docs/README.md"><img src="https://img.shields.io/badge/EN-555?style=for-the-badge" alt="English"></a><!--
--><a href="https://github.com/BlugDeg/SCOverlay-Updates/blob/main/docs/README.de.md"><img src="https://img.shields.io/badge/DE-555?style=for-the-badge" alt="Deutsch"></a>
&nbsp;&nbsp;|&nbsp;&nbsp;
<!-- Manual Links -->
<a href="https://github.com/BlugDeg/SCOverlay-Updates/blob/main/docs/MANUAL.md"><img src="https://img.shields.io/badge/Manual-555?style=for-the-badge" alt="Manual"></a><!--
--><a href="https://github.com/BlugDeg/SCOverlay-Updates/blob/main/docs/MANUAL.md"><img src="https://img.shields.io/badge/EN-555?style=for-the-badge" alt="English"></a><!--
--><a href="https://github.com/BlugDeg/SCOverlay-Updates/blob/main/docs/MANUAL.de.md"><img src="https://img.shields.io/badge/DE-555?style=for-the-badge" alt="Deutsch"></a>
&nbsp;&nbsp;|&nbsp;&nbsp;
<!-- Developer/SDK Links -->
<a href="https://github.com/BlugDeg/SCOverlay-Updates/blob/main/docs/SDK_MANUAL.md"><img src="https://img.shields.io/badge/Developer-007bff?style=for-the-badge" alt="Developer"></a><!--
--><a href="https://github.com/BlugDeg/SCOverlay-Updates/blob/main/docs/SDK_MANUAL.md"><img src="https://img.shields.io/badge/EN-ff6f00?style=for-the-badge" alt="English"></a><!--
--><a href="https://github.com/BlugDeg/SCOverlay-Updates/blob/main/docs/SDK_MANUAL.de.md"><img src="https://img.shields.io/badge/DE-555?style=for-the-badge" alt="Deutsch"></a>
</p>

<h1 align="center">SCOverlay Addon SDK (API 0.0.5.0)</h1>

<p align="center">
  <strong>The Ultimate Developer's Guide to the SCOverlay Platform.</strong>
  <br>
  <em>Updated for the latest API Architecture & Thread Safety.</em>
</p>

<!-- Badges -->
<p align="center">
  <a href="https://github.com/BlugDeg/SCOverlay-Updates/blob/main/LICENSE"><img src="https://img.shields.io/github/license/BlugDeg/SCOverlay-Updates" alt="License"></a>
  <a href="https://scoverlay.it-en.ch/donate"><img src="https://img.shields.io/badge/Donate-support%20the%20project-orange" alt="Donate"></a>
  <a href="https://github.com/BlugDeg/SCOverlay-Updates/issues"><img src="https://img.shields.io/badge/Issue%20Council-Active-brightgreen" alt="Status"></a>
</p>

## Table of Contents

1.  [Chapter 1: Vision & Architecture](#chapter-1-vision--architecture)
2.  [Chapter 2: Quickstart - Your First Add-on](#chapter-2-quickstart---your-first-add-on)
3.  [Chapter 3: The `IAddon` Interface (The Contract)](#chapter-3-the-iaddon-interface-the-contract)
4.  [Chapter 4: The API Reference (All Methods & Parameters)](#chapter-4-the-api-reference-all-methods--parameters) **(IMPORTANT!)**
5.  [Chapter 5: Hotkey System & Exclusive Control](#chapter-5-hotkey-system--exclusive-control)
6.  [Chapter 6: UI & Settings (Modern vs. Legacy)](#chapter-6-ui--settings-modern-vs-legacy)
7.  [Chapter 7: Best Practices & Thread Safety](#chapter-7-best-practices--thread-safety)
8.  [Chapter 8: API additions since 0.0.4.0](#chapter-8-api-additions-since-0040)
9.  [Chapter 9: Getting into the Gallery](#chapter-9-getting-into-the-gallery)

---

## Chapter 1: Vision & Architecture

SCOverlay is a modular host. The core only manages the window, input hooks (RawInput), and system services. The real magic comes from YOU, the add-on developers.

*   **Framework:** .NET 8.0 (Windows Desktop / WinForms).
*   **Isolation:** Each add-on is its own `.dll`.
*   **Safety:** The `PerformanceWatchdog` monitors your add-on. If your `Draw` method takes too long and impacts game FPS, your add-on is automatically ejected at runtime.

---

## Chapter 2: Quickstart - Your First Add-on

### Prerequisites
*   Visual Studio 2022 (Workload: .NET Desktop Development)
*   .NET 8 SDK

### 1. Create Project
Create a **Class Library** for **C#**.

### 2. The `.csproj` File (Automation)
We configure the project to reference the API but **not** compile it into the output folder (since SCOverlay already has the API). We also automatically copy the finished add-on to your `%AppData%` folder for testing.

Replace your `.csproj` content with this:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>net8.0-windows</TargetFramework>
    <UseWindowsForms>true</UseWindowsForms>
    <Nullable>enable</Nullable>
    <Version>1.0.0</Version>
  </PropertyGroup>

  <ItemGroup>
    <!-- 
      Reference the API DLL. 
      Download it from the repo or take it from your SCOverlay install folder.
    -->
    <Reference Include="SCOverlay.API">
      <HintPath>C:\Path\To\Your\SCOverlay.API.dll</HintPath>
      <!-- IMPORTANT: Private=false prevents version conflicts! -->
      <Private>false</Private>
    </Reference>
  </ItemGroup>

  <!-- Auto-Deploy to AppData folder for testing -->
  <Target Name="CopyToAppData" AfterTargets="Build">
    <PropertyGroup>
      <AddonDir>$(AppData)\SCOverlay\addons\$(ProjectName)</AddonDir>
    </PropertyGroup>
    <MakeDir Directories="$(AddonDir)" />
    <Copy SourceFiles="$(TargetDir)$(ProjectName).dll" DestinationFolder="$(AddonDir)" />
    <Copy SourceFiles="$(TargetDir)$(ProjectName).pdb" DestinationFolder="$(AddonDir)" Condition="Exists('$(TargetDir)$(ProjectName).pdb')" />
  </Target>

</Project>
```

### 3. The Code (`MyAddon.cs`)

```csharp
using SCOverlay.API;
using System.Collections.Generic;
using System.Drawing;
using System.Windows.Forms;

namespace MyFirstAddon
{
    [Addon] // Marks this class as the entry point
    public class MyAddon : IAddon
    {
        private IAddonHost? _host;

        public string Name => "My First Addon";
        public string Author => "Your Name";
        public string Version => "1.0.0";

        public void Initialize(IAddonHost host)
        {
            _host = host;
            _host.LogInfo("Addon initialized!");
        }

        public IEnumerable<AddonButton> GetMainMenuButtons()
        {
            yield return new AddonButton(
                id: "btn_hello",
                getLabel: () => "Hello World",
                onClick: () => {
                    // Shows a pop-up bottom right (NOT HUD Overlay!)
                    _host?.Window.ShowToast(
                        "This is a message", 
                        "Title", 
                        NotificationLevel.Success
                    );
                }
            );
        }

        // Mandatory Methods (can be empty)
        public void Shutdown() { }
        public void Draw(Graphics g, Rectangle bounds) { }
        public void OnOverlayVisibilityChanged(bool isVisible) { }
        public void OnExclusiveHotkey() { }
        public IEnumerable<AddonControl> GetSettingsControls() => [];
        public UserControl? GetSettingsControl(IAddonHost host) => null;
        
        // Localization (English, German Tuple)
        public IDictionary<string, (string en, string de)> GetLocalizations() 
            => new Dictionary<string, (string, string)>();
    }
}
```

---

## Chapter 3: The `IAddon` Interface (The Contract)

Every add-on must implement this interface.

| Method / Property | Return Type | Description |
| :--- | :--- | :--- |
| `Name`, `Author`, `Version` | `string` | Metadata for display in settings. |
| `Initialize(host)` | `void` | **Most important method.** You receive the `IAddonHost` here. Store it in a variable! You can also register events or start background tasks here. |
| `GetMainMenuButtons()` | `IEnumerable<AddonButton>` | Returns buttons displayed in the SCOverlay main menu. |
| `GetSettingsControl(host)` | `UserControl?` | (Modern) Returns a complete WinForms `UserControl` displayed in settings. Allows complex UIs. |
| `GetSettingsControls()` | `IEnumerable<AddonControl>` | (Legacy) Deprecated method for simple list settings. Prefer `GetSettingsControl`. |
| `Draw(g, bounds)` | `void` | Called when the overlay is drawn. **Warning:** Slow code here slows down the game! Use this only for overlays that must *always* be visible (e.g., crosshair). |
| `OnOverlayVisibilityChanged(visible)` | `void` | Fired when the user opens or closes the overlay menu. |
| `OnExclusiveHotkey()` | `void` | Called when you have taken over the main hotkey via `RequestExclusiveHotkeyControl` and the user presses it. |
| `GetLocalizations()` | `IDictionary` | Returns a dictionary. Key = ID. Value = Tuple `(string en, string de)`. |
| `Shutdown()` | `void` | Cleanup. Stop timers, close windows, and release resources. |

---

## Chapter 4: The API Reference (All Methods & Parameters)

This is the heart of the documentation. Here you find all functions provided by the `IAddonHost`.

### 4.1 The Host (`IAddonHost`)

The host is your control center.

| Method | Parameters | Description |
| :--- | :--- | :--- |
| `LogInfo` / `LogError` | `string message` | Writes to `debug.log` and the Developer Console (`Ctrl+Shift+D`). |
| `T` | `string key` | Translates a text key based on selected language (En/De). |
| `RequestExclusiveHotkeyControl` | `IAddon addon` | Tries to claim the global SCOverlay hotkey (e.g., F10) for your addon. Returns `true` if successful. |
| `ReleaseExclusiveHotkeyControl` | `IAddon addon` | Releases the hotkey again. **Must** be called when closing your addon window! |
| `BlockGameInput` | `bool block` | `true` = Mouse/Keyboard go to the overlay (game stopped). `false` = Input goes to game. |
| `TakeMenuControl` | `IAddon, Action onBack` | Temporarily replaces the main menu with your addon menu. |
| `HideMenu` | - | Closes the overlay menu completely. |
| `RequestHighPerformanceMode` | `IAddon, string reason` | Asks the Performance Watchdog to look away momentarily (e.g., loading large data). |
| `GetSetting` / `SetSetting` | `key, value` | Persistently saves simple strings in `settings.json`. Use a prefix (e.g., `MyAddon_Volume`). |
| `TakeScreenshotAsync` | `string? deviceName` | Takes a screenshot. Optionally from a specific monitor. Returns an `Image`. |

### 4.2 The Window System (`IAddonHost.Window`)

This is where most errors ("Toasted User") happened previously. Please distinguish carefully!

| Method | Signature | Description & Usage |
| :--- | :--- | :--- |
| **`ShowToast`** | `(string msg, string title, NotificationLevel level, int durationSeconds)` | **The Pop-up bottom right.**<br>• `level`: `Info`, `Success` (Green), `Warning` (Yellow), `Error` (Red).<br>• Use this for feedback ("Save successful", "Login failed"). |
| **`ShowRainbowToast`** | `(string msg, string title, int durationSeconds)` | A toast with animated rainbow border. For special "High Score" moments or rare events. |
| **`ShowNotification`** | `(CustomNotificationOptions options)` | **NOT A POP-UP!** This is a HUD element.<br>Displays text large and centered (or other position) *directly on the screen*.<br>• Use this for in-game warnings ("Ammo empty!", "Timer expired"). |
| **`CreateStandardWindow`** | `(string title) -> Form` | Creates an empty form in SCOverlay design (Dark, Borderless).<br>• **Perfect for:** Custom GUIs, Calculators, Browsers, etc.<br>• Add standard WinForms Controls (`Button`, `Label`) to this form. |
| **`CreateThemedWindow`** | `(string title) -> Form` | Similar to StandardWindow but "bare". Intended more for custom drawing (GDI+). `CreateStandardWindow` is usually the better choice. |

### 4.3 The Sound Service (`IAddonHost.Sound`)

| Method | Parameters | Description |
| :--- | :--- | :--- |
| `PlayFile` | `string path, float volume` | Plays an `.mp3` or `.wav` file.<br>• `path`: Can be absolute or relative to SCOverlay folder.<br>• `volume`: 0.0 to 1.0. |

---

## Chapter 5: Hotkey System & Exclusive Control

Want your add-on to open when the user presses the SCOverlay hotkey (instead of the main menu)? Here's how:

```csharp
// 1. Request
if (_host.RequestExclusiveHotkeyControl(this)) 
{
    _host.HideMenu(); // Hide Main Menu
    OpenMyWindow(); // Show your window
}

// 2. React (in your IAddon class)
public void OnExclusiveHotkey()
{
    // Called when user presses hotkey WHILE you have control
    if (MyWindow.Visible) MyWindow.Hide();
    else MyWindow.Show();
}

// 3. Release (IMPORTANT!)
// When the user explicitly closes your window (X Button):
_host.ReleaseExclusiveHotkeyControl(this);
```

---

## Chapter 6: UI & Settings (Modern vs. Legacy)

### The Modern Method: `UserControl`
Create a new "User Control (Windows Forms)" in Visual Studio. Design it with the Designer (Buttons, Checkboxes, etc.).

In your `IAddon` class:
```csharp
public UserControl GetSettingsControl(IAddonHost host)
{
    // Pass the host so the control can retrieve themes or store settings
    return new MySettingsControl(host); 
}
```

In your `UserControl`:
Use `host.Theme_Background`, `host.Theme_Text`, etc. to adjust your controls' colors in the constructor. This makes your add-on look native.

---

## Chapter 7: Best Practices & Thread Safety

### The "Cross-Thread Operation" Problem
SCOverlay is a UI application. If you want to change the UI (e.g., `ShowToast`) from a background thread (e.g., `Task.Run` or after an `HttpClient` Request), the app will crash.

**Wrong:**
```csharp
await Task.Run(() => {
    // BOOM! Crash, wrong thread.
    _host.Window.ShowToast("Done", "Info", NotificationLevel.Success);
});
```

**Right:**
Use the `Form` or `Control` you are currently operating to synchronize. If you have none, create one briefly or use pattern matching if the host allows access to the main form (via hacks), but cleaner is:

```csharp
// Save a reference to your settings control or window
_myControl.Invoke((MethodInvoker)delegate {
    _host.Window.ShowToast("Done", "Info", NotificationLevel.Success);
});
```

### Performance
*   Do not load large files in the `Draw` loop.
*   Use `RequestHighPerformanceMode` if you know you need high CPU momentarily.

**Good luck developing!**

---
## Chapter 8: API additions since 0.0.4.0

The `SCOverlay.API.dll` in this repository (`addons/SCOverlay.API.dll`) is **0.0.5.0**. Everything below needs at least that version on the user's machine; adding members to `IAddonHost` is binary-safe, so an add-on built against 0.0.5.0 still loads on an older core as long as it does not *call* the new members there (wrap such calls, see the last bullet).

| Member | What it is for |
| :--- | :--- |
| `IAddon.Kurzbeschreibung` | One short line (max. 40 characters) shown under the add-on's name on its menu tile. Has a default implementation (empty), so older add-ons keep compiling. |
| `AddonButton(id, getLabel, onClick, string iconKey)` | Picks one of the built-in tile glyphs (`timer`, `trade`, `mining`, `scan`, `log`, `settings`, `picture`, `sound`, `sheet`, `table`, `craft`, `accept`, `rep`, ...). Unknown keys draw a plain rounded square. |
| `AddonButton(id, getLabel, onClick, Image icon)` | Your own tile symbol as a bitmap. Works on every shipped core. |
| `IAddonHost.RegisterHotkey(callback, id, defaultHotkey, string? description)` | Same as before, plus a short description that the core shows next to the hotkey in *Settings → Shortcuts*. |
| `IAddonHost.Spiel` (`ISpielPfade`) | Where Star Citizen is installed, answered once by the core and shared with every add-on: `Bekannt`, `Kanalordner`, `Kanal`, `GameLog`, `LogBackups`, `LogDateien(mitBackups)`, `GlobalIni`, `GlobalIniDateien`, and a `Geaendert` event. **Always check `Bekannt` first**; "not installed" and "question skipped" are valid states and then everything is `null`. Do not guess a path yourself. |
| `IAddonHost.Nyx` (`INyxTheme`) | The design system: `Color(token)`, `Font(role[, designPx])`, `Space`, `Radius`, `Scale(designPx)` for DPI, and ready-made GDI+ calls (`DrawSurface`, `DrawButton`, `DrawInput`, `DrawTag`, `DrawIconTile`, `DrawText`, `DrawStat`, `DrawDivider`). `ThemeChanged` fires when the user switches the colour scheme. For **WPF** add-ons, `SharedResourceDictionary` is a `ResourceDictionary` you merge into your window (`Resources.MergedDictionaries.Insert(0, (ResourceDictionary)host.Nyx.SharedResourceDictionary)`); use `{DynamicResource}` throughout, then a theme switch reaches your window live. |
| `IWindowService.SetMousePassthrough(bool)` | Makes the overlay click-through for HUD-style add-ons. |
| `[Addon(LicenseId = ...)]` | Still compiles, does nothing. Licensing was removed; SCOverlay is free. Leave it out of new add-ons. |

Things that cost real time and are not obvious:

- **`host.T()` returns the raw keys during `Initialize`.** The core registers your `GetLocalizations()` only *after* `Initialize` has returned. Build no visible text in `Initialize`; do it in the first timer tick or when a window opens.
- **A modeless WPF window accepts no keyboard input** until you call `System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop(window)` after `InitializeComponent()`. The window looks perfectly healthy without it: it draws, the mouse works, the text box even has focus, and nothing you type arrives.
- **Never return a `HotkeyControl` from `GetSettingsControls()`.** The core auto-registers a hotkey for it whose action is empty and that overwrites the callback you registered in `Initialize`. Register hotkeys only in `Initialize`.
- **Hotkey strings must match the core's spelling exactly** or they silently never fire: `Ctrl+`, then `Alt+`, then `Shift+`, then the .NET 8 `Keys` enum name (for example `"Shift+OemSemicolon"` for Shift+Ü on a German keyboard). There is no error for a typo.
- **Calling a new API member on an older core throws `MissingMethodException` inside `Initialize`, and the core swallows it**, so your add-on simply disappears. If you want to support older cores, put the call in its own method marked `[MethodImpl(MethodImplOptions.NoInlining)]` and wrap the *call* in `try/catch`; a `try` around the direct access does not help, because the exception is thrown when the surrounding method is JIT-compiled, before the `try` is entered.
- **Do not ship a copy of `SCOverlay.API.dll` with your add-on.** The host provides it; a stale copy next to your DLL shadows the host's and makes new members vanish.

---

## Chapter 9: Getting into the Gallery

The Gallery inside the overlay and on the website lists add-ons that users can install with one click. What is in there is described honestly in [SECURITY.md](../SECURITY.md), and the rule for listing follows from it:

- **Only add-ons whose source the maintainer can read and build get listed.** There is no sandbox and no permission model; the maintainer building the package from source is what stands between a listing and the user's machine. That applies to updates too.
- **Package format:** a `.zip` named `<AddonId>.zip` with exactly one folder `<AddonId>/` at the root, containing your DLL, its `.deps.json` and any resources you load at runtime (sounds, sheets, data). No `.pdb`, no `SCOverlay.API.dll`, no `bin/obj` leftovers.
- **Versioning:** the updater compares version numbers only. A rebuilt package with the same version reaches nobody; bump `<Version>`/`<AssemblyVersion>`/`<FileVersion>` for every release.
- **Description:** bilingual, with `DE:` and `EN:` markers on their own lines; the overlay shows the part that matches the user's language.
- **How to start:** open an issue in this repository describing the add-on and linking to its source. You keep your copyright and choose your own licence for the add-on.
