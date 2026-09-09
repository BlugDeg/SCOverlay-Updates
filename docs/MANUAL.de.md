<p align="center">
<!-- Readme Links -->
<a href="README.de.md"><img src="https://img.shields.io/badge/Liesmich-555?style=for-the-badge" alt="Liesmich"></a><!--
--><a href="README.md"><img src="https://img.shields.io/badge/EN-555?style=for-the-badge" alt="English"></a><!--
--><a href="README.de.md"><img src="https://img.shields.io/badge/DE-555?style=for-the-badge" alt="Deutsch"></a>
&nbsp;&nbsp;|&nbsp;&nbsp;
<!-- Manual Links -->
<a href="MANUAL.de.md"><img src="https://img.shields.io/badge/Anleitung-007bff?style=for-the-badge" alt="Anleitung"></a><!--
--><a href="MANUAL.md"><img src="https://img.shields.io/badge/EN-555?style=for-the-badge" alt="English"></a><!--
--><a href="MANUAL.de.md"><img src="https://img.shields.io/badge/DE-ff6f00?style=for-the-badge" alt="Deutsch"></a>
&nbsp;&nbsp;|&nbsp;&nbsp;
<!-- Developer/SDK Links -->
<a href="SDK_MANUAL.de.md"><img src="https://img.shields.io/badge/Entwickler-555?style=for-the-badge" alt="Entwickler"></a><!--
--><a href="SDK_MANUAL.md"><img src="https://img.shields.io/badge/EN-555?style=for-the-badge" alt="English"></a><!--
--><a href="SDK_MANUAL.de.md"><img src="https://img.shields.io/badge/DE-555?style=for-the-badge" alt="Deutsch"></a>
</p>

<h1 align="center">SCOverlay Benutzerhandbuch</h1>

<p align="center">
  <strong>SCOverlay und seine Addons installieren, einrichten und benutzen.</strong>
  <br>
  Geschrieben für SCOverlay 0.0.5.x.
</p>

---

## Inhaltsverzeichnis

1.  [**Installation & erster Start**](#1-installation--erster-start)
2.  [**Grundbedienung**](#2-grundbedienung)
3.  [**Einstellungen**](#3-einstellungen)
4.  [**Die Addon-Gallery**](#4-die-addon-gallery)
5.  [**Addon-Anleitungen**](#5-addon-anleitungen)
    *   [ExecTimer](#exectimer-der-hangar-timer)
    *   [QuickSheets](#quicksheets-dein-in-game-bildbetrachter)
    *   [Die übrigen Addons](#die-übrigen-addons)
6.  [**Updates**](#6-updates)
7.  [**Fehlerbehebung & FAQ**](#7-fehlerbehebung--faq)

---

## 1. Installation & erster Start

**Schritt 1: Herunterladen**
-   ➡️ Den neuesten Installer von der Website holen: **https://scoverlay.it-en.ch/download/core** (der Link zeigt immer auf die aktuelle Version).
-   ✔️ Windows SmartScreen zeigt eine Warnung, weil der Installer nicht code-signiert ist. Klicke *Weitere Informationen → Trotzdem ausführen*. Wer die Datei vorher prüfen will: [SECURITY.de.md](../SECURITY.de.md) zeigt, wie man ihre SHA-256 mit der veröffentlichten vergleicht.

**Schritt 2: Installieren**
-   ➡️ Installer ausführen und durchklicken.
-   ✔️ Er fragt, wo Star Citizen installiert ist. Wähle den Ordner `LIVE` (zum Beispiel `C:\Program Files\Roberts Space Industries\StarCitizen\LIVE`). Addons finden darüber die `Game.log` und die Textdateien des Spiels. Wer es überspringt, wird beim ersten Start noch einmal gefragt, und ändern lässt es sich jederzeit unter *Einstellungen → Allgemein*.

**Schritt 3: Erster Start**
-   ➡️ SCOverlay über das Startmenü oder die Desktop-Verknüpfung starten.
-   ✔️ Es öffnet sich nichts Grosses. SCOverlay lebt im **Infobereich** der Taskleiste, dem Bereich mit den kleinen Symbolen neben der Uhr. Ein Rechtsklick auf sein Symbol zeigt das Menü (Einstellungen, Beenden).
-   ✔️ Beim allerersten Start bietet SCOverlay an, die Standard-Addons zu installieren (ExecTimer, QuickSheets, ein Demo). Klicke **Ja**; sie werden geladen, geprüft und eingerichtet, und SCOverlay startet neu.

Das war's. Star Citizen starten und weiterlesen.

## 2. Grundbedienung

-   **Overlay ein- und ausblenden:** <kbd>Shift</kbd> + <kbd>F10</kbd> als Vorgabe. Einmal drücken zeigt die Fläche, nochmal drücken blendet sie aus. Umbelegen unter *Einstellungen → Tastenkürzel*.
-   **Die Fläche:** eine Kachel je Addon. Ein Klick auf eine Kachel öffnet das Menü oder Fenster dieses Addons. In der Fusszeile stehen links die Übersicht der Tastenkürzel und rechts die Knöpfe *Gallery* und *Einstellungen*.
-   **Wenn das Kürzel im Spiel nicht ankommt:** unter *Einstellungen → Tastenkürzel* den *Rollen-Taste-Fallback* einschalten. Dann öffnet ein **Doppeltipp auf <kbd>Rollen</kbd>** (Scroll Lock) das Overlay; das funktioniert auch in Spielen, die andere Kombinationen schlucken.
-   **Addon-Kürzel:** viele Addons haben ein eigenes Kürzel (siehe Abschnitt 5 und *Einstellungen → Tastenkürzel*, wo sich alle umbelegen lassen).

## 3. Einstellungen

Overlay öffnen und in der Fusszeile auf **Einstellungen** klicken.

-   **Allgemein**
    *   `Sprache`: Englisch (Vorgabe) oder Deutsch. Wirkt für den Kern sofort; ein bereits offenes Addon-Fenster übernimmt es beim nächsten Öffnen.
    *   `Star-Citizen-Ordner`: wo das Spiel installiert ist. Hier ändern, wenn du auf PTU spielst oder das Spiel verschoben hast.
    *   `Mit Windows starten` und `Overlay beim Start anzeigen`: beides als Vorgabe aus. Mit dem zweiten aus startet SCOverlay still im Infobereich und wartet auf das Kürzel.
    *   `Fenster entsperren`: erlaubt, das Overlay zu verschieben und in der Grösse zu ändern. Danach wieder sperren.
    *   `Verbindung`: zeigt, wann die Website zuletzt erreicht wurde. Es ist dieselbe Verbindung, die der Updater benutzt.
    *   `Projekt unterstützen`: öffnet die Spendenseite im Browser.
-   **Anzeige**
    *   `Overlay-Breite / -Höhe`: Grösse der Fläche in Prozent des Bildschirms.
    *   `Kachelgrösse`: 60–200 %. Kacheln behalten diese Grösse unabhängig von der Fläche; eine grössere Fläche zeigt mehr Kacheln, nicht grössere.
    *   `Theme` und Farben.
-   **Tastenkürzel**
    *   `Umschalt-Kürzel`: auf *Neu belegen* klicken und die Kombination drücken.
    *   `Rollen-Taste-Fallback`: siehe Abschnitt 2.
    *   Jedes Addon-Kürzel, mit einer kurzen Beschreibung, was es tut.
-   **Audio**: welches Ein- und Ausgabegerät SCOverlay für die Töne der Addons benutzt.
-   **Erweitert**: Tray-Symbol ein/aus, der Schalter *Debug-Protokoll aktivieren* (vor einer Fehlermeldung einschalten), *Datenordner öffnen* und eine Abkürzung zum *Fehlerbericht*.
-   **Addons** (Knopf in den Einstellungen): die Liste der installierten Addons mit Versionen, Ein-/Ausschalten je Addon, und *Addon aus .zip installieren* für ein Paket, das du ausserhalb der Gallery bekommen hast.

## 4. Die Addon-Gallery

In der Fusszeile der Hauptfläche auf **Gallery** klicken. Jede Karte zeigt ein Addon mit Beschreibung, Autor und Version.

-   **Installieren** lädt das Addon, prüft es und legt es ab. Ein Streifen oben bittet dann um einen **Neustart** von SCOverlay: Addons werden einmal beim Start geladen.
-   **Aktivieren / Deaktivieren** schaltet ein installiertes Addon ab, ohne es zu entfernen. Braucht ebenfalls einen Neustart.
-   **Entfernen** löscht den Ordner des Addons. Hat SCOverlay das Addon noch geladen, scheitert das mit einer Meldung; erst deaktivieren, neu starten, dann entfernen.
-   Ein Klick auf Bild oder Text einer Karte öffnet die Seite des Addons auf der Website im Browser.

Dieselben Addons stehen auf der Website: https://scoverlay.it-en.ch/gallery

Jedes Addon in der Gallery wird vom Betreuer von SCOverlay aus Quellcode gebaut und veröffentlicht, der ihm vorliegt. Was das für dich bedeutet und was nicht, steht in [SECURITY.de.md](../SECURITY.de.md).

## 5. Addon-Anleitungen

### ExecTimer: Der Hangar-Timer

-   **Auf einen Blick:** ein Countdown für den Zyklus des Executive Hangars in Pyro, als kleines HUD in einer Ecke deines Bildschirms. Es zeigt die fünf Lampen, den Zustand (`HANGAR OFFEN`, `HANGAR RESET`, `HANGAR GESCHLOSSEN`) und die Zeit bis zum nächsten Wechsel.
-   **HUD-Modus** (im Menü des Addons): `Aus`, `Immer` oder `Mit Overlay` (nur sichtbar, solange die Hauptfläche offen ist). Das HUD ist klickdurchlässig und steht dem Spiel nie im Weg.
-   **Ecke:** eine der vier Bildschirmecken wählen.
-   **Vorwarnung:** ein Ton einige Minuten bevor der Hangar öffnet (Vorgabe 5 min). Vorlauf, Lautstärke und Tondatei lassen sich ändern.
-   **Woher die Zeit kommt:** der Anker des Zyklus wird von der Website abgeglichen, weil sich der Hangar-Zyklus mit jedem Server-Neustart und Patch verschiebt. Geht der Timer nach einem Patch um Minuten falsch, wird gerade der Anker korrigiert; er holt es von selbst auf.
-   Der **?**-Knopf im Addon öffnet seine eigene Anleitung.

### QuickSheets: Dein In-Game-Bildbetrachter

-   **Auf einen Blick:** eigene Bilder (Handelskarten, Bergbau-Guides, Tastenbelegungen) in Fenstern über dem Spiel anzeigen. Drei StormBreaker-Sheets sind dabei.
-   **Eigene Sheets hinzufügen:**
    1.  <kbd>Win</kbd> + <kbd>R</kbd> drücken, `%appdata%\SCOverlay\addons\QuickSheetAddon\sheets` einfügen und Enter.
    2.  `.png`- oder `.jpg`-Dateien in diesen Ordner legen. Unterordner werden zu Untermenüs, so lassen sie sich sortieren (`Bergbau`, `Handel`, …).
    3.  Ein Ordner mit genau einem Bild, das so heisst wie der Ordner, öffnet das Bild direkt statt eines Untermenüs.
    4.  SCOverlay neu starten; das Menü wird beim Start aufgebaut.
-   **Das Sheet-Fenster:** zoomen mit dem Mausrad oder den Knöpfen `−` / `+` / `FIT`, das Bild verschieben, `PIN` hält das Fenster sichtbar, während die Hauptfläche zu ist (`WIN` blendet es mit der Fläche aus), und der Knopf ganz rechts wechselt in den Vollbildmodus und zurück.

### Die übrigen Addons

Jedes davon hat ein eigenes Fenster und meist eine eigene Hilfeseite darin. Die Kürzel sind die Vorgaben und lassen sich unter *Einstellungen → Tastenkürzel* umbelegen.

| Addon | Was es tut | Kürzel |
|---|---|---|
| **Wingman** | Nimmt Missionen, die Party-Mitglieder teilen, automatisch an. Vor dem Spielen einschalten; es startet bei jedem Start aus, damit es nie eine Taste drückt, die du nicht erwartest. Missionen lassen sich ausschliessen. | <kbd>Shift</kbd> + <kbd>Ü</kbd> schaltet um |
| **Omnia** | Alles durchsuchen, was das Spiel kennt: Planeten, Monde, Stationen, Schiffe, Gegenstände, Missionen, Preise mit Alter. | <kbd>Strg</kbd> + <kbd>Shift</kbd> + <kbd>L</kbd> Hauptfenster, <kbd>Shift</kbd> + <kbd>F5</kbd> Schnellsuche |
| **OreScout** | Bergbau-Nachschlagewerk: Erz → Signatur, Ort → Erze, Clusterwert → Erz und Brockenzahl. Optionales HUD mit deinen gemerkten Erzen. | <kbd>Strg</kbd> + <kbd>Shift</kbd> + <kbd>O</kbd> |
| **Workbench** | Baupläne: welche es gibt, welche du besitzt (aus deinen Logs gelesen), Zutaten, Zerlegeausbeute und ein Werte-Rechner. | <kbd>Strg</kbd> + <kbd>Shift</kbd> + <kbd>B</kbd> |
| **OrgaStorage** | Geteilte Tabellen für deine Orga. Das Addon einmal mit deinem Website-Konto koppeln (ein sechsstelliger Code, eingegeben auf https://scoverlay.it-en.ch/verbinden). | <kbd>Strg</kbd> + <kbd>Shift</kbd> + <kbd>G</kbd> |
| **MouseMover** | Warnt dich, wenn du länger untätig warst, und bewegt dann die Maus, damit das Spiel dich nicht rauswirft. Die Schwelle stellst du in seinem Menü ein. | <kbd>Strg</kbd> + <kbd>Shift</kbd> + <kbd>M</kbd> schaltet um |
| **RepTracker** | Den Rufbalken im mobiGlas je Auftrag messen und sehen, was jede Mission bringt. Ein Assistent führt durch die erste Messung. | über seine Kachel |
| **CitizenHauler** | Handelsbegleiter mit Live-Daten von UEX Corp, Routenplanung und Routenführung. | über seine Kachel |
| **BetterPicture** | Fotomodus mit hochwertigen Bildschirmfotos und Farbfilter-Overlay. | über seine Kachel |

## 6. Updates

-   **Beim Start** fragt SCOverlay die Website nach neuen Versionen des Kerns und jedes installierten Addons. Gibt es eine, bietet ein Dialog an, sie jetzt zu installieren.
-   **Während du spielst** prüft es alle zwei Stunden erneut. Eine neue Version wird nur mit einem kleinen Toast gemeldet; mitten im Spiel wird nichts installiert. Eingespielt wird sie beim nächsten Start.
-   Jeder Download wird vor dem Entpacken gegen seine veröffentlichte SHA-256 geprüft. Ein Download, der nicht passt, wird gelöscht.
-   Es wird nie etwas heruntergeladen, ohne dass du es bestätigst.

## 7. Fehlerbehebung & FAQ

-   **F: SmartScreen oder mein Virenscanner warnt vor SCOverlay. Ist es sicher?**
    *   **A:** SCOverlay ist nicht code-signiert, deshalb warnt SmartScreen bei jeder neuen Version; das ist erwartbar und kein Urteil über die Datei. Was du prüfen *kannst*: dass die Datei die ist, die die Website veröffentlicht hat. Vergleiche ihre SHA-256 mit dem Wert in `https://scoverlay.it-en.ch/api/updates/core` (die Schritte stehen in [SECURITY.de.md](../SECURITY.de.md)). Virenscanner-Heuristiken stossen sich manchmal am globalen Tastatur-Horcher; dasselbe Dokument erklärt genau, was er tut und warum. Wer dem nicht vertrauen will, lässt es weg; das ist eine legitime Entscheidung.
-   **F: Das Kürzel tut im Spiel nichts.**
    *   **A:** Unter *Einstellungen → Tastenkürzel* den *Rollen-Taste-Fallback* einschalten und <kbd>Rollen</kbd> doppelt tippen. Ausserdem prüfen, ob die Kombination im Spiel belegt ist.
-   **F: Wo sind meine Einstellungen und Addon-Daten?**
    *   **A:** In `%appdata%\SCOverlay`. Einstellungen in `settings.json`, das Protokoll in `debug.log`, Addons in `addons\`.
-   **F: Ich habe Star Citizen verschoben / ich spiele auf PTU.**
    *   **A:** Den Ordner unter *Einstellungen → Allgemein* ändern. Addons, die die `Game.log` lesen, folgen sofort.
-   **F: Ein Addon ist aus dem Menü verschwunden.**
    *   **A:** In `debug.log` nach seinem Namen suchen. Entweder ist es beim Laden gescheitert (meist eine Versionsabweichung nach einem Update; aus der Gallery neu installieren) oder der Performance Watchdog hat es entladen, weil es das Overlay ausgebremst hat.
-   **F: Wie entferne ich ein Addon vollständig?**
    *   **A:** Gallery → *Entfernen*, oder seinen Ordner unter `%appdata%\SCOverlay\addons\` löschen, während SCOverlay nicht läuft.
-   **F: Wo bekomme ich Hilfe?**
    *   **A:** Ein Issue auf GitHub öffnen: **https://github.com/BlugDeg/SCOverlay-Updates/issues**. Deutsch ist genauso willkommen wie Englisch. Die passenden Zeilen aus `debug.log` anhängen.
