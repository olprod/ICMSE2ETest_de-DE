---
author: Justinha
Description: Starten Sie UEFI-Modus oder Legacy-BIOS-Modus
ms.assetid: 04ad6b97-b41d-40fd-88a7-d63d4722c336
MSHAttr: PreferredLib:/library/windows/hardware
title: Starten Sie UEFI-Modus oder Legacy-BIOS-Modus
ms.openlocfilehash: a574e00054ceb2017cc6af10d22c065ac858669b
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="boot-to-uefi-mode-or-legacy-bios-mode"></a>Starten Sie UEFI-Modus oder Legacy-BIOS-Modus


Starten Sie in UEFI-Modus oder älteren BIOS-Kompatibilitätsmodus beim Installieren von Windows über USB, DVD oder Speicherort im Netzwerk.

Wenn Sie über den falschen Modus Windows installieren, werden Sie kann nicht auf die Features von diesem Firmware-Modus verwenden, ohne das Laufwerk formatieren zu.

**Wählen Sie den Firmware-Modus beim Systemstart**

1.  Starten Sie den PC. Die Firmware startet, drücken Sie die Taste, die das Boot-Gerät im Menü geöffnet wird. Beispielsweise Drücken der ESC-Taste, F2, F9, F12 oder anderen Schlüssel geben Sie die Firmware oder Boot-Menüs.

2.  Aktivieren Sie auf das Startmenü Gerät des Befehls, der den Firmware-Modus und das Gerät identifiziert. Wählen Sie zum Beispiel **UEFI USB-Laufwerk** oder im **Netzwerk - BIOS**.

    **Hinweis**  
    Möglicherweise werden separate Befehle für dasselbe Gerät angezeigt. Sie können beispielsweise **UEFI USB-Laufwerk** und **BIOS ein USB-Laufwerk**sehen. Jeder Befehl verwendet den gleichen Geräte- und Medien, aber startet den PC in eine andere Firmware-Modus.

     

    Wenn die Option ein Boot-Gerät für das Gerät nicht angezeigt wird:

    -   Überprüfen Sie die Optionen in den Menüs Firmware zum Aktivieren oder Deaktivieren der BIOS-Kompatibilitätsmodus.

    -   Um BIOS-Kompatibilitätsmodus verwenden möchten, aktivieren Sie für die Optionen in den Menüs Firmware UEFI SecureBoot Features deaktivieren.

    -   Ältere PCs (Windows® 7 Zeitraum oder früher), finden Sie Optionen, um **aus der Datei**, und navigieren Sie zu der \\EFI\\BOOT\\BOOTX64. Auf diesem Gerät EFI-Datei.

**Verwenden Sie eine der folgenden Methoden verwenden, um sicherzustellen, dass Windows installiert ist, mit dem richtigen Firmware-Modus**

1.  Wenn Sie Windows mithilfe von Windows Setup oder der Windows-Installations-DVD installieren, verwenden Sie vorformatierten Festplatte auf Ihre Anlaufstelle PCs. Verwenden Sie das GPT-Dateiformat für UEFI-Modus oder im MBR-Dateiformat für BIOS-Modus. Wenn Windows Setup ausgeführt wird, wenn der PC-Option auf den falschen Modus gestartet wird, wird Windows nicht installiert. Weitere Informationen finden Sie unter [Windows Setup: Installieren von MBR- oder GPT-Formatvorlage partitionieren](windows-setup-installing-using-the-mbr-or-gpt-partition-style.md).

2.  Sie können die Startdateien UEFI oder BIOS aus Windows PE oder Windows Setup entfernen. Wenn Sie nur Startdateien für UEFI-Modus klicken Sie auf der Windows-Installations-DVD enthalten und während der Herstellung Sie versehentlich versuchen, den PC im BIOS-Modus zu starten, beispielsweise der PC fehl sofort zu starten, und können Sie mit der Problembehandlung sofort beginnen.

    -   **UEFI**: um zu verhindern, dass Windows-Setup oder Windows PE starten im BIOS-Modus, entfernen Sie die **Bootmgr** -Datei im Stammverzeichnis des Mediums.

    -   **BIOS**: um zu verhindern, dass Windows-Setup oder Windows PE starten im Modus UEFI, **Efi** -Ordner im Stamm des Mediums entfernen.

3.  Windows PE können Sie die [Funktion GetFirmwareEnvironmentVariable](http://go.microsoft.com/fwlink/p/?LinkId=698644)überprüfen. Weitere Informationen finden Sie unter [Windows PE: Boot in UEFI oder BIOS-Legacymodus](winpe-boot-in-uefi-or-legacy-bios-mode.md).

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Windows PE: Erstellen von startbaren USB-Laufwerk](winpe-create-usb-bootable-drive.md)

 

 






