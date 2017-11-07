---
author: KPacquer
Description: "Windows PE: Speichern oder geteilte Bilder zum Bereitstellen von Windows mit einem USB-Schlüssel"
ms.assetid: 66036c4e-f64c-4175-b4fe-15e4cc1fc600
MSHAttr: PreferredLib:/library/windows/hardware
title: "Windows PE: Speichern oder geteilte Bilder zum Bereitstellen von Windows mit einem USB-Schlüssel"
ms.openlocfilehash: a747d21c165e29690af81b500afc36848a282e0d
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="winpe-store-or-split-images-to-deploy-windows-using-a-single-usb-key"></a>Windows PE: Speichern oder geteilte Bilder zum Bereitstellen von Windows mit einem USB-Schlüssel

Wie können Sie Windows auf PCs mit nur einem USB-Anschluss bereitstellen?

Windows-Vorinstallation-Umgebung (Windows PE) Laufwerk Standardformat FAT32 wird verwendet, um UEFI-basierten PCs starten, aber das ist zu klein, um die meisten Windows Bilder zu speichern:

-   FAT32 hat eine maximale Größe von 4GB Größe. Am häufigsten angepassten Windows Bilder sind mehr als 4GB.
-   FAT32 hat eine maximale Partitionsgröße von 32GB. Einige Windows-Abbilder sind größer als 32GB.

    (Sie können weiterhin einen 64GB oder 128GB USB-Schlüssel verwenden, aber Sie müssen sie zum Formatieren Verwendung nur 32GB seine Speicherplatz verwendet.)

Nachfolgend finden Sie einige Wege zur Umgehung dieser Einschränkungen:

## <a name="span-idoption1storetheimageonaseparateusbdrivespanspan-idoption1storetheimageonaseparateusbdrivespanspan-idoption1storetheimageonaseparateusbdrivespanoption-1-store-the-image-on-a-separate-usb-drive"></a><span id="Option_1__Store_the_image_on_a_separate_USB_drive"></span><span id="option_1__store_the_image_on_a_separate_usb_drive"></span><span id="OPTION_1__STORE_THE_IMAGE_ON_A_SEPARATE_USB_DRIVE"></span>Option 1: Speichern Sie das Abbild auf einem separaten USB-Laufwerk


Auch wenn Ihr PC nur über ein USB-Anschluss verfügt, können Sie weiterhin Windows mithilfe von zwei separaten USB-Schlüssel bereitstellen.

1.  Starten Sie Windows PE.
2.  Entfernen Sie das Windows PE-Laufwerk ein. (Nach dem Starten führt Windows PE im Arbeitsspeicher.)
3.  Schließen Sie ein separater Speichervolumes Laufwerk mit dem Bild, und wenden sie auf das Gerät.

## <a name="span-idoption2storetheimageonanetworklocationspanspan-idoption2storetheimageonanetworklocationspanspan-idoption2storetheimageonanetworklocationspanoption-2-store-the-image-on-a-network-location"></a><span id="Option_2__Store_the_image_on_a_network_location"></span><span id="option_2__store_the_image_on_a_network_location"></span><span id="OPTION_2__STORE_THE_IMAGE_ON_A_NETWORK_LOCATION"></span>Option 2: Speichern Sie das Abbild auf einem Speicherort im Netzwerk


1.  Kopieren Sie das Abbild auf einen Server in Ihrem Netzwerk, beispielsweise \\ \\Server\\freigeben\\install.wim

2.  Starten Sie Windows PE.

3.  Verbinden von einem Netzlaufwerk mit einem Laufwerkbuchstaben, beispielsweise N.

    ``` syntax
    net use N: \\server\share
    ```

4.  Wenden Sie das Abbild aus dem Netzwerk.
    ```
    Dism /apply-image /imagefile:N:\install.wim /index:1 /applydir:D:\
    ```

## <a name="span-idoption3splittheimagespanspan-idoption3splittheimagespanspan-idoption3splittheimagespanoption-3-split-the-image"></a><span id="Option_3__Split_the_image"></span><span id="option_3__split_the_image"></span><span id="OPTION_3__SPLIT_THE_IMAGE"></span>Option 3: Teilen des Abbilds


**Einschränkungen:**

-   Windows-Setup unterstützt keine Installation aus einer geteilten WIM-Datei für Windows 10. eine aufgeteilte WIM-Datei können nicht geändert.
-   Eine aufgeteilte WIM-Datei kann nicht geändert werden.
-   Um einen Schlüssel 64 GB oder 128 GB zu verwenden, format, um nur 32 GB Speicherplatz verwenden.
-   Für Bilder, die größer als 32GB müssten eine zweite Taste USB trotzdem aufgrund der FAT32 Partition Uploaddatei Sie.

1.  Erstellen Sie über Ihre Techniker PC Ihre Windows PE-Taste. Finden Sie unter [Windows PE: Erstellen von startbaren USB-Laufwerk](winpe-create-usb-bootable-drive.md).

2.  Öffnen Sie die **Bereitstellung und Imaging Tools-Umgebung** als Administrator an.

3.  Das Windows-Abbild in Dateien kleiner als 4GB aufgeteilt:

    ``` syntax
    Dism /Split-Image /ImageFile:C:\install.wim /SWMFile:C:\images\install.swm /FileSize:4000
    ```

    Dabei gilt:

    -   `C:\images\install.wim`ist der Name und den Speicherort der Bilddatei an, die Sie teilen möchten.

    -   `D:\images\install.swm`ist der Name des Ziels und der Speicherort für die aufgeteilten WIM-Dateien.

    -   `4000`ist die maximale Größe in MB für jede der geteilten WIM-Dateien erstellt werden soll.

    In diesem Beispiel wird die *Option/Teilen* erstellt, Install.swm.swm Install.swm2.swm, ein install3.swm-Datei und So weiter in Laufwerk D:\\Verzeichnis Images.

4.  Kopieren Sie die Dateien der Windows PE-Taste.

5.  Auf dem Ziel-PC Windows PE starten, und klicken Sie dann ein Bild mit DISM /Apply-Image /SWMFile Befehl anwenden.
    ```
    Dism /apply-image /imagefile:install.swm /swmfile:install*.swm /index:1 /applydir:D:\
    ```

## <a name="span-idcreateamultiplepartitionusbdrivespanoption-4-create-a-multiple-partition-usb-drive-windows-to-go-or-other-storage-drive"></a><span id="Create_a_multiple_partition_USB_drive"></span>Option 4: Erstellen einer mehrere Partition USB-Laufwerk (Windows auf Gehe zu oder andere Speicherlaufwerk)

Am häufigsten flash Laufwerke Bericht selbst als austauschbare Laufwerke, jedoch zum Erstellen von mehreren Partitionen auf einem USB-Laufwerk das Laufwerk muss melden sich selbst als einen festen (nicht-) Wechseldatenträger. Wenn Sie Zugriff auf eine [Windows wechseln (WTG) zertifiziert Laufwerk](http://technet.microsoft.com/library/hh831833.aspx) haben können, Sie, da WTG Bericht als festen Laufwerke. Einige externen USB-Festplatten Berichten auch sich selbst als fest.

**Überprüfen Sie, ob das Laufwerk, sich selbst als festen oder austauschbaren gemeldet wird**

1.  Schließen Sie das Laufwerk.
2.  Maustaste auf Start, und wählen Sie **Disk Management**.
3.  Im linken Bereich auf den unteren Rand des Bildschirms wird das Laufwerk **grundlegende** anstelle von **austauschbares**angenommen.

**Erstellen Sie ein Laufwerk mit mehreren Partitionen**

1.  Starten der **Bereitstellung und Imaging Tools Umgebung** als Administrator an.

2.  Geben Sie **Diskpart** ein, und drücken Sie die EINGABETASTE.

3.  Verwenden Sie Diskpart, um das Laufwerk neu formatiert und zwei neue Partitionen für Windows PE und die Bilder zu erstellen:

    ``` syntax
    List disk
    select disk X    (where X is your USB drive)
    clean
    create partition primary size=2048
    active
    format fs=FAT32 quick label="WinPE"
    assign letter=P
    create partition primary
    format fs=NTFS quick label="Images"
    assign letter=I  
    Exit
    ```

4.  Kopieren Sie die Windows PE-Dateien auf der Partition Windows PE:

    ``` syntax
    copype amd64 C:\WinPE_amd64
    xcopy C:\WinPE_amd64\media P:\ /s
    ```

5.  Kopieren Sie auf die Bilder Partition Windows Bilddatei an:

    ``` syntax
    xcopy C:\Images\install.wim I:\install.wim
    ```

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen

[Windows PE: Identifizieren Sie Laufwerkbuchstaben mithilfe eines Skripts](winpe-identify-drive-letters.md)

[Teilen Sie eine Windows-Abbilddatei (WIM) für Medien FAT32 oder auf mehreren DVDs umfassen](split-a-windows-image--wim--file-to-span-across-multiple-dvds.md)

[DISM Bild Management-Befehlszeilenoptionen](dism-image-management-command-line-options-s14.md)