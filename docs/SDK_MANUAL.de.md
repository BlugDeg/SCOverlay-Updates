<p align="center">
  <strong>Readme:</strong>&nbsp;
  <a href="../README.md"><img src="https://img.shields.io/badge/EN-ff6f00?style=flat-square" alt="English Readme"></a><!--
  --><a href="../README.de.md"><img src="https://img.shields.io/badge/DE-ff6f00?style=flat-square" alt="German Readme"></a>
  &nbsp;&nbsp;|&nbsp;&nbsp;
  <strong>Developer:</strong>&nbsp;
  <a href="SDK_MANUAL.md"><img src="https://img.shields.io/badge/EN-ff6f00?style=flat-square" alt="English Developer Manual"></a><!--
  --><a href="SDK_MANUAL.de.md"><img src="https://img.shields.io/badge/DE-007bff?style=flat-square" alt="German Developer Manual"></a>
</p>

# SCOverlay Addon SDK Handbuch

Willkommen beim SCOverlay Addon SDK! Dieses Dokument ist Ihr umfassender Leitfaden für die Entwicklung von Erweiterungen (Addons) für SCOverlay.

## Kapitel 1: Philosophie & Erste Schritte

### Die Vision hinter der API
Die SCOverlay-Architektur wurde nach drei Kernprinzipien entworfen: **Modularität**, **Stabilität & Performance** und ein **Strikter Vertrag** über die `SCOverlay.API.dll`.

### 1.1. Voraussetzungen & Projekt-Setup
- Visual Studio 2022 mit der ".NET Desktop Development"-Workload.
- .NET 8 SDK oder neuer.
- Die `SCOverlay.API.dll`-Datei.

Erstellen Sie ein **Klassenbibliothek (.NET)**-Projekt, fügen Sie einen Verweis auf die API-DLL hinzu und setzen Sie deren `<Private>false</Private>`-Eigenschaft in der `.csproj`-Datei.

### 1.2. Deployment-Struktur
Nach dem Kompilieren muss Ihr Addon in einer bestimmten Ordnerstruktur platziert werden, damit SCOverlay es findet:
`%AppData%\SCOverlay\addons\**MyFirstAddon**\**MyFirstAddon.dll**`

---

## Kapitel 2: Die `IAddon`-Schnittstelle im Detail

Dies ist der Bauplan für jedes Addon. Ihre Hauptklasse muss diese Schnittstelle implementieren.
*   `Name, Author, Version`: Metadaten für Ihr Addon.
*   `Initialize(IAddonHost host)`: Der Einstiegspunkt Ihres Addons.
*   `GetMainMenuButtons()`: Stellt Buttons für das Hauptmenü des Overlays bereit.
*   `GetSettingsControls()`: Stellt UI-Elemente für die zentrale Einstellungsseite bereit.
*   `Draw(Graphics g, ...)`: Die Zeichen-Engine, die bei jedem Frame aufgerufen wird. Halten Sie sie schnell!
*   `OnOverlayVisibilityChanged(bool isVisible)`: Callback zur Zustandssynchronisation.
*   `Shutdown()`: Aufräummethode. Geben Sie hier alle Ressourcen frei.
*   `GetLocalizations()`: Stellt Übersetzungs-Strings für Ihr Addon bereit.

---

## Kapitel 3: Der `IAddonHost`: Ihre Brücke zum Kern

Die `IAddonHost`-Instanz ist Ihr Tor zur Hauptanwendung und bietet sicheren Zugriff auf gekapselte Kerndienste.

### 3.1. UI & Menü-Steuerung
*   `TakeMenuControl(...)`: Übernimmt die exklusive Kontrolle über das Menü für Untermenüs.
*   `ReleaseMenuControl()`: Gibt die Menükontrolle an den Kern zurück.
*   `InvalidateOverlay()`: Erzwingt ein komplettes Neuzeichnen des Overlays.

### 3.2. Service-Zugriff
*   `_host.Sound.PlayFile(...)`: Spielt einen Sound asynchron ab.
*   `_host.Window.ShowNotification(...)`: Zeigt eine systemweite "Toast"-Benachrichtigung an.
*   `_host.Window.CreateThemedWindow(...)`: Erstellt ein neues, leeres Fenster, das automatisch das aktuelle Theme des Overlays übernimmt.

---

## Kapitel 4: Kommunikationsflüsse: Addon <=> Kern

### 4.1. Addon an Kern (Befehle & Datenbereitstellung)
Ihr Addon befiehlt dem Kern aktiv, eine Aktion auszuführen (`_host.LogInfo(...)`), oder stellt passiv Daten bereit, wenn sie angefordert werden (`GetMainMenuButtons()`).

### 4.2. Kern an Addon (Callbacks & Lebenszyklus)
Der Kern informiert Ihr Addon über Ereignisse durch Lebenszyklus-Methoden (`Initialize`, `Shutdown`) und UI-Events (`Draw`, `OnOverlayVisibilityChanged`).

---

## Kapitel 5: Best Practices & Häufige Fehler

### DOs:
*   ✅ **Immer auf Null prüfen:** Verwenden Sie Null-Conditional-Operatoren: `_host?.LogInfo(...)`.
*   ✅ **Ressourcen freigeben:** Implementieren Sie `IDisposable` für benutzerdefinierte Forms und rufen Sie `Dispose()` in `Shutdown()` auf.
*   ✅ **Events deabonnieren:** Deabonnieren Sie Events wie `_host.OnPaintOverlay` immer in Ihrer `Shutdown()`-Methode.
*   ✅ **`try...finally` für den Performance-Modus verwenden:** Stellen Sie sicher, dass `ReleaseHighPerformanceMode()` immer aufgerufen wird.

### DON'Ts:
*   ❌ **Blockieren Sie niemals `Draw()`:** Vermeiden Sie Datei-I/O oder lange Schleifen in der `Draw`-Methode.
*   ❌ **Vergessen Sie nicht `InvalidateOverlay()`:** Rufen Sie es auf, nachdem Sie einen Zustand geändert haben, der die UI beeinflusst.
*   ❌ **Gehen Sie nicht von einem UI-Thread aus:** Verwenden Sie `meinFenster.BeginInvoke(...)`, um die UI sicher aus einem Nicht-UI-Thread zu aktualisieren.