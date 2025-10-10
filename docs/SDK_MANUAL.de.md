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
-   **`void ReleaseMenuControl()`**
    *   **Zweck:** Gibt die Kontrolle an das Hauptmenü zurück.
-   **`void InvalidateOverlay()`**
    *   **Zweck:** Zwingt das Overlay zu einem sofortigen Neuzeichnen. Essenziell, um UI-Änderungen sichtbar zu machen.

### Zugriff auf Kern-Dienste
-   **`ISoundService Sound { get; }`**
    *   **`PlayFile(string path, float volume = 1.0f)`**: Spielt eine Sound-Datei asynchron in einem Hintergrundthread ab.
-   **`IWindowService Window { get; }`**
    *   **`ShowNotification(string message)`**: Zeigt eine kurze "Toast"-Benachrichtigung an.
    *   **`CreateThemedWindow(string title)`**: Erstellt eine leere `Form`, die automatisch das aktuelle Overlay-Theme erbt.

### Persistenz
-   **`string GetSetting(string key, string defaultValue)` & `void SetSetting(string key, string value)`**
    *   **Zweck:** Ein einfaches Schlüssel-Wert-Speichersystem, das in der zentralen `settings.json`-Datei gespeichert wird.
    *   **Best Practice:** Verwende immer ein eindeutiges Präfix für deine Schlüssel (z.B. `MyAddon_ApiToken`).

### Logging & Lokalisierung
-   **`LogInfo(string message)` & `LogError(string message, Exception? ex = null)`**
    *   **Zweck:** Schreibt standardisierte Einträge in die `debug.log`-Datei (`%AppData%\SCOverlay\debug.log`). Dein wichtigstes Werkzeug bei der Fehlersuche!
-   **`string T(string localizationKey)`**
    *   **Zweck:** Greift auf das zentrale Übersetzungssystem zu.

### Theming
-   **`Color Theme_Background { get; }`, `Font Theme_TextFont { get; }`, etc.**
    *   **Zweck:** Gibt dir Lesezugriff auf die Farben und Schriftarten des aktiven Themes für ein konsistentes Erscheinungsbild.

### Performance Management
-   **`void RequestHighPerformanceMode(...)` & `void ReleaseHighPerformanceMode(...)`**
    *   **Zweck:** Kommuniziert mit dem "Performance Watchdog", um eine temporäre Ausnahme für rechenintensive Aufgaben zu erhalten.
    *   **Best Practice:** IMMER in einem `try...finally`-Block verwenden!

<div class="note">
<strong>Fehlt dir eine Schnittstelle?</strong><br>
Du hast eine Idee für eine neue Funktion, die der Host bereitstellen sollte? Fantastisch! Wir wollen, dass die API mit den Bedürfnissen der Community wächst. Erstelle ein Issue auf GitHub, tagge es mit <code>api-suggestion</code> und beschreibe, welche Schnittstelle du dir wünschst und was du damit bauen möchtest. Lass uns die API gemeinsam besser machen!
</div>

---

## Kapitel 5: Fortgeschrittene Konzepte & Best Practices

### Lizenzierung für Premium-Addons: Ein geführter Prozess
Du möchtest ein Addon entwickeln, das exklusiv für Unterstützer verfügbar ist? Das SCOverlay-System ist genau dafür ausgelegt. Dies ist ein **kollaborativer Prozess**.

**Der Prozess sieht wie folgt aus:**
1.  **Entwickle dein Addon:** Konzentriere dich zuerst auf die Entwicklung.
2.  **Kontaktiere uns:** Wenn dein Addon fertig ist, kontaktiere den **Creator (BlugDeg)**, um dein Projekt vorzustellen. Der beste Weg dafür ist, ein neues Issue auf GitHub zu erstellen (siehe Kapitel 7).
3.  **Abstimmung & Erstellung:** Wir arbeiten mit dir zusammen. Anschließend wird der Creator eine neue, einzigartige **`LicenseId`** für dein Addon auf dem Lizenz-Server erstellen und in die Kernanwendung integrieren.
4.  **Integration in dein Addon:** Du erhältst die offizielle ID von uns. Erst jetzt fügst du das Attribut zu deiner Addon-Klasse hinzu.
    ```csharp
    [Addon(LicenseId = "VomCreatorErhalteneID")]
    public class MyPremiumAddon : IAddon { /* ... */ }
    ```

### Dos & Don'ts: Häufige Fehler vermeiden
-   ✅ **Ressourcen freigeben:** Implementiere `IDisposable` für eigene Fenster und rufe `Dispose()` in deiner `Shutdown()`-Methode auf.
-   ✅ **Events deabonnieren:** Deabonniere Events wie `_host.OnPaintOverlay` in `Shutdown()`, um Speicherlecks zu verhindern.
-   ❌ **Blockiere niemals `Draw()`:** Keine Dateioperationen, Netzwerkzugriffe oder lange Schleifen in der `Draw`-Methode.
-   ❌ **Gehe nicht von einem UI-Thread aus:** Nutze `meinFenster.BeginInvoke(...)`, um UI-Elemente sicher aus anderen Threads zu aktualisieren.

---

## Kapitel 6: Troubleshooting & Häufige Fehler

Hier sind die häufigsten Stolpersteine und wie du sie schnell aus dem Weg räumst.

### Problem: "Mein Addon wird nicht im Menü angezeigt!"
1.  **Die Ordner/Dateistruktur ist falsch.**
    *   **Lösung:** Der Ordner in `%AppData%\SCOverlay\addons` muss **exakt** denselben Namen haben wie deine DLL.
2.  **"Copy Local" ist auf "True" gesetzt.**
    *   **Lösung:** Setze in Visual Studio die Eigenschaft **"Copy Local"** für die `SCOverlay.API`-Referenz auf **"Nein" (False)**.
3.  **Dein Addon verursacht einen Fehler beim Start.**
    *   **Lösung:** Schaue in die `debug.log` (`%AppData%\SCOverlay\debug.log`). Ein Fehler in `Initialize` bricht das Laden ab.

### Problem: "Mein Button-Text wird nicht aktualisiert!"
*   **Ursache:** Du hast dem Overlay nicht mitgeteilt, dass es sich neu zeichnen soll.
*   **Lösung:** Rufe **immer** `_host?.InvalidateOverlay();` auf, nachdem du einen Zustand geändert hast, der die Anzeige beeinflusst.

### Problem: "Ich bekomme eine 'Cross-thread operation not valid'-Exception."
*   **Ursache:** Du versuchst, ein UI-Element von einem anderen Thread aus zu ändern.
*   **Lösung:** Nutze `BeginInvoke`, um den Code sicher auf dem UI-Thread auszuführen.
    ```csharp
    myLabel.BeginInvoke((Action)(() => { myLabel.Text = "Neuer Text"; }));
    ```

### Problem: "Mein Addon verschwindet plötzlich!"
*   **Ursache:** Der **Performance Watchdog** hat zugeschlagen, weil dein Addon zu viel CPU-Last verursacht hat.
*   **Lösung:** Wenn die Last kurz und gewollt ist, nutze `RequestHighPerformanceMode`. Wenn sie ungewollt ist, optimiere deinen Code (besonders die `Draw`-Methode!).

<div class="note">
<strong>Pro-Tipp: Dein persönlicher Code-Assistent</strong><br>
Du kannst das gesamte Handbuch oder Teile davon kopieren und in eine moderne KI wie Gemini oder ChatGPT einfügen. Beschreibe dein Problem oder was du bauen möchtest, und die KI kann dir basierend auf den Informationen in diesem Handbuch präzise Code-Beispiele und Lösungen für dein spezifisches Problem generieren. Nutze sie als deinen persönlichen Assistenten!
</div>

---

## Kapitel 7: Werde Teil der Entwicklung!

**Dein Beitrag ist wertvoll.** Ob du ein erfahrener Entwickler bist oder gerade erst anfängst, deine Ideen und deine Hilfe sind willkommen.

### Wo du Hilfe findest
Wir wissen, dass der Einstieg manchmal holprig sein kann. Zögere niemals, uns um Hilfe zu bitten!

➡️ **[Frage im `developer-need-help`-Channel stellen](https://github.com/BlugDeg/SCOverlay-Updates/issues/new?labels=developer-need-help)**
Erstelle einfach ein neues Issue mit dem Label **`developer-need-help`**. Einer aus dem Team oder der Community wird sich so schnell wie möglich bei dir melden.

### Gestalte die Zukunft der API mit!
Diese API ist ein lebendiges Werkzeug. Wenn du während der Entwicklung denkst: "Mensch, wenn der Host doch nur DIESE Funktion hätte...", dann bist du genau die Person, die wir suchen!

➡️ **[Eine neue API-Funktion vorschlagen](https://github.com/BlugDeg/SCOverlay-Updates/issues/new?labels=api-suggestion)**
Teile deine Gedanken mit uns, indem du ein Issue mit dem Label **`api-suggestion`** erstellst.

### Ein lizenziertes Addon vorschlagen
Du hast ein Premium-Addon entwickelt und möchtest eine offizielle `LicenseId` anfragen? Fantastisch!

➡️ **[Eine neue Lizenz-ID anfragen](https://github.com/BlugDeg/SCOverlay-Updates/issues/new?labels=licensing-request)**
Erstelle ein Issue mit dem Label **`licensing-request`** und stelle uns dein Projekt vor. Wir werden uns dann bei dir melden, um die nächsten Schritte zu besprechen.

**Wir freuen uns darauf, zu sehen, was du erschaffst!**
