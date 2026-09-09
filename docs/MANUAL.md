<p align="center">
<!-- Readme Links -->
<a href="README.md"><img src="https://img.shields.io/badge/Readme-555?style=for-the-badge" alt="Readme"></a><!--
--><a href="README.md"><img src="https://img.shields.io/badge/EN-555?style=for-the-badge" alt="English"></a><!--
--><a href="README.de.md"><img src="https://img.shields.io/badge/DE-555?style=for-the-badge" alt="Deutsch"></a>
&nbsp;&nbsp;|&nbsp;&nbsp;
<!-- Manual Links -->
<a href="MANUAL.md"><img src="https://img.shields.io/badge/Manual-007bff?style=for-the-badge" alt="Manual"></a><!--
--><a href="MANUAL.md"><img src="https://img.shields.io/badge/EN-ff6f00?style=for-the-badge" alt="English"></a><!--
--><a href="MANUAL.de.md"><img src="https://img.shields.io/badge/DE-555?style=for-the-badge" alt="Deutsch"></a>
&nbsp;&nbsp;|&nbsp;&nbsp;
<!-- Developer/SDK Links -->
<a href="SDK_MANUAL.md"><img src="https://img.shields.io/badge/Developer-555?style=for-the-badge" alt="Developer"></a><!--
--><a href="SDK_MANUAL.md"><img src="https://img.shields.io/badge/EN-555?style=for-the-badge" alt="English"></a><!--
--><a href="SDK_MANUAL.de.md"><img src="https://img.shields.io/badge/DE-555?style=for-the-badge" alt="Deutsch"></a>
</p>

<h1 align="center">SCOverlay User Manual</h1>

<p align="center">
  <strong>Installing, configuring and using SCOverlay and its add-ons.</strong>
  <br>
  Written for SCOverlay 0.0.5.x.
</p>

---

## Table of Contents

1.  [**Installation & First Launch**](#1-installation--first-launch)
2.  [**Basic Controls**](#2-basic-controls)
3.  [**Settings**](#3-settings)
4.  [**The Add-on Gallery**](#4-the-add-on-gallery)
5.  [**Add-on Guides**](#5-add-on-guides)
    *   [ExecTimer](#exectimer-the-hangar-timer)
    *   [QuickSheets](#quicksheets-your-in-game-image-viewer)
    *   [The other add-ons](#the-other-add-ons)
6.  [**Updates**](#6-updates)
7.  [**Troubleshooting & FAQ**](#7-troubleshooting--faq)

---

## 1. Installation & First Launch

**Step 1: Download**
-   ➡️ Get the newest installer from the website: **https://scoverlay.it-en.ch/download/core** (the link always points at the current version).
-   ✔️ Windows SmartScreen will show a warning, because the installer is not code-signed. Click *More info → Run anyway*. If you want to check the file first, [SECURITY.md](../SECURITY.md) shows how to compare its SHA-256 with the published one.

**Step 2: Install**
-   ➡️ Run the installer and click through it.
-   ✔️ It asks where Star Citizen is installed. Choose the `LIVE` folder (for example `C:\Program Files\Roberts Space Industries\StarCitizen\LIVE`). Add-ons use this to find `Game.log` and the game's text files. If you skip it, SCOverlay asks again on first launch, and you can change it any time under *Settings → General*.

**Step 3: First launch**
-   ➡️ Start SCOverlay from the Start menu or desktop shortcut.
-   ✔️ Nothing big opens. SCOverlay lives in the **system tray**, the area with the small icons next to the clock. A right-click on its icon shows the menu (settings, exit).
-   ✔️ On the very first start SCOverlay offers to install the default add-ons (ExecTimer, QuickSheets, a demo). Click **Yes**; they are downloaded, verified and set up, and SCOverlay restarts.

That's it. Launch Star Citizen and read on.

## 2. Basic Controls

-   **Open / close the overlay:** <kbd>Shift</kbd> + <kbd>F10</kbd> by default. Press once to show the panel, again to hide it. You can rebind it under *Settings → Shortcuts*.
-   **The panel:** one tile per add-on. Click a tile to open that add-on's menu or window. The footer has the hotkey overview on the left and the *Gallery* and *Settings* buttons on the right.
-   **If the hotkey doesn't reach the game:** turn on the *ScrollLock fallback* under *Settings → Shortcuts*. Then a **double-tap on <kbd>Scroll Lock</kbd>** opens the overlay; that works even in games that swallow other combinations.
-   **Add-on hotkeys:** many add-ons have their own hotkey (listed in section 5 and under *Settings → Shortcuts*, where all of them can be rebound).

## 3. Settings

Open the overlay and click **Settings** in the footer.

-   **General**
    *   `Language`: English (default) or German. Takes effect immediately for the core; an add-on window that is already open picks it up when you open it next.
    *   `Star Citizen folder`: where the game is installed. Change it here if you play on PTU or moved the game.
    *   `Start with Windows` and `Show overlay on start`: off by default. With the second one off, SCOverlay starts quietly in the tray and waits for the hotkey.
    *   `Unlock Window`: lets you drag and resize the overlay. Lock it again when you're happy with the position.
    *   `Connection`: shows when the website was last reached. This is the same connection the updater uses.
    *   `Support the project`: opens the donation page in your browser.
-   **Display**
    *   `Overlay width / height`: size of the panel in percent of the screen.
    *   `Tile size`: 60–200 %. Tiles keep this size no matter how large the panel is; a bigger panel shows more tiles, not bigger ones.
    *   `Theme` and colours.
-   **Shortcuts**
    *   `Toggle hotkey`: click *Rebind* and press your combination.
    *   `ScrollLock fallback`: see section 2.
    *   Every add-on hotkey, with a short description of what it does.
-   **Audio**: which input and output device SCOverlay uses for the sounds add-ons play.
-   **Advanced**: tray icon on/off, the *Enable Debug Log* switch (turn it on before reporting a bug), *Open Data Folder* and a *Bug Report* shortcut.
-   **Addons** (button in the settings): the list of installed add-ons with their versions, enable/disable per add-on, and *Install Addon from .zip* for a package you got outside the Gallery.

## 4. The Add-on Gallery

Click **Gallery** in the footer of the main panel. Each card shows an add-on with its description, author and version.

-   **Install** downloads the add-on, verifies it and puts it in place. A strip at the top then asks you to **restart** SCOverlay: add-ons are loaded once at startup.
-   **Enable / Disable** switches an installed add-on off without removing it. Also needs a restart.
-   **Remove** deletes the add-on's folder. If SCOverlay still has the add-on loaded, the removal fails with a message; disable it, restart, then remove.
-   Clicking the picture or text of a card opens the add-on's page on the website in your browser.

The same add-ons are listed on the website: https://scoverlay.it-en.ch/gallery

Every add-on in the Gallery is built and published by the SCOverlay maintainer from source he holds. What that means for you, and what it doesn't, is spelled out in [SECURITY.md](../SECURITY.md).

## 5. Add-on Guides

### ExecTimer: The Hangar Timer

-   **At a glance:** a countdown for the Executive Hangar cycle in Pyro, as a small HUD in a corner of your screen. It shows the five lamps, the current state (`HANGAR OPEN`, `HANGAR RESET`, `HANGAR CLOSED`) and the time to the next change.
-   **HUD mode** (in the add-on's menu): `Off`, `Always`, or `With overlay` (visible only while the main panel is open). The HUD is click-through, so it never gets in the way of the game.
-   **Corner:** pick one of the four screen corners.
-   **Pre-warning:** a sound a few minutes before the hangar opens (default 5 min). You can change the lead time, the volume and the sound file.
-   **Where the timing comes from:** the cycle anchor is synced from the website, because the hangar cycle shifts with every server restart and patch. If the timer is off by minutes after a patch, that is the anchor being corrected; it catches up on its own.
-   The **?** button in the add-on opens its own help window.

### QuickSheets: Your In-Game Image Viewer

-   **At a glance:** show your own images (trade maps, mining guides, keybind charts) in windows over the game. Three StormBreaker sheets are included.
-   **Adding your own sheets:**
    1.  Press <kbd>Win</kbd> + <kbd>R</kbd>, paste `%appdata%\SCOverlay\addons\QuickSheetAddon\sheets` and press Enter.
    2.  Put `.png` or `.jpg` files in that folder. Sub-folders become sub-menus, so you can sort them (`Mining`, `Trading`, …).
    3.  A folder that contains exactly one image named like the folder opens that image directly instead of showing a sub-menu.
    4.  Restart SCOverlay; the menu is built at startup.
-   **The sheet window:** zoom with the mouse wheel or the `−` / `+` / `FIT` buttons, drag the image around, `PIN` keeps the window visible while the main panel is closed (`WIN` hides it with the panel), and the button on the far right switches to fullscreen and back.

### The other add-ons

Each of these has its own window and, mostly, its own help page inside. Hotkeys are the defaults and can be rebound under *Settings → Shortcuts*.

| Add-on | What it does | Hotkey |
|---|---|---|
| **Wingman** | Accepts missions that party members share, automatically. Turn it on before you play; it starts off on every launch so it never presses a key you didn't expect. Missions can be blacklisted. | <kbd>Shift</kbd> + <kbd>Ü</kbd> toggles it |
| **Omnia** | Search everything the game knows: planets, moons, stations, ships, items, missions, prices with age. | <kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>L</kbd> main window, <kbd>Shift</kbd> + <kbd>F5</kbd> quick search |
| **OreScout** | Mining reference: ore → signature, location → ores, cluster value → ore and rock count. Optional HUD with your marked ores. | <kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>O</kbd> |
| **Workbench** | Blueprints: which exist, which you own (read from your logs), ingredients, salvage yield, and a value calculator. | <kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>B</kbd> |
| **OrgaStorage** | Shared spreadsheets for your org. Pair the add-on with your website account once (a six-character code, entered at https://scoverlay.it-en.ch/verbinden). | <kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>G</kbd> |
| **MouseMover** | Warns you when you've been idle and then moves the mouse so the game doesn't kick you. Set the idle threshold in its menu. | <kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>M</kbd> toggles it |
| **RepTracker** | Measure the reputation bar in the mobiGlas per contract and see what each mission is worth. A setup wizard guides the first measurement. | via its tile |
| **CitizenHauler** | Trading companion with live UEX Corp data, route planning and route guidance. | via its tile |
| **BetterPicture** | Photo mode with high-quality screenshots and a colour filter overlay. | via its tile |

## 6. Updates

-   **At start** SCOverlay asks the website for new versions of the core and of every installed add-on. If there is one, a dialog offers to install it now.
-   **While you play** it checks again every two hours. A new version is only announced with a small toast; nothing is installed mid-game. It's installed at the next start.
-   Every download is verified against its published SHA-256 before it's unpacked. A download that doesn't match is deleted.
-   Nothing is ever downloaded without you confirming it.

## 7. Troubleshooting & FAQ

-   **Q: SmartScreen or my antivirus warns about SCOverlay. Is it safe?**
    *   **A:** SCOverlay is not code-signed, so SmartScreen warns on every new version; that's expected and not a verdict on the file. What you *can* check is that the file is the one the website published: compare its SHA-256 with the value in `https://scoverlay.it-en.ch/api/updates/core` (the steps are in [SECURITY.md](../SECURITY.md)). Antivirus heuristics sometimes flag the global hotkey listener; the same document explains exactly what it does and why. If you don't want to trust that, don't run it; that's a legitimate choice.
-   **Q: The hotkey does nothing in the game.**
    *   **A:** Turn on the *ScrollLock fallback* under *Settings → Shortcuts* and double-tap <kbd>Scroll Lock</kbd>. Also make sure the combination isn't bound in the game.
-   **Q: Where are my settings and add-on data?**
    *   **A:** In `%appdata%\SCOverlay`. Settings are in `settings.json`, the log in `debug.log`, add-ons in `addons\`.
-   **Q: I moved Star Citizen / I play on PTU.**
    *   **A:** Change the folder under *Settings → General*. Add-ons that read `Game.log` follow it immediately.
-   **Q: An add-on has disappeared from the menu.**
    *   **A:** Look in `debug.log` for its name. Either it failed to load (a version mismatch after an update is the usual cause; reinstall it from the Gallery) or the Performance Watchdog unloaded it because it stalled the overlay.
-   **Q: How do I remove an add-on completely?**
    *   **A:** Gallery → *Remove*, or delete its folder under `%appdata%\SCOverlay\addons\` while SCOverlay is not running.
-   **Q: How do I get support?**
    *   **A:** Open an issue on GitHub: **https://github.com/BlugDeg/SCOverlay-Updates/issues**. German is as welcome as English. Attach the relevant lines from `debug.log`.
