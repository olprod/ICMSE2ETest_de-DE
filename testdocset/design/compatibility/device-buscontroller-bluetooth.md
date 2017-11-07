---
title: Device.BusController.Bluetooth
Description: Requirements.
ms.assetid: 
MSHAttr: 
author: beneluxboy
ms.openlocfilehash: ba1aeb4d788cacf839032c3e1131730c897b4e1c
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="devicebuscontrollerbluetooth"></a>Device.BusController.Bluetooth

 - [Device.BusController.Bluetooth.Base](#device.buscontroller.bluetooth.base)
 - [Device.BusController.Bluetooth.NonUSB](#device.buscontroller.bluetooth.nonusb)
 - [Device.BusController.Bluetooth.USB](#device.buscontroller.bluetooth.usb)

<a name="device.buscontroller.bluetooth.base"></a>
## <a name="devicebuscontrollerbluetoothbase"></a>Device.BusController.Bluetooth.Base

### <a name="devicebuscontrollerbluetoothbase4lespecification"></a>Device.BusController.Bluetooth.Base.4LeSpecification

*Bluetooth-Domänencontroller müssen die Anforderungen der Bluetooth-4.0-Spezifikation unterstützen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
</td></tr></table>

**Beschreibung**

Diese Anforderungen für Clientsysteme sind "Wenn implementiert" und gilt nur, wenn ein Clientsystem Bluetooth unterstützt.

*Die grundlegende Rate (Brasilien) und wenig Energie (LE) kombiniert Core Konfiguration Controller Webparts und Host-Controller-Schnittstelle (HCI) Kernkonfiguration Anforderungen beschrieben, die in den Spezifikationen Compliance Bluetooth-Version 4.0 muss der Bluetooth-Controller einhalten.*

*"Der Bluetooth-Radio Hardware wird als"Controller Subsystem"gekennzeichnet sein und kann außerdem als"Komponente"durch die Bluetooth besonders interessant Gruppe gekennzeichnet werden."*

### <a name="devicebuscontrollerbluetoothbaselestatecombinations"></a>Device.BusController.Bluetooth.Base.LeStateCombinations

*Bluetooth-Domänencontroller müssen einen minimalen Satz von LE Zustand Kombinationen unterstützen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
</td></tr></table>

**Beschreibung**

Der Bluetooth-Controller muss die Spec LE Zustand Kombinationen zulassen (wie im Abschnitt zulässig \[Lautstärke 6\] Teil B, Abschnitt 1.1.1 der Spezifikation Version 4.0 Bluetooth): nur die folgenden Zustände nicht unterstützt werden müssen:

-   0x0000000000800000 aktiv Überprüfung und Initiating Zustand Kombination unterstützt.

-   die passive Überprüfung 0x0000000004000000-Status und untergeordnete Rolle Kombination unterstützt.

-   0x0000000008000000 aktive Scannen Zustand und untergeordnete Rolle Kombination unterstützt.

### <a name="devicebuscontrollerbluetoothbaselewhitelist"></a>Device.BusController.Bluetooth.Base.LeWhiteList

*Bluetooth-Domänencontroller müssen eine minimale LE weiße Listengröße von 25 Einträge unterstützen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
</td></tr></table>

**Beschreibung**

Der Bluetooth-Controller muss mindestens 25 Einträge in der Liste weiß für remote niedrig Energie (LE) Geräte unterstützen.

### <a name="devicebuscontrollerbluetoothbasemicrosoftbluetoothstack"></a>Device.BusController.Bluetooth.Base.MicrosoftBluetoothStack

*Bluetooth-Controller müssen mithilfe von Microsoft Bluetooth-Stack getestet werden.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
</td></tr></table>

**Beschreibung**

Beim Einreichen für die Hardwarezertifizierung, müssen die Bluetooth-Controller mit Bluetooth-Stapel von Microsoft getestet werden.

### <a name="devicebuscontrollerbluetoothbasehciextensions-if-implemented"></a>Device.BusController.Bluetooth.Base.HCIExtensions (sofern implementiert)

*Microsoft definiert HCI Extensions Unterstützung für Hardware-Offloading Werbung und RSSI monitoring.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
</td></tr></table>

**Beschreibung**

Sender, die die Microsoft unterstützen definiert Bluetooth HCI Erweiterungen der Spezifikation entsprechen und übergeben Sie die zugehörigen HLK Tests müssen. Die Details der Spezifikationen befinden sich auf MSDN. Finden Sie in der nachstehenden Links

[https://msdn.Microsoft.com/en-us/library/Windows/Hardware/dn917903.aspx.](https://msdn.microsoft.com/en-us/library/windows/hardware/dn917903.aspx)

### <a name="devicebuscontrollerbluetoothbasenobluetoothlefilterdriver"></a>Device.BusController.Bluetooth.Base.NoBluetoothLEFilterDriver

*Bluetooth-LE Filtertreiber dürfen nicht auf BTHLEENUM laden. SYS.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
</td></tr></table>

**Beschreibung**

Um eine einheitliche Erfahrung über Windows Store-Apps mithilfe der Bluetooth-LE (GATT) WinRT-API zu gewährleisten, müssen Filtertreiber nicht auf BTHLEENUM geladen werden. SYS.

### <a name="devicebuscontrollerbluetoothbaseonoffstatecontrollableviasoftware"></a>Device.BusController.Bluetooth.Base.OnOffStateControllableViaSoftware

*Bluetooth-Controller ein-/ausschalten Zustand muss über Software gesteuert.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
</td></tr></table>

**Beschreibung**

Beim aktivieren das Optionsfeld "off" und müssen Bluetooth-Controller nach unten zu den niedrigsten unterstützten Power Zustand eingeschaltet und keine Übertragung/Empfang erfolgt. Windows wird durch Entladen der Protokolltreiber Posteingang und ihre untergeordneten Elemente, Senden von der HCI Bluetooth-Aktivität beendet\_Befehl in der Controller und klicken Sie dann auf den D3 logische Power Status, zulassen der Bustreiber Herunterfahren, den Sender entsprechend festlegen des Controllers zurückzusetzen. Vollständig kann der Sender ausgeschaltet werden, wenn eine Methode Bus unterstützt den Sender wieder aktivieren verfügbar ist. Keine zusätzliche Hersteller-Steuerelement Softwarekomponenten werden unterstützt.

Zum Aktivieren den Sender wieder deaktivieren, wird Windows Bluetooth-Stapel das Gerät D0, sodass Bustreiber für das Gerät neu starten fortsetzen. Der Windows Bluetooth-Stack wird die Bluetooth-Komponenten des Controllers klicken Sie dann erneut initialisieren.

Bluetooth-Radio Management in Windows 8.1 wird nur für interne Bluetooth-4.0-Domänencontroller aktiviert sein.

### <a name="devicebuscontrollerbluetoothbasescatternet"></a>Device.BusController.Bluetooth.Base.Scatternet

*Bluetooth-Hostcontroller muss Bluetooth-Scatternet unterstützen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
</td></tr></table>

**Beschreibung**

Bluetooth-Hostcontroller muss mindestens zwei gleichzeitige Piconets (auch bekannt als Scatternet) unterstützen. Der Hostcontroller muss auch der Host auf einem Gerät teilnehmen, die eine Verbindung mit der vorhandenen Piconet aufgefordert wird, wenn das lokale Radio das Master-Shape von dieser Piconet ist möglich sein. Diese Anforderung wird bei der Angabe von der Bluetooth-System, Version 2.1 + Enhanced Data Rate (EDR) (Basisband Specification), Abschnitt 8.6.6 beschrieben. 

Hinweise zum Entwurf: Die Scatternet Unterstützung der erweiterten Scatternet Support fehlerverzeichnis befolgen, die durch die Bluetooth besonders interessant Group (SIG) definiert sind.

### <a name="devicebuscontrollerbluetoothbasesimultaneousbredrandletraffic"></a>Device.BusController.Bluetooth.Base.SimultaneousBrEdrAndLeTraffic

*Bluetooth-Controller müssen gleichzeitige BR/EDR und LE Datenverkehr unterstützen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
</td></tr></table>

**Beschreibung**

Bluetooth-Controller müssen die gleichzeitige Verwendung von grundlegenden Rate BR/Enhanced Data Rate (EDR) und wenig Energie (LE) Sender zulassen.

### <a name="devicebuscontrollerbluetoothbasespecificinformationparameters"></a>Device.BusController.Bluetooth.Base.SpecificInformationParameters

*Bluetooth-Hostcontroller muss bestimmte Informationszwecken-Parameter, um genaue Informationen über den Host des Controllers Funktionen bereitstellen implementieren.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
</td></tr></table>

**Beschreibung**

Der Hersteller behebt die Informationszwecken Parameter, die nützliche Informationen über Bluetooth-Geräts und der Funktionen von den Hostcontroller bereitstellen. Bluetooth-Hostcontroller müssen die Hardwarekompatibilitätsliste implementieren\_lesen\_lokale\_Version\_Befehl Informationen und HCI\_lesen\_lokale\_unterstützte\_Befehl Features gemäß der Spezifikation des Bluetooth-System, Version 2.1 + Enhanced Data Rate (EDR), Teil E, Abschnitt 7.4. Erforderliche Support umfasst Mechanismus für die unterstützte Version und Features reporting.

### <a name="devicebuscontrollerbluetoothbasesupportsbluetooth21andedr"></a>Device.BusController.Bluetooth.Base.SupportsBluetooth21AndEdr

*Bluetooth-Domänencontroller müssen unterstützen, die Bluetooth 2.1 + EDR Spezifikation Anforderungen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
</td></tr></table>

**Beschreibung**

Bluetooth-Hostcontroller muss die Anforderungen entsprechen, die in der Spezifikation der Bluetooth System Version 2.1 + Enhanced Data Rate (EDR) beschrieben werden.

### <a name="devicebuscontrollerbluetoothwidebandspeech-if-implemented"></a>Device.BusController.Bluetooth.WidebandSpeech (sofern implementiert)

<table>
<tr>
<th>Gilt für</th>
<td>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
</td></tr></table>

**Beschreibung**

Breitband Speech ermöglicht Sprachqualität high-Definition (Audio wird gemessen, mit 16 KHz im Gegensatz zu nur 8 KHz) für Telefonie Audio auf Windows-Geräten der Benutzer über eine Bluetooth peripherer Kommunikation, die auch Breitband Sprache unterstützt.

Dies bedeutet, dass Bluetooth-Sender Breitband Speech unterstützen müssen, in der Hardware gemäß Definition durch die Bluetooth SIG [Headset Profil (HFP) 1.6-Spezifikation](https://www.bluetooth.org/docman/handlers/downloaddoc.ashx?doc_id=238193) und [Core Spezifikation Addendum (CSA) 2](https://www.bluetooth.org/docman/handlers/downloaddoc.ashx?doc_id=245127) in der [Version 4.1 Core](https://www.bluetooth.org/DocMan/handlers/DownloadDoc.ashx?doc_id=282159) Bluetooth-Spezifikation enthalten ist. Mindestens muss mindestens ein Bluetooth SIG definierten Breitband Speech Codec (derzeit mSBC) verwendet werden.

**Unternehmensvorgabe:**

Wir möchten, dass Benutzer die beste mögliche Tonqualität-Umgebung zu bieten bei Verwendung von Bluetooth-Peripheriegeräte unter Windows. Ein Standard für Peripheriegeräte, die das Profil HFP unterstützen Breitband Speech gewinnt. Konkurrenz bereits wird unterstützt

<a name="device.buscontroller.bluetooth.nonusb"></a>
## <a name="devicebuscontrollerbluetoothnonusb"></a>Device.BusController.Bluetooth.NonUSB

*Bluetooth-Controller - NonUSB Sender verbunden*

### <a name="devicebuscontrollerbluetoothnonusbperformance"></a>Device.BusController.Bluetooth.NonUSB.Performance

*Nicht-USB-Bluetooth-Controller müssen Sie mindestens einen Durchsatz von 700 KBit/s erreichen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
</td></tr></table>

**Beschreibung**

Nicht-USB-Bluetooth-Controller müssen Sie mindestens einen Durchsatz von 700 KBit/s auf der Ebene RFCOMM erzielen.

### <a name="devicebuscontrollerbluetoothnonusbscosupport"></a>Device.BusController.Bluetooth.NonUSB.ScoSupport

*Nicht-USB-Bluetooth verbunden Domänencontroller müssen den Kanal Sideband für SCO verwenden.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
</td></tr></table>

**Beschreibung**

Um eine hohe Qualität Audioqualität zu gewährleisten, müssen alle nicht-USB-verbunden Bluetooth-Controller für SCO (z. B. SCO über eine Schnittstelle I2S/PCM) einen Sideband Channel verwenden.

<a name="device.buscontroller.bluetooth.usb"></a>
## <a name="devicebuscontrollerbluetoothusb"></a>Device.BusController.Bluetooth.USB

*Bluetooth-Controller - USB Sender verbunden*

### <a name="devicebuscontrollerbluetoothusbscodatatransportlayer"></a>Device.BusController.Bluetooth.USB.ScoDataTransportLayer

*Bluetooth-Hostcontroller müssen der SCO Daten Transportschicht wie angegeben in der Bluetooth 2.1 + EDR Spezifikationen unterstützen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
</td></tr></table>

**Beschreibung**

Bluetooth-Hostcontroller muss mit der synchronen Verbindung orientierten (SCO) einzuhalten-USB-Anforderungen, die in der Spezifikation des Bluetooth-System, Version 2.1 + Enhanced Data Rate (EDR), Teil A beschriebenen Abschnitt 3.5.
