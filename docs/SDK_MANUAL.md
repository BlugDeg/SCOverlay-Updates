<p align="center">
  <a href="../README.de.md"><img src="https://img.shields.io/badge/Readme-555?style=flat-square" alt="Readme"></a><!--
  --><a href="../README.md"><img src="https://img.shields.io/badge/EN-007bff?style=flat-square" alt="English"></a><!--
  --><a href="../README.de.md"><img src="https://img.shields.io/badge/DE-555?style=flat-square" alt="Deutsch"></a>
  &nbsp;&nbsp;|&nbsp;&nbsp;
  <a href="SDK_MANUAL.de.md"><img src="https://img.shields.io/badge/Developer-555?style=flat-square" alt="Developer"></a><!--
  --><a href="SDK_MANUAL.md"><img src="https://img.shields.io/badge/EN-ff6f00?style=flat-square" alt="English"></a><!--
  --><a href="SDK_MANUAL.de.md"><img src="https://img.shields.io/badge/DE-555?style=flat-square" alt="Deutsch"></a>
</p>

---

<div align="center">
  <br>
  <svg width="120" height="120" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
    <path d="M12 21C16.9706 21 21 16.9706 21 12C21 7.02944 16.9706 3 12 3C7.02944 3 3 7.02944 3 12C3 16.9706 7.02944 21 12 21Z" stroke="#4a90e2" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" opacity="0.4"/>
    <path d="M12 17V12" stroke="#4a90e2" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
    <path d="M12 3C12 3 15 6 15 9C15 12 12 17 12 17" stroke="#4a90e2" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
    <path d="M12 3C12 3 9 6 9 9C9 12 12 17 12 17" stroke="#4a90e2" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
  </svg>
  <h1>SCOverlay Addon SDK</h1>
  <p><strong>Comprehensive Developer Manual v2.3</strong></p>
  <br>
</div>

---

## Table of Contents

1.  [**Our Vision: A Platform by Developers, for Gamers**](#chapter-1-our-vision-a-platform-by-developers-for-gamers)
2.  [**Getting Started: Your First Addon in 10 Minutes**](#chapter-2-getting-started-your-first-addon-in-10-minutes)
3.  [**The Core Interfaces in Detail**](#chapter-3-the-core-interfaces-in-detail)
4.  [**The `IAddonHost` as a Toolbox**](#chapter-4-the-iaddonhost-as-a-toolbox)
5.  [**Advanced Concepts & Best Practices**](#chapter-5-advanced-concepts--best-practices)
6.  [**Troubleshooting & Common Pitfalls**](#chapter-6-troubleshooting--common-pitfalls)
7.  [**Become Part of the Development!**](#chapter-7-become-part-of-the-development)

---

## Chapter 1: Our Vision: A Platform by Developers, for Gamers

### The Philosophy Behind the API
Welcome, developer! SCOverlay is more than just a tool—it's an ecosystem. Our vision is to create a stable, performant, and, above all, **extensible** platform that creative minds like you can build upon.

-   **Modularity:** The core provides the stage; your addon is the star.
-   **Stability & Performance:** As a game overlay, performance is everything. We protect the gaming experience so you can focus on features.
-   **Strict Contract:** The `SCOverlay.API.dll` is our shared foundation. It guarantees that your work will last.

---

## Chapter 2: Getting Started: Your First Addon in 10 Minutes

### Prerequisites & Setup in Visual Studio
-   **Visual Studio 2022** with the ".NET Desktop Development" workload.
-   **.NET 8 SDK** or newer.
-   The **`SCOverlay.API.dll`**.

1.  Create a **"Class Library"** project for C# (.NET 8.0).
2.  **Add API Reference:** Right-click on **Dependencies > Add Assembly Reference...** and select the `SCOverlay.API.dll`.
3.  **IMPORTANT:** Click on the new `SCOverlay.API` reference, press `F4` for the Properties window, and set **"Copy Local"** to **"No" (False)**.

### The "Hello World" Implementation
```csharp
using SCOverlay.API;
using System.Collections.Generic;
using System.Drawing;

namespace MyFirstAddon
{
    [Addon]
    public class MyFirstAddon : IAddon
    {
        private IAddonHost? _host;
        public string Name => "My First Addon";
        public string Author => "Your Name";
        public string Version => "1.0.0";

        public void Initialize(IAddonHost host)
        {
            _host = host;
            _host.LogInfo($"[{Name}] has been successfully initialized!");
        }

        public IEnumerable<AddonButton> GetMainMenuButtons()
        {
            yield return new AddonButton(
                id: "my_addon_hello_button",
                getLabel: () => "Say Hello",
                onClick: () => _host?.Window.ShowNotification("Hello world from my addon!")
            );
        }

        // Empty implementations for the rest
        public IEnumerable<AddonControl> GetSettingsControls() => [];
        public IDictionary<string, (string en, string de)> GetLocalizations() => new Dictionary<string, (string, string)>();
        public void Draw(Graphics g, Rectangle bounds) { }
        public void OnOverlayVisibilityChanged(bool isVisible) { }
        public void Shutdown() { }
    }
}
```

### Deployment: How SCOverlay Finds Your Addon
Copy your compiled `.dll` file into a subfolder of the same name within `%AppData%\SCOverlay\addons`.
**Structure:** `%AppData%\SCOverlay\addons\MyFirstAddon\MyFirstAddon.dll`

<div class="note">
<strong>Stuck? We're here for you!</strong><br>
If anything is unclear during these first steps, don't hesitate! Create a new issue on GitHub with the <code>developer-need-help</code> tag. We'll be happy to help you get started.
</div>

---

## Chapter 3: The Core Interfaces in Detail

### Analysis of the `IAddon` Interface
This is the blueprint for every addon. Your main class must fully implement this interface.

| Member                                | Type                                            | Purpose & Detailed Explanation                                                                                                   |
| ------------------------------------- | ---------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------- |
| `Name, Author, Version`               | `string`                                       | **Metadata:** Used for identification and display in future UI elements.                                                         |
| `Initialize(IAddonHost host)`         | `void`                                         | **The constructor of your addon.** Called upon loading. Store the `host` instance here for later use.                              |
| `GetMainMenuButtons()`                | `IEnumerable<AddonButton>`                     | **Main Menu Visibility.** Defines which buttons your addon wants to display in the main menu.                                      |
| `GetSettingsControls()`               | `IEnumerable<AddonControl>`                    | **Settings Integration.** Places UI elements on the central settings page of the overlay.                                       |
| `Draw(Graphics g, ...)`               | `void`                                         | **The Drawing Engine.** Called on every redraw of the overlay. Keep this code extremely performant!                                |
| `OnOverlayVisibilityChanged(...)`     | `void`                                         | **State Synchronization.** Reacts to the opening/closing of the overlay.                                                        |
| `Shutdown()`                          | `void`                                         | **Cleanup.** Called before the addon is unloaded. Release all resources here.                                                     |
| `GetLocalizations()`                  | `IDictionary<string, (string en, string de)>`  | **Internationalization.** Provides custom translations for the multilingual system.                                              |

### Analysis of the `IAddonHost` Interface
Your gateway to the SCOverlay core. It's designed as a facade to hide complexity and ensure a stable API, even if the core's internals change. We will dissect every function in the next chapter.

---

## Chapter 4: The `IAddonHost` as a Toolbox

Here is a detailed breakdown of all methods available to you through the `IAddonHost` instance.

### Menu and UI Control
-   **`void TakeMenuControl(IAddon addon, Action? onBack)`**
    *   **Purpose:** Takes exclusive control of the main menu to create your own sub-menus.
-   **`void ReleaseMenuControl()`**
    *   **Purpose:** Returns control to the main menu.
-   **`void InvalidateOverlay()`**
    *   **Purpose:** Forces an immediate redraw of the overlay. Essential for making UI changes visible.

### Accessing Core Services
-   **`ISoundService Sound { get; }`**
    *   **`PlayFile(string path, float volume = 1.0f)`**: Plays a sound file asynchronously on a background thread.
-   **`IWindowService Window { get; }`**
    *   **`ShowNotification(string message)`**: Displays a short, non-blocking "toast" notification.
    *   **`CreateThemedWindow(string title)`**: Creates a new, empty `Form` that automatically inherits the current overlay theme.

### Persistence
-   **`string GetSetting(string key, string defaultValue)` & `void SetSetting(string key, string value)`**
    *   **Purpose:** A simple key-value storage system for your addon, saved in the central `settings.json` file.
    *   **Best Practice:** Always use a unique prefix for your keys (e.g., `MyAddon_ApiToken`) to avoid conflicts with other addons.

### Logging & Localization
-   **`LogInfo(string message)` & `LogError(string message, Exception? ex = null)`**
    *   **Purpose:** Writes standardized entries to the `debug.log` file (`%AppData%\SCOverlay\debug.log`). This is your most important tool for debugging!
-   **`string T(string localizationKey)`**
    *   **Purpose:** Accesses the central translation system.

### Theming
-   **`Color Theme_Background { get; }`, `Font Theme_TextFont { get; }`, etc.**
    *   **Purpose:** Gives you read-only access to the active theme's colors and fonts for a consistent look.

### Performance Management
-   **`void RequestHighPerformanceMode(...)` & `void ReleaseHighPerformanceMode(...)`**
    *   **Purpose:** Communicates with the "Performance Watchdog" to request a temporary exemption for computationally expensive tasks.
    *   **Best Practice:** ALWAYS use this in a `try...finally` block!

<div class="note">
<strong>Missing an interface?</strong><br>
Do you have an idea for a new function the host should provide? Fantastic! We want the API to grow with the needs of the community. Create an issue on GitHub, tag it with <code>api-suggestion</code>, and describe what interface you're dreaming of and what you want to build with it. Let's make the API better together!
</div>

---

## Chapter 5: Advanced Concepts & Best Practices

### The Addon Lifecycle
1.  **Loading:** The `AddonManager` finds your DLL.
2.  **Instantiation:** An instance of your `IAddon` class is created.
3.  **Initialization:** `Initialize(host)` is called. Your addon is now "alive".
4.  **Operation:** The core calls methods like `GetMainMenuButtons()` or `Draw()` as needed.
5.  **Shutdown:** When the addon is unloaded, `Shutdown()` is called.

### Licensing for Premium Addons: A Guided Process
Want to develop an addon that is exclusively available to certain Patreon supporter tiers? The SCOverlay system is designed for this. However, licensing is a **collaborative process** to ensure a secure and fair system for everyone.

**You cannot invent a `LicenseId` yourself.** Each `LicenseId` must be generated by the SCOverlay core team and integrated into the core application.

**The process is as follows:**
1.  **Develop Your Addon:** First, focus entirely on developing your addon. You can test it without the `[Addon]` attribute for now.
2.  **Contact Us:** When your addon is finished or in an advanced stage, contact the **creator (BlugDeg)** to present your project. The best way is to create a new issue on GitHub.
3.  **Alignment & Creation:** We will work with you to finalize the model. The creator will then:
    *   Create a new, unique **`LicenseId`** for your addon on the license server.
    *   Integrate this `LicenseId` into the **SCOverlay core application** code.
4.  **Integration into Your Addon:** Once the new version of SCOverlay containing your `LicenseId` is released, you will receive the official ID from us. Only then do you add the attribute to your addon class.
    ```csharp
    // Example: You received the ID "MySuperAddon" from the creator.
    [Addon(LicenseId = "MySuperAddon")]
    public class MyPremiumAddon : IAddon { /* ... Your addon code ... */ }
    ```

### Dos & Don'ts: Avoiding Common Mistakes
-   ✅ **Release Resources:** Implement `IDisposable` for custom windows and call `Dispose()` in your `Shutdown()` method.
-   ✅ **Unsubscribe from Events:** Always unsubscribe from events like `_host.OnPaintOverlay` in `Shutdown()` to prevent memory leaks.
-   ❌ **Never Block `Draw()`:** Do not perform file operations, network access, or long loops in the `Draw` method.
-   ❌ **Don't Assume a UI Thread:** Use `myWindow.BeginInvoke(...)` to safely update UI elements from other threads.

---

## Chapter 6: Troubleshooting & Common Pitfalls

We want you to succeed. Here are the most common stumbling blocks and how to quickly get past them.

### Problem: "My addon doesn't appear in the menu!"
1.  **Incorrect Folder/File Structure:**
    *   **Solution:** The folder in `%AppData%\SCOverlay\addons` must have the **exact** same name as your DLL.
2.  **"Copy Local" is set to "True".**
    *   **Solution:** In Visual Studio, set the **"Copy Local"** property for the `SCOverlay.API` reference to **"No" (False)**.
3.  **Your addon throws an error on startup.**
    *   **Solution:** Check the `debug.log` (`%AppData%\SCOverlay\debug.log`). An error in your `Initialize` method will cause the loading process to be aborted.

### Problem: "My button text (or other UI change) isn't updating!"
*   **Cause:** You haven't told the overlay that it needs to redraw itself.
*   **Solution:** **Always** call `_host?.InvalidateOverlay();` after changing a state that affects the display.

### Problem: "I'm getting a 'Cross-thread operation not valid' exception."
*   **Cause:** You are trying to modify a UI element from a thread other than the one that created it.
*   **Solution:** Use `BeginInvoke` to safely marshal the call to the UI thread.
    ```csharp
    myLabel.BeginInvoke((Action)(() => { myLabel.Text = "New Text"; }));
    ```

### Problem: "My addon suddenly disappears during use!"
*   **Cause:** The **Performance Watchdog** has struck. Your addon caused excessive CPU load for an extended period and was automatically unloaded to protect the gaming experience.
*   **Solution:** If the load is short and intentional, wrap it in a `RequestHighPerformanceMode` block. If it's unintentional, optimize your code (especially the `Draw()` method).

<div class="note">
<strong>Pro-Tip: Your Personal Code Assistant</strong><br>
You can copy this entire manual, or parts of it, and paste it into a modern AI like Gemini or ChatGPT. Describe your problem or what you want to build, and the AI can generate precise code examples and solutions for your specific issue based on the information in this guide. Use it as your personal assistant!
</div>

---

## Chapter 7: Become Part of the Development!

**Your contribution is valuable.** Whether you're an experienced developer or just starting, your ideas and your help are welcome.

### Where to Find Help
We know that getting started can sometimes be bumpy. Never hesitate to ask for help!

➡️ **[Ask a question in the `developer-need-help` channel](https://github.com/BlugDeg/SCOverlay-Updates/issues/new?labels=developer-need-help)**
Simply create a new issue with the **`developer-need-help`** label. Someone from the team or community will get back to you as soon as possible.

### Shape the Future of the API!
This API is a living tool meant to evolve. If you're developing and think, "Man, if only the host had THIS function, I could build something amazing...", then you're exactly the person we're looking for!

➡️ **[Suggest a new API feature](https://github.com/BlugDeg/SCOverlay-Updates/issues/new?labels=api-suggestion)**
Share your thoughts by creating an issue with the **`api-suggestion`** label.

### Propose a Licensed Addon
Have you developed a premium addon and want to request an official `LicenseId`? Fantastic!

➡️ **[Request a new License ID](https://github.com/BlugDeg/SCOverlay-Updates/issues/new?labels=licensing-request)**
Create an issue with the **`licensing-request`** label and introduce us to your project. We will then contact you to discuss the next steps.

**We're excited to see what you create!**