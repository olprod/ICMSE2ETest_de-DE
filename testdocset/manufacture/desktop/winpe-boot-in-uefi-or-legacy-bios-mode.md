---
author: Justinha
Description: 'Windows PE: Boot in UEFI oder BIOS-Legacymodus'
ms.assetid: bc3c4d41-c4f7-4432-b11a-f409e171d60d
MSHAttr: PreferredLib:/library/windows/hardware
title: 'Windows PE: Boot in UEFI oder BIOS-Legacymodus'
ms.openlocfilehash: bc26e1e6c128737bdff873fa13447e2a36bca079
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="winpe-boot-in-uefi-or-legacy-bios-mode"></a>Windows PE: Boot in UEFI oder BIOS-Legacymodus


Wenn Sie Windows PE auf einem PC UEFI starten, müssen Sie überprüfen, ob der PC-Option in UEFI-Modus oder älteren BIOS-Kompatibilitätsmodus gestartet wird.

Beispielsweise erfordert das Ausführen von Windows Setup über Windows PE Sie werden in den richtigen Firmware-Modus.

Für zahlreiche Vorgänge, wie das Anwenden von Windows-Bildern mithilfe von Diskpart und DISM kann der Firmware-Modus keinen Unterschied machen.

**Starten Sie UEFI Modus**

-   Beim Starten des PCs-Option benötigten manuell auswählen die Startdateien UEFI: \\EFI\\BOOT\\BOOTX64. EFI.

    1.  Starten Sie den PC, und drücken Sie die Taste, um die Menüs Firmware zu speichern (Beispiele: Esc, F2, F9, F12).

    2.  Suchen Sie nach einer Option Firmware wählen Sie die Bootdatei (Beispiele: Starten Sie die Datei unter dem Namen Boot EFI-Datei).

    3.  Wählen Sie die Datei aus dem USB-Laufwerk: `\EFI\BOOT\BOOTX64.EFI`.

**Erkennen Sie, ob Windows PE im Modus für das BIOS oder UEFI gestartet wurde**

1.  Überprüfen der **HKLM\\System\\CurrentControlSet\\Steuerelement\\PEFirmwareType** Registrierungswert, um festzustellen, ob der PC-Option UEFI oder BIOS-Modus gestartet wird. Hinweis: müssen Sie möglicherweise ausführen `wpeutil UpdateBootInfo` um sicherzustellen, dass dieser Wert vorhanden ist.

    ``` syntax
    reg query HKLM\System\CurrentControlSet\Control /v PEFirmwareType
    ```

    Dieser Befehl gibt 0 x 1, wenn der PC-Option in BIOS-Modus oder 0 x 2 gestartet wird, wenn der PC im UEFI-Modus gestartet wird.

    Beispielskript:

    ``` syntax
    wpeutil UpdateBootInfo
    for /f "tokens=2* delims=    " %%A in ('reg query HKLM\System\CurrentControlSet\Control /v PEFirmwareType') DO SET Firmware=%%B
    :: Note: delims is a TAB followed by a space.
    if %Firmware%==0x1 echo The PC is booted in BIOS mode.
    if %Firmware%==0x2 echo The PC is booted in UEFI mode.
    ```

2.  Wenn dies häufig ein Problem aufgetreten ist, können Sie die Startdateien für UEFI oder BIOS-Modus, um zu verhindern, dass den PC starten in den falschen Modus entfernen. Wenn die Firmware PC starten in den falschen Modus eingerichtet ist, wird das Medium sofort fehlschlägt, ermöglicht es Ihnen, sofort wiederholen, Starten des PCs-Option in den richtigen Modus.

    -   **Im Modus UEFI Boot**: um zu verhindern, dass Windows PE starten im BIOS-Modus, entfernen Sie die **Bootmgr** -Datei im Stammverzeichnis des Mediums.

    -   **Boot im BIOS-Modus**: um zu verhindern, dass Windows PE starten im Modus UEFI, **Efi** -Ordner im Stamm des Mediums entfernen.

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Windows PE für Windows 10](winpe-intro.md)

[Windows-Setup: Installieren, verwenden Sie die MBR oder GPT-partition](windows-setup-installing-using-the-mbr-or-gpt-partition-style.md)

[Command-Line Options Wpeutil](wpeutil-command-line-options.md)

[UEFI-Firmware](uefi-firmware.md)

 

 






