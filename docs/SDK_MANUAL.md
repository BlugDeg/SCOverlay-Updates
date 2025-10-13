<p align="center">
<!-- Readme Links -->
<a href="README.md"><img src="https://img.shields.io/badge/Readme-555?style=for-the-badge" alt="Readme"></a><!--
--><a href="README.md"><img src="https://img.shields.io/badge/EN-ff6f00?style=for-the-badge" alt="English"></a><!--
--><a href="README.de.md"><img src="https://img.shields.io/badge/DE-555?style=for-the-badge" alt="Deutsch"></a>
&nbsp;&nbsp;|&nbsp;&nbsp;
<!-- Manual Links -->
<a href="MANUAL.md"><img src="https://img.shields.io/badge/Manual-555?style=for-the-badge" alt="Manual"></a><!--
--><a href="MANUAL.md"><img src="https://img.shields.io/badge/EN-555?style=for-the-badge" alt="English"></a><!--
--><a href="MANUAL.de.md"><img src="https://img.shields.io/badge/DE-555?style=for-the-badge" alt="Deutsch"></a>
&nbsp;&nbsp;|&nbsp;&nbsp;
<!-- Developer/SDK Links -->
<a href="SDK_MANUAL.md"><img src="https://img.shields.io/badge/Developer-007bff?style=for-the-badge" alt="Developer"></a><!--
--><a href="SDK_MANUAL.md"><img src="https://img.shields.io/badge/EN-ff6f00?style=for-the-badge" alt="English"></a><!--
--><a href="SDK_MANUAL.de.md"><img src="https://img.shields.io/badge/DE-555?style=for-the-badge" alt="Deutsch"></a>
</p>
<div align="center">
<br>
<svg width="120" height="120" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
<path d="M12 21C16.9706 21 21 16.9706 21 12C21 7.02944 16.9706 3 12 3C7.02944 3 3 7.02944 3 12C3 16.9706 7.02944 21 12 21Z" stroke="#4a90e2" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" opacity="0.4"/>
<path d="M12 17V12" stroke="#4a90e2" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
<path d="M12 3C12 3 15 6 15 9C15 12 12 17 12 17" stroke="#4a90e2" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
<path d="M12 3C12 3 9 6 9 9C9 12 12 17 12 17" stroke="#4a90e2" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
</svg>
<h1>SCOverlay Addon SDK</h1>
<p><strong>Developer Manual & API Guide (API v1.1 / Core v0.0.1.7+)</strong></p>
<br>
</div>

## Table of Contents
*   [Our Vision: A Platform for Creators](#chapter-1-our-vision-a-platform-for-creators)
*   [Getting Started: Your First Addon](#chapter-2-getting-started-your-first-addon)
    *   [Prerequisites & Setup](#prerequisites--setup)
    *   [Your First Code ("Hello World")](#your-first-code-hello-world)
    *   [Deployment](#deployment)
*   [The IAddon Interface: Your Addon's DNA](#chapter-3-the-iaddon-interface-your-addons-dna)
*   [The IAddonHost: Your Toolbox for the Core](#chapter-4-the-iaddonhost-your-toolbox-for-the-core)
    *   [Menu and UI Control](#menu-and-ui-control)
    *   [Core Services & Windows](#core-services--windows)
    *   [Hotkeys & Input (New & Powerful)](#hotkeys--input-new--powerful)
    *   [Persistence (Saving Data)](#persistence-saving-data)
    *   [Logging & Localization](#logging--localization)
    *   [Theming (Styling Your UI)](#theming-styling-your-ui)
    *   [Performance Management](#performance-management)
*   [Advanced Tutorial: Taking Over the Core Hotkey](#chapter-5-advanced-tutorial-taking-over-the-core-hotkey)
    *   [Step 1: Prepare the Logic](#step-1-prepare-the-logic)
    *   [Step 2: Request Control](#step-2-request-control)
    *   [Step 3: React to the Hotkey](#step-3-react-to-the-hotkey)
    *   [Step 4: Release Control](#step-4-release-control)
*   [Building Settings UIs: From Simple to Powerful](#chapter-6-building-settings-uis-from-simple-to-powerful)
    *   [Method 1: The Building Block System (Simple/Legacy)](#method-1-the-building-block-system-simplelegacy)
    *   [Method 2: Full UI Freedom (UserControl - Recommended)](#method-2-full-ui-freedom-usercontrol---recommended)
*   [Advanced Concepts & Best Practices](#chapter-7-advanced-concepts--best-practices)
    *   [Licensing for Premium Addons](#licensing-for-premium-addons)
    *   [Dos & Don'ts](#dos--donts)
*   [Troubleshooting: Solving Common Problems](#chapter-8-troubleshooting-solving-common-problems)
*   [Become Part of the Development!](#chapter-9-become-part-of-the-development)

---

## Chapter 1: Our Vision: A Platform for Creators

Welcome, developer! SCOverlay is more than just a tool—it's an ecosystem. Our vision is to create a stable, performant, and, above all, extensible platform that creative minds like you can build upon. You don't need to be a professional programmer to create something amazing. This guide is here to help you every step of the way.

*   **Modularity:** The core provides the stage; your addon is the star.
*   **Stability & Performance:** As a game overlay, performance is everything. We protect the gaming experience so you can focus on features.
*   **Strict Contract:** The `SCOverlay.API.dll` is our shared foundation. It's a promise that your work will continue to function across updates.

## Chapter 2: Getting Started: Your First Addon

### Prerequisites & Setup

*   **Visual Studio 2022** (the free Community Edition is perfect) with the ".NET Desktop Development" workload.
*   **.NET 8 SDK** or newer.
*   The `SCOverlay.API.dll` from the latest SCOverlay release.

1.  Create a "Class Library" project in Visual Studio for C# (.NET 8).
2.  Add API Reference: Right-click `Dependencies > Add Assembly Reference...` and select the `SCOverlay.API.dll`.
3.  **IMPORTANT:** Click on the `SCOverlay.API` reference, press `F4` for Properties, and set "Copy Local" to "No" (False). This prevents conflicts.

### Your First Code ("Hello World")

This is all you need for a functional addon. Copy this code into your `Class1.cs` file.
```csharp
// Using statements tell your code which toolboxes to use.
using SCOverlay.API;
using System.Collections.Generic;
using System.Drawing;
using System.Windows.Forms; // Needed for UserControl

namespace MyFirstAddon
{
    // The [Addon] attribute marks this class as the entry point for SCOverlay.
    [Addon]
    public class MyFirstAddon : IAddon
    {
        private IAddonHost? _host; // A private variable to store the "toolbox" from the core.

        // --- Basic Information ---
        public string Name => "My First Addon";
        public string Author => "Your Name";
        public string Version => "1.0.0";

        // This is like the constructor. It's called once when your addon is loaded.
        public void Initialize(IAddonHost host)
        {
            _host = host; // Store the host toolbox for later use.
            _host.LogInfo($"[{Name}] has been successfully initialized!");
        }

        // This method adds buttons to the main SCOverlay menu.
        public IEnumerable<AddonButton> GetMainMenuButtons()
        {
            // 'yield return' is a simple way to add one item at a time to a list.
            yield return new AddonButton(
                id: "my_addon_hello_button",
                getLabel: () => "Say Hello", // The text on the button.
                onClick: () => _host?.Window.ShowNotification("Hello from my addon!") // What happens on click.
            );
        }

        // --- For now, we leave the other required methods empty ---
        public IDictionary<string, (string en, string de)> GetLocalizations() => new Dictionary<string, (string, string)>();
        public void Draw(Graphics g, Rectangle bounds) { }
        public void OnOverlayVisibilityChanged(bool isVisible) { }
        public void Shutdown() { }
        public IEnumerable<AddonControl> GetSettingsControls() => []; // Legacy method, can be left empty
        public UserControl? GetSettingsControl(IAddonHost host) => null; // Recommended method, can return null
    }
}
```
### Deployment

Copy your compiled `.dll` file into a subfolder of the same name within `%AppData%\SCOverlay\addons`.

**Structure:** `%AppData%\SCOverlay\addons\MyFirstAddon\MyFirstAddon.dll`

<div class="note">
<strong>Stuck? We're here for you!</strong><br>
If anything is unclear, create a new issue on GitHub with the <code>developer-need-help</code> tag. There are no stupid questions!
</div>

## Chapter 3: The IAddon Interface: Your Addon's DNA

This is the blueprint for every addon. Your main class must implement all these members.

| Member                        | Type                              | Purpose & Detailed Explanation                                                                                                 |
| :---------------------------- | :-------------------------------- | :----------------------------------------------------------------------------------------------------------------------------- |
| `Name`, `Author`, `Version`   | `string`                          | **Metadata:** Identifies your addon.                                                                                           |
| `Initialize(IAddonHost host)` | `void`                            | **Constructor:** Called once on load. Store the host instance here. This is your setup phase.                                   |
| `GetMainMenuButtons()`        | `IEnumerable<AddonButton>`        | **Main Menu Buttons:** Defines the buttons your addon shows in the main menu.                                                  |
| `OnExclusiveHotkey()`         | `void`                            | **(NEW)** The callback the Core calls when you have exclusive hotkey control and the hotkey is pressed. Has an empty default implementation, so it's optional. |
| `GetSettingsControl(...)` | `UserControl?`                    | **(Recommended)** Provides a complete, custom UI panel for your settings. Gives you total creative freedom. See Chapter 6. |
| `GetSettingsControls()`       | `IEnumerable<AddonControl>`       | **(Legacy)** A limited way to add basic controls to the settings page. Only for very simple addons with no UI ambitions. |
| `Draw(Graphics g, ...)`       | `void`                            | **Drawing Engine:** Called every frame the overlay is redrawn. Keep this code extremely fast!                                   |
| `OnOverlayVisibilityChanged(...)` | `void`                            | **State Sync:** Reacts to the overlay opening/closing. Useful for starting/stopping background tasks.                            |
| `Shutdown()`                  | `void`                            | **Cleanup:** Called before unloading. Release all resources (e.g., close windows) here to prevent errors.        |
| `GetLocalizations()`          | `IDictionary<...>`                | **Localization:** Provide English and German translations for your addon's UI texts.                                           |

## Chapter 4: The IAddonHost: Your Toolbox for the Core

The `IAddonHost` is your bridge to all of SCOverlay's features.

### Menu and UI Control

*   `void TakeMenuControl(...)`: Takes exclusive control of the main menu if it's already open to create your own sub-menus.
*   `void ReleaseMenuControl()`: Returns control to the main menu.
*   `void InvalidateOverlay()`: Forces an immediate redraw. Crucial for making your UI changes visible.
*   `void HideMenu()`: **(NEW)** Safely and programmatically closes the entire overlay menu.

### Core Services & Windows

*   `ISoundService Sound { get; }`
    *   `PlayFile(...)`: Plays a sound file asynchronously without freezing the overlay.
*   `IWindowService Window { get; }`
    *   `ShowNotification(...)`: Displays a short, non-blocking "toast" notification.
    *   `CreateThemedWindow(...)`: Creates a new, empty, custom-drawn window (like the main overlay). **Not suitable for standard controls like buttons.**
    *   `CreateStandardWindow(...)`: **(NEW)** Creates a new window that inherits the theme and is **perfect for hosting standard controls** like buttons, labels, etc. This is the right choice for interactive dialogs.
    *   `Show/HideFilterOverlay(...)`: Shows or hides a screen-wide color filter.
*   `Task<Image> TakeScreenshotAsync()`: Asynchronously takes a screenshot of the game screen.

### Hotkeys & Input (New & Powerful)

<div class="note" style="background-color: #e7f3fe; border-left: 6px solid #2196F3;">
<strong>Important API Update: The Exclusive Control System</strong><br>
The old, error-prone `SuppressCoreHotkeys` method has been removed. The new system gives you full, yet safe, control over the main hotkey.
</div>

*   `bool RequestExclusiveHotkeyControl(IAddon addon)`:
    *   **Purpose:** This is the new way to "hijack" the overlay's main hotkey for your addon.
    *   **Function:** You request exclusive control. If no other addon already has it, the method returns `true`. From this moment on, all presses of the main hotkey are routed to your addon's `OnExclusiveHotkey()` method.
*   `void ReleaseExclusiveHotkeyControl(IAddon addon)`:
    *   **Purpose:** Returns control to the Core.
    *   **Function:** When you're done (e.g., when your window closes), you **must** call this method so the main overlay can respond to the hotkey again.
*   `void BlockGameInput(bool block)`:
    *   **Purpose:** Unchanged and vital for interactive UI. Blocks or unblocks input to the game.
*   `RegisterHotkey`, `UnregisterHotkey`, `RebindHotkey`:
    *   **Purpose:** For adding **additional, custom hotkeys** for your addon that are independent of the core hotkey.

### Persistence (Saving Data)

*   `string GetSetting(...) & void SetSetting(...):` A simple key-value storage for your addon.
*   **Best Practice:** Always use a unique prefix for your keys (e.g., `MyAddon_ApiToken`) to avoid conflicts.

### Logging & Localization

*   `LogInfo(...) & LogError(...):` Writes to the central `debug.log`. Your most important tool for debugging!
*   `string T(...):` Accesses the central translation system for multilingual text.

### Theming (Styling Your UI)

*   `Color Theme_Background { get; }`, `Font Theme_TextFont { get; }`, etc.: Read-only access to the active theme. Essential for styling your custom `UserControl` settings UI to match the rest of the overlay.

### Performance Management

*   `void RequestHighPerformanceMode(...) & void ReleaseHighPerformanceMode(...):` Temporarily tells the "Performance Watchdog" not to intervene during a short, CPU-intensive task.

## Chapter 5: Advanced Tutorial: Taking Over the Core Hotkey

This tutorial shows you how to use the new system to open your own UI instead of the main menu.

### Step 1: Prepare the Logic

Define the logic in your addon class for starting and stopping your exclusive mode.
```csharp
private IAddonHost? _host;
private Form? _myExclusiveWindow;
private bool _hasControl = false;

// Method to start the mode (e.g., from a button click)
private void StartExclusiveMode()
{
    if (_host == null || _hasControl) return;

    // 1. Request control
    if (_host.RequestExclusiveHotkeyControl(this))
    {
        _hasControl = true;
        _host.Window.ShowNotification("Control taken!");
        
        // 2. Safely hide the core menu
        _host.HideMenu();

        // 3. Show your own window
        OpenMyWindow();
    }
}

// Method to stop the mode
private void StopExclusiveMode()
{
    if (_host == null || !_hasControl) return;
    
    // 1. Close your window
    _myExclusiveWindow?.Close();
    _myExclusiveWindow = null;

    // 2. Release control
    _host.ReleaseExclusiveHotkeyControl(this);
    _hasControl = false;
    _host.Window.ShowNotification("Control released!");
}

private void OpenMyWindow()
{
    // Use CreateStandardWindow for interactive UI!
    _myExclusiveWindow = _host.Window.CreateStandardWindow("My Panel");
    _myExclusiveWindow.FormClosed += (s, e) => StopExclusiveMode(); // Failsafe!
    // ... add your buttons etc. here ...
    _myExclusiveWindow.Show();
}
```
### Step 2: React to the Hotkey

Implement the `OnExclusiveHotkey` method. It will now be called by the Core.
```csharp
public void OnExclusiveHotkey()
{
    // If the window exists, toggle it. If not, create it.
    if (_myExclusiveWindow != null && !_myExclusiveWindow.IsDisposed)
    {
        _myExclusiveWindow.Visible = !_myExclusiveWindow.Visible;
    }
    else
    {
        OpenMyWindow();
    }
}
```
### Step 3: Release Control
See `StopExclusiveMode()` above. The call to `_host.ReleaseExclusiveHotkeyControl(this)` is the crucial part. Make sure this happens when your feature is done (e.g., when the user closes your window).

### Step 4: Clean Up on Shutdown

Always ensure you return control to the core if your addon is unloaded.
```csharp
public void Shutdown()
{
    // Always ensure control is returned when unloading.
    StopExclusiveMode();
}
```
This system is robust, safe, and gives you full control over when and how your addon responds to the main hotkey.

## Chapter 6: Building Settings UIs: From Simple to Powerful

You have two ways to create a settings page for your addon. Choose the one that fits your needs.

### Method 1: The Building Block System (Simple/Legacy)

With `GetSettingsControls()`, you give the core a list of simple building blocks (`AddonControl`, `HotkeyControl`). The core then stacks them vertically for you.

*   **Pros:** Very simple for basic needs.
*   **Cons:** Extremely limited. No sliders, text boxes, or custom layouts.

```csharp
public IEnumerable<AddonControl> GetSettingsControls()
{
    yield return new HotkeyControl(
        identifier: "myaddon_hotkey_ctrl", 
        label: "Special Action Hotkey", 
        hotkeyIdentifier: "MyAddon_Action1",
        defaultHotkey: "Shift+F1"
    );
}
```
### Method 2: Full UI Freedom (UserControl - Recommended)

With `GetSettingsControl(IAddonHost host)`, you build your entire settings page visually in the Visual Studio Designer and hand this complete UI to the core. This is the **modern and recommended** approach.

*   **Pros:** Total creative freedom. Use sliders, text boxes, images, dropdowns, and arrange them however you want.
*   **Cons:** Requires a little more setup.

This is how you do it:

#### 1. Create your UserControl

In Visual Studio, right-click your project > Add > **User Control (Windows Forms)**. Name it `MySettingsPanel.cs`.
Use the visual designer to drag-and-drop controls onto your panel.

#### 2. Implement the Code

Your `IAddon` class now simply returns an instance of your new panel:

```csharp
// In your main IAddon class
public UserControl? GetSettingsControl(IAddonHost host)
{
    return new MySettingsPanel(host);
}

// And leave the old method empty
public IEnumerable<AddonControl> GetSettingsControls() => [];
```
The code for your `MySettingsPanel.cs` applies the core's theme to your UI:

```csharp
// In your MySettingsPanel.cs file
using SCOverlay.API;
using System.Windows.Forms;

public partial class MySettingsPanel : UserControl
{
    private readonly IAddonHost _host;

    public MySettingsPanel(IAddonHost host)
    {
        InitializeComponent(); // Loads controls from the designer
        _host = host;

        // Apply the theme to all controls
        ApplyThemeToAllControls(this); 
    }

    private void ApplyThemeToAllControls(Control parent)
    {
        // Set the background color of the panel
        parent.BackColor = _host.Theme_Background;

        foreach (Control control in parent.Controls)
        {
            control.ForeColor = _host.Theme_Text;
            control.Font = _host.Theme_TextFont;

            if (control is Button button)
            {
                var brush = _host.Theme_ButtonNormalBrush as System.Drawing.SolidBrush;
                if (brush != null) button.BackColor = brush.Color;
                button.FlatStyle = FlatStyle.Flat;
                button.FlatAppearance.BorderSize = 0;
            }
            
            // Recurse for container controls like GroupBox or Panel
            if (control.HasChildren)
            {
                ApplyThemeToAllControls(control);
            }
        }
    }
}
```
This approach gives you a professional, fully custom settings UI that still perfectly matches the look and feel of SCOverlay.

## Chapter 7: Advanced Concepts & Best Practices

### Licensing for Premium Addons

Want to offer your addon to supporters? This is a collaborative process.

1.  **Develop Your Addon.**
2.  **Contact Us:** When ready, contact the creator (BlugDeg) via a GitHub issue.
3.  **Integration:** We will generate a unique `LicenseId` for you.
4.  **Implementation:** You add the attribute to your addon class.

```csharp
[Addon(LicenseId = "MySuperAddon")]
public class MyPremiumAddon : IAddon { /* ... */ }
```

### Dos & Don'ts

*   ✅ **Release Resources:** Call `Dispose()` on any windows or UserControls you create, usually in your `Shutdown()` method, to prevent memory leaks.
*   ❌ **Never Block `Draw()`:** Do not perform long operations in `Draw`. It will cause stuttering.
*   ❌ **Don't Assume a UI Thread:** When updating UI from a background task, use `myControl.BeginInvoke(...)`.

## Chapter 8: Troubleshooting: Solving Common Problems

**"My addon doesn't appear in the menu!"**

*   **Incorrect Folder Structure:** The folder in `%AppData%\SCOverlay\addons` must have the exact same name as your DLL file (without the `.dll`).
*   **"Copy Local" is True:** The `SCOverlay.API` reference must have "Copy Local" set to "No" (False).
*   **Startup Error:** Check `debug.log` in `%AppData%\SCOverlay\`.

**"My UI change isn't showing up!"**

*   **Solution:** You must call `_host?.InvalidateOverlay();` after changing anything that should be visually updated.

**"My addon suddenly disappears!"**

*   **Cause:** The Performance Watchdog or the Hotkey Failsafe has ejected your addon.
*   **Solution:** Check `debug.log` for `CRITICAL` messages. Your addon has caused a serious error.

## Chapter 9: Become Part of the Development!

Your contribution is valuable. Your ideas and your help are always welcome.
Create an issue on GitHub to get help or suggest features. We're excited to see what you create!
