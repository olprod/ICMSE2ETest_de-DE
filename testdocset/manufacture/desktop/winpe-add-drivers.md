---
author: Justinha
Description: "Windows PE: Hinzufügen von Treibern"
ms.assetid: 9eecfba3-2a0d-4c38-8cec-6d5e839ae8d4
MSHAttr: PreferredLib:/library/windows/hardware
title: "Windows PE: Hinzufügen von Treibern"
ms.openlocfilehash: 9c6385c5fefa35af6e8fd444e78732da07a0c31c
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="winpe-add-drivers"></a>Windows PE: Hinzufügen von Treibern


Hinzufügen von Treibern zu Windows PE wie Grafiktreiber oder Netzwerk-Treiber.

Gerätetreiber beinhalten in der Regel einen Ordner, der mehrere Dateien enthält. Diese Ordner enthalten, eine Datei mit der `.inf` Dateinamenerweiterung. Dieser Datei werden die anderen Dateien in Gerätetreiberpakets verwaltet. Viele wichtige Treiber können in das Windows-Abbild und in Windows PE verwendet werden.

Sie können außerdem Gerätetreiber aktualisieren, während der Ausführung von Windows PE. Weitere Informationen finden Sie unter [Drvload Command-Line Options](drvload-command-line-options.md).

**Abrufen von Windows Assessment and Deployment Kit mit Windows PE-tools**

-   Installieren Sie [Windows Assessment and Deployment Kit (Windows ADK) technische Referenz](http://go.microsoft.com/fwlink/p/?LinkId=526803), einschließlich des Windows PE-Features.

**Erstellen einer Gruppe von 32-Bit oder 64-Bit-Windows PE-Dateien**

1.  Klicken Sie auf **Start**, und geben Sie die **Bereitstellung**. Mit der rechten Maustaste, **Bereitstellung und Imaging Tools Umgebung** , und wählen Sie dann auf **als Administrator ausführen**.

2.  Kopieren Sie Sie in den **Bereitstellungstools und Imaging-Umgebung**Windows PE-Dateien für die PCs, die Sie starten möchten.

    -   Die 64-Bit-Version kann UEFI 64-Bit- und 64-Bit-BIOS PCs gestartet werden.

        ``` syntax
        copype amd64 C:\WinPE_amd64
        ```

    -   Die 32-Bit-Version kann 32-Bit-UEFI, BIOS-32-Bit- und 64-Bit-BIOS-PCs gestartet werden.

        ``` syntax
        copype x86 C:\WinPE_x86
        ```

**Stellen Sie das Windows PE Boot-Abbild**

-   Stellen Sie das Windows PE-Abbild.

    ``` syntax
    Dism /Mount-Image /ImageFile:"C:\WinPE_amd64\media\sources\boot.wim" /index:1 /MountDir:"C:\WinPE_amd64\mount"
    ```

## <a name="span-idaddcustomizationsspanspan-idaddcustomizationsspanspan-idaddcustomizationsspanadd-customizations"></a><span id="Add_customizations"></span><span id="add_customizations"></span><span id="ADD_CUSTOMIZATIONS"></span>Hinzufügen von Anpassungen


**Hinzufügen von Gerätetreibern (INF-Dateien)**

1.  Windows PE-Abbild den Gerätetreiber hinzugefügt.

    ``` syntax
    Dism /Add-Driver /Image:"C:\WinPE_amd64\mount" /Driver:"C:\SampleDriver\driver.inf"
    ```

    **Hinweis**  
    Obwohl Sie mehrere Treiber zu einem Bild mit einem einzigen Befehl hinzufügen können, ist es oft einfacher zur Behandlung von Problemen durch jedes Paket einzeln hinzufügen.

     

2.  Stellen Sie sicher, dass der Treiberpakete Teil des Bilds sind:

    ``` syntax
    Dism /Get-Drivers /Image:"C:\WinPE_amd64\mount"
    ```

    Überprüfen der resultierenden Liste der Treiber, und stellen Sie sicher, dass die Liste des Treiberpakets enthält, die Sie hinzugefügt haben.

**Grafikkartentreiber: ändern die Auflösung**

-   Für die meisten Graphics-Treiber wählt Windows PE automatisch die maximale Auflösung.

    Um die Größe manuell anpassen möchten, verwenden Sie eine Antwortdatei und umfassen Einstellungen für Microsoft-Windows-Setup /[Anzeigen](https://msdn.microsoft.com/library/windows/hardware/dn915285). Weitere Informationen finden Sie unter [Wpeinit und Startnet.cmd: Verwenden von Windows PE zum Starten des Skripts](wpeinit-and-startnetcmd-using-winpe-startup-scripts.md).

**Heben Sie die Bereitstellung des Windows PE-Abbilds und Erstellen von Medien**

1.  Hängen Sie das Windows PE-Abbild.

    ``` syntax
    Dism /Unmount-Image /MountDir:"C:\WinPE_amd64\mount" /commit
    ```

2.  Erstellen von startbaren Medien, wie ein USB-Laufwerk.

    ``` syntax
    MakeWinPEMedia /UFD C:\WinPE_amd64 F:
    ```

3.  Die Medien zu starten. Windows PE wird automatisch gestartet. Nachdem das Windows PE-Fenster angezeigt wird, wird der Befehl Wpeinit automatisch ausgeführt. Dies kann einige Minuten dauern. Überprüfen Sie Ihre Anpassungen.

**Problembehandlung**

1.  Windows PE wird nicht gestartet? Finden Sie die Tipps zur Problembehandlung am Ende des Themas: [Installieren von Windows PE](http://go.microsoft.com/fwlink/?LinkId=526830).

2.  Tipps zum Herstellen einer Verbindung mit einem Netzwerk finden Sie unter [Windows PE Netzwerk-Treiber: Initialisieren und Hinzufügen von Treibern](winpe-network-drivers-initializing-and-adding-drivers.md).

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen

[Windows PE: Optimieren der Leistung und das Bild zu reduzieren](winpe-optimize.md)

[Windows PE für Windows 10](winpe-intro.md)

[Installieren von Windows PE](http://go.microsoft.com/fwlink/?LinkId=526830)

[Windows PE: Erstellen von startbaren USB-Laufwerk](winpe-create-usb-bootable-drive.md)

[Windows PE: Erstellen einer Start-CD, DVD, ISO oder virtuelle Festplatte](winpe-create-a-boot-cd-dvd-iso-or-vhd.md)

[Windows PE: Installieren auf einer Festplatte (flach Boot oder nicht-RAM)](winpe-install-on-a-hard-drive--flat-boot-or-non-ram.md)

[Windows PE: Boot in UEFI oder BIOS-Legacymodus](winpe-boot-in-uefi-or-legacy-bios-mode.md)

[Windows PE: Hinzufügen von Paketen (optionalen Komponenten Reference (engl.)](winpe-add-packages--optional-components-reference.md)

 

 






