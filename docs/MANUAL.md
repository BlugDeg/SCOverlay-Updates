<p align="center">
  <!-- Readme Links -->
  <a href="README.md"><img src="https://img.shields.io/badge/Readme-007bff?style=for-the-badge" alt="Readme"></a><!--
  --><a href="README.md"><img src="https://img.shields.io/badge/EN-007bff?style=for-the-badge" alt="English"></a><!--
  --><a href="README.de.md"><img src="https://img.shields.io/badge/DE-555?style=for-the-badge" alt="Deutsch"></a>
  &nbsp;&nbsp;|&nbsp;&nbsp;
  <!-- Manual Links -->
  <a href="MANUAL.md"><img src="https://img.shields.io/badge/Manual-555?style=for-the-badge" alt="Manual"></a><!--
  --><a href="MANUAL.md"><img src="https://img.shields.io/badge/EN-555?style=for-the-badge" alt="English"></a><!--
  --><a href="MANUAL.de.md"><img src="https://img.shields.io/badge/DE-555?style=for-the-badge" alt="Deutsch"></a>
  &nbsp;&nbsp;|&nbsp;&nbsp;
  <!-- Developer/SDK Links -->
  <a href="SDK_MANUAL.md"><img src="https://img.shields.io/badge/Developer-555?style=for-the-badge" alt="Developer"></a><!--
  --><a href="SDK_MANUAL.md"><img src="https://img.shields.io/badge/EN-555?style=for-the-badge" alt="English"></a><!--
  --><a href="SDK_MANUAL.de.md"><img src="https://img.shields.io/badge/DE-555?style=for-the-badge" alt="Deutsch"></a>
</p>

<h1 align="center">SCOverlay User Manual</h1>
<p align="center">Your complete guide to installing, configuring, and mastering SCOverlay, written for everyone.</p>

---

## Table of Contents

1.  [**Installation & First Launch**](#1-installation--first-launch)
2.  [**Basic Controls: Your First Steps In-Game**](#2-basic-controls-your-first-steps-in-game)
3.  [**The Main Settings Panel Explained**](#3-the-main-settings-panel-explained)
4.  [**Addon Guides: Mastering Your Tools**](#4-addon-guides-mastering-your-tools)
    *   [ExecTimer: The Hangar Timer](#exectimer-the-hangar-timer)
    *   [QuickSheets: Your In-Game Image Viewer](#quicksheets-your-in-game-image-viewer)
    *   [SpyCitizen: The Intelligence Monitor](#spycitizen-the-intelligence-monitor)
5.  [**Troubleshooting & FAQ**](#5-troubleshooting--faq)

---

## 1. Installation & First Launch

Welcome aboard, Citizen! Let's get you set up in a few simple steps.

**Step 1: Download & Install**
-   ➡️ Use the download link from your Patreon welcome email to get the installer (`SCOverlay-Setup-vX.Y.Z.exe`).
-   ✔️ Run the installer. It's a standard process; you can safely click "Next" until it's finished.

**Step 2: Launch and Find the Tray Icon**
-   ➡️ Start SCOverlay using the new shortcut on your desktop.
-   ✔️ The application runs in the background. You won't see a big window pop up. Instead, a new icon will appear in your **System Tray**. The System Tray is the area with the small icons near your clock, usually at the bottom-right of your screen.

**Step 3: Activate Your License**
-   ➡️ The very first time you launch SCOverlay, an activation window will appear.
-   ✔️ Find your Patreon welcome email and copy the **License Key**. It's a long string of characters.
-   ➡️ Paste the key into the activation window and click "Activate".

**Step 4: Automatic Addon Installation**
-   ✔️ After activation, SCOverlay might show a pop-up asking if you want to install missing default addons (like ExecTimer). **Click "Yes"**.
-   ✔️ The program will quickly download and set up these essential tools for you. It will then restart itself automatically.

You are now fully installed and ready to go!

## 2. Basic Controls: Your First Steps In-Game

With SCOverlay running in the background, launch Star Citizen.

-   **Open/Close the Overlay:** Press <kbd>Shift</kbd> + <kbd>F10</kbd>. This is your main command. Press it to show the overlay, press it again to hide it.

-   **Moving and Resizing the Window:**
    1.  Press <kbd>Shift</kbd> + <kbd>F10</kbd> to open the overlay.
    2.  Click the **"Settings"** button at the bottom of the menu.
    3.  In the "General" tab, find the **"Unlock Window"** option and click the button next to it to switch it to **"On"**.
    4.  Now you can drag the window around with your mouse and resize it by pulling on its edges, just like any other window.
    5.  Once you have it positioned perfectly, it's a good idea to lock it again to prevent accidental moves.

-   **The Lifesaver Hotkey:** If <kbd>Shift</kbd> + <kbd>F10</kbd> ever seems to not work (sometimes games can be tricky), just **double-tap the <kbd>Scroll Lock</kbd> key** on your keyboard. This is a reliable backup that will always work.

## 3. The Main Settings Panel Explained

This is your command center for customizing the overlay itself.

-   **General Tab:**
    *   `Language`: Switch between English and German. The change is instant.
    *   `Unlock Window`: Think of this as "Edit Mode" for the window's position and size.

-   **Display Tab:**
    *   `Overlay Width / Height`: Fine-tune the window size.
    *   `Reset Position`: Lost the window off-screen? This button brings it back to the center.
    *   `Theme`: Change the look and feel. `DarkSilver` and `RedShock` are presets. `Custom` lets you pick your own colors!

-   **Shortcuts Tab:**
    *   `Toggle Hotkey`: Click **"Rebind"** to set your preferred hotkey combination. Choose something that doesn't conflict with your game controls!

## 4. Addon Guides: Mastering Your Tools

### ExecTimer: The Hangar Timer

-   **At a Glance:** A super-accurate timer that tells you exactly when the valuable Executive Hangars open and close.
-   **How to Use:**
    1.  Open the overlay and click the **"ExecTimer"** button to enter its menu.
    2.  Click **"Show Timer"** to open the separate timer window. You can drag this window anywhere on your screen.
-   **The `PIN` / `WIN` Button (Very Important!):**
    *   **`PIN` (Pinned Mode):** The timer is "glued" to your screen. It stays visible **even when you hide the main overlay**. This is perfect for active gameplay.
    *   **`WIN` (Window Mode):** The timer acts like a normal part of the overlay. It disappears when you hide the main panel and reappears when you open it.
-   **Sounds & Alerts:** ExecTimer comes with a default sound that plays when the hangar opens. In its settings menu, you can change the volume, or even select your own custom `.wav` sound file!

### QuickSheets: Your In-Game Image Viewer

-   **At a Glance:** Display any image from your computer (like a trade route map, mining guide, or keybinds chart) as a window inside the game.
-   **How to Add Your Images (The Easy Way):**
    1.  Press the <kbd>Windows Key</kbd> + <kbd>R</kbd> to open the "Run" dialog.
    2.  Type exactly this and press Enter: `%appdata%\SCOverlay\addons\QuickSheet`
    3.  A folder will open. Inside this folder, create a **new folder** and name it `sheets`.
    4.  Place any `.png` or `.jpg` image files you want into this `sheets` folder. You can even create sub-folders inside `sheets` to organize them (e.g., `Mining`, `Trading`).
-   **How to Use:** In the overlay menu, click **"Quicksheets"**. You will see a menu that perfectly matches the folders and files you created. Click any item to open the image in its own resizable window. Each sheet window also has its own `PIN`/`WIN` button!

### SpyCitizen: The Intelligence Monitor

-   **At a Glance:** Your personal intelligence agent that reads the Star Citizen log file to give you a tactical advantage, tracking who is on your server and your combat performance.

> **⚠️ IMPORTANT FIRST STEPS**
> SpyCitizen needs to be configured to work. This is the most important part!
> 1.  Open the overlay, then go to `SpyCitizen -> Settings -> Account`.
> 2.  **Set Log Path:** Click **"Set Game.log Path"**. You must find and select the `Game.log` file for Star Citizen. It's usually located in: `C:\Program Files\Roberts Space Industries\StarCitizen\LIVE`.
> 3.  **Set Your Name:** Click **"Set In-game Name"**. Enter your character's name **exactly** as it appears in-game. This is required for tracking your kills and deaths correctly.

-   **Features:**
    *   **Monitor Window:** A powerful window with views for players on your current server (`Players Today`), all players you've ever seen (`History`), and detailed logs of your kills and deaths.
    *   **HUD Alerts:** Get a simple on-screen notification when a new player joins the server, so you're never caught by surprise.
    *   **Sound Alerts:** Want a special sound to play when a known hostile player appears? You can set that up in `Settings -> Sounds`.
-   **Pro-Tip: Using the Included Sounds:** SCOverlay comes with some ready-to-use alert sounds! When setting a sound for a category (like "Hostile"), you can navigate to this folder and pick one: `%appdata%\SCOverlay\Resources`

## 5. Troubleshooting & FAQ

-   **Q: My antivirus is warning me about SCOverlay. Is it a virus?**
    *   **A:** No, it is **100% safe**. SCOverlay uses low-level keyboard hooks to make its hotkeys work reliably. Some antivirus programs see this behavior and flag it as suspicious (a "false positive"). You can safely tell your antivirus to allow SCOverlay.
-   **Q: Where are all the settings and addon data stored?**
    *   **A:** Everything is located in `%appdata%\SCOverlay`. This is where settings are saved and where you can place files for addons like QuickSheets.
-   **Q: How do I get support?**
    *   **A:** The best way is to visit our **[GitHub Issue Council](https://github.com/BlugDeg/SCOverlay-Updates/issues)** and describe your problem.
