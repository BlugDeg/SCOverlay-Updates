<p align="center">
  <a href="../README.de.md"><img src="https://img.shields.io/badge/Readme-555?style=flat-square" alt="Readme"></a><!--
  --><a href="../README.md"><img src="https://img.shields.io/badge/EN-555?style=flat-square" alt="English"></a><!--
  --><a href="../README.de.md"><img src="https://img.shields.io/badge/DE-007bff?style=flat-square" alt="Deutsch"></a>
  &nbsp;&nbsp;|&nbsp;&nbsp;
  <a href="SDK_MANUAL.md"><img src="https://img.shields.io/badge/Developer-555?style=flat-square" alt="Developer"></a><!--
  --><a href="SDK_MANUAL.md"><img src="https://img.shields.io/badge/EN-555?style=flat-square" alt="English"></a><!--
  --><a href="SDK_MANUAL.de.md"><img src="https://img.shields.io/badge/DE-ff6f00?style=flat-square" alt="Deutsch"></a>
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
  <p><strong>Umfassendes Entwicklerhandbuch v2.0</strong></p>
  <br>
</div>

---

## Inhaltsverzeichnis

1.  [**Philosophie & Architektur**](#kapitel-1-philosophie--architektur)
    *   Die Vision hinter der API
    *   Der strikte Vertrag: `SCOverlay.API.dll`

2.  [**Erste Schritte: Dein erstes Addon**](#kapitel-2-erste-schritte-dein-erstes-addon)
    *   Voraussetzungen & Setup
    *   Schritt-für-Schritt: Projekt in Visual Studio erstellen
    *   Die "Hallo Welt"-Implementierung
    *   Deployment: Wie SCOverlay dein Addon findet

3.  [**Die Kern-Schnittstellen im Detail**](#kapitel-3-die-kern-schnittstellen-im-detail)
    *   Analyse der `IAddon`-Schnittstelle
    *   Analyse der `IAddonHost`-Schnittstelle

4.  [**Der `IAddonHost` als Werkzeugkasten**](#kapitel-4-der-iaddonhost-als-werkzeugkasten)
    *   Menü- und UI-Steuerung
    *   Zugriff auf Kern-Dienste (Sound & Fenster)
    *   Persistenz (Einstellungen speichern & laden)
    *   Logging & Lokalisierung
    *   Theming
    *   Performance Management

5.  [**Fortgeschrittene Konzepte & Best Practices**](#kapitel-5-fortgeschrittene-konzepte--best-practices)
    *   Lebenszyklus eines Addons
    *   Event-basierte Programmierung
    *   Erstellen eigener Fenster
    *   Lizenzierung für Premium-Addons
    *   Dos & Don'ts: Häufige Fehler vermeiden

---

## Kapitel 1: Philosophie & Architektur

### Die Vision hinter der API
Die Architektur von SCOverlay wurde nach drei Kernprinzipien entworfen:

-   **Modularität:** Der Kern bietet eine stabile Plattform, während die gesamte Funktionalität durch austauschbare Addons bereitgestellt wird. Ihr Addon ist ein Bürger erster Klasse im Ökosystem.
-   **Stabilität & Performance:** Als Game-Overlay ist die Performance nicht verhandelbar. Die API ist so gestaltet, dass sie Addons daran hindert, die Hauptanwendung oder das Spielerlebnis negativ zu beeinflussen.
-   **Strikter Vertrag:** Die `SCOverlay.API.dll` ist ein unveränderlicher Vertrag. Der Kern und die Addons kommunizieren *ausschließlich* über die darin definierten Schnittstellen.

---

## Kapitel 2: Erste Schritte: Dein erstes Addon

### Voraussetzungen & Setup
-   **Visual Studio 2022** mit der ".NET Desktop Development"-Workload.
-   **.NET 8 SDK** oder neuer.
-   Die **`SCOverlay.API.dll`**.

### Schritt-für-Schritt: Projekt in Visual Studio erstellen
1.  Öffne Visual Studio und wähle **"Create a new project"**.
2.  Suche nach und wähle die Vorlage **"Klassenbibliothek (Class Library)"** für C#.
3.  **Projektnamen festlegen:** Nenne dein Projekt z.B. `MyFirstAddon`. Der Assemblyname wird standardmäßig derselbe sein. Das ist wichtig!
4.  **Framework auswählen:** Wähle **.NET 8.0**.
5.  **API-Referenz hinzufügen:**
    *   Klicke im Projektmappen-Explorer mit der rechten Maustaste auf **Abhängigkeiten > Assemblyverweis hinzufügen...**.
    *   Klicke auf **"Durchsuchen..."** und wähle die `SCOverlay.API.dll` aus.
6.  **Referenz-Eigenschaften anpassen:**
    *   Klicke auf den neuen Verweis `SCOverlay.API` unter `Abhängigkeiten > Assemblys`.
    *   Gehe ins Eigenschaftenfenster (Taste `F4`).
    *   Setze die Eigenschaft **"Copy Local" (Lokale Kopie)** auf **"Nein" (False)**. Dies ist entscheidend, damit deine Addon-DLL nicht versucht, eine eigene Kopie der API mitzuliefern.
    
### Die "Hallo Welt"-Implementierung
Erstelle eine neue Klasse und implementiere die `IAddon`-Schnittstelle.

```csharp
using SCOverlay.API;
using System.Collections.Generic;
using System.Drawing;

namespace MyFirstAddon
{
    [Addon]
    public class MyFirstAddon : IAddon
    {
        private IAddonHost? _host;
        public string Name => "Mein Erstes Addon";
        public string Author => "Ihr Name";
        public string Version => "1.0.0";

        public void Initialize(IAddonHost host)
        {
            _host = host;
            _host.LogInfo($"[{Name}] wurde erfolgreich initialisiert!");
        }

        public IEnumerable<AddonButton> GetMainMenuButtons()
        {
            yield return new AddonButton(
                id: "my_addon_hello_button",
                getLabel: () => "Sag Hallo",
                onClick: () => _host?.Window.ShowNotification("Hallo Welt von meinem Addon!")
            );
        }

        // Leere Implementierungen für den Rest
        public IEnumerable<AddonControl> GetSettingsControls() => [];
        public IDictionary<string, (string en, string de)> GetLocalizations() => new Dictionary<string, (string, string)>();
        public void Draw(Graphics g, Rectangle bounds) { }
        public void OnOverlayVisibilityChanged(bool isVisible) { }
        public void Shutdown() { }
    }
}
```

### Deployment: Wie SCOverlay dein Addon findet
1.  Kompiliere dein Projekt (Build -> Build Solution).
2.  Navigiere zum Ausgabeordner (z.B. `bin/Release/net8.0-windows`).
3.  Öffne den SCOverlay Addon-Ordner: `%AppData%\SCOverlay\addons`.
4.  Erstelle darin einen neuen Ordner, der **exakt denselben Namen** hat wie deine kompilierte DLL-Datei ohne die Endung (also `MyFirstAddon`).
5.  Kopiere die `MyFirstAddon.dll` in diesen neuen Ordner.

**Korrekte Struktur:**
`%AppData%\SCOverlay\addons\MyFirstAddon\MyFirstAddon.dll`

---

## Kapitel 3: Die Kern-Schnittstellen im Detail

### Analyse der `IAddon`-Schnittstelle
Dies ist der Bauplan für jedes Addon.
*   `Name, Author, Version`: Essenzielle Metadaten.
*   `Initialize(IAddonHost host)`: Der "Konstruktor" deines Addons.
*   `GetMainMenuButtons()`: Definiert die Präsenz deines Addons im Hauptmenü.
*   `GetSettingsControls()`: Bietet eine einfache Möglichkeit, Einstellungen in der Haupt-UI zu verankern.
*   `Draw(...)`: Der Hook in die Render-Schleife des Overlays für grafische Darstellungen.
*   `OnOverlayVisibilityChanged(...)`: Reagiert auf das Öffnen/Schließen des Overlays.
*   `Shutdown()`: Die "Destruktor"-Methode für sauberes Aufräumen.
*   `GetLocalizations()`: Integriert dein Addon in das Mehrsprachigkeits-System.

### Analyse der `IAddonHost`-Schnittstelle
Dein Tor zum SCOverlay-Kern. Sie ist als Fassade konzipiert, um Komplexität zu verbergen und eine stabile API zu gewährleisten.

---

## Kapitel 4: Der `IAddonHost` als Werkzeugkasten

Hier ist eine detaillierte Aufschlüsselung aller Methoden, die dir über die `IAddonHost`-Instanz zur Verfügung stehen.

### Menü- und UI-Steuerung
-   **`void TakeMenuControl(IAddon addon, Action? onBack)`**
    *   **Zweck:** Übernimmt die exklusive Kontrolle über das Hauptmenü, um eigene Untermenüs zu erstellen.
    *   **Analyse:** Ein mächtiger Befehl an die `OverlayForm`. Er signalisiert: "Verstecke alle anderen Buttons und zeige nur noch die, die ich jetzt über `GetMainMenuButtons()` liefere." Der `onBack`-Callback wird an den "Zurück"-Button gebunden.
    *   **Best Practice:**
        ```csharp
        private bool _isInSubMenu = false;
        
        public IEnumerable<AddonButton> GetMainMenuButtons()
        {
            if (!_isInSubMenu) {
                yield return new AddonButton("root", () => "Mein Menü", () => {
                    _isInSubMenu = true;
                    _host?.TakeMenuControl(this, () => {
                        _isInSubMenu = false;
                        _host?.ReleaseMenuControl();
                    });
                });
            } else {
                yield return new AddonButton("action1", () => "Aktion 1", () => { /* ... */ });
            }
        }
        ```

-   **`void InvalidateOverlay()`**
    *   **Zweck:** Zwingt das Overlay zu einem sofortigen Neuzeichnen.
    *   **Analyse:** Ruft intern die `UpdateThemedWindow()`-Methode der Hauptform auf. Dies ist unerlässlich, wenn sich ein visueller Zustand ändert, der von einer `Func<string>` in deinen Buttons abhängt.
    *   **Best Practice:**
        ```csharp
        private bool _isToggled = false;

        private void OnToggle() {
            _isToggled = !_isToggled;
            _host?.Window.ShowNotification($"Status ist jetzt: {_isToggled}");
            _host?.InvalidateOverlay(); // Wichtig, damit der Button-Text aktualisiert wird!
        }
        ```
        
### Zugriff auf Kern-Dienste
-   **`ISoundService Sound { get; }`**
    *   **`PlayFile(string path, float volume = 1.0f)`**: Spielt eine Sound-Datei asynchron in einem Hintergrundthread ab, um die UI niemals zu blockieren.
-   **`IWindowService Window { get; }`**
    *   **`ShowNotification(string message)`**: Zeigt eine kurze, nicht-blockierende "Toast"-Benachrichtigung an.
    *   **`CreateThemedWindow(string title)`**: Erstellt eine leere `Form`, die automatisch das aktuelle Overlay-Theme erbt. Ideal für komplexe, eigene UI-Fenster.

### Persistenz
-   **`string GetSetting(string key, string defaultValue)` & `void SetSetting(string key, string value)`**
    *   **Zweck:** Ein einfaches Schlüssel-Wert-Speichersystem für dein Addon.
    *   **Analyse:** Die Daten werden in der zentralen `settings.json`-Datei von SCOverlay gespeichert. Dies ist für einfache Konfigurationen gedacht. Für komplexe Daten (wie Datenbanken) solltest du einen eigenen Speicherort im `%AppData%\SCOverlay\AddonData`-Ordner verwenden.
    *   **Best Practice:** Verwende immer ein eindeutiges Präfix für deine Schlüssel, um Konflikte mit anderen Addons zu vermeiden (z.B. `MyAddon_ApiToken`).

### Logging & Lokalisierung
-   **`LogInfo(string message)` & `LogError(string message, Exception? ex = null)`**
    *   **Zweck:** Schreibt standardisierte Einträge in die `debug.log`-Datei.
-   **`string T(string localizationKey)`**
    *   **Zweck:** Greift auf das zentrale Übersetzungssystem zu. Du kannst sowohl Kern-Schlüssel (z.B. `generic.back`) als auch eigene, über `GetLocalizations()` bereitgestellte Schlüssel verwenden.

### Theming
-   **`Color Theme_Background { get; }`, `Font Theme_TextFont { get; }`, etc.**
    *   **Zweck:** Gibt dir Lesezugriff auf die Farben und Schriftarten des aktiven Themes.
    *   **Best Practice:** Verwende diese Eigenschaften immer, wenn du eigene Fenster (`CreateThemedWindow`) oder Zeichenoperationen (`Draw`) erstellst, um ein konsistentes Erscheinungsbild zu gewährleisten.

### Performance Management
-   **`void RequestHighPerformanceMode(IAddon addon, string reason)` & `void ReleaseHighPerformanceMode(IAddon addon)`**
    *   **Zweck:** Kommuniziert mit dem "Performance Watchdog".
    *   **Analyse:** Wenn du eine kurzzeitig rechenintensive Operation durchführen musst (z.B. eine große Datei parsen), rufe `Request...` auf. Der Watchdog wird dein Addon für diesen Zeitraum ignorieren. `Release...` signalisiert das Ende.
    *   **Best Practice:** IMMER in einem `try...finally`-Block verwenden!
        ```csharp
        _host?.RequestHighPerformanceMode(this, "Lade große Daten");
        try
        {
            // ... Aufwendige Operation ...
        }
        finally
        {
            _host?.ReleaseHighPerformanceMode(this);
        }
        ```

---

## Kapitel 5: Fortgeschrittene Konzepte & Best Practices

### Lebenszyklus eines Addons
1.  **Laden:** Der `AddonManager` findet deine DLL.
2.  **Instanziierung:** Eine Instanz deiner `IAddon`-Klasse wird erstellt.
3.  **Initialisierung:** `Initialize(host)` wird aufgerufen. Ab jetzt ist dein Addon "lebendig".
4.  **Betrieb:** Der Kern ruft Methoden wie `GetMainMenuButtons()` oder `Draw()` bei Bedarf auf.
5.  **Shutdown:** Wenn das Addon entladen wird (Anwendung schließt, Watchdog greift ein), wird `Shutdown()` aufgerufen.

### Dos & Don'ts: Häufige Fehler vermeiden
-   ✅ **Ressourcen freigeben:** Implementiere `IDisposable` für eigene Fenster und rufe `Dispose()` in deiner `Shutdown()`-Methode auf.
-   ✅ **Events deabonnieren:** Wenn du dich für ein Event wie `_host.OnPaintOverlay` registrierst, deabonniere es in `Shutdown()`, um Speicherlecks zu verhindern.
-   ❌ **Blockiere niemals `Draw()`:** Führe in der `Draw`-Methode keine Dateioperationen, Netzwerkzugriffe oder lange Schleifen aus. Dies friert das gesamte Overlay ein.
-   ❌ **Gehe nicht von einem UI-Thread aus:** Wenn du UI-Elemente aktualisieren musst, die in einem anderen Thread erstellt wurden (z.B. dein eigenes Fenster), verwende `meinFenster.BeginInvoke(...)`, um den Aufruf sicher an den UI-Thread zu übergeben.