---
author: KPacquer
Description: "Hinzufügen von Updates, und aktualisieren Sie die Edition."
ms.assetid: 9a8f525c-bb8f-492c-a555-0b512e44bcd1
MSHAttr: PreferredLib:/library/windows/hardware
title: "Übung 4: Hinzufügen von Updates und Upgraden Sie die edition"
ms.openlocfilehash: 05e2029fca31dfb47457f8b6d7c44758b84a753b
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="lab-4-add-updates-and-upgrade-the-edition"></a>Übung 4: Hinzufügen von Updates und Upgraden Sie die edition

Für viele Anpassungen, wie das Hinzufügen von Treibern INF-Schreibweise Windows-updates oder aktualisieren die Edition, bereitstellen und bearbeiten Sie das Windows-Abbild. Bereitstellen eines Abbilds ordnet dem Inhalt einer Datei in ein temporäres Verzeichnis, in dem die Dateien bearbeiten oder mithilfe von DISM häufige Bereitstellungsaufgaben ausgeführt.

**Notizen** 

* Hinzufügen von Updates vor dem Hinzufügen von Sprachen. Wenn Sie Sprachen bereits hinzugefügt haben, Ihr Bild und dann nach dem Hinzufügen des Updates, wechseln Sie zurück, und [Fügen Sie Ihre Sprache erneut](add-drivers-langs-universal-apps-sxs.md).

-  **Aktualisieren Sie für wichtige Updates-Image für die Wiederherstellung zu**: beinhalten kann Hotfixes, allgemein verfügbare Versionen, Servicepacks oder andere Vorabversionen. Zeigen wir Ihnen diese aktualisieren später in [Übung 10: Aktualisieren der Wiederherstellung](update-the-recovery-image.md).

-  **– Wartung Stack Update (SSU): ist erforderlich,[KB3199209](http://www.catalog.update.microsoft.com/Search.aspx?q=KB3199209) ** vor dem Anwenden der neuesten General Distribution Release (GDR, derzeit KB3200970) oder alle zukünftigen GDRs.

![Bild: Bilddateien und Bereitstellungsskripts kopieren](images/dep-win8-sxs-createmodelspecificfiles.jpg)

Hinweis: Treiber, ein Installationspaket enthalten, finden Sie unter [Übung 12: Hinzufügen von desktopanwendungen und Einstellungen mit Silos zusammengefasst provisioning Pakete (SPPs)](add-desktop-apps-wth-spps-sxs.md)

## <a name="span-idmounttheimagespanmount-the-image"></a><span id="Mount_the_image"></span>Bereitstellen des Abbilds

**Schritt 1: Stellen Sie das Abbild**

Die Schritte von [Übung 3: Hinzufügen von Gerätetreibern (INF-Schreibweise)](add-device-drivers.md) , das Bild bereitzustellen. Die Kurzversion:

1.  Öffnen Sie die Befehlszeile als Administrator (**Start** > geben **Bereitstellung** > mit der rechten Maustaste **Bereitstellung und Imaging Tools Umgebung** > **als Administrator ausführen**.)

2.  Erstellen Sie eine Sicherungskopie der Datei (`copy "C:\Images\Win10_x64\sources\install.wim" C:\Images\install-backup.wim`)

3.  Stellen Sie das Abbild (`md C:\mount\windows`, klicken Sie dann `Dism /Mount-Image /ImageFile:"C:\Images\install.wim" /Index:1 /MountDir:"C:\mount\windows" /Optimize`)

## <a name="span-idaddcustomizationstotheimagespanadd-customizations-to-the-image"></a><span id="Add_customizations_to_the_image"></span>Hinzufügen von Anpassungen auf das Bild
    
**Schritt 2: Aktualisieren der Edition von zu Hause mit Pro**

Verwenden Sie dieses Verfahren, um die Edition zu aktualisieren. Ein Windows-Bild kann nicht auf eine niedrigere Edition festgelegt werden. Sie sollten dieses Verfahren nicht auf ein Bild verwenden, die bereits auf eine höhere Edition geändert wurde.

1.  Bestimmen, welche Bilder Sie das Bild aktualisieren können: Beachten Sie die Edition IDs verfügbar.

    ``` syntax
    Dism /Get-TargetEditions /Image:C:\mount\windows
    ```

2.  Aktualisieren der Edition.

    ``` syntax
    Dism /Set-Edition:Professional /Image:C:\mount\windows
    ```
    
**Schritt 3: Hinzufügen eines Windows Update-Pakets**

1.  Rufen Sie ein Windows Update-Paket. Nehmen Sie beispielsweise das neueste kumulative Update in [Windows-10-Updateverlauf](https://support.microsoft.com/en-us/help/12387/windows-10-update-history) aus dem [Microsoft Update-Katalog](http://www.catalog.update.microsoft.com)aufgelistet. Extrahieren Sie das Update des MSU-Datei in einen Ordner, beispielsweise C:\\WindowsUpdates\\windows10.0-kb3194798-x64_8bc6befc7b3c51f94ae70b8d1d9a249bb4b5e108.msu.

2.  Fügen Sie die Updates auf das Bild ein. Pakete mit Abhängigkeiten Vergewissern Sie sich, dass Sie die Pakete in Reihenfolge installieren. Wenn Sie nicht die Abhängigkeiten sicher sind, ist es OK, um alle im selben Ordner ablegen, und fügen sie alle mit demselben DISM/Add-Package Befehl durch mehrere/PackagePath Elemente hinzufügen.

    Beispiel: Hinzufügen eines kumulierten Updates:

    ``` syntax
    Dism /Add-Package /Image:"C:\mount\windows" /PackagePath="C:\WindowsUpdates\windows10.0-kb3194798-x64_8bc6befc7b3c51f94ae70b8d1d9a249bb4b5e108.msu"  /LogPath=C:\mount\dism.log
    ```

    Beispiel: Hinzufügen von mehreren Updates:

    ``` syntax
    Dism /Add-Package /Image:"C:\mount\windows" /PackagePath="C:\WindowsUpdates\windows10.0-kb00001-x64.msu" /PackagePath="C:\WindowsUpdates\windows10.0-kb00002-x64.msu" /PackagePath="C:\WindowsUpdates\windows10.0-kb00003-x64.msu" /LogPath=C:\mount\dism.log
    ```

3.  Sperren Sie in den Updates, sodass sie während einer Wiederherstellung wiederhergestellt werden. 

    ``` syntax
    DISM /Cleanup-Image /Image=C:\ /StartComponentCleanup /ResetBase /ScratchDir:C:\Temp
    ```

## <a name="span-idunmounttheimagespanunmount-the-image"></a><span id="Unmount_the_image"></span>Heben Sie die Bereitstellung des Abbilds
    
**Schritt 4: Heben Sie die Bereitstellung der Bilder**

1.  Schließen Sie alle Programme, die Dateien aus dem Bild zugreifen können.

2.  Commit der Änderungen, und heben Sie die Bereitstellung des Windows-Abbilds:

    ``` syntax
    Dism /Unmount-Image /MountDir:"C:\mount\windows" /Commit
    ```

## <a name="span-idtryitoutspantry-it-out"></a><span id="Try_it_out"></span>Probieren Sie es aus

**Schritt 5: Wenden Sie das Abbild auf einen neuen PC**

Verwenden Sie die Schritte auf [Übung 2: Bereitstellen von Windows mithilfe eines Skripts](deploy-windows-with-a-script-sxs.md) um das Bild auf den Speicher, USB-Laufwerk zu kopieren, wenden Sie das Abbild, und starten. Die Kurzversion:

1.  Kopieren Sie die Bilddatei mit dem Speicherlaufwerk.
2.  [Verweis Gerät, um mit dem Windows PE USB-Schlüssel Windows PE starten](install-windows-pe-sxs.md).
3.  Suchen Sie nach der Laufwerkbuchstabe des Laufwerks Speicher (`diskpart, list volume, exit`).
4.  Wenden Sie das Abbild: `D:\ApplyImage.bat D:\Images\install.wim`.
5.  Trennen Sie die Laufwerke, und klicken Sie dann neu starten (`exit`).

**Schritt 6: Überprüfen Sie, ob updates**
1.  Nach dem Starten des PCs-Option, entweder ein neues Benutzerkonto zu erstellen, andernfalls Drücken von STRG + UMSCHALT + F3, in das integrierte Administratorkonto (Dies ist auch bekannt als Überwachungsmodus) neu starten.

2.  Klicken Sie mit der rechten Maustaste auf **Start** , und wählen Sie **die Befehlszeile (Admin)**.

3.  Stellen Sie sicher, dass die Edition korrekt ist:

    ``` syntax
    dism /online /get-currentedition
    ```

    Stellen Sie sicher, dass sie die richtige Edition ist. Beispiel:

    ``` syntax
    Current edition is:

    Current Edition : Professional

    The operation completed successfully.
    ```

4.  Stellen Sie sicher, dass die Pakete ordnungsgemäß angezeigt werden:

    ``` syntax
    Dism /Get-Packages /Online
    ```

    Überprüfen der resultierenden Liste der Pakete, und stellen Sie sicher, dass die Liste das Paket enthält. Beispiel:

    ``` syntax
    Package Identity : Package_for_RollupFix~31bf3856ad364e35~amd64~~14393.321.1.5
    State : Installed
    Release Type : Security Update
    Install Time : 10/13/2016 6:26 PM

    The operation completed successfully.
    ```

Nächster Schritt: [Übung 5: Hinzufügen von Sprachen](add-drivers-langs-universal-apps-sxs.md)