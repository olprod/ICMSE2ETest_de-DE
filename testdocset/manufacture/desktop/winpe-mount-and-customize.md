---
author: Justinha
Description: 'Windows PE: Bereitstellen und anpassen'
ms.assetid: 5d5c13e8-8754-4fff-afd1-dcc3fb757bb9
MSHAttr: PreferredLib:/library/windows/hardware
title: 'Windows PE: Bereitstellen und anpassen'
ms.openlocfilehash: 5283cbb0c827a3909a98203f232d270cd5ba70f1
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="winpe-mount-and-customize"></a>Windows PE: Bereitstellen und anpassen


Hinzufügen von Treibern zu Windows Vorinstallation Environment (Windows PE), wie Grafiktreiber oder Netzwerk-Treiber.

Allgemeine Anpassungen:

-   [Hinzufügen von Gerätetreibern (INF-Dateien)](winpe-add-drivers.md). Sie können Gerätetreibern, wie Treiber anpassen, die Netzwerkkarten oder Speichergeräten unterstützen.
-   [Add-Pakete (CAB-Dateien, auch bekannt als Windows PE optionale Komponenten)](winpe-add-packages--optional-components-reference.md) Hinzufügen von Sprachen, Hotfixes oder Unterstützung für Features wie PowerShell und der HTML-Anwendung Sprache (HTA).
-   [Hinzufügen einer Sprache](winpe-add-packages--optional-components-reference.md). Wenn Windows PE in mehreren Sprachen ausgeführt werden soll, fügen Sie der (optionalen Komponenten)-Pakete für diese Sprachen hinzu.
-   Hinzufügen von Dateien und Ordnern. Diese können direkt an das Windows PE-Abbild hinzugefügt werden.
-   [Hinzufügen einer neueren Version von DISM](copy-dism-to-another-computer.md). Wenn neue Versionen der Windows-Funktionen, die neueste Version von DISM benötigen, können Sie direkt in Windows PE DISM hinzufügen.
-   [Hinzufügen eines Skripts zum Starten](#addstartupscript). Beispiele: Einrichten einer Netzwerkverbindung oder Hinzufügen einer benutzerdefinierten Anwendung, wie beispielsweise Diagnostics-Software.
-   [Fügen Sie eine app hinzu](#addapp). Beachten Sie, dass Windows PE unterstützt nur die Vorversion apps.
-   [Temporäre Speicher hinzufügen (Scratch Leerzeichen)](#scratchspace). Wenn Ihre Anwendung temporäre Dateispeicher erforderlich ist, können Sie zusätzlichen Arbeitsspeicher Platz im RAM reservieren.
-   [Ersetzen Sie das Hintergrundbild](#addwallpaper)
-   [Hinzufügen von Einstellungen für den Antwort](#addanswerfilesettings)

**Abrufen von Windows Assessment and Deployment Kit mit Windows PE-tools**

-   Installieren Sie [Windows Assessment and Deployment Kit (Windows ADK) technische Referenz](http://go.microsoft.com/fwlink/p/?LinkId=526803), einschließlich des **Windows PE** -Features.

**Erstellen eines Satzes von 32-Bit oder 64-Bit-Windows PE-Dateien**

1.  Klicken Sie auf **Start**, und geben Sie die **Bereitstellung**. Mit der rechten Maustaste **Bereitstellung und Imaging Tools Umgebung** , und wählen Sie dann auf **als Administrator ausführen**.

2.  Kopieren Sie in der **Bereitstellungstools und Imaging-Umgebung**die Windows PE-Dateien für die PCs, die Sie starten möchten.

    -   Die 64-Bit-Version kann UEFI 64-Bit- und 64-Bit-BIOS PCs starten.

        ``` syntax
        copype amd64 C:\WinPE_amd64
        ```

    -   Die 32-Bit-Version von Windows PE kann 32-Bit-UEFI, BIOS-32-Bit- und 64-Bit-BIOS PCs starten.

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

-   Hinzufügen von den Gerätetreiber zum Windows PE-Abbild.

    ``` syntax
    Dism /Add-Driver /Image:"C:\WinPE_amd64\mount" /Driver:"C:\SampleDriver\driver.inf"
    ```

    Obwohl Sie mehrere Treiber für ein Bild mit einem einzigen Befehl hinzufügen können, ist es oft einfacher zur Behandlung von Problemen durch jedes Paket einzeln hinzufügen.

    Weitere Informationen zum Treiber finden Sie unter [Add Gerätetreiber (INF-Dateien)](winpe-add-drivers.md).

**Pakete/Sprachen/optionalen Komponenten CAB-Dateien hinzufügen**

-   Fügen Sie die optionale Komponente Windows PE hinzu. Wenn optionale Komponenten hinzufügen möchten, müssen Sie die optionale Komponente und der zugeordneten Sprachpakete hinzufügen.

    ``` syntax
    Dism /Add-Package /Image:"C:\WinPE_amd64\mount" /PackagePath:"C:\Program Files\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\WinPE-HTA.cab"  

    Dism /Add-Package /Image:"C:\WinPE_amd64\mount" /PackagePath:"C:\Program Files\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\en-us\WinPE-HTA_en-us.cab"
    ```

    Weitere Informationen zum Hinzufügen von Paketen, finden Sie unter [Windows PE: Hinzufügen von Paketen (optionalen Komponenten Verweis)](winpe-add-packages--optional-components-reference.md).

**Hinzufügen von Dateien und Ordnern**

-   Kopieren von Dateien und Ordner in der C:\\Windows PE\_amd64\\Mount-Ordner. Diese Dateien werden angezeigt, in der X:\\ Ordner in Windows PE.

    Fügen Sie nicht zu viele Dateien hinzu, wie diese verlangsamt Windows PE und können Sie den verfügbaren Speicherplatz in der Standardeinstellung RAMDisk Umgebung ausfüllen.

<span id="AddStartupScript"></span><span id="addstartupscript"></span><span id="ADDSTARTUPSCRIPT"></span>
**Hinzufügen eines Skripts zum Starten**

-   Ändern Sie das Startnet.cmd-Skript aus, um die benutzerdefinierten Befehle einzuschließen. Diese Datei befindet sich unter `C:\WinPE_amd64\mount\Windows\System32\Startnet.cmd`.

    Sie können auch andere Batchdateien oder eine Befehlszeile Skripts aus dieser Datei aufrufen.

    Plug & Play oder Netzwerke Support stellen Sie sicher, dass Sie einen Anruf an **Wpeinit** in Ihrer benutzerdefinierten Startnet.cmd Skripts einschließen. Weitere Informationen finden Sie unter [Wpeinit und Startnet.cmd: Verwenden von Windows PE zum Starten des Skripts](wpeinit-and-startnetcmd-using-winpe-startup-scripts.md).

<span id="AddApp"></span><span id="addapp"></span><span id="ADDAPP"></span>
**Fügen Sie eine app hinzu**

1.  Erstellen eines app-Verzeichnis innerhalb der bereitgestellten Windows PE-Abbild.

    ``` syntax
    md "C:\WinPE_amd64\mount\windows\<MyApp>"
    ```

2.  Kopieren Sie die erforderlichen app-Dateien in das lokale Windows PE-Verzeichnis.

    ``` syntax
    Xcopy C:\<MyApp> "C:\WinPE_amd64\mount\windows\<MyApp>"
    ```

3.  Testen der app später durch Starten von Windows PE und die Anwendung aus dem Verzeichnis X: ausführen.

    ``` syntax
    X:\Windows\System32> X:\Windows\<MyApp>
    ```

    Wenn Ihre app temporärer Speicher erforderlich ist, oder Windows PE nicht mehr reagiert, wenn sie eine app ausgeführt wird, müssen Sie die Erhöhung des temporärer Speicher (Scratch Leerzeichen), Windows PE zugewiesen ist.

4.  Automatisch gestartet, ein Shell oder eine Anwendung, die ausgeführt wird, wenn Windows PE wird gestartet, fügen Sie den Pfad zur Datei Winpeshl.ini. Weitere Informationen finden Sie unter [Winpeshl.ini Verweis: Starten eine app beim Start von Windows PE](winpeshlini-reference-launching-an-app-when-winpe-starts.md).

<span id="ScratchSpace"></span><span id="scratchspace"></span><span id="SCRATCHSPACE"></span>
**Hinzufügen von temporären Speicher (Scratch Leerzeichen)**

-   Windows PE reserviert Arbeitsspeicher auf dem Laufwerk X: Entpacken der Windows PE-Dateien sowie zusätzliche temporäre Dateispeicher, bezeichnet als Scratch Leerzeichen, die von der Anwendung verwendet werden kann. Dies ist 512MB für PCs mit mehr als 1GB RAM werden standardmäßig, andernfalls ist der Standardwert 32MB. Gültige Werte sind 32, 64, 128, 256 oder 512.

    ``` syntax
    Dism /Set-ScratchSpace:256 /Image:"C:\WinPE_amd64\mount"
    ```

<span id="AddWallpaper"></span><span id="addwallpaper"></span><span id="ADDWALLPAPER"></span>
**Ersetzen Sie das Hintergrundbild**

1.  Wenn Sie mehrere Versionen von Windows PE haben, können Sie das Hintergrundbild festlegen, sodass Sie sofort erkennen können, welche Version von Windows PE ausgeführt wird.

    Ändern der Sicherheitsberechtigungen der Bilddatei Windows PE Hintergrund (`\windows\system32\winpe.jpg`). Dadurch können Sie zum Ändern oder löschen Sie die Datei.

    1.  Navigieren Sie in Windows Explorer zu `C:\WinPE_amd64\mount\windows\system32`.

    2.  Mit der rechten Maustaste die `C:\WinPE_amd64\mount\windows\system32\winpe.jpg` Datei, und wählen Sie **Eigenschaften** aus &gt; Registerkarte **Sicherheit** &gt; **Erweitert**.

    3.  Aktivieren Sie neben Besitzer **Ändern**. Ändern des Besitzers für **Administratoren**.

    4.  Übernehmen Sie die Änderungen zu, und beenden Sie das Fenster Eigenschaften, um die Änderungen zu speichern.

    5.  Mit der rechten Maustaste die `C:\WinPE_amd64\mount\windows\system32\winpe.jpg` Datei, und wählen Sie **Eigenschaften** aus &gt; Registerkarte **Sicherheit** &gt; **Erweitert**.

    6.  Ändern der Berechtigungen **Administratoren** vollen Zugriff zulassen.

    7.  Übernehmen Sie die, und beenden Sie das Fenster Eigenschaften, um die Änderungen zu speichern.

2.  Ersetzen Sie die `winpe.jpg` -Datei mit Ihrer eigenen Bilddatei an.

<span id="AddAnswerFileSettings"></span><span id="addanswerfilesettings"></span><span id="ADDANSWERFILESETTINGS"></span>
**Hinzufügen von Einstellungen für den Antwort**

-   Einige Einstellungen Windows PE können mithilfe einer Antwortdatei, wie Firewall, Netzwerk und Anzeigeeinstellungen verwaltet werden. Erstellen einer Antwortdatei, nennen Sie sie unattend.xml, und fügen Sie es in den Stamm des Windows PE Mediums zum Verarbeiten dieser Einstellungen. Weitere Informationen finden Sie unter [Wpeinit und Startnet.cmd: Verwenden von Windows PE zum Starten des Skripts](wpeinit-and-startnetcmd-using-winpe-startup-scripts.md).

**Windows PE-Abbild entladen und Erstellen von Medien**

1.  Heben Sie die Bereitstellung des Windows PE-Abbildes.

    ``` syntax
    Dism /Unmount-Image /MountDir:"C:\WinPE_amd64\mount" /commit
    ```

2.  Erstellen von startbaren Medien, wie ein USB-Laufwerk.

    ``` syntax
    MakeWinPEMedia /UFD C:\WinPE_amd64 F:
    ```

3.  Die Medien zu starten. Windows PE wird automatisch gestartet. Nachdem das Windows PE-Fenster angezeigt wird, wird der Befehl Wpeinit automatisch ausgeführt. Dies kann einige Minuten dauern. Überprüfen Sie die Anpassungen aus.

## <a name="span-idtroubleshootingspanspan-idtroubleshootingspanspan-idtroubleshootingspantroubleshooting"></a><span id="Troubleshooting"></span><span id="troubleshooting"></span><span id="TROUBLESHOOTING"></span>Problembehandlung


-   Windows PE wird nicht gestartet? Finden Sie die Tipps zur Problembehandlung am Ende des Themas: [Windows PE: Erstellen startbaren USB-Laufwerk](winpe-create-usb-bootable-drive.md)
-   Tipps zum Herstellen einer Verbindung mit einem Netzwerk finden Sie unter [Windows PE-Netzwerk-Treiber: Initialisieren und Hinzufügen von Treibern](winpe-network-drivers-initializing-and-adding-drivers.md).
-   Wenn das Windows PE-Image nicht verarbeitbare ist, müssen Sie die Bilder bereinigen, bevor Sie das Abbild erneut bereitstellen zu können. Informationen finden Sie unter [Reparieren einer Windows-Abbild](repair-a-windows-image.md).

### <a name="span-idtodeleteaworkingdirectoryspanspan-idtodeleteaworkingdirectoryspanspan-idtodeleteaworkingdirectoryspanto-delete-a-working-directory"></a><span id="To_delete_a_working_directory_"></span><span id="to_delete_a_working_directory_"></span><span id="TO_DELETE_A_WORKING_DIRECTORY_"></span>Um einem Arbeitsverzeichnis zu löschen:

In einigen Fällen können Sie nicht das bereitgestellte Abbild wiederherstellen sein. DISM schützt Sie vor versehentlich Arbeitsverzeichnis, sodass Sie möglicherweise die folgenden Schritte aus, um Zugriff auf das bereitgestellte Verzeichnis zu löschen versuchen. Versuchen Sie es mit den folgenden Schritten:

1.  Erneutes Bereitstellen des Abbilds Try:

    ``` syntax
    dism /Remount-Image /MountDir:C:\mount
    ```

2.  Versuchen Sie, Aufheben der Bereitstellung des Bilds, die Änderungen zu verwerfen:

    ``` syntax
    dism /Unmount-Image /MountDir:C:\mount /discard
    ```

3.  Versuchen Sie, bereinigen die bereitgestellten Abbild zugeordneten Ressourcen:

    ``` syntax
    dism /Cleanup-Mountpoints
    ```

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen

[Windows PE: Optimieren der Leistung und das Bild zu reduzieren](winpe-optimize.md)

[Windows PE für Windows 10](winpe-intro.md)

[Windows PE: Erstellen von startbaren USB-Laufwerk](winpe-create-usb-bootable-drive.md)

[Windows PE: Erstellen einer Boot-CD, DVD, ISO oder virtuelle Festplatte](winpe-create-a-boot-cd-dvd-iso-or-vhd.md)

[Windows PE: Installieren auf einer Festplatte (flach Boot oder nicht-RAM)](winpe-install-on-a-hard-drive--flat-boot-or-non-ram.md)

[Windows PE: Boot in UEFI oder BIOS-Legacymodus](winpe-boot-in-uefi-or-legacy-bios-mode.md)

[Windows PE: Hinzufügen von Paketen (optionalen Komponenten Reference (engl.)](winpe-add-packages--optional-components-reference.md)

 

 






