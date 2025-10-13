<p align="center">
<!-- Readme Links -->
<a href="README.md"><img src="https://img.shields.io/badge/Readme-555?style=for-the-badge" alt="Readme"></a><!--
--><a href="README.md"><img src="https://img.shields.io/badge/EN-555?style=for-the-badge" alt="English"></a><!--
--><a href="README.de.md"><img src="https://img.shields.io/badge/DE-555?style=for-the-badge" alt="Deutsch"></a>
&nbsp;&nbsp;|&nbsp;&nbsp;
<!-- Manual Links -->
<a href="MANUAL.md"><img src="https://img.shields.io/badge/Manual-555?style=for-the-badge" alt="Manual"></a><!--
--><a href="MANUAL.md"><img src="https://img.shields.io/badge/EN-555?style=for-the-badge" alt="English"></a><!--
--><a href="MANUAL.de.md"><img src="https://img.shields.io/badge/DE-555?style=for-the-badge" alt="Deutsch"></a>
&nbsp;&nbsp;|&nbsp;&nbsp;
<!-- Developer/SDK Links -->
<a href="SDK_MANUAL.md"><img src="https://img.shields.io/badge/Developer-007bff?style=for-the-badge" alt="Developer"></a><!--
--><a href="SDK_MANUAL.md"><img src="https://img.shields.io/badge/EN-555?style=for-the-badge" alt="English"></a><!--
--><a href="SDK_MANUAL.de.md"><img src="https://img.shields.io/badge/DE-ff6f00?style=for-the-badge" alt="Deutsch"></a>
</p>
<div align="center">
<br>
<svg width="120" height="120" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
<path d="M12 21C16.9706 21 21 16.9706 21 12C21 7.02944 16.9706 3 12 3C7.02944 3 3 7.02944 3 12C3 16.9706 7.02944 21 12 21Z" stroke="#4a90e2" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" opacity="0.4"/>
<path d="M12 17V12" stroke="#4a90e2" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
<path d="M12 3C12 3 15 6 15 9C15 12 12 17 12 17" stroke="#4a90e2" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
<path d="M12 3C12 3 9 6 9 9C9 12 12 17 12 17" stroke="#4a90e2" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
</svg>
<h1>SCOverlay Addon SDK</h1>
<p><strong>Entwicklerhandbuch & API-Leitfaden (API v1.1 / Core v0.0.1.7+)</strong></p>
<br>
</div>

## Inhaltsverzeichnis
*   [Unsere Vision: Eine Plattform für Entwickler](#kapitel-1-unsere-vision-eine-plattform-für-entwickler)
*   [Erste Schritte: Dein erstes Addon](#kapitel-2-erste-schritte-dein-erstes-addon)
    *   [Voraussetzungen & Setup](#voraussetzungen--setup)
    *   [Dein erster Code ("Hallo Welt")](#dein-erster-code-hallo-welt)
    *   [Deployment (Bereitstellung)](#deployment-bereitstellung)
*   [Das IAddon-Interface: Die DNA deines Addons](#kapitel-3-das-iaddon-interface-die-dna-deines-addons)
*   [Der IAddonHost: Deine Werkzeugkiste für den Core](#kapitel-4-der-iaddonhost-deine-werkzeugkiste-für-den-core)
    *   [Menü- und UI-Steuerung](#menü--und-ui-steuerung)
    *   [Core-Dienste & Fenster](#core-dienste--fenster)
    *   [Hotkeys & Eingabe (Neu & Leistungsstark)](#hotkeys--eingabe-neu--leistungsstark)
    *   [Persistenz (Daten speichern)](#persistenz-daten-speichern)
    *   [Logging & Lokalisierung](#logging--lokalisierung)
    *   [Theming (Styling deiner UI)](#theming-styling-deiner-ui)
    *   [Performance-Management](#performance-management)
*   [Fortgeschrittenes Tutorial: Den Core-Hotkey übernehmen](#kapitel-5-fortgeschrittenes-tutorial-den-core-hotkey-übernehmen)
    *   [Schritt 1: Die Logik vorbereiten](#schritt-1-die-logik-vorbereiten)
    *   [Schritt 2: Die Kontrolle anfordern](#schritt-2-die-kontrolle-anfordern)
    *   [Schritt 3: Auf den Hotkey reagieren](#schritt-3-auf-den-hotkey-reagieren)
    *   [Schritt 4: Die Kontrolle zurückgeben](#schritt-4-die-kontrolle-zurückgeben)
*   [Einstellungs-UIs erstellen: Von einfach bis leistungsstark](#kapitel-6-einstellungs-uis-erstellen-von-einfach-bis-leistungsstark)
    *   [Methode 1: Das Baukasten-System (Einfach/Legacy)](#methode-1-das-baukasten-system-einfachlegacy)
    *   [Methode 2: Völlige UI-Freiheit (UserControl - Empfohlen)](#methode-2-völlige-ui-freiheit-usercontrol---empfohlen)
*   [Fortgeschrittene Konzepte & Best Practices](#kapitel-7-fortgeschrittene-konzepte--best-practices)
    *   [Lizenzierung für Premium-Addons](#lizenzierung-für-premium-addons)
    *   [Dos & Don'ts](#dos--donts)
*   [Fehlerbehebung: Häufige Probleme lösen](#kapitel-8-fehlerbehebung-häufige-probleme-lösen)
*   [Werde Teil der Entwicklung!](#kapitel-9-werde-teil-der-entwicklung)

---

## Kapitel 1: Unsere Vision: Eine Plattform für Entwickler

Willkommen, Entwickler! SCOverlay ist mehr als nur ein Werkzeug – es ist ein Ökosystem. Unsere Vision ist es, eine stabile, performante und vor allem erweiterbare Plattform zu schaffen, auf der kreative Köpfe wie du aufbauen können. Du musst kein professioneller Programmierer sein, um etwas Erstaunliches zu schaffen. Dieser Leitfaden ist hier, um dich bei jedem Schritt zu unterstützen.

*   **Modularität:** Der Core stellt die Bühne bereit; dein Addon ist der Star.
*   **Stabilität & Performance:** Als Game-Overlay ist die Leistung entscheidend. Wir schützen das Spielerlebnis, damit du dich auf die Features konzentrieren kannst.
*   **Strikter Vertrag:** Die `SCOverlay.API.dll` ist unser gemeinsames Fundament. Es ist ein Versprechen, dass deine Arbeit auch über Updates hinweg funktionsfähig bleibt.

## Kapitel 2: Erste Schritte: Dein erstes Addon

### Voraussetzungen & Setup

*   **Visual Studio 2022** (die kostenlose Community Edition ist perfekt) mit dem ".NET-Desktopentwicklung"-Workflow.
*   **.NET 8 SDK** oder neuer.
*   Die `SCOverlay.API.dll` aus dem neuesten SCOverlay-Release.

1.  Erstelle ein "Klassenbibliothek"-Projekt in Visual Studio für C# (.NET 8).
2.  API-Referenz hinzufügen: Rechtsklick auf `Abhängigkeiten > Assemblyverweis hinzufügen...` und wähle die `SCOverlay.API.dll`.
3.  **WICHTIG:** Klicke auf den `SCOverlay.API`-Verweis, drücke `F4` für Eigenschaften und setze "Lokale Kopie" auf "Nein" (False). Dies verhindert Konflikte.

### Dein erster Code ("Hallo Welt")

Das ist alles, was du für ein funktionsfähiges Addon brauchst. Kopiere diesen Code in deine `Class1.cs`-Datei.
```csharp
// Using-Anweisungen sagen deinem Code, welche Werkzeugkisten er verwenden soll.
using SCOverlay.API;
using System.Collections.Generic;
using System.Drawing;
using System.Windows.Forms; // Notwendig für UserControl

namespace MeinErstesAddon
{
    // Das [Addon]-Attribut markiert diese Klasse als Einstiegspunkt für SCOverlay.
    [Addon]
    public class MeinErstesAddon : IAddon
    {
        private IAddonHost? _host; // Eine private Variable, um die "Werkzeugkiste" vom Core zu speichern.

        // --- Grundlegende Informationen ---
        public string Name => "Mein Erstes Addon";
        public string Author => "Dein Name";
        public string Version => "1.0.0";

        // Dies ist wie der Konstruktor. Er wird einmal aufgerufen, wenn dein Addon geladen wird.
        public void Initialize(IAddonHost host)
        {
            _host = host; // Speichere den Host für die spätere Verwendung.
            _host.LogInfo($"[{Name}] wurde erfolgreich initialisiert!");
        }

        // Diese Methode fügt Buttons zum Hauptmenü von SCOverlay hinzu.
        public IEnumerable<AddonButton> GetMainMenuButtons()
        {
            // 'yield return' ist eine einfache Möglichkeit, ein Element nach dem anderen zu einer Liste hinzuzufügen.
            yield return new AddonButton(
                id: "mein_addon_hallo_button",
                getLabel: () => "Sag Hallo", // Der Text auf dem Button.
                onClick: () => _host?.Window.ShowNotification("Hallo von meinem Addon!") // Was bei einem Klick passiert.
            );
        }

        // --- Vorerst lassen wir die anderen erforderlichen Methoden leer ---
        public IDictionary<string, (string en, string de)> GetLocalizations() => new Dictionary<string, (string, string)>();
        public void Draw(Graphics g, Rectangle bounds) { }
        public void OnOverlayVisibilityChanged(bool isVisible) { }
        public void Shutdown() { }
        public IEnumerable<AddonControl> GetSettingsControls() => []; // Legacy-Methode, kann leer bleiben
        public UserControl? GetSettingsControl(IAddonHost host) => null; // Empfohlene Methode, kann null zurückgeben
    }
}
```
### Deployment (Bereitstellung)

Kopiere deine kompilierte `.dll`-Datei in einen Unterordner mit demselben Namen in `%AppData%\SCOverlay\addons`.

**Struktur:** `%AppData%\SCOverlay\addons\MeinErstesAddon\MeinErstesAddon.dll`

<div class="note">
<strong>Du kommst nicht weiter? Wir sind für dich da!</strong><br>
Wenn etwas unklar ist, erstelle ein neues Issue auf GitHub mit dem <code>developer-need-help</code>-Tag. Es gibt keine dummen Fragen!
</div>

## Kapitel 3: Das IAddon-Interface: Die DNA deines Addons

Dies ist die Blaupause für jedes Addon. Deine Hauptklasse muss alle diese Member implementieren.

| Member                        | Typ                              | Zweck & Detaillierte Erklärung                                                                                                 |
| :---------------------------- | :-------------------------------- | :----------------------------------------------------------------------------------------------------------------------------- |
| `Name`, `Author`, `Version`   | `string`                          | **Metadaten:** Identifiziert dein Addon.                                                                                           |
| `Initialize(IAddonHost host)` | `void`                            | **Konstruktor:** Wird einmal beim Laden aufgerufen. Speichere hier die Host-Instanz. Dies ist deine Setup-Phase.                 |
| `GetMainMenuButtons()`        | `IEnumerable<AddonButton>`        | **Hauptmenü-Buttons:** Definiert die Buttons, die dein Addon im Hauptmenü anzeigt.                                              |
| `OnExclusiveHotkey()`         | `void`                            | **(NEU)** Der Callback, den der Core aufruft, wenn du die exklusive Hotkey-Kontrolle hast und der Hotkey gedrückt wird. Hat eine leere Standardimplementierung, ist also optional. |
| `GetSettingsControl(...)` | `UserControl?`                    | **(Empfohlen)** Stellt ein komplettes, benutzerdefiniertes UI-Panel für deine Einstellungen bereit. Gibt dir totale kreative Freiheit. Siehe Kapitel 6. |
| `GetSettingsControls()`       | `IEnumerable<AddonControl>`       | **(Legacy)** Eine begrenzte Möglichkeit, grundlegende Steuerelemente zur Einstellungsseite hinzuzufügen. Nur für sehr einfache Addons ohne UI-Ansprüche. |
| `Draw(Graphics g, ...)`       | `void`                            | **Zeichen-Engine:** Wird bei jedem Neuzeichnen des Overlays aufgerufen. Halte diesen Code extrem schnell!                     |
| `OnOverlayVisibilityChanged(...)` | `void`                            | **Zustandssynchronisierung:** Reagiert auf das Öffnen/Schließen des Overlays. Nützlich zum Starten/Stoppen von Hintergrundaufgaben. |
| `Shutdown()`                  | `void`                            | **Aufräumen:** Wird vor dem Entladen aufgerufen. Gib hier alle Ressourcen frei (z.B. Fenster schließen), um Fehler zu vermeiden. |
| `GetLocalizations()`          | `IDictionary<...>`                | **Lokalisierung:** Stelle englische und deutsche Übersetzungen für die UI-Texte deines Addons bereit.                         |

## Kapitel 4: Der IAddonHost: Deine Werkzeugkiste für den Core

Der `IAddonHost` ist deine Brücke zu allen Funktionen von SCOverlay.

### Menü- und UI-Steuerung

*   `void TakeMenuControl(...)`: Übernimmt die exklusive Kontrolle über das Hauptmenü, um deine eigenen Untermenüs zu erstellen.
*   `void ReleaseMenuControl()`: Gibt die Kontrolle an das Hauptmenü zurück.
*   `void InvalidateOverlay()`: Erzwingt ein sofortiges Neuzeichnen. Entscheidend, um deine UI-Änderungen sichtbar zu machen.
*   `void HideMenu()`: **(NEU)** Schließt das gesamte Overlay-Menü programmatisch auf eine sichere Weise.

### Core-Dienste & Fenster

*   `ISoundService Sound { get; }`
    *   `PlayFile(...)`: Spielt eine Sounddatei asynchron ab, ohne das Overlay einzufrieren.
*   `IWindowService Window { get; }`
    *   `ShowNotification(...)`: Zeigt eine kurze, nicht blockierende "Toast"-Benachrichtigung an.
    *   `CreateThemedWindow(...)`: Erstellt ein neues, leeres, selbstgezeichnetes Fenster (wie das Haupt-Overlay). **Nicht für Standard-Controls wie Buttons geeignet.**
    *   `CreateStandardWindow(...)`: **(NEU)** Erstellt ein neues Fenster, das das Theme übernimmt und **perfekt für Standard-Controls** wie Buttons, Labels, etc. geeignet ist. Dies ist die richtige Wahl für interaktive Dialoge.
    *   `Show/HideFilterOverlay(...)`: Zeigt einen bildschirmweiten Farbfilter an oder verbirgt ihn.
*   `Task<Image> TakeScreenshotAsync()`: Erstellt asynchron einen Screenshot des Spielbildschirms.

### Hotkeys & Eingabe (Neu & Leistungsstark)

<div class="note" style="background-color: #e7f3fe; border-left: 6px solid #2196F3;">
<strong>Wichtige API-Änderung: Das exklusive Kontroll-System</strong><br>
Die alte, fehleranfällige `SuppressCoreHotkeys`-Methode wurde entfernt. Das neue System gibt dir die volle, aber sichere Kontrolle über den Haupt-Hotkey.
</div>

*   `bool RequestExclusiveHotkeyControl(IAddon addon)`:
    *   **Zweck:** Dies ist der neue Weg, um den Haupt-Hotkey des Overlays für dein Addon zu "kapern".
    *   **Funktion:** Du forderst die exklusive Kontrolle an. Wenn kein anderes Addon sie bereits hat, gibt die Methode `true` zurück. Ab diesem Moment werden alle Drücke des Haupt-Hotkeys an deine `OnExclusiveHotkey()`-Methode weitergeleitet.
*   `void ReleaseExclusiveHotkeyControl(IAddon addon)`:
    *   **Zweck:** Gibt die Kontrolle wieder an den Core zurück.
    *   **Funktion:** Wenn du fertig bist (z.B. dein Fenster geschlossen wird), musst du diese Methode aufrufen, damit das Haupt-Overlay wieder normal auf den Hotkey reagieren kann.
*   `void BlockGameInput(bool block)`:
    *   **Zweck:** Unverändert wichtig für interaktive UI. Blockiert oder gibt die Eingaben an das Spiel frei.
*   `RegisterHotkey`, `UnregisterHotkey`, `RebindHotkey`:
    *   **Zweck:** Für das Hinzufügen von **zusätzlichen, eigenen Hotkeys** für dein Addon, die unabhängig vom Core-Hotkey sind.

### Persistenz (Daten speichern)

*   `string GetSetting(...) & void SetSetting(...):` Ein einfacher Schlüssel-Wert-Speicher für dein Addon.
*   **Best Practice:** Verwende immer ein eindeutiges Präfix für deine Schlüssel (z. B. `MeinAddon_ApiToken`), um Konflikte zu vermeiden.

### Logging & Lokalisierung

*   `LogInfo(...) & LogError(...):` Schreibt in die zentrale `debug.log`. Dein wichtigstes Werkzeug zum Debuggen!
*   `string T(...):` Greift auf das zentrale Übersetzungssystem für mehrsprachige Texte zu.

### Theming (Styling deiner UI)

*   `Color Theme_Background { get; }`, `Font Theme_TextFont { get; }`, etc.: Schreibgeschützter Zugriff auf das aktive Theme. Unerlässlich, um deine benutzerdefinierte `UserControl`-Einstellungs-UI an den Rest des Overlays anzupassen.

### Performance-Management

*   `void RequestHighPerformanceMode(...) & void ReleaseHighPerformanceMode(...):` Teilt dem "Performance Watchdog" vorübergehend mit, während einer kurzen, CPU-intensiven Aufgabe nicht einzugreifen.

## Kapitel 5: Fortgeschrittenes Tutorial: Den Core-Hotkey übernehmen

Dieses Tutorial zeigt dir, wie du mit dem neuen System eine eigene UI anstelle des Hauptmenüs öffnest.

### Schritt 1: Die Logik vorbereiten

Definiere in deiner Addon-Klasse die Logik zum Starten und Stoppen deines exklusiven Modus.
```csharp
private IAddonHost? _host;
private Form? _meinExklusivesFenster;
private bool _hatKontrolle = false;

// Methode zum Starten des Modus (z.B. von einem Button-Klick)
private void StartExklusivModus()
{
    if (_host == null || _hatKontrolle) return;

    // 1. Kontrolle anfordern
    if (_host.RequestExclusiveHotkeyControl(this))
    {
        _hatKontrolle = true;
        _host.Window.ShowNotification("Kontrolle übernommen!");
        
        // 2. Core-Menü sicher verstecken
        _host.HideMenu();

        // 3. Eigenes Fenster anzeigen
        OeffneMeinFenster();
    }
}

// Methode zum Stoppen des Modus
private void StoppExklusivModus()
{
    if (_host == null || !_hatKontrolle) return;
    
    // 1. Fenster schließen
    _meinExklusivesFenster?.Close();
    _meinExklusivesFenster = null;

    // 2. Kontrolle zurückgeben
    _host.ReleaseExclusiveHotkeyControl(this);
    _hatKontrolle = false;
    _host.Window.ShowNotification("Kontrolle zurückgegeben!");
}

private void OeffneMeinFenster()
{
    // Verwende CreateStandardWindow für interaktive UI!
    _meinExklusivesFenster = _host.Window.CreateStandardWindow("Mein Panel");
    _meinExklusivesFenster.FormClosed += (s, e) => StoppExklusivModus(); // Failsafe!
    // ... füge hier deine Buttons etc. hinzu ...
    _meinExklusivesFenster.Show();
}
```
### Schritt 2: Auf den Hotkey reagieren

Implementiere die `OnExclusiveHotkey`-Methode. Sie wird nun vom Core aufgerufen.
```csharp
public void OnExclusiveHotkey()
{
    // Wenn das Fenster da ist, zeige/verstecke es. Wenn nicht, erstelle es.
    if (_meinExklusivesFenster != null && !_meinExklusivesFenster.IsDisposed)
    {
        _meinExklusivesFenster.Visible = !_meinExklusivesFenster.Visible;
    }
    else
    {
        OeffneMeinFenster();
    }
}
```
### Schritt 3: Die Kontrolle zurückgeben
Siehe `StoppExklusivModus()` oben. Der Aufruf von `_host.ReleaseExclusiveHotkeyControl(this)` ist der entscheidende Teil. Stelle sicher, dass dies passiert, wenn deine Funktion beendet wird (z.B. wenn der Benutzer dein Fenster schließt).

### Schritt 4 (Optional): Aufräumen

Stelle sicher, dass du in deiner `Shutdown()`-Methode den Modus beendest, um Fehler zu vermeiden.
###```csharp
public void Shutdown()
{
    // Stellt sicher, dass die Kontrolle beim Entladen immer zurückgegeben wird.
    StoppExklusivModus();
}
```
Dieses System ist robust, sicher und gibt dir die volle Kontrolle, wann und wie dein Addon auf den Haupt-Hotkey reagiert.

## Kapitel 6: Einstellungs-UIs erstellen: Von einfach bis leistungsstark

Du hast zwei Möglichkeiten, eine Einstellungsseite für dein Addon zu erstellen. Wähle die, die zu deinen Anforderungen passt.

### Methode 1: Das Baukasten-System (Einfach/Legacy)

Mit `GetSettingsControls()` gibst du dem Core eine Liste einfacher Bausteine (`AddonControl`, `HotkeyControl`). Der Core stapelt sie dann vertikal für dich.

*   **Vorteile:** Sehr einfach für grundlegende Bedürfnisse.
*   **Nachteile:** Extrem eingeschränkt. Keine Schieberegler, Textfelder oder benutzerdefinierten Layouts.

```csharp
public IEnumerable<AddonControl> GetSettingsControls()
{
    yield return new HotkeyControl(
        identifier: "meinaddon_hotkey_ctrl", 
        label: "Spezial-Aktion Hotkey", 
        hotkeyIdentifier: "MeinAddon_Aktion1",
        defaultHotkey: "Shift+F1"
    );
}
```
### Methode 2: Völlige UI-Freiheit (UserControl - Empfohlen)

Mit `GetSettingsControl(IAddonHost host)` erstellst du deine gesamte Einstellungsseite visuell im Visual Studio Designer und übergibst diese komplette UI an den Core. Dies ist der **moderne und empfohlene** Ansatz.

*   **Vorteile:** Totale kreative Freiheit. Verwende Schieberegler, Textfelder, Bilder, Dropdowns und ordne sie an, wie du möchtest.
*   **Nachteile:** Erfordert etwas mehr Einrichtung.

So wird's gemacht:

#### 1. Erstelle dein UserControl

Klicke in Visual Studio mit der rechten Maustaste auf dein Projekt > Hinzufügen > **Benutzersteuerelement (Windows Forms)**. Nenne es `MeineEinstellungenPanel.cs`.
Verwende den visuellen Designer, um Steuerelemente auf dein Panel zu ziehen.

#### 2. Implementiere den Code

Deine `IAddon`-Klasse gibt jetzt einfach eine Instanz deines neuen Panels zurück:

```csharp
// In deiner IAddon-Hauptklasse
public UserControl? GetSettingsControl(IAddonHost host)
{
    return new MeineEinstellungenPanel(host);
}

// Und lasse die alte Methode leer
public IEnumerable<AddonControl> GetSettingsControls() => [];
```
Der Code für deine `MeineEinstellungenPanel.cs` wendet das Theme des Cores auf deine UI an:

```csharp
// In deiner MeineEinstellungenPanel.cs-Datei
using SCOverlay.API;
using System.Windows.Forms;

public partial class MeineEinstellungenPanel : UserControl
{
    private readonly IAddonHost _host;

    public MeineEinstellungenPanel(IAddonHost host)
    {
        InitializeComponent(); // Lädt die Steuerelemente aus dem Designer
        _host = host;

        // Wende das Theme auf alle Steuerelemente an
        ApplyThemeToAllControls(this); 
    }

    private void ApplyThemeToAllControls(Control parent)
    {
        // Setze die Hintergrundfarbe des Panels
        parent.BackColor = _host.Theme_Background;

        foreach (Control control in parent.Controls)
        {
            control.ForeColor = _host.Theme_Text;
            control.Font = _host.Theme_TextFont;

            if (control is Button button)
            {
                var brush = _host.Theme_ButtonNormalBrush as System.Drawing.SolidBrush;
                if (brush != null) button.BackColor = brush.Color;
                button.FlatStyle = FlatStyle.Flat;
                button.FlatAppearance.BorderSize = 0;
            }
            
            // Rekursiv für Container-Controls wie GroupBox oder Panel
            if (control.HasChildren)
            {
                ApplyThemeToAllControls(control);
            }
        }
    }
}
```
Dieser Ansatz ermöglicht dir eine professionelle, vollständig benutzerdefinierte Einstellungs-UI, die immer noch perfekt zum Erscheinungsbild von SCOverlay passt.

## Kapitel 7: Fortgeschrittene Konzepte & Best Practices

### Lizenzierung für Premium-Addons

Möchtest du dein Addon für Unterstützer anbieten? Dies ist ein kollaborativer Prozess.

1.  **Entwickle dein Addon.**
2.  **Kontaktiere uns:** Wenn es fertig ist, kontaktiere den Ersteller (BlugDeg) über ein GitHub-Issue.
3.  **Integration:** Wir generieren eine eindeutige `LicenseId` für dich.
4.  **Implementierung:** Du fügst das Attribut zu deiner Addon-Klasse hinzu.

```csharp
[Addon(LicenseId = "MeinSuperAddon")]
public class MeinPremiumAddon : IAddon { /* ... */ }
```

### Dos & Don'ts

*   ✅ **Ressourcen freigeben:** Rufe `Dispose()` für alle Fenster oder UserControls auf, die du erstellst, normalerweise in deiner `Shutdown()`-Methode, um Speicherlecks zu vermeiden.
*   ❌ **Blockiere niemals `Draw()`:** Führe keine langen Operationen in `Draw` aus. Dies führt zu Ruckeln.
*   ❌ **Gehe nicht von einem UI-Thread aus:** Wenn du die UI aus einem Hintergrund-Task aktualisierst, verwende `meinControl.BeginInvoke(...)`.

## Kapitel 8: Fehlerbehebung: Häufige Probleme lösen

**"Mein Addon erscheint nicht im Menü!"**

*   **Falsche Ordnerstruktur:** Der Ordner in `%AppData%\SCOverlay\addons` muss exakt denselben Namen haben wie deine DLL-Datei (ohne `.dll`).
*   **"Lokale Kopie" ist True:** Der `SCOverlay.API`-Verweis muss "Lokale Kopie" auf "Nein" (False) gesetzt haben.
*   **Startfehler:** Überprüfe die `debug.log` in `%AppData%\SCOverlay\`.

**"Meine UI-Änderung wird nicht angezeigt!"**

*   **Lösung:** Du musst `_host?.InvalidateOverlay();` aufrufen, nachdem du etwas geändert hast, das visuell aktualisiert werden soll.

**"Mein Addon verschwindet plötzlich!"**

*   **Ursache:** Der Performance Watchdog oder der Hotkey-Failsafe hat dein Addon ausgeworfen.
*   **Lösung:** Überprüfe die `debug.log` auf `CRITICAL`-Meldungen. Dein Addon hat einen schweren Fehler verursacht.

## Kapitel 9: Werde Teil der Entwicklung!

Dein Beitrag ist wertvoll. Deine Ideen und deine Hilfe sind immer willkommen.
Erstelle ein Issue auf GitHub, um Hilfe zu erhalten oder Features vorzuschlagen. Wir sind gespannt, was du erschaffen wirst!
