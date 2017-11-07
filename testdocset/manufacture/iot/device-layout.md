---
author: kpacquer
Description: "IoT Gerät Layout"
title: "IoT Gerät Layout"
ms.openlocfilehash: abe5ce545f4a77251f464b4c52276922bfa61c74
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="iot-device-layout"></a>IoT Gerät Layout

Beim Ändern einer Pinnwand IoT Core Paket (BSP) zu unterstützen, können Sie durch Ändern der DeviceLayout Dateien die Partitionen und das Layout ändern.

## <a name="partition-layout"></a>Partitions-Layouts

IoT Core unterstützt UEFI (GPT) und legacy BIOS (MBR) Partitionslayouts. Die meisten IoT Core-Geräte verwenden UEFI und GPT-Schreibweise Partitionen, obwohl Brombeere Pi 2 Partitionen MBR-Format verwendet. Lesen Sie weitere Informationen zu UEFI [Starten und UEFI](https://msdn.microsoft.com/windows/hardware/drivers/bringup/boot-and-uefi) und [Windows und GPT-häufig gestellte Fragen zu](https://msdn.microsoft.com/en-us/library/windows/hardware/dn640535(v=vs.85).aspx).  

Beispiel Partitionslayouts in der ADK Add-Ons enthalten:
-  \iot-ADK-addonkit\Common\Packages\DeviceLayout.GPT4GB\devicelayout.Xml
-  \iot-ADK-addonkit\Common\Packages\DeviceLayout.GPT2GB\devicelayout.Xml
-  \iot-ADK-addonkit\Common\Packages\DeviceLayout.MBR4GB\devicelayout.Xml
-  \iot-ADK-addonkit\Common\Packages\DeviceLayout.MBR2GB\devicelayout.Xml

Diese Dateien verwenden Sie drei-Komponentendateien Folgendes:
-  ** DeviceLayout. <Name>. pkg.xml: Packen Datei, Pakete für DeviceLayout und OEMDevicePlatform.xml erstellt.
-  **DeviceLayout.xml**: Gibt das Gerät Partitionslayout
-  **OEMDevicePlatform.xml**: Gibt das Ausmaß der verfügbaren freien Blöcken in das Gerät, und welche Partitionen komprimiert werden.

### <a name="partition-layout-devicelayoutxml"></a>Partitionslayout (DeviceLayout.xml)

IoT Core erfordert 3 obligatorische Partitionen (EFIESP, MainOS und Daten).  Optional können Sie anderen Partitionen, beispielsweise eine Partition Speicherabbild enthalten. Größen werden in Bereichen berechnet, der Standard-Sektor 512 Bytes. 

Unterstützte Eigenschaften:

**EFI**: mit fester Größe Partition mit der Start-Manager, Boot-Konfigurationsdatenbank. Diese Partition ist für beide MBR/GPT-Style-Geräte erforderlich.

- Name:`EFIESP`
    
- Typ: Verwenden Sie für MBR `0x0C`. Verwenden Sie GPT`{c12a7328-f81f-11d2-ba4b-00a0c93ec93b}`
    
- FileSystem:`FAT`
    
- TotalSectors: `65536` (= 32MB)
    
- Startbaren:`true`
    
- RequiredToFlash:`true`
    
**MainOS**: Betriebssystem und apps OEM vorab geladen. Diese Partition erfordert eine minimale Anzahl von freien Bereiche (MinFreeSectors) für den normalen Betrieb. 

- Name:`MainOS`

- Typ: Verwenden Sie für MBR, `0x07`. Verwenden Sie GPT`{ebd0a0a2-b9e5-4433-87c0-68b6b72699c7}`
    
- FileSystem:`NTFS`
    
- MinFreeSectors: `1048576` (= 512MB)
    
- ByteAlignment:`0x800000`
    
- ClusterSize: `0x1000` (dieser Größe wird empfohlen, um die Größe der Partition verwaltbaren beizubehalten.)
    
**Daten**: Benutzer Datenpartition, Benutzer Registrierungsstrukturen, apps, apps Daten. Diese Partition ist in der Regel verwenden Sie den Rest des Speicherplatzes auf dem Gerät festgelegt. (UseAllSpace: True)
    
- Name:`Data`
    
- Typ: Verwenden Sie für MBR `0x07`. Verwenden Sie GPT`{ebd0a0a2-b9e5-4433-87c0-68b6b72699c7}`
    
- FileSystem:`NTFS`
    
- UseAllSpace:`true`
    
- ByteAlignment:`0x800000`
    
- ClusterSize: `0x4000` (diese Partition wird größer, sodass 0 x 4000 empfohlen wird. 0 x 1000 ist auch OK.)

**Absturz Dump Partition**: Optional Partition, zum Sammeln von Daten aus Absturz speichert. Wenn verwendet wird, wird die Größe in insgesamt Bereichen zugewiesen.

-    Name:`CrashDump`
   
-    Typ: Verwenden Sie für MBR, `0x07`. Verwenden Sie GPT`{ebd0a0a2-b9e5-4433-87c0-68b6b72699c7}`
    
-    FileSystem:`FAT32`
   
-    TotalSectors: `1228800` (= 600 MB)

### <a name="required-fields"></a>Erforderliche Felder

Diese Felder sind erforderlich ist, werden die folgenden Werte für IoTCore unterstützt: 

-    Version:`IoTUAP`

-   SectorSize:`512`

-   ChunkSize:`128`

-   DefaultPartitionByteAlignment:`0x200000`
    
### <a name="storage-size-estimations"></a>Speicher Größe Einschätzung 

Die folgenden Diagramme enthalten eine Übersicht über zwei Konfigurationen. 

**2 GB-Konfiguration**  (2048MB hat in der Regel 1843MB für die Speicherung)

![2GB Partitionslayout: EFIESP, MainOS und Daten. MainOS umfasst Windows und freiem Speicherplatz](images/partition-layout-2gb.png)

|Partition    |Inhalt   |MB   |Bereiche |Hinweise                    |
|-------------|-----------|-----|--------|---------------------------|
|EFIESP       |EFIESP     |32   |65536   |EFIESP Größe                |
|Hauptfenster OS      |Hauptfenster OS    |800  |1638400 |MainOS (Schätzung)          |
|Hauptfenster OS      |Freier Speicherplatz |128  |262144  |MainOS Reserven            |
|Data         |Data       |883  |1808384 |Wird erweitert, um Speicherplatz zu füllen |
|**INSGESAMT**        |           |**1843** |**3774464** |                           |


**4GB-Konfiguration:**  (4096MB hat normalerweise 3600MB für die Speicherung verfügbar)

![4GB Partitionslayout: EFIESP, MainOS, Speicherabbild und Daten. MainOS umfasst Windows und freiem Speicherplatz](images/partition-layout-4gb.png)

|Partition    |Inhalt   |MB   |Bereiche |Hinweise                    |
|-------------|-----------|-----|--------|---------------------------|
|EFIESP       |EFIESP     |32   |65536   |EFIESP Größe                |
|Hauptfenster OS      |Hauptfenster OS    |800  |1638400 |MainOS (Schätzung)          |
|Hauptfenster OS      |Freier Speicherplatz |512  |1048576 |MainOS Reserven            |
|Speicherabbild    |Absturzabbild |600  |1228800 |Speicherabbild-Größe             |
|Data         |Data       |1656 |3391488 |Wird erweitert, um Speicherplatz zu füllen |
|**INSGESAMT**        |           |**3600** |**7372800** |         |


### <a name="device-platform-layout-oemdeviceplatformxml"></a>Gerät-Plattform Layout (OEMDevicePlatform.xml)

OEMDevicePlatform.xml gibt die Menge der verfügbaren freien Blöcke in das Gerät, und welche Partitionen komprimiert werden. Beispiel:
   ``` syntax
   <?xml version="1.0" encoding="utf-8"?>
   <OEMDevicePlatform xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns="http://schemas.microsoft.com/embedded/2004/10/ImageUpdate">
      <MinSectorCount>7372800</MinSectorCount>
      <DevicePlatformIDs>
        <ID>*</ID>
      </DevicePlatformIDs>
     <CompressedPartitions>
       <Name>MainOS</Name>
     </CompressedPartitions>
   </OEMDevicePlatform>
   ```

## <a name="bsp-samples-in-iot-adk-addonkit"></a>BSP Beispiele in IoT-ADK-AddonKit

Die IoT ADK AddOnKit enthält BSP Beispiele für die folgenden bewertungseinrichtungen, diese Dateien enthalten:

- {_Bogen_} \Source-\BSP\\{_BSPName_}
  - \OEMInputSamples: Beispiel OEM-Dateien Eingabe
  - \Packages: BSP bestimmte Pakete und Feature-Manifestdatei

Zusätzliche Quelldateien finden Sie unter [Windows 10 IoT Board Support Kernpaket-Quelldateien](https://github.com/ms-iot/bsp).

### <a name="arm-rpi2"></a>ARM: RPi2

Die Brombeere Pi BSP 2.

### <a name="arm-customrpi2"></a>ARM: CustomRPi2

Eine benutzerdefinierte Version von Himbeeren Pi 2 BSP, wobei in benutzerdefinierten GPIO Treiber und Gerät Layouts verwendet werden.  Da benutzerdefinierte Treiber verwendet werden, werden die für die Zielgruppenadressierung Gerätekomponenten in generischen Komponenten geändert. 

### <a name="x86-mbm"></a>X86: MBM

Intel MinnowBoard Max Pinnwand BSP unterstützt und bedient von Microsoft. Dies ist für die Intel MinnowBoard Max Übersichten.

### <a name="x86-custommbm"></a>X86: CustomMBM

CustomMBM ist eine benutzerdefinierte Version von der Intel MinnowBoard Max Pinnwand BSP, wobei in benutzerdefinierten GPIO Treiber und Gerät Layouts verwendet werden. Da benutzerdefinierte Treiber verwendet werden, werden die Komponenten für die Zielgruppenadressierung in generischen Komponenten geändert.

## <a name="related-topics"></a>Verwandte Themen
[Quelldateien für Windows 10 IoT Core Board Support-Paket](https://github.com/ms-iot/bsp)

[Erstellen eigener Board Support-Paket (BSP)](create-a-new-bsp.md)

[Starten und UEFI](https://msdn.microsoft.com/windows/hardware/drivers/bringup/boot-and-uefi) 
[Windows und GPT-häufig gestellte Fragen](https://msdn.microsoft.com/en-us/library/windows/hardware/dn640535(v=vs.85).aspx).  
