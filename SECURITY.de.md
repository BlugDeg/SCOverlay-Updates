# Sicherheit und Datenschutz

*Stand: 9. September 2026, geprüft gegen SCOverlay 0.0.5.4. English version: [SECURITY.md](SECURITY.md).*

SCOverlay ist ein kostenloses, spendenfinanziertes Desktop-Overlay für Star Citizen, geschrieben von einer Person. Der Kern ist nicht quelloffen. Dieses Dokument richtet sich an Leute, die vernünftigerweise wissen wollen, was ein Programm ohne einsehbaren Quellcode auf ihrem Rechner tut, bevor sie es starten. Alles hier ist so formuliert, dass du es **selbst nachprüfen** kannst, mit einem Firewall-Protokoll, Process Monitor oder Wireshark; nichts hier verlangt, mir zu glauben.

Es sagt ausserdem klar, was SCOverlay **nicht** bietet. Lieber liest du hier ein ehrliches „Nein", als es später zu entdecken.

## 1. Was vorhanden ist und was nicht

| Frage | Antwort |
|---|---|
| Sind Installer oder Programmdatei code-signiert? | **Nein.** Windows SmartScreen warnt beim ersten Start. Abschnitt 2 zeigt, wie du einen Download stattdessen prüfst. |
| Werden Prüfsummen veröffentlicht? | **Ja.** Jede Fassung des Kerns und jedes Addons wird mit ihrer SHA-256 über die Update-API veröffentlicht, und der Client prüft diese Summe, bevor er etwas entpackt. |
| Gibt es Telemetrie, Absturzberichte oder Analytik? | **Nein.** Die Anwendung sendet keine Nutzungsdaten, keine Kennungen und keine Hardware-Informationen. |
| Braucht es ein Konto? | **Nein.** Ein Addon (OrgaStorage) kann optional mit einem Website-Konto gekoppelt werden; siehe Abschnitt 5. |
| Wurde der Code unabhängig geprüft (Audit)? | **Nein**, und es ist keines geplant. Ein spendenfinanziertes Hobbyprojekt kann das nicht bezahlen. |
| Sind Addons in einer Sandbox oder mit Berechtigungen versehen? | **Nein.** Siehe Abschnitt 4. Das ist die wichtigste Einschränkung in diesem Dokument. |

## 2. Downloads und Updates

**Woher die Dateien kommen.** Die Website `scoverlay.it-en.ch` ist die Steuerzentrale. Beim Prüfen auf Updates fragt die Anwendung `https://scoverlay.it-en.ch/api/updates` (alle Produkte in einer Anfrage) oder `https://scoverlay.it-en.ch/api/updates/<produkt>`. Die Antwort enthält die Version, die Dateigrösse, die **SHA-256** der Datei und einen kurzlebigen Download-Link auf `release-assets.githubusercontent.com`. Die eigentlichen Dateien liegen als GitHub-Release-Assets in privaten Repositories; die Website holt je Anfrage einen frischen signierten Link, der Client hält also nie eine GitHub-Zugangsberechtigung.

**Wie der Client prüft.** Die heruntergeladene Datei wird gehasht und mit der SHA-256 aus der API-Antwort verglichen. Bei Abweichung wird die Datei gelöscht und das Update abgebrochen. Das schützt vor einem beschädigten oder veränderten Download. Es schützt **nicht** vor einer kompromittierten Website, die Datei und Prüfsumme gleichzeitig fälscht, und es sagt nichts darüber, was die Software tut.

**Einen Download selbst prüfen.** Die Prüfsumme ist öffentlich, du kannst sie also unabhängig von der App vergleichen:

```powershell
# 1. Die API fragen, was sie gerade ausliefert (Version, sha256)
Invoke-RestMethod https://scoverlay.it-en.ch/api/updates/core | Select-Object version, @{n='sha256';e={$_.asset.sha256}}

# 2. Die heruntergeladene Datei hashen und vergleichen
Get-FileHash .\SCOverlay-Setup-0.0.5.4.exe -Algorithm SHA256
```

Ersetze `core` durch den Produktschlüssel eines Addons (zum Beispiel `wingman`, `orescout`, `omnia`), um ein Addon-Paket zu prüfen.

**Wann die App mit dem Server spricht.** Beim Start (Update-Prüfung, danach die Abfrage der Rundnachricht), danach alle zwei Stunden für Updates und einmal pro Minute für die Rundnachricht (eine winzige Anfrage mit ETag, fast immer beantwortet mit „nichts Neues"), und wenn du die Gallery in der App öffnest. Alles sind reine HTTPS-`GET`-Anfragen; der Kern sendet nie ein `POST`. **Ein Download beginnt erst, wenn du ihn in einem Dialog bestätigst.** Updates, die während des Spielens gefunden werden, werden mit einem Toast gemeldet und beim nächsten Start eingespielt.

## 3. Was die Anwendung auf deinem System tut

Geprüft gegen den Quellcode von 0.0.5.4. Wenn du ein Verhalten findest, das hier nicht steht, ist das ein Fehler in der Software oder in diesem Dokument, und ich will davon wissen.

### Netzwerk

| Host | Zweck | Wann |
|---|---|---|
| `scoverlay.it-en.ch` | Update-Prüfung, Gallery-Liste, Rundnachricht, Daten für den Hangar-Timer | Siehe Abschnitt 2 |
| `release-assets.githubusercontent.com` | Der eigentliche Download eines Updates oder Addon-Pakets | Nur nachdem du eine Installation bestätigt hast |

Das ist die vollständige Liste für den Kern. Links, die sich in deinem Browser öffnen (Spendenseite, GitHub-Issues), sind keine Verbindungen, die die Anwendung selbst aufbaut. Fassungen vor 0.0.4.0 haben die GitHub-API direkt für ihre Update-Prüfung angesprochen; aktuelle Fassungen tun das nicht.

### Dateien und Registry

| Ort | Inhalt |
|---|---|
| `%AppData%\SCOverlay\settings.json` | Alle Einstellungen, einschliesslich Tastenkürzel und der Addon-Einstellungen, die über die Host-API gespeichert werden. Klartext. |
| `%AppData%\SCOverlay\debug.log`, `…\log\` | Diagnoseprotokoll. Es hält Ereignisse und die **Namen** ausgelöster Tastenkürzel fest, nie rohe Tastendrücke. |
| `%AppData%\SCOverlay\addons\<AddonName>\` | Installierte Addons, ein Ordner je Addon. Addons legen ihre eigenen Daten neben oder unter diesem Ordner ab. |
| `%AppData%\SCOverlay\cache\gallery\` | Vorschaubilder für die Gallery in der App. |
| `%LocalAppData%\SCOverlay\fonts\` | Die zwei eingebetteten UI-Schriften, einmal entpackt, damit Windows sie von der Platte laden kann. |
| `HKCU\Software\Microsoft\Windows\CurrentVersion\Run` | **Nur**, wenn du „Mit Windows starten" einschaltest. Wird beim Ausschalten wieder entfernt. |
| Dein Star-Citizen-Ordner | Nur lesend. Der Kern fragt, wo das Spiel installiert ist, damit Addons `Game.log` und die Lokalisierungsdateien lesen können. Dort wird nichts geschrieben. |

### Eingabe

Der Kern registriert einen **Raw-Input**-Horcher für Tastatur und Maus mit dem Flag `INPUTSINK` auf seinem Overlay-Fenster. Das heisst, er wird systemweit über Tasten- und Mausereignisse benachrichtigt, auch während das Spiel den Fokus hat. Nur so funktionieren globale Tastenkürzel über einem Vollbildspiel; es gibt keinen Weg, der diese Eigenschaft nicht hätte. Was mit den Ereignissen passiert: jedes Tastenereignis wird mit den registrierten Kürzeln verglichen und dann verworfen. Tastendrücke werden nicht gespeichert, nicht protokolliert und nicht übertragen. Es gibt keine Low-Level-Tastaturhooks (`SetWindowsHookEx`).

Zwei Dinge können Eingaben *erzeugen*, beide nur auf Anforderung: Wenn ein Addon ein interaktives Fenster öffnet und den Kern bittet, die Spieleingabe zu blockieren, simuliert der Kern einen Mausklick, um diesem Fenster den Fokus zu geben; und einzelne Addons können selbst Eingaben senden (siehe Tabelle in Abschnitt 5).

### Bildschirm

Der Kern kann mit `CopyFromScreen` ein Bildschirmfoto machen, aber nur, wenn ein Addon über die Host-API eines anfordert. Von sich aus tut der Kern das nie. Er liest nicht den Speicher des Spiels, injiziert nichts in den Spielprozess und hängt sich nicht in dessen Renderer: Das Overlay ist ein gewöhnliches, von Windows gezeichnetes Fenster im Vordergrund.

## 4. Addons: das Vertrauensmodell, klar gesagt

Ein Addon ist eine .NET-Assembly, die SCOverlay **in seinen eigenen Prozess mit vollem Vertrauen** lädt. Es gibt keine Sandbox, kein Berechtigungsmanifest und keine Fähigkeitsprüfung. Ein Addon kann technisch alles, was dein Windows-Benutzerkonto kann: Dateien lesen und schreiben, Netzwerkverbindungen öffnen, Eingaben lesen und senden, Bildschirmfotos machen. Die Host-API bietet für manches davon Bequemlichkeit (Bildschirmfotos, Eingabeblockierung, Tastenkürzel, Einstellungen), aber sie ist keine Schranke; ein Addon braucht die API für nichts davon.

Ich sage das lieber offen, als ein Berechtigungsmodell anzudeuten, das es nicht gibt. Die Folgen:

- **Ein Addon zu installieren heisst, seinem Autor vollständig zu vertrauen.** Die SHA-256-Prüfung belegt nur, dass du die Datei bekommen hast, die der Server veröffentlicht hat.
- **Zwischen einem Eintrag und deinem Rechner steht der Betreuer.** Jedes Addon, das derzeit in der Gallery steht, ist von mir aus Quellcode gebaut und veröffentlicht, der mir vorliegt: zehn der elf sind meine eigenen, BetterPicture stammt von P-WHITE und wird von mir aus dessen Quellcode gebaut. In der Gallery liegt keine fremde Binärdatei, die ich nicht selbst übersetzt habe. Addon-Updates laufen denselben Weg, eine neue Fassung eines Addons erreicht also niemanden, ohne durch meine Hände zu gehen.
- **Regel für die Gallery:** gelistet wird nur, was ich im Quellcode lesen und selbst bauen kann. Ändert sich das, ändert sich zuerst dieses Dokument.
- Der **Performance Watchdog** kann ein Addon entladen, das das Overlay ausbremst. Das ist eine Leistungsfunktion, keine Sicherheitsgrenze.
- Du kannst ein Addon unter *Einstellungen → Addons* abschalten oder seinen Ordner unter `%AppData%\SCOverlay\addons\` löschen. Beides wirkt beim nächsten Start.

Ein echtes Berechtigungs- oder Manifestsystem müsste vom Host durchgesetzt werden, und bei .NET im selben Prozess kann ich das nicht ehrlich versprechen. Sollte je eines dazukommen, wird es hier beschrieben, einschliesslich dessen, was es durchsetzen kann und was nicht.

## 5. Was jedes gelistete Addon tut

Alle Addons unten stehen zum Prüfdatum in der Gallery. „Kontaktiert" nennt jeden externen Host, mit dem das Addon Verbindung aufnimmt; „Liest" nennt Spieldateien, die es liest.

| Addon | Kontaktiert | Liest | Sendet Eingaben | Bildschirmfotos | Anmerkung |
|---|---|---|---|---|---|
| ExecTimer | `scoverlay.it-en.ch` | – | – | – | Holt den Anker des Hangar-Zyklus und die Serverzeit. |
| QuickSheets | – | Bilder, die du in seinen `sheets`-Ordner legst | – | – | Vollständig offline. |
| BetterPicture | – | – | Ja, ein Klick, um sein eigenes Fenster zu fokussieren | Ja, das ist sein Zweck | Fotomodus; die Bilder bleiben auf deiner Platte. |
| CitizenHauler | `api.uexcorp.space` | – | – | Ja, im Fenster der Routenführung | Spricht die UEX-Corp-API direkt für Handelsdaten an. |
| OreScout | `scoverlay.it-en.ch` | – | – | – | Bergbau-Nachschlagedaten, lokal zwischengespeichert. |
| RepTracker | – | `Game.log`, `global.ini` | – | Ja, wenn du einen Rufbalken misst | Alles bleibt lokal. |
| Wingman | – | `Game.log` | Ja: drückt die Annahmetaste und kann das Spiel nach vorn holen | – | Nur solange eingeschaltet; startet bei jedem Start ausgeschaltet. |
| Omnia | `scoverlay.it-en.ch`; Bilder bei Bedarf von `starcitizen.tools` / `cstone.space` | `global.ini` | – | – | Der Suchindex wird einmal geladen und zwischengespeichert. |
| Workbench | `scoverlay.it-en.ch`; Bilder bei Bedarf von `starcitizen.tools` / `cstone.space` | `Game.log` (inkl. Backups), `global.ini` | – | – | Der Bauplan-Besitz wird lokal aus deinen Logs abgeleitet. |
| OrgaStorage | `scoverlay.it-en.ch` | – | – | – | Optionale Kopplung mit deinem Website-Konto über einen Einmalcode. Das Geräte-Token liegt DPAPI-verschlüsselt unter deinem Windows-Benutzer, nie in `settings.json`. |
| MouseMover | – | – | Ja: bewegt die Maus, wenn du untätig bist | – | Liest den *Zustand* von Tastatur, Maus und Joystick, um Untätigkeit zu erkennen; nichts wird aufgezeichnet. |

Die `Game.log` von Star Citizen enthält deinen Charakternamen und die Namen von Spielern in deiner Nähe. Addons, die sie lesen, tun das lokal; keines der Addons oben lädt sie hoch.

## 6. Eine Sicherheitslücke melden

Bitte öffne ein Issue in diesem Repository mit **„Security"** im Titel und **ohne technische Details** im öffentlichen Text. Ich antworte mit einem privaten Kanal. Meldungen zu Addons sind hier ebenfalls willkommen.

## 7. Änderungen an diesem Dokument

- 09.09.2026: erste Fassung.
