---
author: Justinha
Description: Erfassen von Bildern mithilfe von DISM Festplatte Partitionen
ms.assetid: 164b9185-402f-4afb-bcf5-ef2f37077ed6
MSHAttr: PreferredLib:/library/windows/hardware
title: Erfassen von Bildern mithilfe von DISM Festplatte Partitionen
ms.openlocfilehash: de61537a6793328daa2dddc0a68e005db6aa8aa9
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="capture-images-of-hard-disk-partitions-using-dism"></a>Erfassen von Bildern mithilfe von DISM Festplatte Partitionen


Das Tool Deployment Image Servicing and Management (DISM) können Sie ein Abbild der Festplatte für die Bereitstellung, und speichern Sie es als Windows® WIM-Datei. Informationen wie Windows, System und Recovery Partitionen gelten, finden Sie unter [Capture und Windows anwenden, System, und Recovery Partitionen](capture-and-apply-windows-system-and-recovery-partitions.md).

## <a name="span-idprerequisitesspanspan-idprerequisitesspanspan-idprerequisitesspanprerequisites"></a><span id="Prerequisites"></span><span id="prerequisites"></span><span id="PREREQUISITES"></span>Erforderliche Komponenten


1.  Windows PE. Finden Sie unter [Windows PE: Erstellen von startbaren USB-Laufwerk](winpe-create-usb-bootable-drive.md).

2.  Referenz-Computer. Referenz-Computer können durch Windows bereitstellen und dann die computerspezifischen Informationen aus dem System entfernen. Weitere Informationen finden Sie unter [Sysprep (verallgemeinern) einer Windows-Installation](sysprep--generalize--a-windows-installation.md).

## <a name="span-idstep1determiningwhichpartitionstocapturespanspan-idstep1determiningwhichpartitionstocapturespanspan-idstep1determiningwhichpartitionstocapturespanstep-1-determining-which-partitions-to-capture"></a><span id="Step_1__Determining_Which_Partitions_to_Capture"></span><span id="step_1__determining_which_partitions_to_capture"></span><span id="STEP_1__DETERMINING_WHICH_PARTITIONS_TO_CAPTURE"></span>Schritt 1: Ermitteln, die zum Capture-Partitionen


Diese Tabelle zeigt die Typen von Partitionen, die Sie aufzeichnen müssen und welche automatisch verwaltet werden.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Partitionstyp</th>
<th align="left">Sollten Sie diese Partition erfassen?</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><strong>Systempartition</strong> (BIOS-Systempartition oder EFI-Systempartition)</p></td>
<td align="left"><p>Optional</p>
<p>Wenn nur eine Reihe einfache Partitionsdateien erforderlich ist, müssen Sie diese Partition erfassen.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>Microsoft Reserved Partition (MSR)</strong></p></td>
<td align="left"><p>Nein.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>Primäre Partitionen</strong> (Windows-Partitionen, Dienstprogrammpartitionen)</p></td>
<td align="left"><p>Ja.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>Erweiterte partition</strong></p></td>
<td align="left"><p>Nein.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>Logische Partitionen</strong> (Windows-Partitionen, Dienstprogrammpartitionen)</p></td>
<td align="left"><p>Ja.</p></td>
</tr>
</tbody>
</table>

 

Sie können erfassen und Bilder zwischen Partitionen auf BIOS-basierten und UEFI-basierten Computer angewendet werden, da das Windows-Abbild von der Firmware betroffen ist nicht. Weitere Informationen finden Sie unter [Erfassung und Anwenden von Windows, System, und Recovery Partitionen](capture-and-apply-windows-system-and-recovery-partitions.md).

## <a name="span-idstep2assigndriveletterstopartitionsspanspan-idstep2assigndriveletterstopartitionsspanspan-idstep2assigndriveletterstopartitionsspanstep-2-assign-drive-letters-to-partitions"></a><span id="Step_2__Assign_Drive_Letters_to_Partitions"></span><span id="step_2__assign_drive_letters_to_partitions"></span><span id="STEP_2__ASSIGN_DRIVE_LETTERS_TO_PARTITIONS"></span>Schritt 2: Partitionen Laufwerkbuchstaben zuweisen


Wenn keines der Partitionen, die Sie erfassen möchten nicht bereits einen Laufwerkbuchstaben zugewiesen haben, weisen Sie einen Brief mithilfe des **DiskPart** -Tools.

1.  Referenz-Computer mit Windows PE zu starten.

2.  Geben Sie an der Befehlszeile Windows PE `diskpart` DiskPart-Tool zu öffnen.

    ``` syntax
    X:> diskpart
    DISKPART>
    ```

3.  Wählen Sie die Festplatte mit der `select disk` Befehl. Beispielsweise

    ``` syntax
    DISKPART> select disk 0
    ```

4.  Zeigen Sie die Partitionen mit den `list partition` Befehl. Beispielsweise

    ``` syntax
    DISKPART> list partition

    DISKPART> list partition

      Partition ###  Type              Size     Offset
      -------------  ----------------  -------  -------
      Partition 1    Primary            300 MB  1024 KB
      Partition 2    Primary            200 GB   301 MB
    ```

5.  Wählen Sie die Partition mit der `select partition` Befehl. Beispielsweise

    ``` syntax
    DISKPART> select partition=1
    ```

6.  Weisen Sie der Partition mit einen Buchstaben der `assign letter` Befehl. Beispielsweise

    ``` syntax
    DISKPART> assign letter=S
    ```

7.  Typ `exit` an der Eingabeaufforderung Windows PE zurückgegeben.

    ``` syntax
    DISKPART> exit
    X:\>
    ```

Weitere Informationen finden Sie unter der DiskPart-Hilfe über die Befehlszeile oder [Diskpart Befehlssyntax Zeile](http://go.microsoft.com/fwlink/?LinkId=128458).

## <a name="span-idstep3capturepartitionimagesusingdismspanspan-idstep3capturepartitionimagesusingdismspanspan-idstep3capturepartitionimagesusingdismspanstep-3-capture-partition-images-using-dism"></a><span id="Step_3__Capture_Partition_Images_using_DISM"></span><span id="step_3__capture_partition_images_using_dism"></span><span id="STEP_3__CAPTURE_PARTITION_IMAGES_USING_DISM"></span>Schritt 3: Aufzeichnen von Partition Abbildern mithilfe von DISM


Aufzeichnen von Abbildern für jede angepasste Partition.

-   Erfassen Sie die Bilder mithilfe des Befehls **DISM** zusammen mit der Option **/captureImage** , an der Eingabeaufforderung Windows PE. Beispielsweise

    ``` syntax
    Dism /Capture-Image /ImageFile:c:\my-windows-partition.wim /CaptureDir:C:\ /Name:"My Windows partition"
    Dism /Capture-Image /ImageFile:s:\my-system-partition.wim /CaptureDir:S:\ /Name:"My system partition"
    ```

    Weitere Informationen zur Verwendung des DISM-Tools zum Erfassen eines Abbilds finden Sie unter [DISM Image Management Command-Line Options](dism-image-management-command-line-options-s14.md).

## <a name="span-idstep4saveimagestothenetworkspanspan-idstep4saveimagestothenetworkspanspan-idstep4saveimagestothenetworkspanstep-4-save-images-to-the-network"></a><span id="Step_4__Save_Images_to_the_Network"></span><span id="step_4__save_images_to_the_network"></span><span id="STEP_4__SAVE_IMAGES_TO_THE_NETWORK"></span>Schritt 4: Speichern der Bilder mit dem Netzwerk


Speichern Sie die WIM-Dateien mit dem Netzwerk oder einen anderen sicheren Speicherort.

1.  Verbinden Sie mit Ihrer Verteilung Freigabe ein, mit dem Befehl **net Use** . Beispielsweise

    ``` syntax
    net use n: \\Server\Share
    ```

    Geben Sie bei Aufforderung die Anmeldeinformationen für das Netzwerk.

2.  Kopieren Sie die Partitionen in Ihrer Netzwerkfreigabe. Beispielsweise

    ``` syntax
    md N:\Images\
    copy C:\my-windows-partition.wim N:\Images\
    copy c:\my-system-partition.wim N:\Images\
    ```

## <a name="span-idnextstepsspanspan-idnextstepsspanspan-idnextstepsspannext-steps"></a><span id="Next_Steps"></span><span id="next_steps"></span><span id="NEXT_STEPS"></span>Nächste Schritte


Nachdem das Bild erfasst und gespeichert ist, können Sie folgende Schritte ausführen:

-   Binden Sie es an Ihren Referenzcomputer zur Bearbeitung. Weitere Informationen finden Sie unter [Mount und eine DISM mithilfe eines Windows Bild ändern](mount-and-modify-a-windows-image-using-dism.md).

-   Teilen Sie die Datei in kleinere Dateien. Weitere Informationen finden Sie unter [Split zu Span über mehrere DVDs ein Windows-Abbild (WIM)-Datei](split-a-windows-image--wim--file-to-span-across-multiple-dvds.md).

-   Anwenden der Abbilder auf einem Zielcomputer. Weitere Informationen finden Sie unter [Anwenden von Bildern mithilfe von DISM](apply-images-using-dism.md).

-   Das Bild-Dienst. Weitere Informationen finden Sie unter [Service ein DISM mithilfe eines Windows Bild](service-a-windows-image-using-dism.md).

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Deployment Image Servicing and Management (DISM) Befehlszeilenoptionen](deployment-image-servicing-and-management--dism--command-line-options.md)

[BCDboot Befehlszeilenoptionen](bcdboot-command-line-options-techref-di.md)

[Aufzeichnen und Anwenden von Windows, System und Recovery Partitionen](capture-and-apply-windows-system-and-recovery-partitions.md)

[Starten Sie VHD (systemeigenem Start): Hinzufügen einer virtuellen Festplatte zum Startmenü](boot-to-vhd--native-boot--add-a-virtual-hard-disk-to-the-boot-menu.md)

 

 






