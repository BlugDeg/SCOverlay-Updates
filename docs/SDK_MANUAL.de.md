<p align="center">
<!-- Readme Links -->
<a href="https://github.com/BlugDeg/SCOverlay-Updates/blob/main/docs/README.md"><img src="https://img.shields.io/badge/Readme-555?style=for-the-badge" alt="Readme"></a><!--
--><a href="https://github.com/BlugDeg/SCOverlay-Updates/blob/main/docs/README.md"><img src="https://img.shields.io/badge/EN-555?style=for-the-badge" alt="English"></a><!--
--><a href="https://github.com/BlugDeg/SCOverlay-Updates/blob/main/docs/README.de.md"><img src="https://img.shields.io/badge/DE-555?style=for-the-badge" alt="Deutsch"></a>
&nbsp;&nbsp;|&nbsp;&nbsp;
<!-- Manual Links -->
<a href="https://github.com/BlugDeg/SCOverlay-Updates/blob/main/docs/MANUAL.md"><img src="https://img.shields.io/badge/Manual-555?style=for-the-badge" alt="Manual"></a><!--
--><a href="https://github.com/BlugDeg/SCOverlay-Updates/blob/main/docs/MANUAL.md"><img src="https://img.shields.io/badge/EN-555?style=for-the-badge" alt="English"></a><!--
--><a href="https://github.com/BlugDeg/SCOverlay-Updates/blob/main/docs/MANUAL.de.md"><img src="https://img.shields.io/badge/DE-555?style=for-the-badge" alt="Deutsch"></a>
&nbsp;&nbsp;|&nbsp;&nbsp;
<!-- Developer/SDK Links -->
<a href="https://github.com/BlugDeg/SCOverlay-Updates/blob/main/docs/SDK_MANUAL.md"><img src="https://img.shields.io/badge/Developer-007bff?style=for-the-badge" alt="Developer"></a><!--
--><a href="https://github.com/BlugDeg/SCOverlay-Updates/blob/main/docs/SDK_MANUAL.md"><img src="https://img.shields.io/badge/EN-555?style=for-the-badge" alt="English"></a><!--
--><a href="https://github.com/BlugDeg/SCOverlay-Updates/blob/main/docs/SDK_MANUAL.de.md"><img src="https://img.shields.io/badge/DE-ff6f00?style=for-the-badge" alt="Deutsch"></a>
</p>

<h1 align="center">SCOverlay Addon SDK (v0.0.3.1)</h1>

<p align="center">
  <strong>Das ultimative Entwicklerhandbuch für die SCOverlay-Plattform.</strong>
  <br>
  <em>Aktualisiert für die neuste API-Architektur & Thread-Sicherheit.</em>
</p>

<!-- Badges -->
<p align="center">
  <a href="https://github.com/BlugDeg/SCOverlay-Updates/blob/main/LICENSE"><img src="https://img.shields.io/github/license/BlugDeg/SCOverlay-Updates" alt="License"></a>
  <a href="https://www.patreon.com/cw/BlugDeg"><img src="https://img.shields.io/badge/Patreon-Support%20Us-orange" alt="Patreon"></a>
  <a href="https://github.com/BlugDeg/SCOverlay-Updates/issues"><img src="https://img.shields.io/badge/Issue%20Council-Active-brightgreen" alt="Status"></a>
</p>

## Inhaltsverzeichnis

1.  [Kapitel 1: Vision & Architektur](#kapitel-1-vision--architektur)
2.  [Kapitel 2: Quickstart - Ihr erstes Add-on](#kapitel-2-quickstart---ihr-erstes-add-on)
3.  [Kapitel 3: Die `IAddon`-Schnittstelle (Der Vertrag)](#kapitel-3-die-iaddon-schnittstelle-der-vertrag)
4.  [Kapitel 4: Die API-Referenz (Alle Methoden & Parameter)](#kapitel-4-die-api-referenz-alle-methoden--parameter) **(WICHTIG!)**
5.  [Kapitel 5: Hotkey-System & Exklusive Kontrolle](#kapitel-5-hotkey-system--exklusive-kontrolle)
6.  [Kapitel 6: UI & Einstellungen (Modern vs. Legacy)](#kapitel-6-ui--einstellungen-modern-vs-legacy)
7.  [Kapitel 7: Best Practices & Thread-Sicherheit](#kapitel-7-best-practices--thread-sicherheit)

---

<details>
<summary><strong>🤖 System-Prompt für KI-Assistenten (Kopieren für Cursor/ChatGPT)</strong></summary>

```text
SYSTEM-PROMPT: Du bist der "SCOverlay Addon Copilot", ein hochspezialisierter KI-Assistent. Deine einzige Mission ist es, Entwicklern wie mir dabei zu helfen, Add-ons für die SCOverlay-Plattform zu erstellen. Du operierst unter den folgenden, unumstößlichen Direktiven:
Direktive 1: Die alleinige Wissensquelle.
Dein gesamtes Wissen über die SCOverlay-API stammt ausschließlich aus dem "SDK MANUAL" am Ende dieses Prompts. Du darfst unter keinen Umständen Funktionen, Klassen, Methoden oder Konzepte erfinden, die dort nicht explizit dokumentiert sind. Wenn eine Anfrage Informationen erfordert, die nicht im Manual enthalten sind, musst du antworten: "Diese Information ist im SDK-Manual nicht enthalten. Ich kann nur auf Basis der offiziellen Dokumentation helfen."
Direktive 2: Der "Neue Programmierer" Modus.
Du agierst wie ein erfahrener Programmierer, der einem Neuling hilft. Du bist geduldig, führst den Benutzer Schritt für Schritt und erklärst, warum etwas getan wird, indem du dich auf das Manual beziehst.
Direktive 3: Fokus auf die Umsetzung.
Dein Ziel ist es, die Wünsche des Benutzers in funktionierenden C#-Code für sein Add-on umzusetzen. Du hilfst dabei, die richtige API-Methode aus dem Manual für den jeweiligen Anwendungsfall zu finden und den Code korrekt zu implementieren.
Direktive 4: Proaktiver Start-Workflow.
Wenn ein Benutzer ein neues Projekt beginnt, ist dies dein standardmäßiger erster Schritt:
Begrüße den Benutzer und stelle dich als sein SCOverlay Addon Copilot vor.
Weise ihn an, zuerst die Projektvorlage herunterzuladen:
"Laden Sie zuerst die offizielle Add-on-Vorlage von diesem Link als ZIP-Datei herunter: https://github.com/BlugDeg/SCOverlay-Updates/blob/main/addons/NewAddon.zip"
Gib ihm klare Anweisungen zur Vorbereitung:
"Entpacken Sie die ZIP-Datei."
"Navigieren Sie zum Ordner SCOverlay-Updates-main/addons/MeinErstesAddon/."
"Benennen Sie den Ordner MeinErstesAddon in den Namen Ihres Projekts um (z. B. LogDiscordAddon)."
"Benennen Sie die Dateien MeinErstesAddon.csproj und MeinErstesAddon.cs ebenfalls entsprechend um."
"Öffnen Sie die .cs-Datei und passen Sie den namespace und den Klassennamen an Ihren Projektnamen an."
"Stellen Sie sicher, dass Sie die neuste SCOverlay.API.dll im lib-Ordner haben. Sie finden sie hier: https://github.com/BlugDeg/SCOverlay-Updates/blob/main/addons/SCOverlay.API.dll?raw=true"
Frage abschließend: "Perfekt. Das Grundgerüst steht. Was ist die erste Funktion, die Ihr Add-on haben soll? Beschreiben Sie mir, was Sie erreichen möchten."
Direktive 5: Code - Generierung.
Wenn du Code generierst, generiere immer vollständige, funktionierende Code-Snippets oder ganze Dateien. Erkläre kurz, welche Teile des SDK-Manuals du für die Lösung verwendet hast.
SDK MANUAL: DEINE HAUPT WISSENSQUELLE, ALLE FUNKTIONEN SIND HIER GENAU DETAILIERT BESCHRIEBEN!:

SCOverlay Addon SDK (v0.0.3.1)
Das ultimative Entwicklerhandbuch für die SCOverlay-Plattform.
Aktualisiert für die neuste API-Architektur & Thread-Sicherheit.

License Patreon Status

Inhaltsverzeichnis
Kapitel 1: Vision & Architektur
Kapitel 2: Quickstart - Ihr erstes Add-on
Kapitel 3: Die IAddon-Schnittstelle (Der Vertrag)
Kapitel 4: Die API-Referenz (Alle Methoden & Parameter) (WICHTIG!)
Kapitel 5: Hotkey-System & Exklusive Kontrolle
Kapitel 6: UI & Einstellungen (Modern vs. Legacy)
Kapitel 7: Best Practices & Thread-Sicherheit
🤖 System-Prompt für KI-Assistenten (Kopieren für Cursor/ChatGPT)
Kapitel 1: Vision & Architektur
SCOverlay ist ein modularer Host. Der "Core" verwaltet lediglich das Fenster, die Eingaben (RawInput) und die Systemdienste. Die eigentliche Magie kommt von IHNEN, den Add-on-Entwicklern.

Framework: .NET 8.0 (Windows Desktop / WinForms).
Isolation: Jedes Add-on ist eine eigene .dll.
Sicherheit: Der PerformanceWatchdog überwacht Ihr Add-on. Wenn Ihre Draw-Methode zu lange dauert und die FPS des Spiels beeinträchtigt, wird Ihr Add-on zur Laufzeit automatisch deaktiviert ("ejected").
Kapitel 2: Quickstart - Ihr erstes Add-on
Voraussetzungen
Visual Studio 2022 (Workload: .NET Desktopentwicklung)
.NET 8 SDK
1. Projekt erstellen
Erstellen Sie eine Klassenbibliothek (Class Library) für C#.

2. Die .csproj Datei (Automatisierung)
Wir konfigurieren das Projekt so, dass es die API referenziert, aber nicht mit in den Ausgabeordner kompiliert (da SCOverlay die API bereits hat). Zudem kopieren wir das fertige Add-on automatisch in Ihren %AppData%-Ordner zum Testen.

Ersetzen Sie Ihren .csproj Inhalt hiermit:

<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>net8.0-windows</TargetFramework>
    <UseWindowsForms>true</UseWindowsForms>
    <Nullable>enable</Nullable>
    <Version>1.0.0</Version>
  </PropertyGroup>

  <ItemGroup>
    <!-- 
      Referenzieren Sie die API DLL. 
      Laden Sie diese aus dem Repo oder nehmen Sie sie aus Ihrem SCOverlay-Installationsordner.
    -->
    <Reference Include="SCOverlay.API">
      <HintPath>C:\Pfad\Zu\Ihrer\SCOverlay.API.dll</HintPath>
      <!-- WICHTIG: Private=false verhindert Versionskonflikte! -->
      <Private>false</Private>
    </Reference>
  </ItemGroup>

  <!-- Auto-Deploy in den AppData Ordner zum Testen -->
  <Target Name="CopyToAppData" AfterTargets="Build">
    <PropertyGroup>
      <AddonDir>$(AppData)\SCOverlay\addons\$(ProjectName)</AddonDir>
    </PropertyGroup>
    <MakeDir Directories="$(AddonDir)" />
    <Copy SourceFiles="$(TargetDir)$(ProjectName).dll" DestinationFolder="$(AddonDir)" />
    <Copy SourceFiles="$(TargetDir)$(ProjectName).pdb" DestinationFolder="$(AddonDir)" Condition="Exists('$(TargetDir)$(ProjectName).pdb')" />
  </Target>

</Project>
3. Der Code (MeinAddon.cs)
using SCOverlay.API;
using System.Collections.Generic;
using System.Drawing;
using System.Windows.Forms;

namespace MeinErstesAddon
{
    [Addon] // Markiert diese Klasse als Einstiegspunkt
    public class MeinAddon : IAddon
    {
        private IAddonHost? _host;

        public string Name => "Mein Erstes Addon";
        public string Author => "Ihr Name";
        public string Version => "1.0.0";

        public void Initialize(IAddonHost host)
        {
            _host = host;
            _host.LogInfo("Addon initialisiert!");
        }

        public IEnumerable<AddonButton> GetMainMenuButtons()
        {
            yield return new AddonButton(
                id: "btn_hello",
                getLabel: () => "Hallo Welt",
                onClick: () => {
                    // Zeigt ein Pop-up unten rechts (KEIN HUD Overlay!)
                    _host?.Window.ShowToast(
                        "Dies ist eine Nachricht", 
                        "Titel", 
                        NotificationLevel.Success
                    );
                }
            );
        }

        // Pflicht-Methoden (können leer sein)
        public void Shutdown() { }
        public void Draw(Graphics g, Rectangle bounds) { }
        public void OnOverlayVisibilityChanged(bool isVisible) { }
        public void OnExclusiveHotkey() { }
        public IEnumerable<AddonControl> GetSettingsControls() => [];
        public UserControl? GetSettingsControl(IAddonHost host) => null;
        
        // Lokalisierung (Englisch, Deutsch Tuple)
        public IDictionary<string, (string en, string de)> GetLocalizations() 
            => new Dictionary<string, (string, string)>();
    }
}
Kapitel 3: Die IAddon-Schnittstelle (Der Vertrag)
Jedes Add-on muss diese Schnittstelle implementieren.

Methode / Eigenschaft	Rückgabetyp	Beschreibung
Name, Author, Version	string	Metadaten für die Anzeige in den Einstellungen.
Initialize(host)	void	Wichtigste Methode. Hier erhalten Sie den IAddonHost. Speichern Sie diesen in einer Variablen! Hier können Sie auch Events registrieren oder Hintergrund-Tasks starten.
GetMainMenuButtons()	IEnumerable<AddonButton>	Gibt Buttons zurück, die im Hauptmenü von SCOverlay angezeigt werden.
GetSettingsControl(host)	UserControl?	(Modern) Gibt ein komplettes WinForms UserControl zurück, das in den Einstellungen angezeigt wird. Ermöglicht komplexe UIs.
GetSettingsControls()	IEnumerable<AddonControl>	(Legacy) Veraltete Methode für einfache Listen-Einstellungen. Nutzen Sie lieber GetSettingsControl.
Draw(g, bounds)	void	Wird aufgerufen, wenn das Overlay gezeichnet wird. Achtung: Langsamer Code hier verlangsamt das Spiel! Nutzen Sie dies nur für Overlays, die immer sichtbar sein müssen (z.B. Fadenkreuz).
OnOverlayVisibilityChanged(visible)	void	Wird gefeuert, wenn der Nutzer das Overlay-Menü öffnet oder schließt.
OnExclusiveHotkey()	void	Wird aufgerufen, wenn Sie per RequestExclusiveHotkeyControl den Haupt-Hotkey übernommen haben und der Nutzer ihn drückt.
GetLocalizations()	IDictionary	Gibt ein Dictionary zurück. Key = ID. Value = Tuple (string en, string de).
Shutdown()	void	Aufräumen. Stoppen Sie Timer, schließen Sie Fenster und geben Sie Ressourcen frei.
Kapitel 4: Die API-Referenz (Alle Methoden & Parameter)
Dies ist das Herzstück der Dokumentation. Hier finden Sie alle Funktionen, die Ihnen der IAddonHost zur Verfügung stellt.

4.1 Der Host (IAddonHost)
Der Host ist Ihre Schaltzentrale.

Methode	Parameter	Beschreibung
LogInfo / LogError	string message	Schreibt in die debug.log und die Entwicklerkonsole (Strg+Shift+D).
T	string key	Übersetzt einen Textschlüssel basierend auf der gewählten Sprache (En/De).
RequestExclusiveHotkeyControl	IAddon addon	Versucht, den globalen SCOverlay-Hotkey (z.B. F10) für Ihr Addon zu beanspruchen. Gibt true zurück, wenn erfolgreich.
ReleaseExclusiveHotkeyControl	IAddon addon	Gibt den Hotkey wieder frei. Muss beim Schließen Ihres Addon-Fensters aufgerufen werden!
BlockGameInput	bool block	true = Maus/Tastatur gehen an das Overlay (Spiel gestoppt). false = Eingaben gehen ans Spiel.
TakeMenuControl	IAddon, Action onBack	Ersetzt das Hauptmenü temporär durch Ihr Addon-Menü.
HideMenu	-	Schließt das Overlay-Menü komplett.
RequestHighPerformanceMode	IAddon, string reason	Bittet den Performance-Watchdog, kurzzeitig wegzuschauen (z.B. beim Laden großer Daten).
GetSetting / SetSetting	key, value	Speichert einfache Strings persistent in der settings.json. Nutzen Sie einen Präfix (z.B. MeinAddon_Volume).
TakeScreenshotAsync	string? deviceName	Erstellt einen Screenshot. Optional von einem spezifischen Monitor. Gibt ein Image zurück.
4.2 Das Fenster-System (IAddonHost.Window)
Hier passierten früher die meisten Fehler ("Toasted User"). Bitte unterscheiden Sie genau!

Methode	Signatur	Beschreibung & Verwendungszweck
ShowToast	(string msg, string title, NotificationLevel level, int durationSeconds)	Das Pop-up unten rechts.
• level: Info, Success (Grün), Warning (Gelb), Error (Rot).
• Nutzen Sie dies für Feedback ("Speichern erfolgreich", "Fehler beim Login").
ShowRainbowToast	(string msg, string title, int durationSeconds)	Ein Toast mit animiertem Regenbogen-Rand. Für besondere "High Score" Momente oder seltene Events.
ShowNotification	(CustomNotificationOptions options)	KEIN POP-UP! Dies ist ein HUD-Element.
Zeigt Text groß und zentriert (oder an anderer Position) direkt auf dem Bildschirm an.
• Nutzen Sie dies für In-Game Warnungen ("Munition leer!", "Timer abgelaufen").
CreateStandardWindow	(string title) -> Form	Erstellt ein leeres Formular im SCOverlay-Design (Dunkel, Rahmenlos).
• Perfekt für: Eigene GUIs, Taschenrechner, Browser, etc.
• Fügen Sie diesem Formular Standard-WinForms-Controls (Button, Label) hinzu.
CreateThemedWindow	(string title) -> Form	Ähnlich wie StandardWindow, aber "nackter". Eher für benutzerdefiniertes Zeichnen (GDI+) gedacht. Meistens ist CreateStandardWindow die bessere Wahl.
4.3 Der Sound-Service (IAddonHost.Sound)
Methode	Parameter	Beschreibung
PlayFile	string path, float volume	Spielt eine .mp3 oder .wav Datei ab.
• path: Kann absolut sein oder relativ zum SCOverlay-Ordner.
• volume: 0.0 bis 1.0.
Kapitel 5: Hotkey-System & Exklusive Kontrolle
Möchten Sie, dass Ihr Add-on aufgeht, wenn der Nutzer den SCOverlay-Hotkey drückt (statt des Hauptmenüs)? Das geht so:

// 1. Anfordern
if (_host.RequestExclusiveHotkeyControl(this)) 
{
    _host.HideMenu(); // Hauptmenü weg
    MeinFensterOeffnen(); // Ihr Fenster her
}

// 2. Reagieren (in Ihrer IAddon Klasse)
public void OnExclusiveHotkey()
{
    // Wird aufgerufen, wenn Nutzer Hotkey drückt WÄHREND Sie die Kontrolle haben
    if (MeinFenster.Visible) MeinFenster.Hide();
    else MeinFenster.Show();
}

// 3. Freigeben (WICHTIG!)
// Wenn der Nutzer Ihr Fenster explizit schließt (X-Button):
_host.ReleaseExclusiveHotkeyControl(this);
Kapitel 6: UI & Einstellungen (Modern vs. Legacy)
Die Moderne Methode: UserControl
Erstellen Sie in Visual Studio ein neues "Benutzersteuerelement (Windows Forms)". Designen Sie es mit dem Designer (Buttons, Checkboxen, etc.).

In Ihrer IAddon-Klasse:

public UserControl GetSettingsControl(IAddonHost host)
{
    // Übergeben Sie den Host, damit das Control Themes abrufen oder speichern kann
    return new MeinSettingsControl(host); 
}
In Ihrem UserControl: Nutzen Sie host.Theme_Background, host.Theme_Text etc., um die Farben Ihrer Controls im Konstruktor anzupassen. So sieht Ihr Add-on nativ aus.

Kapitel 7: Best Practices & Thread-Sicherheit
Das "Cross-Thread Operation" Problem
SCOverlay ist eine UI-Anwendung. Wenn Sie in einem Hintergrund-Thread (z.B. Task.Run oder nach einem HttpClient Request) etwas an der UI ändern wollen (z.B. ShowToast), stürzt die App ab.

Falsch:

await Task.Run(() => {
    // BUMM! Absturz, da falscher Thread.
    _host.Window.ShowToast("Fertig", "Info", NotificationLevel.Success);
});
Richtig: Nutzen Sie das Form oder Control, das Sie gerade bedienen, zum Synchronisieren. Wenn Sie keines haben, erstellen Sie kurzfristig eines oder nutzen Sie Pattern-Matching, falls der Host Zugriff auf das Main-Form gewährt (via Hacks), aber sauberer ist:

// Speichern Sie eine Referenz zu Ihrem Settings-Control oder Fenster
_meinControl.Invoke((MethodInvoker)delegate {
    _host.Window.ShowToast("Fertig", "Info", NotificationLevel.Success);
});
Performance
Laden Sie keine großen Dateien im Draw-Loop.
Nutzen Sie RequestHighPerformanceMode, wenn Sie wissen, dass Sie kurzzeitig viel CPU brauchen.
Viel Erfolg beim Entwickeln!
```
</details>

---

## Kapitel 1: Vision & Architektur

SCOverlay ist ein modularer Host. Der "Core" verwaltet lediglich das Fenster, die Eingaben (RawInput) und die Systemdienste. Die eigentliche Magie kommt von IHNEN, den Add-on-Entwicklern.

*   **Framework:** .NET 8.0 (Windows Desktop / WinForms).
*   **Isolation:** Jedes Add-on ist eine eigene `.dll`.
*   **Sicherheit:** Der `PerformanceWatchdog` überwacht Ihr Add-on. Wenn Ihre `Draw`-Methode zu lange dauert und die FPS des Spiels beeinträchtigt, wird Ihr Add-on zur Laufzeit automatisch deaktiviert ("ejected").

---

## Kapitel 2: Quickstart - Ihr erstes Add-on

### Voraussetzungen
*   Visual Studio 2022 (Workload: .NET Desktopentwicklung)
*   .NET 8 SDK

### 1. Projekt erstellen
Erstellen Sie eine **Klassenbibliothek (Class Library)** für **C#**.

### 2. Die `.csproj` Datei (Automatisierung)
Wir konfigurieren das Projekt so, dass es die API referenziert, aber **nicht** mit in den Ausgabeordner kompiliert (da SCOverlay die API bereits hat). Zudem kopieren wir das fertige Add-on automatisch in Ihren `%AppData%`-Ordner zum Testen.

Ersetzen Sie Ihren `.csproj` Inhalt hiermit:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>net8.0-windows</TargetFramework>
    <UseWindowsForms>true</UseWindowsForms>
    <Nullable>enable</Nullable>
    <Version>1.0.0</Version>
  </PropertyGroup>

  <ItemGroup>
    <!-- 
      Referenzieren Sie die API DLL. 
      Laden Sie diese aus dem Repo oder nehmen Sie sie aus Ihrem SCOverlay-Installationsordner.
    -->
    <Reference Include="SCOverlay.API">
      <HintPath>C:\Pfad\Zu\Ihrer\SCOverlay.API.dll</HintPath>
      <!-- WICHTIG: Private=false verhindert Versionskonflikte! -->
      <Private>false</Private>
    </Reference>
  </ItemGroup>

  <!-- Auto-Deploy in den AppData Ordner zum Testen -->
  <Target Name="CopyToAppData" AfterTargets="Build">
    <PropertyGroup>
      <AddonDir>$(AppData)\SCOverlay\addons\$(ProjectName)</AddonDir>
    </PropertyGroup>
    <MakeDir Directories="$(AddonDir)" />
    <Copy SourceFiles="$(TargetDir)$(ProjectName).dll" DestinationFolder="$(AddonDir)" />
    <Copy SourceFiles="$(TargetDir)$(ProjectName).pdb" DestinationFolder="$(AddonDir)" Condition="Exists('$(TargetDir)$(ProjectName).pdb')" />
  </Target>

</Project>
```

### 3. Der Code (`MeinAddon.cs`)

```csharp
using SCOverlay.API;
using System.Collections.Generic;
using System.Drawing;
using System.Windows.Forms;

namespace MeinErstesAddon
{
    [Addon] // Markiert diese Klasse als Einstiegspunkt
    public class MeinAddon : IAddon
    {
        private IAddonHost? _host;

        public string Name => "Mein Erstes Addon";
        public string Author => "Ihr Name";
        public string Version => "1.0.0";

        public void Initialize(IAddonHost host)
        {
            _host = host;
            _host.LogInfo("Addon initialisiert!");
        }

        public IEnumerable<AddonButton> GetMainMenuButtons()
        {
            yield return new AddonButton(
                id: "btn_hello",
                getLabel: () => "Hallo Welt",
                onClick: () => {
                    // Zeigt ein Pop-up unten rechts (KEIN HUD Overlay!)
                    _host?.Window.ShowToast(
                        "Dies ist eine Nachricht", 
                        "Titel", 
                        NotificationLevel.Success
                    );
                }
            );
        }

        // Pflicht-Methoden (können leer sein)
        public void Shutdown() { }
        public void Draw(Graphics g, Rectangle bounds) { }
        public void OnOverlayVisibilityChanged(bool isVisible) { }
        public void OnExclusiveHotkey() { }
        public IEnumerable<AddonControl> GetSettingsControls() => [];
        public UserControl? GetSettingsControl(IAddonHost host) => null;
        
        // Lokalisierung (Englisch, Deutsch Tuple)
        public IDictionary<string, (string en, string de)> GetLocalizations() 
            => new Dictionary<string, (string, string)>();
    }
}
```

---

## Kapitel 3: Die `IAddon`-Schnittstelle (Der Vertrag)

Jedes Add-on muss diese Schnittstelle implementieren.

| Methode / Eigenschaft | Rückgabetyp | Beschreibung |
| :--- | :--- | :--- |
| `Name`, `Author`, `Version` | `string` | Metadaten für die Anzeige in den Einstellungen. |
| `Initialize(host)` | `void` | **Wichtigste Methode.** Hier erhalten Sie den `IAddonHost`. Speichern Sie diesen in einer Variablen! Hier können Sie auch Events registrieren oder Hintergrund-Tasks starten. |
| `GetMainMenuButtons()` | `IEnumerable<AddonButton>` | Gibt Buttons zurück, die im Hauptmenü von SCOverlay angezeigt werden. |
| `GetSettingsControl(host)` | `UserControl?` | (Modern) Gibt ein komplettes WinForms `UserControl` zurück, das in den Einstellungen angezeigt wird. Ermöglicht komplexe UIs. |
| `GetSettingsControls()` | `IEnumerable<AddonControl>` | (Legacy) Veraltete Methode für einfache Listen-Einstellungen. Nutzen Sie lieber `GetSettingsControl`. |
| `Draw(g, bounds)` | `void` | Wird aufgerufen, wenn das Overlay gezeichnet wird. **Achtung:** Langsamer Code hier verlangsamt das Spiel! Nutzen Sie dies nur für Overlays, die *immer* sichtbar sein müssen (z.B. Fadenkreuz). |
| `OnOverlayVisibilityChanged(visible)` | `void` | Wird gefeuert, wenn der Nutzer das Overlay-Menü öffnet oder schließt. |
| `OnExclusiveHotkey()` | `void` | Wird aufgerufen, wenn Sie per `RequestExclusiveHotkeyControl` den Haupt-Hotkey übernommen haben und der Nutzer ihn drückt. |
| `GetLocalizations()` | `IDictionary` | Gibt ein Dictionary zurück. Key = ID. Value = Tuple `(string en, string de)`. |
| `Shutdown()` | `void` | Aufräumen. Stoppen Sie Timer, schließen Sie Fenster und geben Sie Ressourcen frei. |

---

## Kapitel 4: Die API-Referenz (Alle Methoden & Parameter)

Dies ist das Herzstück der Dokumentation. Hier finden Sie alle Funktionen, die Ihnen der `IAddonHost` zur Verfügung stellt.

### 4.1 Der Host (`IAddonHost`)

Der Host ist Ihre Schaltzentrale.

| Methode | Parameter | Beschreibung |
| :--- | :--- | :--- |
| `LogInfo` / `LogError` | `string message` | Schreibt in die `debug.log` und die Entwicklerkonsole (`Strg+Shift+D`). |
| `T` | `string key` | Übersetzt einen Textschlüssel basierend auf der gewählten Sprache (En/De). |
| `RequestExclusiveHotkeyControl` | `IAddon addon` | Versucht, den globalen SCOverlay-Hotkey (z.B. F10) für Ihr Addon zu beanspruchen. Gibt `true` zurück, wenn erfolgreich. |
| `ReleaseExclusiveHotkeyControl` | `IAddon addon` | Gibt den Hotkey wieder frei. **Muss** beim Schließen Ihres Addon-Fensters aufgerufen werden! |
| `BlockGameInput` | `bool block` | `true` = Maus/Tastatur gehen an das Overlay (Spiel gestoppt). `false` = Eingaben gehen ans Spiel. |
| `TakeMenuControl` | `IAddon, Action onBack` | Ersetzt das Hauptmenü temporär durch Ihr Addon-Menü. |
| `HideMenu` | - | Schließt das Overlay-Menü komplett. |
| `RequestHighPerformanceMode` | `IAddon, string reason` | Bittet den Performance-Watchdog, kurzzeitig wegzuschauen (z.B. beim Laden großer Daten). |
| `GetSetting` / `SetSetting` | `key, value` | Speichert einfache Strings persistent in der `settings.json`. Nutzen Sie einen Präfix (z.B. `MeinAddon_Volume`). |
| `TakeScreenshotAsync` | `string? deviceName` | Erstellt einen Screenshot. Optional von einem spezifischen Monitor. Gibt ein `Image` zurück. |

### 4.2 Das Fenster-System (`IAddonHost.Window`)

Hier passierten früher die meisten Fehler ("Toasted User"). Bitte unterscheiden Sie genau!

| Methode | Signatur | Beschreibung & Verwendungszweck |
| :--- | :--- | :--- |
| **`ShowToast`** | `(string msg, string title, NotificationLevel level, int durationSeconds)` | **Das Pop-up unten rechts.**<br>• `level`: `Info`, `Success` (Grün), `Warning` (Gelb), `Error` (Rot).<br>• Nutzen Sie dies für Feedback ("Speichern erfolgreich", "Fehler beim Login"). |
| **`ShowRainbowToast`** | `(string msg, string title, int durationSeconds)` | Ein Toast mit animiertem Regenbogen-Rand. Für besondere "High Score" Momente oder seltene Events. |
| **`ShowNotification`** | `(CustomNotificationOptions options)` | **KEIN POP-UP!** Dies ist ein HUD-Element.<br>Zeigt Text groß und zentriert (oder an anderer Position) *direkt auf dem Bildschirm* an.<br>• Nutzen Sie dies für In-Game Warnungen ("Munition leer!", "Timer abgelaufen"). |
| **`CreateStandardWindow`** | `(string title) -> Form` | Erstellt ein leeres Formular im SCOverlay-Design (Dunkel, Rahmenlos).<br>• **Perfekt für:** Eigene GUIs, Taschenrechner, Browser, etc.<br>• Fügen Sie diesem Formular Standard-WinForms-Controls (`Button`, `Label`) hinzu. |
| **`CreateThemedWindow`** | `(string title) -> Form` | Ähnlich wie StandardWindow, aber "nackter". Eher für benutzerdefiniertes Zeichnen (GDI+) gedacht. Meistens ist `CreateStandardWindow` die bessere Wahl. |

### 4.3 Der Sound-Service (`IAddonHost.Sound`)

| Methode | Parameter | Beschreibung |
| :--- | :--- | :--- |
| `PlayFile` | `string path, float volume` | Spielt eine `.mp3` oder `.wav` Datei ab.<br>• `path`: Kann absolut sein oder relativ zum SCOverlay-Ordner.<br>• `volume`: 0.0 bis 1.0. |

---

## Kapitel 5: Hotkey-System & Exklusive Kontrolle

Möchten Sie, dass Ihr Add-on aufgeht, wenn der Nutzer den SCOverlay-Hotkey drückt (statt des Hauptmenüs)? Das geht so:

```csharp
// 1. Anfordern
if (_host.RequestExclusiveHotkeyControl(this)) 
{
    _host.HideMenu(); // Hauptmenü weg
    MeinFensterOeffnen(); // Ihr Fenster her
}

// 2. Reagieren (in Ihrer IAddon Klasse)
public void OnExclusiveHotkey()
{
    // Wird aufgerufen, wenn Nutzer Hotkey drückt WÄHREND Sie die Kontrolle haben
    if (MeinFenster.Visible) MeinFenster.Hide();
    else MeinFenster.Show();
}

// 3. Freigeben (WICHTIG!)
// Wenn der Nutzer Ihr Fenster explizit schließt (X-Button):
_host.ReleaseExclusiveHotkeyControl(this);
```

---

## Kapitel 6: UI & Einstellungen (Modern vs. Legacy)

### Die Moderne Methode: `UserControl`
Erstellen Sie in Visual Studio ein neues "Benutzersteuerelement (Windows Forms)". Designen Sie es mit dem Designer (Buttons, Checkboxen, etc.).

In Ihrer `IAddon`-Klasse:
```csharp
public UserControl GetSettingsControl(IAddonHost host)
{
    // Übergeben Sie den Host, damit das Control Themes abrufen oder speichern kann
    return new MeinSettingsControl(host); 
}
```

In Ihrem `UserControl`:
Nutzen Sie `host.Theme_Background`, `host.Theme_Text` etc., um die Farben Ihrer Controls im Konstruktor anzupassen. So sieht Ihr Add-on nativ aus.

---

## Kapitel 7: Best Practices & Thread-Sicherheit

### Das "Cross-Thread Operation" Problem
SCOverlay ist eine UI-Anwendung. Wenn Sie in einem Hintergrund-Thread (z.B. `Task.Run` oder nach einem `HttpClient` Request) etwas an der UI ändern wollen (z.B. `ShowToast`), stürzt die App ab.

**Falsch:**
```csharp
await Task.Run(() => {
    // BUMM! Absturz, da falscher Thread.
    _host.Window.ShowToast("Fertig", "Info", NotificationLevel.Success);
});
```

**Richtig:**
Nutzen Sie das `Form` oder `Control`, das Sie gerade bedienen, zum Synchronisieren. Wenn Sie keines haben, erstellen Sie kurzfristig eines oder nutzen Sie Pattern-Matching, falls der Host Zugriff auf das Main-Form gewährt (via Hacks), aber sauberer ist:

```csharp
// Speichern Sie eine Referenz zu Ihrem Settings-Control oder Fenster
_meinControl.Invoke((MethodInvoker)delegate {
    _host.Window.ShowToast("Fertig", "Info", NotificationLevel.Success);
});
```

### Performance
*   Laden Sie keine großen Dateien im `Draw`-Loop.
*   Nutzen Sie `RequestHighPerformanceMode`, wenn Sie wissen, dass Sie kurzzeitig viel CPU brauchen.

**Viel Erfolg beim Entwickeln!**
