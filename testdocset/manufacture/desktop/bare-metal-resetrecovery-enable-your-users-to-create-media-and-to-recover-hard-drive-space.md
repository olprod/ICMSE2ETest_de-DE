---
author: Justinha
Description: 'Bare-Metal Reset-Recovery: Aktivieren Sie Ihre Benutzer zu Wiederherstellungsmedien erstellen'
ms.assetid: 2f12f7aa-2259-453a-a433-4fa56b03b375
MSHAttr: PreferredLib:/library/windows/hardware
title: 'Bare-Metal Reset-Recovery: Aktivieren Sie Ihre Benutzer zu Wiederherstellungsmedien erstellen'
ms.openlocfilehash: 399a175b1309786856dbd58c25c26e7e3e28a064
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="bare-metal-resetrecovery-enable-your-users-to-create-recovery-media"></a>Bare-Metal Reset-Recovery: Aktivieren Sie Ihre Benutzer zu Wiederherstellungsmedien erstellen


Wiederherstellungsmedien (bare-Metal-Recovery) hilft bei Windows-Gerät auf den Status Factory wiederherstellen, auch wenn der Benutzer muss die Festplatte ersetzen oder vollständig das Laufwerk bereinigen.

Windows verwendet die integrierten Windows-Dateien, einschließlich letzte Windows und Treiber-Updates und Anpassungen in die Bereitstellung OEM-Paket enthalten zu Wiederherstellungsmedien erstellen.

Wenn Sie das Standardlayout Partition mit Windows bereitstellen, werden können bare-Metal-Recovery Medien standardmäßig erstellt Ihre Benutzer.

Wenn Sie Windows mit einem benutzerdefinierten Partitionslayout bereitstellen, müssen Sie einige Konfigurationsdateien, um Ihre Benutzer bare-Metal-Recovery Medien erstellen hinzufügen:

-   Eine **Partition Skript zurücksetzen**, also eine geänderte DiskPart-Skript, die vom benutzerdefinierten Partitionslayout setzt.
-   Eine **Drucktaste Reset-Konfigurationsdatei** ([ResetConfig XML](resetconfig-xml-reference-s14.md)), Windows und Windows RE-Partitionen identifiziert.

**Hinweis:** In Windows 1607 Version 10, werden desktopanwendungen und Einstellungen im [Silo provisioning Pakete](siloed-provisioning-packages.md) erfasst nicht wiederhergestellt werden mithilfe der Datenträger. Reguläre Anpassungen-Pakete (.ppkg) erfasst verwenden das Tool ScanState nicht von diesem Problem betroffen sind. 

## <a name="span-idcreateconfigfilesspanspan-idcreateconfigfilesspanspan-idcreateconfigfilesspancreating-configuration-files"></a><span id="CreateConfigFiles"></span><span id="createconfigfiles"></span><span id="CREATECONFIGFILES"></span>Erstellen von Konfigurationsdateien


**Partition zurücksetzen Skript**

1.  Erstellen Sie im Editor eine Konfigurationsdatei, die die Festplatte partitioniert nach dem Zurücksetzen von der Festplatte. Dieses Skript sollten die gleiche wie das Skript zum Erstellen von Partitionen auf der Festplatte mit den folgenden Ausnahmen verwendet werden:

    -   Das Skript sollte keine Befehle auswählen oder Reinigen des Laufwerks enthalten. Windows erkennt automatisch das Systemlaufwerk. Finden Sie weitere Informationen finden Sie weiter unten in diesem Thema [dem Systemlaufwerk zu identifizieren](#identifyingthesystemdrive) .

    -   Das Skript sollte der Systempartition, die Windows-Partition und die Windows RE-Tools Partition Buchstaben zuweisen.

    Beispiele:

    UEFI (basierend auf der [Festplattenpartitionen UEFI, GPT-basierte](configure-uefigpt-based-hard-drive-partitions.md)):

    ``` syntax
    rem == ResetPartitions-UEFI.txt ==
    rem == These commands are used with DiskPart to
    rem    reset the drive and recreate five partitions
    rem    for a UEFI/GPT-based computer.
    rem    Adjust the partition sizes to fill the drive
    rem    as necessary. ==
    rem == The differences between this file and
    rem    CreatePartitions-UEFI.txt
    rem    are noted in parenthesis.
    rem       (NOT USED: select disk 0)
    rem       (NOT USED: clean)
    convert gpt
    rem == 1. System partition =========================
    create partition efi size=100
    rem    ** NOTE: For Advanced Format 4Kn drives,
    rem               change this value to size = 260 ** 
    format quick fs=fat32 label="System"
    assign letter="S"
    rem == 2. Microsoft Reserved (MSR) partition =======
    create partition msr size=128
    rem == 3. Windows partition ========================
    rem ==    a. Create the Windows partition ==========
    create partition primary 
    rem ==    b. Create space for the recovery tools ===
    shrink minimum=500
    rem       ** NOTE: Update this size to match the
    rem                size of the recovery tools 
    rem                (winre.wim)                    **
    rem ==    c. Prepare the Windows partition ========= 
    format quick fs=ntfs label="Windows"
    assign letter="C"
    rem === 4. Recovery tools partition ================
    create partition primary
    format quick fs=ntfs label="Recovery tools"
    assign letter="R"
    set id="de94bba4-06d1-4d40-a16a-bfd50179d6ac"
    gpt attributes=0x8000000000000001
    list volume
    ```

    Das BIOS (basierend auf der [Festplattenpartitionen BIOS/MBR-basierte](configure-biosmbr-based-hard-drive-partitions.md)):

    ``` syntax
    rem == ResetPartitions-BIOS.txt ==
    rem == These commands are used with DiskPart to
    rem    reset the drive and create three partitions
    rem    for a BIOS/MBR-based computer.
    rem    Adjust the partition sizes to fill the drive
    rem    as necessary. ==
    rem == The differences between this file and
    rem    CreatePartitions-BIOS.txt
    rem    are noted in parenthesis.
    rem       (NOT USED: select disk 0 )
    rem       (NOT USED: clean )
    rem == 1. System partition ======================
    create partition primary size=100
    format quick fs=ntfs label="System"
    assign letter="S"
    active
    rem == 2. Windows partition =====================
    rem ==    a. Create the Windows partition =======
    create partition primary
    rem ==    b. Create space for the recovery tools  
    shrink minimum=500
    rem       ** NOTE: Update this size to match the
    rem                size of the recovery tools 
    rem                (winre.wim)                 **
    rem ==    c. Prepare the Windows partition ====== 
    format quick fs=ntfs label="Windows"
    assign letter="C"
    rem == 3. Recovery tools partition ==============
    create partition primary
    format quick fs=ntfs label="Recovery"
    assign letter="R"
    set id=27
    list volume
    ```

2.  Speichern Sie die Datei, z. B. E:\\Wiederherstellung\\RecoveryImage\\ResetPartitions UEFI.txt.

**Drucktaste Reset-Konfigurationsdatei (ResetConfig.xml)**

1.  Erstellen Sie im Editor eine Konfigurationsdatei, die auf Ihrem Drucktaste zurücksetzen Partition Skript verweist.

    Informationen zum Konfigurieren dieser Datei finden Sie unter [ResetConfig XML-Referenz](resetconfig-xml-reference-s14.md).

    UEFI:

    ``` syntax
    <?xml version="1.0" encoding="utf-8"?>
    <!-- ResetConfig.xml for UEFI -->
    <Reset>
        <!-- May be combined with custom scripts – insert Run Phase elements here -->
        <SystemDisk>
            <DiskpartScriptPath>ResetPartitions-UEFI.txt</DiskpartScriptPath>
            <MinSize>75000</MinSize>
            <WindowsREPartition>4</WindowsREPartition>
            <WindowsREPath>Recovery\WindowsRE</WindowsREPath>
            <OSPartition>3</OSPartition>
        </SystemDisk>
    </Reset>
    ```

    BIOS:

    ``` syntax
    <?xml version="1.0" encoding="utf-8"?>
    <!-- ResetConfig.xml for BIOS -->
    <Reset>
        <!-- May be combined with custom scripts – insert Run Phase elements here -->
        <SystemDisk>
            <DiskpartScriptPath>ResetPartitions-BIOS.txt</DiskpartScriptPath>
            <MinSize>75000</MinSize>
            <WindowsREPartition>3</WindowsREPartition>
            <WindowsREPath>Recovery\WindowsRE</WindowsREPath>
            <OSPartition>2</OSPartition>
        </SystemDisk>
    </Reset>
    ```

2.  Speichern Sie die Datei im UTF-8-Dateiformat verwenden:

    Klicken Sie auf **Datei**, und klicken Sie dann auf **Speichern unter**. Wählen Sie **UTF-8**im **Codierung** und speichern Sie die Datei als E:\\Wiederherstellung\\RecoveryImage\\ResetConfig.xml.

## <a name="span-idenableendusersspanspan-idenableendusersspanspan-idenableendusersspanenable-users-to-create-media"></a><span id="EnableEndUsers"></span><span id="enableendusers"></span><span id="ENABLEENDUSERS"></span>Können Sie Benutzer Medien erstellen.


Benutzer können diese Option zum Erstellen von Wiederherstellungsmedien sowie für das Freigeben von des Festplattenspeichers aus der Wiederherstellung Image-Partition bei Bedarf verwenden.

**Schritt 1: Hinzufügen der Konfigurationsdateien auf den Zielcomputer**

1.  Fügen Sie auf dem Zielcomputer das USB flash-Laufwerk mit den Konfigurationsdateien.

2.  Kopieren Sie die Konfigurationsdateien auf dem Zielcomputer aus:

    ``` syntax
    Copy E:\Recovery\RecoveryImage\* R:\RecoveryImage\*
    ```

    wobei *E* der Laufwerkbuchstabe des USB-Laufwerk und *R* ist, ist der Laufwerkbuchstabe der Wiederherstellung Bild Partition.

**Schritt 2: Testen von Windows kann Wiederherstellungsmedien erstellen.**

1.  Starten Sie den Zielcomputer neu, und führen Sie Out-Of-Box-Experience (OOBE).

2.  Klicken Sie auf **Start**, geben Sie **ein Wiederherstellungslaufwerk zu erstellen**, und wählen Sie **erstellen eine Wiederherstellungslaufwerk**aus und klicken Sie auf **Ja** , an der Eingabeaufforderung UAC.

3.  Fügen Sie einem USB-Laufwerk ein.

4.  Wählen Sie **die Wiederherstellungspartition vom PC mit dem Recovery-Laufwerk kopieren** &gt; **nächsten** &gt; **nächsten** &gt; **Erstellen**.

**Schritt 3: Testen der Wiederherstellungsmedien**

1.  Legen Sie auf einem Computer, der kein Betriebssystem installiert ist die Wiederherstellungsmedien.
2.  Starten Sie den Computer, drücken Sie zum Öffnen der Firmware Boot-Menüs, und wählen Sie dann das entsprechende Boot-Gerät aus.
3.  Wählen Sie ein Tastaturlayout, beispielsweise **UNS**an die Menüs **Windows RE-Tools** aus.
4.  Klicken Sie auf **Problembehandlung** &gt; **Zurücksetzen von Ihrem PC** &gt; **Weiter**. Wenn Sie aufgefordert werden, das Laufwerk zu bereinigen, wählen Sie **Ja**.
5.  Wählen Sie **Ja, die Laufwerke partitionieren** &gt; **Meine Dateien entfernen** &gt; **Zurücksetzen**.

**Problembehandlung:**

-   Stellen Sie sicher, dass ResetConfig.xml als UTF-8-Datei gespeichert ist.
-   Stellen Sie sicher, dass der Dateiname im aufgeführt die &lt;DiskpartScriptPath&gt; Element der Datei ResetConfig.xml entspricht der Dateiname in der Diskpart-Skript.
-   Stellen Sie sicher, dass das Skript Diskpart Befehle aus, um das Laufwerk reinigen oder wählen Sie das Laufwerk umfassen nicht (`select disk 0`, `clean`).

## <a name="span-ididentifyingthesystemdrivespanspan-ididentifyingthesystemdrivespanspan-ididentifyingthesystemdrivespanidentifying-the-system-drive"></a><span id="IdentifyingTheSystemDrive"></span><span id="identifyingthesystemdrive"></span><span id="IDENTIFYINGTHESYSTEMDRIVE"></span>Identifizieren von dem Systemlaufwerk


Windows identifiziert das Systemlaufwerk mithilfe der folgenden Methoden:

**BIOS-basierte Computer**: das BIOS gemeldete Systemlaufwerk verwendet wird.

**UEFI-basierte Computer**: Wenn Windows RE aktiviert ist, mithilfe der `reagentc /setreimage` Befehl Windows schreibt der Pfad zum Speicherort Adapter und die GUID des Systemdatenträgers in eine UEFI-Variable. Dieser Schritt wird nur ausgeführt, wenn Systems sowie OS Partitionen auf dem Systemlaufwerk sind. Die Variable wird bei Bedarf aktualisiert, wenn Windows RE ruft deaktiviert, und klicken Sie dann erneut aktiviert.

**Wenn mehrere lokale Laufwerke erkannt werden, identifiziert Windows das Systemlaufwerk, indem Sie in der folgenden Reihenfolge suchen:**

1.  Windows sucht nach einem Laufwerk mit einer GUID, der dem Wert in der Firmware gespeichert.

2.  Windows sucht nach einem Laufwerk mit einem Speicherort Pfad, der dem Wert in der Firmware gespeichert.

3.  Windows sucht nach einem Laufwerk mit einer vorhandenen ESP.

    Wenn mehrere Laufwerke mit ESP gefunden werden, wird der Prozess zur Wiederherstellung nicht fortgesetzt werden.

4.  Windows sucht nach einem nicht initialisiert (unformatiert) Datenträger.

    Wenn mehrere nicht initialisierte Datenträger gefunden werden, wird der Prozess zur Wiederherstellung nicht fortgesetzt werden.

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Übersicht über die Drucktaste zurücksetzen](push-button-reset-overview.md)

[ResetConfig XML (engl.)](resetconfig-xml-reference-s14.md)

[Bare-Metal Reset-Recovery: Erstellen von Wiederherstellungsmedien beim Bereitstellen neuer Geräte](create-media-to-run-push-button-reset-features-s14.md)

[Festplatte UEFI, GPT-basierte Partitionen](configure-uefigpt-based-hard-drive-partitions.md)

[Festplatte BIOS/MBR-basierte Partitionen](configure-biosmbr-based-hard-drive-partitions.md)

 

 






