<p align="center">
<!-- Readme Links -->
<a href="README.md"><img src="https://img.shields.io/badge/Readme-555?style=for-the-badge" alt="Readme"></a><!--
--><a href="README.md"><img src="https://img.shields.io/badge/EN-555?style=for-the-badge" alt="English"></a><!--
--><a href="README.de.md"><img src="https://img.shields.io/badge/DE-ff6f00?style=for-the-badge" alt="Deutsch"></a>
&nbsp;&nbsp;|&nbsp;&nbsp;
<!-- Manual Links -->
<a href="MANUAL.md"><img src="https://img.shields.io/badge/Manual-555?style=for-the-badge" alt="Manual"></a><!--
--><a href="MANUAL.md"><img src="https://img.shields.io/badge/EN-555?style=for-the-badge" alt="English"></a><!--
--><a href="MANUAL.de.md"><img src="https://img.shields.io/badge/DE-ff6f00?style=for-the-badge" alt="Deutsch"></a>
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
<p><strong>Entwicklerhandbuch & API-Leitfaden v3.1</strong></p>
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
    *   [Core-Dienste](#core-dienste)
    *   [Hotkeys & Eingabe](#hotkeys--eingabe)
    *   [Persistenz (Daten speichern)](#persistenz-daten-speichern)
    *   [Logging & Lokalisierung](#logging--lokalisierung)
    *   [Theming (Styling deiner UI)](#theming-styling-deiner-ui)
    *   [Performance-Management](#performance-management)
*   [Einstellungs-UIs erstellen: Von einfach bis leistungsstark](#kapitel-5-einstellungs-uis-erstellen-von-einfach-bis-leistungsstark)
    *   [Methode 1: Das Baukasten-System (Einfach/Legacy)](#methode-1-das-baukasten-system-einfachlegacy)
    *   [Methode 2: Völlige UI-Freiheit (UserControl - Empfohlen)](#methode-2-völlige-ui-freiheit-usercontrol---empfohlen)
*   [Fortgeschrittene Konzepte & Best Practices](#kapitel-6-fortgeschrittene-konzepte--best-practices)
    *   [Lizenzierung für Premium-Addons](#lizenzierung-für-premium-addons)
    *   [Dos & Don'ts](#dos--donts)
*   [Fehlerbehebung: Häufige Probleme lösen](#kapitel-7-fehlerbehebung-häufige-probleme-lösen)
*   [Werde Teil der Entwicklung!](#kapitel-8-werde-teil-der-entwicklung)
    *   [Wo du Hilfe findest](#wo-du-hilfe-findest)
    *   [Gestalte die Zukunft der API!](#gestalte-die-zukunft-der-api)
    *   [Schlage ein lizenziertes Addon vor](#schlage-ein-lizenziertes-addon-vor)

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
2.  API-Referenz hinzufügen: Rechtsklick auf `Abhängigkeiten > Projektverweis hinzufügen...` und wähle das `SCOverlay.API`-Projekt. Wenn du nur die DLL hast, verwende `Assemblyverweis hinzufügen...`.
3.  **WICHTIG:** Klicke auf den `SCOverlay.API`-Verweis, drücke `F4` für Eigenschaften und setze "Lokale Kopie" auf "Nein" (False). Dies verhindert Konflikte.

### Dein erster Code ("Hallo Welt")

Das ist alles, was du für ein funktionsfähiges Addon brauchst. Kopiere diesen Code in deine `Class1.cs`-Datei.
```csharp
// Using-Anweisungen sagen deinem Code, welche Werkzeugkisten er verwenden soll.
using SCOverlay.API;
using System.Collections.Generic;
using System.Drawing;
using System.Windows.Forms; // Wird für UserControl benötigt

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
        public IEnumerable<AddonControl> GetSettingsControls() => [];
        public IDictionary<string, (string en, string de)> GetLocalizations() => new Dictionary<string, (string, string)>();
        public void Draw(Graphics g, Rectangle bounds) { }
        public void OnOverlayVisibilityChanged(bool isVisible) { }
        public void Shutdown() { }
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
| `GetSettingsControl(IAddonHost host)` | `UserControl?`                    | **(Neu & Empfohlen)** Stellt ein komplettes, benutzerdefiniertes UI-Panel für deine Einstellungen bereit. Gibt dir totale kreative Freiheit. Siehe Kapitel 5. |
| `GetSettingsControls()`       | `IEnumerable<AddonControl>`       | **(Einfach/Legacy)** Eine begrenzte Möglichkeit, grundlegende Steuerelemente zur Einstellungsseite hinzuzufügen. Ein guter Fallback für sehr einfache Bedürfnisse.         |
| `Draw(Graphics g, ...)`       | `void`                            | **Zeichen-Engine:** Wird bei jedem Neuzeichnen des Overlays aufgerufen. Halte diesen Code extrem schnell!                     |
| `OnOverlayVisibilityChanged(...)` | `void`                            | **Zustandssynchronisierung:** Reagiert auf das Öffnen/Schließen des Overlays. Nützlich zum Starten/Stoppen von Hintergrundaufgaben. |
| `Shutdown()`                  | `void`                            | **Aufräumen:** Wird vor dem Entladen aufgerufen. Gib hier alle Ressourcen frei (z. B. Events deabonnieren), um Speicherlecks zu vermeiden. |
| `GetLocalizations()`          | `IDictionary<...>`                | **Lokalisierung:** Stelle englische und deutsche Übersetzungen für die UI-Texte deines Addons bereit.                         |
| `OnGlobalHotkey()`            | `void`                            | **(Fortgeschritten)** Ein spezieller Callback, der ausgelöst wird, wenn dein Addon die exklusive Kontrolle über den Haupt-Hotkey hat. |

## Kapitel 4: Der IAddonHost: Deine Werkzeugkiste für den Core

Der `IAddonHost` ist deine Brücke zu allen Funktionen von SCOverlay. Stell ihn dir als eine Werkzeugkiste voller leistungsstarker Werkzeuge vor, die du verwenden kannst.

### Menü- und UI-Steuerung

*   `void TakeMenuControl(...)`: Übernimmt die exklusive Kontrolle über das Hauptmenü, um deine eigenen Untermenüs zu erstellen.
*   `void ReleaseMenuControl()`: Gibt die Kontrolle an das Hauptmenü zurück.
*   `void InvalidateOverlay()`: Erzwingt ein sofortiges Neuzeichnen. Entscheidend, um deine UI-Änderungen sichtbar zu machen.
*   `void HideMenu()`: Schließt das gesamte Overlay-Menü programmatisch.

### Core-Dienste

*   `ISoundService Sound { get; }`
    *   `PlayFile(...)`: Spielt eine Sounddatei asynchron ab, ohne das Overlay einzufrieren.
*   `IWindowService Window { get; }`
    *   `ShowNotification(...)`: Zeigt eine kurze, nicht blockierende "Toast"-Benachrichtigung an.
    *   `CreateThemedWindow(...)`: Erstellt ein neues, leeres Fenster, das automatisch das aktuelle Overlay-Theme verwendet.
    *   `Show/HideFilterOverlay(...)`: Zeigt einen bildschirmweiten Farbfilter an oder verbirgt ihn, z. B. für einen "Nachtmodus".
    *   `Task<Image> TakeScreenshotAsync()`: Erstellt asynchron einen Screenshot des Spielbildschirms.

### Hotkeys & Eingabe

*   `bool RequestExclusiveHotkeyControl(...) / void ReleaseExclusiveHotkeyControl(...):` Übernimmt vorübergehend den Haupt-Hotkey des Overlays. Perfekt für Funktionen wie "Push-to-Talk" oder einen Screenshot-Modus, bei dem sich das Overlay nicht schließen soll.

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

## Kapitel 5: Einstellungs-UIs erstellen: Von einfach bis leistungsstark

Du hast zwei Möglichkeiten, eine Einstellungsseite für dein Addon zu erstellen. Wähle die, die zu deinen Anforderungen passt.

### Methode 1: Das Baukasten-System (Einfach/Legacy)

Mit `GetSettingsControls()` gibst du dem Core eine Liste einfacher Bausteine (`AddonControl`, `HotkeyControl`). Der Core stapelt sie dann vertikal für dich.

*   **Vorteile:** Sehr einfach für grundlegende Bedürfnisse.
*   **Nachteile:** Extrem eingeschränkt. Keine Schieberegler, Textfelder oder benutzerdefinierten Layouts.

```csharp
// Dies gehört in deine IAddon-Klasse
public IEnumerable<AddonControl> GetSettingsControls()
{
    // Ein einfacher Button
    yield return new AddonControl(
        id: "meinaddon_reset_button", 
        label: "Statistik zurücksetzen", 
        type: "RebindButton", // Dieser Typ ist für einfache Buttons
        getValue: () => "", 
        onClick: () => { /* Reset-Logik hier */ }
    );
    
    // Ein spezielles Steuerelement zum Binden eines Hotkeys
    yield return new HotkeyControl(
        identifier: "meinaddon_hotkey_ctrl", 
        label: "Spezial-Aktion Hotkey", 
        hotkeyIdentifier: "MeinAddon_Aktion1", // Der Schlüssel zum Speichern der Einstellung
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
Verwende den visuellen Designer, um Steuerelemente wie `Label`, `TextBox`, `TrackBar` (Schieberegler) usw. auf dein Panel zu ziehen.

#### 2. Implementiere den Code

Deine `IAddon`-Klasse gibt jetzt einfach eine Instanz deines neuen Panels zurück:
```csharp
// In deiner IAddon-Hauptklasse
public UserControl? GetSettingsControl(IAddonHost host)
{
    // Erstelle und gib einfach dein benutzerdefiniertes UI-Panel zurück.
    // Übergib den 'host', damit es die Theme-Farben verwenden kann!
    return new MeineEinstellungenPanel(host);
}

// Und lasse die alte Methode leer
public IEnumerable<AddonControl> GetSettingsControls() => [];
```

Der Code für deine `MeineEinstellungenPanel.cs` wird so aussehen. Der Schlüssel ist, **das Theme des Cores auf deine benutzerdefinierte UI anzuwenden.**
```csharp
// In deiner MeineEinstellungenPanel.cs-Datei
using SCOverlay.API;
using System.Drawing; // Benötigt für Color und Point
using System.Windows.Forms;

public partial class MeineEinstellungenPanel : UserControl
{
    private readonly IAddonHost _host;
    private Label infoLabel;
    private TrackBar volumeSlider;

    public MeineEinstellungenPanel(IAddonHost host)
    {
        InitializeComponent(); // Lädt die Steuerelemente aus dem Designer (falls du ihn verwendest)
        _host = host;

        // --- Steuerelemente programmatisch erstellen ---
        infoLabel = new Label { Text = "Lautstärke einstellen:", Location = new Point(10, 15) };
        volumeSlider = new TrackBar { Location = new Point(10, 40), Width = 200, Maximum = 100 };
        this.Controls.Add(infoLabel);
        this.Controls.Add(volumeSlider);
        
        ApplyTheme(); // Wende das Theme des Cores auf deine UI an
    }

    private void ApplyTheme()
    {
        // Verwende das Theme vom Host, um deine Steuerelemente zu gestalten
        this.BackColor = _host.Theme_Background;
        this.infoLabel.ForeColor = _host.Theme_Text;
        this.infoLabel.Font = _host.Theme_TextFont;
        this.volumeSlider.TickColor = _host.Theme_Accent;
    }
}
```
Dieser Ansatz ermöglicht dir eine professionelle, vollständig benutzerdefinierte Einstellungs-UI, die immer noch perfekt zum Erscheinungsbild von SCOverlay passt.

## Kapitel 6: Fortgeschrittene Konzepte & Best Practices

### Lizenzierung für Premium-Addons

Möchtest du dein Addon für Unterstützer anbieten? Das SCOverlay-System ist dafür ausgelegt. Dies ist ein kollaborativer Prozess. Du kannst eine `LicenseId` nicht selbst erfinden; sie muss vom SCOverlay-Team generiert und in den Core integriert werden.

Der Prozess:

1.  **Entwickle dein Addon:** Konzentriere dich zuerst auf die Entwicklung deines Addons.
2.  **Kontaktiere uns:** Wenn es fertig ist, kontaktiere den Ersteller (BlugDeg) über ein GitHub-Issue (siehe Kapitel 8).
3.  **Integration:** Wir werden mit dir zusammenarbeiten, um eine eindeutige `LicenseId` auf dem Lizenzserver zu erstellen und sie in das nächste SCOverlay-Release zu integrieren.
4.  **Implementierung:** Du erhältst die offizielle ID von uns. Erst dann fügst du das Attribut zu deiner Addon-Klasse hinzu.
```csharp
// Beispiel: Du hast die ID "MeinSuperAddon" vom Ersteller erhalten.
[Addon(LicenseId = "MeinSuperAddon")]
public class MeinPremiumAddon : IAddon { /* ... */ }
```
### Dos & Don'ts

*   ✅ **Events deabonnieren:** Deabonniere in deiner `Shutdown()`-Methode immer Events wie `host.OnPaintOverlay -= MeineZeichenMethode;`, um Speicherlecks zu vermeiden.
*   ❌ **Blockiere niemals `Draw()`:** Führe keine Datei-E/A, Netzwerkanfragen oder langen Schleifen in der `Draw`-Methode aus. Dies führt zu Ruckeln.
*   ❌ **Gehe nicht von einem UI-Thread aus:** Wenn du die UI aus einem Hintergrund-Task aktualisierst, verwende `meinControl.BeginInvoke(...)`, um Abstürze zu vermeiden.

## Kapitel 7: Fehlerbehebung: Häufige Probleme lösen

**"Mein Addon erscheint nicht im Menü!"**

*   **Falsche Ordnerstruktur:** Der Ordner in `%AppData%\SCOverlay\addons` muss exakt denselben Namen haben wie deine DLL-Datei (ohne `.dll`).
*   **"Lokale Kopie" ist True:** Der `SCOverlay.API`-Verweis muss "Lokale Kopie" auf "Nein" (False) gesetzt haben.
*   **Startfehler:** Überprüfe die `debug.log` in `%AppData%\SCOverlay\`. Ein Fehler in deiner `Initialize`-Methode verhindert das Laden des Addons.

**"Meine UI-Änderung wird nicht angezeigt!"**

*   **Lösung:** Du musst `_host?.InvalidateOverlay();` aufrufen, nachdem du etwas geändert hast, das visuell aktualisiert werden soll.

**"Mein Addon verschwindet plötzlich!"**

*   **Ursache:** Der Performance Watchdog hat dein Addon entladen, weil es zu viel CPU verbraucht hat.
*   **Lösung:** Optimiere deinen Code (besonders `Draw()`). Für kurze, absichtlich rechenintensive Aufgaben, umschließe sie mit `RequestHighPerformanceMode`.

## Kapitel 8: Werde Teil der Entwicklung!

Dein Beitrag ist wertvoll. Deine Ideen und deine Hilfe sind immer willkommen.

### Wo du Hilfe findest

➡️ **Stelle eine Frage im `developer-need-help`-Channel**
Erstelle ein neues Issue mit diesem Label. Keine Frage ist zu einfach!

### Gestalte die Zukunft der API!

➡️ **Schlage ein neues API-Feature vor**
Wenn du eine Idee für ein neues Werkzeug in der `IAddonHost`-Werkzeugkiste hast, lass es uns wissen!

### Schlage ein lizenziertes Addon vor

➡️ **Fordere eine neue Lizenz-ID an**
Erstelle ein Issue, um dein Premium-Addon-Projekt vorzustellen.

Wir sind gespannt, was du erschaffen wirst
