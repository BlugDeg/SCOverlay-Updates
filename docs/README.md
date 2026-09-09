<p align="center">
  <!-- Readme Links -->
  <a href="README.md"><img src="https://img.shields.io/badge/Readme-007bff?style=for-the-badge" alt="Readme"></a><!--
  --><a href="README.md"><img src="https://img.shields.io/badge/EN-ff6f00?style=for-the-badge" alt="English"></a><!--
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

<!-- Header: Logo, Title, and Tagline -->
<p align="center">
  <svg width="150" height="150" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
    <path d="M12 21C16.9706 21 21 16.9706 21 12C21 7.02944 16.9706 3 12 3C7.02944 3 3 7.02944 3 12C3 16.9706 7.02944 21 12 21Z" stroke="#4a90e2" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" opacity="0.4"/>
    <path d="M12 17V12" stroke="#4a90e2" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
    <path d="M12 3C12 3 15 6 15 9C15 12 12 17 12 17" stroke="#4a90e2" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
    <path d="M12 3C12 3 9 6 9 9C9 12 12 17 12 17" stroke="#4a90e2" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
  </svg>
</p>

<h1 align="center">SCOverlay</h1>

<p align="center">
  <strong>Your modular cockpit assistant for Star Citizen.</strong>
  <br>
  A free, lightweight in-game overlay that you extend with add-ons.
</p>

<!-- Badges -->
<p align="center">
  <a href="https://scoverlay.it-en.ch/"><img src="https://img.shields.io/badge/Website-scoverlay.it--en.ch-007bff" alt="Website"></a>
  <a href="https://scoverlay.it-en.ch/download/core"><img src="https://img.shields.io/badge/Download-latest%20installer-brightgreen" alt="Download"></a>
  <a href="https://scoverlay.it-en.ch/donate"><img src="https://img.shields.io/badge/Donate-support%20the%20project-orange" alt="Donate"></a>
  <a href="../SECURITY.md"><img src="https://img.shields.io/badge/Security-what%20it%20does%20on%20your%20PC-555" alt="Security"></a>
  <a href="../LICENSE.md"><img src="https://img.shields.io/badge/License-free%20of%20charge-555" alt="License"></a>
</p>

---

## What is SCOverlay?

SCOverlay is a small Windows application that draws a menu over Star Citizen. Press a hotkey in the game and a panel of tiles appears, one per add-on: a hangar timer, cheat sheets, a mining reference, a game lexicon, reputation tracking, shared spreadsheets for your org, and more. Press the hotkey again and it is gone.

The core only provides the window, the hotkeys, the settings and the update system. Everything you actually use is an **add-on**, and add-ons are installed, updated and switched on or off from inside the overlay.

## Free, funded by donations

There is no licence key, no account and no subscription. Download it, install it, play. If SCOverlay is useful to you, you can support its development on the website: **https://scoverlay.it-en.ch/donate**

## Key features

- **Add-on platform.** A stable, documented API; each add-on is its own DLL. See the [SDK manual](SDK_MANUAL.md) if you want to build one.
- **In-app Gallery.** Browse, install, enable, disable and remove add-ons without leaving the game.
- **Automatic updates** for the core and every add-on. Every download is verified against its published SHA-256 before anything is installed; a download only starts after you confirm it.
- **Global hotkeys** that work over the fullscreen game. Default toggle: <kbd>Shift</kbd> + <kbd>F10</kbd>, rebindable.
- **Performance Watchdog.** An add-on that stalls the overlay is unloaded instead of costing you frames.
- **Bilingual.** English and German, switchable in the settings.
- **No telemetry, no accounts.** What the application does on your PC is written down in [SECURITY.md](../SECURITY.md).

## Download and install

1. **Download the newest installer:** https://scoverlay.it-en.ch/download/core
   The website is the source of truth. The releases on this GitHub page are a mirror that older installations still use for their update check; they may lag behind.
2. **Run the installer.** It asks where Star Citizen is installed (the `LIVE` folder) so add-ons can find `Game.log`. You can skip that and set it later under *Settings → General*.
3. **Windows SmartScreen will warn you.** The installer is not code-signed (see [SECURITY.md](../SECURITY.md) for why, and for how to verify the download's hash instead). Choose *More info → Run anyway*.
4. **Start SCOverlay.** It lives in the system tray. Launch Star Citizen and press <kbd>Shift</kbd> + <kbd>F10</kbd>.

The [user manual](MANUAL.md) walks through the first launch, the settings and every bundled add-on.

## Add-ons

All add-ons below are available from the Gallery inside the overlay and on the [website](https://scoverlay.it-en.ch/gallery).

| Add-on | What it does |
|---|---|
| **ExecTimer** | Countdown for the Executive Hangar cycle in Pyro, as a small HUD in a screen corner, with a pre-warning sound. |
| **QuickSheets** | Shows your own images (maps, guides, keybind charts) in zoomable windows over the game. Folders become menus. |
| **Wingman** | Accepts missions that party members share, automatically, in the one or two seconds the game gives you. |
| **Omnia** | The Star Citizen lexicon: one search box over planets, stations, ships, items, missions, prices. Quick search with <kbd>Shift</kbd> + <kbd>F5</kbd>. |
| **OreScout** | Mining reference: ore to scanner signature, location to ores, and a cluster value back to ore and rock count. |
| **Workbench** | Crafting: which blueprints exist, which you own (from your logs), what a blueprint needs and what it yields when broken down, with a value calculator. |
| **RepTracker** | Turns the mobiGlas reputation bar into numbers: measure it per contract and see what each mission is worth. |
| **OrgaStorage** | Shared spreadsheets for your organisation, edited by several members at once, with formulas. |
| **MouseMover** | Notices when you are idle, warns you, then moves the mouse so the game does not kick you for inactivity. |
| **CitizenHauler** | Trading companion with live UEX Corp data, route planning and a Datarunner mode. |
| **BetterPicture** | Photo mode: high-quality screenshots (RAW, 16-bit) with a colour filter overlay. |

## Security and trust

The core is closed source. So that you do not have to take that on faith, [SECURITY.md](../SECURITY.md) lists exactly which hosts the application contacts, which files it writes, what its input listener does and how the add-on trust model works, in a form you can verify with a firewall or Process Monitor. It also states plainly what is not there: no code signing, no independent audit, no add-on sandbox.

## Documentation

- [User manual](MANUAL.md) (English) · [Benutzerhandbuch](MANUAL.de.md) (Deutsch)
- [SDK manual](SDK_MANUAL.md) for add-on developers (English) · [SDK-Handbuch](SDK_MANUAL.de.md) (Deutsch)
- [Security and privacy](../SECURITY.md) (English) · [Sicherheit und Datenschutz](../SECURITY.de.md) (Deutsch)
- [Patch notes](https://scoverlay.it-en.ch/patchnotes) on the website

## Get involved

- **Found a bug or have an idea?** Open an [issue](https://github.com/BlugDeg/SCOverlay-Updates/issues). German is as welcome as English.
- **Want to build an add-on?** The [SDK manual](SDK_MANUAL.md) takes you from an empty project to a working tile in a few minutes. An add-on is your work and stays yours.

## License

SCOverlay is free of charge under a proprietary licence: use it freely, do not redistribute or modify the application itself. Add-ons you write belong to you. Full text in [LICENSE.md](../LICENSE.md).
