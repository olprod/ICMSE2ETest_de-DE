---
author: Justinha
Description: "Fügen Sie ein Volume Image an einem vorhandenen Abbild mithilfe von DISM"
ms.assetid: c537f8bb-05ed-48cd-b75a-a8c1ed3bc66f
MSHAttr: PreferredLib:/library/windows/hardware
title: "Fügen Sie ein Volume Image an einem vorhandenen Abbild mithilfe von DISM"
ms.openlocfilehash: ec7d721ff9a14d5a75c888ec60c5d53012fc6dbc
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="append-a-volume-image-to-an-existing-image-using-dism"></a>Fügen Sie ein Volume Image an ein vorhandenes Bild mithilfe von DISM


Das Tool Deployment Image Servicing and Management (DISM) ist ein Befehlszeilentool, das die Erstellung von Windows® WIM-Dateien für die Bereitstellung in einer Fertigung oder corporate IT-Umgebung ermöglicht. Die Option **/Append-Image** Fügt ein Volume Image an eine vorhandene WIM-Datei ermöglicht es Ihnen, viele angepasste Windows Bilder in einem Bruchteil der Speicherplatz zu speichern. Beim Kombinieren von zwei oder mehr Windows-Abbilddateien in einer einzigen WIM-Datei werden alle Dateien, die zwischen den Bildern dupliziert werden nur einmal gespeichert.

## <a name="span-idmultiplewindowsimagesinawimfilespanspan-idmultiplewindowsimagesinawimfilespanmultiple-windows-images-in-a-wim-file"></a><span id="multiple_windows_images_in_a_.wim_file"></span><span id="MULTIPLE_WINDOWS_IMAGES_IN_A_.WIM_FILE"></span>Mehrere Windows-Abbilder in einer WIM-Datei


Bevor Sie Daten an ein Abbild anhängen können, müssen Sie über Folgendes verfügen:

-   Ein Referenzcomputer unter Windows 8 oder ein Referenzcomputer mit dem Windows Assessment and Deployment Kit (Windows ADK) Tools installiert ist.

-   Ein Windows-Abbilddatei (WIM). Weitere Informationen zum Erfassen eines Abbilds mithilfe von DISM finden Sie unter [Capture Bilder der Festplatte Partitionen mithilfe von DISM](capture-images-of-hard-disk-partitions-using-dism.md).

**Ein Volume Image an ein vorhandenes Bild Anfügen**

1.  Öffnen Sie ein Eingabeaufforderungsfenster mit Administratorrechten. Wenn Sie eine Version von Windows als Windows 8 verwenden, navigieren Sie zu dem Verzeichnis DISM.

2.  Fügen Sie ein Volume Image an ein vorhandenes Bild. Beispielsweise können Sie ein Bild des Laufwerk D an ein vorhandenes Bild aufgerufen eigene Windows-partition.wim anfügen.

    ``` syntax
    Dism /Append-Image /ImageFile:c:\my-windows-partition.wim /CaptureDir:D:\ /Name:Drive-D
    ```

**Nächste Schritte**

1.  Sie können das Bild anwenden, indem Sie darauf verweisenden Bild Nummer oder Image-Name, beispielsweise:

    ``` syntax
    Dism /apply-image /imagefile:install.wim /name:Drive-D /ApplyDir:D:\
    ```

2.  Sie können das Bild in eine separate Datei mit der Option **/Export-Image** extrahieren. Beispiel:

    ``` syntax
    Dism /Export-Image /SourceImageFile:install.wim /SourceName:Drive-D /DestinationImageFile:DriveD.wim
    ```

Weitere Informationen finden Sie unter [DISM Image Management Command-Line Options](dism-image-management-command-line-options-s14.md).

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Erfassen von Bildern mithilfe von DISM Festplatte Partitionen](capture-images-of-hard-disk-partitions-using-dism.md)

[DISM Bild Management-Befehlszeilenoptionen](dism-image-management-command-line-options-s14.md)

 

 






