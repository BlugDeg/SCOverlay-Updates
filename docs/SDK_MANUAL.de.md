<p align="center">
  <!-- Readme Links -->
  <a href="README.de.md"><img src="https://img.shields.io/badge/Readme-555?style=for-the-badge" alt="Readme"></a><!--
  --><a href="README.md"><img src="https://img.shields.io/badge/EN-555?style=for-the-badge" alt="English"></a><!--
  --><a href="README.de.md"><img src="https://img.shields.io/badge/DE-555?style=for-the-badge" alt="Deutsch"></a>
  &nbsp;&nbsp;|&nbsp;&nbsp;
  <!-- Manual Links -->
  <a href="MANUAL.de.md"><img src="https://img.shields.io/badge/Manual-555?style=for-the-badge" alt="Manual"></a><!--
  --><a href="MANUAL.md"><img src="https://img.shields.io/badge/EN-555?style=for-the-badge" alt="English"></a><!--
  --><a href="MANUAL.de.md"><img src="https://img.shields.io/badge/DE-555?style=for-the-badge" alt="Deutsch"></a>
  &nbsp;&nbsp;|&nbsp;&nbsp;
  <!-- Developer/SDK Links -->
  <a href="SDK_MANUAL.de.md"><img src="https://img.shields.io/badge/Developer-007bff?style=for-the-badge" alt="Developer"></a><!--
  --><a href="SDK_MANUAL.md"><img src="https://img.shields.io/badge/EN-555?style=for-the-badge" alt="English"></a><!--
  --><a href="SDK_MANUAL.de.md"><img src="https://img.shields.io/badge/DE-ff6f00?style=for-the-badge" alt="Deutsch"></a>
</p>
---

<div align="center">
  <br>
  <svg width="120" height="120" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
    <path d="M12 21C16.9706 21 21 16.9706 21 12C21 7.02944 16.9706 3 12 3C7.02944 3 3 7.02944 3 12C3 16.9706 7.02944 21 12 21Z" stroke="#4a90e2" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" opacity="0.4"/>
    <path d="M12 17V12" stroke="#4a90e2" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
    <path d="M12 3C12 3 15 6 15 9C15 12 12 17 12 17" stroke="#4a90e2" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
    <path d="M12 3C12 3 9 6 9 9C9 12 12 17 12 17" stroke="#4a90e2" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
  </svg>
  <h1>SCOverlay Addon SDK</h1>
  <p><strong>Umfassendes Entwicklerhandbuch v2.3</strong></p>
  <br>
</div>

## Inhaltsverzeichnis
*   [Unsere Vision: Eine Plattform für Kreative](#kapitel-1-unsere-vision-eine-plattform-für-kreative)
*   [Erste Schritte: Dein erstes Addon](#kapitel-2-erste-schritte-dein-erstes-addon)
    *   [Voraussetzungen & Einrichtung](#voraussetzungen--einrichtung)
    *   [Dein erster Code ("Hello World")](#dein-erster-code-hello-world)
    *   [Bereitstellung](#bereitstellung)
*   [Das IAddon-Interface: Die DNA deines Addons](#kapitel-3-das-iaddon-interface-die-dna-deines-addons)
*   [Der IAddonHost: Dein Werkzeugkasten für den Core](#kapitel-4-der-iaddonhost-dein-werkzeugkasten-für-den-core)
    *   [Menü- und UI-Steuerung](#menü--und-ui-steuerung)
    *   [Core-Dienste](#core-dienste)
    *   [Hotkeys & Eingabe](#hotkeys--eingabe)
    *   [Persistenz (Daten speichern)](#persistenz-daten-speichern)
    *   [Logging & Lokalisierung](#logging--lokalisierung)
    *   [Theming (UI gestalten)](#theming-ui-gestalten)
    *   [Performance-Management](#performance-management)
*   [Einstellungen-UIs erstellen: Von einfach bis leistungsstark](#kapitel-5-einstellungen-uis-erstellen-von-einfach-bis-leistungsstark)
    *   [Methode 1: Das Baukasten-System (Legacy)](#methode-1-das-baukasten-system-legacy)
    *   [Methode 2: Die Fertiggarage (UserControl - Empfohlen)](#methode-2-die-fertiggarage-usercontrol---empfohlen)
*   [Fortgeschrittene Konzepte & Best Practices](#kapitel-6-fortgeschrittene-konzepte--best-practices)
    *   [Lizenzierung für Premium-Addons](#lizenzierung-für-premium-addons)
    *   [Dos & Don'ts](#dos--donts)
*   [Fehlerbehebung: Häufige Probleme lösen](#kapitel-7-fehlerbehebung-häufige-probleme-lösen)
*   [Werde Teil der Entwicklung!](#kapitel-8-werde-teil-der-entwicklung)
    *   [Wo du Hilfe findest](#wo-du-hilfe-findest)
    *   [Gestalte die Zukunft der API mit!](#gestalte-die-zukunft-der-api-mit)
    *   [Schlage ein lizenziertes Addon vor](#schlage-ein-lizenziertes-addon-vor)

---

## Kapitel 1: Unsere Vision: Eine Plattform für Kreative

Willkommen, Entwickler! SCOverlay ist mehr als nur ein Werkzeug – es ist ein Ökosystem. Unsere Vision ist es, eine stabile, performante und vor allem erweiterbare Plattform zu schaffen, auf der kreative Köpfe wie du aufbauen können. Du musst kein professioneller Programmierer sein, um etwas Großartiges zu erschaffen. Dieser Guide hilft dir bei jedem Schritt.

*   **Modularität:** Der Core bietet die Bühne; dein Addon ist der Star.
*   **Stabilität & Performance:** Als Game-Overlay ist Performance alles. Wir schützen das Spielerlebnis, damit du dich auf Funktionen konzentrieren kannst.
*   **Strenger Vertrag:** Die `SCOverlay.API.dll` ist unser gemeinsames Fundament. Sie ist ein Versprechen, dass deine Arbeit auch über Updates hinweg funktioniert.

## Kapitel 2: Erste Schritte: Dein erstes Addon

### Voraussetzungen & Einrichtung

*   **Visual Studio 2022** (die kostenlose Community Edition ist perfekt) mit der Workload ".NET Desktopentwicklung".
*   **.NET 8 SDK** oder neuer.
*   Die Datei `SCOverlay.API.dll` aus dem neuesten SCOverlay-Release.

1.  Erstelle ein "Klassenbibliothek"-Projekt in Visual Studio für C# (.NET 8).
2.  API-Referenz hinzufügen: Rechtsklick auf `Abhängigkeiten > Assemblyverweis hinzufügen...` und wähle `SCOverlay.API.dll` aus.
3.  **WICHTIG:** Klicke auf die `SCOverlay.API`-Referenz, drücke `F4` für Eigenschaften und setze "Lokal kopieren" auf "Nein" (False). Dies verhindert Konflikte.

### Dein erster Code ("Hello World")

Das ist alles, was du für ein funktionierendes Addon brauchst. Kopiere diesen Code in deine `Class1.cs`-Datei.
```csharp
// Using-Anweisungen sagen deinem Code, welche Toolboxes er verwenden soll.
using SCOverlay.API;
using System.Collections.Generic;
using System.Drawing;
using System.Windows.Forms;
namespace MyFirstAddon
{
// Das [Addon]-Attribut markiert diese Klasse als Einstiegspunkt für SCOverlay.
[Addon]
public class MyFirstAddon : IAddon
{
private IAddonHost? _host; // Eine private Variable, um die "Toolbox" vom Core zu speichern.
code
Code
// --- Basisinformationen ---
    public string Name => "Mein erstes Addon";
    public string Author => "Dein Name";
    public string Version => "1.0.0";

    // Dies ist wie der Konstruktor. Er wird einmal aufgerufen, wenn dein Addon geladen wird.
    public void Initialize(IAddonHost host)
    {
        _host = host; // Speichere die Host-Toolbox zur späteren Verwendung.
        _host.LogInfo($"[{Name}] wurde erfolgreich initialisiert!");
    }

    // Diese Methode fügt Schaltflächen zum Hauptmenü von SCOverlay hinzu.
    public IEnumerable<AddonButton> GetMainMenuButtons()
    {
        // 'yield return' ist eine einfache Möglichkeit, nacheinander Elemente zu einer Liste hinzuzufügen.
        yield return new AddonButton(
            id: "my_addon_hello_button",
            getLabel: () => "Sag Hallo", // Der Text auf der Schaltfläche.
            onClick: () => _host?.Window.ShowNotification("Hallo von meinem Addon!") // Was beim Klick passiert.
        );
    }

    // --- Vorerst lassen wir die anderen erforderlichen Methoden leer ---
    public UserControl? GetSettingsControl(IAddonHost host) => null;
    public IEnumerable<AddonControl> GetSettingsControls() => [];
    public IDictionary<string, (string en, string de)> GetLocalizations() => new Dictionary<string, (string, string)>();
    public void Draw(Graphics g, Rectangle bounds) { }
    public void OnOverlayVisibilityChanged(bool isVisible) { }
    public void Shutdown() { }
}
}
```
### Bereitstellung

Kopiere deine kompilierte `.dll`-Datei in einen Unterordner mit dem gleichen Namen unter `%AppData%\SCOverlay\addons`.

**Struktur:** `%AppData%\SCOverlay\addons\MyFirstAddon\MyFirstAddon.dll`

<div class="note">
<strong>Stecken geblieben? Wir sind für dich da!</strong><br>
Wenn etwas unklar ist, erstelle ein neues Issue auf GitHub mit dem Tag <code>developer-need-help</code>. Es gibt keine dummen Fragen!
</div>

## Kapitel 3: Das IAddon-Interface: Die DNA deines Addons

Dies ist die Blaupause für jedes Addon. Deine Hauptklasse muss alle diese Member implementieren.

| Member                        | Typ                               | Zweck & detaillierte Erklärung                                                                                                 |
| :---------------------------- | :-------------------------------- | :----------------------------------------------------------------------------------------------------------------------------- |
| `Name`, `Author`, `Version`   | `string`                          | **Metadaten:** Identifiziert dein Addon.                                                                                       |
| `Initialize(IAddonHost host)` | `void`                            | **Konstruktor:** Wird einmal beim Laden aufgerufen. Speichere die Host-Instanz hier. Dies ist deine Setup-Phase.                 |
| `GetMainMenuButtons()`        | `IEnumerable<AddonButton>`        | **Hauptmenü-Buttons:** Definiert die Schaltflächen, die dein Addon im Hauptmenü anzeigt.                                      |
| `GetSettingsControl(IAddonHost host)` | `UserControl?`                    | **(Neu & Empfohlen)** Bietet ein vollständiges, benutzerdefiniertes UI-Panel für deine Einstellungen. Gibt dir volle kreative Freiheit. Siehe Kapitel 5. |
| `GetSettingsControls()`       | `IEnumerable<AddonControl>`       | **(Legacy)** Eine einfachere, begrenzte Möglichkeit, grundlegende Steuerelemente zur Einstellungsseite hinzuzufügen. Ein guter Fallback für sehr einfache Bedürfnisse. |
| `Draw(Graphics g, ...)`       | `void`                            | **Zeichen-Engine:** Wird bei jedem Frame, in dem das Overlay neu gezeichnet wird, aufgerufen. Halte diesen Code extrem schnell! |
| `OnOverlayVisibilityChanged(...)` | `void`                            | **Status-Synchronisation:** Reagiert auf das Öffnen/Schließen des Overlays. Nützlich zum Starten/Stoppen von Hintergrundaufgaben. |
| `Shutdown()`                  | `void`                            | **Bereinigung:** Wird vor dem Entladen aufgerufen. Gib hier alle Ressourcen (z. B. Event-Abonnements) frei, um Speicherlecks zu verhindern. |
| `GetLocalizations()`          | `IDictionary<...>`                | **Lokalisierung:** Stelle englische und deutsche Übersetzungen für die UI-Texte deines Addons bereit.                           |
| `OnGlobalHotkey()`            | `void`                            | **(Fortgeschritten)** Ein spezieller Callback, der ausgelöst wird, wenn dein Addon die exklusive Kontrolle über den Haupt-Toggle-Hotkey hat. |

## Kapitel 4: Der IAddonHost: Dein Werkzeugkasten für den Core

Der `IAddonHost` ist deine Brücke zu allen Funktionen von SCOverlay. Stell dir ihn als einen Werkzeugkasten vor, gefüllt mit leistungsstarken Tools, die du nutzen kannst.

### Menü- und UI-Steuerung

*   `void TakeMenuControl(...)`: Übernimmt die exklusive Kontrolle über das Hauptmenü, um eigene Untermenüs zu erstellen.
*   `void ReleaseMenuControl()`: Gibt die Kontrolle an das Hauptmenü zurück.
*   `void InvalidateOverlay()`: Erzwingt ein sofortiges Neudraw. Entscheidend, damit deine UI-Änderungen sichtbar werden.
*   `void HideMenu()`: Schließt das gesamte Overlay-Menü programmatisch.

### Core-Dienste

*   `ISoundService Sound { get; }`
    *   `PlayFile(...)`: Spielt eine Sounddatei asynchron ab, ohne das Overlay einzufrieren.
*   `IWindowService Window { get; }`
    *   `ShowNotification(...)`: Zeigt eine kurze, nicht-blockierende "Toast"-Benachrichtigung an.
    *   `CreateThemedWindow(...)`: Erstellt ein neues, leeres Fenster, das automatisch das aktuelle Overlay-Theme verwendet.
    *   `Show/HideFilterOverlay(...)`: Zeigt oder verbirgt einen bildschirmweiten Farbfilter, z. B. für einen "Nachtmodus".
    *   `Task<Image> TakeScreenshotAsync()`: Erstellt asynchron einen Screenshot des Spielbildschirms.

### Hotkeys & Eingabe

*   `bool RequestExclusiveHotkeyControl(...) / void ReleaseExclusiveHotkeyControl(...):` Übernimmt vorübergehend den Haupt-Overlay-Hotkey. Perfekt für Funktionen wie "Push-to-Talk" oder einen Screenshot-Modus, bei dem sich das Overlay nicht schließen soll.

### Persistenz (Daten speichern)

*   `string GetSetting(...) & void SetSetting(...):` Ein einfacher Schlüssel-Wert-Speicher für dein Addon.
*   **Best Practice:** Verwende immer ein eindeutiges Präfix für deine Schlüssel (z. B. `MyAddon_ApiToken`), um Konflikte zu vermeiden.

### Logging & Lokalisierung

*   `LogInfo(...) & LogError(...):` Schreibt in die zentrale `debug.log`. Dein wichtigstes Werkzeug zur Fehlerbehebung!
*   `string T(...):` Greift auf das zentrale Übersetzungssystem für mehrsprachigen Text zu.

### Theming (UI gestalten)

*   `Color Theme_Background { get; }`, `Font Theme_TextFont { get; }`, etc.: Read-only-Zugriff auf das aktive Theme. Essentiell, um deine benutzerdefinierte `UserControl`-Einstellungs-UI an den Rest des Overlays anzupassen.

### Performance-Management

*   `void RequestHighPerformanceMode(...) & void ReleaseHighPerformanceMode(...):` Informiert den "Performance Watchdog" vorübergehend, bei einer kurzen, CPU-intensiven Aufgabe nicht einzugreifen.

## Kapitel 5: Einstellungen-UIs erstellen: Von einfach bis leistungsstark

Du hast zwei Möglichkeiten, eine Einstellungsseite für dein Addon zu erstellen.

### Methode 1: Das Baukasten-System (Legacy)

Mit `GetSettingsControls()` gibst du dem Core eine Liste einfacher Bausteine (`AddonControl`, `HotkeyControl`). Der Core stapelt sie dann vertikal für dich.

*   **Vorteile:** Sehr einfach für grundlegende Bedürfnisse.
*   **Nachteile:** Extrem begrenzt. Keine Slider, Textfelder oder benutzerdefinierten Layouts.
// Dies gehört in deine IAddon-Klasse
public IEnumerable<AddonControl> GetSettingsControls()
{
// Eine einfache Schaltfläche
yield return new AddonControl("myaddon_reset_button", "Statistiken zurücksetzen", "RebindButton", () => "", () => { /* Logik zum Zurücksetzen */ });
code
Code
// Ein spezielles Steuerelement zum Binden eines Hotkeys
yield return new HotkeyControl("myaddon_hotkey", "Hotkey für Spezialaktion", "MyAddon_Action1", "Shift+F1");
}
code
Code
### Methode 2: Die Fertiggarage (UserControl - Empfohlen)

Mit `GetSettingsControl(IAddonHost host)` baust du deine gesamte Einstellungsseite visuell im Visual Studio Designer und übergibst diese komplette "Fertiggarage" an den Core.

*   **Vorteile:** Volle kreative Freiheit. Nutze Slider, Textfelder, Bilder, Dropdowns und ordne sie beliebig an.
*   **Nachteile:** Erfordert etwas mehr Setup.

So gehst du vor:

#### 1. Erstelle dein UserControl

In Visual Studio, Rechtsklick auf dein Projekt > Hinzufügen > Benutzersteuerelement (Windows Forms). Benenne es `MySettingsPanel.cs`.
Nutze den visuellen Designer, um Steuerelemente wie `Label`, `TextBox`, `TrackBar` (Slider) usw. auf dein Panel zu ziehen.

#### 2. Implementiere den Code

Deine `IAddon`-Klasse gibt nun einfach eine Instanz deines neuen Panels zurück:
// In deiner Haupt-IAddon-Klasse
public UserControl? GetSettingsControl(IAddonHost host)
{
// Erstelle und gib einfach dein benutzerdefiniertes UI-Panel zurück.
// Gib den 'host' an es weiter, damit es die Theme-Farben verwenden kann!
return new MySettingsPanel(host);
}
// Und lasse die alte Methode leer
public IEnumerable<AddonControl> GetSettingsControls() => [];
code
Code
Der Code für deine `MySettingsPanel.cs` sieht dann so aus:
// In deiner MySettingsPanel.cs-Datei
using SCOverlay.API;
using System.Windows.Forms;
public partial class MySettingsPanel : UserControl
{
private readonly IAddonHost _host;
code
Code
public MySettingsPanel(IAddonHost host)
{
    InitializeComponent(); // Dies lädt die Steuerelemente aus dem Designer
    _host = host;
    ApplyTheme(); // Wende das Theme des Cores auf deine benutzerdefinierte UI an
}

private void ApplyTheme()
{
    // Verwende das Theme vom Host, um deine Steuerelemente zu stylen
    this.BackColor = _host.Theme_Background;
    this.infoLabel.ForeColor = _host.Theme_Text;
    this.volumeSlider.TickColor = _host.Theme_Accent;
}
}
code
Code
Dieser Ansatz ermöglicht dir eine professionelle, vollständig angepasste Einstellungs-UI, die dennoch perfekt zum Look & Feel von SCOverlay passt.

## Kapitel 6: Fortgeschrittene Konzepte & Best Practices

### Lizenzierung für Premium-Addons

Möchtest du dein Addon Unterstützern anbieten? Das SCOverlay-System ist dafür ausgelegt. Dies ist ein kollaborativer Prozess. Du kannst keine `LicenseId` selbst erfinden; sie muss vom SCOverlay-Team generiert und in den Core integriert werden.

Der Prozess:

1.  **Entwickle dein Addon:** Konzentriere dich zuerst auf den Bau deines Addons.
2.  **Kontaktiere uns:** Wenn es soweit ist, kontaktiere den Ersteller (BlugDeg) über ein GitHub-Issue (siehe Kapitel 8).
3.  **Integration:** Wir werden mit dir zusammenarbeiten, um eine einzigartige `LicenseId` auf dem Lizenzserver zu erstellen und diese in das nächste SCOverlay-Release zu integrieren.
4.  **Implementierung:** Du erhältst die offizielle ID von uns. Erst dann fügst du das Attribut zu deiner Addon-Klasse hinzu.
// Beispiel: Du hast die ID "MySuperAddon" vom Ersteller erhalten.
[Addon(LicenseId = "MySuperAddon")]
public class MyPremiumAddon : IAddon { /* ... */ }
code
Code
### Dos & Don'ts

*   ✅ **Events abbestellen:** In deiner `Shutdown()`-Methode solltest du immer Events abbestellen (z. B. `host.OnPaintOverlay -= MyDrawMethod;`), um Speicherlecks zu verhindern.
*   ❌ **Niemals `Draw()` blockieren:** Führe keine Datei-I/O, Netzwerkanfragen oder lange Schleifen in der `Draw`-Methode aus. Dies führt zu Rucklern.
*   ❌ **Keinen UI-Thread annehmen:** Wenn du die UI von einer Hintergrundaufgabe aus aktualisierst, verwende `myControl.BeginInvoke(...)`, um Abstürze zu vermeiden.

## Kapitel 7: Fehlerbehebung: Häufige Probleme lösen

**"Mein Addon erscheint nicht im Menü!"**

*   **Falsche Ordnerstruktur:** Der Ordner in `%AppData%\SCOverlay\addons` muss genau den gleichen Namen haben wie deine DLL-Datei (ohne die `.dll`).
*   **"Lokal kopieren" ist True:** Die `SCOverlay.API`-Referenz muss auf "Lokal kopieren" "Nein" (False) gesetzt sein.
*   **Startfehler:** Überprüfe `debug.log` in `%AppData%\SCOverlay\`. Ein Fehler in deiner `Initialize`-Methode verhindert das Laden des Addons.

**"Meine UI-Änderung wird nicht angezeigt!"**

*   **Lösung:** Du musst `_host?.InvalidateOverlay();` aufrufen, nachdem du etwas geändert hast, das visuell aktualisiert werden soll.

**"Mein Addon verschwindet plötzlich!"**

*   **Ursache:** Der Performance Watchdog hat dein Addon wegen zu hoher CPU-Auslastung entladen.
*   **Lösung:** Optimiere deinen Code (insbesondere `Draw()`). Bei kurzen, beabsichtigten, rechenintensiven Aufgaben umschließe sie mit `RequestHighPerformanceMode`.

## Kapitel 8: Werde Teil der Entwicklung!

Dein Beitrag ist wertvoll. Deine Ideen und deine Hilfe sind immer willkommen.

### Wo du Hilfe findest

➡️ **Stelle eine Frage im `developer-need-help`-Channel**
Erstelle ein neues Issue mit diesem Label. Keine Frage ist zu einfach!

### Gestalte die Zukunft der API mit!

➡️ **Schlage eine neue API-Funktion vor**
Wenn du eine Idee für ein neues Tool in der `IAddonHost`-Toolbox hast, lass es uns wissen!

### Schlage ein lizenziertes Addon vor

➡️ **Fordere eine neue Lizenz-ID an**
Erstelle ein Issue, um dein Premium-Addon-Projekt vorzustellen.

Wir sind gespannt, was du erschaffst!
