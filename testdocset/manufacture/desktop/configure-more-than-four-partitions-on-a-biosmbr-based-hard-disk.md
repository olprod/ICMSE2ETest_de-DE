---
author: Justinha
Description: Konfigurieren von mehr als vier Partitionen auf einer Festplatte BIOS/MBR-basierte
ms.assetid: a1df0974-870f-498a-9994-5f614d8a308b
MSHAttr: PreferredLib:/library/windows/hardware
title: Konfigurieren von mehr als vier Partitionen auf einer Festplatte BIOS/MBR-basierte
ms.openlocfilehash: ab2d814c98f62d145cddebe8fd02788f8ec13c01
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="configure-more-than-four-partitions-on-a-biosmbr-based-hard-disk"></a>Konfigurieren von mehr als vier Partitionen auf einer Festplatte BIOS/MBR-basierte


In diesem Thema wird beschrieben, wie mehr als vier Datenträgerpartitionen zu konfigurieren, bei der Bereitstellung von Windows auf BIOS und MBR (MBR)-basierte Geräte.

## <a name="span-iddiskpartitionrulesspanspan-iddiskpartitionrulesspanspan-iddiskpartitionrulesspandisk-partition-rules"></a><span id="DiskPartitionRules"></span><span id="diskpartitionrules"></span><span id="DISKPARTITIONRULES"></span>Datenträger Partition Regeln


-   Auf BIOS-basierte Systeme können Sie eine der vier Standardpartitionen als einer *erweiterten Partition*festlegen.

    Eine erweiterte Partition ist eine besondere Partition, die in zusätzliche Partitionen unterteilt werden kann, die *logische Partitionen*aufgerufen werden. Eine erweiterte Partition kann keine Dateien gespeichert. Eine erweiterte Partition erhält keine Partition-ID.

-   Sie können so viele logische Partitionen wie Ihre Datenträger speichern kann einschließen.

    Logische Partitionen können Dateien speichern. Sie können eine logische Partition als die Windows-Partition.

Zusätzliche Datenträger Partition-Regeln für BIOS-basierte Systeme finden Sie unter [Configure BIOS/MBR-Based Hard Drive-Partitionen](configure-biosmbr-based-hard-drive-partitions.md).

**Empfehlungen**

1.  Fügen Sie vor dem Hinzufügen der Windows-Partition System-und Dienstprogramm hinzu.

2.  Fügen Sie die Wiederherstellung Tools Partition unmittelbar nach der Windows-Partition. Wenn Sie diesen Auftrag Partition verwenden, kann Klicken Sie dann zukünftige Updates auf die Wiederherstellungstools benötigt werden, die Partition automatisch geändert werden.

**Beispiel Partitionslayout:**

![Beispiel Partitionslayout: Systempartition, Dienstprogramm-Partition, Dienstprogramm-Partition, und einer erweiterten Partition, die eine Windows-Partition und eine Wiederherstellungspartition enthält](images/dep-win10-partitions-bios-morethanfour.png)

## <a name="span-idconfiguringpartitionsusingdiskpartspanspan-idconfiguringpartitionsusingdiskpartspanspan-idconfiguringpartitionsusingdiskpartspanconfiguring-disk-partitions-by-using-a-diskpart-script-in-windows-pe"></a><span id="ConfiguringPartitionsUsingDiskPart"></span><span id="configuringpartitionsusingdiskpart"></span><span id="CONFIGURINGPARTITIONSUSINGDISKPART"></span>Konfigurieren von Datenträgerpartitionen mithilfe eines DiskPart-Skripts in Windows PE


Abbildbasierte Bereitstellung starten Sie das Gerät mit Windows PE und klicken Sie dann verwenden Sie das DiskPart-Tool, um die Partitionsstrukturen auf Ihren Geräten Ziel zu erstellen. Weitere Informationen finden Sie unter [Anwenden von Bildern mithilfe von DISM](apply-images-using-dism.md).

**Hinweis**  
Windows PE ordnet Datenträger Buchstaben alphabetisch, beginnend mit dem Buchstaben "C", ohne dabei die Konfiguration im Windows-Setup zu berücksichtigen. Diese Konfiguration kann basierend auf das Vorhandensein von verschiedenen Laufwerken, einschließlich USB-Laufwerke ändern.

In diesen Beispielen DiskPart werden die Partitionen die Buchstaben "U", "V", "S", "W" und "R" konfliktvermeidung Laufwerkbuchstaben zugewiesen. Nach dem Neustart des Geräts weist Windows PE automatisch der Buchstabe "C" in der Windows-Partition. Die Utility1, Utility2, System und Recovery Bild Partitionen empfangen keine Laufwerkbuchstaben.

 

Die folgenden Schritte beschreiben Partitionieren der Festplatten und Bilder anwenden vorbereiten. Sie können den Code in den Abschnitten verwenden, die zum Ausführen dieser Schritte befolgen.

**Partitionieren von Festplatten und Vorbereiten von Bildern anwenden**

1.  Speichern Sie den Code in den folgenden Abschnitten als Textdatei (PrepareMyPartitions.txt) auf einem USB flash-Laufwerk.

2.  Verwenden Sie Windows PE zum Starten des Zielgeräts.

3.  Verwendung der `DiskPart /s F:\PrepareMyPartitions.txt` Befehl, wobei *F*: ist der Buchstabe des USB-flash-Laufwerk partitionieren die Laufwerke, auf.

## <a name="span-idsamplecodespanspan-idsamplecodespanspan-idsamplecodespansample-code"></a><span id="Sample_code"></span><span id="sample_code"></span><span id="SAMPLE_CODE"></span>Beispielcode (engl.)


Speichern Sie den folgenden Code als "PrepareMyPartitions.txt", und führen Sie das Skript mithilfe des DiskPart-Tools die Konfiguration der Utility1, Utility2, System, erweitert, Windows und Recovery Tools Partitionen automatisieren:

``` syntax
select disk 0
clean
rem == 1. System partition ======================
create partition primary size=100
format quick fs=ntfs label="System"
assign letter="S"
active
rem == 2. Utility partition =====================
create partition primary size=100
format quick fs=ntfs label="Utility1"
assign letter="U"
set id=27
rem == 3. Utility partition =====================
create partition primary size=200
format quick fs=ntfs label="Utility2"
assign letter="V"
set id=27
rem == 4. Extended partition ====================
create partition extended
rem == 4a. Windows partition ====================
rem ==    a. Create the Windows partition =======
create partition logical
rem ==    b. Create space for the recovery tools  
shrink minimum=500
rem       ** NOTE: Update this size to match the
rem                size of the recovery tools 
rem                (winre.wim)                 **
rem ==    c. Prepare the Windows partition ====== 
format quick fs=ntfs label="Windows"
assign letter="C"
rem == 4b. Recovery tools partition ==============
create partition logical
format quick fs=ntfs label="Recovery"
assign letter="R"
set id=27
list volume
exit
```

## <a name="span-idnextstepsspanspan-idnextstepsspanspan-idnextstepsspannext-steps"></a><span id="Next_Steps"></span><span id="next_steps"></span><span id="NEXT_STEPS"></span>Nächste Schritte


Nach der Erstellung von Partitionen können Sie ein Bereitstellungsskript, die Windows-Abbilder auf die neu erstellten Partitionen angewendet. Weitere Informationen finden Sie unter [Erfassung und Anwenden von Windows, System, und Recovery Partitionen](capture-and-apply-windows-system-and-recovery-partitions.md).

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Konfigurieren Sie Festplatte BIOS/MBR-basierte Partitionen](configure-biosmbr-based-hard-drive-partitions.md)

 

 






