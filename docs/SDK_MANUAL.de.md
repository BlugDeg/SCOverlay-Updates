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
  <p><strong>Umfassendes Entwicklerhandbuch v2.2</strong></p>
  <br>
</div>

---

## Inhaltsverzeichnis

1.  [**Unsere Vision: Eine Plattform von Entwicklern für Spieler**](#kapitel-1-unsere-vision-eine-plattform-von-entwicklern-für-spieler)
2.  [**Erste Schritte: Dein erstes Addon in 10 Minuten**](#kapitel-2-erste-schritte-dein-erstes-addon-in-10-minuten)
3.  [**Die Kern-Schnittstellen im Detail**](#kapitel-3-die-kern-schnittstellen-im-detail)
4.  [**Der `IAddonHost` als Werkzeugkasten**](#kapitel-4-der-iaddonhost-als-werkzeugkasten)
5.  [**Fortgeschrittene Konzepte & Best Practices**](#kapitel-5-fortgeschrittene-konzepte--best-practices)
6.  [**Troubleshooting & Häufige Fehler**](#kapitel-6-troubleshooting--häufige-fehler)
7.  [**Werde Teil der Entwicklung!**](#kapitel-7-werde-teil-der-entwicklung)

---

## Kapitel 1: Unsere Vision: Eine Plattform von Entwicklern für Spieler

### Die Philosophie hinter der API
Willkommen, Entwickler! SCOverlay ist mehr als nur ein Tool – es ist ein Ökosystem. Unsere Vision ist es, eine stabile, performante und vor allem **erweiterbare** Plattform zu schaffen, auf der kreative Köpfe wie du aufsetzen können.

-   **Modularität:** Der Kern bietet die Bühne, dein Addon ist der Star.
-   **Stabilität & Performance:** Als Game-Overlay ist Leistung alles. Wir schützen das Spielerlebnis, damit du dich auf die Features konzentrieren kannst.
-   **Strikter Vertrag:** Die `SCOverlay.API.dll` ist unser gemeinsames Fundament. Sie garantiert, dass deine Arbeit von Dauer ist.

---

## Kapitel 2: Erste Schritte: Dein erstes Addon in 10 Minuten

### Voraussetzungen & Setup in Visual Studio
-   **Visual Studio 2022** mit der ".NET Desktop Development"-Workload.
-   **.NET 8 SDK** oder neuer.
-   Die **`SCOverlay.API.dll`**.

1.  Erstelle ein **"Klassenbibliothek (Class Library)"** Projekt für C# (.NET 8.0).
2.  **API-Referenz hinzufügen:** Klicke mit rechts auf **Abhängigkeiten > Assemblyverweis hinzufügen...** und wähle die `SCOverlay.API.dll` aus.
3.  **WICHTIG:** Klicke auf den neuen Verweis `SCOverlay.API`, drücke `F4` für die Eigenschaften und setze **"Copy Local" (Lokale Kopie)** auf **"Nein" (False)**.

### Die "Hallo Welt"-Implementierung
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
Kopiere deine kompilierte `.dll`-Datei in einen gleichnamigen Unterordner in `%AppData%\SCOverlay\addons`.
**Struktur:** `%AppData%\SCOverlay\addons\MyFirstAddon\MyFirstAddon.dll`

<div class="note">
<strong>Steckst du fest? Wir sind für dich da!</strong><br>
Wenn bei diesen ersten Schritten etwas unklar ist, zögere nicht! Erstelle ein neues Issue auf GitHub mit dem Tag <code>developer-need-help</code>. Wir helfen dir gerne beim Einstieg.
</div>

---

## Kapitel 3: Die Kern-Schnittstellen im Detail

### Analyse der `IAddon`-Schnittstelle
Dies ist der Bauplan für jedes Addon. Ihre Hauptklasse muss diese Schnittstelle vollständig implementieren.

| Member                                | Typ                                            | Zweck & Detaillierte Erklärung                                                                                                   |
| ------------------------------------- | ---------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------- |
| `Name, Author, Version`               | `string`                                       | **Metadaten:** Werden zur Identifizierung und Anzeige in zukünftigen UI-Elementen verwendet.                                     |
| `Initialize(IAddonHost host)`         | `void`                                         | **Der Konstruktor Ihres Addons.** Wird beim Laden aufgerufen. Speichern Sie hier die `host`-Instanz für die spätere Verwendung. |
| `GetMainMenuButtons()`                | `IEnumerable<AddonButton>`                     | **Sichtbarkeit im Hauptmenü.** Definiert, welche Buttons Ihr Addon im Hauptmenü anzeigen möchte.                                  |
| `GetSettingsControls()`               | `IEnumerable<AddonControl>`                    | **Integration in die Einstellungen.** Platziert UI-Elemente auf der zentralen Einstellungsseite des Overlays.                |
| `Draw(Graphics g, ...)`               | `void`                                         | **Die Zeichen-Engine.** Wird bei jedem Neuzeichnen des Overlays aufgerufen. Halten Sie diesen Code extrem performant!          |
| `OnOverlayVisibilityChanged(...)`     | `void`                                         | **Zustands-Synchronisation.** Reagiert auf das Öffnen/Schließen des Overlays.                                                  |
| `Shutdown()`                          | `void`                                         | **Aufräumarbeiten.** Wird aufgerufen, bevor das Addon entladen wird. Geben Sie hier alle Ressourcen frei.                    |
| `GetLocalizations()`                  | `IDictionary<string, (string en, string de)>`  | **Internationalisierung.** Stellt eigene Übersetzungen für das Mehrsprachigkeits-System bereit.                                |

### Analyse der `IAddonHost`-Schnittstelle
Dein Tor zum SCOverlay-Kern. Sie ist als Fassade konzipiert, um Komplexität zu verbergen und eine stabile API zu gewährleisten, die auch bei internen Umbauten im Kern gleich bleibt. Im nächsten Kapitel zerlegen wir jede einzelne Funktion.

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
                    _host?.TakeMenuControl(this, GoBack);
                });
            } else {
                yield return new AddonButton("action1", () => "Aktion 1", () => { /* ... */ });
            }
        }
        
        private void GoBack() {
            _isInSubMenu = false;
            _host?.ReleaseMenuControl();
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
    *   **Zweck:** Schreibt standardisierte Einträge in die `debug.log`-Datei. Dein bester Freund bei der Fehlersuche!
-   **`string T(string localizationKey)`**
    *   **Zweck:** Greift auf das zentrale Übersetzungssystem zu.

### Theming
-   **`Color Theme_Background { get; }`, `Font Theme_TextFont { get; }`, etc.**
    *   **Zweck:** Gibt dir Lesezugriff auf die Farben und Schriftarten des aktiven Themes für ein konsistentes Erscheinungsbild.

### Performance Management
-   **`void RequestHighPerformanceMode(IAddon addon, string reason)` & `void ReleaseHighPerformanceMode(IAddon addon)`**
    *   **Zweck:** Kommuniziert mit dem "Performance Watchdog".
    *   **Best Practice:** IMMER in einem `try...finally`-Block verwenden, um sicherzustellen, dass die Ausnahme wieder freigegeben wird!

<div class="note">
<strong>Fehlt dir eine Schnittstelle?</strong><br>
Du hast eine Idee für eine neue Funktion, die der Host bereitstellen sollte? Fantastisch! Wir wollen, dass die API mit den Bedürfnissen der Community wächst. Erstelle ein Issue auf GitHub, tagge es mit <code>api-suggestion</code> und beschreibe, welche Schnittstelle du dir wünschst und was du damit bauen möchtest. Lass uns die API gemeinsam besser machen!
</div>

---

## Kapitel 5: Fortgeschrittene Konzepte & Best Practices

### Lebenszyklus eines Addons
1.  **Laden:** Der `AddonManager` findet deine DLL.
2.  **Instanziierung:** Eine Instanz deiner `IAddon`-Klasse wird erstellt.
3.  **Initialisierung:** `Initialize(host)` wird aufgerufen. Ab jetzt ist dein Addon "lebendig".
4.  **Betrieb:** Der Kern ruft Methoden wie `GetMainMenuButtons()` oder `Draw()` bei Bedarf auf.
5.  **Shutdown:** Wenn das Addon entladen wird, wird `Shutdown()` aufgerufen.

### Event-basierte Programmierung: `OnPaintOverlay`
Als Alternative zu `Draw()` kannst du Events abonnieren.
```csharp
public void Initialize(IAddonHost host) {
    _host = host;
    _host.OnPaintOverlay += MyCustomDrawMethod;
}

private void MyCustomDrawMethod(Graphics g, Rectangle bounds) {
    g.DrawString("Gezeichnet via Event!", new Font("Arial", 12), Brushes.Cyan, bounds.Location);
}

public void Shutdown() {
    if (_host != null) {
        _host.OnPaintOverlay -= MyCustomDrawMethod; // WICHTIG: Immer deabonnieren!
    }
}
```

### Erstellen eigener Fenster
Nutze `CreateThemedWindow`, um komplexe UIs zu bauen.
```csharp
private Form? _myConfigWindow;

private void OpenConfig() {
    if (_myConfigWindow != null && !_myConfigWindow.IsDisposed) {
        _myConfigWindow.Activate();
        return;
    }
    _myConfigWindow = _host.Window.CreateThemedWindow("Meine Konfiguration");
    
    var myButton = new Button { Text = "Klick mich", Dock = DockStyle.Top };
    myButton.Click += (s, e) => { /* ... */ };
    
    _myConfigWindow.Controls.Add(myButton);
    _myConfigWindow.Show();
}

public void Shutdown() {
    _myConfigWindow?.Dispose(); // WICHTIG: Aufräumen!
}
```

### Lizenzierung für Premium-Addons
Füge einfach das `Addon`-Attribut mit einer `LicenseId` zu deiner Klasse hinzu. Der Kern kümmert sich um den Rest.
```csharp
[Addon(LicenseId = "MeinSuperAddon")]
public class MyPremiumAddon : IAddon { /* ... */ }```

---

## Kapitel 6: Troubleshooting & Häufige Fehler

Hier sind die häufigsten Stolpersteine und wie du sie schnell aus dem Weg räumst.

### Problem: "Mein Addon wird nicht im Menü angezeigt!"
1.  **Die Ordner/Dateistruktur ist falsch.**
    *   **Lösung:** Der Ordner in `%AppData%\SCOverlay\addons` muss **exakt** denselben Namen haben wie deine DLL.
2.  **"Copy Local" ist auf "True" gesetzt.**
    *   **Lösung:** Setze in Visual Studio die Eigenschaft **"Copy Local"** für die `SCOverlay.API`-Referenz auf **"Nein" (False)**.
3.  **Dein Addon verursacht einen Fehler beim Start.**
    *   **Lösung:** Schaue in die `debug.log` (`%AppData%\SCOverlay\debug.log`). Wenn in deiner `Initialize`-Methode ein Fehler auftritt, wird das Laden abgebrochen.

### Problem: "Mein Button-Text (oder eine andere UI-Änderung) wird nicht aktualisiert!"
*   **Ursache:** Du hast dem Overlay nicht mitgeteilt, dass es sich neu zeichnen soll.
*   **Lösung:** Rufe **immer** `_host?.InvalidateOverlay();` auf, nachdem du einen Zustand geändert hast, der die Anzeige beeinflusst.

### Problem: "Ich bekomme eine 'Cross-thread operation not valid'-Exception."
*   **Ursache:** Du versuchst, ein UI-Element von einem anderen Thread aus zu ändern.
*   **Lösung:** Nutze `BeginInvoke`, um den Code sicher auf dem UI-Thread auszuführen.
    ```csharp
    myLabel.BeginInvoke((Action)(() => { myLabel.Text = "Neuer Text"; }));
    ```

### Problem: "Mein Addon verschwindet plötzlich während der Nutzung!"
*   **Ursache:** Der **Performance Watchdog** hat zugeschlagen, weil dein Addon zu viel CPU-Last verursacht hat.
*   **Lösung:** Wenn die Last kurz und gewollt ist, nutze `RequestHighPerformanceMode`. Wenn sie ungewollt ist, optimiere deinen Code (besonders die `Draw`-Methode!).

---

## Kapitel 7: Werde Teil der Entwicklung!

**Dein Beitrag ist wertvoll.** Ob du ein erfahrener Entwickler bist oder gerade erst anfängst, deine Ideen und deine Hilfe sind willkommen.

### Wo du Hilfe findest
Wir wissen, dass der Einstieg manchmal holprig sein kann. Zögere niemals, uns um Hilfe zu bitten!

➡️ **[Frage im `developer-need-help`-Channel stellen](https://github.com/DEIN-USERNAME/DEIN-REPO/issues/new?labels=developer-need-help)**
Erstelle einfach ein neues Issue mit dem Label **`developer-need-help`**. Einer aus dem Team oder der Community wird sich so schnell wie möglich bei dir melden.

### Gestalte die Zukunft der API mit!
Diese API ist ein lebendiges Werkzeug. Wenn du während der Entwicklung denkst: "Mensch, wenn der Host doch nur DIESE Funktion hätte...", dann bist du genau die Person, die wir suchen!

➡️ **[Eine neue API-Funktion vorschlagen](https://github.com/DEIN-USERNAME/DEIN-REPO/issues/new?labels=api-suggestion)**
Teile deine Gedanken mit uns, indem du ein Issue mit dem Label **`api-suggestion`** erstellst. Lass uns gemeinsam darüber diskutieren.

**Wir freuen uns darauf, zu sehen, was du erschaffst!**