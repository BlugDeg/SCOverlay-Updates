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
<p align="center">
  <svg width="150" height="150" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
    <path d="M12 21C16.9706 21 21 16.9706 21 12C21 7.02944 16.9706 3 12 3C7.02944 3 3 7.02944 3 12C3 16.9706 7.02944 21 12 21Z" stroke="#4a90e2" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" opacity="0.4"/>
    <path d="M12 17V12" stroke="#4a90e2" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
    <path d="M12 3C12 3 15 6 15 9C15 12 12 17 12 17" stroke="#4a90e2" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
    <path d="M12 3C12 3 9 6 9 9C9 12 12 17 12 17" stroke="#4a90e2" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
  </svg>
</p>

<h1 align="center">SCOverlay Addon SDK</h1>

<p align="center">
  <strong>Das ultimative Entwicklerhandbuch für die SCOverlay-Plattform.</strong>
  <br>
  Erstelle deine eigenen Addons, integriere sie mit dem Kern und werde Teil des Ökosystems.
</p>

<!-- Badges -->
<p align="center">
  <a href="https://github.com/BlugDeg/SCOverlay-Updates/blob/main/LICENSE"><img src="https://img.shields.io/github/license/BlugDeg/SCOverlay-Updates" alt="License"></a>
  <a href="https://www.patreon.com/cw/BlugDeg"><img src="https://img.shields.io/badge/Patreon-Support%20Us-orange" alt="Patreon"></a>
  <a href="https://github.com/BlugDeg/SCOverlay-Updates/issues"><img src="https://img.shields.io/badge/Issue%20Council-Active-brightgreen" alt="Status"></a>
</p>

## Inhaltsverzeichnis
*   [Kapitel 1: Unsere Vision: Eine Plattform für Entwickler](#kapitel-1-unsere-vision-eine-plattform-für-entwickler)
*   [Kapitel 2: Der absolute Start: Von Null zum ersten Add-on in 10 Minuten](#kapitel-2-der-absolute-start-von-null-zum-ersten-add-on-in-10-minuten)
    *   [Schritt 0: Die Werkzeuge (Voraussetzungen)](#schritt-0-die-werkzeuge-voraussetzungen)
    *   [Schritt 1: Das Projekt-Fundament in Visual Studio](#schritt-1-das-projekt-fundament-in-visual-studio)
    *   [Schritt 2: Die Projektdatei (`.csproj`) – Die Automatisierungs-Magie](#schritt-2-die-projektdatei-csproj--die-automatisierungs-magie)
    *   [Schritt 3: Der erste Code ("Hallo Welt")](#schritt-3-der-erste-code-hallo-welt)
    *   [Schritt 4: Kompilieren und Testen](#schritt-4-kompilieren-und-testen)
*   [Kapitel 3: Die `IAddon`-Schnittstelle: Die DNA Ihres Add-ons](#kapitel-3-die-iaddon-schnittstelle-die-dna-ihres-add-ons)
*   [Kapitel 4: Der `IAddonHost`: Ihre Werkzeugkiste zum Kern](#kapitel-4-der-iaddonhost-ihre-werkzeugkiste-zum-kern)
    *   [Menü- und UI-Steuerung](#menü--und-ui-steuerung)
    *   [Kern-Dienste & Fenster](#kern-dienste--fenster)
    *   [Hotkeys & Eingabe (Neu & Mächtig)](#hotkeys--eingabe-neu--mächtig)
    *   [Daten speichern (Persistenz)](#daten-speichern-persistenz)
    *   [Logging & Lokalisierung](#logging--lokalisierung)
    *   [Theming (UI-Styling)](#theming-ui-styling)
    *   [Performance-Management](#performance-management)
*   [Kapitel 5: Fortgeschrittenes Tutorial: Den Core-Hotkey übernehmen](#kapitel-5-fortgeschrittenes-tutorial-den-core-hotkey-übernehmen)
*   [Kapitel 6: Einstellungs-UIs erstellen: Von einfach bis mächtig](#kapitel-6-einstellungs-uis-erstellen-von-einfach-bis-mächtig)
    *   [Methode 1: Das Baukasten-System (Legacy)](#methode-1-das-baukasten-system-legacy)
    *   [Methode 2: Volle UI-Freiheit (`UserControl` - Empfohlen)](#methode-2-volle-ui-freiheit-usercontrol---empfohlen)
*   [Kapitel 7: Fortgeschrittene Konzepte & Best Practices](#kapitel-7-fortgeschrittene-konzepte--best-practices)
*   [Kapitel 8: Fehlerbehebung: Häufige Probleme lösen](#kapitel-8-fehlerbehebung-häufige-probleme-lösen)
*   [Kapitel 9: Werden Sie Teil der Entwicklung!](#kapitel-9-werden-sie-teil-der-entwicklung)

---

<details>
<summary><strong>System-Prompt für die KI (Deutsch) & Gesamtes SDK-Manual (Kopieren)</strong></summary>

```
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

SDK MANUAL: DEINE EINZIGE WISSENSQUELLE:

SCOverlay Addon SDK
Das ultimative Entwicklerhandbuch für die SCOverlay-Plattform.
Erstelle deine eigenen Addons, integriere sie mit dem Kern und werde Teil des Ökosystems.

Kapitel 1: Unsere Vision: Eine Plattform für Entwickler
Willkommen, Entwickler! SCOverlay ist mehr als nur ein Tool – es ist ein Ökosystem. Unsere Vision ist es, eine stabile, performante und vor allem erweiterbare Plattform zu schaffen, auf der kreative Köpfe wie Sie aufbauen können. Sie müssen kein professioneller Programmierer sein, um etwas Erstaunliches zu schaffen. Dieses Handbuch ist hier, um Sie bei jedem Schritt zu unterstützen.
Modularität: Der Kern stellt die Bühne; Ihr Add-on ist der Star.
Stabilität & Performance: Als Game-Overlay ist die Performance entscheidend. Wir schützen das Spielerlebnis, damit Sie sich auf Features konzentrieren können.
Strikter Vertrag: Die SCOverlay.API.dll ist unser gemeinsames Fundament. Es ist ein Versprechen, dass Ihre Arbeit auch bei zukünftigen Updates funktionieren wird.

Kapitel 2: Der absolute Start: Von Null zum ersten Add-on in 10 Minuten
Dieses Kapitel ist für absolute Anfänger gedacht. Wir nehmen Sie bei der Hand und führen Sie ohne Umschweife zu Ihrem ersten funktionierenden Add-on.

Schritt 0: Die Werkzeuge(Voraussetzungen)
Bevor Sie loslegen, installieren Sie bitte diese beiden Dinge. Sie sind kostenlos und unerlässlich.
.NET 8 SDK: Das "Software Development Kit". Es ist der "Motor", der Ihren Code in eine funktionierende .dll-Datei umwandelt.
Download: Laden Sie das .NET 8 SDK (x64) von Microsoft herunter.
Visual Studio 2022 Community: Das "Cockpit". Ein Programm, in dem Sie Ihren Code schreiben, verwalten und kompilieren.
Download: Visual Studio 2022 Community Edition herunterladen
Wichtige Einstellung bei der Installation: Wählen Sie die Arbeitslast ".NET-Desktopentwicklung" aus. Dies stellt sicher, dass alle benötigten Komponenten installiert werden.

Schritt 1: Das Projekt-Fundament in Visual Studio
Neues Projekt: Öffnen Sie Visual Studio 2022 und wählen Sie "Neues Projekt erstellen".
Vorlage wählen: Suchen Sie nach "Klassenbibliothek" und wählen Sie die Vorlage mit den Tags C#, Windows, Bibliothek. Klicken Sie auf "Weiter".
Projekt benennen:
Projektname: MeinErstesAddon
Speicherort: Wählen Sie einen Ordner, z.B. C:\Dev\SCOverlay-Addons
Klicken Sie auf "Weiter".
Framework wählen: Wählen Sie .NET 8.0 (Langzeitunterstützung) und klicken Sie auf "Erstellen".
Aufräumen: Im Projektmappen-Explorer (rechte Seite), löschen Sie die automatisch erstellte Datei Class1.cs.
API-Referenz hinzufügen (Der wichtigste Schritt):
Neueste API herunterladen: Laden Sie immer die aktuellste Version der SCOverlay.API.dll direkt von der offiziellen Quelle herunter. Dies stellt sicher, dass Sie gegen die neueste Version entwickeln und Zugriff auf alle Features haben.
Offizieller Download-Link: https://github.com/BlugDeg/SCOverlay-Updates/blob/main/addons/SCOverlay.API.dll?raw=true
Speichern und Referenzieren:
Erstellen Sie in Ihrem Projektordner(z.B. in C:\Dev\SCOverlay-Addons\MeinErstesAddon) einen neuen Unterordner namens lib.
Speichern Sie die heruntergeladene SCOverlay.API.dll in diesem lib-Ordner.
Klicken Sie in Visual Studio im Projektmappen-Explorer mit der rechten Maustaste auf Abhängigkeiten > Assemblyverweis hinzufügen....
Klicken Sie auf "Durchsuchen..." und wählen Sie die SCOverlay.API.dll aus Ihrem neu erstellten lib-Ordner aus.
SEHR WICHTIG - Lokale Kopie verhindern: Klicken Sie auf die neu hinzugefügte SCOverlay.API unter Abhängigkeiten > Assemblys, drücken Sie F4, um die Eigenschaften anzuzeigen, und setzen Sie "Lokale Kopie" auf "Nein" (False). Dies ist entscheidend, um Versionskonflikte zu vermeiden.

Schritt 2: Die Projektdatei(.csproj) – Die Automatisierungs-Magie
Diese Datei ist der Bauplan für Ihr Projekt. Wir fügen hier eine Automatisierung ein, damit Ihr Add-on nach jedem Build direkt in den richtigen SCOverlay-Ordner kopiert wird.
Doppelklicken Sie im Projektmappen-Explorer auf den Projektnamen (MeinErstesAddon). Die .csproj-Datei wird als Text geöffnet.
Ersetzen Sie den gesamten Inhalt der .csproj-Datei mit diesem Code.
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>net8.0-windows</TargetFramework>
    <UseWindowsForms>true</UseWindowsForms>
    <CopyLocalLockFileAssemblies>true</CopyLocalLockFileAssemblies>
    <Nullable>enable</Nullable>
    <Version>1.0.0</Version>
    <AssemblyVersion>1.0.0</AssemblyVersion>
    <FileVersion>1.0.0</FileVersion>
  </PropertyGroup>
  <ItemGroup>
    <Reference Include="SCOverlay.API">
      <HintPath>lib\SCOverlay.API.dll</HintPath>
      <Private>false</Private>
    </Reference>
  </ItemGroup>
  <Target Name="CopyToAppData" AfterTargets="Build">
    <PropertyGroup>
      <AddonTargetDir>$(AppData)\SCOverlay\addons\$(ProjectName)</AddonTargetDir>
    </PropertyGroup>
    <Message Text="--> Kopiere Addon '$(ProjectName)' nach: $(AddonTargetDir)" Importance="high" />
    <MakeDir Directories="$(AddonTargetDir)" />
    <ItemGroup>
      <AddonFiles Include="$(TargetDir)$(ProjectName).dll" />
      <AddonFiles Include="$(TargetDir)$(ProjectName).pdb" Condition="Exists('$(TargetDir)$(ProjectName).pdb')" />
    </ItemGroup>
    <Copy SourceFiles="@(AddonFiles)" DestinationFolder="$(AddonTargetDir)" SkipUnchangedFiles="true" />
  </Target>
</Project>

Schritt 3: Der erste Code ("Hallo Welt")
Klicken Sie mit der rechten Maustaste auf Ihr Projekt (MeinErstesAddon), wählen Sie "Hinzufügen" > "Klasse...".
Geben Sie der Datei den Namen MeinAddon.cs und klicken Sie auf "Hinzufügen".
Ersetzen Sie den gesamten Inhalt der neuen Datei mit diesem Code. Die Kommentare erklären, was jede Zeile tut.
// Dateipfad: /MeinAddon.cs
using SCOverlay.API;
using System.Collections.Generic;
using System.Drawing;
using System.Windows.Forms;
namespace MeinErstesAddon
{
    [Addon]
    public class MeinAddon : IAddon
    {
        private IAddonHost? _host;
        public string Name => "Mein Erstes Addon";
        public string Author => "Dein Name";
        public string Version => "1.0.0";
        public void Initialize(IAddonHost host)
        {
            _host = host;
            _host.LogInfo($"[{Name}] wurde erfolgreich geladen!");
        }
        public IEnumerable<AddonButton> GetMainMenuButtons()
        {
            yield return new AddonButton(
                id: "mein_hallo_button",
                getLabel: () => "Sag Hallo!",
                onClick: () => {
                    _host?.Window.ShowNotification("Hallo von meinem Addon!");
                }
            );
        }
        public void Shutdown() { }
        public void Draw(Graphics g, Rectangle bounds) { }
        public void OnOverlayVisibilityChanged(bool isVisible) { }
        public IEnumerable<AddonControl> GetSettingsControls() => [];
        public UserControl? GetSettingsControl(IAddonHost host) => null;
        public IDictionary<string, (string en, string de)> GetLocalizations() => new Dictionary<string, (string, string)>();
    }
}

Schritt 4: Kompilieren und Testen
Kompilieren (Build): Drücken Sie in Visual Studio die Tastenkombination Strg + B oder gehen Sie im Menü auf "Erstellen > Projektmappe erstellen".
Überprüfen: Im "Ausgabe"-Fenster unten sollten Sie eine Meldung sehen wie: --> Kopiere Addon 'MeinErstesAddon' nach: C: \Users\DEINNAME\AppData\Roaming\SCOverlay\addons\MeinErstesAddon. Das bedeutet, die Automatisierung hat funktioniert!
Testen: Starten Sie SCOverlay (oder starten Sie es neu). Öffnen Sie das Hauptmenü. Ihr Button "Sag Hallo!" sollte nun da sein. Klicken Sie ihn an!
Glückwunsch! Sie sind jetzt ein SCOverlay Add-on-Entwickler!

Kapitel 3: Die IAddon-Schnittstelle: Die DNA Ihres Add-ons
Dies ist der Bauplan für jedes Add-on. Ihre Hauptklasse muss alle diese Mitglieder implementieren.
Member	Typ	Zweck & Detaillierte Erklärung
Name, Author, Version	string	Metadaten: Identifiziert Ihr Add-on. Wird in den Einstellungen unter "Erweitert" angezeigt.
Initialize(IAddonHost host)	void	Konstruktor: Wird einmal beim Laden aufgerufen. Speichern Sie die host-Instanz hier. Dies ist Ihre Setup-Phase. Registrieren Sie hier z.B. permanente Hotkeys.
GetMainMenuButtons()	IEnumerable<AddonButton>	Hauptmenü-Buttons: Definiert die Buttons, die Ihr Add-on im Hauptmenü anzeigt.
OnExclusiveHotkey()	void	(NEU) Der Callback, den der Core aufruft, wenn Sie exklusive Hotkey-Kontrolle haben und der Hotkey gedrückt wird. Hat eine leere Standardimplementierung, ist also optional.
GetSettingsControl(...)	UserControl?	(Empfohlen) Bietet ein komplettes, benutzerdefiniertes UI-Panel für Ihre Einstellungen. Gibt Ihnen totale kreative Freiheit. Siehe Kapitel 6.
GetSettingsControls()	IEnumerable<AddonControl>	(Legacy) Eine limitierte Methode, um simple Controls zur Einstellungsseite hinzuzufügen. Nur für sehr einfache Add-ons ohne UI-Ambitionen.
Draw(Graphics g, ...)	void	Zeichen-Engine: Wird bei jedem Frame aufgerufen, in dem das Overlay neu gezeichnet wird. Halten Sie diesen Code extrem schnell! Langsame Operationen hier führen zu Rucklern.
OnOverlayVisibilityChanged(...)	void	Status-Synchronisation: Reagiert auf das Öffnen/Schließen des Overlays. Nützlich, um Hintergrundaufgaben zu starten/stoppen oder UI-Elemente ein-/auszublenden.
Shutdown()	void	Aufräumen: Wird aufgerufen, bevor das Add-on entladen wird. Geben Sie hier alle Ressourcen frei (z.B. schließen Sie Fenster), um Fehler zu vermeiden.
GetLocalizations()	IDictionary<...>	Lokalisierung: Stellen Sie hier englische und deutsche Übersetzungen für die UI-Texte Ihres Add-ons bereit.

Kapitel 4: Der IAddonHost: Ihre Werkzeugkiste zum Kern
Der IAddonHost ist Ihre Brücke zu allen Features von SCOverlay. Sie erhalten ihn in der Initialize-Methode und sollten ihn für die gesamte Lebensdauer Ihres Add-ons aufbewahren.

Menü- und UI-Steuerung
void TakeMenuControl(...): Übernimmt die exklusive Kontrolle über das Hauptmenü, um eigene Untermenüs zu erstellen.
void ReleaseMenuControl(): Gibt die Kontrolle an das Hauptmenü zurück.
void InvalidateOverlay(): Erzwingt ein sofortiges Neuzeichnen. Unerlässlich, um Ihre UI-Änderungen sichtbar zu machen.
void HideMenu(): (NEU)Schließt das gesamte Overlay-Menü programmgesteuert.

Kern-Dienste & Fenster
ISoundService Sound { get; }
PlayFile(...): Spielt eine Sounddatei asynchron ab, ohne das Overlay einzufrieren.
IWindowService Window { get; }
ShowNotification(...): Zeigt eine kurze, nicht-blockierende "Toast"-Benachrichtigung an.
CreateThemedWindow(...): Erstellt ein neues, leeres, benutzerdefiniertes Fenster (wie das Haupt-Overlay). Nicht für Standard-Controls wie Buttons geeignet.
CreateStandardWindow(...): (NEU)Erstellt ein neues Fenster, das das Theme erbt und perfekt für das Hosten von Standard-Controls wie Buttons, Labels etc. geeignet ist. Dies ist die richtige Wahl für interaktive Dialoge.
Show/HideFilterOverlay(...): Zeigt einen bildschirmfüllenden Farbfilter an oder versteckt ihn.
Task<Image> TakeScreenshotAsync(): Erstellt asynchron einen Screenshot des Spielbildschirms.

Hotkeys & Eingabe (Neu & Mächtig)
Wichtiges API-Update: Das alte, fehleranfällige SuppressCoreHotkeys wurde entfernt. Das neue System gibt Ihnen volle, aber sichere Kontrolle über den Haupt-Hotkey.
bool RequestExclusiveHotkeyControl(IAddon addon):
Zweck: Dies ist die neue Methode, um den Haupt-Hotkey des Overlays für Ihr Add-on zu "entführen".
Funktion: Sie fordern die exklusive Kontrolle an. Wenn kein anderes Add-on sie bereits hat, gibt die Methode true zurück. Ab diesem Moment werden alle Drücke des Haupt-Hotkeys an die OnExclusiveHotkey()-Methode Ihres Add-ons weitergeleitet.
void ReleaseExclusiveHotkeyControl(IAddon addon):
Zweck: Gibt die Kontrolle an den Core zurück.
Funktion: Wenn Sie fertig sind (z.B. wenn Ihr Fenster schließt), müssen Sie diese Methode aufrufen, damit das Haupt-Overlay wieder auf den Hotkey reagieren kann.
void BlockGameInput(bool block):
Zweck: Unverändert und unerlässlich für interaktive UI. Blockiert oder gibt die Eingabe an das Spiel frei.
RegisterHotkey, UnregisterHotkey, RebindHotkey:
Zweck: Für das Hinzufügen von zusätzlichen, benutzerdefinierten Hotkeys für Ihr Add-on, die unabhängig vom Core-Hotkey sind.

Daten speichern (Persistenz)
string GetSetting(...) & void SetSetting(...): Ein einfacher Schlüssel-Wert-Speicher für Ihr Add-on.
Best Practice: Verwenden Sie immer ein eindeutiges Präfix für Ihre Schlüssel (z.B. MeinAddon_ApiToken), um Konflikte zu vermeiden.

Logging & Lokalisierung
LogInfo(...) & LogError(...): Schreibt in die zentrale debug.log-Datei. Ihr wichtigstes Werkzeug zur Fehlersuche!
string T(...): Greift auf das zentrale Übersetzungssystem für mehrsprachige Texte zu.

Theming (UI-Styling)
Color Theme_Background { get; }, Font Theme_TextFont { get; }, etc.: Schreibgeschützter Zugriff auf das aktive Theme. Unerlässlich, um Ihre benutzerdefinierte UserControl-Einstellungs-UI an den Rest des Overlays anzupassen.

Performance-Management
void RequestHighPerformanceMode(...) & void ReleaseHighPerformanceMode(...): Teilt dem "Performance Watchdog" vorübergehend mit, während einer kurzen, CPU-intensiven Aufgabe nicht einzugreifen.

Kapitel 5: Fortgeschrittenes Tutorial: Den Core-Hotkey übernehmen
Dieses Tutorial zeigt, wie Sie das neue System verwenden, um Ihre eigene UI anstelle des Hauptmenüs zu öffnen.

Schritt 1: Die Logik vorbereiten
Definieren Sie die Logik in Ihrer Add-on-Klasse zum Starten und Stoppen Ihres exklusiven Modus.
private IAddonHost? _host;
private Form? _myExclusiveWindow;
private bool _hasControl = false;
private void StartExclusiveMode()
{
    if (_host == null || _hasControl) return;
    if (_host.RequestExclusiveHotkeyControl(this))
    {
        _hasControl = true;
        _host.Window.ShowNotification("Kontrolle übernommen!");
        _host.HideMenu();
        OpenMyWindow();
    }
}
private void StopExclusiveMode()
{
    if (_host == null || !_hasControl) return;
    _myExclusiveWindow?.Close();
    _myExclusiveWindow = null;
    _host.ReleaseExclusiveHotkeyControl(this);
    _hasControl = false;
    _host.Window.ShowNotification("Kontrolle freigegeben!");
}
private void OpenMyWindow()
{
    _myExclusiveWindow = _host.Window.CreateStandardWindow("Mein Panel");
    _myExclusiveWindow.FormClosed += (s, e) => StopExclusiveMode(); // Failsafe!
    _myExclusiveWindow.Show();
}

Schritt 2: Auf den Hotkey reagieren
Implementieren Sie die OnExclusiveHotkey-Methode. Sie wird nun vom Core aufgerufen.
public void OnExclusiveHotkey()
{
    if (_myExclusiveWindow != null && !_myExclusiveWindow.IsDisposed)
    {
        _myExclusiveWindow.Visible = !_myExclusiveWindow.Visible;
    }
    else
    {
        OpenMyWindow();
    }
}

Schritt 3: Kontrolle freigeben
Siehe StopExclusiveMode() oben. Der Aufruf von _host.ReleaseExclusiveHotkeyControl(this) ist der entscheidende Teil. Stellen Sie sicher, dass dies geschieht, wenn Ihre Funktion beendet ist (z.B. wenn der Benutzer Ihr Fenster schließt).

Schritt 4: Beim Herunterfahren aufräumen
Stellen Sie immer sicher, dass Sie die Kontrolle an den Core zurückgeben, wenn Ihr Add-on entladen wird.
public void Shutdown()
{
    StopExclusiveMode();
}

Dieses System ist robust, sicher und gibt Ihnen die volle Kontrolle darüber, wann und wie Ihr Add-on auf den Haupt-Hotkey reagiert.

Kapitel 6: Einstellungs-UIs erstellen: Von einfach bis mächtig
Sie haben zwei Möglichkeiten, eine Einstellungsseite für Ihr Add-on zu erstellen. Wählen Sie die, die Ihren Anforderungen entspricht.

Methode 1: Das Baukasten-System (Legacy)
Mit GetSettingsControls() geben Sie dem Core eine Liste einfacher Bausteine (AddonControl, HotkeyControl). Der Core stapelt diese dann vertikal für Sie.
Vorteile: Sehr einfach für grundlegende Bedürfnisse.
Nachteile: Extrem limitiert. Keine Schieberegler, Textboxen oder benutzerdefinierten Layouts.
public IEnumerable<AddonControl> GetSettingsControls()
{
    yield return new HotkeyControl(
        identifier: "myaddon_hotkey_ctrl",
        label: "Special Action Hotkey",
        hotkeyIdentifier: "MyAddon_Action1",
        defaultHotkey: "Shift+F1"
    );
}

Methode 2: Volle UI-Freheit (UserControl - Empfohlen)
Mit GetSettingsControl(IAddonHost host) erstellen Sie Ihre gesamte Einstellungsseite visuell im Visual Studio Designer und übergeben diese komplette UI an den Core. Dies ist der moderne und empfohlene Ansatz.
Vorteile: Totale kreative Freiheit. Verwenden Sie Schieberegler, Textboxen, Bilder, Dropdowns und ordnen Sie sie nach Belieben an.
Nachteile: Erfordert etwas mehr Setup.
So geht's:
1. Ihr UserControl erstellen
Klicken Sie in Visual Studio mit der rechten Maustaste auf Ihr Projekt > Hinzufügen > Benutzersteuerelement (Windows Forms). Nennen Sie es MySettingsPanel.cs. Verwenden Sie den visuellen Designer, um Steuerelemente per Drag-and-Drop auf Ihr Panel zu ziehen.
2. Den Code implementieren
Ihre IAddon-Klasse gibt nun einfach eine Instanz Ihres neuen Panels zurück:
// In Ihrer IAddon-Hauptklasse
public UserControl? GetSettingsControl(IAddonHost host)
{
    return new MySettingsPanel(host, this);
}
// Und lassen die alte Methode leer
public IEnumerable<AddonControl> GetSettingsControls() => [];
Der Code für Ihre MySettingsPanel.cs wendet das Theme des Cores auf Ihre UI an und kann Methoden in Ihrer Haupt-Add-on-Klasse aufrufen:
// In Ihrer MySettingsPanel.cs-Datei
using SCOverlay.API;
using System.Windows.Forms;
public partial class MySettingsPanel : UserControl
{
    private readonly IAddonHost _host;
    private readonly MeinAddon _addonInstance;
    public MySettingsPanel(IAddonHost host, MeinAddon addonInstance)
    {
        InitializeComponent();
        _host = host;
        _addonInstance = addonInstance;
        ApplyThemeToAllControls(this);
        meinTestButton.Click += (s, e) => _addonInstance.DoSomethingCool();
    }
    private void ApplyThemeToAllControls(Control parent)
    {
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
            if (control.HasChildren)
            {
                ApplyThemeToAllControls(control);
            }
        }
    }
}
Dieser Ansatz gibt Ihnen eine professionelle, vollständig benutzerdefinierte Einstellungs-UI, die dennoch perfekt zum Erscheinungsbild von SCOverlay passt.

Kapitel 7: Fortgeschrittene Konzepte & Best Practices
Lizenzierung für Premium-Add-ons
Möchten Sie Ihr Add-on Unterstützern anbieten? Dies ist ein kollaborativer Prozess.
Entwickeln Sie Ihr Add-on.
Kontaktieren Sie uns: Wenn es fertig ist, kontaktieren Sie den Ersteller (BlugDeg) über ein GitHub-Issue.
Integration: Wir generieren eine einzigartige LicenseId für Sie.
Implementierung: Sie fügen das Attribut zu Ihrer Add-on-Klasse hinzu.
[Addon(LicenseId = "MySuperAddon")]
public class MyPremiumAddon : IAddon { /* ... */ }

Dos & Don'ts: Der Weg zum stabilen Add-on
✅ Ressourcen freigeben: Rufen Sie Dispose() für alle Fenster oder UserControls auf, die Sie erstellen, normalerweise in Ihrer Shutdown()-Methode, um Speicherlecks zu vermeiden.
❌ Blockieren Sie niemals Draw(): Führen Sie keine langen Operationen (wie Dateizugriffe oder Webanfragen) in Draw aus. Es wird zu Rucklern führen.
❌ Gehen Sie nicht von einem UI-Thread aus: Wenn Sie die Benutzeroberfläche aus einem Hintergrund-Task aktualisieren, verwenden Sie meinControl.BeginInvoke(...).

Kapitel 8: Fehlerbehebung: Häufige Probleme lösen
"Mein Add-on erscheint nicht im Menü!"
Falsche Ordnerstruktur: Der Ordner in %AppData%\SCOverlay\addons muss exakt denselben Namen haben wie Ihre DLL-Datei (ohne die .dll-Endung).
"Lokale Kopie" ist Wahr: Der SCOverlay.API - Verweis muss "Lokale Kopie" auf "Nein" (False) gesetzt haben.
Fehler beim Start: Überprüfen Sie die debug.log in %AppData%\SCOverlay\.
"Meine UI-Änderung wird nicht angezeigt!"
Lösung: Sie müssen _host?.InvalidateOverlay(); aufrufen, nachdem Sie etwas geändert haben, das visuell aktualisiert werden soll.
"Mein Add-on verschwindet plötzlich!"
Ursache: Der Performance Watchdog oder der Hotkey-Failsafe hat Ihr Add-on ausgeworfen.
Lösung: Überprüfen Sie die debug.log auf CRITICAL-Meldungen. Ihr Add-on hat einen schwerwiegenden Fehler verursacht.

Kapitel 9: Werden Sie Teil der Entwicklung!
Ihr Beitrag ist wertvoll. Ihre Ideen und Ihre Hilfe sind immer willkommen. Erstellen Sie ein Issue auf GitHub, um Hilfe zu erhalten oder Features vorzuschlagen. Wir sind gespannt, was Sie erschaffen werden!
```
</details>

## Kapitel 1: Unsere Vision: Eine Plattform für Entwickler

Willkommen, Entwickler! SCOverlay ist mehr als nur ein Tool – es ist ein Ökosystem. Unsere Vision ist es, eine stabile, performante und vor allem erweiterbare Plattform zu schaffen, auf der kreative Köpfe wie Sie aufbauen können. Sie müssen kein professioneller Programmierer sein, um etwas Erstaunliches zu schaffen. Dieses Handbuch ist hier, um Sie bei jedem Schritt zu unterstützen.

*   **Modularität:** Der Kern stellt die Bühne; Ihr Add-on ist der Star.
*   **Stabilität & Performance:** Als Game-Overlay ist die Performance entscheidend. Wir schützen das Spielerlebnis, damit Sie sich auf Features konzentrieren können.
*   **Strikter Vertrag:** Die `SCOverlay.API.dll` ist unser gemeinsames Fundament. Es ist ein Versprechen, dass Ihre Arbeit auch bei zukünftigen Updates funktionieren wird.

---

## Kapitel 2: Der absolute Start: Von Null zum ersten Add-on in 10 Minuten

Dieses Kapitel ist für absolute Anfänger gedacht. Wir nehmen Sie bei der Hand und führen Sie ohne Umschweife zu Ihrem ersten funktionierenden Add-on.

### Schritt 0: Die Werkzeuge (Voraussetzungen)

Bevor Sie loslegen, installieren Sie bitte diese beiden Dinge. Sie sind **kostenlos und unerlässlich**.

1.  **.NET 8 SDK:** Das "Software Development Kit". Es ist der "Motor", der Ihren Code in eine funktionierende `.dll`-Datei umwandelt.
    *   **Download:** [Laden Sie das .NET 8 SDK (x64) von Microsoft herunter.](https://dotnet.microsoft.com/en-us/download/dotnet/8.0)

2.  **Visual Studio 2022 Community:** Das "Cockpit". Ein Programm, in dem Sie Ihren Code schreiben, verwalten und kompilieren.
    *   **Download:** [Visual Studio 2022 Community Edition herunterladen](https://visualstudio.microsoft.com/vs/community/)
    *   **Wichtige Einstellung bei der Installation:** Wählen Sie die Arbeitslast **".NET-Desktopentwicklung"** aus. Dies stellt sicher, dass alle benötigten Komponenten installiert werden.

### Schritt 1: Das Projekt-Fundament in Visual Studio

1.  **Neues Projekt:** Öffnen Sie Visual Studio 2022 und wählen Sie **"Neues Projekt erstellen"**.
2.  **Vorlage wählen:** Suchen Sie nach **"Klassenbibliothek"** und wählen Sie die Vorlage mit den Tags `C#`, `Windows`, `Bibliothek`. Klicken Sie auf "Weiter".
3.  **Projekt benennen:**
    *   **Projektname:** `MeinErstesAddon`
    *   **Speicherort:** Wählen Sie einen Ordner, z.B. `C:\Dev\SCOverlay-Addons`
    *   Klicken Sie auf "Weiter".
4.  **Framework wählen:** Wählen Sie **.NET 8.0 (Langzeitunterstützung)** und klicken Sie auf "Erstellen".
5.  **Aufräumen:** Im Projektmappen-Explorer (rechte Seite), löschen Sie die automatisch erstellte Datei `Class1.cs`.
6.  **API-Referenz hinzufügen (Der wichtigste Schritt):**
    *   **Neueste API herunterladen:** Laden Sie **immer** die aktuellste Version der `SCOverlay.API.dll` direkt von der offiziellen Quelle herunter. Dies stellt sicher, dass Sie gegen die neueste Version entwickeln und Zugriff auf alle Features haben.
        *   **Offizieller Download-Link:** [https://github.com/BlugDeg/SCOverlay-Updates/blob/main/addons/SCOverlay.API.dll?raw=true](https://github.com/BlugDeg/SCOverlay-Updates/blob/main/addons/SCOverlay.API.dll?raw=true)
    *   **Speichern und Referenzieren:**
        *   Erstellen Sie in Ihrem Projektordner (z.B. in `C:\Dev\SCOverlay-Addons\MeinErstesAddon`) einen neuen Unterordner namens `lib`.
        *   Speichern Sie die heruntergeladene `SCOverlay.API.dll` in diesem `lib`-Ordner.
        *   Klicken Sie in Visual Studio im Projektmappen-Explorer mit der rechten Maustaste auf **Abhängigkeiten > Assemblyverweis hinzufügen...**.
        *   Klicken Sie auf **"Durchsuchen..."** und wählen Sie die `SCOverlay.API.dll` aus Ihrem neu erstellten `lib`-Ordner aus.
    *   **SEHR WICHTIG - Lokale Kopie verhindern:** Klicken Sie auf die neu hinzugefügte `SCOverlay.API` unter `Abhängigkeiten > Assemblys`, drücken Sie `F4`, um die Eigenschaften anzuzeigen, und setzen Sie **"Lokale Kopie" auf "Nein" (False)**. Dies ist entscheidend, um Versionskonflikte zu vermeiden.

### Schritt 2: Die Projektdatei (`.csproj`) – Die Automatisierungs-Magie

Diese Datei ist der Bauplan für Ihr Projekt. Wir fügen hier eine Automatisierung ein, damit Ihr Add-on nach jedem Build direkt in den richtigen SCOverlay-Ordner kopiert wird.

1.  Doppelklicken Sie im Projektmappen-Explorer auf den Projektnamen (`MeinErstesAddon`). Die `.csproj`-Datei wird als Text geöffnet.
2.  **Ersetzen Sie den gesamten Inhalt** der `.csproj`-Datei mit diesem Code.

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <!-- Grundlegende Projekteinstellungen -->
    <TargetFramework>net8.0-windows</TargetFramework>
    <UseWindowsForms>true</UseWindowsForms>
    <CopyLocalLockFileAssemblies>true</CopyLocalLockFileAssemblies>
    <Nullable>enable</Nullable>
    <Version>1.0.0</Version>
    <AssemblyVersion>1.0.0</AssemblyVersion>
    <FileVersion>1.0.0</FileVersion>
  </PropertyGroup>

  <ItemGroup>
    <!-- Dieser Block verweist auf die SCOverlay API, die für die Entwicklung benötigt wird. -->
    <Reference Include="SCOverlay.API">
      <!-- 
        !!! WICHTIG: Dieser Pfad zeigt auf die API.dll, die Sie in den 'lib'-Ordner 
        Ihres Projekts heruntergeladen haben.
      -->
      <HintPath>lib\SCOverlay.API.dll</HintPath>
      <Private>false</Private> <!-- Entspricht "Lokale Kopie: Nein" -->
    </Reference>
  </ItemGroup>

  <!-- DIESER BLOCK IST DIE AUTOMATISCHE KOPIER-MAGIE -->
  <Target Name="CopyToAppData" AfterTargets="Build">
    <PropertyGroup>
      <!-- Definiert das Zielverzeichnis: %AppData%\SCOverlay\addons\PROJEKTNAME -->
      <AddonTargetDir>$(AppData)\SCOverlay\addons\$(ProjectName)</AddonTargetDir>
    </PropertyGroup>
    <Message Text="--> Kopiere Addon '$(ProjectName)' nach: $(AddonTargetDir)" Importance="high" />
    <MakeDir Directories="$(AddonTargetDir)" />
    <ItemGroup>
      <!-- Sammelt alle für das Add-on notwendigen Dateien (DLL und Debug-Informationen) -->
      <AddonFiles Include="$(TargetDir)$(ProjectName).dll" />
      <AddonFiles Include="$(TargetDir)$(ProjectName).pdb" Condition="Exists('$(TargetDir)$(ProjectName).pdb')" />
    </ItemGroup>
    <!-- Führt den Kopiervorgang durch -->
    <Copy SourceFiles="@(AddonFiles)" DestinationFolder="$(AddonTargetDir)" SkipUnchangedFiles="true" />
  </Target>

</Project>
```

### Schritt 3: Der erste Code ("Hallo Welt")

1.  Klicken Sie mit der rechten Maustaste auf Ihr Projekt (`MeinErstesAddon`), wählen Sie **"Hinzufügen" > "Klasse..."**.
2.  Geben Sie der Datei den Namen `MeinAddon.cs` und klicken Sie auf "Hinzufügen".
3.  Ersetzen Sie den gesamten Inhalt der neuen Datei mit diesem Code. Die Kommentare erklären, was jede Zeile tut.

```csharp
// Dateipfad: /MeinAddon.cs

// "using" importiert Werkzeugkisten, die wir brauchen.
using SCOverlay.API;
using System.Collections.Generic;
using System.Drawing;
using System.Windows.Forms;

// Ein Namespace ist wie ein Ordner für unseren Code.
namespace MeinErstesAddon
{
    // Das [Addon]-Attribut sagt SCOverlay: "Hey, das hier ist ein Add-on!"
    [Addon]
    public class MeinAddon : IAddon
    {
        // Eine private Variable, um unsere "Brücke" zu SCOverlay zu speichern.
        private IAddonHost? _host;

        // Grundlegende Informationen über unser Add-on.
        public string Name => "Mein Erstes Addon";
        public string Author => "Dein Name";
        public string Version => "1.0.0";

        // Wird einmal aufgerufen, wenn SCOverlay das Add-on lädt.
        public void Initialize(IAddonHost host)
        {
            _host = host; // Wir speichern die Brücke für die spätere Verwendung.
            _host.LogInfo($"[{Name}] wurde erfolgreich geladen!");
        }

        // Fügt Buttons zum Hauptmenü von SCOverlay hinzu.
        public IEnumerable<AddonButton> GetMainMenuButtons()
        {
            // Wir erstellen und "geben" einen neuen Button an das Hauptmenü zurück.
            yield return new AddonButton(
                id: "mein_hallo_button",
                getLabel: () => "Sag Hallo!", // Text auf dem Button.
                onClick: () => {
                    // Was passiert, wenn man klickt: Zeige eine Benachrichtigung.
                    _host?.Window.ShowNotification("Hallo von meinem Addon!");
                }
            );
        }

        // Die restlichen Methoden sind Pflicht, aber wir brauchen sie jetzt nicht.
        public void Shutdown() { }
        public void Draw(Graphics g, Rectangle bounds) { }
        public void OnOverlayVisibilityChanged(bool isVisible) { }
        public IEnumerable<AddonControl> GetSettingsControls() => [];
        public UserControl? GetSettingsControl(IAddonHost host) => null;
        public IDictionary<string, (string en, string de)> GetLocalizations() => new Dictionary<string, (string, string)>();
    }
}
```

### Schritt 4: Kompilieren und Testen

1.  **Kompilieren (Build):** Drücken Sie in Visual Studio die Tastenkombination `Strg + B` oder gehen Sie im Menü auf **"Erstellen > Projektmappe erstellen"**.
2.  **Überprüfen:** Im "Ausgabe"-Fenster unten sollten Sie eine Meldung sehen wie: `--> Kopiere Addon 'MeinErstesAddon' nach: C:\Users\DEINNAME\AppData\Roaming\SCOverlay\addons\MeinErstesAddon`. Das bedeutet, die Automatisierung hat funktioniert!
3.  **Testen:** Starten Sie SCOverlay (oder starten Sie es neu). Öffnen Sie das Hauptmenü. Ihr Button **"Sag Hallo!"** sollte nun da sein. Klicken Sie ihn an!

**Glückwunsch! Sie sind jetzt ein SCOverlay Add-on-Entwickler!**

---

## Kapitel 3: Die `IAddon`-Schnittstelle: Die DNA Ihres Add-ons

Dies ist der Bauplan für jedes Add-on. Ihre Hauptklasse muss alle diese Mitglieder implementieren.

| Member                        | Typ                              | Zweck & Detaillierte Erklärung                                                                                                 |
| :---------------------------- | :-------------------------------- | :----------------------------------------------------------------------------------------------------------------------------- |
| `Name`, `Author`, `Version`   | `string`                          | **Metadaten:** Identifiziert Ihr Add-on. Wird in den Einstellungen unter "Erweitert" angezeigt. |
| `Initialize(IAddonHost host)` | `void`                            | **Konstruktor:** Wird einmal beim Laden aufgerufen. Speichern Sie die `host`-Instanz hier. Dies ist Ihre Setup-Phase. Registrieren Sie hier z.B. permanente Hotkeys. |
| `GetMainMenuButtons()`        | `IEnumerable<AddonButton>`        | **Hauptmenü-Buttons:** Definiert die Buttons, die Ihr Add-on im Hauptmenü anzeigt. |
| `OnExclusiveHotkey()`         | `void`                            | **(NEU)** Der Callback, den der Core aufruft, wenn Sie exklusive Hotkey-Kontrolle haben und der Hotkey gedrückt wird. Hat eine leere Standardimplementierung, ist also optional. |
| `GetSettingsControl(...)` | `UserControl?`                    | **(Empfohlen)** Bietet ein komplettes, benutzerdefiniertes UI-Panel für Ihre Einstellungen. Gibt Ihnen totale kreative Freiheit. Siehe Kapitel 6. |
| `GetSettingsControls()`       | `IEnumerable<AddonControl>`       | **(Legacy)** Eine limitierte Methode, um simple Controls zur Einstellungsseite hinzuzufügen. Nur für sehr einfache Add-ons ohne UI-Ambitionen. |
| `Draw(Graphics g, ...)`       | `void`                            | **Zeichen-Engine:** Wird bei jedem Frame aufgerufen, in dem das Overlay neu gezeichnet wird. **Halten Sie diesen Code extrem schnell!** Langsame Operationen hier führen zu Rucklern. |
| `OnOverlayVisibilityChanged(...)` | `void`                            | **Status-Synchronisation:** Reagiert auf das Öffnen/Schließen des Overlays. Nützlich, um Hintergrundaufgaben zu starten/stoppen oder UI-Elemente ein-/auszublenden. |
| `Shutdown()`                  | `void`                            | **Aufräumen:** Wird aufgerufen, bevor das Add-on entladen wird. Geben Sie hier alle Ressourcen frei (z.B. schließen Sie Fenster), um Fehler zu vermeiden. |
| `GetLocalizations()`          | `IDictionary<...>`                | **Lokalisierung:** Stellen Sie hier englische und deutsche Übersetzungen für die UI-Texte Ihres Add-ons bereit. |

---

## Kapitel 4: Der `IAddonHost`: Ihre Werkzeugkiste zum Kern

Der `IAddonHost` ist Ihre Brücke zu allen Features von SCOverlay. Sie erhalten ihn in der `Initialize`-Methode und sollten ihn für die gesamte Lebensdauer Ihres Add-ons aufbewahren.

### Menü- und UI-Steuerung

*   `void TakeMenuControl(...)`: Übernimmt die exklusive Kontrolle über das Hauptmenü, um eigene Untermenüs zu erstellen.
*   `void ReleaseMenuControl()`: Gibt die Kontrolle an das Hauptmenü zurück.
*   `void InvalidateOverlay()`: Erzwingt ein sofortiges Neuzeichnen. **Unerlässlich**, um Ihre UI-Änderungen sichtbar zu machen.
*   `void HideMenu()`: **(NEU)** Schließt das gesamte Overlay-Menü programmgesteuert.

### Kern-Dienste & Fenster

*   `ISoundService Sound { get; }`
    *   `PlayFile(...)`: Spielt eine Sounddatei asynchron ab, ohne das Overlay einzufrieren.
*   `IWindowService Window { get; }`
    *   `ShowNotification(...)`: Zeigt eine kurze, nicht-blockierende "Toast"-Benachrichtigung an.
    *   `CreateThemedWindow(...)`: Erstellt ein neues, leeres, benutzerdefiniertes Fenster (wie das Haupt-Overlay). **Nicht für Standard-Controls wie Buttons geeignet.**
    *   `CreateStandardWindow(...)`: **(NEU)** Erstellt ein neues Fenster, das das Theme erbt und **perfekt für das Hosten von Standard-Controls** wie Buttons, Labels etc. geeignet ist. Dies ist die richtige Wahl für interaktive Dialoge.
    *   `Show/HideFilterOverlay(...)`: Zeigt einen bildschirmfüllenden Farbfilter an oder versteckt ihn.
*   `Task<Image> TakeScreenshotAsync()`: Erstellt asynchron einen Screenshot des Spielbildschirms.

### Hotkeys & Eingabe (Neu & Mächtig)

> **Wichtiges API-Update:** Das alte, fehleranfällige `SuppressCoreHotkeys` wurde entfernt. Das neue System gibt Ihnen volle, aber sichere Kontrolle über den Haupt-Hotkey.

*   `bool RequestExclusiveHotkeyControl(IAddon addon)`:
    *   **Zweck:** Dies ist die neue Methode, um den Haupt-Hotkey des Overlays für Ihr Add-on zu "entführen".
    *   **Funktion:** Sie fordern die exklusive Kontrolle an. Wenn kein anderes Add-on sie bereits hat, gibt die Methode `true` zurück. Ab diesem Moment werden alle Drücke des Haupt-Hotkeys an die `OnExclusiveHotkey()`-Methode Ihres Add-ons weitergeleitet.
*   `void ReleaseExclusiveHotkeyControl(IAddon addon)`:
    *   **Zweck:** Gibt die Kontrolle an den Core zurück.
    *   **Funktion:** Wenn Sie fertig sind (z.B. wenn Ihr Fenster schließt), **müssen** Sie diese Methode aufrufen, damit das Haupt-Overlay wieder auf den Hotkey reagieren kann.
*   `void BlockGameInput(bool block)`:
    *   **Zweck:** Unverändert und unerlässlich für interaktive UI. Blockiert oder gibt die Eingabe an das Spiel frei.
*   `RegisterHotkey`, `UnregisterHotkey`, `RebindHotkey`:
    *   **Zweck:** Für das Hinzufügen von **zusätzlichen, benutzerdefinierten Hotkeys** für Ihr Add-on, die unabhängig vom Core-Hotkey sind.

### Daten speichern (Persistenz)

*   `string GetSetting(...) & void SetSetting(...):` Ein einfacher Schlüssel-Wert-Speicher für Ihr Add-on.
*   **Best Practice:** Verwenden Sie immer ein eindeutiges Präfix für Ihre Schlüssel (z.B. `MeinAddon_ApiToken`), um Konflikte zu vermeiden.

### Logging & Lokalisierung

*   `LogInfo(...) & LogError(...):` Schreibt in die zentrale `debug.log`-Datei. Ihr wichtigstes Werkzeug zur Fehlersuche!
*   `string T(...):` Greift auf das zentrale Übersetzungssystem für mehrsprachige Texte zu.

### Theming (UI-Styling)

*   `Color Theme_Background { get; }`, `Font Theme_TextFont { get; }`, etc.: Schreibgeschützter Zugriff auf das aktive Theme. Unerlässlich, um Ihre benutzerdefinierte `UserControl`-Einstellungs-UI an den Rest des Overlays anzupassen.

### Performance-Management

*   `void RequestHighPerformanceMode(...) & void ReleaseHighPerformanceMode(...):` Teilt dem "Performance Watchdog" vorübergehend mit, während einer kurzen, CPU-intensiven Aufgabe nicht einzugreifen.

---

## Kapitel 5: Fortgeschrittenes Tutorial: Den Core-Hotkey übernehmen

Dieses Tutorial zeigt, wie Sie das neue System verwenden, um Ihre eigene UI anstelle des Hauptmenüs zu öffnen.

### Schritt 1: Die Logik vorbereiten

Definieren Sie die Logik in Ihrer Add-on-Klasse zum Starten und Stoppen Ihres exklusiven Modus.
```csharp
private IAddonHost? _host;
private Form? _myExclusiveWindow;
private bool _hasControl = false;

// Methode zum Starten des Modus (z.B. durch einen Button-Klick)
private void StartExclusiveMode()
{
    if (_host == null || _hasControl) return;

    // 1. Kontrolle anfordern
    if (_host.RequestExclusiveHotkeyControl(this))
    {
        _hasControl = true;
        _host.Window.ShowNotification("Kontrolle übernommen!");
        
        // 2. Core-Menü sicher ausblenden
        _host.HideMenu();

        // 3. Eigenes Fenster anzeigen
        OpenMyWindow();
    }
}

// Methode zum Stoppen des Modus
private void StopExclusiveMode()
{
    if (_host == null || !_hasControl) return;
    
    // 1. Eigenes Fenster schließen
    _myExclusiveWindow?.Close();
    _myExclusiveWindow = null;

    // 2. Kontrolle freigeben
    _host.ReleaseExclusiveHotkeyControl(this);
    _hasControl = false;
    _host.Window.ShowNotification("Kontrolle freigegeben!");
}

private void OpenMyWindow()
{
    // CreateStandardWindow für interaktive UI verwenden!
    _myExclusiveWindow = _host.Window.CreateStandardWindow("Mein Panel");
    _myExclusiveWindow.FormClosed += (s, e) => StopExclusiveMode(); // Failsafe!
    // ... fügen Sie hier Ihre Buttons etc. hinzu ...
    _myExclusiveWindow.Show();
}
```
### Schritt 2: Auf den Hotkey reagieren

Implementieren Sie die `OnExclusiveHotkey`-Methode. Sie wird nun vom Core aufgerufen.
```csharp
public void OnExclusiveHotkey()
{
    // Wenn das Fenster existiert, schalte es um. Wenn nicht, erstelle es.
    if (_myExclusiveWindow != null && !_myExclusiveWindow.IsDisposed)
    {
        _myExclusiveWindow.Visible = !_myExclusiveWindow.Visible;
    }
    else
    {
        OpenMyWindow();
    }
}
```
### Schritt 3: Kontrolle freigeben
Siehe `StopExclusiveMode()` oben. Der Aufruf von `_host.ReleaseExclusiveHotkeyControl(this)` ist der entscheidende Teil. Stellen Sie sicher, dass dies geschieht, wenn Ihre Funktion beendet ist (z.B. wenn der Benutzer Ihr Fenster schließt).

### Schritt 4: Beim Herunterfahren aufräumen

Stellen Sie immer sicher, dass Sie die Kontrolle an den Core zurückgeben, wenn Ihr Add-on entladen wird.
```csharp
public void Shutdown()
{
    // Stellen Sie immer sicher, dass die Kontrolle beim Entladen zurückgegeben wird.
    StopExclusiveMode();
}
```
Dieses System ist robust, sicher und gibt Ihnen die volle Kontrolle darüber, wann und wie Ihr Add-on auf den Haupt-Hotkey reagiert.

---

## Kapitel 6: Einstellungs-UIs erstellen: Von einfach bis mächtig

Sie haben zwei Möglichkeiten, eine Einstellungsseite für Ihr Add-on zu erstellen. Wählen Sie die, die Ihren Anforderungen entspricht.

### Methode 1: Das Baukasten-System (Legacy)

Mit `GetSettingsControls()` geben Sie dem Core eine Liste einfacher Bausteine (`AddonControl`, `HotkeyControl`). Der Core stapelt diese dann vertikal für Sie.

*   **Vorteile:** Sehr einfach für grundlegende Bedürfnisse.
*   **Nachteile:** Extrem limitiert. Keine Schieberegler, Textboxen oder benutzerdefinierten Layouts.

```csharp
public IEnumerable<AddonControl> GetSettingsControls()
{
    yield return new HotkeyControl(
        identifier: "myaddon_hotkey_ctrl", 
        label: "Special Action Hotkey", 
        hotkeyIdentifier: "MyAddon_Action1",
        defaultHotkey: "Shift+F1"
    );
}
```
### Methode 2: Volle UI-Freiheit (`UserControl` - Empfohlen)

Mit `GetSettingsControl(IAddonHost host)` erstellen Sie Ihre gesamte Einstellungsseite visuell im Visual Studio Designer und übergeben diese komplette UI an den Core. Dies ist der **moderne und empfohlene** Ansatz.

*   **Vorteile:** Totale kreative Freiheit. Verwenden Sie Schieberegler, Textboxen, Bilder, Dropdowns und ordnen Sie sie nach Belieben an.
*   **Nachteile:** Erfordert etwas mehr Setup.

So geht's:

#### 1. Ihr UserControl erstellen

Klicken Sie in Visual Studio mit der rechten Maustaste auf Ihr Projekt > Hinzufügen > **Benutzersteuerelement (Windows Forms)**. Nennen Sie es `MySettingsPanel.cs`.
Verwenden Sie den visuellen Designer, um Steuerelemente per Drag-and-Drop auf Ihr Panel zu ziehen.

#### 2. Den Code implementieren

Ihre `IAddon`-Klasse gibt nun einfach eine Instanz Ihres neuen Panels zurück:

```csharp
// In Ihrer IAddon-Hauptklasse
public UserControl? GetSettingsControl(IAddonHost host)
{
    // Wir übergeben eine Referenz auf uns selbst (this) an das UI-Panel.
    return new MySettingsPanel(host, this);
}

// Und lassen die alte Methode leer
public IEnumerable<AddonControl> GetSettingsControls() => [];
```
Der Code für Ihre `MySettingsPanel.cs` wendet das Theme des Cores auf Ihre UI an und kann Methoden in Ihrer Haupt-Add-on-Klasse aufrufen:

```csharp
// In Ihrer MySettingsPanel.cs-Datei
using SCOverlay.API;
using System.Windows.Forms;

public partial class MySettingsPanel : UserControl
{
    private readonly IAddonHost _host;
    private readonly MeinAddon _addonInstance; // Eine Referenz zur Haupt-Add-on-Klasse

    public MySettingsPanel(IAddonHost host, MeinAddon addonInstance)
    {
        InitializeComponent(); // Lädt Steuerelemente aus dem Designer
        _host = host;
        _addonInstance = addonInstance;

        // Wenden Sie das Theme auf alle Steuerelemente an
        ApplyThemeToAllControls(this); 

        // Verknüpfen Sie einen Button-Klick mit einer Methode in Ihrem Addon
        meinTestButton.Click += (s, e) => _addonInstance.DoSomethingCool();
    }

    private void ApplyThemeToAllControls(Control parent)
    {
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
            
            if (control.HasChildren)
            {
                ApplyThemeToAllControls(control);
            }
        }
    }
}
```
Dieser Ansatz gibt Ihnen eine professionelle, vollständig benutzerdefinierte Einstellungs-UI, die dennoch perfekt zum Erscheinungsbild von SCOverlay passt.

---

## Kapitel 7: Fortgeschrittene Konzepte & Best Practices

### Lizenzierung für Premium-Add-ons

Möchten Sie Ihr Add-on Unterstützern anbieten? Dies ist ein kollaborativer Prozess.

1.  **Entwickeln Sie Ihr Add-on.**
2.  **Kontaktieren Sie uns:** Wenn es fertig ist, kontaktieren Sie den Ersteller (BlugDeg) über ein GitHub-Issue.
3.  **Integration:** Wir generieren eine einzigartige `LicenseId` für Sie.
4.  **Implementierung:** Sie fügen das Attribut zu Ihrer Add-on-Klasse hinzu.

```csharp
[Addon(LicenseId = "MySuperAddon")]
public class MyPremiumAddon : IAddon { /* ... */ }
```

### Dos & Don'ts: Der Weg zum stabilen Add-on

*   ✅ **Ressourcen freigeben:** Rufen Sie `Dispose()` für alle Fenster oder `UserControls` auf, die Sie erstellen, normalerweise in Ihrer `Shutdown()`-Methode, um Speicherlecks zu vermeiden.
*   ❌ **Blockieren Sie niemals `Draw()`:** Führen Sie keine langen Operationen (wie Dateizugriffe oder Webanfragen) in `Draw` aus. Es wird zu Rucklern führen.
*   ❌ **Gehen Sie nicht von einem UI-Thread aus:** Wenn Sie die Benutzeroberfläche aus einem Hintergrund-Task aktualisieren, verwenden Sie `meinControl.BeginInvoke(...)`.

---

## Kapitel 8: Fehlerbehebung: Häufige Probleme lösen

**"Mein Add-on erscheint nicht im Menü!"**

*   **Falsche Ordnerstruktur:** Der Ordner in `%AppData%\SCOverlay\addons` muss exakt denselben Namen haben wie Ihre DLL-Datei (ohne die `.dll`-Endung).
*   **"Lokale Kopie" ist Wahr:** Der `SCOverlay.API`-Verweis muss "Lokale Kopie" auf "Nein" (False) gesetzt haben.
*   **Fehler beim Start:** Überprüfen Sie die `debug.log` in `%AppData%\SCOverlay\`.

**"Meine UI-Änderung wird nicht angezeigt!"**

*   **Lösung:** Sie müssen `_host?.InvalidateOverlay();` aufrufen, nachdem Sie etwas geändert haben, das visuell aktualisiert werden soll.

**"Mein Add-on verschwindet plötzlich!"**

*   **Ursache:** Der Performance Watchdog oder der Hotkey-Failsafe hat Ihr Add-on ausgeworfen.
*   **Lösung:** Überprüfen Sie die `debug.log` auf `CRITICAL`-Meldungen. Ihr Add-on hat einen schwerwiegenden Fehler verursacht.

---

## Kapitel 9: Werden Sie Teil der Entwicklung!

Ihr Beitrag ist wertvoll. Ihre Ideen und Ihre Hilfe sind immer willkommen.
Erstellen Sie ein Issue auf GitHub, um Hilfe zu erhalten oder Features vorzuschlagen. Wir sind gespannt, was Sie erschaffen werden!
