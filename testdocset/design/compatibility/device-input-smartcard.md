---
title: Device.Input.SmartCard
Description: Requirements.
ms.assetid: 
MSHAttr: 
author: beneluxboy
ms.openlocfilehash: 575a08b7cd183f8181c05ca9cb1d16433f8b0676
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="deviceinputsmartcard"></a>Device.Input.SmartCard

 - [Device.Input.SmartCardMiniDriver](#device.input.smartcardminidriver)
 - [Device.Input.SmartCardReader](#device.input.smartcardreader)

<a name="device.input.smartcardminidriver"></a>
## <a name="deviceinputsmartcardminidriver"></a>Device.Input.SmartCardMiniDriver

*Minitreiber Programm Smart-Karten*

### <a name="deviceinputsmartcardminidriverdonotstopwhenresourcesareunavailable"></a>Device.Input.SmartCardMiniDriver.DoNotStopWhenResourcesAreUnavailable

*Smartcard-Treiber muss das System nicht beendet, falls erforderlich, dass Ressourcen nicht verfügbar sind.*

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

Smartcard-Treiber muss System-Vorgang nicht unterbrechen, wenn Ressourcen, die vom Reader erforderlich sind nicht verfügbar sind.

### <a name="deviceinputsmartcardminidriverspecsandcertifications"></a>Device.Input.SmartCardMiniDriver.SpecsAndCertifications

*Windows Smartcard Minidrivers muss Windows Smartcard Minitreiber Version 5 Spezifikationen und Zertifizierung Kriterien erfüllen.*

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

Smartcard-Minidrivers werden pluggable Security-Komponenten, die eine Abstraktionsebene zwischen dem base CSP und der Smartcard sicheren Speicher für kryptografischen Schlüsseln und Zertifikaten bereitzustellen bereitstellen. Smartcard-Minidrivers führen Sie sichere kryptografische Operationen, einschließlich Verschlüsselung, Entschlüsselung, Einrichtung Schlüssels, Austausch der Sitzungsschlüssel und digitale Signaturen. Smartcard-Minidrivers gehören auch andere Formfaktoren, wie ein USB-Token oder anderen persönlichen Geräten.
Smartcard-Minidrivers muss die folgenden Spezifikationen entsprechen:

-   Smartcard Minitreiber Spezifikation für Windows Base Cryptographic Service Provider (Base CSP) und Smartcard-Taste Speicher-Anbieter (KSP), Version 5.06 (oder höher).

-   Smartcard Minitreiber Zertifizierung Kriterien, Version 5.06 (oder höher).

Smartcard-Minidrivers muss die folgenden grundlegenden Kriterien erfüllen:

-   Wenn das Gerät gesendet zu Testzwecken eine Smartcard ist und eine ISO 7816 ID-1 Smartcard-Formfaktor hat, muss es mit Smartcard-Leser getestet werden, die die WHQL testen Anforderungen für Smart Karten bestanden hat.

-   Das Gerät eine Multifunktionsgeräten ist, müssen sie die Anforderungen an das Logo für jede Gerätekategorie geleitet ist eine Logoprogramm vorhanden.

-   Die Karte Minitreiber möglicherweise zusätzliche Funktionen darüber hinaus in der Karte Minitreiber Spezifikation angegeben nicht implementieren.

-   Die Karte Minitreiber möglicherweise keine trojanischen oder "Kommunikationskanäle" enthalten.

-   Die Karte Minitreiber möglicherweise keine Benutzeroberfläche für den Endbenutzer vorhanden.

-   Alle kryptografischen Vorgänge müssen auf dem Gerät stattfinden.

-   Alle kryptografischen Schlüssel müssen auf dem Gerät gespeichert sein und darf nicht vom Gerät exportierbar sein.

Smartcard Minidrivers muss die folgenden allgemeinen Kriterien in der Karte Minitreiber Zertifizierung Kriterien erfüllen:

-   Karte Minitreiber Verwaltung und Installation

-   Karte Minitreiber logische Datei – Systemanforderungen

-   Karte Minitreiber allgemeine Konventionen

-   Karte Minitreiber Speicherverwaltung

-   Optional allgemeinen Anforderungen

Smartcard-Minitreiber muss für jede der funktionalen Exporte für jede Funktion in der Spezifikation Karte Minitreiber Kriterien entsprechen einschließlich:

-   Funktion

-   Leistung

-   Fehlerbehandlung

Smartcard-Minidrivers muss den sequenzierten Aufruf der Karte Minitreiber Funktionen unterstützen.
Eine Smartcard-Minitreiber möglicherweise mehrere Smart Karten unterstützen, aber die Zertifizierung Kriterien für jede der unterstützten Smart Karten müssen separat übergeben.

*Hinweise zum Entwurf*  

Finden Sie unter Smartcard Minitreiber Spezifikation für Windows Base Cryptographic Service Provider (Base CSP) und Smartcard-Taste Speicher-Anbieter (KSP), Versionsspezifikationen unter <http://msdn.microsoft.com/en-us/windows/hardware/gg487500.aspx>.
Finden Sie unter Smartcard Minitreiber Zertifizierung Kriterien auf <http://msdn.microsoft.com/en-us/windows/hardware/gg487504>.
Die folgende Tabelle beschreibt die minimale und maximale-Spezifikation, Version, die auf bestimmten OS Familie unterstützt werden müssen:

| Betriebssystem-Produktfamilie | Zulässige Spezifikation Versionen                                                                         |
|-------------------------|--------------------------------------------------------------------------------------------------------|
| Windows 7-client        | 5,6,7 (eine beliebige Kombination zulässig wie etwa 5 und nur 7, nur 5, nur 7, 5 und 6 nur 6 und 7 nur usw..) |
| WindowsServer 2008     | 5,6,7 (eine beliebige Kombination zulässig wie etwa 5 und nur 7, nur 5, nur 7, 5 und 6 nur 6 und 7 nur usw..) |
| Windows 8-client        | 5,6,7 (eine beliebige Kombination zulässig wie 5 und nur 7, nur 5, nur 7, 5 und 6 nur 6 und 7 nur usw..) |
| WindowsServer 2016     | 5,6,7 (eine beliebige Kombination zulässig wie etwa 5 und nur 7, nur 5, nur 7, 5 und 6 nur 6 und 7 nur usw..) |

 

### <a name="deviceinputsmartcardminidriversupportmultipleinstancesonasystem"></a>Device.Input.SmartCardMiniDriver.SupportMultipleInstancesOnASystem

*Smartcard-Treiber kann mehrere Instanzen desselben Geräts auf einem System unterstützt.*

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

Smartcard-Treiber muss ordnungsgemäß funktionsfähig, wenn mehr als eine Instanz der Geräte auf einem System installiert ist. Die Funktionalität von jedem Geräteinstanz muss konsistent sein. Wenn eine separate Instanz geladen wird, kann nicht die Funktionalität eingeschränkt.

<a name="device.input.smartcardreader"></a>
## <a name="deviceinputsmartcardreader"></a>Device.Input.SmartCardReader

### <a name="deviceinputsmartcardreaderpindataentrykeyboardcomplieswithiso"></a>Device.Input.SmartCardReader.PinDataEntryKeyboardCompliesWithIso

*Ein input Gerät, das eine PIN zur Dateneingabe Tastatur implementiert muss ISO entsprechen.*

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

Eine Eingabe Gerät, das eine Tastatur für PIN-Eingabe verwendet ISO 13491 entsprechen-1:1998 Bankgeschäfte--Secure kryptografische Geräte (Einzelhandel) Teil 1: Konzepte, Anforderungen sowie zur Verfügung.
 

### <a name="deviceinputsmartcardreadersmartcardservice"></a>Device.Input.SmartCardReader.SmartCardService

*Nach dem Einfügen einer Smartcard in einen Leser, müssen die Smartcard-Dienst starten.*

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

Nach einer Smartcard in den Smartcard-Leser eingefügt wird, muss die Smartcard-Dienst gestartet werden.

**Unternehmensvorgabe**

Dies ist notwendig für die Zuverlässigkeit der Smartcard-Funktion.

### <a name="deviceinputsmartcardreadersupports258and259bytepackets"></a>Device.Input.SmartCardReader.Supports258And259BytePackets

*Ein Leser muss 258-Byte-Paketen in T = 0 und 259-Byte-Paketen in T = 1 unterstützen.*

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

Smartcard-Leser muss in einer einzigen Übertragung den Austausch von Folgendes unterstützen:

-   .258-Byte-Paketen in T = 0; d. h., Wörter Daten 256 Byte plus den zwei Status SW1 und SW2.

-   259-Byte-Paketen in T = 1; d. h., code 254 Bytes Informationen plus Knotenadresse, Paket-Steuerelement Bytes, Länge und zwei Fehlersuche Bytes.

### <a name="deviceinputsmartcardreadersupportsdirectandinverseconvention"></a>Device.Input.SmartCardReader.SupportsDirectAndInverseConvention

*Smartcard-Leser muss direkte und Umkehrung Convention Smartcard-Unterstützung.*

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

Smartcard-Leser muss direkte und Umkehrung Convention effizient Karten in der Hardware oder im Betriebssystemtreiber unterstützen.
 

### <a name="deviceinputsmartcardreadersupportsinsertionandremovalmonitor"></a>Device.Input.SmartCardReader.SupportsInsertionAndRemovalMonitor

*Smartcard einfügen und entfernen, muss ein Leser unterstützen überwachen.*

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

Smartcard-Leser muss erkennen und Melden von Smartcard-einfügungen und entfernten ohne Benutzereingriff nicht entfernen oder Smartcard selbst einfügen können. Der Leser muss einen Interrupt Mechanismus verwenden, um die Smartcard einfügen oder entfernen auf das System aufzuzeichnen. Eine Treiber Abruf-Methode zum Erkennen von Hinzufüge- und Smartcard-Einfügung ist nicht auf diese Anforderung erfüllen Weise zulässig.
 

### <a name="deviceinputsmartcardreadersupportsminclockfrequency"></a>Device.Input.SmartCardReader.SupportsMinClockFrequency

*Smartcard-Leser muss eine minimale Taktrate 3.5795 MHz Häufigkeit unterstützen.*

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

Smartcard-Leser muss eine minimale Taktrate Häufigkeit von 3.5795 MHz unterstützen.
 

### <a name="deviceinputsmartcardreadersupportsmindatarateof9600bps"></a>Device.Input.SmartCardReader.SupportsMinDataRateOf9600bps

*Ein Smar Karte Reader muss eine minimale Datenrate von 9600 Bit/s unterstützt.*

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

Smartcard-Leser muss können zum Übertragen von Daten mit einer Rate von 9600 Bit/s oder höher sein.

### <a name="deviceinputsmartcardreadersupportsnegotiableandspecificmodes"></a>Device.Input.SmartCardReader.SupportsNegotiableAndSpecificModes

*Ein Leser muss aushandelbar und bestimmten Modi gemäß der Spezifikation ISO/IEC unterstützen.*

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

Unterstützung von mehreren-Protokoll Smart-Karten und Smart-Karten, die höhere Datenübertragungsraten und höhere Uhr Frequenzen verwenden, muss der Leser aushandelbar und bestimmten Modi gemäß der Spezifikation ISO/IEC 7816-3 (1997-12 bis 15) Abschnitte 5.4 und 7 unterstützen.
Der **Power-** Befehl für ISO 7816-3 ist optional, aber der Befehl **Zurücksetzen** ist erforderlich.
PT ist nicht erforderlich.
 

### <a name="deviceinputsmartcardreadersupportsresetcommand"></a>Device.Input.SmartCardReader.SupportsResetCommand

*Smartcard-Leser muss den Befehl Zurücksetzen unterstützen.*

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

Smartcard-Leser, muss gemäß der Hardware oder der Treiber die asynchrone Protokolle T = 0 und T = 1 unterstützen. Beide Protokolle müssen vollständig unterstützt werden. Smartcard-Leser und der Treiber müssen Karten unterstützen, die beide Protokolle behandeln können. Unterstützung ist nicht für andere Protokolle als T = 0 und T = 1 erforderlich.
Die folgenden Protokollregeln gelten für das Protokoll T = 1:

-   Eine Übertragung wird definiert, wie das Senden eines Befehls auf eine Smartcard mit mindestens einen T = 1 blockiert und empfangen die entsprechende Antwort mithilfe einer, oder weitere T = 1 Blöcke als in ISO/IEC 7816-3 definiert.

-   Für Karten, die IFSC Anfragen zu unterstützen, muss die erste Übermittlung nach dem Zurücksetzen der Smartcard mit einer Anforderung IFSD beginnen, wie in der Spezifikation ISO/IEC 7816-3, unterzeichnet ist 1, Abschnitt 9.5.1.2 definiert.

-    Für Karten, die keine für eine Anforderung IFSD Unterstützung (d. h., die Karte antwortet sich einen R-Block ein, der angibt, "Anderer Fehler"), muss die Übertragung einen I-Block fortgesetzt.

-   Nach einer erfolgreichen RESYNCH Anforderung muss die Übertragung beginnend mit dem ersten Block neu starten, die Übertragung ursprünglich gestartet.

 

### <a name="deviceinputsmartcardreaderusbccidcomplieswithusbdeviceclassspec"></a>Device.Input.SmartCardReader.UsbCcidCompliesWithUsbDeviceClassSpec

*USB-Smartcard-Leser CCID muss USB-Gerät klassenspezifikation für USB-Chip/Smart Card-Schnittstelle Geräte entsprechen.*

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

Wenn der Leser USB-Konnektivität unterstützt, ist CCID erforderlich. Um sicherzustellen, dass USB-Smartcard-Leser mit der USB-Hostcontroller ordnungsgemäß funktionsfähig, Smartcard CCID Leser USB-Geräteklasse entsprechen: Smartcard-Spezifikation für Integrated Circuit(s) Karten Schnittstelle Geräte, Revision 1.00 oder höher.

### <a name="deviceinputsmartcardreaderusbccidissuesnak"></a>Device.Input.SmartCardReader.UsbCcidIssuesNak

*Ein USB CCID Reader muss eine NAK über eine Pipe Interrupt ausstellen, ein Gerät hat keine Interrupt Daten übertragen.*

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

USB-CCIDs muss ein NAK über eine Pipe Interrupt ausgestellt werden, wenn der Status ändert. Dadurch wird die Notwendigkeit des wiederholt das Gerät zum Status abzufragen.

*Hinweise zum Entwurf*

USB-Chip/Smart Card-Schnittstelle Geräte, Revision 1.00 oder höher, Kapitel 3 finden Sie unter USB-Gerät klassenspezifikation. Finden Sie unter USB-Spezifikation, Version 1.1 oder höher, 5.7.4 und 8.5.4 Abschnitte.

