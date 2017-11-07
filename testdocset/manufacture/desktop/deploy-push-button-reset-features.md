---
author: Justinha
Description: Push-button reset features are included with Windows 10 for desktop editions (Home, Pro, Enterprise, and Education), though you'll need to perform additional steps to deploy PCs with the following customizations.
ms.assetid: f23d7e3f-0254-4fe8-9d61-5a58856c74be
MSHAttr: PreferredLib:/library/windows/hardware
title: Bereitstellen von Drucktaste Reset-features
ms.openlocfilehash: 3849dc9bd5eadc46f9474973799b12548fa00002
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="deploy-push-button-reset-features"></a>Bereitstellen von Drucktaste Reset-features


Drucktaste zurücksetzen Funktionen stehen unter Windows 10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen), obwohl Sie zusätzliche Schritte zum Bereitstellen von PCs mit den folgenden Anpassungen ausführen müssen.

-   Windows-desktopanwendungen
-   Windows-Einstellungen, wie benutzerdefinierte OOBE Bildschirme oder Menüs starten.
-   Angepasste Partitionslayouts.

Diese Schritte zeigen auch zum Hinzufügen eigener Skripts während einer Zurücksetzung zum Erfassen von Protokollen oder andere Bereinigungsaufgaben ausführen.

## <a name="span-idprerequisitesspanspan-idprerequisitesspanspan-idprerequisitesspanprerequisites"></a><span id="Prerequisites"></span><span id="prerequisites"></span><span id="PREREQUISITES"></span>Erforderliche Komponenten


Um diese Verfahren auszuführen, benötigen Sie einen PC-Techniker Windows 10 und folgende Windows Assessment and Deployment Kit (ADK) für Windows 10 Komponenten installiert ist:

-   Bereitstellungstools
-   Vorinstallation Windows-Umgebung (Windows PE)
-   Imaging und Konfiguration-Designer (ICD)
-   Migrationstool für den Benutzerstatus (USMT)

Sie benötigen auch Folgendes:

-   Ein Ziel PC mit einer Größe von 100 GB oder größer
-   Ein Windows-10 für desktop-Editionen Bild (install.wim)
-   Ein Windows RE Boot-Abbild (Winre.wim) (Sie werden von einem Windows-10-Abbild dies extrahieren).

Eine Übersicht über die gesamte Bereitstellung finden Sie im [Desktop Fertigung Guide](http://go.microsoft.com/fwlink/p/?LinkId=526101).

Verwenden Sie die Schritte gehen Sie folgendermaßen vor, um das Tool ScanState Windows-desktopanwendungen erfasst, nachdem sie installiert wurden vorzubereiten:

**Schritt 1: Vorbereiten des ScanState-Tools**

1.  Kopieren Sie auf der PC-Techniker die Windows ADK-Dateien aus Windows User State Migration Tool (USMT) und Windows-Setup auf einen Ordner. Sie müssen die Architektur des Zielgeräts übereinstimmen. Sie müssen nicht die Unterordner zu kopieren.

    ``` syntax
    md C:\ScanState_amd64
    xcopy /E "C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\User State Migration Tool\amd64" C:\ScanState_amd64
    xcopy /E /Y "C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Setup\amd64\Sources" C:\ScanState_amd64
    ```

2.  In einigen Fällen können Windows Defender Einstellungen und Erkennung Verlauf von dem Tool ScanState in das Paket Anpassungen erfasst werden. Dadurch kann dazu führen, dass Fehler während der Wiederherstellung aufgrund von Dateikonflikten, und den PC neu starten, und geben die Phase "Installieren von Windows" wiederholt. Die folgenden Schritte werden verhindert, dass Windows Defender Einstellungen erfasst werden.

    1.  Verwenden das Tool ScanState auf einem Computer mit Windows 10, generieren Sie eine Konfigurationsdatei:

        ``` syntax
        ScanState.exe /apps /genconfig:C:\pbr_config.xml 
        ```

    2.  Öffnen Sie die Konfigurationsdatei im Editor
    3.  Suchen Sie die folgenden Zeilen in der Konfigurationsdatei:

        ``` syntax
        <component displayname="Windows-Defender-AM-Sigs" migrate="yes"… 
        <component displayname="Windows-Defender-AM-Engine" migrate="yes"… 
        <component displayname="Security-Malware-Windows-Defender" migrate="yes"… 
        ```

    4.  Ändern Sie den Wert "migrieren" von "Ja" auf "Nein" für jede Zeile. Beispiel:

        ``` syntax
        <component displayname="Windows-Defender-AM-Sigs" migrate="no"… 
        <component displayname="Windows-Defender-AM-Engine" migrate="no"… 
        <component displayname="Security-Malware-Windows-Defender" migrate="no"… 
        ```

        In Schritt 10 weiter unten in diesem Thema werden Sie die Konfigurationsdatei angeben, wenn Sie ScanState verwenden, um die Anpassungen in eine Datei .ppkg erfassen.

    5.  Speichern Sie und schließen Sie die Konfigurationsdatei.

3.  Kopieren Sie den Inhalt des Arbeitsordners an einem Netzwerkspeicherort oder USB flash-Laufwerk.

Gehen Sie folgendermaßen vor, das Windows RE-Boot-Abbild anpassen, wenn zusätzliche Treiber und Language Packs erforderlich sind.

**Schritt 2: Extrahieren und das Windows RE-Boot-Abbild (optional) anpassen**

1.  Klicken Sie auf den Techniker PC klicken Sie auf **Start**, und geben Sie die Bereitstellung. Mit der rechten Maustaste **Bereitstellung und Imaging Tools Umgebung** , und wählen Sie dann auf **als Administrator ausführen**.
2.  Erstellen Sie in **Bereitstellung und Imaging Tools Umgebung**die Ordnerstruktur, um das Windows-Abbild und den Bereitstellungspunkt zu speichern.

    ``` syntax
    Mkdir C:\OS_image\mount
    ```

3.  Erstellen Sie die Ordnerstruktur, um das Windows RE Boot-Abbild und den Bereitstellungspunkt zu speichern.

    ``` syntax
    Mkdir C:\winre_amd64\mount
    ```

4.  Stellen Sie das Windows-Abbild (install.wim) in den Ordner \\OS\_Bild\\mit dem DISM bereitstellen.

    ``` syntax
    Dism /mount-image /imagefile:C:\OS_image\install.wim /index:1 /mountdir:C:\OS_image\mount
    ```

    wobei `Index:1` ist der Index des ausgewählten Bilds in der Install.wim-Datei.

5.  Kopieren Sie das Windows RE-Abbild aus bereitgestellten Windows-Abbild, in den neuen Ordner.

    ``` syntax
    xcopy /H C:\OS_image\mount\windows\system32\recovery\winre.wim C:\winre_amd64 
    ```

6.  Heben Sie die Bereitstellung des Windows-Abbilds. Tipp: Wenn Sie im Windows-Abbild alle Änderungen vorgenommen noch nicht, Sie können die Bereitstellung aufheben des Bilds schneller mithilfe der `/discard` Option.

    ``` syntax
    Dism /unmount-image /mountdir:C:\OS_image\mount /discard
    ```

7.  Stellen Sie das Windows RE-Boot-Abbild zur Bearbeitung.

    ``` syntax
    Dism /mount-image /imagefile:C:\winre_amd64\winre.wim /index:1 /mountdir:C:\winre_amd64\mount
    ```

    wobei `Index:1` ist die Nummer des ausgewählten Bilds in der Datei Winre.wim.

    Nachdem die Datei Winre.wim aus der Datei Install.wim extrahiert wird, können Sie das Windows RE-Boot-Abbild anpassen.

8.  Fügen Sie das Windows RE-Boot-Abbild Sprachpakete, Treiber erforderliche und Treiber. Weitere Informationen finden Sie unter [Windows RE anpassen](customize-windows-re.md).
9.  Commit Ihre Anpassungen und das Bild aufheben.

    ``` syntax
    Dism /unmount-image /mountdir:C:\winre_amd64\mount /commit 
    ```

Wenn Sie nur die für alle Editionen von Windows 10 (einschließlich Windows 10 Mobile) Allgemeine Einstellungen anpassen möchten, gehen Sie folgendermaßen vor, provisioning Paket zu erstellen, der während der Wiederherstellung wiederhergestellt werden Einstellungen angibt:

**Schritt 3: Erstellen eines Pakets Bereitstellung mit Einstellungen, die wiederhergestellt werden soll (optional)**

1.  Starten Sie auf der PC-Techniker Windows Imaging und Konfiguration Designer (ICD).
2.  Klicken Sie auf **Datei** &gt; **Neues Projekt**.
3.  Geben Sie einen Projektnamen und eine Beschreibung ein, und klicken Sie dann auf **Weiter**
4.  Im Schritt **Wählen Sie Project Workflow** **Provisioning-Pakets** die Option, und klicken Sie dann auf **Weiter**.
5.  Anzeigen und Konfigurieren der Einstellungen im Schritt **auswählen** wählen Sie die Option für die **gemeinsame für alle Editionen von Windows** , und klicken Sie dann auf **Weiter**.
6.  Klicken Sie im Schritt **Import ein (optional) Bereitstellung Paket** auf **Fertig stellen** , um das neue Projekt zu erstellen.
7.  Verwenden Sie den **Anpassungen verfügbar** Bereich, um Einstellungen hinzufügen, und geben Sie die Standardeinstellungen, die während der Wiederherstellung wiederhergestellt werden soll. Klicken Sie im Bereich **ausgewählte Anpassungen** werden die Einstellungen angezeigt.
8.  Klicken Sie auf **Exportieren** &gt; **Provisioning-Paket**.
9.  Klicken Sie im Schritt **beschreiben das provisioning Paket** auf **Weiter**.
10. Klicken Sie im Schritt **Wählen Sie die Sicherheitsdetails für die Bereitstellung Paket** auf **Weiter**.
11. Geben Sie im Schritt **auswählen, wo Sie das Paket provisioning speichern** einen Speicherort zum Speichern des Pakets (beispielsweise eine Netzwerkfreigabe), und klicken Sie dann auf **Weiter**.
12. Klicken Sie auf **Erstellen** , um die Bereitstellung Paket zu erstellen.
13. Nach das Bereitstellung Paket erstellt wurde, klicken Sie auf **Fertig stellen**.

Wenn Ihre Anpassungen Einstellungen, die speziell für Editionen von Windows-10 für desktop-Editionen umfassen, gehen Sie folgendermaßen vor, um eine unattend.xml gibt an, die während der Wiederherstellung wiederhergestellt werden Einstellungen zu erstellen:

**Schritt 4: Erstellen Sie eine Datei zum Wiederherstellen der Einstellungen für (optional)**

1.  Starten Sie auf der PC-Techniker **Windows System Image Manager**.
2.  Klicken Sie auf **Datei** &gt; **Wählen Sie Windows-Abbild**.
3.  Wenn Sie aufgefordert, einen Katalog erstellen, klicken Sie auf **Ja**.
4.  Verwenden Sie die **Windows-Abbild** und **Antwortdatei** Bereiche Einstellungen der Specialize OobeSystem Phase (oder beides) hinzufügen, und geben Sie die Standardeinstellungen, die während der Wiederherstellung wiederhergestellt werden soll ein.
5.  Klicken Sie auf **Tool** &gt; **Antwortdatei überprüfen** auf Fehler überprüfen. Korrigieren Sie ein Problem identifiziert.
6.  Klicken Sie auf **Datei** &gt; **Antwortdatei speichern**. Geben Sie einen Speicherort für die Antwortdatei (beispielsweise eine Netzwerkfreigabe) speichern, und klicken Sie dann auf **Speichern**.

Wenn Sie Drucktaste zurücksetzen Erweiterungspunkte verwenden möchten, verwenden Sie die folgenden Schritte aus zum Vorbereiten der Erweiterbarkeit Skripts und registrieren Sie sie mit einer Konfigurationsdatei Drucktaste zurücksetzen.

**Wichtige**  Wenn Sie eine Datei für die unbeaufsichtigte Installation erstellt haben, müssen Sie auch erstellen ein Skripts, um ihn mit der BasicReset Erneutes Anwenden von\_AfterImageApply und FactoryReset\_AfterImageApply Erweiterungspunkte.

 

**Schritt 5: Vorbereiten der Drucktaste zurücksetzen Erweiterbarkeit-Skripts (optional)**

1.  Erstellen von Skripts (cmd) oder ausführbare Dateien (.exe) unter zur Verfügung stehenden Erweiterungspunkte auszuführen, wenn die Aktualisierung Ihrer PC-Funktion ausgeführt wird:

    A: am BasicReset\_BeforeImageApply

    B: unter BasicReset\_AfterImageApply

2.  Erstellen von Skripts (cmd) oder ausführbare Dateien (.exe) unter zur Verfügung stehenden Erweiterungspunkte auszuführen, wenn das Feature zurücksetzen PC ausgeführt wird:

    C: unter FactoryReset\_AfterDiskFormat

    D: unter FactoryReset\_AfterImageApply

3.  Speichern die Skripts an einem Netzwerkspeicherort oder USB flash-Laufwerk.
4.  Erstellen Sie eine ResetConfig.xml-Datei, die den Speicherort des Skripts angibt, die Sie für die vier Erweiterungspunkte erstellt haben. Beispiel:

    ``` syntax
    <?xml version="1.0" encoding="utf-8"?>
    <Reset>
        <Run Phase="BasicReset_BeforeImageApply">
            <Path>Fabrikam\SampleScript_A.cmd</Path>
            <Duration>2</Duration>
        </Run>
        <Run Phase="BasicReset_AfterImageApply">
            <Path>Fabrikam\SampleScript_B.cmd</Path>
            <Param></Param>
            <Duration>2</Duration>
        </Run>
        <Run Phase="FactoryReset_AfterDiskFormat">
            <Path>Fabrikam\SampleScript_C.cmd</Path>
            <Duration>2</Duration>
        </Run>
        <Run Phase="FactoryReset_AfterImageApply">
            <Path>Fabrikam\SampleScript_D.cmd</Path>
            <Param></Param>
            <Duration>2</Duration>
        </Run>
    </Reset>
    ```

    **Wichtige**  Wenn Sie einen Text-Editor verwenden, um die ResetConfig.xml-Datei erstellen, speichern Sie das Dokument mit der Erweiterung XML-Datei, und verwenden Sie **UTF-8-Codierung**. Verwenden Sie Unicode- oder ANSI nicht.

     

5.  Speichern Sie die Datei ResetConfig.xml zusammen mit der Erweiterbarkeit-Skripts, die Sie erstellt haben.

**Schritt 6: Bare-Metal Recovery-Konfiguration erstellen Sie (optional)**

-   Ändern Sie zum Angeben des Layouts Partition verwendet werden, wenn Benutzer bare-Metal-Recovery mit Wiederherstellungsmedien aus ihren PCs teilnehmen erstellten ausführen resetconfig.xml, um die folgenden Elemente enthalten:

    ``` syntax
    <?xml version="1.0" encoding="utf-8"?>
    <Reset>
                <SystemDisk>
            <MinSize>160000</MinSize>
            <DiskpartScriptPath>ReCreatePartitions.txt</DiskpartScriptPath>
            <OSPartition>3</OSPartition>
            <WindowsREPartition>4</WindowsREPartition>
            <WindowsREPath>Recovery\WindowsRE</WindowsREPath>
            <Compact>False</Compact>
    </SystemDisk>
    </Reset>
    ```

    -   **MinSize** - gibt die minimale Größe des Systemdatenträgers in Megabyte (MB). Prozess zur Wiederherstellung wird nicht fortgesetzt werden, wenn der Systemdatenträger Mindestgröße nicht erfüllt.
    -   **DiskpartScriptPath** - Pfad zum Skript relativ zum Speicherort der install.wim Diskpart. Das Skript sollte wird davon ausgegangen, dass alle vorhandene Partitionen gelöscht wurden, und der Systemdatenträger den Fokus in Diskpart hat.
    -   **OSPartition** - Partition auf dem das Wiederherstellungsabbild angewendet werden soll, müssen angegeben werden. Der ESP oder aktiven Partition muss sich auf demselben Laufwerk wie das Betriebssystem.
    -   **WindowsREPartition**; **WindowsREPath –** (Optional) Der Speicherort, in dem WinRE bereitgestellt werden soll. Das WinRE Boot-Abbild auf die Medien werden kopiert und mit dem Betriebssystem registriert werden. (Identisch mit ausgeführten "reagentc.exe /setreimage")

    Wenn Partitionierung Informationen im resetconfig.xml nicht angegeben ist, können Benutzer weiterhin ausführen bare-Metal-Recovery von ihnen erstellten Medien. Stattdessen wird jedoch das standardmäßige/empfohlenen Partitionslayout für Windows 10 verwendet werden.

**Schritt 7: Erstellen eines Diskpart-Skripts für die erste Bereitstellung**

1.  Erstellen Sie einen Skript für die erste Bereitstellung Partitionierung Datenträger.

    **UEFI-Beispiel**:

    ``` syntax
    rem These commands are used with DiskPart tool.
    rem Erase the drive and create four partitions
    rem for a UEFI/GPT-based PC.
    select disk 0
    clean
    convert gpt
    rem == 1. System Partition =======================
    create partition efi size=100
    rem ***NOTE: For 4KB-per-sector drives, change 
    rem this value to size=260.***
    format quick fs=fat32 label="System"
    assign letter="S"
    rem == 2. Microsoft Reserved (MSR) Partition =====
    create partition msr size=16
    rem == 3. Windows Partition ======================
    rem ==    a. Create Windows Partition ============
    create partition primary
    rem ==    b. Create space for Windows RE tools partition
    shrink minimum=450
    rem ==    c. Prepare the Windows partition
    format quick fs=ntfs label="Windows"
    assign letter="W"
    rem == 4. Windows RE Tools Partition =============
    create partition primary
    format quick fs=ntfs label="Windows RE tools"
    set id=de94bba4-06d1-4d40-a16a-bfd50179d6ac
    assign letter="T"
    exit
    ```

    **BIOS-Beispiel**:

    ``` syntax
    rem These commands are used with DiskPart to 
    rem erase the drive and create three partitions 
    rem for a BIOS/MBR-based PC. 
    rem Adjust the partition sizes to fill the drive.
    select disk 0
    clean
    rem === 1. System Partition =====================
    create partition primary size=100
    format quick fs=ntfs label="System"
    assign letter="S" 
    active 
    rem === 2. Windows Partition ====================
    rem ==    a. Create Windows partition ===========
    create partition primary 
    rem ==    b. Create space for Windows RE tools partition ====
    shrink minimum=450
    rem ==    c. Prepare the Windows partition ======
    format quick fs=ntfs label="Windows" 
    assign letter="W" 
    rem === 3. Windows RE Tools Partition =============
    create partition primary
    format quick fs=ntfs label="Windows RE tools"
    set id=27
    assign letter="R" 
    exit
    ```

2.  Nennen Sie das Skript CreatePartitions UEFI oder CreatePartitions BIOS.txt, und speichern Sie sie an einem Netzwerkspeicherort oder USB-Laufwerk. Hinweis: In diesen Beispielen Diskpart Partitionen zugewiesenen die Buchstaben S:\\, W:\\, und T:\\ Partition Kennung zu vereinfachen. Nach dem Neustart des PCs-Option automatisch weist den Buchstaben C: Windows PE\\ in der Windows-Partition. Die anderen Partitionen empfangen keine Laufwerkbuchstaben.

**Schritt 8: Erstellen eines Diskpart-Skripts für die bare-Metal-Wiederherstellung (optional)**

**Schritt 8: Erstellen eines Diskpart-Skripts für die bare-Metal-Wiederherstellung (optional)**

1.  Erstellen Sie ein Diskpart-Skript für die bare-Metal-Wiederherstellung.

    **Wichtige** Das Diskpart-Skript zum bare-Metal-Recovery sollte nicht enthalten eine `select disk` oder `clean` Befehl. Der Systemdatenträger wird automatisch vor der Verarbeitung des Diskpart-Skripts ausgewählt.

    **UEFI-Beispiel**:

    ``` syntax
    rem These commands are used with DiskPart tool.
    rem Erase the drive and create five partitions
    rem for a UEFI/GPT-based PC.
    convert gpt
    rem == 1. System Partition =======================
    create partition efi size=100
    rem ***NOTE: For 4KB-per-sector drives, change 
    rem this value to size=260.***
    format quick fs=fat32 label="System"
    assign letter="S"
    rem == 2. Microsoft Reserved (MSR) Partition =====
    create partition msr size=16
    rem == 3. Windows Partition ======================
    rem ==    a. Create Windows Partition ============
    create partition primary
    rem ==    b. Create space for Windows RE tools partition
    shrink minimum=450
    rem ==    c. Prepare the Windows partition
    format quick fs=ntfs label="Windows"
    assign letter="W"
    rem == 4. Windows RE Tools Partition =============
    create partition primary
    format quick fs=ntfs label="Windows RE tools"
    set id=de94bba4-06d1-4d40-a16a-bfd50179d6ac
    assign letter="T"
    exit
    ```
    
    **BIOS-Beispiel**:

    ``` syntax
    rem These commands are used with DiskPart to 
    rem erase the drive and create three partitions 
    rem for a BIOS/MBR-based PC. 
    rem Adjust the partition sizes to fill the drive.
    rem === 1. System Partition =====================
    create partition primary size=100
    format quick fs=ntfs label="System"
    assign letter="S" 
    active 
    rem === 2. Windows Partition ====================
    rem ==    a. Create Windows partition ===========
    create partition primary 
    rem ==    b. Create space for Windows RE tools partition ====
    shrink minimum=450
    rem ==    c. Prepare the Windows partition ======
    format quick fs=ntfs label="Windows" 
    assign letter="W" 
    rem === 3. Windows RE Tools Partition =============
    create partition primary
    format quick fs=ntfs label="Windows RE tools"
    set id=27
    assign letter="R" 
    exit
    ```

2.  Nennen Sie das Skript RecreatePartitions UEFI.txt oder RecreatePartitions BIOS.txt, und speichern Sie diese auf den gleichen Netzwerkspeicherort oder USB flash-Laufwerk Partitionen zu erstellen.

**Schritt 9: Bereitstellen und Anpassen von Windows**

1.  Starten Sie auf dem Ziel-PC Windows PE.
2.  Führen Sie an der Eingabeaufforderung Windows PE das Skript aus, um die empfohlene Festplattenpartitionen zu erstellen.

    ``` syntax
    Diskpart /s N:\CreatePartitions.txt
    ```

    wobei N:\\CreatePartition ist der Speicherort der Datei.

3.  Wenden Sie das Windows-Referenz-Abbild auf die Windows-Partition.

    ``` syntax
    Dism /Apply-Image /ImageFile:N:\Install.wim /Index:1 /ApplyDir:W:\
    ```

    Optional: Sie können auch die konvertierte angeben Option, damit die Dateien auf Datenträger komprimiert werden. Beispiel:

    ``` syntax
    Dism /Apply-Image /ImageFile:N:\Install.wim /Index:1 /ApplyDir:W:\ /Compact:on
    ```

    Dies ist nützlich, wenn Sie Windows auf PCs mit begrenzter Speicherkapazität bereitstellen, aber nicht auf PCs mit Rotation Speichergeräten empfohlen werden.

4.  Konfigurieren der Systempartition mithilfe von BCDboot.

    ``` syntax
    W:\Windows\System32\Bcdboot W:\Windows
    ```

5.  Erstellen Sie einen Ordner in der Windows RE-Tools Partition, und kopieren Sie Ihre Windows RE Boot-Abbild hinzu.

    ``` syntax
    Mkdir T:\Recovery\WindowsRE
    xcopy /H N:\Winre.wim T:\Recovery\WindowsRE
    ```

    in dem T:\\ ist die Windows RE-Tools Partition.

    **Wichtige**  Sie müssen Winre.wim in speichern \\Wiederherstellung\\WindowsRE.

     

6.  Registrieren Sie Windows RE Boot Image zusammen mit dem Windows-Abbild.

    ``` syntax
    W:\Windows\System32\Reagentc /setreimage /path T:\Recovery\WindowsRE /target W:\Windows
    ```

7.  Verwenden Sie Diskpart, um die Windows RE-Tools zu verbergen (T:\\) Partition aus Windows Explorer.

    **Für UEFI-basierte PCs:**

    ``` syntax
    select disk 0
    select partition 4
    remove
    set id=de94bba4-06d1-4d40-a16a-bfd50179d6ac
    gpt attributes=0x8000000000000001
    exit
    ```

    **Für BIOS-basierte PCs:**

    ``` syntax
    select disk 0
    select partition 3
    remove
    set id=27
    exit
    ```

8.  Anpassen des Windows-Abbilds auf den Ziel-PC:
    1.  Führen Sie offline angepasst werden, um das Windows-Abbild, wie bestimmte INF-basierte Treiberpakete an das Ziel PC installieren, OS Updates und Language Packs installieren oder Bereitstellung zusätzliche apps für Windows.
    2.  Starten Sie den Ziel-PC im Überwachungsmodus. Dies erfolgt mithilfe einer Antwortdatei mit Microsoft-Windows-Deployment | Reseal | Mode = Audit Einstellung, oder durch erste PC OOBE starten, und drücken Sie dann STRG + UMSCHALT + F3.
    3.  Führen Sie alle verbleibenden Anpassungen wie Installieren von Anwendungen und Gerät Softwarepakete, die an das Ziel PC spezifisch sind.

9.  Wenn Sie OS Updates installiert haben, bereinigen Sie die ersetzten Komponenten und markieren Sie die Updates als permanente, sodass sie während der Wiederherstellung wiederhergestellt werden sollen:

    ``` syntax
    DISM.exe /Cleanup-Image /StartComponentCleanup /ResetBase
    ```

**Schritt 10: Erfassen und Bereitstellen von Anpassungen für die Wiederherstellung**

1.  Verwenden Sie das Tool ScanState die installierten Anpassungen in einer Bereitstellung Paket erfasst. Verwenden Sie die Option/config zum Angeben der Konfigurationsdatei, die Sie geändert in Schritt 1 weiter oben in diesem Thema aus, und speichern Sie die Datei .ppkg im Ordner C:\\Wiederherstellung\\Anpassungen.

    ``` syntax
    D:\ScanState_amd64\scanstate.exe /apps /config:<path_to_config_file> /ppkg C:\Recovery\Customizations\apps.ppkg /o /c /v:13 /l:C:\ScanState.log
    ```

    wobei N:\\ ist der Speicherort des in Schritt 1 installierten ScanState Tools.

2.  Wenn Sie zusätzliche Bereitstellung mit Anpassungen erstellen, die während der Wiederherstellung wiederhergestellt werden sollte Windows ICD verwendet haben, kopieren Sie die Pakete an das Ziel PC. Beispiel:

    ``` syntax
    xcopy N:\RecoveryPPKG\*.ppkg C:\Recovery\Customizations
    ```

    wobei N:\\ ist der Speicherort, in dem sich die Bereitstellung zusätzlicher Pakete befinden.

3.  Kopieren Sie alle Drucktaste Reset-Konfigurationsdatei (resetconfig.xml) und Erweiterbarkeit Skripts in den Ziel-PC, und konfigurieren Sie anschließend Berechtigungen zum Schreiben/sie ändern. Beispiel:

    ``` syntax
    mkdir C:\Recovery\OEM
    xcopy /E N:\RecoveryScripts\* C:\Recovery\OEM
    ```

    wobei N:\\ ist der Speicherort, in dem sich die Konfigurationsdatei und Skripts befinden.

4.  Sollten Sie die Write/Modify Berechtigungen der Anpassungen und blenden Sie im Stammordner aus. Beispiel:

    ``` syntax
    icacls C:\Recovery\Customizations /inheritance:r /T
    icacls C:\Recovery\Customizations /grant:r SYSTEM:(F) /T
    icacls C:\Recovery\Customizations / grant:r *S-1-5-32-544:(F) /T
    icacls C:\Recovery\OEM /inheritance:r /T
    icacls C:\Recovery\OEM /grant:r SYSTEM:(F) /T
    icacls C:\Recovery\OEM / grant:r *S-1-5-32-544:(F) /T
    attrib +H C:\Recovery
    ```

5.  Verwenden Sie das Tool Sysprep ohne Verwendung das Windows-Abbild erneut versiegeln der / die Option verallgemeinern.

    ``` syntax
    Sysprep /oobe /exit
    ```

    **Hinweis**  Wichtig: Sie müssen das Bild konfigurieren, das Sie für den Kunden OOBE starten ausgeliefert werden.

     

6.  (Optional) Um Speicherplatz zu sparen, können Sie auch Ihre installierten Windows-desktopanwendungen in Datei Zeiger verweisen auf das Paket Anpassungen konvertieren. Hierzu starten Sie das Ziel PC zu Windows PE, und führen Sie folgenden Befehl:

    ``` syntax
    DISM /Apply-CustomDataImage /CustomDataImage:C:\Recovery\Customizations\USMT.ppkg /ImagePath:C:\ /SingleInstance
    ```

7.  Fahren Sie den Ziel-PC für das Packen und Lieferung herunter. Wenn der Benutzer den PC zum ersten Mal startet, wird es von OOBE gestartet.

**Schritt 11: Überprüfen Sie, ob die Anpassungen**

1.  Stellen Sie sicher, dass Ihre Anpassungen nach der Wiederherstellung wiederhergestellt werden und sie weiterhin funktionieren nach der Aktualisierung Ihrer PC ausführen und Zurücksetzen Ihrer PC-Funktionen, die folgenden Einstiegspunkte:

    **Einstellungen:** Klicken Sie im Menü Start auf **Einstellungen &gt; Update & Sicherheit &gt; Wiederherstellung**. Klicken Sie auf die Schaltfläche " **Erste Schritte** " unter **diesem PC zurücksetzen** , und befolgen Sie die auf dem Bildschirm Anweisungen.

    **Windows RE**: Klicken Sie auf ein Option Bildschirm in Windows RE, aus der wählen **Troubleshoot &gt; Zurücksetzen dieser PC** und führen Sie dann die auf dem Bildschirm Anweisungen

2.  **Stellen Sie sicher, Wiederherstellungsmedien können erstellt werden, und überprüfen Sie seine Funktionalität durch das Feature bare-Metal-Recovery ausführen:**

    1.  Erstellen einer Wiederherstellungslaufwerk über die Systemsteuerung zu starten.
    2.  Führen Sie die auf dem Bildschirm Anweisungen zum Erstellen des Wiederherstellung USB-Laufwerks.
    3.  Starten Sie den Computer aus der Wiederherstellung USB-Laufwerk
    4.  Vom Bildschirm Option auswählen klicken Sie auf **Problembehandlung**
    5.  Klicken Sie auf **einem Laufwerk wiederherstellen** , und führen Sie dann die auf dem Bildschirm Anweisungen

    **Hinweis**  Zurücksetzen des Drucktaste Benutzeroberfläche wurde in Windows 10 überarbeitet. Meine Dateien Option **beibehalten** auf der Benutzeroberfläche jetzt entspricht das **Aktualisieren von Ihrem PCs** -Feature während der das Feature **PC zurücksetzen** die Option **Entfernen Sie alles** entspricht.

     

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[ScanState-Syntax](http://go.microsoft.com/fwlink/p/?linkid=615076)

[Bare-Metal Reset-Recovery: Erstellen von Wiederherstellungsmedien beim Bereitstellen neuer Geräte](create-media-to-run-push-button-reset-features-s14.md)

[Bereitstellen von ScanState Drucktaste zurücksetzen-features](http://go.microsoft.com/fwlink/?LinkId=615126)

 

 






