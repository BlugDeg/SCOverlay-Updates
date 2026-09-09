<p align="center">
  <!-- Readme Links -->
  <a href="README.de.md"><img src="https://img.shields.io/badge/Liesmich-007bff?style=for-the-badge" alt="Liesmich"></a><!--
  --><a href="README.md"><img src="https://img.shields.io/badge/EN-555?style=for-the-badge" alt="English"></a><!--
  --><a href="README.de.md"><img src="https://img.shields.io/badge/DE-ff6f00?style=for-the-badge" alt="Deutsch"></a>
  &nbsp;&nbsp;|&nbsp;&nbsp;
  <!-- Manual Links -->
  <a href="MANUAL.de.md"><img src="https://img.shields.io/badge/Anleitung-555?style=for-the-badge" alt="Anleitung"></a><!--
  --><a href="MANUAL.md"><img src="https://img.shields.io/badge/EN-555?style=for-the-badge" alt="English"></a><!--
  --><a href="MANUAL.de.md"><img src="https://img.shields.io/badge/DE-555?style=for-the-badge" alt="Deutsch"></a>
  &nbsp;&nbsp;|&nbsp;&nbsp;
  <!-- Developer/SDK Links -->
  <a href="SDK_MANUAL.de.md"><img src="https://img.shields.io/badge/Entwickler-555?style=for-the-badge" alt="Entwickler"></a><!--
  --><a href="SDK_MANUAL.md"><img src="https://img.shields.io/badge/EN-555?style=for-the-badge" alt="English"></a><!--
  --><a href="SDK_MANUAL.de.md"><img src="https://img.shields.io/badge/DE-555?style=for-the-badge" alt="Deutsch"></a>
</p>

<!-- Kopf: Logo, Titel, Untertitel -->
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
  <strong>Dein modularer Cockpit-Assistent für Star Citizen.</strong>
  <br>
  Ein kostenloses, leichtgewichtiges In-Game-Overlay, das du mit Addons erweiterst.
</p>

<!-- Badges -->
<p align="center">
  <a href="https://scoverlay.it-en.ch/"><img src="https://img.shields.io/badge/Website-scoverlay.it--en.ch-007bff" alt="Website"></a>
  <a href="https://scoverlay.it-en.ch/download/core"><img src="https://img.shields.io/badge/Download-neuester%20Installer-brightgreen" alt="Download"></a>
  <a href="https://scoverlay.it-en.ch/donate"><img src="https://img.shields.io/badge/Spenden-Projekt%20unterst%C3%BCtzen-orange" alt="Spenden"></a>
  <a href="../SECURITY.de.md"><img src="https://img.shields.io/badge/Sicherheit-was%20es%20auf%20deinem%20PC%20tut-555" alt="Sicherheit"></a>
  <a href="../LICENSE.md"><img src="https://img.shields.io/badge/Lizenz-kostenlos-555" alt="Lizenz"></a>
</p>

---

## Was ist SCOverlay?

SCOverlay ist ein kleines Windows-Programm, das ein Menü über Star Citizen legt. Im Spiel eine Taste drücken, und eine Fläche mit Kacheln erscheint, eine je Addon: ein Hangar-Timer, Spickzettel, ein Bergbau-Nachschlagewerk, ein Spiellexikon, Ruf-Messung, geteilte Tabellen für die Orga und mehr. Taste nochmal drücken, und es ist weg.

Der Kern liefert nur das Fenster, die Tastenkürzel, die Einstellungen und das Update-System. Alles, was du tatsächlich benutzt, ist ein **Addon**, und Addons werden aus dem Overlay heraus installiert, aktualisiert und ein- oder ausgeschaltet.

## Kostenlos, getragen von Spenden

Es gibt keinen Lizenzschlüssel, kein Konto und kein Abonnement. Herunterladen, installieren, spielen. Wenn dir SCOverlay etwas bringt, kannst du die Entwicklung auf der Website unterstützen: **https://scoverlay.it-en.ch/donate**

## Hauptmerkmale

- **Addon-Plattform.** Eine stabile, dokumentierte API; jedes Addon ist eine eigene DLL. Wer selbst eines bauen will, findet den Weg im [SDK-Handbuch](SDK_MANUAL.de.md).
- **Gallery in der App.** Addons durchstöbern, installieren, ein- und ausschalten und entfernen, ohne das Spiel zu verlassen.
- **Automatische Updates** für den Kern und jedes Addon. Jeder Download wird vor der Installation gegen seine veröffentlichte SHA-256 geprüft; ein Download beginnt erst, wenn du ihn bestätigst.
- **Globale Tastenkürzel**, die über dem Vollbildspiel funktionieren. Vorgabe zum Ein- und Ausblenden: <kbd>Shift</kbd> + <kbd>F10</kbd>, frei belegbar.
- **Performance Watchdog.** Ein Addon, das das Overlay ausbremst, wird entladen, statt dich Bilder pro Sekunde zu kosten.
- **Zweisprachig.** Englisch und Deutsch, in den Einstellungen umschaltbar.
- **Keine Telemetrie, keine Konten.** Was die Anwendung auf deinem PC tut, steht in [SECURITY.de.md](../SECURITY.de.md).

## Herunterladen und installieren

1. **Den neuesten Installer laden:** https://scoverlay.it-en.ch/download/core
   Die Website ist die massgebliche Quelle. Die Releases auf dieser GitHub-Seite sind ein Spiegel, den ältere Installationen noch für ihre Update-Prüfung benutzen; sie können hinterherhinken.
2. **Installer ausführen.** Er fragt, wo Star Citizen installiert ist (der Ordner `LIVE`), damit Addons die `Game.log` finden. Das lässt sich überspringen und später unter *Einstellungen → Allgemein* nachholen.
3. **Windows SmartScreen wird warnen.** Der Installer ist nicht code-signiert (warum, und wie du stattdessen die Prüfsumme des Downloads vergleichst, steht in [SECURITY.de.md](../SECURITY.de.md)). Wähle *Weitere Informationen → Trotzdem ausführen*.
4. **SCOverlay starten.** Es lebt im Infobereich der Taskleiste. Star Citizen starten und <kbd>Shift</kbd> + <kbd>F10</kbd> drücken.

Das [Benutzerhandbuch](MANUAL.de.md) führt durch den ersten Start, die Einstellungen und jedes mitgelieferte Addon.

## Addons

Alle Addons unten gibt es in der Gallery im Overlay und auf der [Website](https://scoverlay.it-en.ch/gallery).

| Addon | Was es tut |
|---|---|
| **ExecTimer** | Countdown für den Zyklus des Executive Hangars in Pyro, als kleines HUD in einer Bildschirmecke, mit Vorwarnton. |
| **QuickSheets** | Zeigt deine eigenen Bilder (Karten, Guides, Tastenbelegungen) in zoombaren Fenstern über dem Spiel. Ordner werden zu Menüs. |
| **Wingman** | Nimmt Missionen, die Party-Mitglieder teilen, automatisch an, in den ein bis zwei Sekunden, die das Spiel dafür lässt. |
| **Omnia** | Das Star-Citizen-Lexikon: ein Suchfeld über Planeten, Stationen, Schiffe, Gegenstände, Missionen, Preise. Schnellsuche mit <kbd>Shift</kbd> + <kbd>F5</kbd>. |
| **OreScout** | Bergbau-Nachschlagewerk: Erz zu Scanner-Signatur, Ort zu Erzen, und ein Clusterwert zurück zu Erz und Brockenzahl. |
| **Workbench** | Baupläne: welche es gibt, welche du besitzt (aus deinen Logs), was ein Bauplan braucht und was er beim Zerlegen zurückgibt, mit Werte-Rechner. |
| **RepTracker** | Macht aus dem Rufbalken im mobiGlas Zahlen: je Auftrag messen und sehen, was jede Mission bringt. |
| **OrgaStorage** | Geteilte Tabellen für deine Organisation, von mehreren Mitgliedern gleichzeitig bearbeitet, mit Formeln. |
| **MouseMover** | Merkt, wenn du untätig bist, warnt dich und bewegt dann die Maus, damit das Spiel dich nicht wegen Inaktivität rauswirft. |
| **CitizenHauler** | Handelsbegleiter mit Live-Daten von UEX Corp, Routenplanung und Datarunner-Modus. |
| **BetterPicture** | Fotomodus: hochwertige Bildschirmfotos (RAW, 16 Bit) mit Farbfilter-Overlay. |

## Sicherheit und Vertrauen

Der Kern ist nicht quelloffen. Damit du das nicht einfach glauben musst, listet [SECURITY.de.md](../SECURITY.de.md) genau auf, welche Hosts die Anwendung kontaktiert, welche Dateien sie schreibt, was ihr Eingabe-Horcher tut und wie das Vertrauensmodell für Addons aussieht, in einer Form, die du mit Firewall oder Process Monitor nachprüfen kannst. Es sagt auch klar, was es nicht gibt: keine Code-Signierung, kein unabhängiges Audit, keine Sandbox für Addons.

## Dokumentation

- [Benutzerhandbuch](MANUAL.de.md) (Deutsch) · [User manual](MANUAL.md) (English)
- [SDK-Handbuch](SDK_MANUAL.de.md) für Addon-Entwickler (Deutsch) · [SDK manual](SDK_MANUAL.md) (English)
- [Sicherheit und Datenschutz](../SECURITY.de.md) (Deutsch) · [Security and privacy](../SECURITY.md) (English)
- [Patchnotes](https://scoverlay.it-en.ch/patchnotes) auf der Website

## Mach mit

- **Fehler gefunden oder eine Idee?** Öffne ein [Issue](https://github.com/BlugDeg/SCOverlay-Updates/issues). Deutsch ist genauso willkommen wie Englisch.
- **Ein Addon bauen?** Das [SDK-Handbuch](SDK_MANUAL.de.md) bringt dich in wenigen Minuten vom leeren Projekt zur funktionierenden Kachel. Ein Addon ist dein Werk und bleibt es.

## Lizenz

SCOverlay ist kostenlos unter einer proprietären Lizenz: frei benutzen, aber die Anwendung selbst nicht weiterverbreiten oder verändern. Addons, die du schreibst, gehören dir. Der volle Text steht in [LICENSE.md](../LICENSE.md).
