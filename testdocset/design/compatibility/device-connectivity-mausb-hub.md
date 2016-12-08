---
title: Device.Connectivity.MAUSB.Hub
Description: "Anforderungen gelten für MA-USB-Hubs. Allerdings MA-USB-Anforderungen sind derzeit optional und werden nicht erzwungen, bis 2017."
ms.assetid: 
MSHAttr: 
author: beneluxboy
ms.openlocfilehash: 5afa1d76015e624c36d7ad7565c44d827d2ae1c5
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
<!--
# Device.Connectivity.MAUSB.Hub

 - [Device.Connectivity.MAUSB.Hub ](#device.connectivity.mausb.hub)
-->

<a name="device.connectivity.mausb.hub"></a>
##Device.Connectivity.MAUSB.Hub 

Die folgenden Anforderungen gelten für MA-USB-Hubs

MA-USB-Anforderungen sind derzeit optional und werden nicht erzwungen, bis 2017.

### <a name="deviceconnectivitymausbhubbulkoutbuffersize"></a>Device.Connectivity.MAUSB.Hub.BulkOutBufferSize

*MA-USB-Hubs müssen mindestens 64 KB Pufferspeicherplatz pro nicht SuperSpeed Massen, Endpunkte und mindestens 512 KB Pufferspeicherplatz pro SuperSpeed Massen Out Endpunkte unterstützen.*

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

MA-USB-Anforderungen sind derzeit optional und werden nicht erzwungen, bis 2017.

MA-USB-Hubs muss zuverlässig und für eine optimale Leistung (Durchsatz) arbeiten können, um diese minimale Puffergrößen unterstützen. Diese Puffergrößen werden durch MA-USB-Spezifikation v1.0a, Abschnitt 6.3.7 beschrieben vom MA-USB-Hub in das Endpunkt Antwortpaket gemeldet.

-   SuperSpeed Massen Out - 512KB

-   nicht SuperSpeed Massen Out - 64KB

### <a name="deviceconnectivitymausbhubidentifynumofuseraccessibleports"></a>Device.Connectivity.MAUSB.Hub.IdentifyNumOfUserAccessiblePorts

*Ein Verwaltungs-Agent-USB-Hub muss ordnungsgemäß identifizieren und melden der Anzahl der Ports, die der Benutzer zugreifen kann.*

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

MA-USB-Anforderungen sind derzeit optional und werden nicht erzwungen, bis 2017.

Der integrierte USB 2.0/3.1 Hub muss Details in seiner Hub Deskriptor, die genaue Anzahl der Anzahl von downstream-seitige und Ports, der Hub unterstützt, die verfügbar gemacht werden, die dem Benutzer das Betriebssystem bereitstellen enthalten. Finden Sie unter USB-Spezifikation, Version 2.0, Section11.23 und USB-3.0-Spezifikation, Abschnitt 10.14.

### <a name="deviceconnectivitymausbhubipmode"></a>Device.Connectivity.MAUSB.Hub.IPMode

*MA-USB-Hubs müssen Support für IP-Modus implementieren.*

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

MA-USB-Anforderungen sind derzeit optional und werden nicht bis 2017 erzwungen werden.

MA-USB-Hubs implementieren müssen die Unterstützung für IP-Modus als der angegebene in der MA-USB-Spezifikation v1.0a, Abschnitt 4.5.3.2 "Anforderungen für IP-Modus"

### <a name="deviceconnectivitymausbhubmausbspeccompliance"></a>Device.Connectivity.MAUSB.Hub.MAUSBSpecCompliance

*MA-USB-Hubs muss USB-IF-Spezifikation kompatibel*

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

MA-USB-Anforderungen sind derzeit optional und werden nicht erzwungen, bis 2017.

MA-USB-Hubs muss mit MA-USB-Spezifikation v1.0a kompatibel oder höher sein.

### <a name="deviceconnectivitymausbhubsupportsuspend"></a>Device.Connectivity.MAUSB.Hub.SupportSuspend

*MA-USB-Hubs unterstützen müssen angehalten werden soll, und downstream-Geräte müssen nicht aus dem Bus ablegen, beim Hub aus Suspend fortgesetzt.*

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

MA-USB-Anforderungen sind derzeit optional und werden bis 2017 nicht erzwungen werden.

MA USBhubs MA-USB-unterstützen muss angehalten werden soll. Nachdem Sie einen Verwaltungs-Agent-USB-Hub von fortgesetzt wird suspend-Zustand, alle Geräte, die downstream angefügt wurden von integrierte USB 2.0/3.1 Hub und, nicht entfernt wurden während der Hub wurde angehalten, muss vorhanden sein.

Integrierte USB 2.0/3.1 Hubs USB unterstützen muss angehalten werden soll. Nachdem ein integrierter USB 2.0/3.1 Hub aus alle Geräte USB aussetzen fortgesetzt wird, die downstream angefügt wurden von integrierte USB 2.0/3.1 Hub- and -, die nicht entfernt wurden während der integrierte USB 2.0/3.1 Hub wurde angehalten, muss vorhanden sein.

### <a name="deviceconnectivitymausbhubsupportswifidirectandwsb"></a>Device.Connectivity.MAUSB.Hub.SupportsWiFiDirectAndWSB

*MA-USB-Hubs unterstützen direkte WLAN-Verbindung und WiFi Serial Bus*

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

MA-USB-Anforderungen sind derzeit optional und werden nicht erzwungen, bis 2017.

Implementierung von Netzwerk-Verwaltungs-Agent-USB-Hub muss zuverlässig entwickelt Posteingang Windows MA-USB-Host die folgenden Anforderungen erfüllen.

-   MA-USB-Hub-Gerät muss unterstützen direkte Wi-Fi-Services (Peer zu Peer Services 1.x) über eine 802. 11n / Ac und/oder 802.11ad NIC

    -   Verschiebt wahrscheinlich asp2 (Wi-Fi direkte Ermittlung und verbinden)

-   MA-USB-Hub-Gerät muss WSB v0.18 implementieren&lt;neueste&gt; als ein Werbekunden

### <a name="deviceconnectivitymausbhubtcpimplementation"></a>Device.Connectivity.MAUSB.Hub.TCPImplementation

*MA-USB-TCP-Implementierung für Zuverlässigkeit*

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

MA-USB-Anforderungen sind derzeit optional und werden nicht erzwungen, bis 2017.

TCP-Implementierung der MA-USB-Hub muss die folgenden Anforderungen Posteingang Windows MA-USB-Host zuverlässig entwickelt erfüllen:

-   TCP verzögerte Bestätigung Optimierung muss deaktiviert werden.

-   TCP Nagle-Algorithmus-Implementierung muss deaktiviert werden.

-   TCP muss mindestens 64 KB empfangen Pufferspeicherplatz bereitstellen.

### <a name="deviceconnectivitymausbhubusb3hubcomplieswithusb3spec"></a>Device.Connectivity.MAUSB.Hub.Usb3HubCompliesWithUsb3Spec

*Integrierte 3.1 USB-Hubs sind kompatibel mit der Spezifikation USB 3.1.*

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

MA-USB-Anforderungen sind derzeit optional und werden nicht erzwungen, bis 2017.

Integrierte 3.1 USB-Hubs müssen mit *der* Universal Serial Bus (USB) 3.1 Spezifikation kompatibel sein. 

Integrierte 3.1 USB-Hubs müssen:

-   Übergeben Sie den USB-Tests der IF-Interoperabilität

-   Übergeben Sie die USB-3.1 Hub Compliance Testsammlung

-   Übergeben Sie den USB-3.1 KA-test

### <a name="deviceconnectivitymausbhubusb3reportportstatusbitscorrectly"></a>Device.Connectivity.MAUSB.Hub.Usb3ReportPortStatusBitsCorrectly

*Integrierte 3.1 USB-Hubs müssen immer die Port Statusbits richtig gemäß den Anweisungen in der Spezifikation USB 3.1 melden.*

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

MA-USB-Anforderungen sind derzeit optional und werden nicht erzwungen, bis 2017.

Eine Reihe von ungültigen Portstatus bit in der aktuellen Stack Kombinationen, dass die Hub-Berichte ignoriert werden. Ungültige Kombinationen von Bits an Port Status wird als Fehler behandelt werden. Insbesondere werden Überprüfungen diese Aktionen folgen:

-   Zurücksetzen eines Ports

-   Anhalten und Fortsetzen eines Ports

-   System fortsetzen

Eine integrierte USB-Hub 3.1 sollten nicht falsche Änderung Interrupts melden.

