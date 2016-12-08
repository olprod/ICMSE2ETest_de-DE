---
title: Device.Storage
Description: Requirements.
ms.assetid: 
MSHAttr: 
author: beneluxboy
ms.openlocfilehash: 76a99600aaae5125d53387386062ecb471aa3483
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="devicestorage"></a>Device.Storage

 - [Device.Storage.Controller](#device.storage.controller)
 - [Device.Storage.Controller.Ata](#device.storage.controller.ata)
 - [Device.Storage.Controller.AzureStack](#device.storage.controller.azurestack)
 - [Device.Storage.Controller.Boot](#device.storage.controller.boot)
 - [Device.Storage.Controller.Fc](#device.storage.controller.fc)
 - [Device.Storage.Controller.Fc.NPIV](#device.storage.controller.fc.npiv)
 - [Device.Storage.Controller.Fcoe](#device.storage.controller.fcoe)
 - [Device.Storage.Controller.Flush](#device.storage.controller.flush)
 - [Device.Storage.Controller.Iscsi](#device.storage.controller.iscsi)
 - [Device.Storage.Controller.Iscsi.iSCSIBootComponent](#device.storage.controller.iscsi.iscsibootcomponent)
 - [Device.Storage.Controller.Optical](#device.storage.controller.optical)
 - [Device.Storage.Controller.PassThroughSupport](#device.storage.controller.passthroughsupport)
 - [Device.Storage.Controller.Raid](#device.storage.controller.raid)
 - [Device.Storage.Controller.Raid.ContinuousAvailability](#device.storage.controller.raid.continuousavailability)
 - [Device.Storage.Controller.Sas](#device.storage.controller.sas)
 - [Device.Storage.Controller.Sata](#device.storage.controller.sata)
 - [Device.Storage.Controller.SD](#device.storage.controller.sd)
 - [Device.Storage.ControllerDrive.NVMe](#device.storage.controllerdrive.nvme)
 - [Device.Storage.Enclosure](#device.storage.enclosure)
 - [Device.Storage.Enclosure.AzureStack](#device.storage.enclosure.azurestack)
 - [Device.Storage.Hd](#device.storage.hd)
 - [Device.Storage.Hd.1394](#device.storage.hd.1394)
 - [Device.Storage.Hd.Alua](#device.storage.hd.alua)
 - [Device.Storage.Hd.Ata](#device.storage.hd.ata)
 - [Device.Storage.Hd.AtaProtocol](#device.storage.hd.ataprotocol)
 - [Device.Storage.Hd.AzureStack](#device.storage.hd.azurestack)
 - [Device.Storage.Hd.DataVerification](#device.storage.hd.dataverification)
 - [Device.Storage.Hd.Ehdd](#device.storage.hd.ehdd)
 - [Device.Storage.Hd.EMMC](#device.storage.hd.emmc)
 - [Device.Storage.Hd.EnhancedStorage](#device.storage.hd.enhancedstorage)
 - [Device.Storage.Hd.FibreChannel](#device.storage.hd.fibrechannel)
 - [Device.Storage.Hd.Flush](#device.storage.hd.flush)
 - [Device.Storage.Hd.Iscsi](#device.storage.hd.iscsi)
 - [Device.Storage.Hd.Mpio](#device.storage.hd.mpio)
 - [Device.Storage.Hd.MultipleAccess](#device.storage.hd.multipleaccess)
 - [Device.Storage.Hd.MultipleAccess.PersistentReservation](#device.storage.hd.multipleaccess.persistentreservation)
 - [Device.Storage.Hd.OffloadedDataTransfer](#device.storage.hd.offloadeddatatransfer)
 - [Device.Storage.Hd.PersistentReservation](#device.storage.hd.persistentreservation)
 - [Device.Storage.Hd.PortAssociation](#device.storage.hd.portassociation)
 - [Device.Storage.Hd.RaidArray](#device.storage.hd.raidarray)
 - [Device.Storage.Hd.ReadZeroOnTrimUnmap](#device.storage.hd.readzeroontrimunmap)
 - [Device.Storage.Hd.RemovableMedia](#device.storage.hd.removablemedia)
 - [Device.Storage.Hd.Sas](#device.storage.hd.sas)
 - [Device.Storage.Hd.Sata](#device.storage.hd.sata)
 - [Device.Storage.Hd.Sata.HybridInformation](#device.storage.hd.sata.hybridinformation)
 - [Device.Storage.Hd.Scsi](#device.storage.hd.scsi)
 - [Device.Storage.Hd.Scsi.ReliabilityCounters](#device.storage.hd.scsi.reliabilitycounters)
 - [Device.Storage.Hd.ScsiProtocol](#device.storage.hd.scsiprotocol)
 - [Device.Storage.Hd.SMR](#device.storage.hd.smr)
 - [Device.Storage.Hd.ThinProvisioning](#device.storage.hd.thinprovisioning)
 - [Device.Storage.Hd.Trim](#device.storage.hd.trim)
 - [Device.Storage.Hd.Uas](#device.storage.hd.uas)
 - [Device.Storage.Hd.UasOnEHCI](#device.storage.hd.uasonehci)
 - [Device.Storage.Hd.Usb](#device.storage.hd.usb)
 - [Device.Storage.Hd.Usb3](#device.storage.hd.usb3)
 - [Device.Storage.Hd.WindowsToGoCapableUSBDrive](#device.storage.hd.windowstogocapableusbdrive)
 - [Device.Storage.Optical](#device.storage.optical)
 - [Device.Storage.Optical.BluRayReader](#device.storage.optical.blurayreader)
 - [Device.Storage.Optical.BluRayWriter](#device.storage.optical.bluraywriter)
 - [Device.Storage.Optical.Sata](#device.storage.optical.sata)

<a name="device.storage.controller"></a>
## <a name="devicestoragecontroller"></a>Device.Storage.Controller

*Features, die für alle Speichercontroller gilt*

### <a name="devicestoragecontrollerbasicfunction"></a>Device.Storage.Controller.BasicFunction

*Grundlegende Speicherfunktion für Domänencontroller*

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

Controller Grundfunktionen

PCI-basierte Hostcontroller und Adapter müssen unterstützen PCI-Bus mastering als Standardeinstellung und virtuelle direkten Zugriff Arbeitsspeicher (DMA) Services müssen in der Host Adapter Option ROM unterstützt werden

Geräte, die ihre Funktion, ohne andere Registrierung Änderungen vor, außer denen automatisch vom Installationsprogramm Co-Klasse des Geräts ausgeführt nicht möglich sind nicht berechtigt, für die Zertifizierung.

Alle Befehle müssen an die zugrunde liegenden physischen Gerät übergeben werden, wenn der Controller einen RAID-Adapter ist.

Wenn ein Gerät weniger Daten als angefordert zurückgibt, müssen ordnungsgemäß angezeigt werden ein Pufferunterlauf Bedingung und Adapter müssen behandeln diese gemäß den WDK (Anpassen der DataTransferLength).

Nicht-RAID-Controller

Miniporttreiber als RAID-Treiber Pseudogeräte als Ziele für Management Befehle für den Adapter verwendet werden, wenn keine tatsächliche LUNs vorhanden sind möglicherweise nicht erstellt werden. Stattdessen muss eine SCSI-Miniports INF-Geben Sie den Parameter CreateInitiatorLu unter Schlüssel Parameter Services und dieser DWORD-Wert auf 1 festgelegt. Dies kann nicht durchgeführt werden, ein Coinstaller verwenden. Speicher Miniporttreiber führen Sie diesen Parameter nicht verwenden, gemäß der Adapter immer verwendet werden kann, selbst wenn keine Geräte vorhanden sind. Werte für Treiber werden in das WDK dokumentiert.

Die folgenden Storage Controller-Treiber Logo ist, der keinen übereinstimmenden Übermittlung Kategorie in der aktuellen Windows Hardware Zertifizierungsprogramm Treiber für den Speichercontroller. Alle mit einem übereinstimmenden Übermittlung Kategorie Speichercontroller wird unter der übereinstimmenden Kategorie vorgelegt.

-   Speichercontroller-Treiber muss eine STORPORT-Miniporttreiber.

-   Registrierungseinträge für STORPORT Miniporttreiber - SPEICHER\_BUS\_TYP muss auf BusTypeUnknown (0 x 00) festgelegt.

-   Für Speicher-Controller muss der Controller selbst ordnungsgemäß übersetzt die Befehle und gemäß den entsprechenden SCSI-Spezifikationen reagieren, selbst wenn der Controller andere Protokolle Befehl wie SATA-, NVMe oder PQI für eine andere Schnittstelle implementiert. Alle Befehle, die nicht erkannt werden müssen eine SCSI Check-Bedingung mit gültigen Sinne Daten führen.

### <a name="devicestoragecontrollerclasscode"></a>Device.Storage.Controller.ClassCode

*Controller Bus-attached müssen den richtigen Klasse-Unterklasse Code gemäß Definition in den PCI-Code und die ID Assignment-Spezifikation (Rev 1.6) implementieren.*

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

Controller-Klassencode

Host-Speichercontroller und Adapter müssen die Anforderungen für das Gerät verwendete Protokoll und alle Anforderungen in Bezug auf das Gerät Storage-Bus erfüllen.
Controller Bus angeschlossenes den richtige Klasse-Unterklasse Code gemäß PCI 2.3, Anhang D. implementiert werden müssen Dies gilt für alle Bustypen, einschließlich, aber nicht beschränkt auf IDE, Fibre Channel, SCSI und SATA-basierte Geräte. Jedes Gerät, das implementiert RAID-Funktionen, unabhängig davon, ob die RAID-Implementierung erfolgt in der Hardware, Firmware, oder im Treibercode muss die PCI-RAID-Klasse implementieren Code (01/04) und nicht mithilfe des Codes der Interconnect-Klasse (beispielsweise ein SATA-RAID-Controller muss implementieren Sie den Klassencode 01/04-und nicht die AHCI-Klasse code 06/01/01).

Nicht-PCI-attached Storage-Hostcontroller muss nicht auf Bericht PCI-Klassencode. Jedoch muss es melden die entsprechende ACPI Compatibility-ID.
 

### <a name="devicestoragecontrollerinffile"></a>Device.Storage.Controller.InfFile

*Alle Hostadapter müssen installiert sein, mithilfe von Plug & Play-Mechanismen und erfordern die Verwendung einer INF-Datei.*

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

Controller INF-Datei alle Hostadapter müssen mithilfe von Plug & Play-Mechanismen installiert werden und erfordern die Verwendung von eine INF-Datei. Installieren von Software müssen INF-Dateien verwenden, müssen das aktuellste Chkinf Tool übergeben und explizit die Registrierungswerte mithilfe der INF-Datei Konstrukte die Windows-Zertifizierungsstelle Programm Anforderungen erfüllen, die nur ändern können. Änderungen können nur unter den folgenden Schlüsseln vorgenommen werden:

-   Unter der Klassentreiber TimeoutValues services Schlüssel (Festplatte und Band).

-   SpecialTargetList nur für SCSIport Implementierungen.

-   Des Geräts Service-Schlüssels (muss HKLM\\System\\CurrentControlSet\\Services\\ und die Parameter\\Gerät Unterschlüssel unter dem).

-   Signal BusChangeDetected auf jedem Link Übergang oder Erkennung eines hot-Plug-Ereignisses. Eine begrenzte ausgleichen ist zulässig, bevor dies signalisiert, aber es über eine Registrierungsparameter festgelegt werden muss.

-   Implementierung der Registrierung Bustyp Kartenangabe DWORD den Schnittstellentyp gemäß der Enumeration NTDDSTOR ordnungsgemäß festgelegt. H (Siehe das WDK). Dieser Wert muss in der Miniport INF-Datei unter der Dienst Parameterschlüssel festgelegt werden. Es gibt keine Möglichkeit, ihn festzulegen, und Sie können nicht auf Coinstallers verlassen, wie diese unter allen Szenarien nicht ausgeführt werden.
     

### <a name="devicestoragecontrollerminiportdrivermodel"></a>Device.Storage.Controller.MiniportDriverModel

*Speicher Miniport Driver Model*

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

Miniport Driver Model

Verwendet mit Speichercontroller Treiber müssen Miniport Treibermodell befolgen. Speicher Miniports müssen alle Definitionen für Miniport Schnittstellen gemäß Definition im WDK entsprechen. Fibre Channel, iSCSI, SAS, SAS RAID SATA, SATA-RAID-, SCSI und SCSI-RAID-Controller-Treiber müssen STORPORT Miniports befinden. Monolithische Full-Port-Treiber oder andere Arten von Treibern, die nicht das Modell Miniport folgen sind nicht berechtigt, für die Zertifizierung. Alle Treiber für physische Hardware müssen zur Unterstützung der Plug & Play implementiert werden. Legacy-Treiber werden nicht mehr unterstützt.

Jedes Gerät, das ein Filtertreiber für physikalischen Laufwerk Funktionalität abhängig ist, kann nicht für die Zertifizierung verwendet. Filtertreiber können nicht umgangen werden einem beliebigen Teil des Speicherstapel des verwendet werden. Beispielsweise ein Filtertreiber, dass viele Hardware (z. B. mithilfe von HAL aufruft) nicht direkt zugreifen und Filter können Treiber nicht zum Verknüpfen der Cache-Manager an die Implementierung der Hardware verwendet werden. Filtertreiber können nicht verletzen Begriffe des Zertifizierungsprogramms verwendet werden.

Multipathing Treiber können nicht an bestimmten HBAs außer PCI RAID-Controller gebunden werden und müssen das Modell MPIO verwenden.

Vorübergehende oder bezeichnet Geräte möglicherweise nicht mit dem System verfügbar gemacht werden. Faktoren, die NODRV angeben können zum "Management Geräte dieses Berichts als Prozessor, Controller oder MSC Gerätetypen Forderung" verwendet werden. Solche Treibern, die nicht auf einen Diensteintrag verweisen sind nicht berechtigt, für das Zertifikat, aber kann signiert werden.

<a name="device.storage.controller.ata"></a>
## <a name="devicestoragecontrollerata"></a>Device.Storage.Controller.Ata

*Definiert die Branche und der Microsoft-Standards erfüllt sein müssen*

### <a name="devicestoragecontrolleratainterface"></a>Device.Storage.Controller.Ata.Interface

*PATA Controller-Schnittstelle*

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

PATA-Schnittstelle PATA Controller müssen der ATA/ATAPI-7-Spezifikation entsprechen. Bus mastering DMA Funktion ist erforderlich für alle PATA Domänencontroller mit Ausnahme von compact flash und ähnliche Flash-RAM-Gerät.
Die folgenden Anforderungen gelten auch für ATA/ATAPI-Controller.

-   Die PAKET-Befehlsprotokoll muss gemäß Definition im ATA/ATAPI-7 Volume 2 Abschnitt 11,8, nicht in nur ATA-Controller implementiert werden.

-   PATA-Domänencontrollern, die das PAKET Befehl-Protokoll unterstützen müssen gemäß Definition im ATA/ATAPI-7 Volume 2 Abschnitt 11,8 vollständig implementiert werden.

-   Identifizieren von Gerät die Datenfelder (61:60) und (103:100) darf nicht verwendet werden, um 28 oder 48-Bit-LBA Adressierung Support zu bestimmen. Stattdessen bit 10 von Word 83 und Bit 10 von Word 86 48-Bit-LBA Adressierung Unterstützung gemäß Definition in ATA/ATAPI-7, Teil 1, Abschnitt 4.2.1 überprüft werden muss.



<a name="device.storage.controller.azurestack"></a>
## <a name="devicestoragecontrollerazurestack"></a>Device.Storage.Controller.AzureStack

*Definiert Anforderungen, die erfüllt sein müssen, wenn der Speichercontroller in einer Microsoft Azure-Stapel basierte private Cloud-Lösung unterstützt wird*

### <a name="devicestoragecontrollerazurestackbasicfunction"></a>Device.Storage.Controller.AzureStack.BasicFunction

*Mindestanforderungen für Speichercontroller in Microsoft Azure-Stapel Lösungen verwendet*

<table><tr><th>Gilt für</th><td><p>Windows Server 2016 X64</p></td></tr></table>

**Beschreibung**

In der folgenden Tabelle werden Microsoft Azure-Stapel-Anforderungen für Speichercontroller erfasst.

<table>
    <tr><th>Feature</th><th>Anforderung</th></tr>
    <tr><td rowspan="4">Device.Storage.Controller</td><td>Device.Storage.Controller.BasicFunction</td></tr>
    <tr><td>Device.Storage.Controller.ClassCode</td></tr>
    <tr><td>Device.Storage.Controller.InfFile</td></tr>
    <tr><td>Device.Storage.Controller.MiniportDriverModel</td></tr>
    <tr><td>Device.Storage.Controller.Boot</td><td>Wenn 'Device.Storage.Controller.Boot.BasicFunction' implementiert wird, ist 'Device.Storage.Controller.Boot.BitLocker' erforderlich</td></tr>
    <tr><td>Device.Storage.Controller.Flush</td><td>Device.Storage.Controller.Flush.BasicFunction</td></tr>
    <tr><td>Device.Storage.Controller.PassThroughSupport</td><td>Device.Storage.Controller.PassThroughSupport.BasicFunction</td></tr>
    <tr><td>Device.Storage.Controller.Sas</td><td>Wenn 'Device.Storage.Controller.Sas.Interface' implementiert wird, ist 'Device.Storage.Controller.Sas.TranslationLayer' erforderlich</td></tr>
    <tr><td>Device.Storage.ControllerDrive.NVMe</td><td>Device.Storage.ControllerDrive.NVMe.BasicFunction</td></tr>
    <tr><td rowspan="6">Device.DevFund.Server.Nano</td><td>Device.DevFund.Server.OperateInServerNano</td></tr>
    <tr><td>Device.DevFund.Server.Nano.Deployment</td></tr>
    <tr><td>Device.DevFund.Server.Nano.Diagnostics</td></tr>
    <tr><td>Device.DevFund.Server.Nano.PatchAndUpdate</td></tr>
    <tr><td>Device.DevFund.Server.Nano.MonitoringAndTelemetry</td></tr>
    <tr><td>Device.DevFund.Server.Nano.FirmwareUpdate</td></tr>
</table>

Zusätzlich zu den oben genannten müssen die folgenden Anforderungen erfüllt sein:

1.  SAS HBA erforderlich für SAS und SATA-Datenträgergeräte
2.  SAS – Erweiterung mit SES-Funktion erforderlich, damit SAS und SATA-Geräte

### <a name="devicestoragecontrollerazurestackcloudstress"></a>Device.Storage.Controller.AzureStack.CloudStress
*Speichercontroller, die Verbindung zum Cluster-Speicher für die private Cloudlösung verwendet werden, müssen mit dieser Spezifikation entsprechen.* 

<table><tr><th>Gilt für</th><td><p>Windows Server 2016 X64</p></td></tr></table>

**Beschreibung**

Private Cloudlösungen umfassen eng integrierte Software und Hardwarekomponenten für Zweigstellenstandorte mit hoher Leistung bieten. Probleme bei der in den Komponenten (Software, Hardware, Treibern, Firmware usw.) können gefährden die Lösung und beeinträchtigt alle Versprechen bezüglich Service Level Agreement (SLA) für die private Cloud vorgenommen. 

Viele dieser Probleme sind nur unter eine hohe Stress, private Cloud Simulation verfügbar gemacht. Private Cloud Simulator (PCS) können Sie zum Überprüfen der Komponente in einem cloudszenario mit und Probleme zu identifizieren. Es simuliert eine live Datacenter/Private Cloud durch VM-Arbeitslasten zu erstellen, Planen von administrative Vorgänge (Lastenausgleich, Wartung von Software/Hardware) und Einfügen von Fehlern (ungeplante Hard-und Software mit Fehlern) auf die private Cloud. 

Um diese Spezifikation entsprechen, muss der Controller PCS Testlauf mit den 'Speichercontroller – Azure Stack' übergeben Profil auf einer 4-Knoten-Cluster-Konfiguration.

### <a name="devicestoragecontrollerazurestackfirmwareupdate"></a>Device.Storage.Controller.AzureStack.FirmwareUpdate
*Speichercontroller, die Verbindung zum Cluster-Speicher für die private Cloudlösung verwendet werden, müssen mit dieser Spezifikation entsprechen.*

<table><tr><th>Gilt für</th><td><p>Windows Server 2016 X64</p></td></tr></table>

**Beschreibung**

Microsoft Azure-Stapel erfordern SAS und NVMe Controller Firmware aktualisierbar sein. Für NVMe Controller muss dies über den Posteingang [Firmwareupdates Mechanismus](https://blogs.technet.microsoft.com/filecab/2016/01/25/updating-firmware-for-disk-drives-in-windows-server-2016-tp4/) eingeführt in WS 2016 (Update-StorageFirmware) möglich sein. SAS HBAs muss außerdem ordnungsgemäß übersetzen Firmware-Download und Befehle gemäß der Spezifikation [SAT-4](http://www.t10.org/cgi-bin/ac.pl?t=f&f=sat4r04a.pdf) aktivieren.


<a name="device.storage.controller.boot"></a>
## <a name="devicestoragecontrollerboot"></a>Device.Storage.Controller.Boot

*Definiert die Anforderungen, die erfüllt sein müssen, wenn der Speichercontroller Boot unterstützt*

### <a name="devicestoragecontrollerbootbasicfunction"></a>Device.Storage.Controller.Boot.BasicFunction

*Wenn der Controller Boot-Unterstützung implementiert wird, muss es Int13h Funktionen unterstützen.*

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

Controller Boot-Unterstützung

Option ROM in Hostcontroller und für einen beliebigen anderen Schnittstellentyp Adapter, einschließlich RAID-Controller, zur Boot-Unterstützung muss vollständig unterstützen gemäß Definition im BIOS Enhanced Disk Drive Services - 3 Int13h-Funktionen (Funktionen 4xh) für erweiterte \[T13 D1572\], Version 3 oder höher. Adressierung logischer Blöcke ist der einzige unterstützte Adressierung Mechanismus.

Es wird empfohlen, Controller auch starten von Extensible Firmware Interface (EFI) unterstützen und Implementieren von Gerätepfaden im Sinne EDD 3. Starten von Windows 8, ist es erforderlich für Domänencontroller auf Starten von Extensible Firmware Interface (EFI) unterstützen.

SD/eMMC/NAND flash Controller haben keine Option ROM, damit der erste Teil dieser Anforderung nicht anwendbar ist. EFI-Unterstützung ist erforderlich.

### <a name="devicestoragecontrollerbootbitlocker"></a>Device.Storage.Controller.Boot.BitLocker

*BitLocker darf keine Fehler in SAN Boot über Speichercontroller bewirken.*

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

BitLocker muss ordnungsgemäß ein Betriebssystems in einem SAN Startkonfiguration schützen aktiviert sein.

**Unternehmensvorgabe**

(1) Wenn Sie ein Server in einer Umgebung ohne angemessene physische Sicherheit befindet, schützt BitLocker Daten auf dem Server vor nicht autorisiertem Zugriff bei ein Server Diebstahl; (2) Wenn Hostinganbieter Dienst einem neuen Zweck zuführen oder außer Betrieb Speicherarrays nehmen, wird verhindert, dass Datenträger-BitLocker-Verschlüsselung Daten Verletzung.

<a name="device.storage.controller.fc"></a>
## <a name="devicestoragecontrollerfc"></a>Device.Storage.Controller.Fc

*Definiert die Branche und der Microsoft-Standards erfüllt sein müssen*

### <a name="devicestoragecontrollerfcinterface"></a>Device.Storage.Controller.Fc.Interface

*Fibre Channel HBA-Schnittstelle*

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

Fibre Channel-Schnittstelle Fibre Channel Host Bus-Grafikkartentreiber müssen die WMI-Klassen und Methoden zum Implementieren von der FC-HBA- oder SM-API mithilfe der Microsoft-HBAAPI erforderlich unterstützen. DLL-DATEI. Lieferanten möglicherweise nicht die Microsoft bereitgestellten Version der HBAAPI ersetzen. DLL-Datei. Eine Teilmenge der Hbapiwmi.mof WMI-Klassen und Methoden sind für Windows-Kompatibilität erforderlich. Anderen WMI-Klassen sind optional und zum Formular Featuregruppen gruppiert werden. Wenn ein Treiber beliebigen Teils einer optional Featuregruppe implementiert, verwandten alle Klassen, Featuregruppe unterstützt werden muss. In einigen Fällen sind einige Features in Unterfeatures unterteilt. Wenn ein Treiber ein untergeordnetes Feature implementiert wird, muss der Treiber ordnungsgemäß, bestimmte Unterfeature unterstützen.
 

<a name="device.storage.controller.fc.npiv"></a>
## <a name="devicestoragecontrollerfcnpiv"></a>Device.Storage.Controller.Fc.NPIV

*NPIV wird verwendet, um die Bereitstellung von virtuellen Fibre Channel-Funktionalität in Hyper-V.*

### <a name="devicestoragecontrollerfcnpivbasicfunction"></a>Device.Storage.Controller.Fc.NPIV.BasicFunction

*Hyper-V Virtual Fibre Channel N\_Port e/a-Unterstützung der Virtualisierung*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

N\_Port e/a-Virtualisierung (NPIV) ist die zugrunde liegende Technologie, die in der Hyper-V-Feature virtuellen Fibre Channel verwendet. Diese Tests können Hersteller Treiber für Kompatibilität mit virtuellen Fibre Channel auf einer Ebene der API während des Entwicklungszyklus und vor dem Senden für die Zertifizierung aktualisierte Treiber an Microsoft Self-test.

Die folgenden Klassen sind erforderlich: MSFC:\_VirtualFibrePortAttributes, MSFC:\_FibrePortNPIVAttributes, MSFC:\_FibrePortNPIVMethodsEx, MSFC:\_FibrePortNPIVCapabilities, MSFC:\_NPIVCapabilities, MSFC:\_NPIVLUNMappingInformationEx. Optional können Sie MSFC:\_DH\_Chap\_Parameter implementiert werden können.

Diese Tests behandelt typische gültige und ungültige API-Aufrufe, jedoch werden ausführliche Szenarien mit VM Arbeitslasten, Speicherfunktion für Ziel und die Datenintegrität, Leistung oder anderer Aspekte nicht behandelt.

<a name="device.storage.controller.fcoe"></a>
## <a name="devicestoragecontrollerfcoe"></a>Device.Storage.Controller.Fcoe

*Definiert die Branche und der Microsoft-Standards erfüllt sein müssen*

### <a name="devicestoragecontrollerfcoeinterface"></a>Device.Storage.Controller.Fcoe.Interface

*Fibre Channel over Ethernet-Hostbusadapter*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Fibre Channel over Ethernet-Hostbusadapter  
 

-   FCoE Adapter muss FC-BB-5 FC-BB implementieren\_E-Spezifikation.

-   FCoE Adapter Miniport muss als Storport Miniport implementiert werden.

-   FCoE Adapter Miniport muss VER definieren\_FILEDESCRIPTION\_STR enthalten die Teilzeichenfolge "\[FCoE\]".

-   Für FCoE Adapter Miniport INF-Datei des \[Service-Install-Abschnitt\]:

    -   "DisplayName" der Wert ist erforderlich und muss enthalten die Teilzeichenfolge "\[FCoE\]".

    -   "Beschreibung" der Wert ist optional, wenn angegeben, dürfen die Teilzeichenfolge "\[FCoE\]".

-   Für FCoE Adapter Miniport INF Modelle Abschnitt \[Modelle-Abschnitt-Name\] | \[Modelle-Abschnitt-Name. TargetOSVersion\]:

    -   der Wert "Gerät-Beschreibung" muss die Teilzeichenfolge enthalten "\[FCoE\]".

-   FCoE Adapter Miniport muss BusTypeFibre als dessen SPEICHER deklarieren\_BUS\_TYP in der INF-Datei. SPEICHER\_BUS\_TYP-Aufzählung

-   FCoE Adapter, die PCI-Speichermedien verfügbar machen / Funktionen für FCoE Frame Verarbeitung (Ausgang oder eingehende), müssen als dessen Klassencode (Basisklasse, Unterklasse und Schnittstelle Code) 0x0c0400 (Fibre Channel) melden.

### <a name="devicestoragecontrollerfcoeinteroperability"></a>Device.Storage.Controller.Fcoe.Interoperability

*Fibre Channel over Ethernet-Hostbusadapter – Interoperabilität*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Interoperabilität
 

-   FCoE Adapter muss mit FC-SAN-Geräte über FCF interagieren.

-   FCoE Adapter muss mit dem systemeigenen FCoE Geräte interagieren.

-   FCoE Adapter muss Transportnetzwerk (IP) und (FCoE) Speicherdatenverkehr gleichzeitig können.

-   Deaktivieren/entfernen/Funktionalitätsverlust FC (Storage) muss nicht Netzwerkkonnektivität (Ethernet) und Funktionen auswirken.

-   FCoE Adapter muss auf zugreifen und Beheben von FC und systemeigenen FCoE Geräte gleichzeitig (über FCF).

 
Initiator-Koexistenz
 

-   FCoE Adapter muss Koexistenz mit FC-Adapter störungsfrei auf dem gleichen System.

-   FCoE Adapter muss Koexistenz mit anderen Adapter FCoE störungsfrei auf dem gleichen System.

<a name="device.storage.controller.flush"></a>
## <a name="devicestoragecontrollerflush"></a>Device.Storage.Controller.Flush

*Definiert die Branche und der Microsoft-Standards erfüllt sein müssen*

### <a name="devicestoragecontrollerflushbasicfunction"></a>Device.Storage.Controller.Flush.BasicFunction

*Flush an verbundenen Gerät*

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

Standard – Spezifikation branchenanforderungen:

-   Für ATA-Gerät CACHE zu LEEREN (E7h, nicht-Daten) 28-Bit-Befehl ist optional für ATA-Geräte und ATAPI-Geräte. FLUSH CACHE EXT (EAh, nicht-Daten) 48-Bit-Befehl für Geräte implementieren die Featuregruppe der 48-Bit-Adresse obligatorisch ist.

-   SCSI-Geräten müssen SYNCHRONIZE CACHE (10) Befehle und und/oder SYNCHRONIZE CACHE (16) implementiert werden.

Windows entwerfen Spec Anforderungen - Controller:

-   Für Controller und Gerätetreiber aller Bus-Typen (ATA, SCSI und USB) flush Cache Befehl verbundenen Fingereingabegerät ohne alle Auslassung übermittelt.

<a name="device.storage.controller.iscsi"></a>
## <a name="devicestoragecontrolleriscsi"></a>Device.Storage.Controller.Iscsi

*Definiert die Branche und der Microsoft-Standards erfüllt sein müssen*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>10 Windows Mobile x86</p>
<p>10 Windows Mobile x64</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

### <a name="devicestoragecontrolleriscsiinterface"></a>Device.Storage.Controller.Iscsi.Interface

*iSCSI-Schnittstelle*

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

iSCSI-Schnittstelle iSCSI-Hostbusadapter müssen mit iSCSI RFC3720 kompatibel sein und müssen alle verbindlich implementieren. Die einzige Ausnahme ist, dass IPsec ist zwar nicht obligatorisch jedoch nicht, wenn implementiert wird, wird getestet. Alle optionale Komponenten müssen diese Spezifikation Falls implementiert, entsprechen.
 

-   Optionales Verhalten muss Einhaltung der iSCSI-Spezifikation oder die Windows-Zertifizierung Programm Anforderungen für iSCSI nicht beeinträchtigt werden.

-   Das Gerät und Treiber müssen auch bestimmte Anforderungen für SCSI-Controller und Geräte erfüllen.

-   Ein iSNS-Client kann implementiert werden und wenn Ja, RFC3723 entsprechen.

-   Ein Adapter muss möglicherweise Ping (ICMP) empfangen und Senden von Ping (ICMP).

-   Gerät Anmeldungen müssen konsistent mit dem Microsoft iSCSI-Discovery-Dienst sein.

-   Alle Boot-Gerät mit anderen Mitteln konfiguriert muss nach dem Start des Diensts gemeldet werden.

-   Andere persistent Ziel Zuordnungen und unter Kontrolle des HBA-Sitzungen mitzuteilen durch Verwenden von WMI für die iSCSI-Initiator-Dienst beim verfügbar ist.

-   Die folgenden Anmeldung Authentifizierung Implementierungen sind beide erforderlich:

    <!-- -->

    -   "Initiator authentifiziert CHAP Target"

    -   Keine

    <!-- -->

-   Gegenseitiges CHAP muss Falls implementiert, die Spezifikation und wird getestet.

-   IPSec-Unterstützung muss alle anwendbaren IPSec Vorschriften in diesem Dokument entsprechen.

-   Der HBA-Treiber muss in das WDK dokumentiert werden alle erforderliche WMI-Schnittstellen implementieren.

-   Der Initiator muss eine automatische Anmeldung an Ziele am Computer als persistent Ziele zugewiesen ausführen. Der Initiator wird mit allen persistent Zielen verbunden, bevor die Ziele von Windows aufgelistet werden, die mit einer Abfrage zu LUN 0 beginnt. Wenn eine Verbindung getrennt wird, wird es weiterhin erneut eine Verbindung herzustellen. Der Suchdienst für diese Informationen können nicht Geräte abhängen.

-   Initiatoren müssen:

    <!-- -->

    -   Verwalten der permanenten Anmeldeinformationen in der Registrierung oder im NVRAM.

    -   Unterstützt die neue WMI-Klasse für persistent Anmeldungen definieren/verwalten.

    -   Beibehalten von IP-Netzwerk Adapter und-Suche Konfigurationen (IP-Konfigurationsinformationen, z. B. statische IP-Adresse, statische IP-Adresse des Standardgateways, statische Subnetzmaske und DNS-Server) oder DHCP verwenden, um diese Informationen zu erhalten.

    -   Denken Sie für die suchekonfiguration daran, welche Discovery-Methoden verwendet und für iSNS (sofern implementiert) sind, verwalten die Adresse des iSNS-Servers.

    <!-- -->

-   Ein iSCSI-HBA muss Wechsler, Datenträger, Band und externen RAID-Geräte unterstützen.

<a name="device.storage.controller.iscsi.iscsibootcomponent"></a>
## <a name="devicestoragecontrolleriscsiiscsibootcomponent"></a>Device.Storage.Controller.Iscsi.iSCSIBootComponent

*Definiert die Branche und der Microsoft-Standards erfüllt sein müssen*

### <a name="devicestoragecontrolleriscsiiscsibootcomponentfwtable"></a>Device.Storage.Controller.Iscsi.iSCSIBootComponent.FwTable

*iSCSI-Boot-Funktionalität*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

iSCSI-Boot-Funktionalität der iSCSI-Boot-Komponente muss:

-   Mit iSCSI-Zielen mit iSCSI-RFC3720 Benutzer/innen kompatibel sein.

-   Verschieben Sie alle iSCSI-Funktionalität des Microsoft iSCSI Softwareinitiator nach dem Starten Sie den Windows Sequenz beginnt (sobald ntoskrnl.exe lädt).

-   Unterstützen Sie Anmeldung Umleitung.

-   Unidirektionale CHAP unterstützen und CHAP geheimen im permanenten Speicher verwalten müssen.

-   Implementieren Sie iSCSI Boot Firmware-Tabelle in Firmware oder Option ROM pro die optionale ACPI SIIG-Tabelle.

-   Unterstützen Sie Speicherabbild.

-   Die Verwendung von IPV6-Adressen unterstützt.

-   Unterstützung von RELOGIN als minimale Fehlerbehandlung im Fall eines Fehlers während der Initialisierung Anmeldesequenz mit iSCSI-Ziel.

-   Unterstützt die folgenden DHCP-Optionsnummern: 1, 3, 17, 43, 51, 54, 57, 60, 61, 255, 201, 202, 203, 204, 205 und 206.

-   Die folgenden DHCP-Parameter unterstützt:

-   DHCPDISCOVER zum Abrufen einer IP-Adresse zugewiesen.

-   DHCPREQUEST iSCSI Protocol Parameter abrufen.

-   DHCPINFORM Updates in Informationen vom DHCP-Server verfügbar ist.

Außerdem:

-   Alle Anfragen von iSCSI-Komponente vor dem Start stattfindende DHCP-Clients zum DHCP-Server müssen Option 60 verwenden, um den jeweiligen Anbieter Bereich anzuzeigen.

-   Alle Anfragen von iSCSI-Komponente vor dem Start stattfindende DHCP-Clients an DHCP-Servern müssen die Option 61 verwenden, um die Identität des dieser bestimmten Client signalisieren. Wenn die Client-ID die ALT-Taste nicht definiert ist, Typfeld auf 0 x 01 festgelegt werden sollte, und die EN-MAC-Adresse muss verwendet werden, um die Clientidentität definieren. Wenn die Client-Id Alt definiert ist, klicken Sie dann das Typfeld auf 0 x 00 festgelegt werden sollte und Feld CAID muss verwendet werden.

-   Alle Anfragen von iSCSI-Komponente vor dem Start stattfindende DHCP-Clients auf DHCP-Servern müssen das CHADDR Feld mit der EN-MAC-Adresse des DHCP-Client verwenden.

-   Die Verwendung von der BEIDES vor dem Start stattfindende iSCSI-Komponente muss die DHCP-Nutzung der BEIDES entsprechen.

-   Die Verwendung der vor dem Start stattfindende YIADDR iSCSI-Komponente muss die DHCP-Nutzung der YIADDR entsprechen. DHCP-Client die vor dem Start stattfindende iSCSI-Komponente muss nämlich das vom DHCP-Server bereitgestellt werden, während der Transaktion Sequenz DHCPREQUESTÃ³DHCPACK oder DHCPINFORMÃ³DHCPACK YIADDR akzeptieren.

-   Die Verwendung von SIADDR in der vor dem Start stattfindende iSCSI-Komponente muss die DHCP-Nutzung der SIADDR entsprechen. nämlich muss iSCSI vor dem Start stattfindende Komponente DHCP-Clients diese Adresse Zugriff auf den DHCP-Server während DHCPREQUESTÃ³DHCPACK oder DHCPINFORMÃ³DHCPACK Transaktionen verwenden.

-   Zur Unterstützung der DHCP-Option 1 muss die Subnetzmaske bereitgestellt, in der Antwort DHCPOFFER aus der iSCSI-Komponente vor dem Start die Subnetzmaske angeben.

-   Alle Transaktionen zwischen der iSCSI vor dem Start Komponente DHCP-Clients und DHCP-Server muss eine einzelne Frame-Transaktion.

-   Um einen Konflikt mit anderen Diensten zu vermeiden, muss die vor dem Start stattfindende iSCSI-Komponente nicht DHCP-Option 52 verwenden.

-   Implementierung von mehreren Option Antworten in der vor dem Start stattfindende iSCSI-Komponente muss RFC 3396 entsprechen.

<a name="device.storage.controller.optical"></a>
## <a name="devicestoragecontrolleroptical"></a>Device.Storage.Controller.Optical

*Features, die für alle Speichercontroller, um sicherzustellen, dass optische Brennen von Anforderungen gilt erfüllt sind.*

### <a name="devicestoragecontrolleropticalbasicfunction"></a>Device.Storage.Controller.Optical.BasicFunction

*HBA Treiber müssen optische Laufwerke unterstützen.*

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

Optische Controller-Unterstützung

Die Speicherung HBA-Treiber müssen optische Laufwerk unterstützen. Die CDBs optische Gerät gesendet und die Antwort vom optisches Laufwerk muss ordnungsgemäß behandelt werden.
 

<a name="device.storage.controller.passthroughsupport"></a>
## <a name="devicestoragecontrollerpassthroughsupport"></a>Device.Storage.Controller.PassThroughSupport

*Pass-Through-Storage Controller Grundfunktionen*

### <a name="devicestoragecontrollerpassthroughsupportbasicfunction"></a>Device.Storage.Controller.PassThroughSupport.BasicFunction

*Pass-Through-Storage Controller Grundfunktionen*

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

Der Bus-Adapter muss den tatsächlichen Bustyp verwendet, um verbundene Laufwerke melden (z. B. Laufwerke über den Bus SAS verbunden sind; reporting Laufwerke wie über die "RAID" Bus verbunden ist ungültig).  Alle Befehle müssen für die zugrunde liegenden physischen Geräte direkt über übergeben werden.  Die physischen Geräte müssen nicht abstrahiert (z. B. gebildet in einen logischen RAID-Datenträger) und der Busadapter muss Befehle für die physische Geräte nicht antwortet.

HINWEIS: Dieser betrifft nur SAS und SATA-Controller.

<a name="device.storage.controller.raid"></a>
## <a name="devicestoragecontrollerraid"></a>Device.Storage.Controller.Raid

*Definiert die Branche und der Microsoft-Standards erfüllt sein müssen*

### <a name="devicestoragecontrollerraidbasicfunction"></a>Device.Storage.Controller.Raid.BasicFunction

*RAID-controller*

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

RAID-Controller

-   Miniporttreiber für PCI RAID-Adapter können eine Management LU Wenn dieses Gerät ist immer für Befehle zur Verwaltung und verfügt über ein anderes Gerät als Datenträger erstellen. Da dieses Gerät im Geräte-Manager angezeigt wird, können eine NODRV INF-Datei übermittelt werden, dieses Gerät anfordern und zu verhindern, dass Benutzer Popups (Diese INF-Datei kann signiert sein).

-   Für RAID-Controller muss der Controller selbst richtig interpretiert werden die Befehle und gemäß den entsprechenden SCSI-Spezifikationen reagieren, selbst wenn der Controller RAID auf einen anderen Schnittstellentyp wie SATA-implementiert. Alle Befehle, die nicht erkannt werden, müssen sich eine SCSI-Check-Bedingung mit gültigen Sinne Daten ergeben.

-   (Sofern implementiert) Wenn der RAID-Controller einen Pass-Through-Datenträger-Modus (auch bekannt als HBA-Modus unterstützt) und die Verwendung von SATA-Laufwerken, müssen sie mindestens die folgenden T10 SAT-4-Spezifikation (Rev 03a) Übersetzungen implementieren:

    -   Laden Sie Microcode Modus 0Eh (Abschnitt 8.16.2.5)

    -   Laden Sie Microcode Modus 0Fh (Abschnitt 8.16.2.6)

    Hinweis: Einhaltung dieser Anforderung sollte getestet werden, indem Sie den Test mit HLK Firmware zu aktualisieren beenden und Herstellen einer Verbindung mit SATA-Laufwerk, kompatibel mit der Windows-10 Firmware Update Anforderungen an die RAID-Controller im HBA Modus.

SCSI-Anforderungen finden Sie im Abschnitt Device.Storage.SCSI.

<a name="device.storage.controller.raid.continuousavailability"></a>
## <a name="devicestoragecontrollerraidcontinuousavailability"></a>Device.Storage.Controller.Raid.ContinuousAvailability

*Überprüft, dass Speichercontroller kontinuierliche Verfügbarkeit (CA) und Treiber alle bestimmte Anforderungen erfüllen*

### <a name="devicestoragecontrollerraidcontinuousavailabilityactivemode"></a>Device.Storage.Controller.Raid.ContinuousAvailability.ActiveMode

*Ein Gerät und dessen Treiber müssen auf jedem Knoten in einem Windows-Failovercluster Systemkonfiguration aktiven LUN Zugriff unterstützen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Wenn das Gerät und Treiber in mehreren Knoten in einem Windows-Failovercluster konfiguriert werden, muss jedem Knoten als eine minimale "Dual-aktiv" Access als vollständigem Lese-/Schreibzugriff-Funktionalität für mindestens eine LUN, das die Möglichkeit zum Failover ausgeführt wird, zu einem anderen Knoten im Cluster verfügt definierten unterstützen. Insbesondere ein Gerät darf nicht nur passive Vorgang unterstützt das Gerät und Treiber nur in den standby-Modus, in dem ausgeführt, bis eine LUN von einem anderen Knoten des Clusters Failover.

Hinweise zum Entwurf:

-   Für diesen Zugriff "Dual-aktiv" müssen LUNs nicht vollständige, leistungsfähige Lese-/Schreibzugriff, die alle Knoten im Cluster zu ermöglichen. Zugriff von anderen Knoten muss nur unterstützt werden, wie erforderlich, um eine gültige Windows-Failovercluster zu unterstützen.

-   Es handelt sich hierbei wünschenswert, jedoch nicht erforderlich, wenn Gleichzeitiges, gemeinsamen Zugriff auf eine LUN aus mehreren Knoten im Cluster.

### <a name="devicestoragecontrollerraidcontinuousavailabilityfailoverclustering"></a>Device.Storage.Controller.Raid.ContinuousAvailability.FailoverClustering

*Ein Gerät und dessen Treiber müssen einen minimalen Satz von Anforderungen für den Betrieb in einem Windows-Failovercluster erfüllen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

SPC-3 Abschnitt 6.11 PERSISTENT RESERVE IN Befehl muss ein Gerät einhalten.

-   SPC-3-Abschnitt 6.12 PERSISTENT RESERVE OUT Befehl muss ein Gerät einhalten.

    -   Gerät muss beständiger Reservierungen Typ unterstützen, gemäß Definition im Abschnitt 6.11.3.4 Tabelle 107:

        <!-- -->

        -   5h schreiben exklusive – nur Teilnehmer

        <!-- -->

-   Ein Gerät muss mit den Reservierung Verhalten entsprechen, gemäß Definition im Abschnitt 5.6 SPC-3

-   Testen der Übereinstimmung mit SCSI sollten insbesondere besonders darauf, dass Folgendes überprüfen berücksichtigt werden:

    -   Reserving – einmal reserviert ist, vergewissern Sie sich im Bereich & Typ von einer bestehenden beständigen Reservierung nicht möglich

    -   Abschnitt 5.6.1 – Tabelle 32 entsprechen

    -   Abschnitt 5.6.6 – Tabelle 33, 34, Tabelle 36 einhalten – Bedingungen eine gute Status überprüfen

    -   Stellen Sie sicher, registrieren Sie ein ich neu\_T Nexus, die bereits registrierte (5.6.6) – wurde sollte eine gute Status zurückgegeben werden

    -   Stellen Sie sicher, reservieren Sie erneut eine\_T Nexus, die die Reservierung persistente (5.6.9) – enthält eine gute Status sollte zurückgegeben werden

    -   Reservierungskonflikt – zurück, wenn Sie PRO Dienst eine Aktion Befehl PREEMPT oder PREEMPT & ABBRECHEN mit ungültigen Service Aktion Reservierung Schlüssel (5.6.10.4.4) gesendet wird

    -   Überprüfen Sie im Feld werden zusätzliche Länge pro 6.11.3.2 - sollte 0 (null) zurück, wenn keine persistenten Reservierung gehalten wird

Hinweise zum Entwurf:

-   Es wird empfohlen, dass zusätzlich zu den standardmäßigen HCT Qualifikation alle Lösungen auch mit dem Tool "Microsoft Cluster Configuration Validation Wizard" (ClusPrep) überprüft werden.

-   Nur SAS-Geräte unter Verwendung des Transports seriellen SCSI-Protokoll (SSP) werden in Failoverclustern (einschließlich SAS JBOD oder SAS SSP RAID-Systemen) unterstützt.

Wenn die Systemdatenträgern zu einem Bus, die kein gültiger Typ für freigegebenen Speicher (etwas als FC, iSCSI oder SAS), klicken Sie dann die Festplatten des Systems und freigegeben ist zugeordnet sind.

### <a name="devicestoragecontrollerraidcontinuousavailabilitylunaccess"></a>Device.Storage.Controller.Raid.ContinuousAvailability.LunAccess

*Ein Gerät und dessen Treiber müssen die Anforderungen für den Zugriff auf LUNs in einer Windows Failover-Clusterunterstützung Konfiguration erfüllen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Wenn ein Knoten in einem Windows-Failovercluster über seine Ressourcen ausfällt geplant oder ungeplant (z. B. entsteht ein Knoten Absturz oder Knoten Stromausfall), müssen das Gerät und Treiber die folgenden Anforderungen erfüllen:

-   Sämtliche Daten vom erfolgreich bestätigten Schreibvorgänge vor dem Failover müssen beibehalten werden und von funktionierenden Knoten verfügbar sein. Insbesondere Daten entsprechend den Schreibvorgängen gesendet an das Gerät und Treiber auf dem fehlerhaften Knoten vor dem Beginn der Failover für seine LUNs (d. h., nachdem der entsprechende RAID-Controller auf einen betriebsbereiten Knoten eine permanente Reservierung Anforderung entspricht der LUNs aus der ausgefallene Knoten), haben anerkannt wurden vom Treiber als abgeschlossen muss nach Abschluss des Failovers aus einen betriebsbereiten Knoten zugegriffen werden. Darüber hinaus alle Daten, die möglicherweise ausstehende aus nicht bestätigten Schreibvorgänge am Anfang des Failover müssen keine Daten ändern anschließend das Gerät aus einen betriebsbereiten Knoten geschrieben.

-   Wenn die LUNs unterstützt stoppen, indem Sie die RAID-Controller auf dem fehlerhaften Knoten wird zugegriffen werden (d. h., Stop bestätigen und Verarbeitung von e/a-Anforderungen), die LUN muss zugänglich gemacht werden (d. h., zu bestätigen und Verarbeiten von e/a-Anforderungen) durch mindestens einen anderen Knoten im Cluster mit einer maximalen Verzögerung von 5 Sekunden. Diese zeitliche Begrenzung muss für bis zu 100 LUNs oder die maximale Anzahl von LUNs, die vom Controller unterstützt unterstützt werden, je nachdem, was kleiner ist.

Während des normalen Betriebs (d. h., nicht während des Failovers) in einem Windows-Failovercluster einer das Gerät und Treiber müssen die folgende Anforderung erfüllen:

-   Alle e/a-Anforderungen an beliebige LUN von der RAID-Controller unterstützt müssen innerhalb von 25 Sekunden ausführen. Diese zeitliche Begrenzung muss für bis zu 100 LUNs oder die maximale Anzahl von LUNs, die vom Controller unterstützt unterstützt werden, je nachdem, was kleiner ist.

### <a name="devicestoragecontrollerraidcontinuousavailabilityraid"></a>Device.Storage.Controller.Raid.ContinuousAvailability.RAID

*Ein Gerät und dessen Treiber müssen einen minimalen Satz von Anforderungen für RAID-Funktionen erfüllen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

-   Ein Gerät und dessen Treiber Befehle von SBC-2 (oder höher) unterstützen müssen unabhängig von der Laufwerk-Schnittstelle implementiert.

-   Ein Gerät und dessen Treiber müssen unterstützen, mindestens eine der: RAID1, RAID 5, RAID6 oder RAID 1/0 oder ein gleichwertiges Feature, das unterstützt vollständiger LUN-Funktionen bei einem Ausfall eines einzelnen Daten Laufwerks.

-   Ein Gerät und dessen Treiber RAID-Implementierung müssen Datenverlusten aufgrund der RAID "Schreiben Hole" Fehler Mechanismus, um eine Lösung bereitstellen. (Siehe Hinweise zum Entwurf für die Definition des RAID "Schreiben Hole" Fehler Mechanismus).

**Hinweise zum Entwurf**

Befindet sich ein System- oder Controller-Fehler während der aktiven Schreibvorgänge, die Löschung eines Stripe (z. B. Parität) Informationen möglicherweise mit den Daten inkonsistent. Datenverlust möglicherweise Laufzeitfehler, wenn diese falsche Löschung Codeinformationen zum Wiederherstellen des fehlenden Blocks in diesem Stripe nachfolgend verwendet wird. Dieses Problem wird als RAID "Write Hole" bezeichnet.

-   Beispiele für typische Lösungen für das RAID-Write Hole Problem sind anzugebende Mechanismen zum Erkennen und Wiederherstellen von einem unterbrochenen Update-in-Place-Vorgang oder Update-in-Place Semantik zu vermeiden.

### <a name="devicestoragecontrollerraidcontinuousavailabilityrecoveryprocessing"></a>Device.Storage.Controller.Raid.ContinuousAvailability.RecoveryProcessing

*Ein Gerät und dessen Treiber müssen automatisch alle Wiederherstellung Verarbeitung entsteht fehlerhaften über eine LUN von einem Knoten in einem Windows-Failovercluster ausführen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Wenn das Gerät und die Treiber werden in einem Windows-Failovercluster konfiguriert und LUN-Zugriff nach einem Failover wiederhergestellt wird (siehe die Anforderung CAHWStorage 0004), muss alle das Gerät und aus dem Failover und Wiederherstellen normalen Betrieb-Treiber erforderliche Verarbeitung automatisch, d. h., ohne manuelle Eingriffe.

<a name="device.storage.controller.sas"></a>
## <a name="devicestoragecontrollersas"></a>Device.Storage.Controller.Sas

*Definiert die Branche und der Microsoft-Standards erfüllt sein müssen*

### <a name="devicestoragecontrollersasinterface"></a>Device.Storage.Controller.Sas.Interface

*SAS-Schnittstelle*

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

SAS-Schnittstelle

SAS-Host Bus Adapter Miniporttreiber müssen die Microsoft Hbaapi DLL zur Unterstützung der Windows-Verwaltungsinstrumentation (WMI)-Methods verwenden. Der spezifischen erforderlich WMI-Klassen und Methoden gruppiert und als obligatorisch oder optional festgelegt werden. Alle obligatorischen Klassen und Methoden müssen unterstützt werden. Wenn eine Gruppe als optional gekennzeichnet ist und ein Miniporttreiber diese Gruppe unterstützt, werden einzelne Methoden und Klassen in dieser Gruppe auch klassifiziert als obligatorisch, wenn die Gruppe implementiert wird, oder optional, wenn die Gruppe nicht implementiert ist.

**Hinweis:** Die SAS HBA-API ist derzeit in der Phase der Entwurfsdatenbank an der Arbeitsgruppe T11.5. Diese Unterstützung wird bis zum Abschluss des Entwurfsdokument nicht mehr erforderlich sein. WHQL wird eine Ankündigung ausstellen, sobald diese Unterstützung erforderlich ist.

### <a name="devicestoragecontrollersastranslationlayer"></a>Device.Storage.Controller.Sas.TranslationLayer

*Definiert bestimmte Übersetzungen aus SAS SATA an, die implementiert werden müssen*

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

(Sofern implementiert)

SAS HBAs und/oder Gerätetreibern sollten die folgenden SCSI implementieren / ATA-GERÄTS Translations, gemäß Definition in T10 SAT-4-Spezifikation (Rev 03a):

-   Herunterladen von Microcode Modus 0Eh (Abschnitt 8.16.2.5)
-   Laden Sie Microcode Modus 0Fh (Abschnitt 8.16.2.6)

Hinweis: Einhaltung dieser Anforderung sollte getestet werden, indem eine Verbindung SATA-Laufwerk, kompatibel mit der Windows-10 Firmware Update Anforderungen zu SAS HBA HLK Firmware aktualisieren Tests ausgeführt. Testen der Controller Übersetzung Ebene sollte mit einem SAS – Erweiterung zwischen dem Ziel (SATA-Laufwerk) und der Controller (HBA) ausgeführt werden.

<a name="device.storage.controller.sata"></a>
## <a name="devicestoragecontrollersata"></a>Device.Storage.Controller.Sata

*Definiert die Branche und der Microsoft-Standards erfüllt sein müssen*

### <a name="devicestoragecontrollersatainterface"></a>Device.Storage.Controller.Sata.Interface

*SATA-Controller-Schnittstelle*

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

SATA-Schnittstelle
 

-   SATA-Controller müssen der ATA-/ ATAPI-7-Spezifikation entsprechen.

-   SATA-Controller müssen hot Plug & Play unterstützen.

-   SATA-Controller werden gemäß Definition im SATA asynchrone Benachrichtigung zu unterstützen: hohe Geschwindigkeit serialisiert unter Anlage, Version 2,6 oder höher und AHCI 1.3 oder höher.

-   Wenn implementiert, muss ordnungsgemäß NCQ unterstützt werden.

-   Wenn implementiert wird, müssen größer Bereiche als 512 Bytes ordnungsgemäß unterstützt werden.

-   AHCI SATA-Controller müssen mit der Spezifikation AHCI 1.0 oder höher entsprechen.

-   SATA-Controller darf nicht PATA emulieren.

-   Schnittstellen für AHCI SATA - Controller, wenn eine Schnittstelle als AHCI, implementieren müssen von einem Windows-Posteingang-Treiber unterstützt werden oder müssen mit einem angegebenen Treiber Zertifizierung. Die angegebenen Treiber müssen die Treiber Zertifizierung-Anforderungen in diesem Dokument erfüllen.

-   Empfehlung: SATA-Controller sollten die Power Management Schnittstelle implementieren.

-   Empfehlung: SATA-Controller sollten Native Command Queuing (NCQ) Support implementieren.

<a name="device.storage.controller.sd"></a>
## <a name="devicestoragecontrollersd"></a>Device.Storage.Controller.SD

*Definiert die Branche und der Microsoft-Standards erfüllt sein müssen*

### <a name="devicestoragecontrollersdbasicfunction"></a>Device.Storage.Controller.SD.BasicFunction

*SD Controller Grundfunktionen*

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

-   Unterstützt die SD Standard-Host-Schnittstelle (gemäß den Anweisungen in der SD 3.0 Standard).

-   Unterstützt die CMD21 eMMC HS200 optimieren.

-   Alle Interrupts sind mit Ausnahme der Puffer Lesen bereit, beim Ausführen der Prozedur tuning für SD 3.0-Geräten (CMD19) oder eMMC 4.5-Geräte (CMD21) deaktiviert werden.

-   Optimieren von Verfahren muss den Optimierung Blöcke jeweils in standard-Spezifikationen SD und eMMC definierten Standard verwenden.

-   ® 1,8 v und 3.3 v Spannungswerte Signale unterstützt.

-   Unterstützt ADMA2 (kein System DMA).

-   Registrieren ordnungsgemäß express alle Funktionen, die von den Hostcontroller in der standard-Funktionen unterstützt.

-   Byte (8-Bit), Word (16-Bit) und Word Double-Wert (32-Bit) Register Zugriffe anhand der in der standard-Host Controller-Spezifikation angegebenen Register Größe unterstützt.

-   Unterstützt schreiben schützen, in dem Schreibschutz werden angegeben durch den Wert 0.

-   1 und 4-Bit-Bus breiten unterstützt. 8-Bit-Busbreite ist auch für eMMC Controller erforderlich.

-   Unterstützt alle UHS-ich Modi (SDR50 DDR50, SDR104). HS200 ist auch für eMMC Controller erforderlich.

-   Keine retuning wird SDR50 Modus erforderlich sein.

-   Retuning darf kein Zeitgebers Software erforderlich.

-   Automatische CMD23 und automatische CMD12 unterstützt.

-   Keine das Umschalten der proprietäre Register Bits sind erforderlich sind, um alle Funktionen zu aktivieren.

-   Gemäß den standard-Spezifikation wird Taktfrequenz berechnet werden.

-   Unterstützen Sie Standardfehler Wiederherstellungsverfahren.

<a name="device.storage.controllerdrive.nvme"></a>
## <a name="devicestoragecontrollerdrivenvme"></a>Device.Storage.ControllerDrive.NVMe

*Speicher NVMe-Funktion*

### <a name="devicestoragecontrollerdrivenvmebasicfunction"></a>Device.Storage.ControllerDrive.NVMe.BasicFunction

*NVMe Gerät Anforderungen*

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

**Beschreibung**

Die folgenden Anforderungen müssen im Allgemeinen vom Gerät NVMe erfüllt sein:

-   Das Gerät muss PCIe Gen2 unterstützen oder höher.

Das Gerät muss die folgenden Modi Interrupt unterstützen:


-   Mit der angeforderten Anzahl von Interrupts ausgeführt (d. h., &gt; 1 MSI-DATEI oder MSI-X-basierten Interrupt)

-   Mit nur 1 MSI-DATEI oder MSI-X Interrupt ausgeführt

-   Mit nur 1 Zeile-basierte Interrupt ausgeführt

    -   \[Server\] MSI-X ist erforderlich

    -   \[Client\] MSI-DATEI oder MSI-X ist erforderlich

Verwenden Sie das Gerät muss die folgende Klasse und Unterklasse Codes für die Identifikation für weitere Treiber entsprechen die Hersteller- und Produkt-IDs verwendet werden sollten:

-   Basis Klasse: 01 h

-   Sub-Klasse: 08 h

-   Benutzeroberfläche: 02 h Programming

Das Gerät muss über mindestens einen erweiterbaren Firmware-Steckplatz verfügen.

\[Client\] (wenn implementiert) das Gerät muss entweder unterstützen:

-   Ein nicht betriebsbereit NVMe Power Zustand von nicht mehr als 5mW und einer Exit Wartezeit in einen betriebsbereiten Zustand von weniger als 100 ms (impliziert L1.2), eine maximale aufgeführten Stromverbrauchs oder

-   Die Möglichkeit zum Fortsetzen von D3cold (schalten Sie) innerhalb von 500 ms, während eine Eintrag Wartezeit von 1,000ms nicht überschreiten.

Hinweis: Wenn eine solche Power Status oder Funktion nicht vom Gerät bereitgestellt wird, wird Erfahrung auf verbunden Standby-Systemen durch zunehmender ausgleichen Batterie erheblich beeinträchtigt werden.

Es wird dringend empfohlen, NVMe Geräte, die mit eingeschränkte Funktionalität auf Kühlung Clientsysteme verwendet werden mindestens folgende zusätzlich zu 100 %, ein- und ausschalten Zustände unterstützen:

-   1 betriebliche Power Status (Leistungseinbußen) – so, dass erhebliche zur Einschränkung des Geräts möglich ist

-   1 nicht betriebsbereit Power-Status mit einer Resume Wartezeit von maximal 50 ms

Die folgenden Anforderungen, die das Gerät erfüllen muss sind auf Version 1.0 der offiziellen NVMe Spezifikation spezifisch:

-   3.1.1 Controller-Funktionen

    -   MPSMIN (Arbeitsspeicher Seite Größe Minimum) muss auf 0 festgelegt werden. Bit: 51:48

-   5.2 asynchronen Anforderung

    -   Fehlerereignisse als auch EFFIZIENT oder Health Statusereignisse müssen unterstützt werden, finden Sie im Abschnitt 5.12 unten.

-   5.3 e/a Abschluss Warteschlange erstellen

-   5.4 Erstellen Sie Übermittlungswarteschlange e/a

-   5.5 e/a-Abschluss-Warteschlange löschen

-   5.6 löschen Sie Übermittlungswarteschlange e/a

-   Für 5.3 über 5.6 müssen mindestens 2 Warteschlangen unterstützt werden

    -   1 Satz von e/a-einreichen und Fertigstellung Warteschlangen und 1 Satz von Admin einreichen und Fertigstellung Warteschlangen sind zulässig.

    -   Hinweis: Es wird empfohlen, mindestens 4 e/a-Warteschlangen auf Clientgeräten und 16 oder Weitere Informationen zur Server-Geräte bieten die Möglichkeit, eine Gruppe von Warteschlangen pro Prozessor auf dem System binden bereitzustellen.

-   5.7 Firmware Commit

    -   Aktivierung eines Bilds Firmware sollte ohne dem aus-und Einschalten des Geräts ausgeführt werden.

    -   Der Prozess für die Aktivierung wird erwartet, dass über einen Reset Server initiierte erreicht werden wie im Abschnitt 8.1 der Spezifikation Version 1.2a beschrieben.

-   5.8 Bild-Firmware-Download

    -   Das Gerät e/a während der Downloadphase muss kein Fehler auf und Übermitteln von Suchabfragen e/a bleibt.

-   5,9 abrufen Features – mindestens die folgenden müssen exakt gemeldet werden:

-   5.12.1.5 Fehler Wiederherstellung

-   5.12.1.6 veränderliche Schreibcache

    -   Ein veränderliche Schreibcache ist nicht zu diesen Anforderungen entsprechen, auf dem Gerät erforderlich. Dieses Feld muss genau gemeldet werden.

-   5.12.1.8 unterbrechen Sie zusammenfügenden

    -   \[Server\] erforderlich

    -   \[Client\] nicht erforderlich

-   5.12.1.11 asynchrone Ereigniskonfiguration

-   5.10 erste Seite Protokoll

    -   Das Gerät muss implementieren, und füllen Sie die Log-Seiten für Fehlerinformationen (01h) SMART mindestens / Integritätsinformationen (02h) und Informationen zum Steckplatz Firmware (03h)

-   5.11 Identifizieren der

    -   MDTS (maximale Daten übertragen Größe) muss entweder 0 (keine Einschränkung) oder mindestens 5 (128 KB). Byte: 77

        -   Hinweis: Dieser Wert erhöhen in Zukunft Überarbeitungen und der nächsten Generation Geräte mit diesem sollten entwickelt werden, berücksichtigen.

    -   NN (Anzahl der Namespaces) muss mindestens 1 sein. Bytes: 519:516

    -   FLBAS (formatiert LBA Größe) muss bit, 4 auf 0 festgelegt haben. Byte: 26

        -   Wenn das Feature Metadaten-Funktionen dieser Anforderung enthält, unterstützt wird, können sie andernfalls die werden ignoriert; d. h., iff MC Bit 1 ist auf 1 festgelegt, die oben genannten FLBAS-Anforderung gebunden werden soll. Byte: 27

    -   LBADS (LBA Datengröße) muss auf 9 oder 12, d. h., 512B oder 4 KB festgelegt werden. Bits: 23:16

        -   Andere LBA Datengrößen sind akzeptabel, solange 512B oder 4KB unterstützt wird.

    -   NGUID (Namespace Globally Unique Identifier) / EUI64 implementiert werden müssen.

        -   Der Controller ist einen global eindeutigen Namespacebezeichner in dieses Feld oder das Feld EUI64 angeben, wenn der Namespace erstellt wird.

-   5.12 festgelegt Funktionen – mindestens Folgendes implementiert werden müssen:

    -   Fehlerbehebung (05h)

    -   Veränderliche Schreibcache (06h)

        -   Wenn ein veränderliche Schreibcache auf dem Gerät vorhanden ist

    -   Anzahl von Warteschlangen (07h)

    -   Unterbrechen Sie COALESCE (08h)

    -   Asynchrone Ereigniskonfiguration (0Bh)

-   5.13 (sofern implementiert) formatieren NVM

    -   Das Gerät sollte kann zum Ausführen einer kryptografischen löschen (SES Wert 010 b) sein.

        -   Wenn kryptografische Erase nicht unterstützt wird, wird Windows nicht den Befehl FormatNVM nutzen.

    -   Format NVM muss auf einzelne Namespaces, d. h., Bit 1 und Bit 0 in der Datenstruktur Controller identifizieren Byte 524 (FNA) festzulegen, muss auf 0 festgelegt werden.

-   6,6 Freigeben von Dataset Management –

    -   Alle e/a und Deallocate Befehle sind in weniger als 500 ms auszufüllen.

    -   98,5 % der e/a-Befehle sind in weniger als 100 ms auszufüllen.

-   6.7 leeren

    -   Wenn ein flüchtiger Cache auf dem Gerät vorhanden ist

-   6.8 lesen

-   6.9 schreiben

<a name="device.storage.enclosure"></a>
## <a name="devicestorageenclosure"></a>Device.Storage.Enclosure

*Laufwerk Anlagen müssen folgenden Anforderungen erfüllen.*

### <a name="devicestorageenclosuredirectaccess"></a>Device.Storage.Enclosure.DirectAccess

*Laufwerk Anlagen müssen direkten Zugriff auf die Laufwerke, auf bereitstellen, die sie untergebracht werden.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Anlagen müssen nicht die Laufwerke, auf untergebracht werden sie als abstract (z. B. gebildet in einen logischen RAID-Datenträger).  Integrierte Switches müssen falls vorhanden, Erkennung von und den Zugriff auf alle Laufwerke in die Anlage bereitzustellen, ohne dass zusätzliche physischen Host Verbindungen.

### <a name="devicestorageenclosuredriveidentification"></a>Device.Storage.Enclosure.DriveIdentification

*Laufwerk Anlagen müssen einen Laufwerk Identification-Dienst bereitstellen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Speicher Anlage muss zur Unterstützung von Speicherkonfiguration Speicherplatz die folgenden Anforderungen erfüllen.

-   Muss die folgenden Befehle unterstützen:

    -   ABFRAGE

    -   DIAGNOSE SENDEN

    -   DIAGNOSE ERGEBNISSE ERHALTEN

    -   ANFORDERUNG SINNVOLL

    -   TEST-GERÄT BEREIT

-   Festgelegtes ENCSERV Bit auf eine in die Standard-Abfrage-Daten (SPC4) an, dass das Zielgerät Speicher muss enthält eine Komponente der eingebetteten Anlage-Dienste, die über diese logische Einheit adressierbar sind.

-   Anlage-Service-Geräte muss die folgenden diagnostic Seiten unterstützen:

    -   Unterstützte Diagnostic diagnostic Seite Seiten (00h)

    -   Diagnose-Konfigurationsseite (01h)

    -   Anlage Steuerelement diagnostic Seite (02h)

    -   Anlage diagnostic Statusseite (02h)

    -   Zusätzliche Element diagnostic Statusseite (0Ah)

-   Im Windows-Speicherplatz Feature werden die folgenden Steuerelements vom Typ und Status Elemente verwendet.

| Element-Typcode | Elementname-Typ                        |
|-------------------|------------------------------------------|
| 01h               | Gerät-Steckplatz                              |
| 02h               | Stromversorgung                             |
| 03h               | Kühlung                                  |
| 04h               | Temperatursensor                       |
| 07h               | Anlage Service-Controller Electronics |
| 12h               | Spannungssensor                           |
| 13h               | Aktueller Sensor                           |
| 17 Std               | Array Gerät Steckplatz                        |

-   Speicher Anlage muss Gerät Steckplatz (01 h) oder Elementtyp Array Gerät Steckplatz (17 h) unterstützen. Alle anderen Elementtypen (Stromversorgung, Kühlung, Temperatursensor, Anlage Service-Controller Electronics, Spannungssensor und Stromfühlers) sind optional.

<!-- -->

-   Für zusätzliche Element diagnostic Statusseite (0Ah) übermitteln Anlagen zusätzliche Element Status Deskriptor das Bit EIP (Elementindex vorhanden) auf einen:

    -   Das Index des Elements dar, das von Schächte gemeldet wird, sind in aufsteigender Reihenfolge.

    -   Der Protokollbezeichner muss auf 6 Stunden (SAS) festgelegt.

-   Das SES-Gerät muss gemeldet werden, dass dieselbe Adresse das Laufwerk für Gerät Identification VPD Seite (83h) meldet eine Bezeichnung Deskriptor einschließen soll in dem die Ziel-Port-Namen oder Bezeichner (Siehe SAM-5) angegeben wird. Die Bezeichnung Descriptor verwendet wird, sofern zutreffend, darf haben Feld ZUORDNUNG auf 01 festgelegt (d. h., Zielport) und Feld KENNZEICHNER TYP auf festgelegt:

    - 2h (d. h., EUI-64-basierten);

    - 3h (d. h., NAA); oder

    - 8h (d. h., SCSI-Zeichenfolge).

<!-- -->

-   Steuerelement Deskriptoren werden für Anlage-Steuerelement diagnostic Seite (02h) von Datenträger Schacht Anzahl in aufsteigender Reihenfolge aufgeführt.

-   T10 SES3 Spec Anlage Steuerelement diagnostic Seite und Diagnose Anlage Statusseite mit INFO 1nicht CRIT, CRIT und UNRECOV Bits implementiert entsprechen muss.

-   STATUSCODE-ELEMENT dar, in allen Formaten der Status-Element muss die folgenden Codes annehmen:

| Code     | Name              | Bedingung                                                                                                                  |
|----------|-------------------|----------------------------------------------------------------------------------------------------------------------------|
| 0h       | Nicht unterstützte       | Status-Erkennung ist für dieses Element nicht implementiert.                                                                      |
| 1h       | OK                | Element installiert ist und keine fehlerbedingungen bekannt sind.                                                                    |
| 2h       | Critical          | Kritische Bedingung erkannt wird.                                                                                            |
| 3h       | Nicht kritisch       | Nicht kritische Bedingung wird erkannt                                                                                          |
| 4h       | Nicht wiederhergestellt     | Nicht wiederherstellbare Bedingung erkannt wird.                                                                                       |
| 5h       | Nicht installiert     | Element wird in der Anlage nicht installiert.                                                                                     |
| 6h       | Unbekannt           | Sensor ausgefallen ist oder Element Status ist nicht verfügbar.                                                                      |
| 7h       | Nicht verfügbar     | Element ist installiert ist, können keine bekannten Fehlern, aber das Element nicht eingeschaltet oder in Betrieb festgelegt wurde.                       |
| 8h       | Kein Zugriff zulässig | Der Initiator-Port, von dem der Befehl DIAGNOSTIC ERGEBNIS ERHALTEN nicht empfangen wurden, hat keinen Zugriff auf dieses Element. |
| 9h, um Fh | Reserviert          |  &nbsp;          |

Hinweise: Windows korreliert Anlage Services auf Laufwerken über die auf Laufwerken geht zur Gerät Identification VPD Seite (83h) und das Protokoll spezifische Informationen mit ZUORDNUNG dar, die auf 1 festgelegt.

<a name="device.storage.enclosure.azurestack"></a>
## <a name="devicestorageenclosureazurestack"></a>Device.Storage.Enclosure.AzureStack

*Definiert die Anforderungen, die erfüllt sein müssen, wenn die Anlage Laufwerk in einer Microsoft Azure-Stapel basierte private Cloud-Lösung unterstützt wird*

### <a name="devicestorageenclosureazurestackbasicfunction"></a>Device.Storage.Enclosure.AzureStack.BasicFunction

*Mindestanforderungen für Laufwerk Anlagen in Microsoft Azure-Stapel Lösungen verwendet*

<table><tr><th>Gilt für</th><td><p>Windows Server 2016 X64</p></td></tr></table>

**Beschreibung**

Microsoft Azure-Stapel-Anforderungen für Laufwerk Anlagen werden in der folgenden Tabelle erfasst.

<table>
    <tr><th>Feature</th><th>Anforderung</th></tr>
    <tr><td rowspan="2">Device.Storage.Enclosure</td><td>Device.Storage.Enclosure.DirectAccess</td></tr>
    <tr><td>Device.Storage.Enclosure.DriveIdentification</td></tr>
    <tr><td rowspan="6">Device.DevFund.Server.Nano</td><td>Device.DevFund.Server.OperateInServerNano</td></tr>
    <tr><td>Device.DevFund.Server.Nano.Deployment</td></tr>
    <tr><td>Device.DevFund.Server.Nano.Diagnostics</td></tr>
    <tr><td>Device.DevFund.Server.Nano.PatchAndUpdate</td></tr>
    <tr><td>Device.DevFund.Server.Nano.MonitoringAndTelemetry</td></tr>
    <tr><td>Device.DevFund.Server.Nano.FirmwareUpdate</td></tr>
</table>

Zusätzlich zu den oben genannten muss die folgende Anforderungen erfüllt sein:

- Speicher Anlagen haben müssen, und melden eindeutige ID

### <a name="devicestorageenclosureazurestackcloudstress"></a>Device.Storage.Enclosure.AzureStack.CloudStress

*Laufwerk Anlagen, die Cluster-Speicher für die private Cloudlösung bereitstellen müssen diese Spezifikation entsprechen.* 

<table><tr><th>Gilt für</th><td><p>Windows Server 2016 X64</p></td></tr></table>

**Beschreibung**

Private Cloudlösungen umfassen eng integrierte Software und Hardwarekomponenten für Zweigstellenstandorte mit hoher Leistung bieten. Probleme bei der in den Komponenten (Software, Hardware, Treibern, Firmware usw.) können gefährden die Lösung und beeinträchtigt alle Versprechen bezüglich Service Level Agreement (SLA) für die private Cloud vorgenommen.

Viele dieser Probleme sind nur unter eine hohe Stress, private Cloud Simulation verfügbar gemacht. Private Cloud Simulator (PCS) können Sie zum Überprüfen der Komponente in einem cloudszenario mit und Probleme zu identifizieren. Es simuliert eine live Datacenter/Private Cloud durch VM-Arbeitslasten zu erstellen, Planen von administrative Vorgänge (Lastenausgleich, Wartung von Software/Hardware) und Einfügen von Fehlern (ungeplante Hard-und Software mit Fehlern) auf die private Cloud.

Um die Einhaltung dieser Spezifikation muss der Controller den mit dem Profil Speicher Anlage auf einer 4-Knoten-Clusterkonfiguration Testlauf PCS übergeben.

### <a name="devicestorageenclosureazurestackfirmwareupdate"></a>Device.Storage.Enclosure.AzureStack.FirmwareUpdate

*Laufwerk Anlagen, die Cluster-Speicher für die private Cloudlösung bereitstellen müssen diese Spezifikation entsprechen.* 

<table><tr><th>Gilt für</th><td><p>Windows Server 2016 X64</p></td></tr></table>

**Beschreibung**

Microsoft Azure-Stapel erfordern die Anlagen Firmware aktualisierbar sein.



<a name="device.storage.hd"></a>
## <a name="devicestoragehd"></a>Device.Storage.Hd

### <a name="devicestoragehdbasicfunction"></a>Device.Storage.Hd.BasicFunction

*Grundlegende HD-Funktionen*

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

Das Gerät muss die folgenden Szenarien durchführen:

-   Sequenzielle Lesen
-   Sequenzielle Schreibvorgänge
-   Sequenzieller überprüfen (gefolgt von Lese- und Vergleich schreiben)
-   Lesezugriff
-   Zufälliges Schreiben
-   Überprüfen Zufall

### <a name="devicestoragehdphysicalsectorsizereportsaccurately"></a>Device.Storage.Hd.PhysicalSectorSizeReportsAccurately

*Die Größe des physischen Sektor gemeldeten muss die Maßeinheit für eine unteilbare schreiben.*

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

**Folgendes gilt für Festplattenlaufwerke ATA-basiert:**

Wenn implementiert, die Unterstützung für Speichergeräten mit logischen Sektor Größen größer als 512 Bytes gemäß den ATA-8-Spezifikationen implementiert werden müssen. Näheres INCITS T13 Spezifikation Repository für den Zugriff auf die Spezifikation.

**Folgendes gilt für SCSI-basierten Festplattenlaufwerke:**

Wenn implementiert werden, die Unterstützung für Speichergeräten mit logischen Sektor Größen größer als 512 Bytes gemäß den SBC-3, SPC-4 und SAT-3-Spezifikationen implementiert werden müssen. Näheres INCITS T10 Spezifikation Repository für den Zugriff auf den jeweiligen Spezifikationen.
 
**Unternehmensvorgabe**

Einige Festplattenlaufwerke melden die physischen Sektorgröße der Festplatte nicht richtig. Das Laufwerk wird freigegeben, z. B. "4K" Laufwerk ohne meldet, dass es sich tatsächlich um ein Laufwerk 4 KB ist. Applikationen verwenden Sie die Größe des physischen Sektor gemeldeten als Konzept eines Unteilbarkeit und führen Sie anhand dieser e/a. Das grundlegenden Beispiel ist eine Datenbank-Schreibweise Anwendung nur ein Commitdatensatz innerhalb der Maßeinheit unteilbare Write konfiguriertes Verlust gespeichert werden, wenn Stromversorgung unterbrochen wurde oder wenn ein physischer Sektor physisch fehlerhaften wird. Wenn die Größe des physischen Sektor gemeldeten nicht Unit Unteilbarkeit aufweist, schwerwiegenden Zuverlässigkeit Bedenken können auftreten in Szenarien wobei ist Power wie verloren: Anwendung können nicht zum Wiederherstellen und -Benutzer müssen aus Sicherung wiederherstellen. Anwendung können nicht zum Wiederherstellen, jedoch müssen die Anwendung eine langen konsistenzprüfung ausführen. Eine Beschädigung der Metadaten, Protokolldateidaten, Benutzerdaten oder sogar Daten aus einer anderen Anwendung stammen.

### <a name="devicestoragehdrotationalrate"></a>Device.Storage.Hd.RotationalRate

*HD Rotation Rate Anforderungen an das logo*

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

Solid State-Gerät (SSD) dürfen Nominal Media Drehung Rate ein nicht gedreht mittlerer Wert festgelegt. Ein Rotation oder ein Rotation gemischt und SSD-Gerät berichtet der Rotation Rate der Rotation Medium.

Die **folgenden Informationen gelten für ATA-basierte Festplatten Datenträger**:

ATA-Festplatte Geräte müssen nominal Media Drehung Rate gemäß den ATA-8-Spezifikationen melden. Rückgabe Befehls identifizieren Gerät Word 217 darf nicht 0000 h sein.

**NOMINAL Media Drehung Rate Wertbeschreibung**

| Wert       | Beschreibung                                                                         |
|-------------|-------------------------------------------------------------------------------------|
| 0000h       | Rate nicht gemeldet                                                                   |
| 0001h       | Nicht drehen Medien (z. B. solid State-Gerät)                                       |
| 0002h - 0400h | Reserviert                                                                            |
| 0401h-FFFEh | NOMINAL Media Drehung Rate in Drehungen pro Minute (Rpm) (z. B. 7 200 u/Min = 1C20h) |
| FFFFh       | Reserviert                                                                            |

Die **folgenden Informationen gelten für SCSI-basierten Festplatten Datenträger**:

SCSI-Festplatte Gerät muss nominal Media Drehung Rate gemäß den Spezifikationen T10 SBC3 melden. Die Abfragebefehl zurückgeben Block Gerät Merkmale VPD Seite Media Drehung Rate nicht festgelegt ist 0000h =.

**MITTEL DREHUNG RATE-Feld**

| Code        | Beschreibung                                                                                              |
|-------------|----------------------------------------------------------------------------------------------------------|
| 0000h       | Mittlere Drehung Rate wird nicht angezeigt.                                                                     |
| 0001h       | Mittel nicht gedreht (z. B. solid-State)                                                                  |
| 0002h - 0400h | Reserviert                                                                                                 |
| 0401h-FFFEh | NOMINAL mittlere Drehung Rate in u/min (z. B. 7 200 u/Min = 1C20h, 10 000 u/Min = 2710 h und 15 000 u/Min = 3A98h) |
| FFFFh       | Reserviert                                                                                                 |

<a name="device.storage.hd.1394"></a>
## <a name="devicestoragehd1394"></a>Device.Storage.Hd.1394

### <a name="devicestoragehd1394compliance"></a>Device.Storage.Hd.1394.Compliance

*IEEE 1394 Festplattenlaufwerk Spezifikation compliance*

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

1394-compliance

IEEE-1394 (Firewire) Geräte müssen Serial Bus Protocol-2 (SBP-2) und SCSI primären Befehle-2 (SPC-2) einhalten, und Datenträgergeräte müssen mit SCSI reduziert Block Befehle (RBC) entsprechen.

Die Referenz für die Einhaltung der Spezifikation...: SBP-2, SPC-2, Min:RBC
 

<a name="device.storage.hd.alua"></a>
## <a name="devicestoragehdalua"></a>Device.Storage.Hd.Alua

### <a name="devicestoragehdaluacompliance"></a>Device.Storage.Hd.Alua.Compliance

*Hinsichtlich der asymmetrischen Logical Unit (ALUA)*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Wenn ein Gerät asymmetrischen logical Unit Access (ALUA) unterstützt, muss das Gerät die Anforderung Implementieren von Unterstützung für die Ziel-Port-Gruppen (TPGS) in standard Abfragedaten als SPC3-r23 Abschnitt 6.4.2 entsprechen.

Der Bericht Port Zielgruppe Befehl muss unterstützt werden, wenn logische Einheiten in der Abfrage Standarddaten meldet, dass ALUA unterstützt. Das Speichergerät SPC3 entsprechen-r23 Abschnitt 6,25 Bericht Port Zielgruppe Befehl entsprechend seiner TPGS Feldfunktion in die standard-Abfrage-Daten.
 

<a name="device.storage.hd.ata"></a>
## <a name="devicestoragehdata"></a>Device.Storage.Hd.Ata

### <a name="devicestoragehdatabasicfunction"></a>Device.Storage.Hd.Ata.BasicFunction

*ATA/ATAPI-Schnittstelle*

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

PATA-Geräte (Legacy)

(PATA-Geräte werden nicht mehr für die Übermittlung nach Juni 2013 WHQL akzeptiert).

Microsoft empfiehlt die Verwendung von SATA für neue Geräte. Dem Willen Kompatibilität mit vorhandenen Gerät Basis, werden jedoch die folgenden Anforderungen für PATA Geräte bereitgestellt.

Gemeinsam genutzten Bus-Funktionen sind für PATA-Geräte erforderlich. Geräten müssen als 0 oder 1 Gerät konfiguriert sein.
 

### <a name="devicestoragehdatadma"></a>Device.Storage.Hd.Ata.Dma

*ATA/ATAPI DMA-Modus.*

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

ATA/ATAPI DMA-Modus

Alle PATA Controller und PATA Peripheriegeräte haben extrem DMA gemäß ATA/ATAPI-7 unterstützen.

Begründung:

Zusätzlich zu den verbesserten Übertragungsraten außerdem extrem DMA fehlerprüfung für verbesserte Stabilität vorherigen PATA Implementierungen.

<a name="device.storage.hd.ataprotocol"></a>
## <a name="devicestoragehdataprotocol"></a>Device.Storage.Hd.AtaProtocol

### <a name="devicestoragehdataprotocolperformance"></a>Device.Storage.Hd.AtaProtocol.Performance

*ATA-Gerät-Leistung*

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

ATA-Gerät-Leistung

Windows 7 Windows System Assessment-Tool (WinSAT) Datenträger formelle Test für das Blockieren Speichergerät muss die folgenden leistungsanforderungen für alle sichtbar Speicher raumnutzung bis zu 95 % (% der Auslastung als % der "verwendeter Speicherplatz" angezeigt, über das Windows File System) übergeben.

-   Auf dem Datenträger sequenzielle 64 KB Byte lesen &gt;25 MB/s

-   Auf dem Datenträger zufällige 16 KB Byte lesen &gt;0,5 MB/s

-   Datenträger sequenzielle 64 KB Byte &gt;20 MB/s

-   Durchschnittliche Zeit mit sequenzielle Schreibvorgänge Read &lt;25 ms

-   Latenz: 95. Quantil &lt;120 ms

-   Wartezeit: Maximale &lt;700 ms

-   Durchschnittliche Zeit mit zufällige Schreibvorgänge lesen &lt;40 ms

### <a name="devicestoragehdataprotocolprotocol"></a>Device.Storage.Hd.AtaProtocol.Protocol

*ATA/ATAPI-Protokoll*

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

ATA/ATAPI-Protokoll
 

-   ATA/ATAPI Controller und Geräte müssen mit den folgenden Produktmärkte entsprechen.

    -   INCITS 397-2005 (1532D): am Anlage mit Paket-Schnittstelle - 7 oder höher, um auch in diesem Dokument als ATA/ATAPI-7 bezeichnet. UNTER Anlage mit Paket-Schnittstelle - 8 oder höher wird beim Überarbeitung 8 final zu betrachten und veröffentlichte ist erforderlich sein.

-   ATA/ATAPI-Controller sind Windows-Betriebssystem Boot unterstützen.

-   ATA/ATAPI-Geräte stützen sich nicht auf dem Gerät Identifizieren von Datenfeldern (61:60) und (103:100) 28 oder 48-Bit-LBA Adressierung Support zu bestimmen. ATA/ATAPI-Bit-Version 10 von Word 83 stattdessen abhängig und 10 von Word zum Identifizieren der 48-Bit-LBA-Unterstützung (gemäß den Anweisungen in ATA/ATAPI-7) Adressierung 86-bit.  

*Hinweise zum Entwurf*

Empfohlen:

Nominal Media Drehung Rate Reporting

Benötigt ein Gerät Windows Defragmentierung standardmäßig deaktiviert ist, sollte das Gerät der Nennwert Media Drehung Rate als 0001 h nicht gedreht Medien (z. B. solid State-Gerät) gemäß den Anweisungen in der ATA8 ACS1-Spezifikation, Abschnitt 7.16.7.77 melden. 

Begründung:

Beim Nominal Media Drehung Rate gemeldet vom Gerät als 0001 h Medien nicht gedreht ist, wird standardmäßig Defragmentierung der Blockspeichergerät Windows ausführen.
 

<a name="device.storage.hd.azurestack"></a>
## <a name="devicestoragehdazurestack"></a>Device.Storage.Hd.AzureStack

*Definiert die Anforderungen, die erfüllt sein müssen, wenn die Festplatte in einer Microsoft Azure-Stapel basierte private Cloud-Lösung unterstützt wird*

### <a name="devicestoragehdazurestackbasicfunction"></a>Device.Storage.Hd.AzureStack.BasicFunction

*Mindestanforderungen für Laufwerke, die in Microsoft Azure-Stapel-Lösungen*

<table><tr><th>Gilt für</th><td><p>Windows Server 2016 X64</p></td></tr></table>

**Beschreibung**

Microsoft Azure-Stapel-Anforderungen für Datenträger werden in der folgenden Tabelle erfasst.

<table>
    <tr><th>Feature</th><th>Anforderung</th></tr>
    <tr><td rowspan="3">Device.Storage.Hd</td><td>Device.Storage.Hd.BasicFunction</td></tr>
    <tr><td>Device.Storage.Hd.PhysicalSectorSizeReportsAccurately</td></tr>
    <tr><td>Device.Storage.Hd.RotationalRate</td></tr>
    <tr><td>Device.Storage.Hd.DataVerification</td><td>Device.Storage.Hd.DataVerification.BasicFunction</td></tr>
    <tr><td>Device.Storage.Hd.Flush</td><td>Device.Storage.Hd.Flush.BasicFunction</td></tr>
    <tr><td>Device.Storage.Hd.PortAssociation</td><td>Device.Storage.Hd.PortAssociation.BasicFunction</td></tr>
    <tr><td>Device.Storage.Hd.Sas</td><td>Device.Storage.Hd.Sas.ComplyWithIndustrySpec</td></tr>
    <tr><td>Device.Storage.Hd.Sata</td><td>Device.Storage.Hd.Sata.BasicFunction</td></tr>
    <tr><td>Device.Storage.Hd.Scsi.ReliabilityCounters</td><td>Device.Storage.Hd.Scsi.ReliabilityCounters.BasicFunction</td></tr>
    <tr><td rowspan="3">Device.Storage.Hd.ScsiProtocol</td><td>Device.Storage.Hd.ScsiProtocol.ReferenceSpec</td></tr>
    <tr><td>Device.Storage.Hd.ScsiProtocol.SamCompliance</td></tr>
    <tr><td>Device.Storage.Hd.ScsiProtocol.SpcCompliance</td></tr>
    <tr><td rowspan="6">Device.DevFund.Server.Nano</td><td>Device.DevFund.Server.OperateInServerNano</td></tr>
    <tr><td>Device.DevFund.Server.Nano.Deployment</td></tr>
    <tr><td>Device.DevFund.Server.Nano.Diagnostics</td></tr>
    <tr><td>Device.DevFund.Server.Nano.PatchAndUpdate</td></tr>
    <tr><td>Device.DevFund.Server.Nano.MonitoringAndTelemetry</td></tr>
    <tr><td>Device.DevFund.Server.Nano.FirmwareUpdate</td></tr>
</table>

Zusätzlich zu den oben genannten müssen die folgenden Anforderungen erfüllt sein:

- Datenträger-Geräten müssen vom und gemeldet, SATA, SAS oder NVMe Bus-Typ
- Datenträger-Geräten müssen vom und gemeldet, SSD oder HDD Medientyp
- Datenträgergeräte verfügen müssen, und melden eindeutige ID

### <a name="devicestoragehdazurestackcloudstress"></a>Device.Storage.Hd.AzureStack.CloudStress

*Datenträger, die als Cluster-Speicher für die private Cloudlösung verwendet werden müssen diese Spezifikation einhalten.*

<table><tr><th>Gilt für</th><td><p>Windows Server 2016 X64</p></td></tr></table>

**Beschreibung**

Private Cloudlösungen umfassen eng integrierte Software und Hardwarekomponenten für Zweigstellenstandorte mit hoher Leistung bieten. Probleme bei der in den Komponenten (Software, Hardware, Treibern, Firmware usw.) können gefährden die Lösung und beeinträchtigt alle Versprechen bezüglich Service Level Agreement (SLA) für die private Cloud vorgenommen. 

Viele dieser Probleme sind nur unter eine hohe Stress, private Cloud Simulation verfügbar gemacht. Private Cloud Simulator (PCS) können Sie zum Überprüfen der Komponente in einem cloudszenario mit und Probleme zu identifizieren. Es simuliert eine live Datacenter/Private Cloud durch VM-Arbeitslasten zu erstellen, Planen von administrative Vorgänge (Lastenausgleich, Wartung von Software/Hardware) und Einfügen von Fehlern (ungeplante Hard-und Software mit Fehlern) auf die private Cloud. 

Um diese Spezifikation entsprechen, muss der Datenträger PCS Testlauf mit den 'Datenträger – AzureStack' übergeben Profil in einer 4-Knoten-Clusterkonfiguration.

### <a name="devicestoragehdazurestackfirmwareupdate"></a>Device.Storage.Hd.AzureStack.FirmwareUpdate

*Datenträger, die als Cluster-Speicher für die private Cloudlösung verwendet werden müssen diese Spezifikation einhalten.*

<table><tr><th>Gilt für</th><td><p>Windows Server 2016 X64</p></td></tr></table>

**Beschreibung**

Microsoft Azure-Stapel erfordern SAS und SATA-Laufwerken Firmware über den Posteingang [Firmwareupdates Mechanismus](https://blogs.technet.microsoft.com/filecab/2016/01/25/updating-firmware-for-disk-drives-in-windows-server-2016-tp4/), eingeführt in Windows Server 2016 (Update-StorageFirmware) aktualisierbar sein.


<a name="device.storage.hd.dataverification"></a>
## <a name="devicestoragehddataverification"></a>Device.Storage.Hd.DataVerification

*Überprüfungstests ausführen, um sicherzustellen, dass kein Datenverlust oder Beschädigung Datenträger*

### <a name="devicestoragehddataverificationbasicfunction"></a>Device.Storage.Hd.DataVerification.BasicFunction

*Alle Speichergeräten müssen Windows ordnungsgemäß funktionieren.*

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

Speichergeräten müssen zuverlässig lesen und Schreiben von Daten ohne Datenverlust oder Beschädigung der Daten.

<a name="device.storage.hd.ehdd"></a>
## <a name="devicestoragehdehdd"></a>Device.Storage.Hd.Ehdd

### <a name="devicestoragehdehddcompliance"></a>Device.Storage.Hd.Ehdd.Compliance

*Verschlüsselte Festplatte erfüllt Microsoft und aus dem Gesundheitswesen Spezifikationen.*

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

Verschlüsselte Festplatte

eDrives müssen mit dieser Industrie Spezifikationen kompatibel sein.

-   IEEE 1667 IEEE 1667 2009-version

    <!-- -->

    -   Prüfpunkt Silo unterstützen
    -   Unterstützung TCG Speicher silo

    <!-- -->

-   TCG

    <!-- -->

    -   TCG Core Spezifikation, Version 2.0

    -   OPAL SSC 2.0

        <!-- -->

        -   Programmgesteuerte TPer zurücksetzen Rev
        -   Änderbare CommonName Spalte
        -   SID Autorität deaktivieren

        <!-- -->

    -   OPAL SSC Featuregruppen

        <!-- -->

        -   Set zusätzliche Datenspeicher Rev 1.05 oder höher
        -   Einzelne Benutzer Modus Rev 1.02 oder höher

        <!-- -->

-   SCSI

    <!-- -->

    -   SPC4
    -   SAT2

    <!-- -->

-   ATA-GERÄTS

    <!-- -->

    -   ACS2

eDrives müssen diese Windows-Design-Spec Anforderungen entsprechen:

-   Unterstützung von mindestens AES-128

-   Unterstützung von mindestens eines der folgenden Verschlüsselungsmodi

    <!-- -->

    -   CBC
    -   XTS

    <!-- -->

-   Mindestens 8 Bereichen zu unterstützen

-   Unterstützung für zusätzliche Daten Speichern von Tabellen

-   Unterstützung Bereich überschreiten

-   Unterstützung authenticate-Methode

-   Info zu Support geheimen Schlüssel schützen

-   Unterstützung änderbare allgemeiner name

-   Unterstützung für TCG Stack zurücksetzen

-   Unterstützt programmatischen TPer zurücksetzen

-   Unterstützung Einzelbenutzermodus

-   Wenn SCSI-devices(SPC4):-

    <!-- -->

    -   In der ABFRAGE sollten 1667 Version Deskriptor 0xFFC2 (IEEE 1667 2009) gemeldet werden. Das Feld 'Zusätzliche Länge' Datengruppe ABFRAGE muss größer als oder gleich 0x38 sein.

    -   Security-Protokoll IN Ausgabe muss 00, 01, 02, in der Liste für Security-Protokoll unterstützt Nutzlast EE melden

    <!-- -->

-   Wenn ATA-Geräte (ACS2):-

    <!-- -->

    -   Die TrustedComputer.FeatureSupported (word-48 - Bit 0 muss auf "1" festgelegt sein) muss in den Daten IDENTIFIZIEREN berichtet werden

    -   Die AdditionalSupported.IEEE1667IDENTIFY (word-69 - 7 Bit auf "1" festgelegt werden sollte) in den Daten IDENTIFIZIEREN gemeldet werden müssen

    -   Vertrauenswürdige empfangen ausgeben soll Bericht 00,01, 02, in der Liste für Security-Protokoll unterstützt Nutzlast EE

    <!-- -->

-   Wenn SATA-USB-:-

    <!-- -->

    -   Unterstützung von SAT2

    <!-- -->

-   Befehl Leistung:-das Laufwerk muss die folgenden Vorgänge ausführen, in die angegebene Dauer

| Vorgänge            | Max Fertigstellungstermin |
|-----------------------|---------------------|
| Discovery-Enumeration | 24 s (8 Balken)    |
| Aktivieren              | 45 s              |
| Zurücksetzen                | 8 s               |
| Erstellen von Band           | 1,5 s             |
| Band löschen           | 2 Sekunden               |
| Band löschen            | 2 Sekunden               |
| Festlegen von Metadaten          | 20 s              |
| Abrufen von Metadaten          | 14 s              |
| Sperre Band             | 1,5 s             |
| Entsperren von Band           | 1,5 s             |

<a name="device.storage.hd.emmc"></a>
## <a name="devicestoragehdemmc"></a>Device.Storage.Hd.EMMC

*Definiert die Branche und der Microsoft-Standards erfüllt sein müssen*

### <a name="devicestoragehdemmcbasicfunction"></a>Device.Storage.Hd.EMMC.BasicFunction

*Emmc Grundfunktionen*

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

Muss Branchenstandards unterstützen.

eMMC 4.5.1 Anforderungen

-   Beide Sektor Größe unterstützen Sie verwerfen/bereinigen und löschen Sie blockieren Grenzen.

-   Unterstützen Sie HPI/BKOPS.

-   Gepackte Befehle unterstützt.

-   HS200 Signale zu unterstützen.

-   DDR50 Signale zu unterstützen.

-   Unterstützung für eine RPMB von mindestens 128 KB in Größe und Erstellen von GPPs.

-   Ruhezustand (CMD5) unterstützen.

-   Unterstützung Kryptografie Abladung von Vorgängen (CMD53/54).

-   Unterstützung OS initiiert Cache leeren, wenn Gerät flüchtigen Cache unterstützt.

<a name="device.storage.hd.enhancedstorage"></a>
## <a name="devicestoragehdenhancedstorage"></a>Device.Storage.Hd.EnhancedStorage

### <a name="devicestoragehdenhancedstorage1667compliance"></a>Device.Storage.Hd.EnhancedStorage.1667Compliance

*Erweiterte Speichergeräten müssen die IEEE 1667 definierten Standards entsprechen.*

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

IEEE1667-Klasse (Enhanced Storage) aktiviert Speichergeräten müssen Branchenstandards erfüllen.
Erweiterte Speichergeräten müssen die IEEE 1667 definierten Standards entsprechen.

-   Erweiterte Speichergerät muss:

    -   Unterstützung den Host authentifizieren

    -   Implementieren der Unterstützung für IEEE 1667 (Version 1.1 oder höher) definiert belegen Silo auf dem Gerät.

    -   Implementieren Sie mindestens ein Zertifikat oder Kennwort Silo auf dem Gerät aus.

-   Erweiterte Speichergerät, das Zertifikat Silo implementiert muss:

    -   Laden Sie systemeigenen Windows Zertifikat Silo Treiber.

    -   Reagieren Sie auf alle Befehle der 1667 IEEE-Spezifikation, Version 1.1.

    -   Sicherstellen Sie, dass die zertifikatbasierte Authentifizierung zum Zulassen und blockieren Sie den Zugriff auf Datenträger verwendet wird.

-   Erweiterte Speichergerät, das Kennwort Silo implementiert muss:

    -   Systemeigene Kennwort Silo-Treiber laden.

    -   Reagieren Sie auf alle Befehle in der Spezifikation IEEE 1667 Kennwort Silo. 

    -   Stellen Sie sicher, dass Authentifizierung zulassen und blockieren Sie den Zugriff auf den Datenträger verwendet wird.

*Hinweise zum Entwurf*

Abrufen von IEEE 1667 Spezifikation von IEEE am folgenden Speicherort:<http://go.microsoft.com/fwlink/?LinkID=110100>

<a name="device.storage.hd.fibrechannel"></a>
## <a name="devicestoragehdfibrechannel"></a>Device.Storage.Hd.FibreChannel

### <a name="devicestoragehdfibrechannelcompliance"></a>Device.Storage.Hd.FibreChannel.Compliance

*Fibre Channel-Geräte*

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

Fibre Channel-Geräte müssen mit Fibre Channel-Protokoll für SCSI, zweite Version (FCP-2) entsprechen oder höher. Um die Interoperabilität auf den Ebenen Stromversorgung und Signalübermittlung gewährleisten Fibre Channel-Geräte müssen dritten Generation Fibre Channel physischen und einhalten Signale-Schnittstelle (früher ANSI X3. 303:1998).
 

<a name="device.storage.hd.flush"></a>
## <a name="devicestoragehdflush"></a>Device.Storage.Hd.Flush

### <a name="devicestoragehdflushbasicfunction"></a>Device.Storage.Hd.Flush.BasicFunction

*Mit diesem Befehl Abschluss*

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

Standard – Spezifikation branchenanforderungen:
 

-   Für ein ATA-Gerät CACHE zu LEEREN (E7h, nicht-Daten) 28-Bit-Befehl ist optional für ATA-Geräte und ATAPI-Geräte. FLUSH CACHE EXT (EAh, nicht-Daten) 48-Bit-Befehl für Geräte implementieren die Featuregruppe der 48-Bit-Adresse obligatorisch ist.

-   Bei einem SCSI-Gerät muss Befehl SYNCHRONIZE CACHE (10) und/oder Befehl SYNCHRONIZE CACHE (16) implementiert werden.

Windows-Design-Spec Anforderungen - Festplatte:

-   Korrigieren der Fertigstellung Reporting: Wenn das Betriebssystem einen Befehl flush Cache ausgibt, das Speichergerät sollten synchron melden den Abschluss des Befehls nur, wenn der Inhalt des Caches beibehalten wurde.

Hinweis: Die Anforderung ist nicht mit Laptop anwendbar.

<a name="device.storage.hd.iscsi"></a>
## <a name="devicestoragehdiscsi"></a>Device.Storage.Hd.Iscsi

### <a name="devicestoragehdiscsibasicfunction"></a>Device.Storage.Hd.Iscsi.BasicFunction

*iSCSI-Geräte*

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

iSCSI-Geräte iSCSI-Geräte müssen RFC3720, RFC3721 und RFC3723 entsprechen.

-   Gerät müssen mithilfe des Microsoft iSCSI-Initiators testen.

-   Gerät muss Ping (ICMP) empfangen und Senden von Ping (ICMP) sein.

-   Die folgenden Features von iSCSI-Protokoll sind erforderlich:

-   Ziele zu senden.

-   Authentifizierung bei der Anmeldung: CHAP und keine Authentifizierung. Ziele können Radius-Authentifizierung CHAP delegieren.

-   Ermittlung Sitzung Anmeldung Schlüssel/Wert-Paare: InitiatorName des SessionType und Authentifizierungsmethode.

-   Normal Sitzung Anmeldung Schlüssel/Wert-Paare: InitiatorName, des SessionType, Authentifizierungsmethode und Zielname.

-   DataPDUInOrder.

-   DataSequenceInOrder.

-   DefaultTime2Wait.

-   DefaultTime2Retain

-   ErrorRecoveryLevel = 0.

-   Ziele, mit die unterschiedliche können geheime für verschiedene Initiator Namen.

Die folgenden Features von iSCSI-Protokoll müssen übergeben testen, wenn sie implementiert werden:

-   Gegenseitige CHAP.

-   Zeilen HeaderDigest: CRC32 und keine Authentifizierung.

-   Data: CRC32 und keine Authentifizierung.

-   InitialR2T.

-   IPsec; Wenn Sie IPsec verwenden, muss Hauptmodus verfügbar sein. Darüber hinaus sind die folgenden Elemente erforderlich, wenn IPsec implementiert wird:

    <!-- -->

    -   IPSec-Transportmodus muss implementiert werden.

    -   Internet Key Exchange (IKE) Implementierungen müssen Hauptmodus und vorinstallierte Schlüssel unterstützen. Zielportale mit derselben IP-Adresse müssen die identische Hauptmodus IKE-Richtlinie zu erwarten.

    -   Ziele und Initiatoren müssen verschiedene vorinstallierten Schlüssel für verschiedene Bezeichner Nutzlast zulassen.

    -   Ziele und Initiatoren müssen statische IP-Adressen für Hauptmodus aufweisen.

    -   Zusätzliche Standard Abfragedaten VERSION DESKRIPTOREN (SPC-3) sind erforderlich

    -   Mindestens ein iSCSI VERSION DESKRIPTOR erforderlich ist (Wert = 0960h).

<a name="device.storage.hd.mpio"></a>
## <a name="devicestoragehdmpio"></a>Device.Storage.Hd.Mpio

### <a name="devicestoragehdmpiobasicfunction"></a>Device.Storage.Hd.Mpio.BasicFunction

*RAID-Implementierungen integrieren, die Bereitstellung einer Lösung Multipathing müssen mit Microsoft Multipfad e/a (MPIO) entsprechen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Intern oder externe RAID-Implementierungen, die eine Multipathing Lösung bereitstellen müssen Microsoft Multipfad-e/a (MPIO) entsprechen. Windows Multipathing Solutions müssen von einem Gerät bestimmte Modul (DSM) mithilfe von Microsoft MPIO DDK erstellt bestehen und alle Anforderungen dargelegten des Multipfad-e/a-Programm zu entsprechen.
Die folgenden WMI-Klassen muss 3. Partei DSM implementiert werden.

-     DSM\_QuerySupportedLBPolicies

-     DSM\_QueryUniqyeId

3. Partei DSM muss kleine, major Versionsnummern für die DSM melden.
 

<a name="device.storage.hd.multipleaccess"></a>
## <a name="devicestoragehdmultipleaccess"></a>Device.Storage.Hd.MultipleAccess

*Laufwerke, die mehrere Zugriff unterstützen müssen folgenden Anforderungen erfüllen.*

### <a name="devicestoragehdmultipleaccessmultipleports"></a>Device.Storage.Hd.MultipleAccess.MultiplePorts

*Mit mehreren Ports Laufwerke müssen symmetrischen Zugriff bereitstellen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Mit mehreren Ports Laufwerke müssen den gleichen Satz von Befehlen auf alle Ports unterstützen.  Laufwerke müssen nicht unterschiedlichem Verhalten oder verschlechtert sich die Leistung für Befehle basierend auf welcher Port für die Übermittlung Befehl verwendet wird.

Wenn Laufwerke mit einem Host über mehrere Pfade verbunden sind, müssen die Laufwerke, auf Windows e/a Multipfad-Projektmappe mit dem Microsoft Gerät bestimmten Modul (DSM) verwenden.

Beispiel: Laufwerke müssen die gleiche Leistung für Data Access-Befehle und dasselbe Verhalten für permanente Reservierung Befehle wie darin enthalten, wenn die Befehle auf dem gleichen Port eintreffen an unterschiedlichen Ports eintreffen angeben.

Die Leistungseinbußen zwischen zwei Ports sollte in einem Bereich von 10 %.

Hinweise: Multi-port Laufwerke möglicherweise für eine oder mehrere Computer Hosts über einen oder mehrere Pfade pro Host verbunden sein.  Herstellen einer Verbindung mit einem Laufwerk zu mehreren Hosts ermöglicht Windows das Laufwerk als Teil eines Failoverclusters der Hosts verwenden.  Herstellen einer Verbindung mit einem Laufwerk mit einem einzelnen Host über mehrere Pfade kann fortsetzen, um Zugriff auf das Laufwerk im Fall eines Ausfalls Kabel bereitzustellen.  Windows unterstützt die Verwendung von diese Verbindung Topologies unabhängig und gemeinsam.

<a name="device.storage.hd.multipleaccess.persistentreservation"></a>
## <a name="devicestoragehdmultipleaccesspersistentreservation"></a>Device.Storage.Hd.MultipleAccess.PersistentReservation

*Festplatten, die Persistent Reservierungen unterstützen müssen folgenden Anforderungen erfüllen.*

### <a name="devicestoragehdmultipleaccesspersistentreservationbasicfunction"></a>Device.Storage.Hd.MultipleAccess.PersistentReservation.BasicFunction

*Laufwerke müssen beständige Reservierungen bereitstellen.*

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

Laufwerke müssen beständige Reservierungen gemäß den Anweisungen in der primären SCSI-3-Befehle (SPC-3)-Spezifikation implementieren.  Windows hängt ordnungsgemäße Verhalten für das unten permanente Reservierung Funktionen.
 

-   PERSISTENT RESERVE UNTER lesen Keys (00h)
-   PERSISTENT RESERVE lesen RESERVIERUNG (01h)
-   PERSISTENT RESERVE OUT Reserve (01h)
    -   Reichweite: LU\_BEREICH (0h)
    -   Typ: Schreiben Sie Exclusive - nur Teilnehmer (5 Stunden)
-   PERSISTENT RESERVE OUT Release (02h)
-   PERSISTENT RESERVIEREN SIE Clear (03h)
-   PERSISTENT RESERVE, haben Vorrang vor (04h)
-   PERSISTENT RESERVE OUT Register UND vorhandenen Schlüssel (06h) ignorieren
-   PERSISTENT RESERVE OUT Register (00h)

Hinweise: Windows physische Datenträgern können Sie einen Speicherpool bilden.  Aus dem Speicherpool können Windows virtuelle Festplatten aufgerufen Speicherplätze definieren.  Ein Failovercluster kann den Pool von physischen Datenträgern, die Speicherplätze, den, die Sie definieren, und die darin enthaltenen Daten hoch verfügbar machen.  Zusätzlich zu den standardmäßigen HCT Qualifikation sollten physische Datenträgern auch das Tool "Microsoft Cluster Configuration Validation Wizard" (ClusPrep) übergeben.

<a name="device.storage.hd.offloadeddatatransfer"></a>
## <a name="devicestoragehdoffloadeddatatransfer"></a>Device.Storage.Hd.OffloadedDataTransfer

*Windows ausgelagerten Datenübertragung*

### <a name="devicestoragehdoffloadeddatatransfercopyoffload"></a>Device.Storage.Hd.OffloadedDataTransfer.CopyOffload

*Wenn Kopie Abladung unterstützt wird, müssen diese Anforderungen implementiert werden.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

**Standard – Spezifikation branchenanforderungen:**

-   Ziele, die die Windows Kopie des Features unterstützen müssen die T10 XCOPY Lite-Spezifikation (11 059r8) implementieren:

    <!-- -->

    -   Unterstützte VPD Seiten (muss ECOP VPD Seite (Seite Code 8Fh) in der Liste der unterstützten VPD Seite enthalten)

    -   ECOP VPD Seite oder ECOP VPD Seite (Seite Code 8Fh) + Block Gerät ROD Grenzwerte ECOP Deskriptor (0000h)

    -   Block Grenzwert VPD Seite (Seite Code B0h)

    -   Entsprechend der Spezifikation für T10 11 059r8, nimmt Windows 83 h lokal Code + 10 Service Aktionscode für AUFFÜLLEN TOKEN und 83 h lokal Code + 11 Service Aktionscode für Befehle MITHILFE von TOKEN SCHREIBEN.

    -   Gemäß der Spezifikation T10 11 059r8, nimmt Windows 84 h lokal Code + 07 Service Aktionscode für den Befehl ROD TOKENINFORMATIONEN EMPFANGEN. Antwort Aktionsfeld-service und command, dass Parameter mit T10 XCOPY Lite-Spezifikation (11 059r8) kompatibel sein müssen.

**Windows-Design-Spec Anforderungen:**

-   Windows sendet während der Ziel-Gerät-Aufzählung um eine Abfrage für unterstützt VPD Seiten VPD Seite nach unten. Wenn in der Liste der unterstützten VPD Seite 8F enthalten ist, wird Windows für die Seite ECOP VPD und BLOCKIEREN Grenzwerte VPD Seite Abfragen.

-   Implementierung und Fehlerbehandlung mit Parametern der ECOP VPD Seite

    <!-- -->

    -   Die MAXIMALE BEREICH DESKRIPTOREN - übersteigt die Anzahl der Block Gerätedeskriptoren Bereich eines Befehls TOKEN AUFFÜLLEN oder SCHREIBEN TOKEN MITHILFE der MAXIMALEN BEREICH GELANGEN, dürfen Kopie-Manager den Befehl mit dem Status ÜBERPRÜFEN BEDINGUNG mit dem Sinne Schlüssel UNZULÄSSIGE ANFORDERN und den zusätzlichen Sinne Zeichensatz mit ZU VIELEN SEGMENT DESKRIPTOREN festlegen enden.

    -   Die MAXIMALE INAKTIVITÄT TIMER (MAXIMALE IAT) - das ZEITLIMIT für INAKTIVITÄT eines Befehls TOKEN AUFFÜLLEN überschreitet die MAXIMALE INAKTIVITÄT-TIMER, dürfen Kopie-Manager den Befehl mit dem Status ÜBERPRÜFEN BEDINGUNG mit dem Sinne Schlüssel festlegen UNZULÄSSIGE ANFORDERN und den zusätzlichen Sinne Zeichensatz mit UNGÜLTIGEN FELD IN PARAMETER LISTEN enden.

    -   Die GRÖßE des TOKENS DATENÜBERTRAGUNG-

        -   Ist die Summe der ANZAHL DER LOGISCHEN BLÖCKE Felder in alle blockieren Bereich Gerätedeskriptoren des Befehls VERWENDEN TOKEN SCHREIBEN größer als die MAXIMALGRÖßE des TOKENS ÜBERTRAGEN, dürfen Kopie-Manager den Befehl mit dem Status ÜBERPRÜFEN BEDINGUNG mit dem Sinne Schlüssel festgelegt UNZULÄSSIGE ANFORDERN und den UNGÜLTIGEN FELD IN PARAMETER Liste Zeichensatz zusätzliche Sinne enden.

        -   Ist die Summe der ANZAHL DER LOGISCHEN BLÖCKE Felder in alle blockieren Bereich Gerätedeskriptoren von TOKEN AUFFÜLLEN größer als die MAXIMALGRÖßE des TOKENS ÜBERTRAGEN, dürfen Kopie-Manager den Befehl mit dem Status ÜBERPRÜFEN BEDINGUNG mit dem Sinne Schlüssel festlegen UNZULÄSSIGE ANFORDERN und den zusätzlichen Sinne Zeichensatz mit UNGÜLTIGEN FELD IN PARAMETER LISTEN enden.

    <!-- -->

-   Implementierung und Fehlerbehandlung mit den Parametern Block Grenzwerte VPD Seite

-   Das MAXIMALLÄNGE der ÜBERTRAGUNG Feld gibt an, die Übertragung maximale Länge in Blöcke, die für einen einzelnen BLOCKIEREN GERÄT BEREICH DESKRIPTOR Copy Manager akzeptiert. Wenn Sie ein Kopie Manager erhält eine Anforderung für eine ANZAHL VON LOGISCHEN BLÖCKE überschreiten, dass dieses Maximum, und klicken Sie dann auf Copy Manager den Befehl mit dem Status ÜBERPRÜFEN BEDINGUNG mit dem Sinne Schlüssel so festgelegt, UNZULÄSSIGE ANFORDERUNG und den zusätzlichen Sinne Zeichensatz mit UNGÜLTIGEN FELD IN PARAMETER LISTEN beendet wird.

-   Speicherarray muss sowohl synchrone und asynchrone AUFFÜLLEN TOKEN und VERWENDEN von TOKEN SCHREIBEN T10 11 059r8, 11 078r4 und 11 204r0 Spec unterstützen.

-   Speicherarray muss synchrone TOKEN FÜLLEN und VERWENDEN von TOKEN SCHREIBEN Befehle in sehr kurzer Zeit (4 Sekunden) ausführen, ohne dass eine beliebige Befehlstimeout SCSI.

**Anforderungen an die Benutzer wünschen:**

-   Zurückgreifen auf älteren Kopie - Windows-Offloading Kopiervorgang muss zurückgreifen legacy Kopiervorgang, wenn eine Kopie Abladung Fehler oder Einschränkung gemeldet wird.

-   Und drop kopieren Erfahrung – müssen sein können Support Drag & Drag & drop Kopie mit Copy-Offloading kann Speicher Zielgerät.

<a name="device.storage.hd.persistentreservation"></a>
## <a name="devicestoragehdpersistentreservation"></a>Device.Storage.Hd.PersistentReservation

### <a name="devicestoragehdpersistentreservationclusterfailover"></a>Device.Storage.Hd.PersistentReservation.ClusterFailover

*Cluster-Failover für RAID-Arrays Systeme*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

**Erforderlich**: alle Microsoft MPIO gerätespezifischen Module (DSM) müssen Windows Hardwarezertifizierung qualifizierten und registrieren und Aufheben der Registrierung persistent Reservierungen für alle Pfade zu unterstützen.

Hinweise zum Entwurf:

-   Alle Hostbusadapter (HBA) auf den Knoten im Cluster Failover verwendet können nur einen Windows Hardwarezertifizierung qualifizierten Miniporttreiber basierend auf dem Storport Miniport-Modell.

-   Alle Multipfad e/a-Lösungen in hochverfügbare Failoverclustern genutzt Microsoft MPIO basieren.

-   Es wird empfohlen, dass zusätzlich zu den standardmäßigen HCT Qualifikation alle Lösungen auch mit dem Tool "Microsoft Cluster Configuration Validation Wizard" (ClusPrep) überprüft werden.

-   FC und iSCSI-besonders Serial-attached SCSI (SAS) Failover Cluster-Lösungen können nicht auf RAID HBAs erstellt werden dabei Zwischenspeichern und/oder RAID-Konfiguration bestimmter Computer/Knoten ist. Das RAID legen Informationen und Hardwarecache muss sich in einer einzigen freigegebenen Punkt, der in einer externen Speichercontroller befindet sich befinden.

-   SAS, FC und iSCSI-haben keine Einschränkungen hinsichtlich der Anzahl der Knoten, die sie unterstützen (die derzeit 8nodes ist).

Hinweis: Legacy paralleles SCSI-Servercluster waren auf einer maximalen Größe von 2 Knoten beschränkt.

-   Nur SAS-Geräte unter Verwendung des Transports seriellen SCSI-Protokoll (SSP) werden in Failoverclustern (einschließlich SAS JBOD oder SAS SSP RAID-Systemen) unterstützt. SATA-Geräte, die an eine SAS-Domäne muss ein Teil eines RAID-Systems.

-   Direkte SATA Anfügen und SATA JBOD wird nicht unterstützt; das System muss RAID enthalten.

-   Wenn die Systemdatenträgern angefügt sind, ein Bustyp, der ist kein gültiger geben für freigegebenen Speicher (etwas andere dann FC, iSCSI, oder SAS), klicken Sie dann die Festplatten des Systems, und freigegebener Speicher auf separaten physischen Controller/Hostbusadapter sein.

<a name="device.storage.hd.portassociation"></a>
## <a name="devicestoragehdportassociation"></a>Device.Storage.Hd.PortAssociation

*Laufwerke müssen Port Zuordnung bereitzustellen.*

### <a name="devicestoragehdportassociationbasicfunction"></a>Device.Storage.Hd.PortAssociation.BasicFunction

*Laufwerke müssen Port Zuordnung bereitzustellen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Ein Laufwerk muss seine Portadresse für Geräte-Identifikation VPD Seite 83 h Abfrage Zuordnungstyp 1 (Port Association) melden.  Dies muss die gleiche Adresse das Laufwerk ein Gerät SCSI-Anlage Services (SES) und das Gerät SES stellt Berichte über SES diagnostic Seite 0Ah mit Protokollbezeichner auf 6 Stunden festgelegt.

Hinweise: Windows hängt Laufwerk Anlagen zur Bereitstellung von Funktionen wie Laufwerk Steckplatz Identifikation und visual Laufwerk Angaben (häufig als Laufwerk LED implementiert) SCSI-Anlage Services (SES) ab.  Windows ermittelt ein Laufwerk in eine Anlage mit SES Identification-Funktionen über das Laufwerk Portadresse.  Computer als Host fungiert möglicherweise getrennt von Anlagen Laufwerk oder Laufwerk Anlagen integriert werden können.

<a name="device.storage.hd.raidarray"></a>
## <a name="devicestoragehdraidarray"></a>Device.Storage.Hd.RaidArray

### <a name="devicestoragehdraidarraybasicfunction"></a>Device.Storage.Hd.RaidArray.BasicFunction

*RAID-Array-Systeme*

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

RAID-Anforderungen

RAID-Systeme und Geräte müssen Befehle von SBC-2 (oder höher) unterstützen unabhängig von der Laufwerk-Schnittstelle implementiert.

RAID-Controller und RAID-Systeme müssen unterstützen, mindestens eine der: RAID1, RAID 5, RAID6 oder RAID 1/0.

Externe RAID-Arrays müssen ein fehlerhaftes Laufwerk zulassen, das ohne beendet oder angehalten werden muss das System manuell ersetzt werden redundante ist. Dies umfasst, jedoch ist nicht beschränkt auf, in eine Spiegelung auf einem physischen Laufwerk ersetzt durch "solches" und das erste fehlerhafte Laufwerk in einem RAID-Level-5-Array-Laufwerke. RAID-Subsystems muss auch verloren gegangene Daten neu erstellt werden, ohne eine Störung Systemvorgänge zulassen. Es wird erwartet, dass während der Wiederherstellung RAID-Arrays Durchsatz betroffen sind.

### <a name="devicestoragehdraidarraybitlocker"></a>Device.Storage.Hd.RaidArray.BitLocker

*BitLocker muss auf Speicherarrays nicht Daten beschädigen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

BitLocker muss ordnungsgemäß Inhaltsdaten auf Speicherarrays schützen aktiviert sein.

**Unternehmensvorgabe**

(1) Wenn Sie ein Server in einer Umgebung ohne angemessene physische Sicherheit befindet, schützt BitLocker Daten auf dem Server vor nicht autorisiertem Zugriff bei Diebstahl ein Servers an. (2) Wenn Hostinganbieter Dienst einem neuen Zweck zuführen oder außer Betrieb Speicherarrays nehmen, wird verhindert, dass Datenträger-BitLocker-Verschlüsselung Daten Verletzung.

<a name="device.storage.hd.readzeroontrimunmap"></a>
## <a name="devicestoragehdreadzeroontrimunmap"></a>Device.Storage.Hd.ReadZeroOnTrimUnmap

### <a name="devicestoragehdreadzeroontrimunmapbasicfunction"></a>Device.Storage.Hd.ReadZeroOnTrimUnmap.BasicFunction

*Die Anforderung bezieht sich auf Festplatten.*

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

Der logische Block provisioning lesen (LBPRZ) Nullen auf eine Bit festgelegt ist, dann der Geräteserver setzt alle Bits 0 (null) im Data-In Puffer für ein Lesevorgang auf eine nicht zugeordnete LBA (freigegeben oder verankertes).

<a name="device.storage.hd.removablemedia"></a>
## <a name="devicestoragehdremovablemedia"></a>Device.Storage.Hd.RemovableMedia

*Definiert die Anforderungen, die erfüllt sein müssen, ob der Speicher Wechselmedium, d. h., es RMB bit auf 1 festgelegt ist.*

### <a name="devicestoragehdremovablemediabasicfunction"></a>Device.Storage.Hd.RemovableMedia.BasicFunction

*Geräte mit true Speichermedien*

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

Gerät mit true Speichermedien sollten als True Wechselmedium melden (RMB = 1) entsprechend der SPC-4 Revision 29, Abschnitt 6.4.2.

<a name="device.storage.hd.sas"></a>
## <a name="devicestoragehdsas"></a>Device.Storage.Hd.Sas

### <a name="devicestoragehdsascomplywithindustryspec"></a>Device.Storage.Hd.Sas.ComplyWithIndustrySpec

*Serielle angeschlossene SCSI-Geräte müssen aus dem Gesundheitswesen Spezifikationen entsprechen.*

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

Die Referenz für die Einhaltung der Spezifikation. Als Min nicht anders angegeben, ist die Baseline-Spezifikation erforderlich. "MAK:" gibt die bevorzugte Version der Spezifikation. Wenn nicht anders angegeben, wird die angegebene Version die Mindestanforderung. Sofern nichts anderes angegeben ist, müssen der genannten Spezifikationen, die von der Stelle Standards als obligatorisch klassifiziert werden alle Features implementiert werden.

SAS-1, SAM-3, SPC-3, Min:SBC-2, MAK: SBC-3

Serial Attached SCSI-Geräten Einhaltung der Serial Attached SCSI (SAS)-Spezifikation 1 oder höher.

-   Darf nicht mehr als 10 % e/a-Leistungseinbußen verursachen, wenn in einer MPIO Konfiguration Speichergerät SAS verwendet wird.

-   SAS Speichergerät knüpft eine ÜBERPRÜFUNG der EINHEIT nach Erkennung der folgenden Ereignisse.

    <!-- -->

    -   Schalten Sie
    -   Setzen
    -   Logische Einheit zurücksetzen
    -   Ich\_T Nexus Verlust
    -   Stromausfall erwartet

    <!-- -->

-   SAS SSD muss folgende T10 SCSI-Befehl Spezifikation implementieren:

    -   Lesen Sie die Kapazität (16)
    -   Block Grenzwert VPD Seite (B0h Seite Code)
    -   Block Gerät Merkmale VPD Seite (Seite Code B1h)
    -   Logische Provisioning VPD Seite (Seite Code B2h) blockieren
        -   SAS-Geräte müssen in der SAM-5-Spezifikation (T10) beschriebenen Aufgabe abbricht Funktionalität unterstützt.

-   SAS SSD muss die folgenden Anforderungen erfüllen:

    -   SAS SSD Zielgerät muss Rendite MITTEL DREHUNG = 0001h (nicht gedreht Mittel)

    -   SAS SSD Zielgerät muss zurückgeben lesen Kapazität (16) Befehl mit LBPME bit auf 1 und Provisioning Feld festgelegt = 0 (000 b) meldet einen Typ bereitstellen oder 1 (001 b) Ressource bereitgestellt in der logischen Block Provisioning VPD Seite (Seite Code B2) nicht.

    -   SAS SSD-Gerät muss Block Grenzwert VPD Seite (Seite Code B0h) implementieren und die folgenden Parametern unterstützen.

        <!-- -->

        -   MAXIMALE ANZAHL LBA AUFHEBEN
        -   MAXIMUM BLOCK DESKRIPTOR COUNT AUFHEBEN
        -   OPTIMALE GRANULARITÄT AUFHEBEN
        -   AUFHEBEN DER ZUORDNUNG VON GRANULARITÄT AUSRICHTUNG
        -   UGAVALID-Bit

    -   SAS SSD Zielgerät muss logische Block Provisioning VPD Seite (Seite Code B2h) implementieren und unterstützt die folgenden Parameter:

        -   LBPU-bit
        -   LBPRZ bit
        -   Die Bereitstellung von Typ dar.

    -   SAS SSD muss Befehl AUFHEBEN (10) unterstützen, und das LBPU Bit in LBP VPD Seite muss auf eine festgelegt.

        -   Wenn das Gerät eine Seek beeinträchtigt (SMR) meldet, gelten die folgenden Schwellenwerte:

            -   98,5 % der alle e/a müssen innerhalb von 200 ms
            -   100 % der alle e/a muss innerhalb 1,000ms abgeschlossen.

        -   Andernfalls (SSD):

            -   98,5 % der alle e/a müssen innerhalb von 100 ms
            -   100 % der alle e/a müssen innerhalb von 500 ms

<!-- -->

-   Wenn das LBPME Bit in ReadCapacity(16) zurück auf 1 festgelegt ist, muss das Gerät SAS SSD logischen Block Provisioning VPD Seite (Seite Code B2h) unterstützen.

-   Wenn das LBPRZ Bit in ReadCapacity(16) zurück auf 1 festgelegt ist, muss das Gerät SAS SSD auf einen LBPRZ Bit der logischen Block Provisioning VPD Seite festgelegt.

(Sofern implementiert) Firmware herunterzuladen und zu aktivieren

Implementieren die Möglichkeit zum Herunterladen und Aktivieren von Firmware, d. h., SAS-Geräte command-PUFFER SCHREIBEN werden auf folgende Weise Verhalten:

-   Modus 0Eh (herunterladen Microcode mit Offsets, speichern und zurückstellen aktivieren) und 0Fh (Activate verzögert Microcode) des Befehls SCHREIBEN PUFFER vom Gerät unterstützt werden.

-   Das Gerät muss beständiger Reservierungen bis zum Firmware Download/Aktivieren des Lebenszyklus beibehalten werden.

-   Das Gerät muss VPD Seite 0 x 83 durch Download beibehalten und Aktivieren eines Bilds Firmware.

-   Der Downloadvorgang muss möglich mit SCSI-Puffer-ID 0 und eine Übertragungsgröße 64 KB sein.

-   Ausführung des Befehls PUFFER zu SCHREIBEN (Unterbefehl 0Eh) darf nicht verhindern, dass die Ausführung von anderen lesen oder Schreiben von e/a in der Gerätewarteschlange. Kein e/a-Fehler wird während des Herunterladens (Unterbefehl 0Eh) erwartet.

-   Wenn während der Aktivierung (Unterbefehl 0Fh) – e/a aus anderen Initiatoren ausgefallen ist müssen mit Sinne Code MICROCODE GEÄNDERT WURDE Fehler auf.

-   Der Aktivierungsprozess muss auftreten, ohne dass des Hosts ein-/ausschalten oder bus-Reset, d. h., Aktivierung über einen internen Zurücksetzen des Laufwerks SAS ausgeführt werden muss.

<a name="device.storage.hd.sata"></a>
## <a name="devicestoragehdsata"></a>Device.Storage.Hd.Sata

### <a name="devicestoragehdsatabasicfunction"></a>Device.Storage.Hd.Sata.BasicFunction

*ATA-Gerät-Leistung*

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

SATA-Geräte: 

SATA-Geräte: 

-   Anforderung: SATA-Geräte sind die Anforderungen des seriellen ATA-GERÄTS entsprechen: hohe Geschwindigkeit serialisiert unter Anlage, Version 2,6 oder höher.

-   Empfehlung: SATA-Geräte sollten Power-Management Schnittstelle implementieren.

-   Empfehlung: SATA-Geräte sollten Native Command Queuing (NCQ) Support implementieren.

-   Hot-Plug:

    -   Hot-Plug-Unterstützung ist erforderlich, wenn das Gerät an einen Anschluss als "extern" markiert verbunden ist. Ein Port gilt als "externe", wenn eine der folgenden Register-Einstellungen (entsprechend der AHCI Branche Spec) zutrifft:

        -   PxCMD.HPCP = 1 oder,

        -   CAP HAT. SXS = 1 und PxCMD.ESP = 1 oder

        -   CAP HAT. SMPS = 1 und PxCMD.MPSP = 1

    -   Wenn das Gerät an einen Anschluss als "intern" markiert angeschlossen ist muss kein Interrupt für ein hot-Plug-Ereignis generiert werden

(Sofern implementiert) Firmware herunterladen und aktivieren

Implementieren die Möglichkeit zum Herunterladen und Aktivieren von Firmware, d. h., SATA-Laufwerken Befehl HERUNTERLADEN MICROCODE DMA (GERÄT IDENTIFIZIEREN word 69 Bit 8 == 1) oder Befehl MICROCODE HERUNTERLADEN (GERÄT IDENTIFIZIEREN word 83 Bit 0 == 1) wird wie folgt Verhalten:

-   Das Gerät muss die folgenden IDENTIFIZIEREN Gerätedaten durch Download beibehalten und Aktivieren eines Bilds Firmware: Herstellerklassen-ID, Modell-ID, Seriennummer.

-   Der Aktivierungsprozess muss auftreten, ohne dass des Hosts ein-/ausschalten oder bus-Reset, d. h., Aktivierung über einen internen Zurücksetzen des Geräts SATA ausgeführt werden muss.

-   \[DMA\] das Laufwerk wird GERÄT IDENTIFIZIEREN Protokoll Datenseite 03h unterstützen.

    -   Das Feld "DM OFFSETS ZURÜCKGESTELLT UNTERSTÜTZTE Bit" festgesetzt auf 1 fest, was bedeutet, dass die Befehle 0EH und 0FH unterstützt werden.

-   \[DMA\] Unterbefehl 0Eh "herunterladen mit Offsets und speichern Microcode für die zukünftige Verwendung" des Befehls HERUNTERLADEN MICROCODE DMA unterstützt werden.

-   \[DMA\] Unterbefehl 0Fh "Activate heruntergeladen Microcode" des Befehls HERUNTERLADEN MICROCODE DMA unterstützt werden.

Hinweis: Eine DMA Implementierung dieser Befehle ist bevorzugte aber nicht erforderlich

<a name="device.storage.hd.sata.hybridinformation"></a>
## <a name="devicestoragehdsatahybridinformation"></a>Device.Storage.Hd.Sata.HybridInformation

*Dieses Feature ist für alle Geräte, die das Feature Hybrid Informationen zu unterstützen.*

### <a name="devicestoragehdsatahybridinformationbasicfunction"></a>Device.Storage.Hd.Sata.HybridInformation.BasicFunction

*SATAIO Hybrid Laufwerk Anforderungen*

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

Die folgenden Funktionen und Anforderungen müssen vom Gerät unterstützt werden, und finden Sie unter Hybridgeräten im Allgemeinen. Sie sind für die Verwendung mit der Windows-Box-Treiber (StorAHCI.sys) erforderlich.

Wenn ein Laufwerk selbst als Hybrid-Laufwerk meldet, müssen sie einen sich drehenden Datenträger und mindestens eine Komponente von permanenten Cache (NVC) innerhalb einer einzelnen physischen Gerät bestehen.

Beim Start Verankern Self

Das Gerät muss über einen Mechanismus zum Startdateien, d. h., Self anheften alle vor Windows aktiv, mit der Ebene oberste Priorität des Caches implementieren. Insbesondere wird das Laufwerk auf diese Weise von Power auf Self anheften, bis der Informationsseite Protokoll Hybrid gelesen wird. Das Laufwerk sollte nicht mehr auf die oberste Priorität Self verankern, nachdem 160 MB der Daten fixiert wurde. Alle anderen Self verankern, das Laufwerk führt, auftreten bei Priorität 0.

Cachegröße

Hybrid Cache verfügt über mindestens 5 GB nutzbare Kapazität (5 x 2-<sup>30</sup> Byte) an den Host senden.

Hinweis: Geräte Bereitstellen von weniger als 12 GB nutzbare Cache-Kapazität werden nicht für Hiberfile, Auslagerungsdatei oder andere sequenzielle e/a-caching nutzen verfügbar.

6 Prioritätsebenen (0 bis 5)

Das Gerät muss mindestens 6 Prioritätsebenen unterstützen. Keine Daten vom Host im Cache gespeichert werden entfernt werden aus Bereichen 1 bis 5 vom Gerät, es sei denn, Windows es durch Aufrufen gibt von Demotebysize oder Trim, entfernen oder Probleme e/a mit Priorität Weiter &gt; 0 in einen vollständigen Cache (d. h., Cache churning).

Priorität 0

Alle mit dem Hinweis mit Priorität 0 e/a wird verarbeitet werden, direkt vom Platte, unabhängig von der aktuellen Status (d. h., wenn die Platte angehalten wird und eine Priorität 0 e/a erhält, es sind Drehfeld oben). E/a mit dem Hinweis unter Priorität 0 wird den permanenten Cache umgehen und alle Cache Wohnsitz LBAs an, die werden mit dem Hinweis unter Priorität 0 und präsentieren jetzt auf der Platte ungültig.

Direkter Zugriff Flash

Wenn die Platte, alle Hint Write Befehle – außer Schreibvorgänge Priorität 0 heruntergefahren wird – wird direkt vom Cache unveränderliche bedient. Die Write e/a wird nicht auf die Platte zunächst bereitgestellt werden um eine Platte Hochfahren zu verhindern. Wenn das Schreiben von permanenten Cache bedient werden kann nicht, aufgrund von Systemressourcen eingeschränkt (keine clean Seiten usw.) die Platte möglicherweise Hochfahren, um die e/a-service.

Schalten Sie In dem Standbymodus

Das Gerät muss definierte SATA-Spezifikation ATA ACS-3 Power Up In Standby-Eigenschaft (PUIS) unterstützen.

Cache Seite Ersatz

Das Laufwerk ist Cacheseiten des unteren Prioritäten e/a mit höheren Prioritäten, beginnend mit der niedrigsten Priorität erfüllen wiederverwenden. Beispielsweise wenn der Cache mit 25 % mit Priorität 0 voll ist, tritt 50 % bei 2 Priorität und 25 % bei Priorität 3 und eine Priorität 3 Lese-/Schreibzugriff auf, die nicht im Cache ist, eine Priorität 0 Cacheseite zugewiesen werden sollten, um die Priorität aufzunehmen 3 LBA, das gelesen wurde. Nachdem alle Priorität 0 Cacheseiten zugewiesen sind, werden jeweils Priorität 1 und 2 Seiten zugewiesen werden. Wenn keine niedrigere Priorität, die Seiten werden von Seiten zur Verfügung, Priorität 3 Ändern eines Befehls sollten zuerst, die durch eine LRU-ähnliche Algorithmus gewählt werden.

Aktualisieren der Priorität für e/a (Lesen/Schreiben)

Prioritäten zugeordnet LBAs im Cache aktualisiert werden müssen, auf alle nachfolgenden lesen oder Schreiben in dieser LBA aus eine beliebige gültige Priorität auf eine beliebige gültige Priorität. Darüber hinaus wenn Lese- oder Schreibzugriff auf einen Bereich LBA, die derzeit NICHT im Cache befindet ausgegeben wird, klicken Sie dann es so angeordnet werden im Cache mit der angegebenen Priorität (bereitgestellt Platz im Cache vorhanden ist oder es werden blockiert – bei einer vollen Cache niedrigere Priorität, die entfernt werden kann).

Glätten

Das Gerät muss trim gemäß Definition in der Windows 8-Zertifizierung Hardwareanforderungen unter Device.Storage.Hd.Trim.BasicFunction unterstützen.

Unveränderliche Cacheleistung:

Zufällige lesen: &gt;= 8 MB/s @ 4 KB (Tiefe in die Warteschlange = 1)

Latenz:

Festlegen dirty hohe und dirty niedrige Grenzwerte sind innerhalb 50 ms abgeschlossen.

Dieser Befehl kann asynchron ausgeführt werden.

E/a, das Prioritätsinformationen ausführt, darf nicht wesentlich langsamer als e/a, ohne Prioritätsinformationen sein. Lese- oder Schreibvorgang mit der Priorität zugewiesen muss, entstehen keiner Wartezeit beeinträchtigt, die größer als die größer 10 % der identisch e/a ohne Prioritätsinformationen oder 0,5 ms (Max (10 %, 0,5 ms)). 95 % aller e/as hierfür ist mit der beeinträchtigt nie mehr als 100 % der ein ohne Priorität e/a zulässig.

HybridDemoteBySize muss innerhalb von 500 ms zurückgeben auf 3/255<sup>ten</sup> der Cachegröße aufgerufen.

HybridChangePriorityByLBARange muss innerhalb von 150 ms beim Aufruf für einen Bereich 32 MB der Daten zurückgeben.

Eine mögliche asynchrone Implementierung dieser Befehle ist zulässig.

Befehl/Protokollanforderungen

Die folgenden Funktionen und Anforderungen müssen vom Gerät unterstützt werden, und verweisen SATA-Revision 3.2 vom SATAIO bearbeitet wurden:

13.7.5.4.11 MaxPriority Verhalten

Das Verhalten der MaxPriority Bit muss auf 0 festgelegt werden.

13.3.15 Aktivieren/Deaktivieren der Hybrid Informationen

13.6.5.4.13 Hybrid-Steuerelement

Aktivieren/Deaktivieren der Zwischenspeichern Mittel

Windows benötigen die Möglichkeit zum Aktivieren und deaktivieren Sie den Cache Hybrid. Beim Deaktivieren des Caches Hybrid, verfügt über alle dirty Daten im Cache mit der endgültigen Speichermedium synchronisiert werden.

Dirty niedrige Schwellenwert

Dirty hohe Schwellenwert

Dirty-Daten synchronisiert werden soll, in aufsteigender Reihenfolge der Priorität, d. h., Priorität 0 dirty-Daten synchronisiert werden soll, bevor die Priorität 1 dirty-Daten synchronisiert werden. Wenn die Menge der dirty-Daten auf dem Gerät überschreitet die dirty hohe Schwellenwert Marke, muss das Gerät die Synchronisierung von dirty Daten beginnen. Es wird davon ausgegangen, dass dies erfordert, dass die Platte an Hochfahren.

13.6.5.4.7 Hybrid nach Größe tiefer stufen

Hybride Informationen Feature bezogene Protokolle

Das Gerät muss aktivieren Windows zum Lesen der Hybrid-Log-Seiten und sinnvollen Informationen zurück. Anders ausgedrückt, allgemeine Zweck Protokollierung ist erforderlich, und die Versionsnummer wird auf 0001h festgesetzt. Insbesondere:

13.7.9 Wort 0 x 12 "Allgemeine Zweck Protokollverzeichnis" festgesetzt auf "1", was bedeutet, dass "NCQ NON-DATA-Protokoll unterstützt wird.

13.7.10 Word 0 x 13 der "Allgemeine Zweck Protokollverzeichnis" festgesetzt auf "1" zurück, der angibt, dass das Protokoll "NCQ SENDEN UND EMPFANGEN" unterstützt wird.

13.7.12 Word 0 x 14 des "Allgemeine Zweck Log Directory" festgesetzt auf "1" zurück, der angibt, dass das Protokoll "NCQ HYBRID INFORMATIONEN" unterstützt wird. Windows muss Folgendes bestimmen können:

Mittlere Integritätsstatus Zwischenspeichern

Dirty niedrige Schwellenwert

Dirty hohe Schwellenwert

Maximale Hybrid Prioritätsstufe

Max Priorität Verhalten

NVM-Größe

Max Entfernung Befehle.

Max Entfernung Datenblöcke

Für jede Ebene Priorität:

verbrauchten NVM Größe Bruch

verbrauchten Zuordnen von Ressourcen Bruch

verbrauchten NVM Größe für Dirty Daten Bruch

belegten Zuordnen von Ressourcen für dirty Daten Bruchteil

13.6.5.4.1 Hybrid entfernen

Mit dem Befehl Entfernen angegebene Bereich sortiert LBA wird auf das primäre Medium wie ein regulären Schreibvorgang abgestimmt werden. Der Host wird – bei Bedarf – Konsistenz durch einen weiteren flush Befehl ausgeben. Entfernten LBA Bereiche sollte so, dass die Daten nur auf die Platte nach Abschluss des Befehls entfernen befindet sich in der NVC ungültig.

13.6.5.4.10 Hybrid Änderung durch LBA Bereich

Hybride Ändern von LBA Bereich muss vom Gerät, einschließlich der Cacheverhaltensweisen-Bit-Version des Befehls unterstützt werden.

<a name="device.storage.hd.scsi"></a>
## <a name="devicestoragehdscsi"></a>Device.Storage.Hd.Scsi

### <a name="devicestoragehdscsiconnectors"></a>Device.Storage.Hd.Scsi.Connectors

*SCSI-connectors*

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

SCSI-Connectors, wenn Sie ein externer Connector implementiert wird, müssen sie die Anforderungen in SCSI oder eine höhere Spezifikation erfüllen. SCSI-Connector muss den gleichen Verbindungstyp als jeder andere nicht-SCSI-Konnektor im System nicht verwenden. Alle externen paralleles SCSI-Connectors müssen mit einem ANSI genehmigten Symbol für den Bus gekennzeichnet werden. Für interne und externe Konfigurationen muss das SCSI-Bus Kabel shrouded und Schlüsseln Verbindern auf dem Hostadapter und Geräte verbunden werden. Dadurch wird sichergestellt, dass das Kabel ordnungsgemäß positioniert ist, damit der Benutzer Kabel nicht richtig angeschlossen ist nicht möglich. Für interne Konfigurationen muss Pin-1-Ausrichtung an einer Kante des Kabels Menüband und auch für den Schlüssel Connector für das peripherer SCSI-Gerät zugewiesen werden.

### <a name="devicestoragehdscsiparallelinterface"></a>Device.Storage.Hd.Scsi.ParallelInterface

*Paralleles SCSI-Schnittstelle*

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

Paralleles SCSI-Schnittstelle
 

-   Paralleles SCSI-Geräten und Adapter entsprechen mit SCSI parallele Schnittstelle-4 (SPI-4) oder höher.

-   Beendigung: Automatische Beendigung Netzfrequenz und SCSI-Abschlusszeichen erfüllen SPI-4 standard oder höher. Paralleles SCSI-Hostcontroller und Adapter müssen automatische Beendigung verwenden, die einem Benutzer ermöglicht, externe Geräte hinzufügen, ohne die Groß-/Kleinschreibung Server entfernen. Im SCSI Hostadapter verwendeten Abschlusszeichen muss regulierten Abschlusszeichen, die auch als aktiv bezeichnet werden, SCSI SPI-4 oder Boulay Abschlusszeichen. SCSI-Beendigung in interne Kabel integriert muss auch die SPI-4-Spezifikation erfüllen.

-   Terminator Power muss mit dem Bus SCSI mit Überspannungsschutz angegeben werden. Der Host-Adapter muss Terminator (TERMPWR) für den SCSI-Bus für Hauptplatine Implementierungen Stromversorgung PCI oder einer anderen Erweiterungsbus mit. In den Zeilen TERMPWR der SCSI-Bus müssen alle Abschlusszeichen externen SCSI-Bus versorgt werden. Darüber hinaus benötigen der Netzfrequenz, die TERMPWR liefert Überspannungsschutz integriert.

-   Externe Wechseldatenträgern, Festplatten und optische Laufwerke CD-DVD müssen automatische Kündigung oder einen Switch zugänglich integrierte Beendigung bereitstellen. Mindestens ein mechanische Mittel muss für die Festlegung der Beendigung bereitgestellt werden, und die Option muss ohne das Gerät Chassis öffnen auf die Benutzer zugreifen kann.

-   Anhang D SPI-4, welche Adressen SCSI-Gerät einfügen und Entfernen mit und ohne Aktivität Befehl müssen alle SCSI-Geräte unterstützen hot anschließen entsprechen.

-   Differenzielle Geräte müssen DIFFSENS unterstützen, gemäß Definition in Norm SPI-4 oder höher.

<a name="device.storage.hd.scsi.reliabilitycounters"></a>
## <a name="devicestoragehdscsireliabilitycounters"></a>Device.Storage.Hd.Scsi.ReliabilityCounters

*Grundlegende Zuverlässigkeit Leistungsindikator Funktionalität für Datenträgern, die von den SCSI-Befehl implementiert wird.*

### <a name="devicestoragehdscsireliabilitycountersbasicfunction"></a>Device.Storage.Hd.Scsi.ReliabilityCounters.BasicFunction

*Grundlegende Zuverlässigkeit Leistungsindikator Funktionalität für Datenträgern, die von den SCSI-Befehl implementiert wird.*

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

Alle SCSI-Laufwerke erforderlich gültige Daten für das unten Sinne Seite (LOG SINNE 4Dh) Parameter gemäß den Anweisungen in der primären Befehle 4 SCSI (SPC-4) und SCSI-Block Befehle 3 (SBC-3) Spezifikationen.

-   Start-Stop Cycle Leistungsindikator (0Eh)

<!-- -->

-   Herstellung Datum (0001h)

<!-- -->

-   Lesen Error-Zähler (03h)

    <!-- -->

    -   Insgesamt (0002h)

    -   Gesamtanzahl der Fehler behoben (h 0003 usw.)

    -   Insgesamt nicht korrigierte Fehler (0006h)

    <!-- -->

-   Temperatur (0Dh)

    <!-- -->

    -   Temperatur (0000h)

    -   Verweis Temperatur (0001h)

    <!-- -->

-   Error-Zähler (02h) schreiben

    <!-- -->

    -   Insgesamt (0002h)

    -   Gesamtanzahl der Fehler behoben (h 0003 usw.)

    -   Insgesamt nicht korrigierte Fehler (0006h)

    <!-- -->

-   Hintergrund-Scan (15h)

    <!-- -->

    -   Hintergrund-Scan-Status (0000h)

Laufwerke, die physisch Aufzeichnung Media und/oder Lese-/ Geräten, wie Festplatten, verschieben erforderlich gültige Daten für die unter Sinne Seite (LOG SINNE 4Dh) Parameter gemäß den Anweisungen in der primären Befehle 4 SCSI (SPC-4)-Spezifikation.

-   Start-Stop Cycle Leistungsindikator (0Eh)

    <!-- -->

    -   Inventur Over Gerät Lebensdauer (h 0003 usw.)

    -   Kumulierte Start beenden Zyklen (0004h)

    -   Angegebene Laden-Entladen Count Over Gerät Lebensdauer (0005h)

    -   Kumulierte Laden-Entladen Zyklen (0006h)

Solid-State-Laufwerke erforderlich gültige Daten für die unter Protokoll Sinne Seite (LOG SINNE 4Dh) Parameter gemäß den Anweisungen in der Spezifikation SCSI-Block Befehle 3 (SBC-3).

-   Solid-State-Medien (11h)

    <!-- -->

    -   Prozentsatz verwendet Endurance Indicator (0001h)

<a name="device.storage.hd.scsiprotocol"></a>
## <a name="devicestoragehdscsiprotocol"></a>Device.Storage.Hd.ScsiProtocol

### <a name="devicestoragehdscsiprotocolreferencespec"></a>Device.Storage.Hd.ScsiProtocol.ReferenceSpec

*Verweis auf Spezifikationen*

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

Als Min nicht anders angegeben, ist die Baseline-Spezifikation erforderlich. MAK gibt die bevorzugte Version der Spezifikation. Wenn nicht anders angegeben, wird die angegebene Version die Mindestanforderung. Sofern nichts anderes angegeben ist, müssen der genannten Spezifikationen, die von der Stelle Standards als obligatorisch klassifiziert werden alle Features implementiert werden.

SPI-4, SAM-3, Min:SPC-2, MAK: SPC-3, Min: SBC, MAK: SBC-2
 

### <a name="devicestoragehdscsiprotocolsamcompliance"></a>Device.Storage.Hd.ScsiProtocol.SamCompliance

*SCSI-Architektur Modell SAM-3*

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

SCSI-Architektur Modell SAM-3

SCSI-Geräte müssen entsprechen, SCSI-Architektur Model SAM-3 oder höher (mit Ausnahme der entsprechend den Angaben in SBP-2 für 1394-Geräte), einschließlich der folgenden Anforderungen:

-   Alle Geräte müssen LUN zurücksetzen unterstützen. Insbesondere wenn zwei LUNs L0 und L1 unter desselben Ziels Ausstehende Befehle verfügen, muss eine LUN auf L0 zurücksetzen ausstehender Befehle an, die L0 nur deaktivieren.

-   Nach dem zurücksetzen müssen auf allen Geräten ein entsprechendes zurückgeben Einheit Aufmerksamkeit Bedingung an alle derzeit mit Zugriff auf die logical Unit Initiator.

-   Alle FC, iSCSI, SCSI und SAS-Geräte müssen mehrere Initiatoren unterstützen.

-   SELECT-Modusbefehle, ändern Sie die Parameter eine Überprüfung der Einheit verursachen müssen Bedingung für andere Initiator konsistent mit SAM-3 ausgelöst werden soll.

-   LUN 0 muss für alle Ziele implementiert werden. Mindestens LUN 0 Anfrage reagieren muss, und alle Multi-LUN Ziele müssen die Befehle MELDEN von LUNS unterstützen.

-   Wenn eine beliebige LUN hinzugefügt oder entfernt wird, um die Initiatoren zugänglich ist, das Gerät muss eine Einheit Aufmerksamkeit Bedingung (06/3F/0E) BERICHT LUNS DATEN WURDE GEÄNDERT AUTHENTIFIZIERUNGSMODUS AUSWÄHLEN melden. Befehle, die Änderung Parameter bewirken, dass eine Überprüfung der Einheit müssen Bedingung für eine beliebige andere Initiator ausgelöst werden soll, die von der Änderung auswirkt.

-   Unbekannte SCSI-Befehle oder falsch formatiert Befehl Descriptor Block (CDB) muss eine sofortige BEDINGUNG ÜBERPRÜFEN wieder an der Initiator gemeldet führen.

### <a name="devicestoragehdscsiprotocolspccompliance"></a>Device.Storage.Hd.ScsiProtocol.SpcCompliance

*Primäre SCSI-Befehle (SPC-3, SPC-4 und SBC-3)*

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

SCSI primären Befehle-3 (SPC-3), SCSI primären Befehle-4 (SPC-4) und SCSI-Befehle-3 (SBC-3) blockieren

Primäre SCSI-Befehle Geräte entsprechen: unterstützen Befehle aufgeführt, die als obligatorisch in die primäre SCSI-Befehle (SPC-3 oder höher). Darüber hinaus muss jede Art von Gerät die obligatorische Befehlssatz für dieses Typs (SBC-3 für Geräte Sperren usw.) implementieren.

**Für SCSI-ABFRAGE und MELDEN von LUNS Befehle**:

Auf allen Geräten müssen der SCSI-ABFRAGE-Befehl unterstützt.

Multi-LUN-Geräten müssen immer reagieren Sie auf einem Abfragebefehl an LUN 0 gesendet werden, selbst wenn LUN 0 nicht implementiert ist. Dies kann durch das Gerät Typbezeichner 3 zurückgeben angegeben werden.

-   Alle Multi-LUN-Geräte müssen den Befehl BERICHT LUNS unterstützen, gemäß Definition in SPC-2 oder höher.

-   Windows unterstützt einstufigen nur logische Gerätenummern bis zu 255; Siehe SAM-3. Verwendung von einem anderen Format wird nicht richtig interpretiert werden, und das Gerät möglicherweise nicht zur Verfügung oder wird Datenverluste auftreten.

Alle standard-ABFRAGE-Daten müssen ordnungsgemäß für die Gerätefunktionen festgelegt werden.

-   Versionsfeld muss 04 oder größer sein. Für SAS muss dieses Feld 05 oder höher sein.

-   Min mit angefügte Medienwechsler müssen das Bit MChgnr in den standard-Abfragedaten festgelegt.

-   Multi-LUN Einheiten müssen gültige BERICHT LUNS Daten für LUN 0 zurück.

-   Wenn LUN 0 nicht zugänglich PERIPHERER GERÄT vom TYP ist, wird der PERIPHERER QUALIFIZIERER als 1 zurückgegeben werden soll. SCSIport wird nicht das gesamte Zielgerät aufgelistet werden, wenn Qualifizierer 3 verwendet wird. Es wird dringend empfohlen, LUN 0 nicht Typ 0 sein, da es für alle Initiatoren verfügbar gemacht werden muss. Geben Sie 0 ist nur zulässig, wenn das Array LUN 0 für jeden Initiator andere logische Einheiten zuordnen kann.

-   Wenn ein Gerät mehr als einen Port hat, ür Bit festgelegt werden muss und Seite 83h Deskriptoren ordnungsgemäß müssen in der Portinformationen wider.

Wichtige Produkt-Daten (VPD) Seiten:

-   Seite 00h (Seiten VPD Seite unterstützt) ist erforderlich.

-   Page B1h (Block Gerät Merkmale VPD Seite) ist erforderlich.

-   Die Seite 80h (Organizational Unit Seriennummer VPD Seite) ist erforderlich.

    Seite 83h (Gerät Identification VPD Seite) ist erforderlich. Für VPD Seite 83, mindestens einen Typ-3 oder eine, die den Typ 2-Deskriptor für jedes Gerät zurückgegeben werden muss der Wert muss Code 1 festgelegt (binär) verwenden, der Wert muss für diese logische Einheit eindeutig sein und muss den gleichen Wert unabhängig von den Pfad oder Port auf die Anforderung reagiert. Entsprechende Deskriptoren für Multiportgeräte sind erforderlich, zusätzlich zu den obligatorisch Deskriptor. Geräte, die Aliase unterstützen müssen auch die entsprechenden Deskriptor Typen unterstützt werden. Herstellerspezifische Gerätebezeichner, müssen falls vorhanden, Typ 0 müssen verwendet werden und angegebenen Formats, einschließlich der richtigen Seitenlänge.

-   Herstellerspezifische Bezeichner sind kein Ersatz für die obligatorische Typdeskriptoren 2/3. Formatierungsregeln dargelegten in SPC-3 oder höher, selbst wenn das Gerät nur Übereinstimmung mit einer Vorversion Ansprüche müssen alle Gerätebezeichner entsprechen.

-   Gerät muss SPC-3 Abschnitt 7.6.3 Gerät Identification VPD Seite 83 h entsprechen.

Mindestens eine Kennung Descriptor muss Feld ID-TYP auf festgelegt sein:

-   2h (EUI-64-basierten) gemäß Definition im 7.6.3.5

-   3h (NAA); oder wie in 7.6.3.6 definiert

-   8h (SCSI-Zeichenfolge) am definierten in 7.6.3.11

**SCSI-Modus Sinne Befehl und Seiten**

MODUS SINNE (6) ist erforderlich für alle Geräte außer RBC Geräte, die welche MODUS SINNE (10) implementieren. Das Bit DBD muss unterstützt werden.

-   Die Seite 3Fh Modus (alle Seiten Modusseite zurückgeben) obligatorisch ist.

-   Gerät spezifischen Seiten, die in den Abschnitten gerätespezifischen dieses Dokuments aufgelistet.

-   Weitere Befehle für alle Geräte sind wie folgt aus:

-   Auf allen Geräten müssen der Befehle TEST UNIT READY und ANFORDERN SINNE unterstützen.

**Speichergeräten (Datenträger und RAID) blockieren**

Blockieren (Datenträger und RAID) Speichergeräten müssen die folgenden Anforderungen erfüllen:

-   SCSI-Blockbefehle (SBC) oder höher (RBC für 1394). Diese Anforderungen gelten für alle Geräte als Gerätetyp 0, einschließlich der logische Einheiten, die von einer RAID-Controller oder Subsystem verfügbar gemacht werden.

-   Geräte sperren muss den Befehl SCSI START BEENDEN UNIT Reduzieren des Stromverbrauchs unterstützen.

-   LESEN Sie KAPAZITÄT (10) Befehl. Verfügt ein Gerät mehr als 2 ^ 32-1-Bereiche Wert 0xFFFFFFFF muss zurückgegeben werden für das Feld LOGISCHE BLOCKIEREN ADRESSE ZURÜCKGEGEBEN und muss der Befehl LESEN KAPAZITÄT (16) unterstützt werden (siehe unten).

-   Jede Änderung an der Kapazität muss eine Einheit Aufmerksamkeit Bedingung der KAPAZITÄT, die DATEN GEÄNDERT WURDE für alle Initiatoren Zugriff der logical Unit fest.

-   READ(10).

-   WRITE(10). Unterstützung für Force Einheit Zugriff (FUA) ist erforderlich für einzelne physische Laufwerke oder RAID-Controller, die veränderliche Cache-Speicher (nicht-batteriegepufferten) enthalten und müssen dazu führen, dass die gesendeten Daten mit diesen Befehl, um physische Medien übernommen werden, bevor der Befehl ausgeführt wurde.

-   Erneutes ZUWEISEN BLÖCKE (nur Festplatten). RAID-Controller, die fehlerhaften Block Replacement behandelt sollte dieser Befehl erfolgreich ausgeführt werden.

-   VERGEWISSERN SIE SICH (10).

-   STARTEN SIE STOP EINHEIT. Mit diesem Befehl muss keine anderen Aktion wie etwa Pfad-Failover ausführen.

-   SYNCHRONIZE CACHE (10) (keine optionale Felder werden verwendet). Für einen physikalischen Laufwerk bewirkt, dass dieser Befehl alle Daten im Schreibcache an Speichermedien übermittelt werden, wenn der Schreibcache aktiviert ist. Dies führen kann Datenverlusten führen.

Seiten:

-   Modus Seite 08 h (Zwischenspeichern Modusseite) mit der folgenden Bits muss gültige Informationen enthalten: WCE (Cache Schreiben aktiviert werden), CACHE SEGMENTGRÖßE und ANZAHL DER CACHE SEGMENTE (optional). RBC Geräte unterstützen Seite 6 anstelle von Seite 8 (WCD, WRITED, FORMATD und LOCKD Bits).

    -   Wenn ein Gerät deaktivieren Schreibcache durch Verwendung der WCE Bit unterstützt, dieses Bit muss auch als veränderbare gemeldet und durch einen Vorgang AUTHENTIFIZIERUNGSMODUS AUSWÄHLEN aus der ändert unterstützt werden. Der Status der den Schreibcache muss Beitrag Modus Seite 8 sichtbar sein. Lieferanten können außerhalb der eingeschränkten SBC Unterhaltungen Zwischenspeichern Richtlinien implementieren, und Deaktivieren des Schreibcaches muss sich in diesem Modusseite werden nicht.

-   Die Seite 0Ah Modus (Seite im Steuerelement Modus) erforderlich ist.

-   Die Seite 1Ah Modus (Power Bedingung Modusseite) ist erforderlich

Datenträgergeräte, die größer als 2 TB logische Einheiten (einschließlich 1394-Datenträger) unterstützen. Geräte müssen SPC-3 entsprechen und müssen die folgenden gemäß der Spezifikation SCSI-Block Befehle-2 (SBC-2) implementieren:

-   LESEN SIE DIE KAPAZITÄT (16)

-   LESEN (16)

-   WRITE (16) FUA (Bit muss unterstützt werden, wenn ein flüchtiger Cache auf dem Gerät vorhanden ist)

-   VERGEWISSERN SIE SICH (16)

-   ERNEUTES WEISEN SIE BLOCKIERT ZU. LONGLBA Feld muss unterstützt werden.

**Löschbare SCSI-Datenträger-Geräte**

Löschbare SCSI-Datenträger-Geräte müssen auch die folgenden Befehle oder Features unterstützen:

-   ERASE: Vollständig clientseitigen und ausgewählt-Block löschen.

-   Formatieren von Anforderungen, die mit dem Befehl FORMAT gemeldet.

-   MODUS SINNE (6) Austauschkomponenten Blöcke zur Verfügung, Schreibschutz Status.

-   Verhindern, DASS ZULASSEN MITTEL zum ENTFERNEN und BEENDEN EINHEIT STARTEN.

-   Erneutes ZUWEISEN BLÖCKE und LESEN DEFEKTDATEN (10).

    SCHREIBEN, ohne vor dem Löschen für löschbare optische nur.

<a name="device.storage.hd.smr"></a>
## <a name="devicestoragehdsmr"></a>Device.Storage.Hd.SMR

*Definiert die Branche und der Microsoft-Standards für Laufwerke müssen, die sich selbst als SMR identifizieren und Host-fähigen oder Host verwaltete erfüllt sein (auch als Restricted bezeichnet). Laufwerk verwalteten SMR (auch als Autonomous bezeichnet) müssen keine zusätzliche Anforderungen von Microsoft.*

### <a name="devicestoragehdsmrbasicfunction"></a>Device.Storage.Hd.SMR.BasicFunction

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>
 
**Beschreibung**

*SMR Host-fähigen/Host-verwalteten Gerät Grundfunktionen, ZAC (ATA) und ZBC (SCSI/SAS) Geräte zutreffend.*

**SMR Gerät Grundfunktionen**

-   Schreiben Sie, dass Zeiger Zonen Länge 256 MB sein.

-   Herkömmliche Zonen werden empfohlen (aber nicht erforderlich) Länge 256 MB sein.

-   Beginnend mit LBA 0 (der erste adressierbaren logischen Sektor), werden zusammenhängende konventionelle Zonen, die durch mindestens 0,1 % der adressierbaren LBA Speicherplatz insgesamt. *(Beispielsweise ein Gerät 10 TB mindestens 10 GB konventionellen Speicherplatz, Aufrunden auf das nächste Vielfache von 256 MB empfohlen übermitteln)*

-   SMR Gerät möglicherweise zusätzliche konventionelle Zonen, über das Laufwerk LBA Speicherplatz, einschließlich des letzten Zonen ermöglichen.

-   SMR Host-fähigen Gerät muss mindestens 128 open sequenzielle Schreibvorgänge bevorzugte Zonen unterstützen.

-   SMR Host-verwalteten Gerät muss mindestens 128 open sequenzielle Schreibvorgänge erforderlich Zonen unterstützen.

### <a name="devicestoragehdsmrata"></a>Device.Storage.Hd.SMR.ATA

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>
 

**Beschreibung**

**SMR Host-fähigen/Host verwaltete Geräte unterstützen die folgenden Branchenstandards:**

-   T13 Zonen Gerät ATA-Befehl festgelegt (ZAC), Version 04i oder höher

-   T13 ATA-Befehlssatz – 4 (ACS-4), Version 10 oder höher (für Teile des Geräts der Zonen ist)

-   Gerät muss alle ACS-4-Features unterstützen, wie in ZAC r04i für SMR Gerätetyp als obligatorisch definiert und ACS-4-Features, die definiert, wie in ZAC r04i für SMR Gerätetyp verboten wird nicht unterstützt.

-   Gerät ist NCQ-Featuregruppe unterstützen, gemäß Definition im r10 ACS-4.

-   SMR Host-fähigen Geräte berichtet die optimale Anzahl der bevorzugte sequenzielle Schreibzugriff geöffnet Zonen, gemäß Definition im ZAC r04i 6.2.2 Geräteinformationen Zonen Seite.

-   Host-verwalteten Gerät SMR berichtet die maximale Anzahl der Zonen bevorzugte sequenzielle Schreibzugriff geöffnet, gemäß Definition im ZAC r04i 6.2.2 Geräteinformationen Zonen-Seite. 

 

### <a name="devicestoragehdsmrscsi"></a>Device.Storage.Hd.SMR.SCSI

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>
 

**Beschreibung**

**SMR Host-fähigen/Host verwaltete Geräte unterstützen Industriestandards, insbesondere:**

-   T10 Zonen blockieren Befehle (ZBC), Version 4 oder höher

-   T10 SCSI-Block Befehlen-4 (SBC-4), Version 9 oder höher (für Teile des Geräts der Zonen ist)

-   Gerät sind alle SBC-4-Features unterstützen, wie in ZBC r4 für SMR Gerätetyp als obligatorisch definiert und SBC-4-Features, die definiert, wie in ZBC r4 für SMR Gerätetyp verboten wird nicht unterstützt.

-   SMR Host-fähigen Geräte berichtet die optimale Anzahl der bevorzugte sequenzielle Schreibzugriff geöffnet Zonen, gemäß Definition im ZBC r4 6.4.2 Zonen blockieren Gerät Merkmale VPD Seite.

-   Host-verwalteten Gerät SMR berichtet die maximale Anzahl von open sequenzielle Schreibvorgänge bevorzugte Zonen, gemäß Definition im ZBC r4 6.4.2 Zonen blockieren Gerät Merkmale VPD Seite.

<a name="device.storage.hd.thinprovisioning"></a>
## <a name="devicestoragehdthinprovisioning"></a>Device.Storage.Hd.ThinProvisioning

### <a name="devicestoragehdthinprovisioningbasicfunction"></a>Device.Storage.Hd.ThinProvisioning.BasicFunction

*Thin-Bereitstellung*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

**Standard – Spezifikation branchenanforderungen:**

-   Beruht, unterstützen, thin provisioning Feature nach T10 SPC4 und SBC3 Spezifikation implementieren muss:

-   Unterstützte VPD VPD Seite (Seite Code 00h)

-   Block Grenzwert VPD Seite (B0h Seite Code)

-   Logische Provisioning VPD Seite (Seite Code B2h) blockieren

-   Logische Provisioning Seite-Protokoll (Seite Code 0Ch) blockieren

**Windows-Design-Spec Anforderungen:**
 

-   Zielgeräte mit thin provisioning Feature müssen die folgenden Anforderungen erfüllen.

    <!-- -->

    -   Abfragebefehl muss für unterstützt VPD VPD Seite mit B0h und B2h zurückgegeben werden.

    -   Bit ist festgelegt LBPU muss zurückgeben eins und Provisioning Feld = 3 (010 b) der logischen Block Provisioning VPD Seite (Seite Code B2). 

    -   Block Grenzwert VPD Seite (Seite Code B0h) implementieren und unterstützt die folgenden Parameter muss.

        <!-- -->

        -   MAXIMALE ANZAHL LBA AUFHEBEN
        -   MAXIMUM BLOCK DESKRIPTOR COUNT AUFHEBEN
        -   OPTIMALE GRANULARITÄT AUFHEBEN
        -   AUFHEBEN DER ZUORDNUNG VON GRANULARITÄT AUSRICHTUNG
        -   UGAVALID-Bit

        <!-- -->

    -   Logische Block Provisioning VPD Seite (Seite Code B2h) implementieren und unterstützt die folgenden Parameter muss.

        <!-- -->

        -   Schwellenwert für Exponent
        -   LBPU-bit
        -   LBPRZ bit
        -   Feld-Bereitstellung

        <!-- -->

    -   Thin Provisioning Geräte sollten für das Hinzufügen der folgenden Informationen in das Systemereignisprotokoll Schwellenwert für die Benachrichtigung Sinne-Befehl abzurufenden logische Block Provisioning Seite-Protokoll (Seite Code 0Ch) - Protokoll unterstützen.

        <!-- -->

        -   Zuordnung von Ressourcen einer dünnen Provisioning LUN LBA verwendet.
        -   Verfügbare LBA Zuordnung von Ressourcen zur Thin Provisioning LUN.

        <!-- -->

    -   Speicher-Array muss Befehl AUFHEBEN (10) unterstützen, setzt das bit in LBP VPD Seite LBPU auf eine.

    -   Muss erste LBA Status (16) Befehl nach T10 SBC3-Spezifikation unterstützen.

    <!-- -->

-   Wenn das LBPME Bit in ReadCapacity(16) zurück auf eine festgelegt ist oder B2h unterstützt VPD Seite VPD Seite gemeldet wird, muss Speicherarray logische Block Provisioning VPD Seite (Seite Code B2h) unterstützen.

-   Wenn das LBPRZ Bit in ReadCapacity(16) zurück auf 1 festgelegt ist, muss Speicherarray LBPRZ Bit der logischen Block Provisioning VPD Seite auf einen festgelegt.

-   Speicher-Array muss Schwellenwert-Benachrichtigung (TN), temporäre Ressource Erschöpfung (TRE) und permanente Ressource Erschöpfung (älter als Version) über die folgenden Sinne Schlüssel, zusätzliche und zusätzliche Sinne Code Qualifizierer gibt als SPC4 und SBC3 Spezifikationsdialogfeld unterstützen.

    <!-- -->

    -   Sinne TN - Schlüssel/ASC/ASCQ (38/06/07)
    -   TRE - Sinne Schlüssel/ASC/ASCQ (02/04/14)
    -   Vor dem Sinne Schlüssel/ASC/ASCQ (07/27/07)

**Anforderungen an die Benutzer wünschen:**

-   Müssen möglicherweise über Anbieter Storage Management Dienstprogramm Schwellenwert und überwachen Systemereignisprotokoll bei der thin provisioning soft Schwellenwert erreicht wird.

-   Protokoll Sinne Befehl aus, um die Seite LBP-Protokoll für reporting verfügbar LBA Ressource zuordnen und LBA die thin provisioning LUN Ressourceninformationen zuordnen verwendet, wenn auf der Seite Protokoll (Seite Code OCh) implementiert wird abgerufen muss unterstützt werden.

<a name="device.storage.hd.trim"></a>
## <a name="devicestoragehdtrim"></a>Device.Storage.Hd.Trim

### <a name="devicestoragehdtrimbasicfunction"></a>Device.Storage.Hd.Trim.BasicFunction

*ATA-GERÄTS Zuschneiden und Aufheben der Zuordnung von SCSI-Funktionalität*

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

Wenn das Gerät ATA-GERÄTS nicht - NCQ Zuschneiden oder Aufheben der Zuordnung von SCSI-Unterstützung implementiert:

-   Die Trim-Implementierung muss ATA-ACS2 Abschnitt 7.10 (Befehl im DataSet Management) entsprechen.

-   Die Implementierung der Zuordnung SCSI-Befehl entsprechen T10 SBC3 Abschnitt 5,28 (AUFHEBEN-Befehl).

-   Wenn das Gerät eine Seek beeinträchtigt, der angibt, einen Media-Berichte:

    -   Alle e/a- und Trim/aufheben Befehle sind in weniger als 1000 ms auszufüllen.

    -   98,5 % der e/a-Befehle sind in weniger als 200 ms auszufüllen.

-   Andernfalls (SSD):

    -   Alle e/a- und Trim/aufheben Befehle sind in weniger als 500 ms auszufüllen.

    -   98,5 % der e/a-Befehle sind in weniger als 100 ms auszufüllen.

Wenn das RZAT Bit ist auf einem Gerät SATA oder das LBPRZ Bit auf einem SCSI-Gerät festgelegt ist, muss das Gerät auf einen Befehl Lesen vor der zugeschnittenen Speicherblöcke Orchestrierung neu geschrieben alle ' 0 zurück.

<a name="device.storage.hd.uas"></a>
## <a name="devicestoragehduas"></a>Device.Storage.Hd.Uas

### <a name="devicestoragehduascompliance"></a>Device.Storage.Hd.Uas.Compliance

*USB UAS Speichergeräten*

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

USB UASP Speichergeräten müssen auch mit der v1. 0 USB UASP und SPC4, SBC3 kompatibel sein.
USB-UASP Speichergeräten müssen Folgendes unterstützen:

-   Modus Seitencode: 0 x 08 Modus Unterseite Code: 00

-   Block Grenzwerte Seite - 0xB0 SPC3 6.5.3

-   Unterstützung von mindestens 16 Datenströme

-   Unterstützen Task Management Befehle

**           Note:** Weitere Informationen zu Seiten, finden Sie unter SPC4: D.6 Modus Seite Codes.

-   Unterstützung der SPC, SBC Version Deskriptoren

-   Support-/ Bericht R02. R04 Version Deskriptoren

-   Gerät muss FIXED gemeldet, wenn es sich nicht um ein Wechselmedium true ist (RMB = 0)

**Hinweis:** Weitere Informationen zu Seiten, finden Sie unter SPC4: D.6 Modus Seite Codes.
Geräte müssen ausführen wie angegeben:

-   Minimale sequenzielle Schreibvorgänge Geschwindigkeit: 100 MBIT/s

-   Die minimalen sequenzielle Lesevorgänge Geschwindigkeit: 110 MB/s

Zusätzliche Anforderung: Wenn das Gerät UASP XHCI unterstützt, müssen sie UASP auf EHCI unterstützen.

<a name="device.storage.hd.uasonehci"></a>
## <a name="devicestoragehduasonehci"></a>Device.Storage.Hd.UasOnEHCI

### <a name="devicestoragehduasonehcibasicfunction"></a>Device.Storage.Hd.UasOnEHCI.BasicFunction

*USB UAS Speichergeräten*

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

Wenn das Gerät UASP über XHCI unterstützt und sie müssen UASP auf EHCI unterstützen.

<a name="device.storage.hd.usb"></a>
## <a name="devicestoragehdusb"></a>Device.Storage.Hd.Usb

### <a name="devicestoragehdusbcompatibility"></a>Device.Storage.Hd.Usb.Compatibility

*USB-Kompatibilität*

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

USB-Kompatibilität
 

-   Alle USB-Speichergeräten müssen die Anforderungen der Universal Serial Bus Masse Speicher Spezifikation Übersicht über die Klasse, v1. 2 Revision erfüllen. Dazu gehören alle USB-Massenspeicher Klasse Dokumente, einschließlich nur Massen, Control/Bulk/Interrupt, Bootability und UFI-Befehl Spezifikationen.

-   BOT1.0, SPC-2, SBC-2

-   3.0 USB-Geräten müssen behalten Abwärtskompatibilität am Typ A Connector zum lässt Superspeed Geräte verwendet werden, dies ist allerdings mit einer kleineren Geschwindigkeit, mit USB 2.0-PCs und Hochgeschwindigkeits-Geräte mit ihren vorhandenen Kabel mit den Konnektoren für den USB-3.0 Superspeed Type-A verbunden sein.

-   USB-Speichergeräten müssen USB-3.0 - Abschnitt 11 Interoperabilität und Power Übermittlung Spezifikationen entsprechen. Die folgende Tabelle enthält die Kompatibilitätsmatrix für USB-3.0 und USB 2.0. Die Auswirkung der Identifizieren eines Ports Host wie unterstützenden USB 3.0 besteht darin, dass die Unterstützung von Hardware und Software für USB 3.0 ist fertig. Andernfalls wird der Port nur als einen USB 2.0-Anschluss identifiziert werden.

<html>
    <table>
        <thead>
            <tr class="header">
                <th>USB-hostPort</th>
                <th>USB-Gerät-Funktion</th>
                <th>Verbundenen Modus</th>
            </tr>
        </thead>
        <tbody>
            <tr class="odd">
                <th rowspan="2">USB 2.0</th>
                <td>USB 2.0</td>
                <td>
USB 2.0 schnelle, schnellen, oder<br />
niedrige Geschwindigkeit                </td>
            </tr>
            <tr class="even">
                <td>USB 3.0</td>
                <td>
USB 2.0 Hochgeschwindigkeits<br />
                </td>
            </tr>
            <tr class="odd">
                <th rowspan="2">USB 3.0</th>
                <td>USB 2.0</td>
                <td>
USB 2.0 schnelle, schnellen, oder<br />
niedrige Geschwindigkeit                </td>
            </tr>
            <tr class="even">
                <td>USB 3.0</td>
                <td>
USB 3.0 SuperSpeed<br />
                </td>
            </tr>
        </tbody>
    </table>
</html>

-   USB-Speichergeräten müssen mit Zertifizierung Anforderung für USB-Geräte und USB-Speichergeräten entsprechen.

Hinweis:  
Näheres USB3.0 Spec Abschnitt 3.1.4 USB 3.0 Architektur-Übersicht

-   Geschwindigkeit der USB3.0 Super-5 Gb/s
-   USB Hochgeschwindigkeits - 2.0 480 Mb/s
-   Full-Speed - 12 Mb/s
-   Niedrige Geschwindigkeit - 1,5 Mb/s

<a name="device.storage.hd.usb3"></a>
## <a name="devicestoragehdusb3"></a>Device.Storage.Hd.Usb3

### <a name="devicestoragehdusb3compliance"></a>Device.Storage.Hd.Usb3.Compliance

*Speichergeräten USB 3.0*

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

USB 3.0 Speichergeräten müssen wie folgt aus dem Gesundheitswesen Spezifikationen Folgendes unterstützen:
 

-   Alle USB-3.0 Speichergeräten müssen mit der USB-3.0 Version 1.0-Spezifikation kompatibel sein.

-   Geben Sie eindeutigen Product ID über jeden Speicher-Endpunkt (ROBOT, UASP)

    <!-- -->

    -   USB-ANBIETER-/PRODUKT-ID

Geräte müssen ausgeführt werden wie angegeben:

-   Minimale sequenzielle Schreibvorgänge Geschwindigkeit: 60MB/s

-   Die minimalen sequenzielle Lesevorgänge Geschwindigkeit: 90MB/s

<a name="device.storage.hd.windowstogocapableusbdrive"></a>
## <a name="devicestoragehdwindowstogocapableusbdrive"></a>Device.Storage.Hd.WindowsToGoCapableUSBDrive

*Windows wechseln Sie zur Lage USB-Laufwerk feature*

### <a name="devicestoragehdwindowstogocapableusbdrivewindowstogocapableusbdrive"></a>Device.Storage.Hd.WindowsToGoCapableUSBDrive.WindowsToGoCapableUSBDrive

*Windows wechseln Sie zur Lage USB-Laufwerk*

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

USB-Bootgeräte müssen USB 3.0 und diese Branchenspezifikationen erfüllen:

-   USB-3.0 Version 1.0-Spezifikation
-   USB-BOT-Spezifikation
-   Block SCSI-Befehle 3 (SBC-3)-Spezifikation


USB-Boot-Geräte müssen:

-   Boot Windows

    -   Arbeiten Sie mit SuperSpeed, wenn in einen 3.0 USB-Anschluss verbunden

    -   Erfolgreich eingeben und fortsetzen aus dem Standbymodus (S3) und Ruhezustand (S4)

-   Schließen Sie in der MS OS Descriptor erweiterte Eigenschaft der Wert "WindowsBootCapable" DWORD-Wert-1

-   Mindestens 32 GB Größe (20 GB verfügbar)

-   Bereitstellen von eindeutigen, konsistenten Product ID

    -   USB-ANBIETER-/PRODUKT-ID
    -   Abfrage Seriennummer
    -   Anzahl der Abfrage-Objektmodell

-   Unwichtigstes, FIXED (RMB = 0)

-   Implementieren der Block Gerät Merkmale VPD Seite

-   IEEE-1667 implementiert **nicht**

-   Verfügbarmachen von mehr als eine LUN **nicht** während des Startvorgangs

-   Das USB-Attached SCSI (UAS) Protokoll unterstützt **nicht**

-   Wenn das Laufwerk WTG des Betriebssystems für mehrere Funktionen bereitstellt:

    -   Das Gerät muss als zusammengesetzte USB-Gerät konzipiert

    -   Zusammengesetzte Geräte müssen DeviceClass, Unterklasse und Protokoll in der zusammengesetzten Knoten Gerätedeskriptoren auf 0 festgelegt.

    -   Alle Funktionen außer WTG Speicher und Smartcard muss nicht implementiert werden.

    -   Die Speicherfunktion muss die erste Funktion verfügbar gemacht werden.

-   Unterstützt die folgenden Seiten

    -   Modus Seitencode: 0 x 08 Modus Unterseite Code: 00

-   Erfüllen Sie die folgenden leistungsanforderungen:

    -   Zufällige 4 KB schreiben IOPs &gt;= 200 (Laufwerke Rotation ausgenommen)

    -   Zufällige 4 KB lesen IOPs &gt;= 2000 (Laufwerke Rotation ausgenommen)

    -   Lese-/Schreibzugriff Perf sollte in gemischten Arbeitslast random Access Lese-/Schreibzugriff linear skaliert.

    -   Sequenzieller schreiben Geschwindigkeit &gt;= 80 MB/s

    -   Lesen Geschwindigkeit sequenzieller &gt;= 80 MB/s

    -   Max-e/a-Wartezeit &lt; 500 Millisekunden

    -   Bis zu 16 Sekunden-Gesamtsumme der Benutzer wahrnehmbar Wartezeiten von e/a über einen beliebigen Zeitraum 1 Stunde ein, in dem ein Benutzer wahrnehmbar e/a definitionsgemäß ist eine Wartezeit von mindestens 100 Millisekunden besseren Benutzer Vertreter

<a name="device.storage.optical"></a>
## <a name="devicestorageoptical"></a>Device.Storage.Optical

### <a name="devicestorageopticalcdrawrecording"></a>Device.Storage.Optical.CdRawRecording

*Optische Laufwerke müssen ROH-CD Aufzeichnung unterstützen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Optische Laufwerke müssen ROH-CD Aufzeichnung Modus für CD-R und Deinstalliert und Profile unterstützen.

### <a name="devicestorageopticalcommandperformance"></a>Device.Storage.Optical.CommandPerformance

*Optische Laufwerke müssen innerhalb der zulässigen Zeitrahmen Leistung Befehl ausführen.*

</table>
<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

 
Optische Laufwerke müssen alle Befehle in die maximal zulässige Zeiten gemäß der folgenden Tabelle.

| BEFEHL                                                                              | Grundlegende Zertifizierung Anforderung (ms) | Ausnahme (Ausnahmekriterien / ms)                                    |
|--------------------------------------------------------------------------------------|----------------------------------------|-------------------------------------------------------------------------|
| GET-KONFIGURATION                                                                    | 20                                     | &nbsp; |
| BENACHRICHTIGUNG BEI STATUS ABRUFEN                                                        | 20                                     | &nbsp; |
| LEISTUNG                                                                      | 20                                     | &nbsp; |
| ABFRAGE                                                                              | 20                                     | &nbsp; |
| MECHANISMUS STATUS                                                                     | 20                                     | &nbsp; |
| MODUS AUSWÄHLEN                                                                          | 20                                     | &nbsp; |
| MODUS SINNE                                                                           | 20                                     | &nbsp; |
| VERHINDERN, DASS DAS ENTFERNEN DES MEDIUMS ZULASSEN                                                         | 20                                     | &nbsp; |
| INHALTSVERZEICHNIS PMA ATIP LESEN                                                                    | 20                                     | &nbsp; |
| LESEN BUFFER-KAPAZITÄT                                                                 | 20                                     | &nbsp; |
| KAPAZITÄT LESEN                                                                        | 20                                     | &nbsp; |
| CD<sup>1,2,4</sup> LESEN                                                              | 500                                    | &nbsp; |
| LESE-CD INFORMATIONEN                                                                | 50                                     | &nbsp; |
| LESBAREN FORMAT KAPAZITÄTEN                                                               | 20                                     | &nbsp; |
| LESEN NACHVERFOLGEN INFORMATIONEN                                                               | 20                                     | &nbsp; |
| ANFORDERN SINNE (wenn nicht nach einem Befehl mit dem Status Fehler)                | 20                                     | &nbsp; |
| SENDEN SIE OPC-INFORMATIONEN                                                                 | 60000                                  | Für Medien, d. h., DVD + R DL, DL DVD-R, BD-RE DL / 70000        |
| LEGEN SIE IM VORAUS LESEN                                                                       | 20                                     | &nbsp; |
| LEGEN SIE STREAMING                                                                        | 20                                     | &nbsp; |
| START BEENDEN UNIT (Immed = 1 b)                                                           | 20                                     | &nbsp; |
| START BEENDEN UNIT (ausschließen, Immed = 0 b)                                                    | 7000                                   | &nbsp; |
| BEENDEN Sie EINHEIT STARTEN (einlegen, Immed = 0 b, bis die Medien bereit)                             | 25000                                  | DVD-RAM / 40000<br/>Für Medien, d. h., DVD + R DL, DVD-R DL, BD-RE DL / 30000 |
| SYNCHRONISIEREN von CACHE (Immed = 1 b)                                                         | 20                                     | &nbsp; |
| SYNCHRONISIEREN von CACHE (Immed = 0 b)                                                         | 15000                                  | &nbsp; |
| TEST-GERÄT BEREIT                                                                      | 20                                     | &nbsp; |
| LEER (Immed = 1 b)                                                                     | 20                                     | &nbsp; |
| LEER (Immed = 0 b)                                                                     | n/v                                    | &nbsp; |
| SCHLIEßEN NACHVERFOLGEN SITZUNG (Immed = 1 b)                                                       | 20                                     | &nbsp; |
| SCHLIEßEN Sie VERFOLGEN SITZUNG (Immed 0 b =, logischen Spur oder der Sitzung zu schließen, führen Sie nicht abschließen von CD) | 65000                                  | DL DVD + R, DVD-R DL / 300000<br/>DVD-R SL, DVD-LESE / 180000 |
| SCHLIEßEN NACHVERFOLGEN SITZUNG (Immed = 0 b, Abschließen von CD)                                        | 65000                                  | DVD + R DL 300000<br/>DVD-R-SL, DVD-R DL DVD-LESE / 900000 |
| FORMAT UNIT (unmittelbar)                                                              | 20                                     | &nbsp; |
| LADEN UND ENTFERNEN MITTEL                                                                   | n/v                                    | &nbsp; |
| READ10<sup>1,2,4</sup>                                                               | 500                                    | DVD-RAM / 800                                                           |
| READ12 (nicht streaming)<sup>1,2,4</sup>                                               | 500                                    | DVD-RAM / 800                                                           |
| READ12 (streaming)<sup>1,2,4</sup>                                                   | 100                                    | 1 X CD / 500;             2 x CD / 350;              4 x CD / 200 |
| LESE-CD STRUKTUR<sup>6</sup>                                                      | 20                                     | &nbsp; |
| LESEN von MEDIEN SERIENNUMMER<sup>2</sup>                                                 | 500                                    | &nbsp; |
| BERICHT-TASTE                                                                           | 20                                     | &nbsp; |
| RESERVIEREN NACHVERFOLGEN                                                                        | n/v                                    | &nbsp; |
| HINWEISES BLATT SENDEN                                                                       | n/v                                    | &nbsp; |
| SENDEN SIE CD-STRUKTUR                                                                  | n/v                                    | &nbsp; |
| SCHLÜSSEL SENDEN                                                                             | 20                                     | &nbsp; |
| SET-CD-GESCHWINDIGKEIT                                                                         | 20                                     | &nbsp; |
| WRITE 10 (FUA = 0) <sup>1,3</sup>                                                      | 50                                     | &nbsp; |
| WRITE 12 (FUA = 0) <sup>1,3</sup>                                                      | 50                                     | &nbsp; |
| SCHREIBEN DES PUFFERS                                                                         | n/v                                    | &nbsp; |
| LÖSCHEN                                                                                | n/v                                    | &nbsp; |
| PUFFER ZU LESEN                                                                          | n/v                                    | &nbsp; |
| LESEN CD MSF<sup>1,2,4</sup>                                                          | 500                                    | &nbsp; |
| NACHVERFOLGEN DER REPARATUR                                                                         | n/v                                    | &nbsp; |
| SEEK10                                                                               | n/v                                    | &nbsp; |
| VERGEWISSERN SIE SICH 10                                                                            | n/v                                    | &nbsp; |
| SCHREIBEN UND ÜBERPRÜFEN 10                                                                  | n/v                                    | &nbsp; |

 
**"Fertigstellungstermin Befehl" ist definiert als die Zeit zwischen einem Befehl verlassen den Microsoft-Port / Miniporttreiber und der Befehl Abschluss zurückgegeben wird, auf den Microsoft-Port / Miniporttreiber. Wenn Sie der Befehl mit dem Status nicht erfolgreich ist, enthält diesmal außerdem den nachfolgenden anfordern Sinne Befehl verlassen den Microsoft-Port / Miniporttreiber und anfordern Sinne Befehl nach Abschluss zurückgegeben wird, auf den Microsoft-Port / Miniporttreiber.**

Alle die Befehl Ausführungszeit Leistung Messung sollte auf Medien, die Media physischen Ebene standard-Spezifikation aus zugehörigen Ausschüsse - d. h. DVD-Forum BDA, DVD + LESE Allianz entsprechen ausgeführt werden. Auch sollte unter normalen Temperatur und Feuchtigkeit betriebliche Bedingung gemäß der Deklaration in der Gerätespezifikation für ausgeführt werden.

**Hinweis:** Read-Only Laufwerke werden aus der Windows-Zertifizierung Programm für 01 Juni 2010 zurückgezogen werden. Folglich werden Zertifizierung Anforderungen und Tests nicht mehr für Read-Only Laufwerke auf 01 Juni 2010 vorhanden sein. Partner, die Windows-Zertifizierung für Systeme mit Read-Only Laufwerke erhalten möchten, würde weiterhin können. Das Laufwerk Read-Only würde jedoch in der Kategorie "nicht klassifizierte" Geräte fallen.
 
<sup>1</sup>: übertragen Länge für das Lesen und Schreiben von Leistungstests ist kleiner oder gleich in einen einzelnen ECC-Block (32 KB oder 64 KB abhängig von der aktuellen Medientyp, d. h., 64 KB für CD und BD 32 KB für DVD).

<sup>2</sup>: Leistungstests können bei jeder Geschwindigkeit gemeldet unterstützt das Gerät, einschließlich 1 x-Medien Geschwindigkeit Wenn also gemeldet unterstützt ausgeführt werden.

<sup>3</sup>: Laufwerk ***müssen*** , verwenden Sie Schreib-Puffer und ***darf nicht*** Verzögerung Befehl Abschluss durch keine Art von Medienzugriff. Wenn Write Puffer voll ist, fehl Laufwerk ***muss*** im Write-Befehl mit langen Write im Sinne Fortschrittsinformationen (02 h/h 04/08 h).
 
<sup>4</sup>: die ersten 100 e/a-Befehle nach Ankunft von Medien zu lesen oder fortsetzen aus dem Standbymodus Power Bundesland oder Cd-Geschwindigkeit festlegen oder Streaming festgelegt sind eine Verzögerung von bis zu einer Gesamtsumme von 60 000 zulässig (ms) zum Abschließen, um zusätzliche Hochfahren Zeit zu ermöglichen. Diese Befehle können einzeln können eine beliebige Dauer bis zu einem Maximum von 7 000 (ms), aber die kumulierte Zeit für die Durchführung aller hundert Befehle 60 000 nicht überschreiten dauern (ms). Nur die Zeit zwischen beim Lese-Befehl an das Gerät gesendet wird und Lese Befehl abgeschlossen ist, indem Sie wird das Gerät berücksichtigt, für die Zeit zwischen zwei aufeinanderfolgenden Befehle lesen ist (d. h., Host verzögert werden nicht gemessen) nicht unterstützt.

<sup>6</sup>: die Liste der CD Projektstrukturplan-Codes auf; beschränkt ist physische Formatinformationen (Format = 0 x 00, Adresse = 0), mittlere DVD-RAM-Status (Format = 0 x 09, Adresse = 0), DVD + LESE schreiben verhindern DCB (Format = 0 x 30-Adresse = 0x57444300), Schutzstatus schreiben (Format = "0xC0" Adresse = 0)<sup>7</sup>: Dual Layer schreiben profile *wird am 1. Juni 2010 erforderlich sein* , für Blu-Ray-Laufwerke 9,5 mm Höhe und kleiner als auch dem DVD-Laufwerke 7 mm Höhe und beträgt. Dadurch wird die vorherige Ausnahme für diese Formfaktoren beendet.

### <a name="devicestorageopticaldrivedefinition"></a>Device.Storage.Optical.DriveDefinition

*Wie optische Laufwerke für die Zertifizierung definiert sind.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Um ein optisches Laufwerk sein, muss das Gerät definiert werden als CD (CD)-Gerät, DVD (Digital vielseitig Disc oder Digital Video Disc) Gerät, BD (Blu-Ray Disc) Gerät oder jedes Gerät, das sich selbst identifiziert, wie peripherer Gerät Typ 5 pro Befehl INCITSs T10 des primären SCSI-Befehle, legen Sie SPC (beliebige Version).

### <a name="devicestorageopticalfeatures"></a>Device.Storage.Optical.Features

*Optisches Laufwerk Features erforderlich*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Optische Laufwerke müssen die unten aufgeführten erforderlichen Features unterstützen:

-   Core-Funktion
-   Profil Beispiellistenfeatures
-   Obligatorische Funktionen pro Profil
-   Austauschbare mittlere Feature aus MT. Den geltenden 7
-   Statusberichte richtigen Schacht
-   Power-Funktion
-   Umwandeln Feature
-   Laufwerk Seriennummer-Funktion
-   DVD-CSS-Funktion (0106h)

### <a name="devicestorageopticalmmcversion"></a>Device.Storage.Optical.MmcVersion

*Optische Laufwerke müssen MMC entsprechen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Optische Laufwerke müssen Befehlssatz und MultiMedia Befehl festgelegt - 6 (6 MMC), nach der Veröffentlichung INCITSs T10 des entsprechen. Da die Veröffentlichung von MMC 6 verzögert wurde, optische Laufwerke in der Zwischenzeit entsprechen muss die Kombination INCITSs T10s Befehls Set MultiMedia Befehl festgelegt - 5 (MMC-5) und SFFs MT. Den geltenden Befehle für Multimedia-Geräte, Version 7 (INF-8090i Version 7), bis die Veröffentlichung der MMC-6. Wenn MMC-5 und INF-8090i Version 7 im Widerspruch zueinander stehen, und die folgenden Anforderungen nicht explizit das erforderliche Verhalten angeben, ist die Einhaltung der MMC-5 erforderlich (mit Ausnahme der neu definierten in INF-8090i Version 7 Features).

### <a name="devicestorageopticalprofiles"></a>Device.Storage.Optical.Profiles

*Optisches Laufwerk Profile erforderlich*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Optische Laufwerke müssen die erforderlichen Profile unterstützen, wie unten aufgeführt:

-   CD-ROM-
-   DVD-ROM-
-   Wechseldatenträger
-   CD-R
-   LAUFWERK
-   DVD-R sequenzielle Aufzeichnung
-   DVD-LESE eingeschränkt überschreiben
-   DVD-R Dual Layer sequenzielle Aufzeichnung
-   DVD + LESE
-   DVD + R
-   DVD + R DL.

### <a name="devicestorageopticalrealtimestreaming"></a>Device.Storage.Optical.RealTimeStreaming

*Optische Laufwerke müssen Real Time Streaming unterstützen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Optische Laufwerke müssen nach Bedarf gemäß den Anforderungen für den Benutzerprofildienst Real Time Streaming unterstützen. Für alle beschreibbaren und wieder beschreibbaren Profile, die folgenden Felder werden festgesetzt entsprechend: Stream schreiben (SW) = 1 b und Schreiben Geschwindigkeit Leistung Deskriptor (WSPD) = 1 b.

<a name="device.storage.optical.blurayreader"></a>
## <a name="devicestorageopticalblurayreader"></a>Device.Storage.Optical.BluRayReader

### <a name="devicestorageopticalblurayreaderprofiles"></a>Device.Storage.Optical.BluRayReader.Profiles

*Erforderliche Profile für Blu-Ray Leser*

</table>
<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Blu-Ray Reader Laufwerke müssen BD-ROM-Profil unterstützen.

<a name="device.storage.optical.bluraywriter"></a>
## <a name="devicestorageopticalbluraywriter"></a>Device.Storage.Optical.BluRayWriter

### <a name="devicestorageopticalbluraywriterprofiles"></a>Device.Storage.Optical.BluRayWriter.Profiles

*Erforderliche Profile für Blu-Ray-Autoren*

</table>
<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Blu-Ray Laufwerke, schreiben kann BD-ROM-, BD-R sequenzielle Aufzeichnung und BD-RE-Profile unterstützen müssen.

<a name="device.storage.optical.sata"></a>
## <a name="devicestorageopticalsata"></a>Device.Storage.Optical.Sata

### <a name="devicestorageopticalsataasynchronousnotification"></a>Device.Storage.Optical.Sata.AsynchronousNotification

*Asynchrone Benachrichtigung ist für alle verbunden SATA-Laufwerken erforderlich.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Optische Laufwerke, die über den SATA-Bus verbinden müssen asynchrone Benachrichtigung zu unterstützen.

