<p align="center">
<!-- Readme Links -->
<a href="README.md"><img src="https://img.shields.io/badge/Readme-555?style=for-the-badge" alt="Readme"></a><!--
--><a href="README.md"><img src="https://img.shields.io/badge/EN-ff6f00?style=for-the-badge" alt="English"></a><!--
--><a href="README.de.md"><img src="https://img.shields.io/badge/DE-555?style=for-the-badge" alt="Deutsch"></a>
&nbsp;&nbsp;|&nbsp;&nbsp;
<!-- Manual Links -->
<a href="MANUAL.md"><img src="https://img.shields.io/badge/Manual-555?style=for-the-badge" alt="Manual"></a><!--
--><a href="MANUAL.md"><img src="https://img.shields.io/badge/EN-ff6f00?style=for-the-badge" alt="English"></a><!--
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
<p><strong>The Ultimate Developer's Guide (API v1.1 / Core v0.0.1.7+)</strong></p>
<br>
</div>

## Table of Contents
*   [Chapter 1: Our Vision: A Platform for Developers](#chapter-1-our-vision-a-platform-for-developers)
*   [Chapter 2: The Absolute Start: From Zero to Your First Add-on in 10 Minutes](#chapter-2-the-absolute-start-from-zero-to-your-first-add-on-in-10-minutes)
    *   [Step 0: The Tools (Prerequisites)](#step-0-the-tools-prerequisites)
    *   [Step 1: The Project Foundation in Visual Studio](#step-1-the-project-foundation-in-visual-studio)
    *   [Step 2: The Project File (`.csproj`) – The Automation Magic](#step-2-the-project-file-csproj--the-automation-magic)
    *   [Step 3: The First Code ("Hello World")](#step-3-the-first-code-hello-world)
    *   [Step 4: Compile and Test](#step-4-compile-and-test)
*   [Chapter 3: The `IAddon` Interface: The DNA of Your Add-on](#chapter-3-the-iaddon-interface-the-dna-of-your-add-on)
*   [Chapter 4: The `IAddonHost`: Your Toolbox to the Core](#chapter-4-the-iaddonhost-your-toolbox-to-the-core)
    *   [Menu and UI Control](#menu-and-ui-control)
    *   [Core Services & Windows](#core-services--windows)
    *   [Hotkeys & Input (New & Powerful)](#hotkeys--input-new--powerful)
    *   [Saving Data (Persistence)](#saving-data-persistence)
    *   [Logging & Localization](#logging--localization)
    *   [Theming (UI Styling)](#theming-ui-styling)
    *   [Performance Management](#performance-management)
*   [Chapter 5: Advanced Tutorial: Taking Over the Core Hotkey](#chapter-5-advanced-tutorial-taking-over-the-core-hotkey)
*   [Chapter 6: Creating Settings UIs: From Simple to Powerful](#chapter-6-creating-settings-uis-from-simple-to-powerful)
    *   [Method 1: The Building Block System (Legacy)](#method-1-the-building-block-system-legacy)
    *   [Method 2: Full UI Freedom (`UserControl` - Recommended)](#method-2-full-ui-freedom-usercontrol---recommended)
*   [Chapter 7: Advanced Concepts & Best Practices](#chapter-7-advanced-concepts--best-practices)
*   [Chapter 8: Troubleshooting: Solving Common Problems](#chapter-8-troubleshooting-solving-common-problems)
*   [Chapter 9: Become Part of the Development!](#chapter-9-become-part-of-the-development)

---

## Chapter 1: Our Vision: A Platform for Developers

Welcome, developer! SCOverlay is more than just a tool – it's an ecosystem. Our vision is to create a stable, high-performance, and above all, extensible platform that creative minds like you can build upon. You don't have to be a professional programmer to create something amazing. This guide is here to support you every step of the way.

*   **Modularity:** The core provides the stage; your add-on is the star.
*   **Stability & Performance:** As a game overlay, performance is crucial. We protect the gaming experience so you can focus on features.
*   **Strict Contract:** The `SCOverlay.API.dll` is our common foundation. It's a promise that your work will continue to function even with future updates.

---

## Chapter 2: The Absolute Start: From Zero to Your First Add-on in 10 Minutes

This chapter is intended for absolute beginners. We'll take you by the hand and guide you directly to your first working add-on.

### Step 0: The Tools (Prerequisites)

Before you start, please install these two things. They are **free and essential**.

1.  **.NET 8 SDK:** The "Software Development Kit." It's the "engine" that turns your code into a working `.dll` file.
    *   **Download:** [Download the .NET 8 SDK (x64) from Microsoft.](https://dotnet.microsoft.com/en-us/download/dotnet/8.0)

2.  **Visual Studio 2022 Community:** The "cockpit." A program where you write, manage, and compile your code.
    *   **Download:** [Download Visual Studio 2022 Community Edition](https://visualstudio.microsoft.com/vs/community/)
    *   **Important setting during installation:** Select the **".NET desktop development"** workload. This ensures that all required components are installed.

### Step 1: The Project Foundation in Visual Studio

1.  **New Project:** Open Visual Studio 2022 and select **"Create a new project"**.
2.  **Choose a template:** Search for **"Class Library"** and select the template with the tags `C#`, `Windows`, `Library`. Click "Next".
3.  **Name your project:**
    *   **Project name:** `MyFirstAddon`
    *   **Location:** Choose a folder, e.g., `C:\Dev\SCOverlay-Addons`
    *   Click "Next".
4.  **Choose a framework:** Select **.NET 8.0 (Long-term support)** and click "Create".
5.  **Clean up:** In the Solution Explorer (right side), delete the automatically created `Class1.cs` file.
6.  **Add API reference:**
    *   Find your SCOverlay installation folder (by default `C:\Program Files (x86)\SCOverlay`).
    *   In the Solution Explorer, right-click on **Dependencies > Add Assembly Reference...**.
    *   Click **"Browse..."** and select the `SCOverlay.API.dll` from the installation folder.
    *   **VERY IMPORTANT:** Click on the newly added `SCOverlay.API` under `Dependencies > Assemblies`, press `F4` to show the properties, and set **"Copy Local" to "No" (False)**. This prevents version conflicts.

### Step 2: The Project File (`.csproj`) – The Automation Magic

This file is the blueprint for your project. We'll add some automation here so that your add-on is copied directly to the correct SCOverlay folder after every build.

1.  In the Solution Explorer, double-click on the project name (`MyFirstAddon`). The `.csproj` file will open as text.
2.  **Replace the entire content** of the `.csproj` file with this code. **Be sure to adjust the `HintPath`** if your SCOverlay is installed elsewhere!

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <!-- Basic project settings -->
    <TargetFramework>net8.0-windows</TargetFramework>
    <UseWindowsForms>true</UseWindowsForms>
    <CopyLocalLockFileAssemblies>true</CopyLocalLockFileAssemblies>
    <Nullable>enable</Nullable>
    <Version>1.0.0</Version>
    <AssemblyVersion>1.0.0</AssemblyVersion>
    <FileVersion>1.0.0</FileVersion>
  </PropertyGroup>

  <ItemGroup>
    <!-- This block references the SCOverlay API, which is required for development. -->
    <Reference Include="SCOverlay.API">
      <!-- 
        !!! IMPORTANT: ADJUST THIS PATH TO YOUR SCOVERLAY INSTALLATION FOLDER !!!
      -->
      <HintPath>C:\Program Files (x86)\SCOverlay\SCOverlay.API.dll</HintPath>
      <Private>false</Private> <!-- Corresponds to "Copy Local: No" -->
    </Reference>
  </ItemGroup>

  <!-- THIS BLOCK IS THE AUTOMATIC COPY MAGIC -->
  <Target Name="CopyToAppData" AfterTargets="Build">
    <PropertyGroup>
      <!-- Defines the target directory: %AppData%\SCOverlay\addons\PROJECTNAME -->
      <AddonTargetDir>$(AppData)\SCOverlay\addons\$(ProjectName)</AddonTargetDir>
    </PropertyGroup>
    <Message Text="--> Copying Addon '$(ProjectName)' to: $(AddonTargetDir)" Importance="high" />
    <MakeDir Directories="$(AddonTargetDir)" />
    <ItemGroup>
      <!-- Collects all files necessary for the add-on (DLL and debug information) -->
      <AddonFiles Include="$(TargetDir)$(ProjectName).dll" />
      <AddonFiles Include="$(TargetDir)$(ProjectName).pdb" Condition="Exists('$(TargetDir)$(ProjectName).pdb')" />
    </ItemGroup>
    <!-- Executes the copy operation -->
    <Copy SourceFiles="@(AddonFiles)" DestinationFolder="$(AddonTargetDir)" SkipUnchangedFiles="true" />
  </Target>

</Project>
```

### Step 3: The First Code ("Hello World")

1.  Right-click on your project (`MyFirstAddon`), select **"Add" > "Class..."**.
2.  Name the file `MyAddon.cs` and click "Add".
3.  Replace the entire content of the new file with this code. The comments explain what each line does.

```csharp
// File path: /MyAddon.cs

// "using" imports toolboxes that we need.
using SCOverlay.API;
using System.Collections.Generic;
using System.Drawing;
using System.Windows.Forms;

// A namespace is like a folder for our code.
namespace MyFirstAddon
{
    // The [Addon] attribute tells SCOverlay: "Hey, this is an add-on!"
    [Addon]
    public class MyAddon : IAddon
    {
        // A private variable to store our "bridge" to SCOverlay.
        private IAddonHost? _host;

        // Basic information about our add-on.
        public string Name => "My First Addon";
        public string Author => "Your Name";
        public string Version => "1.0.0";

        // Called once when SCOverlay loads the add-on.
        public void Initialize(IAddonHost host)
        {
            _host = host; // We save the bridge for later use.
            _host.LogInfo($"[{Name}] was loaded successfully!");
        }

        // Adds buttons to the SCOverlay main menu.
        public IEnumerable<AddonButton> GetMainMenuButtons()
        {
            // We create and "yield" a new button back to the main menu.
            yield return new AddonButton(
                id: "my_hello_button",
                getLabel: () => "Say Hello!", // Text on the button.
                onClick: () => {
                    // What happens on click: Show a notification.
                    _host?.Window.ShowNotification("Hello from my Addon!");
                }
            );
        }

        // The remaining methods are mandatory, but we don't need them right now.
        public void Shutdown() { }
        public void Draw(Graphics g, Rectangle bounds) { }
        public void OnOverlayVisibilityChanged(bool isVisible) { }
        public IEnumerable<AddonControl> GetSettingsControls() => [];
        public UserControl? GetSettingsControl(IAddonHost host) => null;
        public IDictionary<string, (string en, string de)> GetLocalizations() => new Dictionary<string, (string, string)>();
    }
}
```

### Step 4: Compile and Test

1.  **Compile (Build):** In Visual Studio, press the key combination `Ctrl + B` or go to the menu **"Build > Build Solution"**.
2.  **Check:** In the "Output" window at the bottom, you should see a message like: `--> Copying Addon 'MyFirstAddon' to: C:\Users\YOURNAME\AppData\Roaming\SCOverlay\addons\MyFirstAddon`. This means the automation worked!
3.  **Test:** Start SCOverlay (or restart it). Open the main menu. Your **"Say Hello!"** button should now be there. Click it!

**Congratulations! You are now an SCOverlay add-on developer!**

---

## Chapter 3: The `IAddon` Interface: The DNA of Your Add-on

This is the blueprint for every add-on. Your main class must implement all of these members.

| Member                        | Type                              | Purpose & Detailed Explanation                                                                                                 |
| :---------------------------- | :-------------------------------- | :----------------------------------------------------------------------------------------------------------------------------- |
| `Name`, `Author`, `Version`   | `string`                          | **Metadata:** Identifies your add-on. Displayed in the settings under "Advanced". |
| `Initialize(IAddonHost host)` | `void`                            | **Constructor:** Called once on load. Store the `host` instance here. This is your setup phase. Register permanent hotkeys here, for example. |
| `GetMainMenuButtons()`        | `IEnumerable<AddonButton>`        | **Main Menu Buttons:** Defines the buttons your add-on displays in the main menu. |
| `OnExclusiveHotkey()`         | `void`                            | **(NEW)** The callback the core invokes when you have exclusive hotkey control and the hotkey is pressed. Has an empty default implementation, so it's optional. |
| `GetSettingsControl(...)` | `UserControl?`                    | **(Recommended)** Provides a complete, custom UI panel for your settings. Gives you total creative freedom. See Chapter 6. |
| `GetSettingsControls()`       | `IEnumerable<AddonControl>`       | **(Legacy)** A limited method for adding simple controls to the settings page. Only for very simple add-ons without UI ambitions. |
| `Draw(Graphics g, ...)`       | `void`                            | **Drawing Engine:** Called every frame the overlay is redrawn. **Keep this code extremely fast!** Slow operations here will cause stuttering. |
| `OnOverlayVisibilityChanged(...)` | `void`                            | **Status Synchronization:** Reacts to the overlay opening/closing. Useful for starting/stopping background tasks or showing/hiding UI elements. |
| `Shutdown()`                  | `void`                            | **Cleanup:** Called before the add-on is unloaded. Release all resources here (e.g., close windows) to prevent errors. |
| `GetLocalizations()`          | `IDictionary<...>`                | **Localization:** Provide English and German translations for your add-on's UI text here. |

---

## Chapter 4: The `IAddonHost`: Your Toolbox to the Core

The `IAddonHost` is your bridge to all of SCOverlay's features. You receive it in the `Initialize` method and should keep it for the entire lifetime of your add-on.

### Menu and UI Control

*   `void TakeMenuControl(...)`: Takes exclusive control of the main menu to create your own submenus.
*   `void ReleaseMenuControl()`: Returns control to the main menu.
*   `void InvalidateOverlay()`: Forces an immediate redraw. **Essential** to make your UI changes visible.
*   `void HideMenu()`: **(NEW)** Programmatically closes the entire overlay menu.

### Core Services & Windows

*   `ISoundService Sound { get; }`
    *   `PlayFile(...)`: Plays a sound file asynchronously without freezing the overlay.
*   `IWindowService Window { get; }`
    *   `ShowNotification(...)`: Displays a short, non-blocking "toast" notification.
    *   `CreateThemedWindow(...)`: Creates a new, empty, custom window (like the main overlay). **Not suitable for standard controls like buttons.**
    *   `CreateStandardWindow(...)`: **(NEW)** Creates a new window that inherits the theme and is **perfect for hosting standard controls** like buttons, labels, etc. This is the right choice for interactive dialogs.
    *   `Show/HideFilterOverlay(...)`: Shows or hides a screen-filling color filter.
*   `Task<Image> TakeScreenshotAsync()`: Asynchronously takes a screenshot of the game screen.

### Hotkeys & Input (New & Powerful)

> **Important API Update:** The old, error-prone `SuppressCoreHotkeys` has been removed. The new system gives you full, but safe, control over the main hotkey.

*   `bool RequestExclusiveHotkeyControl(IAddon addon)`:
    *   **Purpose:** This is the new method to "hijack" the overlay's main hotkey for your add-on.
    *   **Function:** You request exclusive control. If no other add-on already has it, the method returns `true`. From this moment on, all presses of the main hotkey are forwarded to your add-on's `OnExclusiveHotkey()` method.
*   `void ReleaseExclusiveHotkeyControl(IAddon addon)`:
    *   **Purpose:** Returns control to the core.
    *   **Function:** When you are done (e.g., when your window closes), you **must** call this method so that the main overlay can react to the hotkey again.
*   `void BlockGameInput(bool block)`:
    *   **Purpose:** Unchanged and essential for interactive UI. Blocks or releases input to the game.
*   `RegisterHotkey`, `UnregisterHotkey`, `RebindHotkey`:
    *   **Purpose:** For adding **additional, custom hotkeys** for your add-on that are independent of the core hotkey.

### Saving Data (Persistence)

*   `string GetSetting(...) & void SetSetting(...):` A simple key-value store for your add-on.
*   **Best Practice:** Always use a unique prefix for your keys (e.g., `MyAddon_ApiToken`) to avoid conflicts.

### Logging & Localization

*   `LogInfo(...) & LogError(...):` Writes to the central `debug.log` file. Your most important tool for debugging!
*   `string T(...):` Accesses the central translation system for multilingual text.

### Theming (UI Styling)

*   `Color Theme_Background { get; }`, `Font Theme_TextFont { get; }`, etc.: Read-only access to the active theme. Essential for making your custom `UserControl` settings UI match the rest of the overlay.

### Performance Management

*   `void RequestHighPerformanceMode(...) & void ReleaseHighPerformanceMode(...):` Temporarily tells the "Performance Watchdog" not to intervene during a short, CPU-intensive task.

---

## Chapter 5: Advanced Tutorial: Taking Over the Core Hotkey

This tutorial shows how to use the new system to open your own UI instead of the main menu.

### Step 1: Prepare the Logic

Define the logic in your add-on class to start and stop your exclusive mode.
```csharp
private IAddonHost? _host;
private Form? _myExclusiveWindow;
private bool _hasControl = false;

// Method to start the mode (e.g., via a button click)
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
    
    // 1. Close your own window
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

Implement the `OnExclusiveHotkey` method. It will now be called by the core.
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
See `StopExclusiveMode()` above. The call to `_host.ReleaseExclusiveHotkeyControl(this)` is the crucial part. Ensure this happens when your feature is finished (e.g., when the user closes your window).

### Step 4: Clean Up on Shutdown

Always make sure you return control to the core when your add-on is unloaded.
```csharp
public void Shutdown()
{
    // Always ensure control is returned on unload.
    StopExclusiveMode();
}
```
This system is robust, safe, and gives you full control over when and how your add-on reacts to the main hotkey.

---

## Chapter 6: Creating Settings UIs: From Simple to Powerful

You have two options for creating a settings page for your add-on. Choose the one that fits your needs.

### Method 1: The Building Block System (Legacy)

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
### Method 2: Full UI Freedom (`UserControl` - Recommended)

With `GetSettingsControl(IAddonHost host)`, you create your entire settings page visually in the Visual Studio Designer and pass this complete UI to the core. This is the **modern and recommended** approach.

*   **Pros:** Total creative freedom. Use sliders, text boxes, images, dropdowns, and arrange them as you like.
*   **Cons:** Requires a bit more setup.

Here's how:

#### 1. Create Your UserControl

In Visual Studio, right-click on your project > Add > **User Control (Windows Forms)**. Name it `MySettingsPanel.cs`.
Use the visual designer to drag and drop controls onto your panel.

#### 2. Implement the Code

Your `IAddon` class now simply returns an instance of your new panel:

```csharp
// In your main IAddon class
public UserControl? GetSettingsControl(IAddonHost host)
{
    // We pass a reference to ourselves (this) to the UI panel.
    return new MySettingsPanel(host, this);
}

// And leave the old method empty
public IEnumerable<AddonControl> GetSettingsControls() => [];
```
The code for your `MySettingsPanel.cs` applies the core's theme to your UI and can call methods in your main add-on class:

```csharp
// In your MySettingsPanel.cs file
using SCOverlay.API;
using System.Windows.Forms;

public partial class MySettingsPanel : UserControl
{
    private readonly IAddonHost _host;
    private readonly MyAddon _addonInstance; // A reference to the main add-on class

    public MySettingsPanel(IAddonHost host, MyAddon addonInstance)
    {
        InitializeComponent(); // Loads controls from the designer
        _host = host;
        _addonInstance = addonInstance;

        // Apply the theme to all controls
        ApplyThemeToAllControls(this); 

        // Link a button click to a method in your addon
        myTestButton.Click += (s, e) => _addonInstance.DoSomethingCool();
    }

    private void ApplyThemeToAllControls(Control parent)
    {
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
            
            if (control.HasChildren)
            {
                ApplyThemeToAllControls(control);
            }
        }
    }
}
```
This approach gives you a professional, fully custom settings UI that still perfectly matches the look and feel of SCOverlay.

---

## Chapter 7: Advanced Concepts & Best Practices

### Licensing for Premium Add-ons

Want to offer your add-on to supporters? This is a collaborative process.

1.  **Develop your add-on.**
2.  **Contact us:** When it's ready, contact the creator (BlugDeg) via a GitHub issue.
3.  **Integration:** We will generate a unique `LicenseId` for you.
4.  **Implementation:** You add the attribute to your add-on class.

```csharp
[Addon(LicenseId = "MySuperAddon")]
public class MyPremiumAddon : IAddon { /* ... */ }
```

### Dos & Don'ts: The Path to a Stable Add-on

*   ✅ **Release Resources:** Call `Dispose()` on any windows or `UserControls` you create, usually in your `Shutdown()` method, to prevent memory leaks.
*   ❌ **Never Block `Draw()`:** Do not perform long operations (like file access or web requests) in `Draw`. It will cause stuttering.
*   ❌ **Don't Assume a UI Thread:** If you are updating the UI from a background task, use `myControl.BeginInvoke(...)`.

---

## Chapter 8: Troubleshooting: Solving Common Problems

**"My add-on doesn't appear in the menu!"**

*   **Incorrect folder structure:** The folder in `%AppData%\SCOverlay\addons` must have the exact same name as your DLL file (without the `.dll` extension).
*   **"Copy Local" is True:** The `SCOverlay.API` reference must have "Copy Local" set to "No" (False).
*   **Error on startup:** Check the `debug.log` in `%AppData%\SCOverlay\`.

**"My UI change isn't showing up!"**

*   **Solution:** You need to call `_host?.InvalidateOverlay();` after you've changed something that needs to be visually updated.

**"My add-on suddenly disappears!"**

*   **Cause:** The Performance Watchdog or the hotkey failsafe has ejected your add-on.
*   **Solution:** Check the `debug.log` for `CRITICAL` messages. Your add-on has caused a fatal error.

---

## Chapter 9: Become Part of the Development!

Your contribution is valuable. Your ideas and help are always welcome.
Create an issue on GitHub to get help or suggest features. We are excited to see what you will create!
