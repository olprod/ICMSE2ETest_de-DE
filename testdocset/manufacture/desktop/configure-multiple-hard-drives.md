---
author: Justinha
Description: Konfigurieren Sie mehrerer Festplatten
ms.assetid: 2cb7386a-b3f6-40dd-b084-fce52a7aed9b
MSHAttr: PreferredLib:/library/windows/hardware
title: Konfigurieren Sie mehrerer Festplatten
ms.openlocfilehash: f0ed2a7118ffa79b462524444cee74a0a79bcdbe
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="configure-multiple-hard-drives"></a>Konfigurieren Sie mehrerer Festplatten


Wenn Sie Windows auf einem Computer, die über mehrere Festplatten verfügt bereitstellen, können Sie überprüfen, dass das Bild auf einer bestimmten Festplatte angewendet wird, mithilfe von Hardware-spezifischen Bezeichner wie den Pfad zum Speicherort oder die Hardware Interrupt-Wert.

Der Pfad zum Speicherort ist eine Zeichenfolge, die den physischen Standort gibt an, die jedes Laufwerk mit dem Computer verbunden ist beispielsweise: `PCIROOT(0)#PCI(0100)#ATA(C00T00L00)`. Bei einen Computer Fertigung, Ihre Laufwerke Verbinden mit einen konsistenten physischen Standort verwenden, und anschließend mithilfe der Pfadzeichenfolge Speicherort um jede Festplatte zu ermitteln.

Für BIOS-basierte Computer oder einem Computer, auf dem Virtual Disk Service (VDS) ausgeführt wird, können Sie die **FESTPLATTEN WÄHLEN = SYSTEM** und **FESTPLATTEN WÄHLEN = WEITER** Befehle aus, um die entsprechenden Festplatte auswählen.

In diesem Thema:

-   [Identifizieren einen Speicherort Pfad](#identifyingdisklocationpath)
-   [Auswählen von dem Systemlaufwerk](#selectingsystemdisk)
-   [Auswählen von nicht-System-Laufwerke](#selectingnonsystemdisks)
-   [Identifizieren von dem Systemlaufwerk nach einem Neustart](#exampleidentifyingsystemdiskafterreboot)
-   [Formatieren von außerhalb des Systems Laufwerken](#exampleformattingnonsystemdisks)

## <span id="IdentifyingDiskLocationPath"></span><span id="identifyingdisklocationpath"></span><span id="IDENTIFYINGDISKLOCATIONPATH"></span>


 **Identifizieren einen Datenträgerpfad**

-   Verwenden Sie die Befehle DiskPart: **List Disk ein** und **select Datenträger &lt;Anzahl Datenträger&gt; ** (Beispiel: **Wählen Sie Datenträger 1**) zwischen den Laufwerken auf Ihrem Computer navigieren.

    Um den Pfad zum Speicherort von einem ausgewählten Laufwerk anzuzeigen, verwenden Sie den Befehl DiskPart `detail disk`.

    Im folgenden Beispiel wird der Pfad zum Speicherort des vom ausgewählten Laufwerk PCIROOT(0)\#PCI(0100)\#ATA(C00T00L00).

    ``` syntax
    DISKPART> detail disk

    HITACHI HTS722016K9SA00
    Disk ID: 5E27161A
    Type   : ATA
    Bus    : 0
    Target : 0
    LUN ID : 0
    Location Path : PCIROOT(0)#PCI(0100)#ATA(C00T00L00)
    Read-only  : No
    Boot Disk  : Yes
    PagefileDisk  : Yes
    Hibernation File Disk  : No
    CrashdumpDisk  : Yes
    Clustered Disk  : No


      Volume ###  Ltr  Label        Fs     Type        Size     Status     Info
      ----------  ---  -----------  -----  ----------  -------  ---------  --------
      Volume 1     C                NTFS   Partition    149 GB  Healthy    System

    DISKPART>
    ```

## <a name="span-idselectingdrivesspanspan-idselectingdrivesspanspan-idselectingdrivesspanselecting-drives"></a><span id="Selecting_Drives"></span><span id="selecting_drives"></span><span id="SELECTING_DRIVES"></span>Auswählen von Laufwerken


<span id="SelectingSystemDisk"></span><span id="selectingsystemdisk"></span><span id="SELECTINGSYSTEMDISK"></span>
 **Auswählen von dem Systemlaufwerk**

1.  **BIOS-basierte Computer**: Verwenden Sie den Befehl **FESTPLATTEN WÄHLEN = SYSTEM** um das standardmäßige Systemlaufwerk auszuwählen.

    Mit diesem Befehl werden das Laufwerk mit dem Interrupt 13 h Wert 80 h markiert. Wenn der Wert 80h einem USB-Laufwerk zugewiesen ist, wird mit diesem Befehl eine Festplatte, die den Wert 81 h hat markiert. Weitere Informationen finden Sie auf der folgenden Microsoft Developer Network (MSDN)-Website:

    [Konvertieren von Laufwerkbuchstaben zu MS-DOS-INT 13H Festplattenlaufwerk Zahlen](http://go.microsoft.com/fwlink/?LinkId=164574)

2.  **UEFI-basierte Computer**: um ein Laufwerk auszuwählen, verwenden Sie den Befehl DiskPart **FESTPLATTEN WÄHLEN =&lt;Pfad zum Speicherort&gt;**.

    **Hinweis**  
    Verwenden Sie nicht die **FESTPLATTEN WÄHLEN = SYSTEM** Befehl oder der GetSystemDiskNTPath-API für Unified Extensible Firmware Interface UEFI-basierte Computer, auf das Systemlaufwerk zu aktivieren. Die **FESTPLATTEN WÄHLEN = SYSTEM** Befehl und die API GetSystemDiskNTPath identifiziert das Laufwerk, das das Betriebssystem als dem Systemlaufwerk aus gestartet wurde. Wenn Sie von Windows® PE starten, wählt diesen Befehl das Laufwerk Windows PE als dem Systemlaufwerk. Wenn Sie von einem System zu, die über mehrere Laufwerke verfügt, die eine EFI-Systempartition (ESP) enthalten starten, kann mit diesem Befehl das falsche Laufwerk auswählen.

     

<span id="SelectingNonSystemDisks"></span><span id="selectingnonsystemdisks"></span><span id="SELECTINGNONSYSTEMDISKS"></span>
 **Auswählen von nicht-System-Laufwerke**

1.  **Wählen Sie das Laufwerk durch den Pfad zum Speicherort.** Um ein Laufwerk auszuwählen, verwenden Sie den Befehl DiskPart **FESTPLATTEN WÄHLEN =&lt;Pfad zum Speicherort&gt;**, wobei &lt; *Pfad zum Speicherort* &gt; ist der Pfad der Speicherort der Festplatte. Dieser Befehl kann ein Laufwerk, hängt vom Speicherort angegeben werden.

    Beispiel:

    ``` syntax
    SELECT DISK=PCIROOT(0)#PCI(0100)#ATA(C00T00L00)
    ```

2.  **Wählen Sie das Laufwerk mithilfe des Laufwerks "WEITER".** Verwenden Sie den Befehl DiskPart **FESTPLATTEN WÄHLEN = WEITER**. Dieser Befehl kann alle verbleibenden Festplatten, unabhängig vom Standort angegeben werden. Um weitere Festplatten auszuwählen, wiederholen Sie die **FESTPLATTEN WÄHLEN = WEITER** Befehl aus, um jedes Laufwerk auswählen. Wenn es keine weitere Laufwerke sind auswählen, werden DiskPart ein Fehler zurückgegeben.

    **Hinweis**  
    Der Computer verwaltet den Kontext für den **FESTPLATTEN WÄHLEN = WEITER** Befehl als DiskPart weiterhin ausgeführt wird. Wenn DISKPART beendet wird, verliert der Computer in diesem Kontext.

     

    UEFI-basierte Beispiel:

    ``` syntax
    SELECT DISK=PCIROOT(0)#PCI(0100)#ATA(C00T00L00)
    clean
    convert gpt
    rem == 1. System partition =========================
    create partition efi size=100
    rem    ** NOTE: For Advanced Format 4Kn drives,
    rem               change this value to size = 260 ** 
    format quick fs=fat32 label="System"
    assign letter="S"
    rem == 2. Microsoft Reserved (MSR) partition =======
    create partition msr size=16
    rem == 3. Windows partition ========================
    rem ==    a. Create the Windows partition ==========
    create partition primary 
    rem ==    b. Create space for the recovery tools ===
    shrink minimum=500
    rem       ** NOTE: Update this size to match the
    rem                size of the recovery tools 
    rem                (winre.wim)                    **
    rem ==    c. Prepare the Windows partition ========= 
    format quick fs=ntfs label="Windows"
    assign letter="W"
    rem === 4. Recovery tools partition ================
    create partition primary
    format quick fs=ntfs label="Recovery tools"
    assign letter="R"
    set id="de94bba4-06d1-4d40-a16a-bfd50179d6ac"
    gpt attributes=0x8000000000000001
    rem NON-SYSTEM DRIVE ===============================
    SELECT DISK=NEXT
    clean
    convert gpt
    rem == 1. Microsoft Reserved (MSR) partition =======
    create partition msr size=16
    rem == 2. Data partition ===========================
    create partition primary
    format quick fs=ntfs label="Data"
    assign letter=z
    ```

### <a name="span-idexampleidentifyingsystemdiskafterrebootspanspan-idexampleidentifyingsystemdiskafterrebootspanspan-idexampleidentifyingsystemdiskafterrebootspanidentifying-the-system-drive-after-a-reboot"></a><span id="ExampleIdentifyingSystemDiskAfterReboot"></span><span id="exampleidentifyingsystemdiskafterreboot"></span><span id="EXAMPLEIDENTIFYINGSYSTEMDISKAFTERREBOOT"></span>Identifizieren von dem Systemlaufwerk nach einem Neustart

Nach dem Neustart möglicherweise Laufwerk Textformats ändern. Im folgenden Beispielskript können Sie das Systemlaufwerk auswählen und dann neu Buchstaben der ESP, Wiederherstellung und Windows-Partitionen.

``` syntax
SELECT DISK=PCIROOT(0)#PCI(0100)#ATA(C01T01L00)
select partition=1
assign letter=s
select partition=2
assign letter=t
select partition=3
assign letter=w
```

### <a name="span-idexampleformattingnonsystemdisksspanspan-idexampleformattingnonsystemdisksspanspan-idexampleformattingnonsystemdisksspanformatting-non-system-drives"></a><span id="ExampleFormattingNonSystemDisks"></span><span id="exampleformattingnonsystemdisks"></span><span id="EXAMPLEFORMATTINGNONSYSTEMDISKS"></span>Formatieren von kein Systemlaufwerk Laufwerken

Dieses Beispielskript wählt das Systemlaufwerk und anschließend springt hinter dem Laufwerk, ohne das Ändern des Inhalts des Laufwerks. Das Skript wählt zwei kein Systemlaufwerk Laufwerke und erstellt eine einzelne, formatierte, leere Partition auf jedem Laufwerk. Die Partitionen empfangen keine Schwelle, daher es nicht notwendig ist, den sie speziell zu kennzeichnen.

UEFI-basierte Beispiel:

``` syntax
SELECT DISK=PCIROOT(0)#PCI(0100)#ATA(C01T01L00)
SELECT DISK=NEXT
clean
convert gpt
create partition msr size=16
create partition primary
format quick fs=ntfs label="DataDrive1"
SELECT DISK=NEXT
clean
convert gpt
create partition primary
format quick fs=ntfs label="DataDrive2"
```

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Festplatte Speicherort Pfadformat](hard-disk-location-path-format.md)

[DiskPart Befehlssyntax Linie](http://go.microsoft.com/fwlink/?LinkId=128458)

 

 






