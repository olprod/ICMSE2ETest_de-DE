---
title: "Spezifikation für die Hardware für Filter für Windows 10, Version 1607"
Description: "In diesem Abschnitt der Dokumentation sind die Spezifikationen für Hardware-Kompatibilität für Filtertreiber auf Windows 10, Version 1607."
ms.assetid: 
MSHAttr: 
author: beneluxboy
ms.openlocfilehash: 4e20698db8c2fa7fa36c47f25859bd21415d51a2
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="hardware-compatibility-specification-for-filter-for-windows-10-version-1607"></a>Spezifikation für die Hardware für Filter für Windows 10, Version 1607

In diesem Abschnitt der Dokumentation sind die Spezifikationen für Hardware-Kompatibilität für Filtertreiber auf Windows 10, Version 1607.

Diese Spezifikationen sind in den Themen und die folgenden Kategorien unterteilt:

- [Filter.Driver.AntiVirus](#filterdriverantivirus)
- [Filter.Driver.DeviceGuard](#filterdriverdeviceguard)
- [Filter.Driver.EarlyLaunchAntiMalware](#filterdriverearlylaunchantimalware)
- [Filter.Driver.FileSystem](#filterdriverfilesystem)
- [Filter.Driver.Fundamentals](#filterdriverfundamentals)
- [Filter.Driver.Network LWF](#filterdrivernetworklwf)
- [Filter.Driver.Security](#filterdriversecurity)
- [Filter.Driver.vSwitchExtension](#filterdrivervswitchextension)
- [Filter.Driver.WindowsFilteringPlatform](#filterdriverwindowsfilteringplatform)

<a name="filterdriverantivirus"></a>
## <a name="filterdriverantivirus"></a>Filter.Driver.AntiVirus 

*Antivirus-Anforderungen für Filtertreiber.*

### <a name="filterdriverantivirusfunctionality"></a>Filter.Driver.AntiVirus.Functionality

*Kernelmodus Filter-Treiber müssen so entworfen werden, um die Zuverlässigkeit zu maximieren und Funktionalität von Windows Datei Systeme als auch die Hauptkomponenten des Betriebssystems genau interagieren.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Kernelmodus Filter-Treiber müssen so entworfen werden, um die Zuverlässigkeit zu maximieren und Funktionalität von Windows Datei Systeme als auch die Hauptkomponenten des Betriebssystems genau interagieren. Einige Bereiche besonders interessant sind: 
 

-   Lokale Dateisysteme
    -   NT-API, Win32-API und Win32 zugeordnet e/a-API-Verwendung
    -   Objekt-ID-Funktionen
    -   Analysepunkte
    -   Oplocks
    -   Systemverwendung cache
    -   Transaktions-Funktion
-   Remotedatei Systeme
-   Oplock Semantik über SMB

Informationen zur Datei Systemverhalten: <http://download.microsoft.com/download/4/3/8/43889780-8d45-4b2e-9d3a-c696a890309f/File%20System%20Behavior%20Overview.pdf>

Informationen zu Oplock Semantik über SMB, finden Sie unter der \[MS SMB2\] Dokument, Protokoll: <http://msdn.microsoft.com/en-us/library/cc246482(PROT.13).aspx>

### <a name="filterdriverantivirusicardetection"></a>Filter.Driver.AntiVirus.IcarDetection

*Virenschutz Filtertreiber müssen so konzipiert werden, dass Übung Grundfunktionen Virenschutz sowie interagieren genau mit der Hauptkomponenten des Betriebssystems.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
            
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Virenschutz Filtertreiber müssen so konzipiert werden, dass Übung Grundfunktionen Virenschutz sowie interagieren genau mit der Hauptkomponenten des Betriebssystems.  Einige Bereiche besonders interessant sind:    

-   Dateisysteme
-   Antivirus-Funktionen

### <a name="filterdriverantivirusminifilter"></a>Filter.Driver.AntiVirus.MiniFilter

*Ein Systemfilter-Treiber muss ein Minifiltertreiber sein, die den Datei Systeme Filter-Manager verwendet.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Diese Anforderung wird implizit getestet werden soll. So, dass legacy Dateisystem Filter-Treiber nicht aufgelistet werden, werden der Treiber Erkennungsmechanismus für das Windows Hardware Lab Kit geschrieben. Nur Minifilter Treiber werden aufgezählt und im Kit verfügbar gemacht werden. Ein Benutzer wird als solche nicht auswählen einen legacy-Filter-Treiber für Logo-Test über das Kit sein.

Informationen zu filtern-Manager und Minifilter Treiber hier: <http://msdn.microsoft.com/en-us/library/ff540402(v=VS.85).aspx>
<http://msdn.microsoft.com/en-us/windows/hardware/gg462968.aspx>

### <a name="filterdriverantivirusnamedpipeandmailslots"></a>Filter.Driver.AntiVirus.NamedPipeAndMailSlots

*Kernelmodus-Filtertreiber müssen so konzipiert werden, dass Maximieren der Zuverlässigkeit und Funktionalität von Named Pipes und Mail Slots als auch die Hauptkomponenten des Betriebssystems genau interagieren.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Kernelmodus Filter-Treiber müssen so konzipiert werden, dass Maximieren der Zuverlässigkeit und Funktionalität von Named Pipes und Mail Slots als auch die Hauptkomponenten des Betriebssystems genau interagieren.  Einige Bereiche besonders interessant sind: 

-   Benannte Pipe-Dateisystem

    -   Funktionen und Stress für allgemeine-APIs

    -   Anonyme pipes

    -   Pipe Modi

    -   Open-Modi

    -   Ungültige Pipe Namen

    -   Das leeren pipe

    -   Max Pipe-Instanz

    -   Pipe Richtung (in/Out/Duplex)

    -   Ein- und Ausgabe Puffergrößen

    -   Verschiedene rufen Semantik, wie das Wiederherstellen der Verbindung für einer Pipe an, die auf der Serverseite getrennt wurde.

    -   Verhalten Überprüfung aller named Pipes Vorgänge für die einzelnen unterschiedliche Zustände einer Pipe-Instanz.

    -   Leistung für named Pipes Erstellung und Verbindung.

    -   Durchsatz bei unterschiedlichen eingehend/ausgehend Puffergrößen und die Anzahl der Clients. 

    -   Skalierbarkeit von sich eine Erhöhung der Anzahl von Clients, Zeitaufwand für die Verbindung mit einer Instanz von named Pipes

-   Mail-Steckplatz Dateisystem

-   Funktionen und Stress für allgemeine-APIs

Informationen zu Named Pipes und Mail Slots finden Sie unter: <http://msdn.microsoft.com/en-us/library/aa365574(v=VS.85).aspx>

### <a name="filterdriverantivirusregistryandprocess"></a>Filter.Driver.AntiVirus.RegistryAndProcess

*Kernelmodus-Filtertreiber müssen so entworfen werden, um zu maximieren der Zuverlässigkeit und Funktionalität der Windows-Registrierung und Prozesse sowie die Hauptkomponenten des Betriebssystems genau interagieren.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Kernelmodus-Filtertreiber müssen so entworfen werden, um zu maximieren der Zuverlässigkeit und Funktionalität der Windows-Registrierung und Prozesse sowie die Hauptkomponenten des Betriebssystems genau interagieren.  Einige Bereiche besonders interessant sind:      

-   Registrierung

    -   NT-API und Win32-API-Verwendung

    -   Wichtige Funktionen

    -   Registrierung von Transaktionen

    -   Symbolische Verbindung Verhalten

-   Prozessfarben

    -   Allgemeines Modul management

    -   Racebedingungen bei Beendigung Thread-Prozess

    -   Process Management Callback-Funktion

-   Thread und Prozess auf Vorgänge

### <a name="filterdriverantiviruswinsock"></a>Filter.Driver.AntiVirus.Winsock

*Kernelmodus Filter-Treiber müssen so konzipiert werden, dass Maximieren der Zuverlässigkeit und Funktionalität von Windows Sockets als auch die Hauptkomponenten des Betriebssystems genau interagieren.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Kernelmodus-Filtertreiber müssen so entworfen werden, um Maximieren der Zuverlässigkeit und Funktionalität von Windows-Sockets als auch die Hauptkomponenten des Betriebssystems genau interagieren.  Einige Bereiche besonders interessant sind:   

-   Winsock

-   Winsock-API-Funktionen

Informationen zu Winsock-APIs finden Sie unter: <http://msdn.microsoft.com/en-us/library/ms740673(VS.85).aspx>

<a name="filterdriverdeviceguard"></a>
## <a name="filterdriverdeviceguard"></a>Filter.Driver.DeviceGuard 

*Alle Kernel-Treiber müssen erstellt werden, um mit [Gerät Guard](http://blogs.msdn.com/b/windows_hardware_certification/archive/2015/05/22/driver-compatibility-with-device-guard-in-windows-10.aspx)kompatibel sein.*

### <a name="filterdriverdeviceguarddrivercompatibility"></a>Filter.Driver.DeviceGuard.DriverCompatibility

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Windows 10 hat ein Feature namens [*Guard Gerät*](http://blogs.windows.com/business/2015/04/21/windows-10-security-innovations-at-rsa-device-guard-windows-hello-and-microsoft-passport/) , die Organisationen bietet die Möglichkeit zum Sperren von Geräten in eine Möglichkeit, die erweiterte Malwareschutz vor Schadsoftware neue und unbekannte Varianten bietet sowie erweiterte Persistent Bedrohungen (APTs). Gerät Guard können Hardware-Technologie und Virtualisierung Sie um die Funktion der Code Integrität (CI) Entscheidung vom Rest des Windows-Betriebssystems zu isolieren. Bei der Virtualisierung basierende Sicherheit verwenden, um die Integrität des Codes zu isolieren, ist die einzige Möglichkeit, den Kernel-Speicher ausführbare werden kann durch eine Überprüfung der Integrität des Codes. Dies bedeutet, dass Seiten im Kernelmodus Arbeitsspeicher können nie Schreibzugriff und ausführbare Datei (W + X) und ausführbarer Code kann nicht direkt geändert werden.

Details stehen auf der Windows-Hardware Zertifizierung Blog: [Kompatibilität mit Gerät Guard in Windows 10](http://aka.ms/DeviceGuard).

Die folgenden Attribute müssen auf die Datei Sys festgelegt werden.
<table>
<tr><th>Name des Attributs</th><th>Beschreibung</th></tr>
<tr><td>CompanyName</td><td>Name des Unternehmens</td></tr>
<tr><td>FileDescription</td><td>Datei-Produkt Beschreibung des Treibers</td></tr>
<tr><td>Den Eintrag OriginalFilename</td><td>Ursprünglicher Dateiname</td></tr>
<tr><td>ProductName</td><td></td></tr>
<tr><td>VS\_FIXEDFILEINFO:</td><td></td></tr>
<tr><td>&nbsp;&nbsp;&nbsp;"Filever"</td><td>Versionsnummer der Datei</td></tr>
<tr><td>&nbsp;&nbsp;&nbsp;"Filever"</td><td>Versionsnummer des Produkts</td></tr>
</table>

Weitere Informationen finden Sie auf der folgenden MSDN-Seite:

-   <https://msdn.Microsoft.com/en-us/library/Windows/Desktop/aa381058 (v=vs.85).aspx>

Alle Kernel-Treiber auf Windows MÜSSEN signiert werden von Microsoft (WHQL-Zertifikat) über das SysDev Dashboard.

<a name="filterdriverearlylaunchantimalware"></a>
## <a name="filterdriverearlylaunchantimalware"></a>Filter.Driver.EarlyLaunchAntiMalware 

*Dieser Abschnitt beschreibt die Anforderungen für frühe Launch-Treiber.*

### <a name="filterdriverearlylaunchantimalwarebackupdriver"></a>Filter.Driver.EarlyLaunchAntiMalware.BackupDriver

*Frühe Einführung Antischadsoftware-Treiber müssen eine Sicherungskopie im Falle einer Beschädigung enthalten.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Der Treiber Anti-Malware (Uhr) ist entscheidend für den Erfolg beim Starten des Computers.  Wenn der Treiber beschädigt wird, kann der Start nicht erfolgreich.  Um die beste benutzerumgebung zu ermöglichen, ist es erforderlich, dass bei der Installation des Treibers Uhr auch eine Kopie im Speicher backup Treiber installiert.  Dadurch einer reibungslose Remediation Erfahrung im Fall der primäre Treiber beschädigt.

Der Speicherort für die Sicherung ELAM von Windows definiert ist, und in der Registrierung gespeichert: HKEY\_LOKALE\_COMPUTER\\SYSTEM\\CurrentControlSet\\Steuerelement\\EarlyLaunch! BackupPath

*Design Notes:* Die frühe Einführung Anti-Malware (Uhr) Treiber gestartet wurden, sofort nach der NTOS Kernel beginnt.  Für jede nachfolgende Boot-Treiber erhält der Treiber Uhr einen Rückruf von der Plug & Play-Manager, um zu bestimmen, ob der Treiber Boot initialisiert werden soll.  Uhr Treiber wertet den Boot-Treiber und muss gut, fehlerhafte oder unbekannte zurückgeben.  Basierend auf der zurückgegebenen Klassifikation und definiert die Richtlinie, der Plug & Play-Manager entscheidet, ob den Boot-Treiber nicht initialisiert werden.

### <a name="filterdriverearlylaunchantimalwareelamsignatureattributes"></a>Filter.Driver.EarlyLaunchAntiMalware.ELAMSignatureAttributes

*Anforderung für den Abschnitt SignatureAttribute in der ELAM INF-Dateien.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

ELAM Dateien müssen mit einer speziellen Signatur im Rahmen des Prozesses zum Absenden angemeldet sein. Den Prozess beim bestimmen, welche Signatur jedes Modul muss standardisiert ist; Jede INF-Datei muss jetzt einen Abschnitt SignatureAttributes enthalten, der welche Art von Signatur für die zugeordnete Treiber Binärdateien anwendbar ist die eindeutig identifiziert. Hinzufügen von vorhandenen INF-Dateien in diesem Abschnitt wird ein sehr einfacher Vorgang.

Ein Beispiel:
```
\[SignatureAttributes\]
ELAMFILE.dll = SignatureAttributes.Elam
\[SignatureAttributes.Elam\]
Elam=true
```

### <a name="filterdriverearlylaunchantimalwaremvimembership"></a>Filter.Driver.EarlyLaunchAntiMalware.MVIMembership

*Frühe Einführung Antischadsoftware-Treiber können nur von Mitgliedern MVI erstellt werden.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Jeder frühe Einführung Anti-Malware (Uhr) Treiber kann nur von Membern von Microsoft Virus Initiative (MVI) erstellt werden.

 *Design Notes:* Die frühe Einführung Uhr Treiber gestartet wurden, sofort nach NTOS Kernel gestartet wird.  Für jede nachfolgende Boot-Treiber erhält der Treiber Uhr einen Rückruf von der Plug & Play-Manager, um festzustellen, ob der Treiber Boot initialisiert werden soll.  Uhr Treiber wertet den Boot-Treiber und muss gut, fehlerhafte oder unbekannte zurückgeben.  Basierend auf der zurückgegebenen Klassifikation und definiert die Richtlinie, der Plug & Play-Manager entscheidet, ob den Boot-Treiber nicht initialisiert werden.

### <a name="filterdriverearlylaunchantimalwareperformance"></a>Filter.Driver.EarlyLaunchAntiMalware.Performance

*Frühe Einführung Antischadsoftware-Treiber müssen leistungsfähige sein.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Rückruf Latenz: Der Treiber Anti-Malware (Uhr) ist erforderlich, um ein Ergebnis für jeden Rückruf in 0,5 ms den Rückruf entgegennehmen.

Zuweisung von virtuellem Speicher: Uhr-Treiber, einschließlich sowohl das Treiber-Image als auch die Konfigurationsdaten (Signatur) ist erforderlich, um eine begrenzte Speicherbedarf von 256 KB haben oder weniger.

Unload-Blockierung: Jede Uhr Treiber synchronen empfängt einen Rückruf nach der letzte Boot-Treiber zurück, der angibt, dass der Treiber Uhr entladen initialisiert wurde. Zu diesem Zeitpunkt muss der Treiber Uhr nach oben und speichern alle persistent Statusinformationen bereinigen. Dies muss innerhalb 0,5 ms, gemessen ab dem Zeitpunkt bei der Kernel den Rückruf an den Treiber die Zeit Probleme, die der Treiber Uhr des Rückrufs auftritt.

*Design Notes:* Die frühe Einführung Uhr Treiber gestartet wurden, sofort nach der NTOS Kernel beginnt.  Für jede nachfolgende Boot-Treiber erhält der Treiber Uhr einen Rückruf von der Plug & Play-Manager, um zu bestimmen, ob der Treiber Boot initialisiert werden soll.  Uhr Treiber wertet den Boot-Treiber und muss gut, fehlerhafte oder unbekannte zurückgeben.  Basierend auf der zurückgegebenen Klassifikation und definiert die Richtlinie, der Plug & Play-Manager entscheidet, ob den Boot-Treiber nicht initialisiert werden. 

### <a name="filterdriverearlylaunchantimalwaresignaturedata"></a>Filter.Driver.EarlyLaunchAntiMalware.SignatureData

*Frühe Einführung Antischadsoftware-Treiber dürfen nur in der Microsoft-spezifischen Speicherort gespeicherte Signaturdaten verwenden.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Der Treiber Uhr muss seine Malware Signaturdaten aus einem bekannten Ort und keine anderen abrufen.  Die Signaturdaten sind in der Registrierung in eine neue ELAM-Struktur unter HKLM gespeichert werden, die Winload geladen wird, und wird daher an den Treiber Uhr vor dem Initialisieren Dateisystem verfügbar sein.   Jede Uhr Treiber müssen einen eindeutigen Schlüssel in der ihre Signatur Blob gespeichert.   Der Registrierungspfad und Schlüssel muss des Formats HKLM\\ELAM\\<*Herstellername*>\\wird: Binary <*Blob*> =.

*Design Notes:* Die frühe Einführung Anti-Malware (Uhr) Treiber gestartet wurden, sofort nach der NTOS Kernel beginnt.  Für jede nachfolgende Boot-Treiber erhält der Treiber Uhr einen Rückruf von der Plug & Play-Manager, um zu bestimmen, ob der Treiber Boot initialisiert werden soll.  Uhr Treiber wertet den Boot-Treiber und muss gut, fehlerhafte oder unbekannte zurückgeben.  Basierend auf der zurückgegebenen Klassifikation und definiert die Richtlinie, der Plug & Play-Manager entscheidet, ob den Boot-Treiber nicht initialisiert werden.

<a name="filterdriverfilesystem"></a>
## <a name="filterdriverfilesystem"></a>Filter.Driver.FileSystem 

### <a name="filterdriverfilesystemfunctionality"></a>Filter.Driver.FileSystem.Functionality

*Müssen Kernelmodus-Filtertreiber so konzipiert, um die Zuverlässigkeit zu maximieren und Funktionalität von Windows Datei Systeme als auch die Hauptkomponenten des Betriebssystems genau interagieren.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Kernelmodus Filter-Treiber müssen so konzipiert werden, um die Zuverlässigkeit zu maximieren und Funktionalität von Windows Datei Systeme als auch die Hauptkomponenten des Betriebssystems genau interagieren. Einige Bereiche besonders interessant sind:   

-   Lokale Dateisysteme

    -   NT-API, Win32-API und Win32 zugeordnet e/a-API-Verwendung

    -   Objekt-ID-Funktionen

    -   Analysepunkte

    -   Oplocks

    -   Systemverwendung cache

    -   Transaktionale-Funktion

-   Remotedatei Systeme

-   Oplock Semantik über SMB

Informationen zur Datei Systemverhalten: <http://download.microsoft.com/download/4/3/8/43889780-8d45-4b2e-9d3a-c696a890309f/File%20System%20Behavior%20Overview.pdf>

Informationen zu Oplock Semantik über SMB, finden Sie die \[MS-SMB2\] Dokument, Protokoll: <http://msdn.microsoft.com/en-us/library/cc246482(PROT.13).aspx>

### <a name="filterdriverfilesystemminifilter"></a>Filter.Driver.FileSystem.MiniFilter

*Ein Systemfilter-Treiber muss ein Minifiltertreiber mit dem Dateisystem Filter-Manager.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Diese Anforderung wird implizit getestet werden soll. Gatherer wird geschrieben werden, sodass es aufgezählt und nur Minifilter Treiber für Windows Hardware Zertifizierung Kit (WHCK Flächen). Daher wird ein Benutzer wählen Sie einen legacy-Filter-Treiber für das Testen der Zertifizierung möglich.

Informationen zum Filter-Manager und Minifilter Treiber verfügbar hier: <http://msdn.microsoft.com/en-us/library/ff540402(v=VS.85).aspx>

### <a name="filterdriverfilesystemnamedpipeandmailslots"></a>Filter.Driver.FileSystem.NamedPipeAndMailSlots

*Kernelmodus-Filtertreiber müssen so konzipiert werden, dass Maximieren der Zuverlässigkeit und Funktionalität von Named Pipes und Mail Slots als auch die Hauptkomponenten des Betriebssystems genau interagieren.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Kernelmodus Filter-Treiber müssen so konzipiert werden, dass Maximieren der Zuverlässigkeit und Funktionalität von Named Pipes und Mail Slots als auch die Hauptkomponenten des Betriebssystems genau interagieren.  Einige Bereiche besonders interessant sind:  

-   Benannte Pipe-Dateisystem

    -   Funktionen und Stress für allgemeine-APIs

    -   Anonyme pipes

    -   Pipe-Modi

    -   Open-Modi

    -   Ungültige senkrechten Namen

    -   Das leeren pipe

    -   Max Pipe-Instanz

    -   Senkrechten Richtung (in/Out/Duplex)

    -   Ein- und Ausgabe Puffergrößen

    -   Rufen Sie verschiedene Semantik, wie das Wiederherstellen der Verbindung für einer Pipe an, die auf der Serverseite getrennt wurde.

    -   Verhalten Überprüfung aller named Pipes Vorgänge für jeden distinct Zustand eine Pipeinstanz.

    -   Leistung für named Pipes Erstellung und Verbindung.

    -   Durchsatz bei unterschiedlichen eingehend/ausgehend Puffergrößen und die Anzahl der Clients. 

    -   Skalierbarkeit von sich eine Erhöhung der Anzahl von Clients, Zeitaufwand für die Verbindung mit einer Instanz von named Pipes

-   Mail-Steckplatz Dateisystem

-   Funktionen und Stress für allgemeine-APIs

Informationen zu Named Pipes und Mail Slots finden Sie unter: <http://msdn.microsoft.com/en-us/library/aa365574(v=VS.85).aspx>

### <a name="filterdriverfilesystemregistryandprocess"></a>Filter.Driver.FileSystem.RegistryAndProcess

*Kernelmodus-Filtertreiber müssen so entworfen werden, um zu maximieren der Zuverlässigkeit und Funktionalität der Windows-Registrierung und Prozesse sowie die Hauptkomponenten des Betriebssystems genau interagieren.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Kernelmodus Filter-Treiber müssen so entworfen werden, um zu maximieren der Zuverlässigkeit und Funktionalität der Windows-Registrierung und Prozesse sowie die Hauptkomponenten des Betriebssystems genau interagieren.  Einige Bereiche besonders interessant sind:      

-   Registrierung

    -   NT-API und Win32 API-Verwendung

    -   Wichtige Funktionen

    -   Registrierung von Transaktionen

    -   Symbolische Verbindung Verhalten

-   Prozessfarben

    -   Allgemeines Modul management

    -   Racebedingungen bei Beendigung Thread-Prozess

    -   Process Management Callback-Funktion

-   Thread und Prozess Handle-Vorgänge


## <a name="filterdriverfundamentals"></a>Filter.Driver.Fundamentals 

*Entspricht für Device-Treiber Grundlagen, aber für Filtertreiber.*

### <a name="filterdriverfundamentalsdriverquality"></a>Filter.Driver.Fundamentals.DriverQuality

*Ein Filtertreiber muss von hoher Qualität.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Treiberkomponenten müssen nicht das System zum Absturz oder Verlust Ressourcen verursachen. Diese Ressourcen enthalten, sind jedoch nicht auf die folgenden beschränkt:  

-   Arbeitsspeicher

-   Graphics Device Interface (GDI) oder User-Objekte

-   Kernelobjekte wie Dateien, Mutex, Semaphore und Gerät handles

-   Kritische Abschnitte

-   Speicherplatz

-   Printer-handles

*Hinweise zum Entwurf*:

Dem Standbymodus & PNP bei e/a vor und nach dem Test - Zyklen Test das System über alle dem Standbymodus Status meldet und grundlegende PNP auf allen Geräten auf dem System wird.

Bei diesem Test werden mit Treiber Verifier mit den Standardeinstellungen aktiviert ausgeführt.

<a name="filterdrivernetworklwf"></a>
## <a name="filterdrivernetworklwf"></a>Filter.Driver.Network.LWF 

*LAN-Anforderungen.*

### <a name="filterdrivernetworklwfbase"></a>Filter.Driver.Network.LWF.Base

*Alle vorläufiger Filter müssen NDIS 6.30 oder höher sein.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Alle vorläufiger Filter müssen NDIS 6.30 oder höher und der NDIS-Spezifikation auf MSDN kompatibel sein.

### <a name="filterdrivernetworklwfmtusize"></a>Filter.Driver.Network.LWF.MTUSize

*Alle vorläufiger Filter muss beliebige Pakete akzeptieren der Miniport MTU größer sein kann.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Alle vorläufiger Filter müssen NDIS 6.30 oder höher sein. Alle vorläufiger Filter muss beliebige Pakete akzeptieren der Miniport MTU größer sein kann.


## <a name="filterdriversecurity"></a>Filter.Driver.Security 

*Zusätzliche Anforderungen in Bezug auf die Sicherheit für TDI-Filter Faktoren und LSPs.*

### <a name="filterdriversecuritynotdifilterandlsp"></a>Filter.Driver.Security.NoTDIFilterAndLSP

*Keine Filter TDI oder LSPs werden während der Installation oder Verwendung durch den Treiber oder zugeordneten Softwarepakete installiert.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Keine Verwendung von TDI-filtern oder LSPs durch Kernel-Modus Software oder Treiber oder Benutzersoftware Modus oder Treiber können vorhanden sein.

<a name="filterdrivervswitchextension"></a>
## <a name="filterdrivervswitchextension"></a>Filter.Driver.vSwitchExtension 

### <a name="filterdrivervswitchextensionextensionrequirements"></a>Filter.Driver.vSwitchExtension.ExtensionRequirements

*Filtertreiber, die VM Switch Erweiterbarkeit implementieren müssen erforderlichen Funktionen, Modi und Protokolle unterstützen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Filtertreiber, die VM Switch Erweiterbarkeit implementieren müssen erforderlichen Funktionen, Modi und Protokolle unterstützen.

Anforderungen

-   Eine Erweiterung muss die Anforderungen an das Logo NDIS Filter übergeben.

    -   Eine gültige INF-Datei muss die Erweiterung aufweisen.

    -   Eine Erweiterung muss nur NDIS WDF oder WDM Anrufe tätigen; alle Anrufe an andere Kernel-Modus-Komponenten sind nicht zulässig.

-   Eine Erweiterung muss Hyper-V Live Migration unterstützen.

    -   Nicht bei Seitenumbruch LM, speichern und wiederherstellen, Export/Import

    -   Nicht gespeicherte Daten aus einer anderen Erweiterung blockieren

    -   Andere Interaktionen Erweiterung nicht blockieren

-   Alle Datenverkehr über einen virtuellen Switch benötigen, die von einer VM, einem Host VNIC, externen Netzwerkkarte oder Erweiterung nicht Kopfzeilen geändert von Erweiterungen.   Ausnahmen von dieser Anforderung gehören:

    -   Umleiten von Datenverkehr an eine Netzwerkeinheit

    -   Veränderlichen IP-Header-Felder (gemäß RFC 4302 Abschnitt 3.3.3.1.1.1 für IPv4 und IPv6 Abschnitt 3.3.3.1.2.1)

-   Erweiterung aufgehoben muss Konnektivität zwischen dem Host und dem externen Netzwerk nicht unterbrochen.

-   Erweiterung Capture muss Konnektivität zwischen vSwitch Ports nicht aufheben.

-   Eine Erweiterung muss die folgende Konfiguration OIDs Switch/Port/NIC des Stapels einer Erweiterung übergeben:

    -   OID\_SWITCH\_PARAMETER

    -   OID\_SWITCH\_PORT\_ARRAY

    -   OID\_SWITCH\_PORT\_BEENDIGUNG

    -   OID\_SWITCH\_PORT\_LÖSCHEN

    -   OID\_SWITCH\_NIC\_ARRAY

    -   OID\_SWITCH\_NIC\_VERBINDEN

    -   OID\_SWITCH\_NIC\_TRENNEN

    -   OID\_SWITCH\_NIC\_LÖSCHEN

    -   OID\_SWITCH\_NIC\_ANFORDERN

-   Eine Erweiterung muss den folgenden Richtlinie/Status OIDs übergeben, der es keine des Stapels belegt ist:

    -   OID\_SWITCH\_PORT\_EIGENSCHAFT\_HINZUFÜGEN

    -   OID\_SWITCH\_PORT\_EIGENSCHAFT\_UPDATE

    -   OID\_SWITCH\_PORT\_EIGENSCHAFT\_LÖSCHEN

    -   OID\_SWITCH\_EIGENSCHAFT\_HINZUFÜGEN

    -   OID\_SWITCH\_EIGENSCHAFT\_UPDATE

    -   OID\_SWITCH\_EIGENSCHAFT\_LÖSCHEN

    -   OID\_SWITCH\_PORT\_FEATURE\_STATUS\_ABFRAGE

    -   OID\_SWITCH\_FEATURE\_STATUS\_ABFRAGE

-   Eine Erweiterung muss die folgenden Richtlinien-OIDs des Stapels übergeben:

    -   OID\_SWITCH\_PORT\_EIGENSCHAFT\_ENUM

    -   OID\_SWITCH\_EIGENSCHAFT\_ENUM

-   Eine Erweiterung muss die folgenden oben im Stapel übergeben:

    -   NDIS\_SWITCH\_NIC\_STATUS\_ANGABE

-   Erweiterung "Capture" darf keinen der folgenden Funktionen aufrufen:

*Design Notes:* Finden Sie in der Spezifikation VM Switch Erweiterbarkeit.

<a name="filterdriverwindowsfilteringplatform"></a>
## <a name="filterdriverwindowsfilteringplatform"></a>Filter.Driver.WindowsFilteringPlatform 

### <a name="filterdriverwindowsfilteringplatformarchitecturaldesignappcontainerssupportmodernapplications"></a>Filter.Driver.WindowsFilteringPlatform.ArchitecturalDesign.AppContainers.SupportModernApplications

*WFP basierenden Produkte müssen nicht blockieren Sie den App-Containers-apps, die Betrieb innerhalb ihrer Absicht deklarierte Netzwerk standardmäßig und sollte nur Block App-Containers apps bei bestimmten Benutzeradministrator Absicht oder das System gegen eine spezifische Bedrohung zu schützen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

WFP basierenden Produkte müssen nicht blockieren App-Containers-apps, die Betrieb innerhalb ihrer Absicht deklarierte Netzwerk standardmäßig und sollten nur *App-Containers apps blockieren* , wenn bestimmte Benutzeradministrator Absicht folgen oder das System gegen eine spezifische Bedrohung zu schützen.

### <a name="filterdriverwindowsfilteringplatformarchitecturaldesigncleanuninstall"></a>Filter.Driver.WindowsFilteringPlatform.ArchitecturalDesign.CleanUninstall

*WFP basierenden Produkte müssen ordnungsgemäß beenden und bereinigen Sie alle Ausführungsstatus auf Deinstallieren.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Dadurch wird sichergestellt, dass Hostfirewalls nicht verlassen, führen Sie nicht verwendete Objekte nach deinstallieren, wodurch potenziell diagnostic Probleme verursacht, wenn eine andere separaten Hostfirewall auf dem gleichen Computer installiert ist. Die folgenden WFP Objekte bereinigt werden müssen: Anbieter, ProviderContext, Filter, Unterebene oder Legende.
Darüber hinaus müssen zusätzliche Installationsanforderungen für Anwendungen (über das Logo Softwareprogramm) erfüllt sein.

*Hinweise zum Entwurf*:

Anwendungen können entweder eine MSI-DATEI oder ein anderes Installationsprogramm, das dieser Anforderung, um sicherzustellen, dass eine Erfahrung Standardkontingente Installieren/Deinstallieren auf eine Windows® PC-basierte erfüllt.
Die Installationsanforderungen für Anwendungen (in der Software Logoprogramm) befinden sich in den folgenden Link: <http://www.microsoft.com/downloads/details.aspx?FamilyID=27028822-B172-4CEC-91A3-26B610A4DA79&displaylang=en>
 

### <a name="filterdriverwindowsfilteringplatformarchitecturaldesignconnectionproxyingnodeadlocks"></a>Filter.Driver.WindowsFilteringPlatform.ArchitecturalDesign.ConnectionProxying.NoDeadlocks

*WFP-basierte Produkte, umleiten oder des Proxys auf umleiten Ebenen (Verbinden umleiten), müssen verwenden der neuen Proxyvorgänge API, damit andere Produkte WFP-basierte können bestimmen, dass die Verbindung hierarchiepostfach weitergegeben wurde.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

WFP basierenden Produkte, welche umleiten oder der Proxy an Ebenen (Verbinden umleiten) umleiten, müssen die neue proxy'ing API verwenden, sodass andere WFP basierenden Produkte ermittelt wird, dass die Verbindung proxy'ed wurde.
 

### <a name="filterdriverwindowsfilteringplatformarchitecturaldesignfwpmfiltersmaintainoneterminating"></a>Filter.Driver.WindowsFilteringPlatform.ArchitecturalDesign.FwpmFilters.MaintainOneTerminating

*WFP basierenden Produkte erstellen und verwalten Sie mindestens einen Abbruch FWPM müssen\_FILTER-Objekt.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Ein Abbruch Filter ist eine, die eine Genehmigung gibt / Entscheidung zu blockieren. Es ist möglicherweise als statische Filter oder in einem Popup vorhanden. Die Absicht hinter dieser Anforderung wird sichergestellt, dass Premium Hostfirewalls führen Sie mindestens eine zulassen oder Entscheidung blockieren und nicht einfach Filter nur aus Gründen Prüfung beibehalten, während die grundlegende Hostfirewalls über WFP oder auf andere Weise wie TDI-NDIS und WinSock LSP Filter dazu berechtigt ist.

*Design Notes:* Die Definition für die FWPM\_FILTER-Objekt finden Sie in der folgenden URL: <http://go.microsoft.com/fwlink/?LinkID=116902&clcid=0x409>

### <a name="filterdriverwindowsfilteringplatformarchitecturaldesignfwpmprovidersassociatewithobjects"></a>Filter.Driver.WindowsFilteringPlatform.ArchitecturalDesign.FwpmProviders.AssociateWithObjects

*WFP basierenden Produkte müssen alle ihre Anbieter Kontext, Filter, Unterebenen und Legenden mit ihren entsprechenden identifizierende Anbieterobjekt zuordnen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Beispiele, die veranschaulichen, das Code-Verhalten erwartet für verschiedene Arten von Objekten finden Sie unter: der Name & Produkt des Unternehmens in einem identifizierende Anbieterobjekt zu verweisen:
```
const PWSTR pCompanyName = L"Microsoft Corporation";
const PWSTR pProductName = L"Windows Firewall";
FWPM\_PROVIDER0 myProvider;
myProvider.displayData.name = pCompanyName;
myProvider.displayData.description = pProductName; 
```
Initialisieren Sie das Anbieterobjekt:
```
FWPM\_PROVIDER\_CONTEXT0 myProviderContext;
FWPM\_PROVIDER0 myProvider;
myProviderContext.providerKey = &(myProvider.providerKey);
```
Initialisieren Sie das Unterebene Objekt und verknüpfen Sie ihn auf Ihrem jeweiligen Anbieterobjekt:
```
FWPM\_SUBLAYER0 mySubLayer;
FWPM\_PROVIDER0 myProvider;
mySubLayer.providerKey = &(myProvider.providerKey); 
```
Initialisieren Sie das Popup-Objekt und verknüpfen Sie ihn auf Ihrem jeweiligen Anbieterobjekt:
```
FWPM\_CALLOUT0 myCallout;
FWPM\_PROVIDER0 myProvider;
myCallout.providerKey = &(myProvider.providerKey); 
```
Initialisieren Sie das Filterobjekt und verknüpfen Sie ihn auf Ihrem jeweiligen Anbieterobjekt:
```
FWPM\_FILTER0 myFilter;
FWPM\_PROVIDER0 myProvider;
myFilter.providerKey = &(myProvider.providerKey);
```
 

### <a name="filterdriverwindowsfilteringplatformarchitecturaldesignfwpmprovidersmaintainidentifying"></a>Filter.Driver.WindowsFilteringPlatform.ArchitecturalDesign.FwpmProviders.MaintainIdentifying

*WFP basierenden Produkte erstellen und Verwalten von mindestens eine identifizierende FWPM müssen\_ANBIETER Provider-Objekt.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Ein identifizierende Anbieter Objekt *müssen* Verweisen im Namen & Produkt des Unternehmens wie im folgenden Beispiel dargestellt.  
FWPM\_PROVIDER0

1.  Alle Anbieter müssen erstellen und Verwalten von mindestens 1 Anbieter.

2.  Die provider.displayData.Name muss der Name des Unternehmens enthalten.

3.  Die provider.displayData.Description muss der Name des Produkts enthalten.

Alle Objekte erstellt und im Besitz des Herstellers müssen nur ihren Anbieter zu verweisen:
```
const PWSTR pCompanyName = L"Microsoft Corporation";
const PWSTR pProductName = L"Windows Firewall";
FWPM\_PROVIDER0 myProvider;
 
myProvider.displayData.name = pCompanyName;
myProvider.displayData.description = pProductName;
```

*Design Notes:* Die Definition der FWPM\_PROVIDER-Objekts finden Sie in der folgenden URL: <http://go.microsoft.com/fwlink/?LinkID=116844&clcid=0x409>
 

### <a name="filterdriverwindowsfilteringplatformarchitecturaldesignfwpmsublayersuseownorbuiltin"></a>Filter.Driver.WindowsFilteringPlatform.ArchitecturalDesign.FwpmSublayers.UseOwnOrBuiltIn

*WFP basierenden Produkte müssen nur ihre eigenen Unterebene verwenden oder eine der integrierten Unterfolien.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Eine Host des Firewall Unterebene kann verwendet werden, um sicherzustellen, dass seine Filter durch eine höhere Gewichtung Filter aus einer anderen Hostfirewall nicht umgangen werden müssen. Darüber hinaus muss eine Hostfirewall zu einem anderen Hostfirewall gehören Filter nicht überschreiben.

*Design Notes:* Die Definition für die FWPM\_SUBLAYERobject finden Sie in der folgenden URL: <http://go.microsoft.com/fwlink/?LinkID=116845&clcid=0x409>
 

### <a name="filterdriverwindowsfilteringplatformarchitecturaldesignnetworkdiagnosticsframeworkhelperclass"></a>Filter.Driver.WindowsFilteringPlatform.ArchitecturalDesign.NetworkDiagnosticsFramework.HelperClass

*WFP basierenden Produkte müssen eine Hilfsklasse Netzwerk Diagnose Framework (NDF) enthalten, die die Filterungsplattform Hilfsklasse (FPHC) erweitert.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Windows-Filterung Plattform (WFP) enthält Hilfsklasse Netzwerk Diagnose Framework (NDF) aufgerufen, die Filterungsplattform Hilfsklasse (FPHC). FPHC unterstützt Sie dabei, identifizieren Sie die Ursachen von Konnektivitätsproblemen durch WFP verursacht. Eine Hostfirewall kann eigene NDF Hilfsklasse aufrufen. Erweiterbarkeit der FPHC ermöglicht diese Drittanbieter-Hilfsklassen während der Diagnose aufgerufen werden.

FPHC kann WFP als die Ursache für ein Problem zu identifizieren. Falls verfügbar, kann FPHC auch den Anbieter identifizieren, die der Filter erstellt, der den Netzwerkverkehr blockiert. FPHC übergibt diese Informationen an NDF, die wiederum klicken Sie dann dem Benutzer benachrichtigen kann, dass WFP das Verbindungsproblem verursacht, und geben Sie den Namen des Anbieters Blockieren von Datenverkehr.

Jedoch die FPHC kann nicht für den Benutzer eine Maßnahme vorschlagen und bietet auch kann der Grund dafür, dass der Filter-Datenverkehr an den Benutzer blockiert wird. Nur eine Erweiterung FPHC kann diese Aufgaben ausführen.

Hostfirewalls müssen möglicherweise erfolgreich Diagnostizieren der eingehenden und ausgehenden Verbindung Ausfällen durch die Firewall, und stellen Sie eine entsprechende Antwort für den Endbenutzer basierend auf der Diagnose bereit. (beispielsweise reparieren Sie Mechanismus, Meldung angezeigt, die dem Benutzer den Grund, warum die Verbindung konnte nicht usw.).

*Design Notes:* Weitere Informationen zu NDF und FPHC finden Sie in den folgenden Links:

NDF: <http://go.microsoft.com/fwlink/?LinkID=125463&clcid=0x409><br/>
FPHC: <http://go.microsoft.com/fwlink/?LinkID=125464&clcid=0x409>

### <a name="filterdriverwindowsfilteringplatformarchitecturaldesignnoaccessviolations"></a>Filter.Driver.WindowsFilteringPlatform.ArchitecturalDesign.NoAccessViolations

*WFP basierenden Produkte darf nicht die resultierende Ursache für eine Access-Verletzung bei hoher Auslastung oder während der Treiber laden/entfernen sein.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

WFP basierenden Produkte muss nicht die resultierende Ursache für eine Access-Verletzung bei hoher Auslastung oder während der Treiber laden/entfernen (while unter Netzwerklast oder nicht).
 

### <a name="filterdriverwindowsfilteringplatformarchitecturaldesignnotamperingwith3rdpartyobjects"></a>Filter.Driver.WindowsFilteringPlatform.ArchitecturalDesign.NoTamperingWith3rdPartyObjects

*WFP basierenden Produkte dürfen nicht versuchen, zu entfernen oder zu ändern, WFP Objekte und integrierter Objekte einer anderen WFP basierenden des Produkts.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Dadurch wird sichergestellt Interoperabilität zwischen mehreren Hosts Firewalls WFP-Objekte innerhalb des Betriebssystems.
 

### <a name="filterdriverwindowsfilteringplatformarchitecturaldesignpacketinjectionnodeadlocks"></a>Filter.Driver.WindowsFilteringPlatform.ArchitecturalDesign.PacketInjection.NoDeadlocks

*WFP basierenden Produkte müssen nicht ständig Netzwerkpakete ändern, die bereits geändert und erneut eingefügt, um potenzielle Deadlocks erstellt wurden.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Firewalls können Legenden ändern und erneut Netzwerkpakete, eingefügt, wenn auf allen Ebenen filtern. Einen oder mehrere Hostfirewalls können auf dem gleichen System vorhanden sein. Wenn es nur ein Host-Firewall auf dem System installiert ist ist, ständig ändern und erneut einfügen die gleichen Pakete können zu Leistungseinbußen führen und werden vermieden werden. Wenn mehrere Hostfirewalls (mit Legenden) auf dem System vorhanden sind, kann die gleichen Netzwerk Paket(e) ständig von mehreren Legenden geändert werden. Wenn eine Hostfirewall ständig ändert und reinjects dasselbe Paket, dazu führen, dass das Netzwerkpaket nie erste verarbeitet und einen Deadlock wird vermieden werden konnte potenziell erstellt.

Hostfirewalls müssen nicht ändern und reinject dasselbe Netzwerkpaket mehr als 2 Mal pro Ebene. Wenn diese Situation auftritt, können Hostfirewalls lassen Sie das Paket durchlaufen, oder legen Sie das Netzwerk-Paket.
 

### <a name="filterdriverwindowsfilteringplatformarchitecturaldesignstreaminjectionnostreamstarvation"></a>Filter.Driver.WindowsFilteringPlatform.ArchitecturalDesign.StreamInjection.NoStreamStarvation

*WFP-basiertes Produkt Legenden unter FWPM\_LAYER\_STREAM muss den Datendurchsatz nicht blockieren.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

*Nicht blockieren* bedeutet Stream sollte Layer Legende Angaben nicht Präfix für mehr als 8 MB der Daten in die Warteschlange.
 

### <a name="filterdriverwindowsfilteringplatformarchitecturaldesignsupportpowermanagedstates"></a>Filter.Driver.WindowsFilteringPlatform.ArchitecturalDesign.SupportPowerManagedStates

*WFP basierenden Produkte müssen Netzwerkkonnektivität beim Wiederherstellen von Power verwaltet Zustände zu gewährleisten.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Testenden muss auf einem Computer, der alle Power Zustände unterstützt (standby, Ruhezustand, Hybrid, Herunterfahren, neu starten). Hostfirewalls lassen Sie das System zum Wiederherstellen von der oben genannten Power und geben in verwalteten Zustände. Nach der Reaktivierung aus dieser bestimmten verwalteten Power Staaten, sollte von WFP erfüllt sein.

Firewalls sollten nie ausstehender Pakete so, dass eine Änderung Power verweigert, aufgrund der Pakete vorangestellt arbeiten.
 

### <a name="filterdriverwindowsfilteringplatformarchitecturaldesignwfpobjectacls"></a>Filter.Driver.WindowsFilteringPlatform.ArchitecturalDesign.WFPObjectACLs

*WFP basierenden Produkte ACL müssen alle ihre Objekte so, dass anderen Produkten WFP-basierte mindestens diese Objekte mithilfe der entsprechenden WFP-Enumeration APIs auflisten kann.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

WFP basierenden Produkte ACL müssen alle ihre Objekte so, dass anderen Produkten WFP-basierte mindestens diese Objekte mithilfe der entsprechenden WFP-Enumeration APIs auflisten kann.
Dies ist, um sicherzustellen, dass alle WFP-Objekte auf dem System von Hostfirewall oder einer Anwendung um zu Diagnosezwecken aufgelistet werden können.

*Design Notes:* Beispielsweise Filter-Objekten muss können durch die FwpmFilterEnum-Funktion in der folgenden URL dokumentiert aufgelistet werden sollen: <http://go.microsoft.com/fwlink/?LinkID=116839&clcid=0x409> entsprechend Enumerationsfunktionen für andere Objekte (Anbieter, Unterebene usw.) finden Sie in der folgenden URL: <http://go.microsoft.com/fwlink/?LinkID=116840&clcid=0x409>

### <a name="filterdriverwindowsfilteringplatformarchitecturaldesignwinsock"></a>Filter.Driver.WindowsFilteringPlatform.ArchitecturalDesign.Winsock

*Kernelmodus-Filtertreiber sind so konzipiert, dass Maximieren der Zuverlässigkeit und Funktionalität von Windows-Sockets als auch die Hauptkomponenten des Betriebssystems genau interagieren.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Filter Kernelmodus-Treiber sind so konzipiert, dass Maximieren der Zuverlässigkeit und Funktionalität von Windows-Sockets als auch die Hauptkomponenten des Betriebssystems genau interagieren.  Einige Bereiche besonders interessant sind:   

-   Winsock

-   Winsock-API-Funktionen

Informationen zu Winsock-APIs finden Sie unter: <http://msdn.microsoft.com/en-us/library/ms740673(VS.85).aspx>

### <a name="filterdriverwindowsfilteringplatformfirewalldisablewindowsfirewallproperly"></a>Filter.Driver.WindowsFilteringPlatform.Firewall.DisableWindowsFirewallProperly

*Hostfirewalls müssen nur die unterstützte Methode mithilfe die Windows-Firewall deaktivieren.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Hostfirewalls dienen die Möglichkeit, wählen Sie einzelne Teile der Windows-Firewall aktivieren oder deaktivieren. Folgende Teile angeben von verschiedenen Arten von Regeln (und damit auch Filter festgelegt), und möglicherweise auch auf als Kategorien bezeichnet werden. Filter werden selektiv deaktiviert werden möglicherweise Start-Filter, Firewall filtert, Verbindungsfiltern für die Sicherheit und Stealth-Filter.
Die Schnittstelle "Registrieren" wird durch das Objekt HNetCfg.FwProducts COM unterstützt. Die Put\_DisplayName() Anruf muss verwendet werden, um Ihre Produktinformationen ausfüllen.
Bevor Sie die Kategorie der Firewall-Regeln ausschalten, müssen Hersteller Firewalls, dass alle Filter installiert werden müssen sicherstellen.

Dadurch wird eine bessere Interoperabilität mit Windows sichergestellt. Darüber hinaus sollten alle installierten Hostfirewalls auf dem System sind deinstalliert aus irgendeinem Grund Windows Firewall ist bekannt, und die Firewallfilter werden automatisch aktiviert, sicherstellen, dass das System immer geschützt ist.
Die Verbindung Sicherheitsfilter müssen Windows Szenarien geschützte beibehalten aktiviert bleiben. Insbesondere unbedingt die Verbindung Sicherheitsfilter das System Communications unterstützt, die Authentifizierung und Verschlüsselung erfordern.

*Hinweise zum Entwurf*:

Dadurch wird sichergestellt, dass Firewalls Windows Firewall pro dokumentierten Richtlinien zu deaktivieren.

### <a name="filterdriverwindowsfilteringplatformfirewallnotonlypermitallfilters"></a>Filter.Driver.WindowsFilteringPlatform.Firewall.NotOnlyPermitAllFilters

*Hostfirewalls benötigen nicht nur "Zulassen\_alle" Filter.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Hostfirewalls müssen nicht den Zweck der Windows-Plattform-API Filtern von Tests, umgehen, indem einfach verwalten aller ' zulassen\_alle ' Netzwerkverkehr Filter für alle Arten von Netzwerkdatenverkehr, die nicht im Wesentlichen Filterung von Bedeutung ist. Dies gilt für sowohl statische sowie Legende Filter. In ähnlicher Weise Hostfirewalls nicht nur verwalten müssen "Block\_alle ' Filter. Allerdings werden, behandelt beim Testen für Consumer-Szenarien.
 

### <a name="filterdriverwindowsfilteringplatformfirewallsupport5tupleexceptions"></a>Filter.Driver.WindowsFilteringPlatform.Firewall.Support5TupleExceptions

*Alle hostbasierte Firewalls müssen in der Lage, blockieren zulassen/von 5-Tupel Teilen (einschließlich Port (ICMP-Typ und Code, UDP und TCP) IP-Adresse und Protokoll (beispielsweise UDP/TCP/ICMP).*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Alle hostbasierte Firewalls müssen in der Lage, blockieren zulassen/von 5-Tupel Teilen (einschließlich Port (ICMP-Typ und Code, UDP und TCP) IP-Adresse, Protokoll (beispielsweise UDP/TCP/ICMP)).

### <a name="filterdriverwindowsfilteringplatformfirewallsupportapplicationexceptions"></a>Filter.Driver.WindowsFilteringPlatform.Firewall.SupportApplicationExceptions

*WFP basierenden Produkte müssen Ausnahmen von entsprechenden Applikationen unterstützen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Zusätzlich zur Unterstützung von Szenarien, die auf innerhalb Windows® ist es wichtig zu Support (von der Privatbenutzer installiert), mit der Hostfirewall zum Filtern registrierten Anwendungen. Firewalls können Parameter, wie beispielsweise Path und Ports, als Grundlage für zulassen oder Blockieren von Datenverkehr von anwendungsspezifischen verwenden. In diesem Szenario müssen zum Arbeiten mit systemeigenen IPv4, nativen IPv6-, 6to4- und Teredo-Pakete.
*Unterstützung von* Word verweist auf die *Host-Firewall-Funktion* zum Sicherstellen der Hostfirewall Ausnahmen von Applikationen entwickelt, wenn das Anwendung/Benutzer/Netzwerk benötigt. Die Hostfirewall muss auch ordnungsgemäß konfiguriert haben Objekte, wie Filter, um die erforderlichen Funktionen unterstützen, obwohl die Funktionalität, die standardmäßig in der Benutzeroberfläche nicht aktiviert werden kann.
 

### <a name="filterdriverwindowsfilteringplatformfirewallsupportmacaddressexceptions"></a>Filter.Driver.WindowsFilteringPlatform.Firewall.SupportMACAddressExceptions

*Alle hostbasierte Firewalls, die Filter in L2 haben (Native/Mac) Ebenen müssen in der Lage zu blockieren oder Zulassen von MAC-Adresse sein.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Alle hostbasierte Firewalls, die Filter im L2 haben (Native/Mac) Ebenen müssen in der Lage zu blockieren oder Zulassen von MAC-Adresse sein.

### <a name="filterdriverwindowsfilteringplatformfirewallusewindowsfilteringplatform"></a>Filter.Driver.WindowsFilteringPlatform.Firewall.UseWindowsFilteringPlatform

*Firewalls entsprechen Filtern Windows-Plattform basierten APIs zum Filtern von Netzwerkdatenverkehr Privatbenutzer-Lösungen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Es muss keine TDI; NDIS WinSock LSP Filtern nach der Installation des Host-Firewall auf dem Computer vorhanden. In Privatbenutzer-Produkte, nur statische Filter / Legenden basierend auf Windows-Filterung Plattform (WFP) müssen verwendet werden.

*Design Notes:* Weitere Informationen zum Filtern von Windows-Plattform, finden Sie unter den folgenden Link: <http://go.microsoft.com/fwlink/?LinkID=116899&clcid=0x409>

 

### <a name="filterdriverwindowsfilteringplatformnetworkingfundamentalsupportaddressresolution"></a>Filter.Driver.WindowsFilteringPlatform.NetworkingFundamental.SupportAddressResolution

*WFP basierenden Produkte müssen erfolgreich ARP und ICMP-Neighbour-Erkennung Austausch zulassen unterstützen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

WFP basierenden Produkte müssen ARP (für IPv4) unterstützen und tauscht ICMP-Neighbour-Ermittlung (für IPv6).

Firewalls lassen Sie das System versenden ARP und ICMP-Neighbour Discovery-Anfragen und-Antworten sowie ARP und ICMP-Neighbour Discovery-Anfragen und Antworten empfangen.
*Unterstützung von* Word verweist auf die *Host-Firewall-Funktion* ARP arbeiten, vornehmen, wenn das Anwendung/Benutzer/Netzwerk benötigt. Die Hostfirewall muss auch ordnungsgemäß konfiguriert haben Objekte, wie Filter, um die erforderlichen Funktionen unterstützen, obwohl die Funktionalität, die standardmäßig in der Benutzeroberfläche nicht aktiviert werden kann.

*Design Notes:* Hostfirewalls sollte zulassen den PC-Option zum Senden von ARP-Anfragen im Auftrag einer anderen Knoten und nicht nur im Namen selbst wenn ICS auf dem Host ausgeführt wird.
Im Rahmen der ICS (ICS) DHCP-Funktionalität, ICS DHCP können ARP-Anfragen für einen anderen Knoten im Subnetz senden.
 

### <a name="filterdriverwindowsfilteringplatformnetworkingfundamentalsupportdynamicaddressing"></a>Filter.Driver.WindowsFilteringPlatform.NetworkingFundamental.SupportDynamicAddressing

*WFP basierenden Produkte unterstützt über IPv4 und IPv6 für den Austausch erfolgreich DHCP zulassen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Hostfirewalls unterstützen zulassen erfolgreichen DHCP Austausch über IPv4 und IPv6.

DHCP ENTDECKEN, DHCP-ANFORDERUNG und INFORMIEREN Sie DHCP-Paketen können über ausgehende UDP Quellport 68 an Zielport 67 übertragen werden. DHCP-ANGEBOT & DHCP ACK & DHCP NACK-Pakete können über eingehende UDP Quellport 67 Zielport 68 empfangen werden. DHCPv6-Pakete, die über ausgehende UDP Quellport 546 Zielport 547 übertragen werden können. DHCPv6-Pakete können über eingehende UDP-Quelle Port 547 Zielport 546 empfangen werden.  

*Unterstützung von* Word verweist auf die *Host-Firewall-Funktion* zum erfolgreichen DHCP-Austausch zulassen, wenn das Anwendung/Benutzer/Netzwerk benötigt. Die Hostfirewall muss auch ordnungsgemäß konfiguriert haben Objekte, wie Filter, um die erforderlichen Funktionen unterstützen, obwohl die Funktionalität, die standardmäßig in der Benutzeroberfläche nicht aktiviert werden kann.

*Design Notes:* Ausführliche Informationen finden Sie in der folgenden URL: <http://go.microsoft.com/fwlink/?LinkID=116834&clcid=0x409>

Hostfirewalls sollte zulassen DHCP eingehende und ausgehende wie der Server über die drahtlosen Schnittstelle bei ein wie ICS-Dienst auf dem Host ausgeführt wird.

Freigabe (ICS) fungiert als DHCP-Server und Empfangen von eingehenden DHCP-Clients erwartet.
DHCP-ENTDECKEN, DHCP-ANFORDERUNG und INFORMIEREN Sie DHCP-Paketen können über UDP eingehend Quellport 68 an Zielport 67 empfangen werden.
DHCP-ANGEBOT & DHCP ACK & DHCP NACK-Pakete können über ausgehende UDP Quellport 67 Zielport 68 übertragen werden.

### <a name="filterdriverwindowsfilteringplatformnetworkingfundamentalsupportipv4"></a>Filter.Driver.WindowsFilteringPlatform.NetworkingFundamental.SupportIPv4

*WFP basierenden Produkte müssen IPv4-Datenverkehr unterstützen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Dadurch wird sichergestellt, dass Consumer Hostfirewalls oder anderen Filtern Komponenten nicht zum Verlust von IPv4-Verbindung auf dem PC führen.
*Unterstützung von* Word verweist auf die *Host-Firewall-Funktion* für die Verwendung IPv4 vornehmen, wenn das Anwendung/Benutzer/Netzwerk benötigt. Die Hostfirewall muss auch ordnungsgemäß konfiguriert haben Objekte, wie Filter, um die erforderlichen Funktionen unterstützen, obwohl die Funktionalität, die standardmäßig in der Benutzeroberfläche nicht aktiviert werden kann.

*Design Notes:* Weitere Informationen zu IPv4, RFCs finden Sie in den folgenden Link: <http://go.microsoft.com/fwlink/?LinkID=116835&clcid=0x409>

### <a name="filterdriverwindowsfilteringplatformnetworkingfundamentalsupportipv6"></a>Filter.Driver.WindowsFilteringPlatform.NetworkingFundamental.SupportIPv6

*WFP basierenden Produkte müssen IPv6-Verkehr unterstützen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Windows® verfügt über IPv6 standardmäßig aktiviert. Hostfirewalls sollten systemeigene IPv6-Konnektivität (und daher Windows Szenarien, die auf IPv6) für Kunden nicht unterbrochen.

*Unterstützung von* Word verweist auf die *Host-Firewall-Funktion* arbeiten, IPv6 vornehmen, wenn das Anwendung/Benutzer/Netzwerk benötigt. Die Hostfirewall muss auch ordnungsgemäß konfiguriert haben Objekte, wie Filter, um die erforderlichen Funktionen unterstützen, obwohl die Funktionalität, die standardmäßig in der Benutzeroberfläche nicht aktiviert werden kann.

*Design Notes:* Weitere Informationen zu IPv6 finden Sie in den folgenden Link: <http://go.microsoft.com/fwlink/?LinkID=116832&clcid=0x409>

### <a name="filterdriverwindowsfilteringplatformnetworkingfundamentalsupportnameresolution"></a>Filter.Driver.WindowsFilteringPlatform.NetworkingFundamental.SupportNameResolution

*WFP basierenden Produkte müssen zulassen erfolgreiche Abfragen für DNS-Clients unterstützen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

DNS-ABFRAGE-Paket gesendet werden kann über out \[UDP Ziel ausgehenden Port 53 (Domain Name Server)\] und DNS-ABFRAGE Antwortpaket über empfangen müssen \[eingehende UDP-Quelle Port 53 (Domain Name Server)\]. Hostfirewalls sollte erfolgreichen DNS-Client Abfragen über IPv4 und IPv6 zulassen.
*Unterstützung von* Word bezieht sich auf die *Host-Firewall-Funktion* zum erfolgreichen DNS-Client-Abfragen zulassen, wenn das Anwendung/Benutzer/Netzwerk benötigt. Die Hostfirewall muss auch ordnungsgemäß konfiguriert haben Objekte, wie Filter, um die erforderlichen Funktionen unterstützen, obwohl die Funktionalität, die standardmäßig in der Benutzeroberfläche nicht aktiviert werden kann.

*Design Notes:* Weitere Informationen zu DNS RFCs finden Sie in den folgenden Link: <http://go.microsoft.com/fwlink/?LinkID=116835&clcid=0x409> Hostfirewalls sollte diese Art von DNS-Datenverkehr (Host als Server) über die Schnittstelle drahtlosen zulassen, wenn ein Dienst wie ICS auf dem Host ausgeführt wird.
Diese Anforderung gilt für ICS, die als einen DNS-Server (Proxy) fungiert und empfangende eingehende DNS-Anforderungen von Clients, auf dem Ziel-UDP-Port 53 erwartet und an den DNS-Client mit DNS-Antwort mit Ziel UDP-Port 53 reagieren.

### <a name="filterdriverwindowsfilteringplatformscenariosupport6to4"></a>Filter.Driver.WindowsFilteringPlatform.Scenario.Support6to4

*WFP basierenden Produkte müssen 6to4 unterstützen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

In bestimmten Märkten erleichtert 6to4-Technologien bestimmte Kunden in IPv6-Konnektivität zu verschieben. Die folgenden Richtlinien können hilfreich sein, diese Anforderung erfüllen:

-   Hostfirewalls für das System zum Senden und Empfangen von IPv6-Paketen über IPv4-Protokoll 41 ermöglichen.

*Unterstützung von* Word bezieht sich auf die *Host-Firewall-Funktion* zum 6to4-Arbeit, wenn das Anwendung/Benutzer/Netzwerk benötigt. Die Hostfirewall muss auch ordnungsgemäß konfiguriert haben Objekte, wie Filter, um die erforderlichen Funktionen unterstützen, obwohl die Funktionalität, die standardmäßig in der Benutzeroberfläche nicht aktiviert werden kann.

*Design Notes:* Im folgenden Artikel unten für Weitere Informationen zu 6to4 Näheres: <http://go.microsoft.com/fwlink/?LinkID=116837&clcid=0x409>
 

### <a name="filterdriverwindowsfilteringplatformscenariosupportautomaticupdates"></a>Filter.Driver.WindowsFilteringPlatform.Scenario.SupportAutomaticUpdates

*WFP-basierte Produkte müssen automatische Updates in Windows unterstützen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Dies bezieht sich auf die automatische Updates / Windows Update (WU) ist eine wichtige Szenario über die wichtige Patches, auf dem Computer installiert werden, auf dem aktuellen Stand zu halten. Die folgende Richtlinien kann hilfreich sein, diese Anforderung erfüllen:
 

-   Hostfirewalls zulassen ausgehende TCP-Verbindungen für Ziel-Anschlüsse 80 und 443

*Unterstützung von* Word verweist auf die *Host-Firewall-Funktion* automatische Updates arbeiten, vornehmen, wenn das Anwendung/Benutzer/Netzwerk benötigt. Die Hostfirewall muss auch ordnungsgemäß konfiguriert haben Objekte, wie Filter, um die erforderlichen Funktionen unterstützen, obwohl die Funktionalität, die standardmäßig in der Benutzeroberfläche nicht aktiviert werden kann.

*Design Notes:* Weitere Informationen zu Windows-Updates oder automatische Updates finden Sie in den folgenden Link: <http://go.microsoft.com/fwlink/?LinkID=116898&clcid=0x409>

### <a name="filterdriverwindowsfilteringplatformscenariosupportbasicwebsitebrowsing"></a>Filter.Driver.WindowsFilteringPlatform.Scenario.SupportBasicWebsiteBrowsing

*WFP basierenden Produkte müssen grundlegende Erfahrungen im Internet unterstützen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Dadurch wird sichergestellt, dass grundlegende Internet browserumgebungen bei der Installation einer Firewall Host auf einem Windows unterstützt werden&ndash;-basierter Computer.
Hostfirewalls müssen TCP-Pakete über Ports 80 und 443 zur Unterstützung dieses Szenarios zulassen. In diesem Szenario muss mit systemeigenen IPv4, nativen IPv6-, 6to4- und Teredo-Pakete arbeiten.
*Unterstützung von* Word verweist auf die *Host-Firewall-Funktion* , die einer erfolgreichen Internet durchsuchen wünschen, stellen Sie sicher, wenn das Anwendung/Benutzer/Netzwerk benötigt. Die Hostfirewall muss auch ordnungsgemäß konfiguriert haben Objekte, wie Filter, um die erforderlichen Funktionen unterstützen, obwohl die Funktionalität, die standardmäßig in der Benutzeroberfläche nicht aktiviert werden kann.

### <a name="filterdriverwindowsfilteringplatformscenariosupportfileandprintersharing"></a>Filter.Driver.WindowsFilteringPlatform.Scenario.SupportFileAndPrinterSharing

*WFP basierenden Produkte müssen Datei- und Druckerfreigabedienst unterstützen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Dadurch wird sichergestellt, dass Privatbenutzer Freigeben von Inhalten zu und von anderen PCs innerhalb ihrer privaten Netzwerk, zusätzlich zu drucken Inhalte auf freigegebenen Druckern können.
Hostfirewalls müssen zulassen UDP-Pakete speziell für 17-Protokoll über Ports 137 / 138 und TCP-Pakete, die speziell für Protokoll 6 über Ports 139/445. In diesem Szenario muss mit systemeigenen IPv4, nativen IPv6-, 6to4- und Teredo-Pakete verwendet werden.
TCP-Pakete dürfen über Ports 5357/5358 & UDP-Pakete über Port 3702 dürfen. In diesem Szenario sollte systemeigenen IPv4, systemeigenen IPv6, 6to4 und Teredo-Pakete entwickelt.
*Unterstützung von* Word verweist auf die *Host-Firewall-Funktion* zum Datei- und Druckerfreigabe Arbeit, getroffen werden, wenn das Anwendung/Benutzer/Netzwerk benötigt. Die Hostfirewall muss auch ordnungsgemäß konfiguriert haben Objekte, wie Filter, um die erforderlichen Funktionen unterstützen, obwohl die Funktionalität, die standardmäßig in der Benutzeroberfläche nicht aktiviert werden kann.

*Design Notes:* Entnehmen Sie den folgenden Link Weitere Informationen:                 <http://go.microsoft.com/fwlink/?LinkID=116838&clcid=0x409>

Lesen Sie die folgenden Dokumente Weitere Informationen:

-   Heimnetzgruppe Firewallanforderungen: <http://technet.microsoft.com/en-us/appcompat/default.aspx>

-   Dialogfeld für Netzwerk-Speicherort: <http://technet.microsoft.com/en-us/appcompat/default.aspx>

-   PNRP: <http://technet.microsoft.com/en-us/appcompat/default.aspx>

### <a name="filterdriverwindowsfilteringplatformscenariosupporticmperrormessages"></a>Filter.Driver.WindowsFilteringPlatform.Scenario.SupportICMPErrorMessages

*WFP basierenden Produkte müssen ICMP-Fehlermeldungen und Discovery-Funktionen unterstützen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Dies ist um sicherzustellen, dass Hostfirewalls ICMP-Fehlermeldungen (pro IETF RFC 4890 und RFC 2979) unterstützen für eingehenden und ausgehenden Pakete, die nicht gelöscht werden müssen. Wichtige Discovery-Funktionen müssen auch unterstützt werden. Die Fehlermeldungen, die für ICMPv4 und ICMPv6 sind unterstützt werden müssen: Ziel nicht erreichbar, Zeit überschritten und Parameter Problem. Darüber hinaus müssen für ICMPv6 Paket zu groß, Router-Anfrage, Neighbour-Anfrage, Router Ankündigung und benachbarten Ankündigung Discovery-Funktionen unterstützt werden.
*Unterstützung von* Word verweist auf die *Host-Firewall-Funktion* ausgeführt, ICMP vornehmen, wenn das Anwendung/Benutzer/Netzwerk benötigt. Die Hostfirewall muss auch ordnungsgemäß konfiguriert haben Objekte, wie Filter, um die erforderlichen Funktionen unterstützen, obwohl die Funktionalität, die standardmäßig in der Benutzeroberfläche nicht aktiviert werden kann.

*Design Notes:* Weitere Informationen finden Sie unter <http://go.microsoft.com/fwlink/?LinkID=116835&clcid=0x409>

### <a name="filterdriverwindowsfilteringplatformscenariosupportinternetstreaming"></a>Filter.Driver.WindowsFilteringPlatform.Scenario.SupportInternetStreaming

*WFP basierenden Produkte müssen Internet streaming und Freigeben für Media Player Netzwerk Dienste für den Austausch von Medien unterstützen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Dies bezieht sich auf die automatische Updates / Windows Update (WU) ist eine wichtige Szenario wichtige Patches über die auf dem Computer installiert werden, auf dem aktuellen Stand zu halten. Die folgenden Richtlinien können hilfreich sein, diese Anforderung erfüllen:

Hostfirewalls zulassen ausgehende TCP-Verbindungen für Ziel-Anschlüsse 80 und 443
*Unterstützung von* Word verweist auf die *Host-Firewall-Funktion* automatische Updates arbeiten, vornehmen, wenn das Anwendung/Benutzer/Netzwerk benötigt. Die Hostfirewall muss auch ordnungsgemäß konfiguriert haben Objekte, wie Filter, um die erforderlichen Funktionen unterstützen, obwohl die Funktionalität, die standardmäßig in der Benutzeroberfläche nicht aktiviert werden kann.

*Design Notes:* Weitere Informationen zu Windows-Updates oder automatische Updates finden Sie in den folgenden Link: <http://go.microsoft.com/fwlink/?LinkID=116898&clcid=0x409>

 

### <a name="filterdriverwindowsfilteringplatformscenariosupportmediaextenderstreaming"></a>Filter.Driver.WindowsFilteringPlatform.Scenario.SupportMediaExtenderStreaming

*WFP basierenden Produkte müssen Media streaming-Szenarien basierend auf Extender-Technologien unterstützen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Extender-Technologie Unterhaltungsmedien Geräten wie TV-Geräte, DVD-Player integriert ist und praktisch, quiet Komponenten, mit denen Sie Ihren PC zu halten, ist es sinnvoll und es als Hub verwenden, um Ihre digitale Unterhaltung in der gesamten Haus TV bereitzustellen. Diese Geräte heißen Extender-Geräte.
Beispiel: mit dem neuen Extender für Windows Media Center, Sie können die digitalen Medien auf Ihrem Computer mit Windows Media Center in fünf Räumen sind stream. Home-Benutzer können die aufgezeichnete und live-TV, Musik, Filme, Videos, Sportliga, Internet TV und andere Onlineinhalte auf Windows® PCs über verdrahtete oder drahtlose private Netzwerke zugreifen. Windows Media Center Extender verwenden Netzwerkports für die Kommunikation mit Windows-PCs. In den folgenden Tabellen von Ausnahmen können Erfüllung dieser Anforderung hilfreich sein.

**In Tabelle 1. Media Center Extender-spezifischen**
<table>
<tr><th>Ausführbare Binärdatei</th><th>Port</th><th>Richtung</th><th>Bereich</th></tr>
<tr><td>Svchost.exe (Ssdpsrv)</td><td>UDP 1900</td><td>Eingehend</td><td>Lokale Subnetz</td></tr>
<tr><td>Svchost.exe (Termservice)</td><td>TCP 3390</td><td>Eingehend</td><td>Lokale Subnetz</td></tr>
<tr><td>Svchost.exe (QWave)</td><td>TCP 2177</td><td>Ausgehende, eingehend</td><td>Lokale Subnetz</td></tr>
<tr><td>Svchost.exe (QWave)</td><td>UDP 2177</td><td>Ausgehende, eingehend</td><td>Lokale Subnetz</td></tr>
<tr><td> System</td><td>TCP 10244</td><td>Ausgehende, eingehend</td><td>Lokale Subnetz</td></tr>
<tr><td>Ehshell.exe</td><td>TCP 554</td><td>Ausgehende, eingehend</td><td>Lokale Subnetz</td></tr>
<tr><td>Ehshell.exe</td><td>UDP 5004, 5005</td><td>Ausgehende, eingehend</td><td>Lokale Subnetz</td></tr>
<tr><td>Ehshell.exe</td><td>TCP 8554-8558</td><td>Ausgehende, eingehend</td><td>Lokale Subnetz</td></tr>
<tr><td>Ehshell.exe</td><td>UDP 50004-50013</td><td>Ausgehende, eingehend</td><td>Lokale Subnetz</td></tr>
<tr><td>Ehshell.exe</td><td>UDP 7777 7781</td><td>Ausgehende, eingehend</td><td>Lokale Subnetz</td></tr>
<tr><td>mcrmgr.exe</td><td>zufällige</td><td>Ausgehende</td><td>Internet</td></tr>
<tr><td>mc2prov.exe</td><td>zufällige</td><td>Ausgehende</td><td>Internet</td></tr>
<tr><td>Svchost.exe (mcs2svc)</td><td>zufällige</td><td>Ausgehende</td><td>Lokale Subnetz</td></tr>
</table>

**In Tabelle 2. Media Center binäre ausführbare Dateien und ports**

<table>
<tr><th>Ausführbare Binärdatei</th><th>Port</th><th>Richtung</th><th>Bereich</th></tr>
<tr><td>ehrecvr.exe</td><td>zufällige</td><td>Ausgehende</td><td>Internet</td></tr>
<tr><td>ehrec.exe</td><td>zufällige</td><td>Ausgehende</td><td>Internet</td></tr>
<tr><td>ehexthost.exe</td><td>zufällige</td><td>Ausgehend, eingehend</td><td>Internet</td></tr>
<tr><td>MCUPDATE.exe</td><td>zufällige</td><td>Ausgehende</td><td>Internet</td></tr>
</table>

**Tabelle 3. Digitales Kabel Receiver-Gerät (Opencable)**

<table>
<tr><th>Ausführbare Binärdatei</th><th>Port</th><th>Richtung</th><th>Bereich</th></tr>
<tr><td>ehprivjob.exe</td><td>UDP 5001 5006</td><td>Eingehend</td><td>Lokale Subnetz</td></tr>
<tr><td>Svchost.exe</td><td>UDP 1900</td><td>Ausgehende, eingehend</td><td>Lokale Subnetz</td></tr>
<tr><td>System</td><td>TCP 2869</td><td>Ausgehende, eingehend</td><td>Lokale Subnetz</td></tr>
<tr><td>ehprivjob.exe</td><td>TCP 554</td><td>Ausgehende</td><td>Lokale Subnetz</td></tr>
<tr><td>ehprivjob.exe</td><td>UDP 5757-5772</td><td>Ausgehende</td><td>Lokale Subnetz</td></tr>
</table>
 
*Unterstützung von* Word verweist auf die *Host-Firewall-Funktion* zu Internet streaming & Media Player-Netzwerk Dienste nutzt gemeinsame Nutzung von Medien, arbeiten, wenn das Anwendung/Benutzer/Netzwerk benötigt. Host-Firewall muss auch ordnungsgemäß konfiguriert haben Objekte, wie Filter, um den erforderlichen Funktionen unterstützen, obwohl die Funktionalität, die standardmäßig in der Benutzeroberfläche nicht aktiviert werden kann.

### <a name="filterdriverwindowsfilteringplatformscenariosupportmobilebroadband"></a>Filter.Driver.WindowsFilteringPlatform.Scenario.SupportMobileBroadBand

*WFP basierenden Produkte müssen Breitband Mobilgeräten zulassen, die mit Windows mobile Breitband-Treiber-Modell eine ordnungsgemäße Funktion kompatibel sind*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

WFP basierenden Produkte müssen mobile Breitband Geräte zulassen, die mit dem Windows mobile Breitband-Treiber-Modell eine ordnungsgemäße Funktion kompatibel sind.
Dadurch wird sichergestellt, dass Host-Firewall-Funktion nicht, die mobile Breitband-Konnektivität blockiert wird und die Firewall-Funktionalität-MB-Geräte verwendet.
Windows Bereitstellen der systemeigenen Unterstützung für mobile (MB) Datenkarten & eingebettete Module Windows entwickelt. Die Geräte MB müssen ihre Treiber gemäß den Anweisungen in Windows mobile Breitband-Treiber-Modell zu implementieren. MB-Treiber-Modell definiert, wie die Geräte verfügbar gemacht werden sollen, Windows und Netzwerk Paketformat in dem MB Geräte Netzwerk- und Datenaustausch zwischen sollten.

### <a name="filterdriverwindowsfilteringplatformscenariosupportpeernameresolution"></a>Filter.Driver.WindowsFilteringPlatform.Scenario.SupportPeerNameResolution

*WFP basierenden Produkte müssen Peer Name Resolution-Protokoll und das Peer-to-Peer gruppieren-Protokoll unterstützen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Hostfirewalls unterstützen Peer Name Resolution Protocol (PNRP) und das Peer-zu-Peer-Gruppierung Protokoll, die für einige Peer-zu-Peer-Anwendungen erforderlich sind. Peer Name Resolution-Protokoll bietet sichere, ohne Server Auflösung und das Protokoll der Peer-zu-Peer-Gruppierung bietet sichere und zuverlässige mit mehreren Teilnehmern Kommunikation. Die folgenden Richtlinien können Erfüllung dieser Anforderung hilfreich sein:

1.  Hostfirewalls unterstützen systemeigene IPv6 (NETWORK-0244) sowie Teredo (NETWORK-0248) und IPv6-Paketen an IPv4-Protokoll 41 (^ to4) (NETWORK-0249).

2.  Hostfirewalls können für das System ausgehende senden und Empfangen von eingehenden, UDP Pakete über Port 3540 gestatten.

3.  Hostfirewalls können für das System ausgehende senden und Empfangen von eingehenden, TCP Pakete über Port 3587 gestatten.

*Unterstützung von* Word verweist auf die *Host-Firewall-Funktion* zum erfolgreichen DHCP-Austausch zulassen, wenn das Anwendung/Benutzer/Netzwerk benötigt. Die Hostfirewall muss auch ordnungsgemäß konfiguriert haben Objekte, wie Filter, um die erforderlichen Funktionen unterstützen, obwohl die Funktionalität, die standardmäßig in der Benutzeroberfläche nicht aktiviert werden kann.

*Hinweise zum Entwurf*:

Finden Sie weitere Informationen, die diese Dokumente den folgenden Dokumenten:
 

-   Heimnetzgruppe firewallanforderungen: <http://technet.microsoft.com/en-us/appcompat/default.aspx>

-   Netzwerk Speicherort Dialogfeld: <http://technet.microsoft.com/en-us/appcompat/default.aspx>

-   PNRP: <http://technet.microsoft.com/en-us/appcompat/default.aspx>

### <a name="filterdriverwindowsfilteringplatformscenariosupportremoteassistance"></a>Filter.Driver.WindowsFilteringPlatform.Scenario.SupportRemoteAssistance

*WFP basierenden Produkte müssen Remoteunterstützung Szenarien unterstützen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Das Szenario Remoteunterstützung wird durch ein Hilfsprogramm an einen Computer anschließen und dem Benutzer eine Lösung des Problems an. Die folgenden Richtlinien möglicherweise Einhaltung dieser Anforderung: Hostfirewalls zulassen, dass den Computer durch systemeigene IPv4, systemeigene IPv6, Teredo und 6to4-(übergeben Sie die entsprechenden Tests) erreicht werden sowie Datenverkehr von der Anwendung Remoteunterstützung innerhalb Windows® (msra.exe) durch die Firewall zu ermöglichen.
*Unterstützung von* Word verweist auf die *Host-Firewall-Funktion* Remoteunterstützung arbeiten, vornehmen, wenn das Anwendung/Benutzer/Netzwerk benötigt. Die Hostfirewall muss auch ordnungsgemäß konfiguriert haben Objekte, wie Filter, um die erforderlichen Funktionen unterstützen, obwohl die Funktionalität, die standardmäßig in der Benutzeroberfläche nicht aktiviert werden kann.

*Design Notes:* Informationen über die Funktionsweise von Remoteunterstützung im Allgemeinen finden Sie im folgenden Artikel: <http://go.microsoft.com/fwlink/?LinkID=116842&clcid=0x409>
 

### <a name="filterdriverwindowsfilteringplatformscenariosupportremotedesktop"></a>Filter.Driver.WindowsFilteringPlatform.Scenario.SupportRemoteDesktop

*WFP basierenden Produkte müssen remote Desktop unterstützen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Remotedesktopverbindung ist eine Technologie, die Verbindung mit einem Remotecomputer in einen anderen Speicherort ausgeführt werden können. Remotedesktop ist eine wichtige Windows® Szenario, die für Consumer mit mehreren am home versucht auf Inhalte zugreifen, die auf einem PC, von einem anderen PC vorhanden ist relevant wären.
Die folgende Richtlinien kann hilfreich sein, diese Anforderung erfüllen:

Hostfirewalls zulässt eingehenden TCP-Pakete über Ziel Port 3389 zur Unterstützung dieses Szenarios. In diesem Szenario müssen zum Arbeiten mit systemeigenen IPv4, nativen IPv6-, 6to4- und Teredo-Pakete.
*Unterstützung von* Word bezieht sich auf die *Host-Firewall-Funktion* zum remote desktop funktioniert, wenn das Anwendung/Benutzer/Netzwerk benötigt. Die Hostfirewall muss auch ordnungsgemäß konfiguriert haben Objekte, wie Filter, um die erforderlichen Funktionen unterstützen, obwohl die Funktionalität, die standardmäßig in der Benutzeroberfläche nicht aktiviert werden kann.

*Design Notes:* Weitere Informationen zum Remotedesktop, finden Sie unter den folgenden Artikel: <http://go.microsoft.com/fwlink/?LinkID=116841&clcid=0x409>

### <a name="filterdriverwindowsfilteringplatformscenariosupportteredo"></a>Filter.Driver.WindowsFilteringPlatform.Scenario.SupportTeredo

*WFP basierenden Produkte müssen Teredo unterstützen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Teredo kann als Connectivity Mechanismus zur Unterstützung von bestimmten Windows-Szenarien wie Remoteunterstützung, instant messaging und anderen Benutzern verwendet werden. Daher ist die Beibehaltung Teredo-Konnektivität entscheidender Faktor in der Windows-Consumer-Szenarien unterstützen.
Für diese Anforderung muss Folgendes erfüllt sein:

-   DNS-Auflösung von teredo.ipv6.microsoft.com zulassen Hostfirewalls

-   Um Client Teredo-Server-Kommunikation zu ermöglichen, müssen das System zum Senden von ausgehenden UDP/IPv4-Pakete an UDP-Port 3544 Hostfirewalls ermöglichen.

-   Um Teredo-Konnektivität zu ermöglichen, müssen Hostfirewalls eingehende und ausgehende UDP/IPv4-Datenverkehr über der Teredo-Client-Ports zulassen. Diese Ports können über die Benachrichtigung FWPMSystemPortsGet bestimmt die System Portnummern wird für die Kommunikation mit der Teredo-Schnittstelle abgerufen werden.

-   Hostfirewalls unterstützen ICMP-Fehlermeldungen und Discovery-Funktionen (NETWORK-0250 Logo Anforderung).

-   Hostfirewalls zulassen UPnP-Framework Pakete über UDP-Port 1900 und UPnP-Frameworkpackets über TCP-Port 2869.

*Unterstützung von* Word verweist auf die *Host-Firewall-Funktion* Teredo arbeiten, vornehmen, wenn das Anwendung/Benutzer/Netzwerk benötigt. Die Hostfirewall muss auch ordnungsgemäß konfiguriert haben Objekte, wie Filter, um die erforderlichen Funktionen unterstützen, obwohl die Funktionalität, die standardmäßig in der Benutzeroberfläche nicht aktiviert werden kann.

*Design Notes:* Näheres im folgenden Artikel unten für Weitere Informationen zu Teredo: <http://go.microsoft.com/fwlink/?LinkID=116836&clcid=0x409>

### <a name="filterdriverwindowsfilteringplatformscenariosupportvirtualprivatenetworking"></a>Filter.Driver.WindowsFilteringPlatform.Scenario.SupportVirtualPrivateNetworking

*WFP-basierte Produkte müssen VPN-Szenarien in Windows unterstützen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Die folgenden Protokolle und Ports müssen zugelassen werden:

-   IP-Protokoll 50: ESP Datenverkehr zulassen            

-   IP-Protokoll 51: AH-Datenverkehr zulassen            

-   UDP-Port 500 / 4500: zulassen ISAKMP-Verkehr           

-   TCP / UDP-Port 88: Zulassen der Kerberos-Datenverkehr

Dadurch wird sichergestellt, dass Firewalls IPSec-Szenarien wie IPsec VPN, die Client-PCs verwendet werden unterstützen, eine sichere Verbindung über das Internet herstellen.
Darüber hinaus sollte Hostfirewalls erfolgreiche Kommunikation über IPv4 und IPv6 zulassen. Hostfirewalls sollten Pakete über Port 1701 UDP und TCP-Pakete über Port 443 zur Unterstützung dieses Szenarios zu ermöglichen. Es wird zudem empfohlen, Hostfirewalls TCP-Pakete über Port 1723 bestimmte zulassen. IP-Protokoll 47 Pakete sollten auch durch die Firewall zugelassen werden.
*Unterstützung von* Word verweist auf die *Host-Firewall-Funktion* , die VPN-Szenarien arbeiten, machen, wenn das Anwendung/Benutzer/Netzwerk benötigt. Die Hostfirewall muss auch ordnungsgemäß konfiguriert haben Objekte, wie Filter, um die erforderlichen Funktionen unterstützen, obwohl die Funktionalität, die standardmäßig in der Benutzeroberfläche nicht aktiviert werden kann.

*Design Notes:* Entnehmen Sie weitere Informationen im folgenden Artikel: <http://go.microsoft.com/fwlink/?LinkID=116843&clcid=0x409>

### <a name="filterdriverwindowsfilteringplatformscenariovswitchinteropwithotherextensions"></a>Filter.Driver.WindowsFilteringPlatform.Scenario.vSwitch.InteropWithOtherExtensions

*WFP muss Datenverkehr von einem anderen vSwitch-Erweiterung (WFP oder LWF) standardmäßig nicht blockieren und sollte nur dann, wenn bestimmte Benutzeradministrator Absicht folgen, oder das System gegen eine spezifische Bedrohung zu schützen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

WFP muss Datenverkehr von einem anderen vSwitch-Erweiterung (WFP oder LWF) standardmäßig nicht blockieren und sollte nur dann, wenn bestimmte Benutzeradministrator Absicht folgen, oder das System gegen eine spezifische Bedrohung zu schützen.

### <a name="filterdriverwindowsfilteringplatformscenariovswitchnoegressmodification"></a>Filter.Driver.WindowsFilteringPlatform.Scenario.vSwitch.NoEgressModification

*WFP-basierte Produkte, die in der vSwitch betrieben werden müssen Pakete auf den Pfad der Ausgang von der vSwitch nicht geändert werden.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

WFP-basierte Produkte, die in der vSwitch betrieben werden müssen Pakete auf den Pfad der Ausgang von der vSwitch nicht geändert werden.

### <a name="filterdriverwindowsfilteringplatformscenariovswitchsupportlivemigration"></a>Filter.Driver.WindowsFilteringPlatform.Scenario.vSwitch.SupportLiveMigration

*WFP basierenden Produkte, die in der vSwitch ausgeführt werden, müssen für die Migration von Live eine minimale MOF darstellen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

WFP basierenden Produkte, die in der vSwitch ausgeführt werden, müssen für die Migration von Live eine minimale MOF darstellen. Deklarieren Sie in MOF es muss selbst Logo kompatible für die Migration von Live und zulässig, Sie selbst nicht standardmäßig blockiert Migration oder migriert werden. Die gesamte Zeitdauer für Migrationen für die Migration Live darf nicht länger als 2 Sekunden sein.

### <a name="filterdriverwindowsfilteringplatformscenariovswitchsupportremoval"></a>Filter.Driver.WindowsFilteringPlatform.Scenario.vSwitch.SupportRemoval

*WFP basierenden Produkte, die in den vSwitch ausgeführt werden dürfen, entfernt werden soll, wenn der Administrator für die Instanz vSwitch WFP deaktiviert.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

WFP basierenden Produkte, die in der vSwitch ausgeführt werden dürfen entfernt werden soll, wenn der Administrator für die Instanz vSwitch WFP deaktiviert.

### <a name="filterdriverwindowsfilteringplatformscenariovswitchsupportreordering"></a>Filter.Driver.WindowsFilteringPlatform.Scenario.vSwitch.SupportReordering

*WFP basierenden Produkte, die in der vSwitch ausgeführt werden müssen auf WFP VmSwitch neu anordnen Ereignisse zu reagieren.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

WFP basierenden Produkte, die in der VmSwitch ausgeführt werden müssen auf WFP VmSwitch neu anordnen Ereignisse zu reagieren.
