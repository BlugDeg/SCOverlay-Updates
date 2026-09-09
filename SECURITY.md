# Security and Privacy

*Last reviewed: 9 September 2026, against SCOverlay 0.0.5.4. Deutsche Fassung: [SECURITY.de.md](SECURITY.de.md).*

SCOverlay is a free, donation-funded desktop overlay for Star Citizen, written by one person. Its core is closed source. This document is meant for people who, quite reasonably, want to know what a closed-source program does on their machine before they run it. Everything below is stated so that you can **verify it yourself** with a firewall log, Process Monitor or Wireshark; nothing here asks you to take my word for it.

It also says plainly what SCOverlay does **not** offer. I would rather you read an honest "no" here than discover it later.

## 1. What is and isn't in place

| Question | Answer |
|---|---|
| Is the installer or the executable code-signed? | **No.** Windows SmartScreen will warn on first launch. See section 2 for how to verify a download instead. |
| Are release hashes published? | **Yes.** Every release of the core and of every add-on is published with its SHA-256 through the update API, and the client verifies that hash before it extracts anything. |
| Is there telemetry, crash reporting or analytics? | **No.** The application sends no usage data, no identifiers and no hardware information. |
| Is an account required? | **No.** One add-on (OrgaStorage) can optionally be paired with a website account; see section 5. |
| Has the code been independently audited? | **No**, and there are no plans for one. A donation-funded hobby project cannot pay for it. |
| Are add-ons sandboxed or permission-gated? | **No.** See section 4. This is the most important limitation in this document. |

## 2. Downloads and updates

**Where files come from.** The website `scoverlay.it-en.ch` is the control plane. When the application checks for updates it asks `https://scoverlay.it-en.ch/api/updates` (all products in one request) or `https://scoverlay.it-en.ch/api/updates/<product>`. The answer contains the version, the file size, the **SHA-256** of the file and a short-lived download link on `release-assets.githubusercontent.com`. The actual binaries are stored as GitHub release assets in private repositories; the website fetches a fresh signed link per request, so the client never holds any GitHub credential.

**How the client verifies.** The downloaded file is hashed and compared to the SHA-256 from the API answer. On a mismatch the file is deleted and the update aborted. This protects against a corrupted or altered download. It does **not** protect against a compromised website that lies about both the file and the hash, and it says nothing about what the software does.

**Verify a download yourself.** The hash is public, so you can check it independently of the app:

```powershell
# 1. Ask the API what it currently publishes (version, sha256)
Invoke-RestMethod https://scoverlay.it-en.ch/api/updates/core | Select-Object version, @{n='sha256';e={$_.asset.sha256}}

# 2. Hash the file you downloaded and compare
Get-FileHash .\SCOverlay-Setup-0.0.5.4.exe -Algorithm SHA256
```

Replace `core` with an add-on's product key (for example `wingman`, `orescout`, `omnia`) to check an add-on package.

**When the app talks to the server.** At start (update check, then the broadcast message check), afterwards every two hours for updates and once a minute for the broadcast message (a tiny request with an ETag, answered with "nothing new" almost every time), and whenever you open the in-app Gallery. Everything is plain HTTPS `GET`; the core never sends a `POST`. **A download only starts after you confirm it in a dialog.** Updates found while you are playing are announced with a toast and installed on the next start.

## 3. What the application does on your system

Verified against the source of 0.0.5.4. If you find behaviour that is not listed here, that is a bug in either the software or this document and I want to know about it.

### Network

| Host | Purpose | When |
|---|---|---|
| `scoverlay.it-en.ch` | Update check, gallery listing, broadcast message, hangar timer data | See section 2 |
| `release-assets.githubusercontent.com` | The actual download of an update or add-on package | Only after you confirm an install |

That is the complete list for the core. Links that open in your browser (the donation page, the GitHub issue tracker) are not connections the application makes itself. Versions before 0.0.4.0 contacted GitHub's API directly for their update check; current versions do not.

### Files and registry

| Location | Content |
|---|---|
| `%AppData%\SCOverlay\settings.json` | All settings, including hotkeys and add-on settings stored through the host API. Plain text. |
| `%AppData%\SCOverlay\debug.log`, `…\log\` | Diagnostic log. It records events and the **names** of hotkeys that fired, never raw keystrokes. |
| `%AppData%\SCOverlay\addons\<AddonName>\` | Installed add-ons, one folder each. Add-ons keep their own data next to or below this folder. |
| `%AppData%\SCOverlay\cache\gallery\` | Thumbnails for the in-app Gallery. |
| `%LocalAppData%\SCOverlay\fonts\` | The two embedded UI fonts, extracted once so Windows can load them from disk. |
| `HKCU\Software\Microsoft\Windows\CurrentVersion\Run` | **Only** if you enable "Start with Windows". Removed again when you disable it. |
| Your Star Citizen folder | Read only. The core asks where the game is installed so add-ons can read `Game.log` and the localization files. Nothing is written there. |

### Input

The core registers a **Raw Input** listener for keyboard and mouse with the `INPUTSINK` flag on its overlay window. That means it is notified of key and mouse events system-wide, also while the game has focus. This is how global hotkeys work over a fullscreen game; there is no alternative that does not have this property. What happens with the events: each key event is compared against the registered hotkey combinations and then discarded. Keystrokes are not stored, not logged and not transmitted. There are no low-level keyboard hooks (`SetWindowsHookEx`).

Two things can *generate* input, both only on request: when an add-on opens an interactive window and asks the core to block game input, the core simulates one mouse click to hand focus to that window; and individual add-ons may send input themselves (see the table in section 5).

### Screen

The core can take a screenshot with `CopyFromScreen`, but only when an add-on asks for one through the host API. The core itself never does this on its own. It does not read the game's memory, does not inject anything into the game process and does not hook the game's renderer: the overlay is an ordinary topmost window drawn by Windows.

## 4. Add-ons: the trust model, stated plainly

An add-on is a .NET assembly that SCOverlay loads **into its own process with full trust**. There is no sandbox, no permission manifest and no capability check. An add-on can technically do anything your Windows user account can: read and write files, open network connections, read and send input, take screenshots. The host API offers convenience for some of that (screenshots, input blocking, hotkeys, settings), but it is not a gate; an add-on does not need the API to do any of it.

I would rather state that than imply a permission model that does not exist. Consequences:

- **Installing an add-on is trusting its author, fully.** The SHA-256 check only proves that you received the file the server published.
- **What stands between a listing and your machine is the maintainer.** Every add-on currently in the Gallery is built and published by me from source I hold: ten of the eleven are my own, BetterPicture was written by P-WHITE and is compiled by me from its source. There is no third-party binary in the Gallery that I have not compiled myself. Add-on updates go through the same path, so a new version of an add-on does not reach anyone without passing through my hands.
- **Rule for the Gallery:** only add-ons whose source I can read and build get listed. If that changes, this document changes first.
- The **Performance Watchdog** can unload an add-on that stalls the overlay. That is a performance feature, not a security boundary.
- You can disable an add-on under *Settings → Add-ons* or delete its folder under `%AppData%\SCOverlay\addons\`. Both take effect on the next start.

A real permission or manifest system would have to be enforced by the host, and with in-process .NET that is not something I can honestly promise. If one is ever added, it will be described here, including what it can and cannot enforce.

## 5. What each listed add-on does

All add-ons below are in the Gallery as of the review date. "Contacts" lists every external host the add-on connects to; "Reads" lists game files it reads.

| Add-on | Contacts | Reads | Sends input | Screenshots | Notes |
|---|---|---|---|---|---|
| ExecTimer | `scoverlay.it-en.ch` | – | – | – | Fetches the hangar cycle anchor and server time. |
| QuickSheets | – | Images you put in its `sheets` folder | – | – | Fully offline. |
| BetterPicture | – | – | Yes, one click to focus its own window | Yes, that is its purpose | Photo mode; images stay on your disk. |
| CitizenHauler | `api.uexcorp.space` | – | – | Yes, in its route guidance window | Talks to the UEX Corp API directly for trade data. |
| OreScout | `scoverlay.it-en.ch` | – | – | – | Mining reference data, cached locally. |
| RepTracker | – | `Game.log`, `global.ini` | – | Yes, when you measure a reputation bar | Everything stays local. |
| Wingman | – | `Game.log` | Yes: presses the accept key and can bring the game to the foreground | – | Only while enabled; starts disabled on every launch. |
| Omnia | `scoverlay.it-en.ch`; images from `starcitizen.tools` / `cstone.space` on demand | `global.ini` | – | – | Search index is downloaded once and cached. |
| Workbench | `scoverlay.it-en.ch`; images from `starcitizen.tools` / `cstone.space` on demand | `Game.log` (incl. backups), `global.ini` | – | – | Blueprint ownership is derived from your logs, locally. |
| OrgaStorage | `scoverlay.it-en.ch` | – | – | – | Optional pairing with your website account via a one-time code. The resulting device token is stored DPAPI-encrypted under your Windows user, never in `settings.json`. |
| MouseMover | – | – | Yes: moves the mouse when you are idle | – | Reads keyboard, mouse and joystick *state* to detect idleness; nothing is recorded. |

Star Citizen's `Game.log` contains your character name and the names of players around you. Add-ons that read it do so locally; none of the add-ons above upload it.

## 6. Reporting a security issue

Please open an issue in this repository with **"Security"** in the title and **no technical details** in the public text. I will answer with a private channel. Reports about add-ons are welcome here too.

## 7. History of this document

- 2026-09-09: first version.
