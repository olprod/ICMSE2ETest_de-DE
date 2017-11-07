---
author: Justinha
Description: Aufzeichnen und Anwenden von Windows, System und Recovery Partitionen
ms.assetid: db1f011f-2cf3-46b7-a386-8333f6214b9e
MSHAttr: PreferredLib:/library/windows/hardware
title: Aufzeichnen und Anwenden von Windows, System und Recovery Partitionen
ms.openlocfilehash: a719f880cf0fe2e3e6ad61d49f2bc3719bd10634
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="capture-and-apply-windows-system-and-recovery-partitions"></a>Aufzeichnen und Anwenden von Windows, System und Recovery Partitionen


Erfassen Sie ein Windows-Abbild (. WIM) Datei und verwenden sie zum Bereitstellen von Windows für neue Geräte.

Statt erfassen jede Partition, Sie erfassen die Windows-Partition in ein Bild, und klicken Sie dann verwenden Sie die Dateien aus dem Bild so richten Sie den Rest der Partitionen auf dem Laufwerk ein.

Im folgende Diagramm veranschaulicht diesen Prozess:

![Diagramm zur Erfassung der Windows-partition](images/dep-adk-partitions-uefi-overview-capture-windows.jpg)

**Vorbereiten von Erfassen des Abbilds**

-   Verallgemeinern des Windows-Abbilds, sodass es auf anderen Geräten bereitgestellt werden kann. Weitere Informationen finden Sie unter [Sysprep (verallgemeinern) einer Windows-Installation](sysprep--generalize--a-windows-installation.md).

**Erfassen Sie das Abbild**

1.  Starten Sie das Gerät mit [Windows PE](winpe-intro.md).

2.  Optional: Leistungssteigerung für die abbilderfassung durch Festlegen des Power-Schemas auf hohe Leistung:

    ``` syntax
    powercfg /s 8c5e7fda-e8bf-4a96-9a85-a6e23a8c635c
    ```

3.  Erfassen Sie die Windows-Partition. Beispiel:

    ``` syntax
    Dism /Capture-Image /ImageFile:"D:\fabrikam.wim" /CaptureDir:C:\ /Name:Fabrikam
    ```

    D: einem USB-Laufwerk oder anderen Dateispeicherort ist.

## <a name="span-idapplyingtheimagespanspan-idapplyingtheimagespanspan-idapplyingtheimagespanapplying-the-image"></a><span id="Applying_the_image"></span><span id="applying_the_image"></span><span id="APPLYING_THE_IMAGE"></span>Anwenden des Abbilds


Nachfolgend finden Sie einige Methoden für das Abbild angewendet wird:

**Wenden Sie das Abbild manuell**

1.  Verwenden Sie auf dem Zielgerät ein DiskPart-Skript zum Konfigurieren und Formatieren von Partitionen Festplatte. Weitere Informationen finden Sie unter [Configure UEFI/GPT-Based Festplatte Laufwerk Partitionen](configure-uefigpt-based-hard-drive-partitions.md) oder [Configure BIOS/MBR-Based Hard Drive-Partitionen](configure-biosmbr-based-hard-drive-partitions.md).

    **Hinweis**  
    Wenn Sie ein Bild in ein Volume mit eine vorhandene Installation von Windows anwenden, können Dateien aus der vorherigen Installation nicht gelöscht werden. Formatieren Sie die Lautstärke mit einem Tool wie DiskPart, bevor Sie das neue Bild anwenden. Beispiel:

    ``` 
    diskpart /s D:\CreatePartitions-UEFI.txt
    ```
    D: einem USB-Laufwerk oder anderen Dateispeicherort ist.

    In diesen Beispielen **DiskPart** Partitionen werden die Buchstaben zugewiesen: System = S, Windows = W und Recovery = R.

    Es wird empfohlen, Ändern der Laufwerkbuchstabe Windows mit einem Laufwerkbuchstaben, der gegen Ende des Alphabet, beispielsweise W verwenden, um Laufwerk Buchstaben Konflikte zu vermeiden. Verwenden Sie nicht X, da diese Laufwerkbuchstaben für Windows PE reserviert ist. Nach dem Neustart des Geräts wird die Windows-Partition den Buchstaben C zugewiesen, und die anderen Partitionen nicht Laufwerkbuchstaben erhalten.

    Nach einem Neustart weist zu Windows PE Datenträger Buchstaben alphabetisch, beginnend mit dem Buchstaben C, ohne dabei die Konfiguration im Windows-Setup zu berücksichtigen. Diese Konfiguration kann basierend auf das Vorhandensein von verschiedenen Laufwerken ändern, wie USB-Laufwerke.

2.  Optional: Leistungssteigerung für die abbilderfassung durch Festlegen des Power Schemas auf hohe Leistung:

    ``` syntax
    powercfg /s 8c5e7fda-e8bf-4a96-9a85-a6e23a8c635c
    ```

3.  Wenden Sie das Abbild auf die Windows-Partition:

    ``` syntax
    dism /Apply-Image /ImageFile:D:\install.wim /Index:1 /ApplyDir:W:\
    ```

    Dabei ist W: die Windows-Partition.

4.  Konfigurieren der Systempartition mithilfe des BCDBoot-Tools. Dieses Tool kopiert und Partition Systemdateien mithilfe von Dateien aus der Windows-Partition konfiguriert. Beispiel:

    ``` syntax
    W:\Windows\System32\bcdboot W:\Windows /s S:
    ```

5.  Kopieren Sie die Tools Windows Recovery Environment (RE) in die Wiederherstellung Tools Partition aus.

    ``` syntax
    md R:\Recovery\WindowsRE
    copy C:\Windows\System32\Recovery\winre.wim R:\Recovery\WindowsRE\winre.wim
    ```

    R: ist, auf dem der Wiederherstellungspartition

6.  Registrieren Sie den Speicherort der Tools WindowsRE mithilfe von REAgentC.

    ``` syntax
    W:\Windows\System32\reagentc /setreimage /path R:\Recovery\WindowsRE /target W:\Windows
    ```

**Wenden Sie das Abbild mithilfe eines Skripts**

1.  Voraussetzung: Erstellen Sie DiskPart-Skripts zum Bereitstellen von Bildern. Beispiele zu erhalten: [CreatePartitions UEFI.txt](configure-uefigpt-based-hard-drive-partitions.md) oder [CreatePartitions BIOS.txt](configure-biosmbr-based-hard-drive-partitions.md).

2.  Kopieren Sie das folgende Skript in Notepad ein, und speichern Sie dann die Datei als ApplyImage.bat:

    ``` syntax
    rem == ApplyImage.bat ==

    rem == These commands deploy a specified Windows
    rem    image file to the Windows partition, and configure
    rem    the system partition.

    rem    Usage:   ApplyImage WimFileName 
    rem    Example: ApplyImage E:\Images\ThinImage.wim ==

    rem == Set high-performance power scheme to speed deployment ==
    call powercfg /s 8c5e7fda-e8bf-4a96-9a85-a6e23a8c635c

    rem == Apply the image to the Windows partition ==
    dism /Apply-Image /ImageFile:%1 /Index:1 /ApplyDir:W:\

    rem == Copy boot files to the System partition ==
    W:\Windows\System32\bcdboot W:\Windows /s S:

    :rem == Copy the Windows RE image to the
    :rem    Windows RE Tools partition ==
    md R:\Recovery\WindowsRE
    xcopy /h W:\Windows\System32\Recovery\Winre.wim R:\Recovery\WindowsRE\

    :rem == Register the location of the recovery tools ==
    W:\Windows\System32\Reagentc /Setreimage /Path R:\Recovery\WindowsRE /Target W:\Windows

    :rem == Verify the configuration status of the images. ==
    W:\Windows\System32\Reagentc /Info /Target W:\Windows
    ```

3.  Führen Sie auf dem Zielcomputer der Diskpart und ApplyImage Skripts zum wenden Sie das Abbild auf dem Computer, und richten Sie das System, Windows und Recovery Partitionen. Beispiel:

    ``` syntax
    diskpart /s D:\CreatePartitions-UEFI.txt
    ApplyImage E:\Images\ThinImage.wim
    ```

    wobei D:\\Bilder\\ThinImage.wim ist der Name der Windows-Bilddatei.

    **Hinweis**  Wenn Sie der Befehl DISM /Apply-Image ein Fehler auftritt, stellen Sie sicher, dass Sie eine [unterstützte Version von DISM](dism-supported-platforms.md) für das Windows-Abbild verwenden. Um eine Windows-10-Bild anwenden möchten, benötigen Sie beispielsweise die Windows-10-Version von DISM eingetragenen.

     

**Aufzeichnen und Anwenden von einzelnen Partitionen (nur BIOS-Geräte)**

1.  Auf dem Gerät Verweis alle Partitionen einzeln über DISM /Capture-Image erfassen und anwenden auf die Ziel-Geräte mit DISM /Apply-Image.

    Dieser Methode können Sie die Flexibilität Ihrer Systempartition einrichten. Beachten Sie für UEFI-basierte Geräte keine erfassen und die EFI-Systempartition oder GPT anwenden – Sie werden vom Gerät verwaltet.

2.  Verwenden Sie den Befehl BCDBoot zum Einrichten der Systempartition an.

    ``` syntax
    bcdboot C:\Windows
    ```

**Aufzeichnen und das gesamte Laufwerk anwenden**

-   Das vollständige Flash Update (FFU)-Dateiformat können zum Erfassen und anwenden das gesamte Laufwerk. Finden Sie weitere Informationen finden Sie unter [Bereitstellen von Windows verwenden vollständige Flash Update (FFU)](deploy-windows-using-full-flash-update--ffu.md).

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Konfigurieren von Partitionen UEFI, GPT-basierten Festplatte](configure-uefigpt-based-hard-drive-partitions.md)

[Konfigurieren Sie Festplatte BIOS/MBR-basierte Partitionen](configure-biosmbr-based-hard-drive-partitions.md)

[BCDboot Befehlszeilenoptionen](bcdboot-command-line-options-techref-di.md)

[REAgentC Befehlszeilenoptionen](reagentc-command-line-options.md)

 

 






