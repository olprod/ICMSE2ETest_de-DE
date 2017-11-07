---
title: Device.BusController.UART
Description: "Die Anforderungen nur für Halbleiterhersteller. UART Controller-Treiber werden empfohlen, SerCXV2."
ms.assetid: 
MSHAttr: 
author: beneluxboy
ms.openlocfilehash: 60f64db8d7497c59ef986b95f5d340c767802ad5
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
<!--
# Device.BusController.UART
 - [Device.BusController.UART](#device.buscontroller.uart)
-->

<a name="device.buscontroller.uart"></a>
##Device.BusController.UART

Die Anforderungen gelten nur für Halbleiterhersteller. UART Controller-Treiber werden empfohlen, SerCXV2.

### <a name="devicebuscontrolleruartcancellation"></a>Device.BusController.UART.Cancellation

*UART Controller und Controller-Treiber müssen den Abbruch der Lese- und Schreibvorgang Anforderungen unterstützen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
</td></tr></table>

**Beschreibung**

Der UART Controller und der zugeordneten Controller-Treiber müssen das serielle Framework entsprechen und unterstützt die folgenden:

-   Controller implementiert erforderlichen Logik zur Unterstützung von e/a-Abbruch

### <a name="devicebuscontrolleruartdma"></a>Device.BusController.UART.DMA

*UART Controller und Controller-Treiber ist DMA-Unterstützung für den entsprechenden DMA Transaktionen erforderlich.*

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

Der UART Controller und der zugeordneten Controller-Treiber müssen das serielle Framework entsprechen und unterstützt die folgenden:

-   Peripherer Treiber kann Problem lesen und Schreiben Anforderung an den Controller max in 5 K Datengröße.

### <a name="devicebuscontrolleruartflowcontrol"></a>Device.BusController.UART.FlowControl

*UART Controller und Controller-Treiber müssen die Einstellung des Steuerelements Ablauf zum ein- und ausschalten unterstützen.*

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

Der UART Controller und der zugeordneten Controller-Treiber müssen das serielle Framework entsprechen und unterstützt die folgenden:

-   Treiber implementiert die Unterstützung für IOCTL\_SERIELLEN\_ABRUFEN\_HANDFLOW und IOCTL\_SERIELLEN\_FESTLEGEN\_HANDFLOW IOCTLs und Flussdiagramm Einstellungen steuern

### <a name="devicebuscontrolleruartflushfifo"></a>Device.BusController.UART.FlushFIFO

*UART Controller und Controller-Treiber müssen leeren FIFOs unterstützen.*

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

Der UART Controller und der zugeordneten Controller-Treiber müssen das serielle Framework entsprechen und unterstützen die Möglichkeit zum Leeren der FIFO Warteschlangen.

### <a name="devicebuscontrolleruartguardbuffer"></a>Device.BusController.UART.GuardBuffer

*UART Controller und zugeordneten Controller-Treiber müssen erkennen und korrigieren Sie des Guard-Puffers Überlauf und Unterlauf.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
</td></tr></table>

**Beschreibung**

Der UART Controller und der zugeordneten Controller-Treiber müssen das serielle Framework entsprechen, und sollte nicht in den Speicher außerhalb der Übertragung Puffer geschrieben werden. Beispielsweise wenn ein Datenpuffer Übertragung 1KB für eine Lese-zugewiesen wird, muss die Datenübertragung UART nicht in Speicher außerhalb der 1 KB Puffer geschrieben werden. Für diese Anforderung wurde ein Test um zu ermitteln, ob der Speicher außerhalb der Übertragung-Puffer überschrieben wurde hinzugefügt. Wenn die Übertragung abgeschlossen ist, wird den Besitz des Übertragungspuffers an die Anwendung zu testen übergeben. Der Test überprüft anschließend, dass der Übertragung Pufferspeicher nicht geändert werden kann, um sicherzustellen, dass der Puffer nicht überschrieben wird.

### <a name="devicebuscontrolleruarthcktestability"></a>Device.BusController.UART.HCKTestability

*Systeme mit UART Controller müssen Angaben ACPI Tabelle und UART Pin-Outs HCK Prüfbarkeit aktivieren verfügbar machen.*

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

Das Ziel dieser Anforderung ist zum Aktivieren des UART Controllers von HCK Framework getestet werden sollen.

Details:

-   Controller testenden muss UART externe Konnektivität Pin skalierten (Rx, Tx, RTS, CTS und GND) bereitstellen.

-   Beschreiben Sie HCK UART Test peripherer Treiber und seiner Verbindung zu UART Controller testenden in der Firmware des Geräts an.

### <a name="devicebuscontrolleruartidlepowermanagement"></a>Device.BusController.UART.IdlePowerManagement

*UART Controller und Controller-Treiber müssen im Leerlauf Power Management unterstützen.*

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

Der UART Controller und der zugeordneten Controller-Treiber müssen das serielle Framework entsprechen und unterstützt die folgenden:

-   Controller Übergänge in den Zustand Dx, wenn keine ausstehende e/a in der Controller für 200 ms vorhanden ist.

### <a name="devicebuscontrolleruartperformance"></a>Device.BusController.UART.Performance

*UART Controller und Controller-Treiber hat eine gemessene Baudrate, die mit der erwartete Wert übereinstimmt.*

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

Die UART Controller und zugeordneten Controller-Treiber müssen das serielle Framework entsprechen, dass die gemessene Baudrate der erwartete Wert übereinstimmt.

### <a name="devicebuscontrolleruartreadwrite"></a>Device.BusController.UART.ReadWrite

*UART Controller und Controller-Treiber müssen Lese-/Schreibzugriff Unicode(8 bits) Daten unterstützen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
</td></tr></table>

**Beschreibung**

Der UART Controller und der zugeordneten Controller-Treiber müssen das serielle Framework entsprechen und beim Lesen von Daten aus einer UART Peripheriegeräte Folgendes unterstützen:

-   Unterstützen IOCTL\_SERIELLEN\_FESTLEGEN\_ZEILE\_STEUERELEMENT und IOCTL\_SERIELLEN\_ABRUFEN\_ZEILE\_STEUERELEMENT, und kann zum Übertragen von Daten entsprechend den Daten Länge (8-Bit).

### <a name="devicebuscontrolleruartstress"></a>Device.BusController.UART.Stress

*UART Controller und Controller-Treiber ordnungsgemäß funktioniert (und diesen entsprechend aus Bus-Fehler) Belastung.*

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

Der UART Controller und der zugeordneten Controllertreiber müssen entsprechen den seriellen Framework und unterstützen Folgendes:

-   Tolerieren Sie Stress Testdurchläufe mindestens 1 Stunde.

### <a name="devicebuscontrolleruartsupportedbaudrates"></a>Device.BusController.UART.SupportedBaudRates

*UART Controller und Controller-Treiber müssen grundlegende Baudrate 115200 und schneller für höhere Bandbreite Kommunikation unterstützen.*

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

Der UART Controller und der zugeordneten Controller-Treiber müssen das serielle Framework entsprechen und unterstützt die folgenden:

-   Treiber unterstützt IOCTL\_SERIELLEN\_FESTLEGEN\_BAUD\_ZINSSATZ sowie IOCTL\_SERIELLEN\_ABRUFEN\_BAUD\_IOCTL RATE.

-   Treiber für nicht unterstützte Baudrate Baudrate sollte fehlschlagen und ist in der Lage e/a mit der Baud Rate-Gruppe ausführen.

