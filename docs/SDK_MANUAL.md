<p align="center">
<!-- Readme Links -->
<a href="README.md"><img src="https://img.shields.io/badge/Readme-555?style=for-the-badge" alt="Readme"></a><!--
--><a href="README.md"><img src="https://img.shields.io/badge/EN-555?style=for-the-badge" alt="English"></a><!--
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
<p><strong>Developer Manual & API Guide v3.2</strong></p>
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
    *   [Core Services](#core-services)
    *   [Hotkeys & Input (New & Powerful)](#hotkeys--input-new--powerful)
    *   [Persistence (Saving Data)](#persistence-saving-data)
    *   [Logging & Localization](#logging--localization)
    *   [Theming (Styling Your UI)](#theming-styling-your-ui)
    *   [Performance Management](#performance-management)
*   [Advanced Tutorial: Taking Over the Core Hotkey](#chapter-5-advanced-tutorial-taking-over-the-core-hotkey)
    *   [Step 1: Subscribe to the Event](#step-1-subscribe-to-the-event)
    *   [Step 2: Take Control](#step-2-take-control)
    *   [Step 3: Block Game Input & Show Your UI](#step-3-block-game-input--show-your-ui)
*   [Building Settings UIs: From Simple to Powerful](#chapter-6-building-settings-uis-from-simple-to-powerful)
    *   [Method 1: The Building Block System (Simple/Legacy)](#method-1-the-building-block-system-simplelegacy)
    *   [Method 2: Full UI Freedom (UserControl - Recommended)](#method-2-full-ui-freedom-usercontrol---recommended)
*   [Advanced Concepts & Best Practices](#chapter-7-advanced-concepts--best-practices)
    *   [Licensing for Premium Addons](#licensing-for-premium-addons)
    *   [Dos & Don'ts](#dos--donts)
*   [Troubleshooting: Solving Common Problems](#chapter-8-troubleshooting-solving-common-problems)
*   [Become Part of the Development!](#chapter-9-become-part-of-the-development)
    *   [Where to Find Help](#where-to-find-help)
    *   [Shape the Future of the API!](#shape-the-future-of-the-api)
    *   [Propose a Licensed Addon](#propose-a-licensed-addon)

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
*   The `SCOverlay.API.dll` (version 1.0.7 or higher) from the latest SCOverlay release.

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
        public IEnumerable<AddonControl> GetSettingsControls() => [];
        public IDictionary<string, (string en, string de)> GetLocalizations() => new Dictionary<string, (string, string)>();
        public void Draw(Graphics g, Rectangle bounds) { }
        public void OnOverlayVisibilityChanged(bool isVisible) { }
        public void Shutdown() { }
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
| `GetSettingsControl(IAddonHost host)` | `UserControl?`                    | **(New & Recommended)** Provides a complete, custom UI panel for your settings. Gives you total creative freedom. See Chapter 6. |
| `GetSettingsControls()`       | `IEnumerable<AddonControl>`       | **(Simple/Legacy)** A limited way to add basic controls to the settings page. A good fallback for very simple needs.         |
| `Draw(Graphics g, ...)`       | `void`                            | **Drawing Engine:** Called every frame the overlay is redrawn. Keep this code extremely fast!                                   |
| `OnOverlayVisibilityChanged(...)` | `void`                            | **State Sync:** Reacts to the overlay opening/closing. Useful for starting/stopping background tasks.                            |
| `Shutdown()`                  | `void`                            | **Cleanup:** Called before unloading. Release all resources (e.g., unsubscribe from events) here to prevent memory leaks.        |
| `GetLocalizations()`          | `IDictionary<...>`                | **Localization:** Provide English and German translations for your addon's UI texts.                                           |

## Chapter 4: The IAddonHost: Your Toolbox for the Core

The `IAddonHost` is your bridge to all of SCOverlay's features. Think of it as a toolbox filled with powerful tools you can use.

### Menu and UI Control

*   `void TakeMenuControl(...)`: Takes exclusive control of the main menu to create your own sub-menus.
*   `void ReleaseMenuControl()`: Returns control to the main menu.
*   `void InvalidateOverlay()`: Forces an immediate redraw. Crucial for making your UI changes visible.
*   `void HideMenu()`: Closes the entire overlay menu programmatically.

### Core Services

*   `ISoundService Sound { get; }`
    *   `PlayFile(...)`: Plays a sound file asynchronously without freezing the overlay.
*   `IWindowService Window { get; }`
    *   `ShowNotification(...)`: Displays a short, non-blocking "toast" notification.
    *   `CreateThemedWindow(...)`: Creates a new, empty window that automatically uses the current overlay theme.
    *   `Show/HideFilterOverlay(...)`: Shows or hides a screen-wide color filter, e.g., for a "night mode".
    *   `Task<Image> TakeScreenshotAsync()`: Asynchronously takes a screenshot of the game screen.

### Hotkeys & Input (New & Powerful)

<div class="note" style="background-color: #e7f3fe; border-left: 6px solid #2196F3;">
<strong>Important API Change: Event-Based System</strong><br>
Starting with version 1.0.7, the hotkey system has been upgraded to a flexible event model. This is the recommended approach for all new addons that need to react to hotkeys, especially if they intend to override the core's default behavior.
</div>

*   `event EventHandler<HotkeyEventArgs> OnGlobalHotkey;`
    *   **Purpose:** This is the new heart of hotkey processing. You can subscribe to this event to listen for **any** hotkey registered in the system, including the core toggle hotkey (`Shift+F10`).
    *   **Most Powerful Feature:** In the `HotkeyEventArgs` object, you can set `e.Handled = true;`. This signals to the core that you have completely handled the hotkey press. The core will then **not** perform its default action (like opening the main menu).
    *   **Use Case:** Perfect for "stealing" the core hotkey to open your own specialized UI, like a photomode panel, instead.
*   `void BlockGameInput(bool block);`
    *   **Purpose:** This is your most important function for managing interactive UI windows.
    *   `BlockGameInput(true)`: Instantly freezes the game. All keyboard and mouse input is intercepted by the core and no longer passed to the game. In the background, the core performs an intelligent trick (the "Invisible Butler") to give your addon window immediate system focus and position the mouse cursor perfectly.
    *   `BlockGameInput(false)`: Instantly unfreezes the game. The core ensures that the game regains focus and the mouse cursor is reset correctly, allowing the user to resume playing seamlessly.
*   `bool ShowHotkeyDialog(...)`: Opens a dialog to capture a new key combination from the user. Useful for your settings UI.
*   <span style="text-decoration: line-through;">`RegisterHotkey`, `UnregisterHotkey`, `RebindHotkey`</span>: **(Legacy)** These methods still work for backward compatibility for simple, specific hotkeys. For new addons, using the `OnGlobalHotkey` event is strongly recommended.

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

This tutorial shows you how to combine the new event system and `BlockGameInput` to open your own interactive UI instead of the default panel.

### Step 1: Subscribe to the Event

In your addon's `Initialize` method, register a handler for the new `OnGlobalHotkey` event.

```csharp
// In your main addon class
private IAddonHost _host;

public void Initialize(IAddonHost host)
{
    _host = host;
    _host.OnGlobalHotkey += OnGlobalHotkeyPress; // Subscribe to the event
}

// IMPORTANT: Unsubscribe from the event in your Shutdown method!
public void Shutdown()
{
    _host.OnGlobalHotkey -= OnGlobalHotkeyPress;
}
```

### Step 2: Take Control

In your handler method, check if the hotkey is the one you want to intercept and set `e.Handled = true`.

```csharp
private void OnGlobalHotkeyPress(object? sender, HotkeyEventArgs e)
{
    // Check if the core toggle hotkey was pressed.
    // .ToLowerInvariant() is important to ignore case sensitivity.
    if (e.Hotkey == _host.CoreToggleHotkey.ToLowerInvariant()) 
    {
        // Claim the event, preventing the default panel from opening.
        e.Handled = true;

        // Execute our own logic.
        ToggleMyInteractivePanel(); 
    }
}
```

### Step 3: Block Game Input & Show Your UI

Your `Toggle` method will use `BlockGameInput` to create a seamless experience.

```csharp
private MyCustomForm? _myPanel; // A reference to your window

private void ToggleMyInteractivePanel()
{
    bool isPanelVisible = _myPanel != null && !_myPanel.IsDisposed;

    if (isPanelVisible)
    {
        // If the panel is visible, simply close it.
        _myPanel.Close(); 
    }
    else
    {
        // To open the panel:

        // 1. Tell the core to freeze the game and prepare focus for us.
        _host.BlockGameInput(true);
        
        // 2. Create your custom window.
        _myPanel = new MyCustomForm(); // Your window that inherits from Form

        // 3. IMPORTANT: Ensure input is released when your window is closed.
        _myPanel.FormClosed += (s, a) => 
        {
            _host.BlockGameInput(false);
            _myPanel = null; // Clean up the reference
        };
        
        // 4. Show the window. The core handles the focus trick in the background.
        _myPanel.Show();
    }
}
```

## Chapter 6: Building Settings UIs: From Simple to Powerful

You have two ways to create a settings page for your addon. Choose the one that fits your needs.

### Method 1: The Building Block System (Simple/Legacy)

With `GetSettingsControls()`, you give the core a list of simple building blocks (`AddonControl`, `HotkeyControl`). The core then stacks them vertically for you.

*   **Pros:** Very simple for basic needs.
*   **Cons:** Extremely limited. No sliders, text boxes, or custom layouts.

```csharp
// This goes inside your IAddon class
public IEnumerable<AddonControl> GetSettingsControls()
{
    // A simple button
    yield return new AddonControl(
        id: "myaddon_reset_button", 
        label: "Reset Stats", 
        type: "RebindButton", // This type is for simple buttons
        getValue: () => "", 
        onClick: () => { /* Reset logic here */ }
    );
    
    // A special control for binding a hotkey
    yield return new HotkeyControl(
        identifier: "myaddon_hotkey_ctrl", 
        label: "Special Action Hotkey", 
        hotkeyIdentifier: "MyAddon_Action1", // The key for saving the setting
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
Use the visual designer to drag-and-drop controls like `Label`, `TextBox`, `TrackBar` (slider), etc. onto your panel.

#### 2. Implement the Code

Your `IAddon` class now simply returns an instance of your new panel:

```csharp
// In your main IAddon class
public UserControl? GetSettingsControl(IAddonHost host)
{
    // Simply create and return your custom UI panel.
    // Pass the 'host' to it so it can use the theme colors!
    return new MySettingsPanel(host);
}

// And leave the old method empty
public IEnumerable<AddonControl> GetSettingsControls() => [];
```

The code for your `MySettingsPanel.cs` will look like this. The key is to **apply the core's theme** to your custom UI.

```csharp
// In your MySettingsPanel.cs file
using SCOverlay.API;
using System.Drawing; // Needed for Color and Point
using System.Windows.Forms;

public partial class MySettingsPanel : UserControl
{
    private readonly IAddonHost _host;
    private Label infoLabel;
    private TrackBar volumeSlider;

    public MySettingsPanel(IAddonHost host)
    {
        InitializeComponent(); // This loads the controls from the designer (if you use it)
        _host = host;

        // --- Create Controls Programmatically ---
        infoLabel = new Label { Text = "Set Volume:", Location = new Point(10, 15) };
        volumeSlider = new TrackBar { Location = new Point(10, 40), Width = 200, Maximum = 100 };
        this.Controls.Add(infoLabel);
        this.Controls.Add(volumeSlider);
        
        ApplyTheme(); // Apply the core's theme to your custom UI
    }

    private void ApplyTheme()
    {
        // Use the theme from the host to style your controls
        this.BackColor = _host.Theme_Background;
        this.infoLabel.ForeColor = _host.Theme_Text;
        this.infoLabel.Font = _host.Theme_TextFont;
        this.volumeSlider.TickColor = _host.Theme_Accent;
    }
}
```
This approach gives you a professional, fully custom settings UI that still perfectly matches the look and feel of SCOverlay.

## Chapter 7: Advanced Concepts & Best Practices

### Licensing for Premium Addons

Want to offer your addon to supporters? The SCOverlay system is designed for this. This is a collaborative process. You cannot invent a `LicenseId` yourself; it must be generated and integrated into the core by the SCOverlay team.

The process:

1.  **Develop Your Addon:** Focus on building your addon first.
2.  **Contact Us:** When ready, contact the creator (BlugDeg) via a GitHub issue (see Chapter 9).
3.  **Integration:** We will work with you to create a unique `LicenseId` on the license server and integrate it into the next SCOverlay release.
4.  **Implementation:** You will receive the official ID from us. Only then do you add the attribute to your addon class.

```csharp
// Example: You received the ID "MySuperAddon" from the creator.
[Addon(LicenseId = "MySuperAddon")]
public class MyPremiumAddon : IAddon { /* ... */ }
```

### Dos & Don'ts

*   ✅ **Unsubscribe from Events:** In your `Shutdown()` method, always unsubscribe from events like `host.OnGlobalHotkey -= MyHandler;` to prevent memory leaks.
*   ❌ **Never Block `Draw()`:** Do not perform file I/O, network requests, or long loops in the `Draw` method. It will cause stuttering.
*   ❌ **Don't Assume a UI Thread:** When updating UI from a background task, use `myControl.BeginInvoke(...)` to prevent crashes.

## Chapter 8: Troubleshooting: Solving Common Problems

**"My addon doesn't appear in the menu!"**

*   **Incorrect Folder Structure:** The folder in `%AppData%\SCOverlay\addons` must have the exact same name as your DLL file (without the `.dll`).
*   **"Copy Local" is True:** The `SCOverlay.API` reference must have "Copy Local" set to "No" (False).
*   **Startup Error:** Check `debug.log` in `%AppData%\SCOverlay\`. An error in your `Initialize` method will stop the addon from loading.

**"My UI change isn't showing up!"**

*   **Solution:** You must call `_host?.InvalidateOverlay();` after changing anything that should be visually updated.

**"My addon suddenly disappears!"**

*   **Cause:** The Performance Watchdog has unloaded your addon for using too much CPU.
*   **Solution:** Optimize your code (especially `Draw()`). For short, intentional heavy tasks, wrap them in `RequestHighPerformanceMode`.

## Chapter 9: Become Part of the Development!

Your contribution is valuable. Your ideas and your help are always welcome.

### Where to Find Help

➡️ **Ask a question in the `developer-need-help` channel**
Create a new issue with this label. No question is too simple!

### Shape the Future of the API!

➡️ **Suggest a new API feature**
If you have an idea for a new tool in the `IAddonHost` toolbox, let us know!

### Propose a Licensed Addon

➡️ **Request a new License ID**
Create an issue to introduce your premium addon project.

We're excited to see what you create
