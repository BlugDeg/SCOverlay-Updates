<p align="center">
  <a href="README.md"><img src="https://img.shields.io/badge/USER-README-007bff?style=flat-square" alt="User Readme"></a><!--
  --><a href="README.de.md"><img src="https://img.shields.io/badge/BENUTZER-LIESMICH-555?style=flat-square" alt="Benutzer Liesmich"></a><!--
  --><a href="SDK_MANUAL.md"><img src="https://img.shields.io/badge/DEVELOPER-EN-ff6f00?style=flat-square" alt="Developer EN"></a><!--
  --><a href="SDK_MANUAL.de.md"><img src="https://img.shields.io/badge/ENTWICKLER-DE-555?style=flat-square" alt="Entwickler DE"></a>
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
  A modular, high-performance in-game overlay for Star Citizen, extensible through a powerful addon system.
</p>

<!-- Badges -->
<p align="center">
  <a href="LICENSE"><img src="https://img.shields.io/github/license/DEIN-GITHUB-USERNAME/DEIN-REPO-NAME" alt="License"></a>
  <a href="https://www.patreon.com/cw/BlugDeg"><img src="https://img.shields.io/badge/patreon-become a patron-orange" alt="Patreon"></a>
  <a href="#"><img src="https://img.shields.io/badge/status-active-brightgreen" alt="Status"></a>
</p>

---

## 🔑 Access & Licensing

SCOverlay is a supporter-driven project. Access to the software, its updates, and your personal license key is granted through a **Patreon membership**. Your support directly contributes to the ongoing development and maintenance of this platform.

**How to get SCOverlay:**

1.  **Become a Patron:** Visit our Patreon page and choose a membership tier.
    <br>➡️ **[https://www.patreon.com/cw/BlugDeg](https://www.patreon.com/cw/BlugDeg)**

2.  **Check Your Email:** After joining, you will receive an email containing:
    *   Your personal **license key** to activate the software.
    *   A **download link** for the latest version of the SCOverlay installer and its addons.

## 🚀 Installation & Quick Start

1.  Run the `SCOverlay-Setup-vX.Y.Z.exe` you received via email.
2.  Start SCOverlay and activate it with the license key from your email.
3.  Press the default hotkey <kbd>Shift</kbd> + <kbd>F10</kbd> to open or close the overlay in-game.
4.  To move or resize the window, go to `Settings -> General` and switch "Unlock Window" to "On".

## ✨ Core Features

- 🚀 **Extensible Addon Architecture:** The heart of SCOverlay. A clean and stable API (`SCOverlay.API`) allows developers to easily create and integrate new features.
- ⚡ **Performance First:** A built-in "Performance Watchdog" continuously monitors system load to prevent frame drops. Resource-intensive addon operations can request a temporary exemption.
- 🎨 **Customizable UI:** The overlay window can be freely moved, resized, and styled with different themes.
- ⌨️ **Robust Hotkey System:** Uses low-level keyboard hooks to function reliably even in demanding game scenarios, including a fail-safe "Scroll Lock Fallback" mechanism.
- 🔄 **Integrated Updater:** The core application and all installed addons can receive updates directly to stay up-to-date.

## 🧩 Included Addons

SCOverlay comes with a set of powerful addons. Some are standard and included for all members, while others are premium addons that may require a specific license tied to your Patreon tier.

- **ExecTimer** (Standard): A precise, network-synchronized timer for the Executive Hangars, complete with customizable sound and visual alerts.
- **QuickSheets** (Standard): Allows you to display your own images (checklists, trade routes, etc.) as floating, pinnable windows in-game.
- **SpyCitizen** (🔑 Licensed): A powerful intelligence tool that parses the `Game.log` file in real-time to track players, record combat events, and maintain detailed statistics.

## 💬 Support, Feedback, and Ideas

Have a question, found a bug, or have a great idea for a new feature? The best way to reach us is through our GitHub Issue Council.

➡️ **[Open an Issue on GitHub](https://github.com/DEIN-GITHUB-USERNAME/DEIN-REPO-NAME/issues)**

Please use the appropriate tags (e.g., `bug`, `feature-request`, `question`) to help us organize feedback.

## 👨‍💻 For Developers

Interested in creating your own addon for SCOverlay? The API is designed to make it as easy as possible. Check out our comprehensive **[Developer SDK Manual](docs/SDK_MANUAL.md)** to get started.

## 🤝 How to Contribute

Contributions are always welcome! Please read our [**Contribution Guidelines (CONTRIBUTING.md)**](CONTRIBUTING.md). We also expect all contributors to abide by our [**Code of Conduct**](CODE_OF_CONDUCT.md).

## 📄 License

The source code of this project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

Please note that while the source code is open, using the compiled, ready-to-use application requires an active license obtained via Patreon.