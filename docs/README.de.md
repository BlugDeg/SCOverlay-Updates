<p align="center">
  <a href="README.md"><img src="https://img.shields.io/badge/Readme-555?style=flat-square" alt="Readme"></a><!--
  --><a href="README.md"><img src="https://img.shields.io/badge/EN-555?style=flat-square" alt="English"></a><!--
  --><a href="README.de.md"><img src="https://img.shields.io/badge/DE-007bff?style=flat-square" alt="Deutsch"></a>
  &nbsp;&nbsp;|&nbsp;&nbsp;
  <a href="SDK_MANUAL.de.md"><img src="https://img.shields.io/badge/Developer-555?style=flat-square" alt="Developer"></a><!--
  --><a href="SDK_MANUAL.md"><img src="https://img.shields.io/badge/EN-ff6f00?style=flat-square" alt="English"></a><!--
  --><a href="SDK_MANUAL.de.md"><img src="https://img.shields.io/badge/DE-555?style=flat-square" alt="Deutsch"></a>
</p>

<!-- Header: Logo, Titel und Slogan -->
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
  Ein modulares, hochperformantes In-Game-Overlay für Star Citizen, erweiterbar durch ein leistungsstarkes Addon-System.
</p>

<!-- Badges -->
<p align="center">
  <a href="LICENSE"><img src="https://img.shields.io/github/license/DEIN-GITHUB-USERNAME/DEIN-REPO-NAME" alt="Lizenz"></a>
  <a href="https://www.patreon.com/cw/BlugDeg"><img src="https://img.shields.io/badge/patreon-Werde ein Patron-orange" alt="Patreon"></a>
  <a href="#"><img src="https://img.shields.io/badge/status-aktiv-brightgreen" alt="Status"></a>
</p>

---

## 🔑 Zugang & Lizenzierung

SCOverlay ist ein Projekt, das von Unterstützern getragen wird. Der Zugang zur Software, zu Updates und zu deinem persönlichen Lizenzschlüssel wird durch eine **Patreon-Mitgliedschaft** gewährt. Deine Unterstützung trägt direkt zur Weiterentwicklung und Instandhaltung dieser Plattform bei.

**Wie du SCOverlay erhältst:**

1.  **Werde ein Patron:** Besuche unsere Patreon-Seite und wähle eine Mitgliedschaftsstufe.
    <br>➡️ **[https://www.patreon.com/cw/BlugDeg](https://www.patreon.com/cw/BlugDeg)**

2.  **Prüfe deine E-Mails:** Nach deinem Beitritt erhältst du eine E-Mail mit:
    *   Deinem persönlichen **Lizenzschlüssel** zur Aktivierung der Software.
    *   Einem **Download-Link** für die neueste Version des SCOverlay-Installers und der Addons.

## 🚀 Installation & Schnellstart

1.  Führe die `SCOverlay-Setup-vX.Y.Z.exe` aus, die du per E-Mail erhalten hast.
2.  Starte SCOverlay und aktiviere es mit dem Lizenzschlüssel aus deiner E-Mail.
3.  Drücke den Standard-Hotkey <kbd>Shift</kbd> + <kbd>F10</kbd>, um das Overlay im Spiel zu öffnen oder zu schließen.
4.  Um das Fenster zu bewegen oder die Größe zu ändern, gehe zu `Einstellungen -> Allgemein` und schalte "Fenster entsperren" auf "An".

## ✨ Kern-Features

- 🚀 **Erweiterbare Addon-Architektur:** Das Herzstück von SCOverlay. Eine saubere und stabile API (`SCOverlay.API`) ermöglicht es Entwicklern, auf einfache Weise neue Funktionen zu erstellen und zu integrieren.
- ⚡ **Performance an erster Stelle:** Ein eingebauter "Performance Watchdog" überwacht kontinuierlich die Systemlast, um Framerate-Einbrüche zu verhindern. Rechenintensive Addon-Operationen können eine temporäre Ausnahme anfordern.
- 🎨 **Anpassbare Benutzeroberfläche:** Das Overlay-Fenster kann frei bewegt, in der Größe verändert und mit verschiedenen Themes gestaltet werden.
- ⌨️ **Robustes Hotkey-System:** Nutzt Low-Level-Keyboard-Hooks, um auch in anspruchsvollen Spiel-Szenarien zuverlässig zu funktionieren, inklusive eines ausfallsicheren "Scroll Lock Fallback"-Mechanismus.
- 🔄 **Integrierter Updater:** Die Kernanwendung sowie alle installierten Addons können Updates direkt beziehen, um immer auf dem neuesten Stand zu bleiben.

## 🧩 Enthaltene Addons

SCOverlay wird mit einem Set leistungsstarker Addons geliefert. Einige sind Standard und für alle Mitglieder enthalten, während andere Premium-Addons sind, die eine separate Lizenz erfordern, die an deine Patreon-Stufe gebunden sein kann.

- **ExecTimer** (Standard): Ein präziser, netzwerk-synchronisierter Timer für die Executive Hangars, komplett mit anpassbaren Sound- und visuellen Alarmen.
- **QuickSheets** (Standard): Ermöglicht es dir, eigene Bilder (Checklisten, Handelsrouten etc.) als schwebende, anpinnbare Fenster im Spiel anzuzeigen.
- **SpyCitizen** (🔑 Lizenziert): Ein mächtiges Spionage-Werkzeug, das die `Game.log`-Datei in Echtzeit analysiert, um Spieler zu verfolgen, Kampfereignisse (Kills/Tode) aufzuzeichnen und Statistiken zu führen.

## 💬 Support, Feedback und Ideen

Hast du eine Frage, einen Fehler gefunden oder eine großartige Idee für ein neues Feature? Der beste Weg, uns zu erreichen, ist über unser GitHub Issue Council.

➡️ **[Ein Issue auf GitHub öffnen](https://github.com/DEIN-GITHUB-USERNAME/DEIN-REPO-NAME/issues)**

Bitte verwende die entsprechenden Tags (z.B. `bug`, `feature-request`, `question`), um uns zu helfen, das Feedback zu organisieren.

## 👨‍💻 Für Entwickler

Möchtest du dein eigenes Addon für SCOverlay erstellen? Wir haben ein umfassendes **[Entwicklerhandbuch (SDK Manual)](docs/SDK_MANUAL.de.md)** erstellt, das dir den Einstieg erleichtert.

## 🤝 Wie du beitragen kannst

Beiträge sind immer willkommen! Lies unsere [**Beitrags-Richtlinien (CONTRIBUTING.md)**](CONTRIBUTING.md). Wir erwarten außerdem, dass sich alle Beitragenden an unseren [**Verhaltenskodex (Code of Conduct)**](CODE_OF_CONDUCT.md) halten.

## 📄 Lizenz

Der Quellcode dieses Projekts ist unter der MIT-Lizenz lizenziert. Siehe die [LICENSE](LICENSE)-Datei für Details.

Bitte beachte, dass die Nutzung der kompilierten, einsatzbereiten Anwendung eine aktive Lizenz erfordert, die über Patreon bezogen wird.