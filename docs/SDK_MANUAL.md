<p align="center">
  <a href="README.md"><img src="https://img.shields.io/badge/USER-README-007bff?style=flat-square" alt="User Readme"></a><!--
  --><a href="README.de.md"><img src="https://img.shields.io/badge/BENUTZER-LIESMICH-555?style=flat-square" alt="Benutzer Liesmich"></a><!--
  --><a href="SDK_MANUAL.md"><img src="https://img.shields.io/badge/DEVELOPER-EN-ff6f00?style=flat-square" alt="Developer EN"></a><!--
  --><a href="SDK_MANUAL.de.md"><img src="https://img.shields.io/badge/ENTWICKLER-DE-555?style=flat-square" alt="Entwickler DE"></a>
</p>

# SCOverlay Addon SDK Manual

Welcome to the SCOverlay Addon SDK! This document is your comprehensive guide to developing extensions (Addons) for SCOverlay.

## Chapter 1: Philosophy & Getting Started

### The Vision Behind the API
The SCOverlay architecture was designed with three core principles in mind: **Modularity**, **Stability & Performance**, and a **Strict Contract** via the `SCOverlay.API.dll`.

### 1.1. Prerequisites & Project Setup
- Visual Studio 2022 with the ".NET Desktop Development" workload.
- .NET 8 SDK or newer.
- The `SCOverlay.API.dll` file.

Create a **Class Library (.NET)** project, add a reference to the API DLL, and set its `<Private>false</Private>` property in the `.csproj` file.

### 1.2. Deployment Structure
After compiling, your addon must be placed in a specific folder structure for SCOverlay to find it:
`%AppData%\SCOverlay\addons\**MyFirstAddon**\**MyFirstAddon.dll**`

---

## Chapter 2: The `IAddon` Interface in Detail

This is the blueprint for every addon. Your main class must implement this interface.
*   `Name, Author, Version`: Metadata for your addon.
*   `Initialize(IAddonHost host)`: The entry point of your addon.
*   `GetMainMenuButtons()`: Provides buttons for the main overlay menu.
*   `GetSettingsControls()`: Provides UI controls for the central settings page.
*   `Draw(Graphics g, ...)`: The drawing engine, called on every frame. Keep it fast!
*   `OnOverlayVisibilityChanged(bool isVisible)`: State synchronization callback.
*   `Shutdown()`: Cleanup method. Release all resources here.
*   `GetLocalizations()`: Provide translation strings for your addon.

---

## Chapter 3: The `IAddonHost`: Your Bridge to the Core

The `IAddonHost` instance is your gateway to the main application, providing safe access to encapsulated core services.

### 3.1. UI & Menu Control
*   `TakeMenuControl(...)`: Takes exclusive control of the menu for sub-menus.
*   `ReleaseMenuControl()`: Returns menu control to the core.
*   `InvalidateOverlay()`: Forces a complete redraw of the overlay.

### 3.2. Service Access
*   `_host.Sound.PlayFile(...)`: Plays a sound asynchronously.
*   `_host.Window.ShowNotification(...)`: Displays a system-wide "toast" notification.
*   `_host.Window.CreateThemedWindow(...)`: Creates a new, empty window that automatically adopts the overlay's current theme.

---

## Chapter 4: Communication Flows: Addon <=> Core

### 4.1. Addon to Core (Commands & Data Provisioning)
Your addon actively commands the core (`_host.LogInfo(...)`) or passively provides data when requested (`GetMainMenuButtons()`).

### 4.2. Core to Addon (Callbacks & Lifecycle)
The core informs your addon about events through lifecycle methods (`Initialize`, `Shutdown`) and UI events (`Draw`, `OnOverlayVisibilityChanged`).

---

## Chapter 5: Best Practices & Common Pitfalls

### DOs:
*   ✅ **Always check for null:** Use null-conditional operators: `_host?.LogInfo(...)`.
*   ✅ **Release resources:** Implement `IDisposable` for custom forms and call `Dispose()` in `Shutdown()`.
*   ✅ **Unsubscribe from events:** Always unsubscribe from events like `_host.OnPaintOverlay` in your `Shutdown()` method.
*   ✅ **Use `try...finally` for Performance Mode:** Ensure `ReleaseHighPerformanceMode()` is always called.

### DON'Ts:
*   ❌ **Never block `Draw()`:** Avoid file I/O or long loops in the `Draw` method.
*   ❌ **Don't forget `InvalidateOverlay()`:** Call it after changing any state that affects the UI.
*   ❌ **Don't assume a UI thread:** Use `myWindow.BeginInvoke(...)` to safely update UI from a non-UI thread.