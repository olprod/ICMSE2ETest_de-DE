---
author: Justinha
Description: Festplatte BIOS/MBR-basierte Partitionen
ms.assetid: 653e0c30-c90d-4d6b-ac77-6489501bad36
MSHAttr: PreferredLib:/library/windows/hardware
title: Festplatte BIOS/MBR-basierte Partitionen
ms.openlocfilehash: b901feb2349ba7ef570dc061067ec86dd4c20a34
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="biosmbr-based-hard-drive-partitions"></a>Festplatte BIOS/MBR-basierte Partitionen


Erstellen Sie benutzerdefinierte Partitionslayouts für Ihren Festplatten (Festplatten), Solid-State-Laufwerke (SSDs) und andere Laufwerke, wenn Windows auf BIOS-basierten Geräten bereitstellen.

**Hinweis**  Wenn Sie einen benutzerdefinierten Partitionslayout auf Windows-10 für desktop-Editionen (Home Pro, Enterprise, Education), Update zu, und das Skript Drucktaste Wiederherstellung verwenden können also die Wiederherstellungstools das Layout individuelle Partitionierung bei Bedarf neu erstellen.


## <a name="span-iddiskpartitionrulesspanspan-iddiskpartitionrulesspanspan-iddiskpartitionrulesspandrive-partition-rules"></a><span id="DiskPartitionRules"></span><span id="diskpartitionrules"></span><span id="DISKPARTITIONRULES"></span>Laufwerk Partition Regeln


Wenn Sie zu einem Gerät BIOS-basierten Windows bereitstellen, müssen Sie die Festplatten mithilfe einer Dateisystem MBR formatieren. Windows unterstützt nicht das Dateisystem GUID Partition Table (GPT) auf BIOS-basierte Computer.

Ein MBR-Laufwerk kann bis zu vier Standardpartitionen aufweisen. In der Regel werden diese Standardpartitionen als *primäre Partitionen*festgelegt. Informationen zum Erstellen zusätzliche Partitionen jenseits dieser Grenze finden Sie unter [Konfigurieren von mehr als vier Partitionen auf einer BIOS/MBR-basierten Festplatte](configure-more-than-four-partitions-on-a-biosmbr-based-hard-disk.md).

**Windows Partition Anforderungen:**

-   **Systempartition**

    Jedes startbare Laufwerk muss eine Systempartition enthalten. Die Systempartition muss als aktive Partition konfiguriert werden.

    Die minimale Größe dieser Partition beträgt 100 MB.

-   **Windows-partition**
    -   Diese Partition benötigen mindestens 20 Gigabyte (GB) Festplattenspeicher für 64-Bit-Versionen oder 16 GB für 32-Bit-Versionen.
    -   Diese Partition muss mit dem NTFS-Dateiformat formatiert sein.
    -   Diese Partition muss genügend 10 GB freiem Speicherplatz verfügen, nachdem der Benutzer die Out Of Box-Experience (OOBE) abgeschlossen wurde.
    -   Diese Partition kann bis zu 2 Terabyte (TB) Speicherplatz verfügen. Softwaretools so erweitern Sie den sichtbaren Partition Platz über 2 TB werden auf BIOS nicht unterstützt, da sie softwarelösungen der Anwendungskompatibilität und der Wiederherstellung beeinträchtigen können.
-   **Recovery Tools partition**

    Das Windows Recovery Environment (Windows RE) Tools Bild (winre.wim) sollte in einer separaten Partition als die Windows-Partition zur Unterstützung der automatischen Failovers und zum Starten des Windows BitLocker Drive Encryption verschlüsselt Partitionen unterstützen.

    Während dieses Bild auf der gleichen Partition als Systempartition berücksichtigt werden kann, wird empfohlen, dass Sie diese Partition in einer separaten Partition, sofort nach der Windows-Partition platzieren. Dadurch wird Windows ändern und neu erstellen der Partition später, wenn zukünftige Updates vergrößern Recovery erfordern.

    Diese Partition benötigen genügend Speicherplatz für das Windows Recovery Environment Tools Bild (in der Regel zwischen 250-300MB, je nach Basissprache und Anpassungen hinzugefügt winre.wim) sowie genügend freier Speicherplatz, damit die Partition von Sicherungsdienstprogramme erfasst werden kann:

    -   Wenn die Partition kleiner als 500 MB ist, benötigen sie mindestens 50 MB freiem Speicherplatz.
    -   Ist die Partition 500 MB oder mehr hat, benötigen sie mindestens 320 MB freiem Speicherplatz.
    -   Wenn die Partition größer als 1 GB ist, wird empfohlen, diese mindestens 1 GB freiem gewählt werden sollte.

    <!-- -->

    -   Es muss mindestens 320 MB freiem Speicherplatz verfügen.
    -   Es wird empfohlen, dass sie mindestens 1 GB freiem verfügen soll.
-   **Datenpartitionen**

    Das empfohlene Partitionslayout für Windows 10 enthält keinen Dienstprogramm oder Datenpartitionen.

    Jedoch wenn Dienstprogramm oder Daten Partitionen benötigt werden, sollten sie vor der Windows-Partition oder nach Windows RE-Partition platziert werden. Durch Zusammenhalten der Windows- und der Wiederherstellungspartitionen, klicken Sie dann werden bei der Windows RE-Bereich zur Verfügung, die Zukunft aktualisiert Windows können Windows RE-Partition zu steigern, indem Sie die Windows-Partition verkleinern.

    In diesem Layout erschwert für Endbenutzer zu Datenpartition entfernen und den Speicherplatz mit der Windows-Partition zusammenführen. Windows RE-Partition müssen möglicherweise bis zum Ende der freie Speicherplatz freigegeben, die von der Datenpartition verschoben werden soll, damit die Windows-Partition erweitert werden kann. Windows 10 enthält keine Funktionalität oder das Dienstprogramm, um diesen Vorgang zu vereinfachen. Jedoch können Hersteller entwickeln und Bereitstellen solches Dienstprogramm Datenpartitionen PCs ausgeliefert werden.

    Jede Partition kann bis zu 2 Terabyte (TB) Speicherplatz verfügen.

    Wenn Sie mehr als vier Partitionen gesamte auf den Datenträger hinzufügen möchten, finden Sie unter [Konfigurieren von mehr als vier Partitionen auf einer BIOS/MBR-basierten Festplatte](configure-more-than-four-partitions-on-a-biosmbr-based-hard-disk.md) Weitere Informationen.

## <a name="span-idrecommendedpartitionconfigurationsspanspan-idrecommendedpartitionconfigurationsspanspan-idrecommendedpartitionconfigurationsspanpartition-layout"></a><span id="RecommendedPartitionConfigurations"></span><span id="recommendedpartitionconfigurations"></span><span id="RECOMMENDEDPARTITIONCONFIGURATIONS"></span>Partitions-Layouts


Wenn Sie mit einem startbaren USB-Schlüssel, die durch Windows Imaging und Konfiguration Designer (ICD) Windows installieren, wird das folgende Layout standardmäßig erstellt: eine Systempartition, eine Windows-Partition und eine Wiederherstellung Tools Partition.

![Diagramm der Partition Standardlayout: System, Windows und Wiederherstellung](images/dep-win10-partitions-bios.png)

## <a name="span-idusingsystemandutilitypartitionsspanspan-idusingsystemandutilitypartitionsspanspan-idusingsystemandutilitypartitionsspansystem-and-utility-partitions"></a><span id="UsingSystemAndUtilityPartitions"></span><span id="usingsystemandutilitypartitions"></span><span id="USINGSYSTEMANDUTILITYPARTITIONS"></span>Die System-und Dienstprogramm


Standardmäßig werden Partitionen im Datei-Explorer nicht angezeigt. Dadurch verhindern, dass Endbenutzer versehentlich eine Partition zu ändern.

**Festlegen von Partitionen als Dienstprogrammpartitionen**

1.  Wenn Sie mithilfe von Windows ICD Windows bereitstellen, wird der Partitionstyp automatisch festgelegt.
2.  Verwenden, wenn Sie mithilfe des Tools **DiskPart** Windows bereitstellen, die **Satz-Id = 27** Befehl nach dem Erstellen der Partition.

**Um sicherzustellen, dass die System-und Dienstprogramm vorhanden**

1.  Klicken Sie auf **Start**, mit der rechten Maustaste in **Dieser PC**, und klicken Sie dann auf **Verwalten**. Das Fenster **Computerverwaltung** wird geöffnet.
2.  Klicken Sie auf **Datenträgerverwaltung**. Die Liste der verfügbaren Laufwerke und Partitionen wird angezeigt.
3.  Bestätigen Sie in der Liste der Laufwerke und Partitionen, dass die System und Programm-Partitionen vorhanden sind und keinen Laufwerkbuchstaben zugewiesen werden.

## <a name="span-idrelatedsamplefilesspanspan-idrelatedsamplefilesspanspan-idrelatedsamplefilesspansample-files-configuring-disk-layout-by-using-windows-pe-and-diskpart-scripts"></a><span id="RelatedSampleFiles"></span><span id="relatedsamplefiles"></span><span id="RELATEDSAMPLEFILES"></span>Beispieldateien: Konfigurieren mithilfe von Windows PE und DiskPart-Skripts und Datenträgerlayout


Starten Sie für die Image-basierte Bereitstellung PC [Windows PE](winpe-intro.md), und klicken Sie dann verwenden Sie das **DiskPart** -Tool, um die Partitionsstrukturen auf Ihre Anlaufstelle PCs erstellen.

**Hinweis**  
In diesen Beispielen **DiskPart** Partitionen werden die Buchstaben zugewiesen: System = S, Windows = W und Recovery = R.

Es wird empfohlen, Ändern der Laufwerkbuchstabe Windows mit einem Laufwerkbuchstaben, der gegen Ende des Alphabet, beispielsweise W verwenden, um Laufwerk Buchstaben Konflikte zu vermeiden. Verwenden Sie nicht X, da diese Laufwerkbuchstaben für Windows PE reserviert ist. Nach dem Neustart des Geräts wird die Windows-Partition den Buchstaben C zugewiesen, und die anderen Partitionen nicht Laufwerkbuchstaben erhalten.

Nach einem Neustart weist zu Windows PE Datenträger Buchstaben alphabetisch, beginnend mit dem Buchstaben C, ohne dabei die Konfiguration im Windows-Setup zu berücksichtigen. Diese Konfiguration kann basierend auf das Vorhandensein von verschiedenen Laufwerken ändern, wie USB-Laufwerke.

 

Die folgenden Schritte beschreiben Partitionieren der Festplatten und Bilder anwenden vorbereiten. Sie können den Code in den Abschnitten verwenden, die zum Ausführen dieser Schritte befolgen.

**Partitionieren von Festplatten und Vorbereiten von Bildern anwenden**

1.  Speichern Sie den folgenden Code als Textdatei (CreatePartitions BIOS.txt) auf einem USB-Laufwerk.

    ``` syntax
    rem == CreatePartitions-BIOS.txt ==
    rem == These commands are used with DiskPart to
    rem    create three partitions
    rem    for a BIOS/MBR-based computer.
    rem    Adjust the partition sizes to fill the drive
    rem    as necessary. ==
    select disk 0
    clean
    rem == 1. System partition ======================
    create partition primary size=100
    format quick fs=ntfs label="System"
    assign letter="S"
    active
    rem == 2. Windows partition =====================
    rem ==    a. Create the Windows partition =======
    create partition primary
    rem ==    b. Create space for the recovery tools  
    shrink minimum=500
    rem       ** NOTE: Update this size to match the
    rem                size of the recovery tools 
    rem                (winre.wim)                 **
    rem ==    c. Prepare the Windows partition ====== 
    format quick fs=ntfs label="Windows"
    assign letter="W"
    rem == 3. Recovery tools partition ==============
    create partition primary
    format quick fs=ntfs label="Recovery"
    assign letter="R"
    set id=27
    list volume
    exit
    ```

2.  Verwenden Sie Windows PE zum Starten des Zielcomputers.
3.  Bereinigen Sie und Partitionieren Sie das Laufwerk. In diesem Beispiel wird die *F* der Buchstabe des USB flash-Laufwerk.

    ``` syntax
    DiskPart /s F:\CreatePartitions-BIOS.txt
    ```

4.  Wenn Sie eine benutzerdefinierte Partitionslayout auf Windows-10 für desktop-Editionen verwenden, aktualisieren Sie das Skript Drucktaste Recovery damit die Wiederherstellungstools das Layout individuelle Partitionierung bei Bedarf neu erstellen können.

## <a name="span-idnextstepsspanspan-idnextstepsspanspan-idnextstepsspannext-steps"></a><span id="NextSteps"></span><span id="nextsteps"></span><span id="NEXTSTEPS"></span>Nächste Schritte


Verwenden Sie ein Bereitstellungsskript, um die Windows-Abbilder auf den neu erstellten Partitionen anzuwenden. Weitere Informationen finden Sie unter [Erfassung und Anwenden von Windows, System, und Recovery Partitionen](capture-and-apply-windows-system-and-recovery-partitions.md).

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Konfigurieren von mehr als vier Partitionen auf einer Festplatte BIOS/MBR-basierte](configure-more-than-four-partitions-on-a-biosmbr-based-hard-disk.md)

[Konfigurieren von Partitionen UEFI, GPT-basierten Festplatte](configure-uefigpt-based-hard-drive-partitions.md)

[BitLocker Drive Encryption](bitlocker-drive-encryption.md)

[Konfigurieren der Spiegelung](http://go.microsoft.com/fwlink/?LinkId=733824)

 

 






