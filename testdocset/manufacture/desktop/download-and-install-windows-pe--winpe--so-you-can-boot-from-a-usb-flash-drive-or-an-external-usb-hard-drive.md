---
author: Justinha
Description: Herunterladen und Installieren von Windows PE (Windows PE), damit Sie von einem USB-Laufwerk oder eine externe USB-Festplatte gestartet werden kann
ms.assetid: 1799a91f-493a-4509-9937-ad6901358240
MSHAttr: PreferredLib:/library/windows/hardware
title: Herunterladen und Installieren von Windows PE (Windows PE), damit Sie von einem USB-Laufwerk oder eine externe USB-Festplatte gestartet werden kann
ms.openlocfilehash: 11ebcb0129e47f1f81e92eda49bb5b8119783c0e
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="download-and-install-windows-pe-winpe-so-you-can-boot-from-a-usb-flash-drive-or-an-external-usb-hard-drive"></a>Herunterladen und Installieren von Windows PE (Windows PE), damit Sie von einem USB-Laufwerk oder eine externe USB-Festplatte gestartet werden kann


Starten Sie den PC mithilfe des Tools BCDEdit in eine VHD-Datei ("systemeigenen Start"). Wenn Sie die virtuelle Festplatte auf einem Computer, die bereits eine Installation von Windows 10 oder Windows 8 hinzugefügt, müssen Sie dem Menü Boot-Eintrag hinzugefügt. Wenn Sie die virtuelle Festplatte auf einem Computer hinzugefügt, die eine ältere Version von Windows, beispielsweise Windows Server 2008 ausgeführt wird Sie aktualisieren, die mit dem Tool BCDboot Systempartition und ändern Sie im Startmenü mit dem BCDedit-Tool.

Systemeigene Start für Windows 10 erfordert das Format **.vhdx** , nicht das VHD-Format.

## <a name="span-idupdatethebootmenutoaddavhdspanspan-idupdatethebootmenutoaddavhdspanspan-idupdatethebootmenutoaddavhdspanupdate-the-boot-menu-to-add-a-vhd"></a><span id="Update_the_Boot_Menu_to_Add_a_VHD"></span><span id="update_the_boot_menu_to_add_a_vhd"></span><span id="UPDATE_THE_BOOT_MENU_TO_ADD_A_VHD"></span>Aktualisieren Sie das Startmenü, um eine virtuelle Festplatte hinzuzufügen.


**So aktualisieren Sie einen BIOS-basierten Computer zum Einschließen von einer Windows 8-Startmenü**

1.  Kopieren Sie die Datei .vhdx auf dem Zielcomputer aus. Beispielsweise an einer Eingabeaufforderung, geben Sie Folgendes ein:

    ``` syntax
    copy N:\VHDs\windows.vhdx C:
    ```

2.  Verwenden Sie das Tool DiskPart in Windows PE So fügen Sie die virtuelle Festplatte auf dem Zielcomputer an. Sie können eine virtuelle Festplatte mit dem **virtuellen Datenträger Attach** Befehl anfügen. Auf diese Weise können die virtuelle Festplatte, sodass sie auf dem Host als Laufwerk statt als .vhdx-Datei angezeigt wird. Geben Sie an einer Eingabeaufforderung Folgendes ein:

    ``` syntax
    diskpart
    select vdisk file=c:\windows.vhdx
    attach vdisk
    list volume
    select volume <volume_number_of_attached_VHD>
    assign letter=v
    exit
    ```

3.  Verwenden Sie das Tool BCDboot in der ** \\System32** Verzeichnis des VHD-Abbilds oder in Windows PE zum Kopieren von der Umgebung Startdateien und Boot Configuration Data (BCD) Konfiguration der ** \\Windows** in die virtuelle Festplatte, auf der Systempartition Verzeichnis. Auf einem Computer, der BIOS-Firmware verfügt, wird die Systempartition aktive Partition der ersten Festplatte. Geben Sie zum Beispiel um BCDboot aus dem Bild VHD, an einer Eingabeaufforderung zu verwenden:

    ``` syntax
    cd v:\windows\system32
    bcdboot v:\windows
    ```

Das Tool BCDboot importiert Informationen aus der vorhandenen Installation, beim Aktualisieren der Startkonfigurationsdaten. Der Computer ist jetzt zum Einschließen von einer Windows 8 Boot-Umgebung aktualisiert. Sie können jetzt die Schritte im Abschnitt "So fügen eine VHD systemeigenem Start zu einem vorhandenen Windows 8 Boot-Menü" weiter unten in diesem Thema ausführen.

**So aktualisieren Sie einen UEFI-basierten Computer zum Einschließen von einer Windows 8-Startmenü**

1.  Kopieren der Datei .vhdx auf dem Zielcomputer. Beispielsweise an einer Eingabeaufforderung, geben Sie Folgendes ein:

    ``` syntax
    copy N:\VHDs\windows.vhdx C:
    ```

2.  Verwenden Sie das Tool DiskPart in Windows PE So fügen Sie die virtuelle Festplatte auf dem Zielcomputer an. Sie können eine virtuelle Festplatte mit dem **virtuellen Datenträger Attach** Befehl anfügen. Auf diese Weise können die virtuelle Festplatte, sodass sie auf dem Host als Laufwerk statt als .vhdx-Datei angezeigt wird. Geben Sie an einer Eingabeaufforderung Folgendes ein:

    ``` syntax
    diskpart
    select vdisk file=C:\windows.vhdx
    attach vdisk
    list volume
    select volume <volume_number_of_attached_VHD>
    assign letter=v
    exit
    ```

3.  Auf einem UEFI-basierten Computer die Systempartition ist standardmäßig ausgeblendet und muss zugewiesen werden einen Laufwerkbuchstaben vor dem Ausführen des BCDboot-Tools. Verwenden Sie das DiskPart-Tool, um die EFI-Systempartition suchen, und weisen Sie es einen Laufwerkbuchstaben. Geben Sie an einer Eingabeaufforderung Folgendes ein:

    ``` syntax
    diskpart
    select disk 0
    list partition
    select partition <x>
    assign letter=s
    exit
    ```

    Dabei * &lt;x&gt; * 100 Megabyte (MB) EFI Systempartition, der mit FAT formatiert ist.

4.  Verwenden Sie das Tool BCDboot in der \\Ordner System32 des VHD-Abbilds oder in Windows PE zum Kopieren der Startdateien Umgebung und die BCD-Konfiguration aus der \\Windows-Verzeichnis in die virtuelle Festplatte, auf der Systempartition. Geben Sie zum Beispiel um BCDboot aus dem Bild VHD, an einer Eingabeaufforderung zu verwenden:

    ``` syntax
    cd v:\windows\system32
    bcdboot v:\windows
    ```

BCDboot-Tool importiert Informationen aus der vorhandenen Installation, beim Aktualisieren der Startkonfigurationsdaten. Der Computer wird nun mit einer Windows 10 Boot-Umgebung aktualisiert wurde. Führen Sie jetzt die Schritte zum Hinzufügen einer VHD systemeigenem Start zu einem vorhandenen Boot-Menü.

**Eine vorhandene Windows 8-Startmenü eine VHD systemeigenem Start hinzu**

1.  Sichern Sie Ihre BCD-Speicher mit dem BCDedit-Tool mit der **Option/Exportieren** . Geben Sie beispielsweise in einer Befehlszeile:`bcdedit /export c:\bcdbackup`

2.  Kopieren eines vorhandenen Boot-Eintrags für eine Windows-Installation. Ändern Sie dann die Kopie für die Verwendung als den VHD Boot-Eintrag. Geben Sie an der Eingabeaufforderung an ein:

    ``` syntax
    bcdedit /copy {default} /d "vhd boot (locate)"
    ```

    Wenn der BCDedit-Befehl erfolgreich abgeschlossen ist, wird {GUID} als Ausgabe in **das Eingabeaufforderungsfenster** zurückgegeben.

3.  Suchen Sie in der Befehlszeilen-Ausgabe des vorherigen Befehls die {GUID}. Kopieren Sie die GUID, einschließlich der geschweiften Klammern in den folgenden Schritten verwendet.

4.  Legen Sie die Optionen **Gerät** und **OS-Devices** für den VHD Boot-Eintrag. Geben Sie an einer Eingabeaufforderung Folgendes ein:

    ``` syntax
    bcdedit /set {guid} device vhd=[locate]\windows.vhdx
    bcdedit /set {guid} osdevice vhd=[locate]\windows.vhdx
    ```

5.  Legen Sie den Boot-Eintrag für die virtuelle Festplatte als den Standard-Boot-Eintrag. Beim Neustart des Computers zeigt im Startmenü allen Windows-Installationen auf dem Computer und Boot in die virtuelle Festplatte nach der Auswahl des Betriebssystems Countdown abgeschlossen ist. Geben Sie an einer Eingabeaufforderung Folgendes ein:

    ``` syntax
    bcdedit /default {guid}
    ```

6.  Einige X86-basierte Systeme erfordern eine Boot Konfigurationsoption für den Kernel um bestimmte Informationen zur Hardware und erfolgreich systemeigenem Start von einer virtuellen Festplatte zu erkennen. Geben Sie an einer Eingabeaufforderung Folgendes ein:

    ``` syntax
    bcdedit /set {guid} detecthal on
    ```

Weitere Informationen zum Verwenden des BCDedit-Tools finden Sie unter [diese Website von Microsoft](http://go.microsoft.com/fwlink/?LinkId=128459).

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[BCDboot Befehlszeilenoptionen](bcdboot-command-line-options-techref-di.md)

[Starten Sie VHD (systemeigenem Start): Hinzufügen einer virtuellen Festplatte zum Startmenü](boot-to-vhd--native-boot--add-a-virtual-hard-disk-to-the-boot-menu.md)

[Grundlegendes zu virtuellen Festplatten mit systemeigenem Start](understanding-virtual-hard-disks-with-native-boot.md)

 

 






