---
title: Device.BusController.I2C
Description: "Anforderungen nur für I2C Controller Halbleiterhersteller. System Hersteller können optional diese Tests ausgeführt, aber möglicherweise Hardware Anpassung."
ms.assetid: 
MSHAttr: 
author: beneluxboy
ms.openlocfilehash: 32b50a6eb2c7911f4639b2dc51de8bdd9bb1f0ff
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
<!--
# Device.BusController.I2C
 - [Device.BusController.I2C](#device.buscontroller.i2c)
-->

<a name="device.buscontroller.i2c"></a>
##Device.BusController.I2C

*Diese Anforderungen gelten nur für I2C Controller Halbleiterhersteller. System Hersteller möglicherweise optional diese Tests ausgeführt, aber möglicherweise Customization Hardware erforderlich.*

### <a name="devicebuscontrolleri2ccancellationofio"></a>Device.BusController.I2C.CancellationOfIO

*I2C Controller und Controller-Treiber müssen das Abbrechen des e/a-Anforderungen unterstützt.*

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

Der I2C Controller und der zugeordneten Controller-Treiber müssen entsprechen dem SP b-Framework und unterstützen Folgendes:

-   Treiber implementiert SP b Anforderung Stornierung Logik für Lese-/Schreibzugriff/Sequenz e/a.

### <a name="devicebuscontrolleri2cclockstretching"></a>Device.BusController.I2C.ClockStretching

*I2C Controller und Controller-Treiber müssen peripherer Uhr Strecken unterstützen.*

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

Der I2C Controller und der zugeordneten Controller-Treiber müssen entsprechen dem SP b-Framework und unterstützen Folgendes:

-   Controller kann für mindestens 2 Sekunden während lesen, schreiben und e/a Sequenz peripherer Betrieb Uhr tolerieren.

### <a name="devicebuscontrolleri2chcktestability"></a>Device.BusController.I2C.HCKTestability

*Systeme mit I2C Controller müssen Angaben ACPI Tabelle und I2C Pin-Outs HCK Prüfbarkeit aktivieren verfügbar machen.*

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

Das Ziel dieser Anforderung ist zum Aktivieren des Controllers vom Framework HCK getestet werden sollen.

Details:

-   Controller getesteten muss I2C externe Konnektivität Pin skalierten (SCL-Bewertung, SDA und GND) bereitstellen.

-   Aktualisieren Sie ACPI um HCK Test peripherer Faktoren und seiner Verbindung zu I2C Controller getesteten ordnungsgemäß zu beschreiben.

-   Anderer Peripheriegeräte auf demselben I2C Controller getesteten müssen beim Ausführen von HCK deaktiviert werden.

### <a name="devicebuscontrolleri2cidlepowermanagement"></a>Device.BusController.I2C.IdlePowerManagement

*I2C Controller und Controller-Treiber müssen im Leerlauf Power Management unterstützen.*

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

Der I2C Controller und der zugeordneten Controller-Treiber müssen entsprechen den SP b-Framework und unterstützen Folgendes:

-   Controller sollte auf den Status D3 eingefügt werden, nachdem er für mehr als 1 Sekunde im Leerlauf Wenn sich ist auf der Bildschirm befindet.

-   Controller sollte auf den Status D3 nach im Leerlauf für mehr als 100 ms wechseln Sie bei der Bildschirm deaktiviert ist.

-   Controller übernimmt 75 ms (50 + 25-Konto für den Timer Granularität von 15ms) aus dem Status D3 auf den Status D0 fortgesetzt.

### <a name="devicebuscontrolleri2clockunlockioctl"></a>Device.BusController.I2C.LockUnlockIOCTL

*I2C Controller und Controller-Treiber müssen die Sperren/Entsperren IOCTL unterstützen.*

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

Wenn die Bedingung Stop unterstützt wird, müssen den I2C Controller und zugeordneten Controllertreiber entsprechen der SP b-Framework und unterstützen Folgendes:

-   Eine beliebige Anzahl von Lese-/Schreibvorgänge im Sperren/Entsperren-Paar unterstützt.

-   Generieren der Startbedingung für die erste e/a in der Reihenfolge Sperren/Entsperren die Bedingung neu starten, für nachfolgende e/a und die Bedingung Stop Unlock aufgerufen wird.

### <a name="devicebuscontrolleri2cnack"></a>Device.BusController.I2C.NACK

*I2C Controller und Controller-Treiber müssen peripherer NACK unterstützen.*

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

Den I2C Controller und den zugeordneten Controller-Treiber müssen entsprechen den SP b-Framework und unterstützen Folgendes:

-   Controller kann Adresse NACK Bus-Bedingung erkennen und Rückgabestatus\_NO\_ENTSPRECHENDE\_GERÄT für Anforderung.

-   Controller Gerät NACK während ein Schreibvorgang erkennen können, führen Sie die Anforderung mit dem STATUS\_ERFOLG, und Informationen Bytes wird festgelegt, um eine Anzahl von Bytes, die kleiner als Was wurde geschrieben werden soll.

-   Controller Gerät NACK während ein Schreibvorgang einer Sequenz IOCTL erkennen können, führen Sie die Anforderung mit dem STATUS\_ERFOLG, und Informationen Bytes auf Anzahl von Bytes, die kleiner als was geschrieben werden soll, wurde festgelegt ist.

### <a name="devicebuscontrolleri2cspbread"></a>Device.BusController.I2C.SPBRead

*I2C Controller und Controller-Treiber müssen ordnungsgemäß SP b Lesevorgänge unterstützen.*

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

Den I2C Controller und den zugeordneten Controller-Treiber müssen entsprechen den SP b-Framework und unterstützen Folgendes beim Lesen von Daten aus einer I2C Peripheriegeräte:

-   Lesen von Standard (100 Kbit/s), Fast (400 Kbit/s) und plus (1 Mbit/s) fast peripherer Ziele müssen unterstützt werden. Hochgeschwindigkeits (3.4 MHz) ist optional, aber alle HCK Anforderungen für I2C muss übergeben werden, wenn in der I2C Controller und Controller-Treiber implementiert.

-   Unterstützung lesen Größe von 1 auf 4096 Byte (4 KB).

-   Größer als 4 KB müssen oder trat ein Fehler auftritt, mit dem STATUS\_NICHT\_UNTERSTÜTZT.

-   SP b lesen ist in Start, Read Data, NACK und beenden I2C Bedingungen zugeordnet.

-   Alle nicht unterstützte Datengröße lesen Anforderung mit dem STATUS fehl\_UNGÜLTIGE\_PARAMETER nicht dazu, dass alle Aktivitäten Bus.

### <a name="devicebuscontrolleri2cspbsequenceioctl"></a>Device.BusController.I2C.SPBSequenceIOCTL

*I2C Controller und Controller-Treiber müssen SP b Sequenz IOCTL ordnungsgemäß unterstützen.*

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

Der I2C Controller und der zugeordneten Controller-Treiber müssen entsprechen dem SP b-Framework und unterstützen Folgendes:

-   Unterstützt jede beliebige e/a-Sequences: Write Lese-, Schreib-/ Lesezugriff Write-schreiben, lesen-Lesevorgang und komplexe kombiniert wie etwa schreiben-Read-Write-schreibgeschützt

-   SP b Sequenz IOCTL in Start, e/a-Sequenz 1, Restart...I/O Sequenz N, beenden I2C Bedingungen zugeordnet ist.

-   Controller die Sequenz untersuchen und zu bestimmen, ob es unterstützt wird oder ein Fehler auftritt, mit dem STATUS muss\_UNGÜLTIGE\_-PARAMETER vor dem Bus Aktivitäten verursacht.

-   Eine beliebige gültige Parameter (z. B. DelayInUs) und Speicherformat unterstützen (EINFACH, MDL, Puffer-Liste usw.) gemäß Definition von SP b.

### <a name="devicebuscontrolleri2cspbwrite"></a>Device.BusController.I2C.SPBWrite

*I2C Controller und Controller-Treiber müssen SP b schreiben Vorgänge ordnungsgemäß unterstützen.*

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

Der I2C Controller und der zugeordneten Controller-Treiber müssen entsprechen den SP b-Framework und beim Schreiben in eine I2C Peripheriegeräte Folgendes unterstützen:

-   Muss Schreibvorgänge Standard (100 Kbit/s), Fast (400 Kbit/s) und plus (1 Mbit/s) fast peripherer Ziele unterstützen. Hochgeschwindigkeits (3.4 MHz) ist optional, aber alle HCK Anforderungen für I2C muss übergeben werden, wenn in der I2C Controller und Controller-Treiber implementiert.

-   Support muss Größe von 1 in 4096 Byte (4 KB) geschrieben werden.

-   Größer als 4 KB müssen oder trat ein Fehler auftritt, mit dem STATUS\_NICHT\_UNTERSTÜTZT.

-   SP b schreiben ist in Start, Write Data und beenden I2C Bedingungen zugeordnet.

-   Alle unterstützten Daten Größe Write-Anforderung mit dem STATUS schlägt fehl\_UNGÜLTIGE\_PARAMETER nicht dazu, dass alle Aktivitäten Bus.

### <a name="devicebuscontrolleri2cstress"></a>Device.BusController.I2C.Stress

*I2C Controller und Controller-Treiber ordnungsgemäß ausgeführt werden müssen, und von Bus hängt oder Seitenfehler längerer Belastung wiederhergestellt.*

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

Der I2C Controller und der zugeordneten Controller-Treiber müssen entsprechen dem SP b-Framework und unterstützen Folgendes:

-   Unterstützt Bus-Wiederherstellung, wenn Peripheriegeräte (Watchdog-Mechanismus) reagiert.

-   Tolerieren Sie mehrere Ziele Stress für mehr als 1 Stunde.
