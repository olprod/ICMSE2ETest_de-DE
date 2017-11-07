---
author: Justinha
Description: 'Windows PE: Erstellen von startbaren USB-Laufwerk'
ms.assetid: 9e7216ed-5a12-4f26-a0cb-da303589c806
MSHAttr: PreferredLib:/library/windows/hardware
title: 'Windows PE: Erstellen von startbaren USB-Laufwerk'
ms.openlocfilehash: 261714b0add0b17dc7a6e4d46447bfae7821cc60
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="winpe-create-usb-bootable-drive"></a>Windows PE: Erstellen von startbaren USB-Laufwerk


Erstellen Sie ein Windows PE (Windows PE) startbaren USB flash-Laufwerk oder eine externe USB-Festplatte.

Die Standardinstallation ausgeführt wird, aus dem Arbeitsspeicher (RAM-Datenträger), damit Sie das Laufwerk während der Ausführung von Windows PE entfernen können.

**Installieren von Windows ADK**

-   Installieren Sie die folgenden Features von [Windows Assessment and Deployment Kit (ADK)](http://go.microsoft.com/fwlink/?LinkId=526803):

    -   **Bereitstellungstools**: **Bereitstellung und Imaging Tools-Umgebung**enthält.

    -   **Windows-Vorinstallation Umgebung** : enthält die Dateien, die zum Installieren von Windows PE verwendet.

**Installieren von Windows PE**

1.  Starten Sie **Bereitstellung und Imaging Tools Umgebung** als **Administrator**an.

2.  Erstellen Sie eine Arbeitskopie von Windows PE-Dateien. Geben Sie entweder X86, amd64 oder arm:

    ``` syntax
    copype amd64 C:\WinPE_amd64
    ```

3.  Installieren Sie Windows PE USB-Laufwerk, der Buchstabe des Laufwerks angeben:

    ``` syntax
    MakeWinPEMedia /UFD C:\WinPE_amd64 F:
    ```

    **Warnung**  
    Dieser Befehl formatiert das Laufwerk.

     

**Starten Sie Windows PE**

1.  Schließen Sie das USB-Gerät an den PC, das Sie bearbeiten möchten.

2.  Aktivieren Sie auf dem PC, und drücken Sie den Schlüssel, der der Firmware Boot Menüs wird geöffnet.

3.  Aktivieren Sie das USB-Laufwerk ein. Windows PE wird automatisch gestartet.

    Nachdem Sie im Befehlsfenster angezeigt wird, die `wpeinit` Befehl ausgeführt wird, die das System richtet. Dies kann einige Minuten dauern.

**Problembehandlung**

1.  Wenn die `copype` Befehl wird nicht erkannt, stellen Sie sicher, Sie haben den Befehl ausführen, von der Bereitstellung und Imaging Tools Umgebung, die Teil von Windows ADK ist.

2.  Wenn Windows PE nicht angezeigt wird, versuchen Sie die folgenden problemumgehungen, Neustart des PCs jedes Mal:

    -   Um einem PC zu starten, die in der Firmware Boot Menüs UEFI Modus unterstützt, versuchen Sie, manuell die Startdateien: \\EFI\\BOOT\\BOOTX64. EFI.

    -   Versuchen Sie es einen anderen USB-Anschluss. Vermeiden Sie die Hubs oder Kabel.

    -   Vermeiden Sie 3.0 USB-Anschlüsse, wenn die Firmware nicht systemeigene Unterstützung für USB-3.0 enthalten.

    -   Bereinigt das USB-Laufwerk und Neuinstallieren von Windows PE. Damit können Sie zusätzliche Boot-Partitionen oder andere Boot-Software entfernen.

        ``` syntax
        diskpart
          list disk
          select disk <disk number>
          clean
          create partition primary
          format quick fs=fat32 label="Windows PE"
          assign letter="F"
          exit

        MakeWinPEMedia /UFD C:\winpe_amd64 F:
        ```

    -   Starten Sie Windows PE von einer DVD. Erstellen Sie eine ISO-Datei, die Sie auf einer DVD brennen können:

        ``` syntax
        MakeWinPEMedia /ISO C:\winpe_amd64 c:\winpe_amd64\winpe.iso
        ```

        Navigieren Sie im Datei-Explorer zu C:\\Windows PE\_amd64 Maustaste **winpe.iso**, und klicken Sie **auf Datenträger brennen**. Führen Sie die aufforderungen, um eine DVD erstellen.

    -   Wenn Ihrem PC Speicher oder Grafiktreiber Start erforderlich sind, versuchen Sie das Windows PE-Abbild dieselben Treiber hinzuzufügen. Weitere Informationen finden Sie unter [Windows PE: Bereitstellen und Anpassen von](winpe-mount-and-customize.md).

    -   Aktualisieren Sie die Firmware des Computers, auf die neueste Version.

3.  Wenn der PC mit Netzwerkadressen nicht verbunden werden, finden Sie unter [Windows PE Netzwerk-Treiber: Initialisieren und Hinzufügen von Treibern](winpe-network-drivers-initializing-and-adding-drivers.md).

**Speichern von Windows-Abbildern auf dem Windows PE-Laufwerk**

1.  In der Regel wird nicht Sie möglicherweise gespeichert oder erfassen Windows-Abbilder auf einem Windows PE USB flash-Laufwerk.

    Die meisten USB-Laufwerke unterstützen nur eine einzigen Laufwerkpartition. Die `MakeWinPEMedia` Befehl formatiert das Laufwerk als FAT32, dem Starten sowohl BIOS-basierten und UEFI-basierten PCs unterstützt. Dieses Dateiformat nur Datei unterstützt bis zu 4 GB Größe.

2.  Für externe USB-Festplatten können Sie eine separate NTFS-Partition erstellen, die größeren Dateiformate verarbeitet werden können:

    ``` syntax
    diskpart
      list disk
      select <disk number>
      clean
      rem === Create the Windows PE partition. ===
      create partition primary size=2000
      format quick fs=fat32 label="Windows PE"
      assign letter=P
      active
      rem === Create a data partition. ===
      create partition primary
      format fs=ntfs quick label="Other files"
      assign letter=O
      list vol
      exit

    MakeWinPEMedia /UFD C:\WinPE_amd64 P:
    ```

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Windows PE für Windows 10](winpe-intro.md)

[Windows PE: Erstellen einer Boot-CD, DVD, ISO oder virtuelle Festplatte](winpe-create-a-boot-cd-dvd-iso-or-vhd.md)

[Windows PE: Installieren auf einer Festplatte (flach Boot oder nicht-RAM)](winpe-install-on-a-hard-drive--flat-boot-or-non-ram.md)

[Windows PE: Bereitstellen und anpassen](winpe-mount-and-customize.md)

[Windows PE: Boot in UEFI oder BIOS-Legacymodus](winpe-boot-in-uefi-or-legacy-bios-mode.md)

[Windows Setup-unterstützte Plattformen und plattformübergreifende Bereitstellungen](windows-setup-supported-platforms-and-cross-platform-deployments.md)

 

 






