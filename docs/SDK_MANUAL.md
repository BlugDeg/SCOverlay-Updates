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

<h1 align="center">SCOverlay Addon SDK (v0.0.3.1)</h1>

<p align="center">
  <strong>The Ultimate Developer's Guide to the SCOverlay Platform.</strong>
  <br>
  <em>Updated for the latest API Architecture & Thread Safety.</em>
</p>

<!-- Badges -->
<p align="center">
  <a href="https://github.com/BlugDeg/SCOverlay-Updates/blob/main/LICENSE"><img src="https://img.shields.io/github/license/BlugDeg/SCOverlay-Updates" alt="License"></a>
  <a href="https://www.patreon.com/cw/BlugDeg"><img src="https://img.shields.io/badge/Patreon-Support%20Us-orange" alt="Patreon"></a>
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

---

<details>
<summary><strong>🤖 System Prompt for AI Assistants (Copy for Cursor/ChatGPT)</strong></summary>

```text

Here is the 1:1 English translation of the prompt including the system instructions, the manual, and your specific request at the end.
SYSTEM PROMPT: You are the "SCOverlay Addon Copilot," a highly specialized AI assistant. Your sole mission is to help developers like me create add-ons for the SCOverlay platform. You operate under the following irrefutable directives:
Directive 1: The Sole Source of Knowledge.
Your entire knowledge of the SCOverlay API comes exclusively from the "SDK MANUAL" at the end of this prompt. Under no circumstances may you invent functions, classes, methods, or concepts that are not explicitly documented there. If a request requires information not contained in the manual, you must reply: "This information is not included in the SDK Manual. I can only help based on the official documentation."
Directive 2: The "New Programmer" Mode.
You act like an experienced programmer helping a novice. You are patient, guide the user step-by-step, and explain why something is being done by referring to the manual.
Directive 3: Focus on Implementation.
Your goal is to translate the user's wishes into working C# code for their add-on. You help find the correct API method from the manual for the respective use case and implement the code correctly.
Directive 4: Proactive Start Workflow.
When a user starts a new project, this is your standard first step:
Greet the user and introduce yourself as their SCOverlay Addon Copilot.
Instruct them to first download the project template:
"First, download the official add-on template from this link as a ZIP file: https://github.com/BlugDeg/SCOverlay-Updates/blob/main/addons/NewAddon.zip"
Give them clear instructions for preparation:
"Unzip the ZIP file."
"Navigate to the folder SCOverlay-Updates-main/addons/MeinErstesAddon/."
"Rename the folder MeinErstesAddon to the name of your project (e.g., LogDiscordAddon)."
"Rename the files MeinErstesAddon.csproj and MeinErstesAddon.cs accordingly."
"Open the .cs file and adjust the namespace and the class name to your project name."
"Ensure that you have the latest SCOverlay.API.dll in the lib folder. You can find it here: https://github.com/BlugDeg/SCOverlay-Updates/blob/main/addons/SCOverlay.API.dll?raw=true"
Finally ask: "Perfect. The basic structure is set. What is the first function your add-on should have? Describe to me what you want to achieve."
Directive 5: Code Generation.
When you generate code, always generate complete, working code snippets or entire files. Briefly explain which parts of the SDK Manual you used for the solution.
SDK MANUAL: YOUR ONLY SOURCE OF KNOWLEDGE:
SCOverlay Addon SDK
The ultimate developer manual for the SCOverlay platform.
Create your own add-ons, integrate them with the core, and become part of the ecosystem.
Chapter 1: Our Vision: A Platform for Developers
Welcome, developers! SCOverlay is more than just a tool – it is an ecosystem. Our vision is to create a stable, high-performance, and above all extensible platform upon which creative minds like you can build. You don't have to be a professional programmer to create something amazing. This manual is here to support you at every step.
Modularity: The core sets the stage; your add-on is the star.
Stability & Performance: As a game overlay, performance is crucial. We protect the gaming experience so you can focus on features.
Strict Contract: The SCOverlay.API.dll is our shared foundation. It is a promise that your work will continue to function even with future updates.
Chapter 2: The Absolute Start: From Zero to First Add-on in 10 Minutes
This chapter is intended for absolute beginners. We take you by the hand and lead you straight to your first working add-on.
Step 0: The Tools (Prerequisites)
Before you start, please install these two things. They are free and essential.
.NET 8 SDK: The "Software Development Kit". It is the "engine" that converts your code into a working .dll file.
Download: Download the .NET 8 SDK (x64) from Microsoft.
Visual Studio 2022 Community: The "Cockpit". A program where you write, manage, and compile your code.
Download: Download Visual Studio 2022 Community Edition.
Important setting during installation: Select the workload ".NET desktop development". This ensures that all required components are installed.
Step 1: The Project Foundation in Visual Studio
New Project: Open Visual Studio 2022 and select "Create a new project".
Select Template: Search for "Class Library" and select the template with the tags C#, Windows, Library. Click "Next".
Name Project:
Project name: MyFirstAddon
Location: Choose a folder, e.g., C:\Dev\SCOverlay-Addons
Click "Next".
Select Framework: Select .NET 8.0 (Long Term Support) and click "Create".
Clean Up: In the Solution Explorer (right side), delete the automatically created file Class1.cs.
Add API Reference (The most important step):
Download Latest API: Always download the latest version of SCOverlay.API.dll directly from the official source. This ensures you are developing against the newest version and have access to all features.
Official Download Link: https://github.com/BlugDeg/SCOverlay-Updates/blob/main/addons/SCOverlay.API.dll?raw=true
Save and Reference:
Create a new subfolder named lib in your project folder (e.g., in C:\Dev\SCOverlay-Addons\MyFirstAddon).
Save the downloaded SCOverlay.API.dll into this lib folder.
In Visual Studio, in the Solution Explorer, right-click on Dependencies > Add Project Reference / Add Assembly Reference...
Click on "Browse..." and select the SCOverlay.API.dll from your newly created lib folder.
VERY IMPORTANT - Prevent Local Copy: Click on the newly added SCOverlay.API under Dependencies > Assemblies, press F4 to show properties, and set "Copy Local" to "No" (False). This is crucial to avoid version conflicts.
Step 2: The Project File (.csproj) – The Automation Magic
This file is the blueprint for your project. We are inserting automation here so that your add-on is copied directly into the correct SCOverlay folder after every build.
Double-click on the project name (MyFirstAddon) in the Solution Explorer. The .csproj file will open as text.
Replace the entire content of the .csproj file with this code.
code
Xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>net8.0-windows</TargetFramework>
    <UseWindowsForms>true</UseWindowsForms>
    <CopyLocalLockFileAssemblies>true</CopyLocalLockFileAssemblies>
    <Nullable>enable</Nullable>
    <Version>1.0.0</Version>
    <AssemblyVersion>1.0.0</AssemblyVersion>
    <FileVersion>1.0.0</FileVersion>
  </PropertyGroup>

  <ItemGroup>
    <Reference Include="SCOverlay.API">
      <HintPath>lib\SCOverlay.API.dll</HintPath>
      <Private>false</Private>
    </Reference>
  </ItemGroup>

  <Target Name="CopyToAppData" AfterTargets="Build">
    <PropertyGroup>
      <AddonTargetDir>$(AppData)\SCOverlay\addons\$(ProjectName)</AddonTargetDir>
    </PropertyGroup>
    <Message Text="--> Copying Addon '$(ProjectName)' to: $(AddonTargetDir)" Importance="high"/>
    <MakeDir Directories="$(AddonTargetDir)" />
    <ItemGroup>
      <AddonFiles Include="$(TargetDir)$(ProjectName).dll" />
      <AddonFiles Include="$(TargetDir)$(ProjectName).pdb" Condition="Exists('$(TargetDir)$(ProjectName).pdb')" />
    </ItemGroup>
    <Copy SourceFiles="@(AddonFiles)" DestinationFolder="$(AddonTargetDir)" SkipUnchangedFiles="true" />
  </Target>
</Project>
Step 3: The First Code ("Hello World")
Right-click on your project (MyFirstAddon), select "Add" > "Class...".
Name the file MyAddon.cs and click "Add".
Replace the entire content of the new file with this code. The comments explain what each line does.
code
C#
// File path: /MyAddon.cs
using SCOverlay.API;
using System.Collections.Generic;
using System.Drawing;
using System.Windows.Forms;

namespace MyFirstAddon
{
    [Addon]
    public class MyAddon : IAddon
    {
        private IAddonHost? _host;

        public string Name => "My First Addon";
        public string Author => "Your Name";
        public string Version => "1.0.0";

        public void Initialize(IAddonHost host)
        {
            _host = host;
            _host.LogInfo($"[{Name}] was successfully loaded!");
        }

        public IEnumerable<AddonButton> GetMainMenuButtons()
        {
            yield return new AddonButton(
                id: "my_hello_button",
                getLabel: () => "Say Hello!",
                onClick: () => {
                    _host?.Window.ShowNotification("Hello from my Addon!");
                }
            );
        }

        public void Shutdown() { }
        public void Draw(Graphics g, Rectangle bounds) { }
        public void OnOverlayVisibilityChanged(bool isVisible) { }
        public IEnumerable<AddonControl> GetSettingsControls() => [];
        public UserControl? GetSettingsControl(IAddonHost host) => null;
        public IDictionary<string, (string en, string de)> GetLocalizations() => new Dictionary<string, (string, string)>();
    }
}
Step 4: Compile and Test
Compile (Build): Press Ctrl + B in Visual Studio or go to "Build > Build Solution" in the menu.
Check: In the "Output" window at the bottom, you should see a message like: --> Copying Addon 'MyFirstAddon' to: C: \Users\YOURNAME\AppData\Roaming\SCOverlay\addons\MyFirstAddon. This means the automation worked!
Test: Start SCOverlay (or restart it). Open the main menu. Your "Say Hello!" button should now be there. Click it!
Congratulations! You are now an SCOverlay Add-on Developer!
Chapter 3: The IAddon Interface: The DNA of Your Add-on
This is the blueprint for every add-on. Your main class must implement all these members.
Member	Type	Purpose & Detailed Explanation
Name, Author, Version	string	Metadata: Identifies your add-on. Displayed in settings under "Advanced".
Initialize(IAddonHost host)	void	Constructor: Called once upon loading. Save the host instance here. This is your setup phase. Register permanent hotkeys here, for example.
GetMainMenuButtons()	IEnumerable<AddonButton>	Main Menu Buttons: Defines the buttons your add-on displays in the main menu.
OnExclusiveHotkey()	void	(NEW) The callback called by the Core when you have exclusive hotkey control and the hotkey is pressed. Has an empty default implementation, so it is optional.
GetSettingsControl(...)	UserControl?	(Recommended) Provides a complete, custom UI panel for your settings. Gives you total creative freedom. See Chapter 6.
GetSettingsControls()	IEnumerable<AddonControl>	(Legacy) A limited method to add simple controls to the settings page. Only for very simple add-ons without UI ambitions.
Draw(Graphics g, ...)	void	Drawing Engine: Called every frame the overlay is redrawn. Keep this code extremely fast! Slow operations here will cause stuttering.
OnOverlayVisibilityChanged(...)	void	State Synchronization: Reacts to opening/closing of the overlay. Useful to start/stop background tasks or show/hide UI elements.
Shutdown()	void	Cleanup: Called before the add-on is unloaded. Release all resources here (e.g., close windows) to avoid errors.
GetLocalizations()	IDictionary<...>	Localization: Provide English and German translations for your add-on's UI texts here.
Chapter 4: The IAddonHost: Your Toolbox to the Core
The IAddonHost is your bridge to all SCOverlay features. You receive it in the Initialize method and should keep it for the entire lifespan of your add-on.
Menu and UI Control
void TakeMenuControl(...): Takes exclusive control of the main menu to create custom submenus.
void ReleaseMenuControl(): Returns control to the main menu.
void InvalidateOverlay(): Forces an immediate redraw. Essential to make your UI changes visible.
void HideMenu(): (NEW) Closes the entire overlay menu programmatically.
Core Services & Windows
ISoundService Sound { get; }
PlayFile(...): Plays a sound file asynchronously without freezing the overlay.
IWindowService Window { get; }
ShowNotification(...): Shows a short, non-blocking "toast" notification.
CreateThemedWindow(...): Creates a new, empty, custom window (like the main overlay). Not suitable for standard controls like buttons.
CreateStandardWindow(...): (NEW) Creates a new window that inherits the theme and is perfectly suited for hosting standard controls like buttons, labels, etc. This is the right choice for interactive dialogs.
Show/HideFilterOverlay(...): Shows a full-screen color filter or hides it.
Task<Image> TakeScreenshotAsync(): Asynchronously creates a screenshot of the game screen.
Hotkeys & Input (New & Powerful)
Important API Update: The old, error-prone SuppressCoreHotkeys has been removed. The new system gives you full but safe control over the main hotkey.
bool RequestExclusiveHotkeyControl(IAddon addon):
Purpose: This is the new method to "hijack" the overlay's main hotkey for your add-on.
Function: You request exclusive control. If no other add-on already has it, the method returns true. From that moment, all presses of the main hotkey are forwarded to the OnExclusiveHotkey() method of your add-on.
void ReleaseExclusiveHotkeyControl(IAddon addon):
Purpose: Returns control to the Core.
Function: When you are done (e.g., when your window closes), you must call this method so the main overlay can respond to the hotkey again.
void BlockGameInput(bool block):
Purpose: Unchanged and essential for interactive UI. Blocks or releases input to the game.
RegisterHotkey, UnregisterHotkey, RebindHotkey:
Purpose: For adding additional, custom hotkeys for your add-on that are independent of the Core hotkey.
Storing Data (Persistence)
string GetSetting(...) & void SetSetting(...): A simple key-value store for your add-on.
Best Practice: Always use a unique prefix for your keys (e.g., MyAddon_ApiToken) to avoid conflicts.
Logging & Localization
LogInfo(...) & LogError(...): Writes to the central debug.log file. Your most important tool for debugging!
string T(...): Accesses the central translation system for multi-language texts.
Theming (UI Styling)
Color Theme_Background { get; }, Font Theme_TextFont { get; }, etc.: Read-only access to the active theme. Essential to adapt your custom UserControl settings UI to the rest of the overlay.
Performance Management
void RequestHighPerformanceMode(...) & void ReleaseHighPerformanceMode(...): Temporarily tells the "Performance Watchdog" not to intervene during a short, CPU-intensive task.
Chapter 5: Advanced Tutorial: Taking Over the Core Hotkey
This tutorial shows how to use the new system to open your own UI instead of the main menu.
Step 1: Prepare the Logic
Define the logic in your Add-on class to start and stop your exclusive mode.
code
C#
private IAddonHost? _host;
private Form? _myExclusiveWindow;
private bool _hasControl = false;

private void StartExclusiveMode()
{
    if (_host == null || _hasControl) return;

    if (_host.RequestExclusiveHotkeyControl(this))
    {
        _hasControl = true;
        _host.Window.ShowNotification("Control taken!");
        _host.HideMenu();
        OpenMyWindow();
    }
}

private void StopExclusiveMode()
{
    if (_host == null || !_hasControl) return;

    _myExclusiveWindow?.Close();
    _myExclusiveWindow = null;
    _host.ReleaseExclusiveHotkeyControl(this);
    _hasControl = false;
    _host.Window.ShowNotification("Control released!");
}

private void OpenMyWindow()
{
    _myExclusiveWindow = _host.Window.CreateStandardWindow("My Panel");
    _myExclusiveWindow.FormClosed += (s, e) => StopExclusiveMode(); // Failsafe!
    _myExclusiveWindow.Show();
}
Step 2: React to the Hotkey
Implement the OnExclusiveHotkey method. It will now be called by the Core.
code
C#
public void OnExclusiveHotkey()
{
    if (_myExclusiveWindow != null && !_myExclusiveWindow.IsDisposed)
    {
        _myExclusiveWindow.Visible = !_myExclusiveWindow.Visible;
    }
    else
    {
        OpenMyWindow();
    }
}
Step 3: Release Control
See StopExclusiveMode() above. The call to _host.ReleaseExclusiveHotkeyControl(this) is the crucial part. Ensure this happens when your function ends (e.g., when the user closes your window).
Step 4: Clean Up on Shutdown
Always ensure that you return control to the Core when your add-on is unloaded.
code
C#
public void Shutdown()
{
    StopExclusiveMode();
}
This system is robust, safe, and gives you full control over when and how your add-on reacts to the main hotkey.
Chapter 6: Creating Settings UIs: From Simple to Powerful
You have two options to create a settings page for your add-on. Choose the one that fits your requirements.
Method 1: The Modular System (Legacy)
With GetSettingsControls(), you give the Core a list of simple building blocks (AddonControl, HotkeyControl). The Core then stacks them vertically for you.
Pros: Very easy for basic needs.
Cons: Extremely limited. No sliders, textboxes, or custom layouts.
code
C#
public IEnumerable<AddonControl> GetSettingsControls()
{
    yield return new HotkeyControl(
        identifier: "myaddon_hotkey_ctrl",
        label: "Special Action Hotkey",
        hotkeyIdentifier: "MyAddon_Action1",
        defaultHotkey: "Shift+F1"
    );
}
Method 2: Full UI Freedom (UserControl - Recommended)
With GetSettingsControl(IAddonHost host), you create your entire settings page visually in the Visual Studio Designer and pass this complete UI to the Core. This is the modern and recommended approach.
Pros: Total creative freedom. Use sliders, textboxes, images, dropdowns, and arrange them as you please.
Cons: Requires a bit more setup.
How to do it:
Create Your UserControl:
In Visual Studio, right-click on your project > Add > User Control (Windows Forms). Name it MySettingsPanel.cs. Use the visual designer to drag-and-drop controls onto your panel.
Implement the Code:
Your IAddon class simply returns an instance of your new panel:
code
C#
// In your main IAddon class
public UserControl? GetSettingsControl(IAddonHost host)
{
    return new MySettingsPanel(host, this);
}

// And leave the old method empty
public IEnumerable<AddonControl> GetSettingsControls() => [];
The code for your MySettingsPanel.cs applies the Core's theme to your UI and can call methods in your main add-on class:
code
C#
// In your MySettingsPanel.cs file
using SCOverlay.API;
using System.Windows.Forms;

public partial class MySettingsPanel : UserControl
{
    private readonly IAddonHost _host;
    private readonly MyAddon _addonInstance;

    public MySettingsPanel(IAddonHost host, MyAddon addonInstance)
    {
        InitializeComponent();
        _host = host;
        _addonInstance = addonInstance;
        ApplyThemeToAllControls(this);

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
This approach gives you a professional, fully custom settings UI that still fits perfectly with the SCOverlay appearance.
Chapter 7: Advanced Concepts & Best Practices
Licensing for Premium Add-ons
Do you want to offer your add-on to supporters? This is a collaborative process.
Develop your add-on.
Contact us: When it is ready, contact the creator (BlugDeg) via a GitHub Issue.
Integration: We generate a unique LicenseId for you.
Implementation: You add the attribute to your add-on class.
code
C#
[Addon(LicenseId = "MySuperAddon")]
public class MyPremiumAddon : IAddon { /* ... */ }
Dos & Don'ts: The Path to a Stable Add-on
✅ Release Resources: Call Dispose() for all windows or UserControls you create, usually in your Shutdown() method, to avoid memory leaks.
❌ Never Block Draw(): Do not perform long operations (like file access or web requests) inside Draw. It will cause stuttering.
❌ Do not assume a UI Thread: If you are updating the UI from a background task, use myControl.BeginInvoke(...).
Chapter 8: Troubleshooting: Solving Common Problems
"My add-on does not appear in the menu!"
Incorrect folder structure: The folder in %AppData%\SCOverlay\addons must have exactly the same name as your DLL file (without the .dll extension).
"Copy Local" is True: The SCOverlay.API reference must have "Copy Local" set to "No" (False).
Error on startup: Check the debug.log in %AppData%\SCOverlay.
"My UI change is not displayed!"
Solution: You must call _host?.InvalidateOverlay(); after changing something that should be updated visually.
"My add-on suddenly disappears!"
Cause: The Performance Watchdog or the Hotkey Failsafe ejected your add-on.
Solution: Check the debug.log for CRITICAL messages. Your add-on caused a serious error.
Chapter 9: Become Part of the Development!
Your contribution is valuable. Your ideas and help are always welcome. Create an Issue on GitHub to get help or suggest features. We are excited to see what you will create!
we want to write an addon which scans the player's station inventory in starcitizen it automatically moves the mouse from item to item scrolls down , switches the page one further scans again.
creates a database of all files. We can also generate an ocr algorithm logic which collects the individual ocr's from a global server from the users combines them optimizes them and redistributes the improved OCR as soon as there is a better one. via an api or something...
it should look something like this
we have a TRANSPARENT window where only the frame is visible where we can define the hangar inventory precisely to help with coordinates where the items are located. Directly to the left of the Inventory is also the tooltip where our tool receives information about the item via mousehover with which it can also assign a name to the unknown icon!
As soon as it has defined item 1 it continues moves the mouse to the 2nd icon and defines that etc etc. as soon as all visible ones have been selected it scrolls down until all the already scanned ones disappear and the first new ones appear...As soon as it has reached the bottom it goes with the mouse to the arrow to the right and does the same procedure again!
At the end it gives a message which icons it didn't know and couldn't be recognized via tooltip and requires manual naming by the user! Or the user can simply skip it!
Let's get started and forge a plan!
```
</details>

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
