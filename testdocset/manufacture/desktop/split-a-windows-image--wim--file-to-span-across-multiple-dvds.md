---
author: Justinha
Description: "Aufteilen einer Windows-Bilddatei (WIM), die über mehrere DVDs erstrecken"
ms.assetid: 3861fd65-4c2b-4955-a0af-233e0bbce454
MSHAttr: PreferredLib:/library/windows/hardware
title: "Aufteilen einer Windows-Bilddatei (WIM), die über mehrere DVDs erstrecken"
ms.openlocfilehash: 1c9f206fdcf6e8e7928da9c79b4c4795aaa50403
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="split-a-windows-image-file-wim-to-span-across-multiple-dvds"></a>Aufteilen einer Windows-Bilddatei (WIM), die über mehrere DVDs erstrecken


Geteilte WIM Dateien in SVM-Dateien für DVDs oder FAT32-Dateisystem. Verwenden Sie dieses Verfahren, wenn die aufgeteilten SVM-Dateien nicht in einem einzelnen Medium, wie diesen Fällen in passen:

-   Bereitstellen von Windows mithilfe von DVDs. (Standard einseitig DVD speichert 4.7 GB).
-   Bereitstellen des Windows-Abbilds aus einem Windows PE USB-Schlüssel. (Die Standardinstallation von Windows PE verwendet FAT32-Dateisystem, das eine maximale Größe von 4 GB hat.) Weitere Informationen finden Sie unter [Windows PE: Store oder Teilen Bilder zum Bereitstellen von Windows mit einem USB-Schlüssel](winpe--use-a-single-usb-key-for-winpe-and-a-wim-file---wim.md).

Hinweis: Split WIMs werden von DISM /Apply-Image unterstützt hingegen werden in der Windows-10-Version von Windows Setup nicht unterstützt.

Nachdem die Dateien aufgeteilt sind, können Sie sie auf separaten DVDs oder auf USB-Keys kopieren.

Beachten Sie, bevor Sie das Bild anwenden können, Sie müssen zuerst eingefügt aller Split-Dateien in dem Ordner, beispielsweise durch in einen temporären Ordner auf dem Zielcomputer kopieren. Klicken Sie dann mithilfe von DISM das Abbild angewendet wird, während die Angabe des geteilten .swm Dateien Ort und Dateiname Musters. DISM unterstützt nicht die Dateien von separaten Ordner oder DVDs anwenden.

In der Standardeinstellung erstellt diese Option neue geteilte WIM-Dateien mit der Erweiterung .swm an. Der Dateiname der ersten basiert auf dem angegebenen Dateinamen und die folgenden Dateien eine Zahl nach dem empfängt. Wenn Sie "Install.wim" Teilen, werden die standardmäßigen Dateinamen beispielsweise "Install.swm", "Install2.swm", "Install3.swm" und So weiter.

**Wichtige**  
-   Windows Setup unterstützt nicht aus einer geteilten SVM-Datei für Windows 10 installieren.
-   Sie können eine aufgeteilte SVM-Datei nicht ändern.

 

## <a name="span-idscenariodeploywindowsusingdvdsspanspan-idscenariodeploywindowsusingdvdsspanspan-idscenariodeploywindowsusingdvdsspanscenario-deploy-windows-using-dvds"></a><span id="Scenario__Deploy_Windows_using_DVDs"></span><span id="scenario__deploy_windows_using_dvds"></span><span id="SCENARIO__DEPLOY_WINDOWS_USING_DVDS"></span>Szenario: Bereitstellen von Windows mithilfe von DVDs


1.  Öffnen Sie auf Ihrem PC Techniker, **Bereitstellung und Imaging Tools Umgebung** als Administrator.
2.  Das Windows-Abbild aufgeteilt:

    ``` syntax
    Dism /Split-Image /ImageFile:C:\images\install.wim /SWMFile:C:\images\install.swm /FileSize:4700
    ```

    Dabei gilt:

    -   `C:\images\install.wim`ist der Name und des Speicherorts der Bilddatei an, die aufgeteilt werden soll.

    -   `C:\images\install.swm`ist der Name des Ziels und den Speicherort für die aufgeteilten .swm Dateien.

    -   `4700`ist die maximale Größe in MB für jede der geteilten SVM-Dateien erstellt werden soll.

    In diesem Beispiel wird die *Option/Teilen* erstellt, Install.swm.swm, Install.swm2.swm, eine install3.swm Datei und usw., in das Laufwerk C:\\Verzeichnis Images.

3.  Kopieren Sie die Dateien auf einzelne DVDs. Fügen Sie beispielsweise den ersten DVD und Typ:
    ```
    copy C:\images\install.swm D:\*
    ```

    Fügen Sie dann die zweite DVD, und geben:
    ```
    copy C:\images\install2.swm D:\*
    ```

    Und so weiter, bis alle SVM-Dateien auf DVDs kopiert werden.
4.  Starten Sie dem Zielcomputer zu Windows Vorinstallation Environment (Windows PE). Weitere Informationen finden Sie unter [Windows PE: Erstellen einer Start-CD, DVD, ISO oder VHD](winpe-create-a-boot-cd-dvd-iso-or-vhd.md).
5.  Konfigurieren und Formatieren von Partitionen Festplatte, siehe [Erfassung und Anwenden von Windows, System, und Recovery-Partitionen](capture-and-apply-windows-system-and-recovery-partitions.md).
6.  Kopieren Sie die Dateien in einem einzelnen temporären Ordner. Fügen Sie beispielsweise den ersten DVD und den Typ:
    ```
    md C:\temp
    copy d:\install.swm c:\TempDVDFolder\*
    ```

    Fügen Sie dann die zweite DVD, und geben:
    ```
    copy d:\install2.swm c:\TempDVDFolder\*
    ```

    Und So weiter, bis alle .swm kopiert werden.
7.  Gelten Sie das Bild mit der Option DISM /Apply-image /swmfile:
    ```
    Dism /apply-image /imagefile:c:\temp\install.swm /swmfile:c:\temp\install*.swm /index:1 /applydir:D:\
    ```

8.  Temp-Ordner zu entfernen:
    ```
    rd c:\TempDVDFolder /s /q
    ```

9.  Richten Sie den Partitionen bis auf System und Wiederherstellung auf, siehe [Erfassung und Anwenden von Windows, System, und Recovery-Partitionen](capture-and-apply-windows-system-and-recovery-partitions.md).

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Aufzeichnen und Anwenden von Windows, System und Recovery Partitionen](capture-and-apply-windows-system-and-recovery-partitions.md)

[Windows PE: Verwenden Sie einen einzelnen USB-Schlüssel für Windows PE und einer WIM-Datei (WIM)](winpe--use-a-single-usb-key-for-winpe-and-a-wim-file---wim.md)

[DISM Bild Management-Befehlszeilenoptionen](dism-image-management-command-line-options-s14.md)

 

 






