---
author: Justinha
Description: Festplatte UEFI, GPT-basierte Partitionen
ms.assetid: a6c97be2-1d1f-4639-9771-3b17234370e6
MSHAttr: PreferredLib:/library/windows/hardware
title: Festplatte UEFI, GPT-basierte Partitionen
ms.openlocfilehash: 5e95875f7bc2c5219f79a082325d518e087760a0
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="uefigpt-based-hard-drive-partitions"></a>Festplatte UEFI, GPT-basierte Partitionen


Erstellen Sie benutzerdefinierte Partitionslayouts für Ihre Festplatten (Festplatten), Solid-State-Laufwerke (SSDs) und andere Laufwerke, wenn Windows auf Unified Extensible Firmware Interface UEFI-basierten Geräten bereitstellen.

**Hinweis**  Wenn Sie einen benutzerdefinierten Partitionslayout auf Windows-10 für desktop-Editionen (Home Pro, Enterprise, Education), Update zu, und das Skript Drucktaste Wiederherstellung verwenden können also die Wiederherstellungstools das Layout individuelle Partitionierung bei Bedarf neu erstellen.

 

In diesem Thema:

-   [Laufwerk Partition Regeln](#diskpartitionrules)
-   [Standard-layout](#recommendedpartitionconfigurations)
-   [Beispielskript Diskpart](#relatedsamplefiles)

## <a name="span-iddiskpartitionrulesspanspan-iddiskpartitionrulesspanspan-iddiskpartitionrulesspandrive-partition-rules"></a><span id="DiskPartitionRules"></span><span id="diskpartitionrules"></span><span id="DISKPARTITIONRULES"></span>Laufwerk Partition Regeln


Wenn Sie zu einem Gerät UEFI-basierten Windows bereitstellen, müssen Sie die Festplatte formatieren, die die Windows-Partition mithilfe einer Dateisystem von GUID Partition Table (GPT) enthält. Zusätzliche Laufwerke können der GPT- oder das Dateiformat der master Boot Record (MBR) verwenden.

Ein GPT-Laufwerk kann bis zu 128 Partitionen verfügen.

Jede Partition kann maximal 18 Exabyte (~18.8 Millionen Terabytes) Speicherplatz verfügen.

**Windows Partition Anforderungen:**

-   **Systempartition**

    Das Gerät muss eine Systempartition enthalten. Auf GPT-Laufwerken ist dies der Systempartition EFI oder der ESP genannt. Diese Partition wird normalerweise auf der primären Festplatte gespeichert. Das Gerät startet diese Partition.

    Die minimale Größe dieser Partition beträgt 100 MB, und Sie müssen mit dem Dateiformat FAT32 formatiert sein.

    Diese Partition wird vom Betriebssystem verwaltet und darf keine anderen Dateien, einschließlich Windows RE-Tools.

    **Hinweis**  
    Für Advanced Format 4K Native-Laufwerke (4-KB-pro Sektor) Laufwerke ist die minimale Größe 260 MB aufgrund einer Einschränkung des Dateiformats FAT32. Die Partition mit mindestens Größe der FAT32-Laufwerken wird als Sektorgröße (4 KB) x 65527 = 256 MB berechnet.

    Erweiterte Format 512e Laufwerke sind diese Einschränkung nicht betroffen, da ihre Sektorgröße emulierten 512 Bytes ist. 512 Bytes x 65527 = 32 MB, die kleiner als die Mindestgröße von 100 MB für diese Partition ist.

     

-   **Microsoft® reservierte Partition (MSR)**

    In Windows 10 beginnen, ist die Größe der MSR 16 MB.

    Fügen Sie eine MSR auf jedem Laufwerk GPT-Partition Management zu unterstützen. Die MSR ist eine reservierte Partition, die keine Partition-ID. erhält Es kann keine Benutzerdaten speichern.

-   **Andere Dienstprogrammpartitionen**

    Alle anderen Dienstprogrammpartitionen nicht von Windows verwaltet müssen vor dem Windows, der Daten und der Wiederherstellung Bild Partitionen befinden. Dies ermöglicht Endbenutzern Aktionen wie das Ändern der Größe der Windows-Partition ohne Systemprogramme ausführen.

    Verhindern Sie, dass Endbenutzer versehentlich Dienstprogrammpartitionen durch das Identifizieren sie über ein GPT-Attribut zu ändern. Dadurch wird verhindert, dass diese Partitionen im Datei-Explorer angezeigt werden.

    **Festlegen von Partitionen als Dienstprogrammpartitionen**

    -   Wenn Sie mithilfe des Tools **DiskPart** Windows bereitstellen, verwenden Sie das **Attribute Datenträgersatz GPT\_ATTRIBUT\_PLATTFORM\_ERFORDERLICH** Befehl nach dem Erstellen der Partition, um als ein Hilfsprogramm Partition ermitteln. Weitere Informationen finden Sie im MSDN-Artikel: [PARTITION\_INFORMATIONEN\_GPT-Struktur](http://go.microsoft.com/fwlink/p/?linkid=240300).

    **Um sicherzustellen, dass die System-und Dienstprogramm vorhanden**

    1.  Klicken Sie auf **Start**, mit der rechten Maustaste in **Dieser PC**, und klicken Sie dann auf **Verwalten**. Das Fenster **Computerverwaltung** wird geöffnet.
    2.  Klicken Sie auf **Datenträgerverwaltung**. Die Liste der verfügbaren Laufwerke und Partitionen wird angezeigt.
    3.  Bestätigen Sie in der Liste der Laufwerke und Partitionen, dass die System und Programm-Partitionen vorhanden sind und keinen Laufwerkbuchstaben zugewiesen werden.
-   **Windows-partition**
    -   Die Partition benötigen mindestens 20 Gigabyte (GB) Festplattenspeicher für 64-Bit-Versionen oder 16 GB für 32-Bit-Versionen.
    -   Die Windows-Partition muss mit dem NTFS-Dateiformat formatiert sein.
    -   Die Windows-Partition muss genügend 10 GB freiem Speicherplatz verfügen, nachdem der Benutzer die Out Of Box-Experience (OOBE) abgeschlossen wurde.
-   **Recovery Tools partition**

    Diese Partition muss mindestens 300 MB sein.

    Diese Partition benötigen genügend Speicherplatz für das Windows Recovery Environment Tools Bild (in der Regel zwischen 250-300MB, je nach Basissprache und Anpassungen hinzugefügt winre.wim) sowie genügend freier Speicherplatz, damit die Partition von Sicherungsdienstprogramme erfasst werden kann:

    -   Wenn die Partition kleiner als 500 MB ist, benötigen sie mindestens 50 MB freiem Speicherplatz.
    -   Ist die Partition 500 MB oder mehr hat, benötigen sie mindestens 320 MB freiem Speicherplatz.
    -   Wenn die Partition größer als 1 GB ist, wird empfohlen, diese mindestens 1 GB freiem gewählt werden sollte.
    -   In diesem Abschnitt muss verwendet die Typ-ID: DE94BBA4 - 06D 1 – 4D 40-A16A-BFD50179D6AC.
    -   Die Wiederherstellungstools sollten in einer separaten Partition als und automatisches Failover zu unterstützen und zur Unterstützung der Windows-Partition mit Windows BitLocker Drive Encryption verschlüsselte Partitionen starten.

    Es wird empfohlen, dass Sie diese Partition unmittelbar nach der Windows-Partition platzieren. Dadurch wird Windows ändern und neu erstellen der Partition später, wenn zukünftige Updates vergrößern Recovery erfordern.

-   **Datenpartitionen**

    Das empfohlene Partitionslayout für Windows 10 enthält keine Datenpartitionen. Jedoch, wenn Datenpartitionen erforderlich sind, sollten sie nach Windows RE-Partition platziert werden. Dies ermöglicht zukünftige Updates Windows RE Windows RE-Partition zu steigern, indem Sie die Windows-Partition verkleinern.

    In diesem Layout erschwert für Endbenutzer zu Datenpartition entfernen und den Speicherplatz mit der Windows-Partition zusammenführen. Hierzu muss Windows RE-Partition am Ende der freie Speicherplatz freigegeben aus der Datenpartition verschoben werden, so, dass die Windows-Partition erweitert werden kann.

    Windows 10 enthält keine Funktionalität oder das Dienstprogramm, um diesen Vorgang zu vereinfachen. Jedoch können Hersteller entwickeln und Bereitstellen solches Dienstprogramm Datenpartitionen PCs ausgeliefert werden.

## <a name="span-idrecommendedpartitionconfigurationsspanspan-idrecommendedpartitionconfigurationsspanspan-idrecommendedpartitionconfigurationsspanpartition-layout"></a><span id="RecommendedPartitionConfigurations"></span><span id="recommendedpartitionconfigurations"></span><span id="RECOMMENDEDPARTITIONCONFIGURATIONS"></span>Partitions-Layouts


Ist das Standardlayout Partition für UEFI-basierte PCs: eine Systempartition, eine MSR, eine Windows-Partition und eine Wiederherstellung Tools Partition. Wenn Sie mit einem startbaren USB-Schlüssel, die durch Windows Imaging und Konfiguration Designer (ICD) Windows installieren, wird das folgende Layout standardmäßig erstellt.

![Diagramm der Partition Standardlayout: System, Msr, Windows und Wiederherstellung](images/dep-win10-partitions-uefi.png)

In diesem Layout können Sie Windows BitLocker Drive Encryption über beide Windows und über die Windows-Recovery-Umgebung verwenden.

## <a name="span-idrelatedsamplefilesspanspan-idrelatedsamplefilesspanspan-idrelatedsamplefilesspansample-files-configure-drive-partitions-by-using-windows-pe-and-diskpart-scripts"></a><span id="RelatedSampleFiles"></span><span id="relatedsamplefiles"></span><span id="RELATEDSAMPLEFILES"></span>Beispieldateien: Konfigurieren von Partitionen mithilfe von Windows PE und DiskPart-Skripts


Starten Sie für die Image-basierte Bereitstellung PC [Windows PE](winpe-intro.md), und klicken Sie dann verwenden Sie das **DiskPart** -Tool, um die Partitionsstrukturen auf Ihre Anlaufstelle PCs erstellen.

**Hinweis**  
In diesen Beispielen **DiskPart** Partitionen werden die Buchstaben zugewiesen: System = S, Windows = W und Recovery = R. GPT erhält keinen Laufwerkbuchstaben.

Es wird empfohlen, Ändern der Laufwerkbuchstabe Windows mit einem Laufwerkbuchstaben, der gegen Ende des Alphabet, beispielsweise W verwenden, um Laufwerk Buchstaben Konflikte zu vermeiden. Verwenden Sie nicht X, da diese Laufwerkbuchstaben für Windows PE reserviert ist. Nach dem Neustart des Geräts wird die Windows-Partition den Buchstaben C zugewiesen, und die anderen Partitionen nicht Laufwerkbuchstaben erhalten.

Nach einem Neustart weist zu Windows PE Datenträger Buchstaben alphabetisch, beginnend mit dem Buchstaben C, ohne dabei die Konfiguration im Windows-Setup zu berücksichtigen. Diese Konfiguration kann basierend auf das Vorhandensein von verschiedenen Laufwerken ändern, wie USB-Laufwerke.

 

Die folgenden Schritte beschreiben Partitionieren der Festplatten und Bilder anwenden vorbereiten. Sie können den Code in den Abschnitten verwenden, die zum Ausführen dieser Schritte befolgen.

**Partitionieren von Festplatten und Vorbereiten von Bildern anwenden**

1.  Speichern Sie den folgenden Code in die als eine Textdatei (CreatePartitions UEFI.txt) auf einem USB flash-Laufwerk.

    ``` syntax
    rem == CreatePartitions-UEFI.txt ==
    rem == These commands are used with DiskPart to
    rem    create four partitions
    rem    for a UEFI/GPT-based PC.
    rem    Adjust the partition sizes to fill the drive
    rem    as necessary. ==
    select disk 0
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
    rem                (winre.wim) plus free space                   **
    rem ==    c. Prepare the Windows partition ========= 
    format quick fs=ntfs label="Windows"
    assign letter="W"
    rem === 4. Recovery tools partition ================
    create partition primary
    format quick fs=ntfs label="Recovery tools"
    assign letter="R"
    set id="de94bba4-06d1-4d40-a16a-bfd50179d6ac"
    gpt attributes=0x8000000000000001
    list volume
    exit
    ```

2.  Verwenden Sie Windows PE, um den Ziel-PC zu starten.

3.  Bereinigen Sie und Partitionieren Sie das Laufwerk. In diesem Beispiel wird die *F* der Buchstabe des USB flash-Laufwerk.

    ``` syntax
    DiskPart /s F:\CreatePartitions-UEFI.txt
    ```

4.  Wenn Sie eine benutzerdefinierte Partitionslayout auf Windows-10 für desktop-Editionen verwenden, aktualisieren Sie das Skript Drucktaste Recovery damit die Wiederherstellungstools das Layout individuelle Partitionierung bei Bedarf neu erstellen können.

## <a name="span-idnextstepsspanspan-idnextstepsspanspan-idnextstepsspannext-steps"></a><span id="NextSteps"></span><span id="nextsteps"></span><span id="NEXTSTEPS"></span>Nächste Schritte


Verwenden Sie ein Bereitstellungsskript, um die Windows-Abbilder auf den neu erstellten Partitionen anzuwenden. Weitere Informationen finden Sie unter [Erfassung und Anwenden von Windows, System, und Recovery Partitionen](capture-and-apply-windows-system-and-recovery-partitions.md).

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Konfigurieren Sie Festplatte BIOS/MBR-basierte Partitionen](configure-biosmbr-based-hard-drive-partitions.md)

[BitLocker Drive Encryption](bitlocker-drive-encryption.md)

[Windows PE: Installieren auf einer Festplatte (flach Boot oder nicht-RAM)](winpe-install-on-a-hard-drive--flat-boot-or-non-ram.md)

[Konfigurieren der Spiegelung](http://go.microsoft.com/fwlink/?LinkId=733824)

[Der Windows- und GPT – häufig gestellte Fragen](http://go.microsoft.com/fwlink/?LinkId=88211)

 

 






