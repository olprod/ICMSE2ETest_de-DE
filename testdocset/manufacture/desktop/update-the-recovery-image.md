---
author: KPacquer
Description: "Übung 10: Aktualisieren der Wiederherstellung"
MSHAttr: PreferredLib:/library/windows/hardware
title: "Übung 10: Aktualisieren der Wiederherstellung"
ms.openlocfilehash: 519d03fde7b23981114450bc4af46e6e218f6cae
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="lab-10-update-the-recovery-image"></a>Übung 10: Aktualisieren der Wiederherstellung

Wenn das System nicht an das Windows-Abbild startet, wird es Windows Recovery Environment (WinRE) Failover auf. Häufige Ursachen für nicht startbaren Betriebssysteme kann WinRE repariert werden. WinRE basiert auf Windows Vorinstallation Environment (Windows PE), und Sie können für Ihre Kunden verwendet werden soll, hinzufügen, Treibern, Sprachen, Windows PE optionale Komponenten, und andere Problembehandlung und Diagnosetools. 

Das Bild WinRE innerhalb der Windows-10 und Windows Server 2016 Bilder enthalten ist, und schließlich auf die Windows RE-Tools-Partition auf dem Ziel-PC oder ein Gerät kopiert. Um sie zu ändern, müssen Sie stellen Sie das Windows-Abbild und dann stellen Sie das Abbild WinRE darin. Stellen Sie die Änderungen, heben Sie die Bereitstellung des WinRE Bilds, und heben Sie die Bereitstellung des Windows-Abbilds. 

   ![Bild: Stellen Sie das Windows-Abbild, und stellen Sie das Wiederherstellungsabbild darin. Nehmen Sie Änderungen vor, und klicken Sie dann entladen Sie der Wiederherstellungsabbild und schließlich auf dem Windows-Abbild](images/customize-recovery-image.jpg)

Aktualisieren Sie Ihre Recovery-Bild, um eine konsistente Recovery sicherstellen auftreten, wenn Sie:
* Hinzufügen von wichtigen INF-Schreibweise-Treibern wie die Treiber Grafiken und Speicher für [Übung 1: Installieren von Windows PE](install-windows-pe-sxs.md).
* Wichtige Updates für Windows, wie allgemein verfügbare Versionen hinzufügen ([Übung 4: Hinzufügen von Updates und Upgraden Sie die Edition](servicing-the-image-with-windows-updates-sxs.md)).   
* Hinzufügen neue Sprachen, wie Sie [Übung 5: Hinzufügen von Sprachen](add-drivers-langs-universal-apps-sxs.md).  (Dies ist nicht immer möglich, da nicht alle Sprachen Windows RE-Entsprechungen haben.)

 **Notes**  
 -  Diese Übungseinheit wird davon ausgegangen, dass Sie vielmehr winre.wim in install.wim auf die Sprachen und die Treiber synchron zu halten beibehalten möchten. Wenn Sie etwas Zeit in der Fabrik speichern möchten, und wenn Sie diese Bilder OK separat verwalten, empfiehlt es sich winre.wim aus diesem Abbild entfernen und angewendet wird getrennt.

-  Warten Stack Update (SSU):[KB3199209](http://www.catalog.update.microsoft.com/Search.aspx?q=KB3199209) muss vor dem Anwenden der neuesten General Distribution Release (GDR, derzeit KB3200970) oder alle zukünftigen GDRs.

## <a name="span-idmountthewindowsimagespanstep-1-mount-the-windows-image"></a><span id="Mount_the_Windows_image"></span>Schritt 1: Stellen Sie das Windows-Abbild

Verwenden Sie die Schritte auf [Übung 3: Hinzufügen von Gerätetreibern (INF-Format)](add-device-drivers.md) , das Windows-Abbild bereitzustellen. Die Kurzversion:

1.  Öffnen Sie die Befehlszeile als Administrator (**Start** > geben **Bereitstellung** > mit der rechten Maustaste **Bereitstellung und Imaging Tools Umgebung** > **als Administrator ausführen**.)

2.  Erstellen Sie eine Sicherungskopie der Datei (`copy "C:\Images\Win10_x64\sources\install.wim" C:\Images\install-backup.wim`)

3.  Stellen Sie das Abbild (`md C:\mount\windows`, klicken Sie dann `Dism /Mount-Image /ImageFile:"C:\Images\install.wim" /Index:1 /MountDir:"C:\mount\windows" /Optimize`)

## <a name="span-idmounttherecoveryimagespanstep-1-mount-the-recovery-image"></a><span id="Mount_the_recovery_image"></span>Schritt 1: Stellen Sie das Wiederherstellungsabbild

-   Binden Sie Windows RE Bilddatei an. 

    ``` syntax
    md C:\mount\winre
    ```

    ``` syntax
    Dism /Mount-Image /ImageFile:"C:\mount\windows\Windows\System32\Recovery\winre.wim" /Index:1 /MountDir:"C:\mount\winre"
    ```

    Dabei ist *C* der Laufwerkbuchstabe des Laufwerks, das das Bild enthält.

    Dieser Schritt kann einige Minuten dauern.

    **Problembehandlung**: Wenn winre.wim im angegebenen Verzeichnis nicht sichtbar ist, verwenden Sie den folgenden Befehl, um die Datei sichtbar festzulegen:

    `attrib -h -a -s C:\mount\windows\Windows\System32\Recovery\winre.wim`

## <a name="span-idadddriverstotheimagespanstep-3-add-boot-critical-drivers-to-winre"></a><span id="Add_drivers_to_the_image"></span>Schritt 3: Hinzufügen von wichtigen Treiber in WinRE

1.  Fügen Sie alle INF-Schreibweise Treiber für Ihre Hardware erforderlich ist.

    ``` syntax
    Dism /Add-Driver /Image:"C:\mount\winre" /Driver:"C:\Drivers\PnP.Media.V1\media1.inf" /LogPath=C:\mount\dism.log
    ```

## <a name="span-idaddupdatestotheimagespanstep-4-add-updates-to-the-image"></a><span id="Add_updates_to_the_image"></span>Schritt 4: Hinzufügen von Updates auf das Bild

1.  Rufen Sie ein Windows Update-Paket. Verwenden Sie das gleiche Update-Paket, die Sie für Windows in verwendet [Übung 4: Hinzufügen von Updates und Upgraden Sie die Edition](servicing-the-image-with-windows-updates-sxs.md). Nehmen Sie beispielsweise das neueste kumulative Update aufgeführt, die im [Verlauf von Windows 10 aktualisieren](https://support.microsoft.com/en-us/help/12387/windows-10-update-history) aus der (Microsoft Update-Katalog] (http://www.catalog.update.microsoft.com/). Extrahieren Sie das Update des MSU-Datei in einen Ordner, beispielsweise C:\\WindowsUpdates\\windows10.0-kb3194798-x64_8bc6befc7b3c51f94ae70b8d1d9a249bb4b5e108.msu.

2.  Fügen Sie der Updates das Bild hinzu. Pakete mit Abhängigkeiten Vergewissern Sie sich, dass Sie die Pakete in Reihenfolge installieren. Wenn Sie nicht sicher, dass der Abhängigkeiten sind, ist es OK, um alle im gleichen Ordner zu platzieren, und fügen Sie sie mithilfe einer Befehls/Add-Package DISM durch mehrere/PackagePath Elemente hinzufügen.

    Beispiel: Hinzufügen eines kumulierten Updates:

    ``` syntax
    Dism /Add-Package /Image:"C:\mount\winre" /PackagePath="C:\WindowsUpdates\windows10.0-kb3194798-x64_8bc6befc7b3c51f94ae70b8d1d9a249bb4b5e108.msu"  /LogPath=C:\mount\dism.log
    ```

    Beispiel: Hinzufügen von mehreren Updates:

    ``` syntax
    Dism /Add-Package /Image:"C:\mount\winre" /PackagePath="C:\WindowsUpdates\windows10.0-kb00001-x64.msu" /PackagePath="C:\WindowsUpdates\windows10.0-kb00002-x64.msu" /PackagePath="C:\WindowsUpdates\windows10.0-kb00003-x64.msu" /LogPath=C:\mount\dism.log
    ```

## <a name="span-idaddlanguagestotheimagespanstep-5-add-languages-to-the-image"></a><span id="Add_languages_to_the_image"></span>Schritt 5: Hinzufügen von Sprachen für das Bild

Wenn der PC-Option Probleme ausgeführt wird, ist Ihre Benutzer möglicherweise nicht in der Lese-/Wiederherstellung Bildschirmen verstehen, wenn Sie die entsprechenden Sprachressourcen WinRE hinzufügen.

1.  Hinzufügen von Sprachen. Diese Sprachen sind in der Windows-ADK enthalten. Sie müssen eine entsprechende Version von Windows ADK verwenden, die Windows RE-Abbild.

    **Hinweis**  Windows RE erfordert jetzt das Windows PE-HTA-Paket, dies ist neu in Windows 10.

    **Hinweis**  Das Windows PE-WLAN-Paket ist nicht sprachspezifische und muss nicht hinzugefügt werden, wenn andere Sprachen hinzufügen. Dies ist neu in Windows 10.

    ``` syntax
    Dism /Add-Package /image:C:\mount\winre /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\lp.cab" 

    Dism /Add-Package /image:C:\mount\winre /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\WinPE-Rejuv_fr-fr.cab"

    Dism /Add-Package /image:C:\mount\winre /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\WinPE-EnhancedStorage_fr-fr.cab"

    Dism /Add-Package /image:C:\mount\winre /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\WinPE-Scripting_fr-fr.cab"

    Dism /Add-Package /image:C:\mount\winre /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\WinPE-SecureStartup_fr-fr.cab"

    Dism /Add-Package /image:C:\mount\winre /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\WinPE-SRT_fr-fr.cab"

    Dism /Add-Package /image:C:\mount\winre /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\WinPE-WDS-Tools_fr-fr.cab"

    Dism /Add-Package /image:C:\mount\winre /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\WinPE-WMI_fr-fr.cab"

    Dism /Add-Package /image:C:\mount\winre /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\WinPE-StorageWMI_fr-fr.cab"

    Dism /Add-Package /image:C:\mount\winre /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\WinPE-HTA_fr-fr.cab"
    ```

2.  Legen Sie die Standardsprache für die Wiederherstellung die bevorzugte Sprache für Ihre Kunden übereinstimmen.

    ``` syntax
    Dism /Set-AllIntl:fr-fr /Image:C:\mount\winre
    ```

3.  Optional: Entfernen von Sprachen in Windows RE (nur für nicht-englischen Regionen erforderlich)

    Wenn Sie Windows Sprachen aufheben, entfernen Sie sie von Windows RE um Speicherplatz einzusparen.

    Sie können entweder den Schalter/PackagePath (was eine entsprechende Version von Windows und Windows ADK erfordert) oder der Option/PackageName (die erforderlich sind, identifizieren das Paket, einschließlich der Versionsnummer).

    Beispiel:

    ``` syntax
    Dism /Remove-Package /Image:"C:\mount\winre" /PackageName:WinPE-Rejuv-Package~31bf3856ad364e35~amd64~en-US~10.0.14393.0 /LogPath=C:\mount\dism.fod2.log
    Dism /Remove-Package /Image:"C:\mount\winre" /PackageName:WinPE-HTA-Package~31bf3856ad364e35~amd64~en-US~10.0.14393.0 /LogPath=C:\mount\dism.fod2.log
    Dism /Remove-Package /Image:"C:\mount\winre" /PackageName:WinPE-StorageWMI-Package~31bf3856ad364e35~amd64~en-US~10.0.14393.0 /LogPath=C:\mount\dism.fod2.log
    Dism /Remove-Package /Image:"C:\mount\winre" /PackageName:WinPE-WMI-Package~31bf3856ad364e35~amd64~en-US~10.0.14393.0 /LogPath=C:\mount\dism.fod2.log
    Dism /Remove-Package /Image:"C:\mount\winre" /PackageName:WinPE-WDS-Tools-Package~31bf3856ad364e35~amd64~en-US~10.0.14393.0 /LogPath=C:\mount\dism.fod2.log
    Dism /Remove-Package /Image:"C:\mount\winre" /PackageName:WinPE-SRT-Package~31bf3856ad364e35~amd64~en-US~10.0.14393.0 /LogPath=C:\mount\dism.fod2.log
    Dism /Remove-Package /Image:"C:\mount\winre" /PackageName:WinPE-SecureStartup-Package~31bf3856ad364e35~amd64~en-US~10.0.14393.0 /LogPath=C:\mount\dism.fod2.log
    Dism /Remove-Package /Image:"C:\mount\winre" /PackageName:WinPE-Scripting-Package~31bf3856ad364e35~amd64~en-US~10.0.14393.0 /LogPath=C:\mount\dism.fod2.log
    Dism /Remove-Package /Image:"C:\mount\winre" /PackageName:WinPE-EnhancedStorage-Package~31bf3856ad364e35~amd64~en-US~10.0.14393.0 /LogPath=C:\mount\dism.fod2.log
    Dism /Remove-Package /Image:"C:\mount\winre" /PackageName:Microsoft-Windows-WinPE-LanguagePack-Package~31bf3856ad364e35~amd64~en-US~10.0.14393.0 /LogPath=C:\mount\dism.fod2.log
    ```

4.  Stellen Sie sicher, dass die Sprachpakete Teil des Bilds sind:

    ``` syntax
    Dism /Get-Packages /Image:"C:\mount\winre"
    ```

    Dabei ist *C* der Laufwerkbuchstabe des Laufwerks, das das Bild enthält.

5.  Überprüfen der resultierenden Liste der Pakete, und überprüfen, ob die Liste das Paket enthält. Beispiel:

    ``` syntax
    Package Identity : Microsoft-Windows-WinPE-Rejuv_fr-fr ...  fr-FR~10.0.14393.0
    State : Installed
    ```

## <a name="span-idoptimizingtheimagepart1spanspan-idoptimizingtheimagepart1spanspan-idoptimizingtheimagepart1spanstep-6-optimizing-the-image-part-1-optional"></a><span id="Optimizing_the_image_part_1"></span><span id="optimizing_the_image_part_1"></span><span id="OPTIMIZING_THE_IMAGE_PART_1"></span>Schritt 6: Optimieren das Bild, Teil 1 (optional)

Nach dem Hinzufügen einer Sprache oder Windows Update-Paket, können Sie die Größe des endgültigen Windows RE-Pakets reduzieren, indem Sie suchen nach doppelten Dateien und markieren die älteren Versionen als ersetzt wurden.

1.  Optimieren Sie das Bild:

    ``` syntax
    Dism /Image:c:\mount\winre /Cleanup-Image /StartComponentCleanup /ResetBase
    ```

2.  Später exportieren Sie das Bild, um die ersetzten Dateien zu entfernen.

## <a name="span-idbkmksaveimagespanspan-idbkmksaveimagespanspan-idbkmksaveimagespanstep-7-unmount-the-winre-image"></a><span id="BKMK_SaveImage"></span><span id="bkmk_saveimage"></span><span id="BKMK_SAVEIMAGE"></span>Schritt 7: Aufheben des WinRE Bilds

-   Heben Sie die Bereitstellung, und speichern Sie das Bild:

    ``` syntax
    Dism /Unmount-Image /MountDir:C:\mount\winre /Commit
    ```

## <a name="span-idoptimizingtheimagepart2spanspan-idoptimizingtheimagepart2spanspan-idoptimizingtheimagepart2spanstep-8-optimizing-the-image-part-2-optional"></a><span id="Optimizing_the_image_part_2"></span><span id="optimizing_the_image_part_2"></span><span id="OPTIMIZING_THE_IMAGE_PART_2"></span>Schritt 8: Optimieren das Bild, Teil 2 (optional)


Wenn Sie das Bild optimiert haben, müssen Sie das Bild zu exportieren, um eine Änderung der Dateigröße zu sehen. Während des Exportvorgangs entfernt DISM Dateien, die ersetzt wurden.

1.  Exportieren Sie das Windows RE-Abbild in einer neuen Windows-Bilddatei.

    ``` syntax
    Dism /Export-Image /SourceImageFile:c:\mount\windows\windows\system32\recovery\winre.wim /SourceIndex:1 /DestinationImageFile:c:\mount\winre-optimized.wim
    ```

2.  Ersetzen Sie das alte Windows RE-Abbild mit dem Bild neu optimiert.

    ``` syntax
    del c:\mount\windows\windows\system32\recovery\winre.wim

    copy c:\mount\winre-optimized.wim c:\mount\windows\windows\system32\recovery\winre.wim
    ```

4.  Überprüfen Sie die neue Größe des Windows RE-Abbilds.

    ``` syntax
    Dir "C:\mount\windows\Windows\System32\Recovery\winre.wim"
    ```

    Wenn die Größe der Partition größer ist als 524,288,000 Bytes, konvertieren Sie die Dateigröße in Megabyte, freien Speicherplatz hinzufügen und ändern Sie das Bereitstellungsskript: CreatePartitions -&lt;Firmware&gt;.txt mit dem neuen Wert. Weitere Informationen zum freien Speicherplatz Recommendations finden Sie unter [UEFI, GPT-basierten Festplattenpartitionen](http://go.microsoft.com/fwlink/?LinkId=526950). Beispiel:

    ``` syntax
    rem == 3. Windows RE tools partition ===============
    create partition primary size=600
    ```

5.  Commit der Änderungen, und heben Sie die Bereitstellung des Windows-Abbilds:

    ``` syntax
    Dism /Unmount-Image /MountDir:"C:\mount\windows" /Commit
    ```

    Dabei ist *C* der Laufwerkbuchstabe des Laufwerks, das das Bild enthält.

    Dieser Vorgang kann einige Minuten dauern.

## <a name="span-idtryitoutspantry-it-out"></a><span id="Try_it_out"></span>Probieren Sie es aus

**Schritt 9: Wenden Sie das Abbild auf einen neuen PC** Verwenden Sie die Schritte auf [Übung 2: Bereitstellen von Windows mithilfe eines Skripts](deploy-windows-with-a-script-sxs.md) um das Bild auf den Speicher, USB-Laufwerk zu kopieren, das Windows-Abbild und die Wiederherstellungsabbild anwenden, und starten. 

Beachten Sie, dass Sie die Schritte zum Hinzufügen des Wiederherstellungsabbilds jetzt bereitstellen möchten:

Die Kurzversion:

1.  Kopieren Sie die Bilddatei auf das Speicherlaufwerk ein.

2.  [Neustart des Geräts Referenz zu Windows PE mit dem Windows PE USB-Schlüssel](install-windows-pe-sxs.md).

3.  Suchen Sie nach der Laufwerkbuchstabe des Laufwerks Speicher (`diskpart, list volume, exit`).

4.  Wenden Sie das Abbild: `D:\ApplyImage.bat D:\Images\install.wim`.

5.  Wenden Sie das Wiederherstellungsabbild:`D:\ApplyRecovery.bat`
    
    Hinweis: Zum Testen eines Bilds unterschiedliche Recovery fügen Sie es auf dieselbe Weise hinzu, Wiederherstellungsabbild angeben: 
    ``` syntax
    D:\ApplyRecovery.bat D:\Images\winre_custom.wim
    ```

5.  Trennen Sie die Laufwerke, und klicken Sie dann neu starten (`exit`).
    
**Schritt 10: Vergewissern Sie sich Treiber und Pakete**
1.  Nach dem Starten des PCs-Option, entweder erstellen Sie ein neues Benutzerkonto zu, andernfalls drücken Sie STRG + UMSCHALT + F3 in das integrierte Administratorkonto (Dies ist auch bekannt als Überwachungsmodus) neu starten.

2.  Klicken Sie auf die Schaltfläche **Start** , klicken Sie auf das Symbol Power, und klicken Sie dann halten Sie die **UMSCHALTTASTE gedrückt** , und wählen Sie **neu starten**.

    Wenn die Treiber erforderliche erfolgreich installiert worden sind, sollte die Windows-wiederherstellungsumgebung angezeigt werden.

    Wenn Sprachen erfolgreich hinzugefügt haben, sehen die entweder die neue Sprache (für eine einzelne Sprache des Bildes) oder Aufforderung des Benutzers für Ihre Sprache (für ein Bild Multi-Language). 
    
Nächster Schritt: [Übung 11: Reduzieren Sie die Bildgröße](shrink-your-image-size.md)