---
author: Justinha
Description: 'Windows-Setup: Installieren, verwenden Sie die MBR oder GPT-partition'
ms.assetid: d8d8901f-9e0c-4f73-b331-8c0d36a1ba47
MSHAttr: PreferredLib:/library/windows/hardware
title: 'Windows-Setup: Installieren, verwenden Sie die MBR oder GPT-partition'
ms.openlocfilehash: 318a0085ba860c588fbd48712f6d7e186ee51d3d
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="windows-setup-installing-using-the-mbr-or-gpt-partition-style"></a>Windows-Setup: Installieren, verwenden Sie die MBR oder GPT-partition


Beim Installieren von Windows auf UEFI-basierten PCs mithilfe von Windows Setup muss Festplatte Partitionsstil eingerichtet werden, zur Unterstützung von UEFI-Modus oder älteren BIOS-Kompatibilitätsmodus.

Beispielsweise, wenn die Fehlermeldung angezeigt: "Windows kann nicht auf den Datenträger installiert werden. Der ausgewählte Datenträger ist nicht der GPT-Partition Formatvorlage"aus, der PC im UEFI Modus gestartet wird, aber die Festplatte ist nicht für UEFI-Modus konfiguriert. Haben Sie einige Optionen:

1.  Neustart des Rechners in älteren BIOS-Kompatibilitätsmodus. Dieser Option können Sie die vorhandene Partition Formatvorlage übernehmen. Weitere Informationen finden Sie unter [Starten UEFI oder Legacy-BIOS-Modus](boot-to-uefi-mode-or-legacy-bios-mode.md).

2.  Formatieren Sie das Laufwerk für UEFI mithilfe von GPT-Partition Formatvorlage. Diese Option können Sie den PC UEFI Firmware-Features verwenden.

    Sie können selbst unter Formatieren des Laufwerks mithilfe der folgenden Schritte ausführen oder wenn Sie die Daten aufbewahren müssen, verwenden ein Drittanbieter-Dienstprogramm zum Konvertieren des Laufwerks in GPT-Format.

## <a name="span-idwhyshouldiconvertmydrivespanspan-idwhyshouldiconvertmydrivespanspan-idwhyshouldiconvertmydrivespanwhy-should-i-convert-my-drive"></a><span id="Why_should_I_convert_my_drive_"></span><span id="why_should_i_convert_my_drive_"></span><span id="WHY_SHOULD_I_CONVERT_MY_DRIVE_"></span>Warum sollte ich mein Laufwerk umwandeln?


Viele PCs enthalten jetzt die Möglichkeit, die UEFI Version des BIOS verwenden, das beim Starten und Herunterfahren Zeiten beschleunigen können und zusätzliche Sicherheitsvorteile bieten können. Um Ihren PC im UEFI-Modus zu starten, müssen Sie ein Laufwerk mit GPT-Laufwerksformat formatiert verwenden.

Viele PCs können UEFI verwenden, aber die einschließen ein Kompatibilität Support-Modul (CSM), das die ältere Version des BIOS verwenden festgelegt ist. Diese BIOS-Version wurde der 1970s entwickelt und bietet Kompatibilität für eine Vielzahl von älteren Geräte und Netzwerkkonfigurationen und erfordert ein Laufwerk, das das MBR Laufwerk-Format verwendet wird.

Allerdings unterstützt das grundlegende MBR Laufwerksformat nicht mehr als 4 TB Laufwerke. Es ist außerdem schwierig, um mehr als vier Partitionen einzurichten. Laufwerk GPT-Format können Sie die Festplatten, die größer als 4 TB (Terabyte) sind und ermöglicht, den, die Sie einrichten auf einfache Weise nach Bedarf beliebig viele Partitionen, einrichten.

## <a name="span-idreformattingthedriveusingadifferentpartitionstylespanspan-idreformattingthedriveusingadifferentpartitionstylespanspan-idreformattingthedriveusingadifferentpartitionstylespanreformatting-the-drive-using-a-different-partition-style"></a><span id="Reformatting_the_drive_using_a_different_partition_style"></span><span id="reformatting_the_drive_using_a_different_partition_style"></span><span id="REFORMATTING_THE_DRIVE_USING_A_DIFFERENT_PARTITION_STYLE"></span>Das Laufwerk, verwenden Sie eine andere Partition formatieren


**Wischen und konvertieren Sie das Laufwerk mithilfe von Windows Setup**

1.  Den PC schalten Sie aus, und platzieren Sie in der Windows-Installation DVD oder USB-Taste.

2.  Starten Sie den PC-DVD oder USB-Taste im UEFI-Modus. Weitere Informationen finden Sie unter [Starten UEFI oder Legacy-BIOS-Modus](boot-to-uefi-mode-or-legacy-bios-mode.md).

3.  Wenn Sie eine Installationsart auswählen, wählen Sie **Benutzerdefiniert**.

4.  Klicken Sie auf die **Wo möchten Sie Windows installieren?** Bildschirm, wählen Sie alle Partitionen auf dem Laufwerk, und wählen Sie **Löschen**aus. Das Laufwerk zeigt einen einzelnen Bereich Speicherplatz.

5.  Wählen Sie den freien Speicherplatz, und klicken Sie auf **Weiter**. Windows erkennt, dass der PC-Option UEFI-Modus gestartet wurde und das Laufwerk mit dem GPT-Laufwerk-Format formatiert und beginnt mit der Installation.

**Manuell Wischen ein Laufwerk und in GPT konvertieren:**

1.  Deaktivieren Sie den PC, und platzieren Sie in der Windows-Installation DVD oder USB-Taste.

2.  Starten Sie den PC-DVD oder USB-Taste im UEFI-Modus. Weitere Informationen finden Sie unter [Starten Sie UEFI oder Legacy-BIOS-Modus](boot-to-uefi-mode-or-legacy-bios-mode.md).

3.  Innerhalb der Installation von Windows Drücken von **UMSCHALT + F10** , um ein Eingabeaufforderungsfenster zu öffnen.

4.  Öffnen Sie das Diskpart-Tool:

    ``` syntax
    diskpart
    ```

5.  Das Laufwerk neu formatiert zu identifizieren:

    ``` syntax
    list disk
    ```

6.  Wählen Sie das Laufwerk, und formatieren Sie es:

    ``` syntax
    select disk <disk number>
    clean
    convert gpt
    exit
    ```

7.  Schließen Sie das Eingabeaufforderungsfenster.

8.  Fortsetzen Sie die Installation des Windows-Setup.

    Wenn Sie eine Installationsart auswählen, wählen Sie **Benutzerdefiniert**. Das Laufwerk wird als einen einzelnen Bereich Speicherplatz angezeigt.

    Wählen Sie den freien Speicherplatz, und klicken Sie auf **Weiter**. Windows beginnt mit der Installation.

## <a name="span-idmakesurewindowssetupbootstothecorrectfirmwaremodespanspan-idmakesurewindowssetupbootstothecorrectfirmwaremodespanspan-idmakesurewindowssetupbootstothecorrectfirmwaremodespanmake-sure-windows-setup-boots-to-the-correct-firmware-mode"></a><span id="Make_sure_Windows_Setup_boots_to_the_correct_firmware_mode"></span><span id="make_sure_windows_setup_boots_to_the_correct_firmware_mode"></span><span id="MAKE_SURE_WINDOWS_SETUP_BOOTS_TO_THE_CORRECT_FIRMWARE_MODE"></span>Stellen Sie sicher, dass die richtige Firmware Modus Windows Setup gestartet


Wenn dieser Prozess automatisieren möchten, müssen Sie Windows Setup über Windows PE ausgeführt, und verwenden Sie ein Skript zum Erkennen von welchen Modus Sie gerade arbeiten, vor der Installation von Windows. Weitere Informationen finden Sie unter [Windows PE: Boot in UEFI oder BIOS-Legacymodus](winpe-boot-in-uefi-or-legacy-bios-mode.md).

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Starten Sie UEFI-Modus oder Legacy-BIOS-Modus](boot-to-uefi-mode-or-legacy-bios-mode.md)

 

 






