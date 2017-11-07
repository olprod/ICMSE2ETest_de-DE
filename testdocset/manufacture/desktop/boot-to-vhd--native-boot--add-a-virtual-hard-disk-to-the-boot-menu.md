---
author: Justinha
Description: "Starten Sie VHD (systemeigenem Start): Hinzufügen einer virtuellen Festplatte zum Startmenü"
ms.assetid: e00d7f8f-502c-40e5-904c-8cc653c1899e
MSHAttr: PreferredLib:/library/windows/hardware
title: "Starten Sie VHD (systemeigenem Start): Hinzufügen einer virtuellen Festplatte zum Startmenü"
ms.openlocfilehash: 1a111e2ad8a07244fa198ffa552bd16a6d1d7eff
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="boot-to-vhd-native-boot-add-a-virtual-hard-disk-to-the-boot-menu"></a>Starten Sie VHD (systemeigenem Start): Hinzufügen einer virtuellen Festplatte zum Startmenü


Systemeigene Start können Sie eine virtual Hard Disk (VHD) erstellen, Installieren von Windows, und klicken Sie dann entweder auf Ihrem PC Side-by-Side-mit Ihre vorhandene Installation von oder auf ein neues Gerät starten.

Virtuelle Festplatte mit eine einheitlichen Boot kann als ausgeführtes Betriebssystem für die designierte Hardware ohne zu einem anderen übergeordneten Betriebssystem verwendet werden. Dies unterscheidet sich von einem Szenario, in dem eine virtuelle Festplatte mit einem virtuellen Computer auf einem Computer verbunden ist, das ein übergeordnetes Betriebssystem verfügt.

VHDs können auf PCs oder Geräte, die keine anderen Installationen von Windows, ohne einen virtuellen Computer oder Hypervisor angewendet werden. (Ein Hypervisor ist eine Ebene der Software unter dem Betriebssystem, das virtuellen Computer ausgeführt wird.) Auf diese Weise können größere Flexibilität bei der Verteilung der Arbeitslast, da ein einzelner Satz von Tools zum Verwalten von Bildern für virtuelle Computer verwendet und Hardware festgelegt werden kann.

Sie können das Bereitstellen der virtuellen Festplatte an einem Computer an, die bereits von Windows installiert ist, und ein Startmenü verwenden, um zwischen der vorhandenen Version von Windows oder die Version auf die virtuelle Festplatte auszuwählen.

Weitere Informationen zur Verwendung von VHDs in einer unternehmensumgebung finden Sie unter [Grundlegendes zu virtuellen Festplatten mit systemeigenem Start](understanding-virtual-hard-disks-with-native-boot.md).

## <a name="span-idprerequisitesspanspan-idprerequisitesspanspan-idprerequisitesspanprerequisites"></a><span id="Prerequisites"></span><span id="prerequisites"></span><span id="PREREQUISITES"></span>Erforderliche Komponenten


-   Ein Techniker PC mit dem Windows Assessment and Deployment Kit (Windows ADK) Tools installiert ist.

-   Ein allgemeiner Windows-Abbild (engl.) (. WIM-Datei). Weitere Informationen finden Sie unter [Sysprep (verallgemeinern) einer Windows-Installation](sysprep--generalize--a-windows-installation.md).

-   Ein startbare Windows PE-Laufwerk. Weitere Informationen finden Sie unter [Windows PE: Erstellen startbaren USB-Laufwerk](winpe-create-usb-bootable-drive.md).

-   Ein Ziel-PC oder ein Gerät, auf die virtuelle Festplatte installiert. Dieses Gerät benötigt mit mindestens 30 Gigabyte (GB) freier Speicherplatz vorhanden. Sie können die virtuelle Festplatte mit einem anderen Betriebssysteminstallationen bereits ausgeführt Gerät oder als nur das Betriebssystem auf einem Gerät installieren.

## <a name="span-idstep1createavhdfromdiskpartspanspan-idstep1createavhdfromdiskpartspanspan-idstep1createavhdfromdiskpartspanstep-1-create-a-vhd-from-diskpart"></a><span id="Step_1__Create_a_VHD_from_diskpart"></span><span id="step_1__create_a_vhd_from_diskpart"></span><span id="STEP_1__CREATE_A_VHD_FROM_DISKPART"></span>Schritt 1: Erstellen einer virtuellen Festplatte aus diskpart


1.  Öffnen Sie auf der PC-Techniker Diskpart ein.

    ``` syntax
    diskpart
    ```

2.  Erstellen und eine neue virtuelle Festplatte vorbereiten. In diesem Beispiel erstellen wir eine feste virtuelle Festplatte mit einer Größe von 25 GB.

    ``` syntax
    create vdisk file=C:\windows.vhd maximum=25600 type=fixed
    ```

3.  Fügen Sie die virtuelle Festplatte. Dadurch wird die virtuelle Festplatte als Datenträger den Speichercontroller auf dem Host.

    ``` syntax
    attach vdisk
    ```

4.  Erstellen Sie eine Partition aus, für den Windows-Dateien, formatieren Sie ihn, und weisen Sie es mit einen Laufwerkbuchstaben. Dieser Laufwerkbuchstabe wird im Datei-Explorer angezeigt.

    ``` syntax
    create partition primary
    format quick label=vhd
    assign letter=v
    ```

5.  Beenden Sie Diskpart

    ``` syntax
    exit
    ```

## <a name="span-idstep2applyawindowsimagetothevhdspanspan-idstep2applyawindowsimagetothevhdspanspan-idstep2applyawindowsimagetothevhdspanstep-2-apply-a-windows-image-to-the-vhd"></a><span id="Step_2__Apply_a_Windows_image_to_the_VHD"></span><span id="step_2__apply_a_windows_image_to_the_vhd"></span><span id="STEP_2__APPLY_A_WINDOWS_IMAGE_TO_THE_VHD"></span>Schritt 2: Anwenden eines Windows-Abbilds auf die virtuelle Festplatte


-   Die primäre Partition der virtuellen Festplatte ein allgemeine Übersicht über Windows-Abbild zuweisen.

    ``` syntax
    Dism /Apply-Image /ImageFile:install.wim /index:1 /ApplyDir:V:\
    ```

## <a name="span-idstep3detachthevhdcopyittoanewdeviceandattachitoptionalspanspan-idstep3detachthevhdcopyittoanewdeviceandattachitoptionalspanspan-idstep3detachthevhdcopyittoanewdeviceandattachitoptionalspanstep-3-detach-the-vhd-copy-it-to-a-new-device-and-attach-it-optional"></a><span id="Step_3__Detach_the_VHD__copy_it_to_a_new_device__and_attach_it__optional_"></span><span id="step_3__detach_the_vhd__copy_it_to_a_new_device__and_attach_it__optional_"></span><span id="STEP_3__DETACH_THE_VHD__COPY_IT_TO_A_NEW_DEVICE__AND_ATTACH_IT__OPTIONAL_"></span>Schritt 3: Trennen Sie die virtuelle Festplatte, auf ein neues Gerät kopieren Sie und fügen Sie es (optional)


Sie können die virtuelle Festplatte bereitstellen, zu einem Gerät, die bereits eine Kopie von Windows installiert ist, oder Sie bereinigen und das Laufwerk, verwenden Sie die virtuelle Festplatte vorbereiten.

**Trennen der virtuellen Festplatte und speichern Sie sie zu einem Netzlaufwerk Speicher oder Dateifreigabe**

1.  Trennen Sie den virtuellen Datenträger.

    ``` syntax
    diskpart
    select vdisk file=C:\windows.vhd
    detach vdisk
    exit
    ```

2.  Kopieren Sie die virtuelle Festplatte in einer Netzwerkfreigabe oder Wechselspeicher Laufwerk.

    ``` syntax
    net use n: \\server\share\
    md N:\VHDs
    copy C:\windows.vhd n:\VHDs\
    ```

**Bereinigen und Vorbereiten eines neuen Geräts systemeigenen Start**

1.  Starten Sie das Zielgerät Windows Vorinstallation Environment (Windows PE).
2.  Bereinigen und das Laufwerk vorbereiten. Erstellen Sie eine Systempartition (S) und eine Hauptfenster Partition (M), in dem die virtuelle Festplatte gespeichert wird.

    BIOS:

    ``` syntax
    diskpart
    select disk 0
    clean
    rem == 1. System partition ======================
    create partition primary size=100
    format quick fs=ntfs label="System"
    assign letter="S"
    active
    rem == 2. Main partition ========================
    create partition primary
    format quick fs=ntfs label="Main"
    assign letter="M"
    exit
    ```

    UEFI:

    ``` syntax
    diskpart
    select disk 0
    clean
    convert gpt
    rem == 1. System partition =========================
    create partition efi size=100
    format quick fs=fat32 label="System"
    assign letter="S"
    rem == 2. Microsoft Reserved (MSR) partition =======
    create partition msr size=128
    rem == 3. Main partition ===========================
    create partition primary 
    format quick fs=ntfs label="Main"
    assign letter="M"
    exit
    ```

3.  Verbinden mit einem Speicherort im Netzwerk Laufwerk oder Speicherung, und notieren Sie den Laufwerkbuchstaben aus.

    ``` syntax
    net use N: \\server\share
    ```

4.  Kopieren Sie die virtuelle Festplatte auf die wichtigsten Partition aus.

    ``` syntax
    copy N:\VHDs\Windows.vhd M:
    ```

**Fügen Sie die virtuelle Festplatte**

1.  Fügen Sie die virtuelle Festplatte.

    ``` syntax
    diskpart
    select vdisk file=M:\windows.vhd
    attach vdisk
    ```

2.  Identifizieren der Volumebuchstabe. (Optional: Ändern Sie ihn in einen anderen Buchstaben, der, beispielsweise V, sinnvoller, und lassen Sie die Befehlszeile Diskpart für den nächsten Schritt).

    ``` syntax
    list volume
    select volume 3
    assign letter=v
    ```

## <a name="span-idstep4addabootentryspanspan-idstep4addabootentryspanspan-idstep4addabootentryspanstep-4-add-a-boot-entry"></a><span id="Step_4__Add_a_boot_entry"></span><span id="step_4__add_a_boot_entry"></span><span id="STEP_4__ADD_A_BOOT_ENTRY"></span>Schritt 4: Hinzufügen eines Boot-Eintrags


1.  Öffnen Sie Diskpart (falls erforderlich) und identifizieren Sie die Laufwerkbuchstaben von der virtuellen Festplatte und die Systempartition, beispielsweise V und S.

    ``` syntax
    diskpart
    list volume
    exit
    ```

2.  Das Gerät einen Boot-Eintrag hinzugefügt. Sie können mehrere VHD-Dateien mit dieser Methode hinzufügen.

    BIOS:

    ``` syntax
    V:
    cd v:\windows\system32
    bcdboot v:\windows /s S: /f BIOS
    ```

    UEFI:

    ``` syntax
    V:\
    cd v:\windows\system32
    bcdboot v:\windows /s S: /f UEFI
    ```

3.  Entfernen Sie den Windows PE USB-Schlüssel.

4.  Starten Sie das Gerät neu.

    Wenn nur eine Boot-Eintrag vorhanden ist, startet das Gerät sofort Windows. Wenn mehr als eine Boot-Eintrag vorhanden ist, sehen Sie ein Startmenü, auf dem Sie zwischen den verfügbaren Versionen von Windows auf dem Gerät auswählen können.

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Grundlegendes zu virtuellen Festplatten mit systemeigenem Start](understanding-virtual-hard-disks-with-native-boot.md)

[BCDboot Befehlszeilenoptionen](bcdboot-command-line-options-techref-di.md)

 

 






