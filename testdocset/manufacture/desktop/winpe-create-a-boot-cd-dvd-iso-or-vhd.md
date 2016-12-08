---
author: Justinha
Description: 'Windows PE: Erstellen einer Start-CD, DVD, ISO oder virtuelle Festplatte'
ms.assetid: d60de9b6-6775-41e7-bc52-dfafede554df
MSHAttr: PreferredLib:/library/windows/hardware
title: 'Windows PE: Erstellen einer Boot-CD, DVD, ISO oder virtuelle Festplatte'
ms.openlocfilehash: ab7d15abe370e5960efbb7a698dec547bc070205
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="winpe-create-a-boot-cd-dvd-iso-or-vhd"></a>Windows PE: Erstellen einer Start-CD, DVD, ISO oder virtuelle Festplatte


Erstellen ein Windows PE (Windows PE) startbare CD-DVD ISO-Datei oder virtuelle Festplatte (VHD).

Die Standardinstallation aus dem Speicher (auch bekannt als einen RAM-Datenträger), wodurch Sie das USB-Laufwerk zu entfernen, während der Ausführung von Windows PE wird ausgeführt.

**Installieren von Windows ADK**

-   Installieren Sie die folgenden Features von [Windows Assessment and Deployment Kit (ADK)](http://go.microsoft.com/fwlink/p/?LinkID=526803):

    -   **Bereitstellungstools**: **Bereitstellung und Imaging Tools-Umgebung**enthält.

    -   **Windows-Vorinstallation Umgebung** : enthält die Dateien, die zum Installieren von Windows PE verwendet.

**Installieren von Windows PE auf einer DVD, eine CD oder eine ISO-Datei**

1.  Klicken Sie auf **Start**, und geben Sie die **Bereitstellung**. Mit der rechten Maustaste **Bereitstellung und Imaging Tools Umgebung** , und wählen Sie dann auf **als Administrator ausführen**.

2.  Erstellen Sie eine Arbeitskopie von Windows PE-Dateien. Geben Sie X86 oder amd64:

    ``` syntax
    copype amd64 C:\WinPE_amd64
    ```

3.  Erstellen Sie eine ISO-Datei mit Windows PE-Dateien:

    ``` syntax
    MakeWinPEMedia /ISO C:\WinPE_amd64 C:\WinPE_amd64\WinPE_amd64.iso
    ```

4.  Auf einer DVD oder CD brennen: In Windows Explorer mit der rechten Maustaste der ISO-Datei, und wählen Sie **CD-Abbild brennen** &gt; **Brennen**, und befolgen Sie.

## <a name="span-idusinghyper-vspanspan-idusinghyper-vspanspan-idusinghyper-vspanusing-hyper-v"></a><span id="Using_Hyper-V"></span><span id="using_hyper-v"></span><span id="USING_HYPER-V"></span>Verwenden von Hyper-V


Beim Ausführen von Windows PE im Hyper-V erwogen Sie werden, eine ISO-Dateiformat anstelle einer virtuellen Festplatte, um schnell Installation des virtual PC zu aktivieren. Weitere Informationen finden Sie im vorherigen Abschnitt.

**So installieren Sie Windows PE auf einer virtuellen Festplatte**

1.  Erstellen Sie eine virtuelle Festplatte (VHD- oder .vhdx):

    ``` syntax
    diskpart
    create vdisk file="C:\WinPE.vhdx" maximum=1000
    attach vdisk
    create partition primary
    assign letter=V
    format fs=ntfs quick
    exit
    ```

2.  Bereiten Sie das Laufwerk mithilfe von MakeWinPEMedia vor:

    ``` syntax
    MakeWinPEMedia /UFD C:\WinPE_amd64 V:
    ```

3.  Das Laufwerk zu trennen:

    ``` syntax
    diskpart
    select vdisk file="C:\WinPE.vhdx"
    detach vdisk
    exit
    ```

**Problembehandlung**

1.  Wenn Windows PE nicht angezeigt wird, versuchen Sie die folgenden problemumgehungen, Neustart des PCs jedes Mal:

    -   Einen PC zu starten, die UEFI Modus unterstützt: In der Firmware Boot-Menüs, versuchen Sie, manuell die Startdateien: \\EFI\\BOOT\\BOOTX64. EFI.

    -   Wenn Ihrem PC Speicher oder Grafiktreiber Start erforderlich sind, versuchen Sie das Windows PE-Abbild dieselben Treiber hinzuzufügen. Weitere Informationen finden Sie unter [Windows PE: Bereitstellen und Anpassen von](winpe-mount-and-customize.md).

2.  Wenn der PC mit Netzwerkadressen nicht verbunden werden, finden Sie unter [Windows PE Netzwerk-Treiber: Initialisieren und Hinzufügen von Treibern](winpe-network-drivers-initializing-and-adding-drivers.md).

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Windows PE für Windows 10](winpe-intro.md)

[Windows PE: Erstellen von startbaren USB-Laufwerk](winpe-create-usb-bootable-drive.md)

[Windows PE: Installieren auf einer Festplatte (flach Boot oder nicht-RAM)](winpe-install-on-a-hard-drive--flat-boot-or-non-ram.md)

[Windows PE: Bereitstellen und anpassen](winpe-mount-and-customize.md)

[Windows PE: Boot in UEFI oder BIOS-Legacymodus](winpe-boot-in-uefi-or-legacy-bios-mode.md)

[Windows Setup-unterstützte Plattformen und plattformübergreifende Bereitstellungen](windows-setup-supported-platforms-and-cross-platform-deployments.md)

 

 






