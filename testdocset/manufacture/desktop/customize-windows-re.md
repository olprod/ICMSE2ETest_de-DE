---
author: KPacquer
Description: Anpassen von Windows RE
ms.assetid: ce94e3c4-03f6-46d1-b2a8-cc5d75c7a66d
MSHAttr: PreferredLib:/library/windows/hardware
title: Anpassen von Windows RE
ms.openlocfilehash: 160345af0b5ddbdf05ea5c39615ef997d05cce48
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="customize-windows-re"></a>Anpassen von Windows RE


Sie können Windows Recovery Environment (Windows RE) durch Hinzufügen von Sprachen, Pakete Treiber und benutzerdefinierte Diagnose- und Problembehandlungsinformationen Tools anpassen.

Das Bild WinRE ist in der Windows-10 und Windows Server 2016 Bilder enthalten und wird schließlich in Windows RE-Tools-Partition auf dem Ziel-PC oder ein Gerät kopiert. Um sie zu ändern, müssen Sie stellen Sie das Windows-Abbild und dann stellen Sie das Abbild WinRE darin. Stellen Sie die Änderungen, heben Sie die Bereitstellung des WinRE Bilds, und heben Sie die Bereitstellung des Windows-Abbilds. 

   ![Bild: Stellen Sie das Windows-Abbild, und stellen Sie das Wiederherstellungsabbild darin. Nehmen Sie Änderungen vor, und klicken Sie dann heben Sie die Bereitstellung der Wiederherstellungsabbild und schließlich auf dem Windows-Abbild](images/customize-recovery-image.jpg)

Es wird empfohlen, wenn Sie Ihre Windows-Abbilder zum Aktualisieren mit Sprachen und Treiber erforderliche, Update Windows RE gleichzeitig Bild.

In diesem Thema wird auch optionale Schritte, um das Windows RE-Abbild nach der Aktualisierung zu optimieren.

   
## <a name="span-idprerequisitesspanspan-idprerequisitesspanspan-idprerequisitesspanprerequisites"></a><span id="Prerequisites"></span><span id="prerequisites"></span><span id="PREREQUISITES"></span>Erforderliche Komponenten


Zum Ausführen dieser exemplarischen Vorgehensweise benötigen Sie Folgendes:

-   Ein Referenzcomputer mit dem Windows Assessment and Deployment Kit (ADK) installiert.
-   Das Windows-Abbild (install.wim). Dies kann aus dem Windows-Installationsmedium oder von einem Verweis Abbild sein.

## <a name="span-idbkmkextractimagespanspan-idbkmkextractimagespanspan-idbkmkextractimagespanstep-1-mount-the-windows-and-windows-re-image"></a><span id="BKMK_ExtractImage"></span><span id="bkmk_extractimage"></span><span id="BKMK_EXTRACTIMAGE"></span>Schritt 1: Stellen Sie das Windows und Windows RE-Abbild

**Binden Sie die Bilder**

1.  Öffnen Sie die **Bereitstellung und Imaging Tools Umgebung** an der Eingabeaufforderung als Administrator:

    Klicken Sie auf **Start**, und geben Sie die **Bereitstellung**. Mit der rechten Maustaste, **Bereitstellung und Imaging Tools Umgebung** und wählen Sie dann auf **als Administrator ausführen** &gt; **Ja**.

2.  Stellen Sie das Windows-base-Abbild zur Bearbeitung.

    ``` syntax
    md C:\mount\windows

    Dism /Mount-Image /ImageFile:C:\mount\install.wim /Index:1 /MountDir:C:\mount\windows
    ```

3.  Stellen Sie das Windows RE-Abbild zur Bearbeitung.

    ``` syntax
    md C:\mount\winre 

    Dism /Mount-Image /ImageFile:c:\mount\windows\windows\system32\recovery\winre.wim /Index:1 /MountDir:C:\mount\winre
    ```

    **Hinweis**   Das Windows RE-Abbild sollte immer Indexnummer 1 sein.

     

## <a name="span-idbkmkaddlanguagepacksspanspan-idbkmkaddlanguagepacksspanspan-idbkmkaddlanguagepacksspanstep-2-adding-languages"></a><span id="BKMK_AddLanguagePacks"></span><span id="bkmk_addlanguagepacks"></span><span id="BKMK_ADDLANGUAGEPACKS"></span>Schritt 2: Hinzufügen von Sprachen


Wenn Sie Windows RE Sprachen hinzufügen, müssen Sie das Basis Language Pack und die entsprechenden Language Packs für die einzelnen optionalen Komponenten Windows PE im Windows RE-Tools Bild hinzufügen.

Beginnend mit Windows 10, Version 1607 und Windows Server 2016, sind die Basis Language Pack und optionale Komponente Sprachpakete erforderlich, um Windows RE anpassen im Language Pack DVDs für Windows 10 und Windows Server 2016 enthalten. Die Windows PE Language Packs in der Windows-10-ADK sollte nicht zum Anpassen von Windows RE verwendet werden.

**Hinweis**  
Zur Sicherstellung einer konsistenten Sprache Erfahrung in Wiederherstellungsszenarien fügen Sie den gleichen Satz von Sprachen zum Windows RE-Bild, das das Windows-Abbild hinzugefügt.

Es wird empfohlen, Hinzufügen von nicht mehr als zehn Language Packs zu einem Windows- oder Windows RE-Abbild. Mehrere Sprachpakete erhöhen die Größe des Windows-Abbilds und zudem Einfluss auf die allgemeine Leistung eines Systems während der Bereitstellung und Wartung.

 

**Hinzufügen von Sprachpaketen**

1.  Die Windows PE optionalen Komponenten im Bild Windows RE-Tools aufgelistet:

    ``` syntax
    Dism /Get-Packages /Image:C:\mount\winre
    ```

2.  Überprüfen der resultierenden Liste der Pakete, und fügen Sie dann die entsprechenden Language Packs für jedes Paket im Bild, einschließlich des Basis Windows PE-Language Packs, aber nicht einschließlich **Windows PE-WLAN-Paket**hinzu.

    Der folgende Code zeigt, wie das Sprachpaket Französisch (fr-fr) hinzufügen, an die Basis Windows PE-Abbild und dann auf die einzelnen optionalen Komponenten, die in der Windows RE Standardbild vorhanden sind:

    ``` syntax
    Dism /Add-Package /Image:C:\mount\winre /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\lp.cab"

    Dism /Add-Package /Image:C:\mount\winre /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\WinPE-Rejuv_fr-fr.cab"

    Dism /Add-Package /Image:C:\mount\winre /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\WinPE-EnhancedStorage_fr-fr.cab"

    Dism /Add-Package /Image:C:\mount\winre /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\WinPE-Scripting_fr-fr.cab"

    Dism /Add-Package /Image:C:\mount\winre /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\WinPE-SecureStartup_fr-fr.cab"

    Dism /Add-Package /Image:C:\mount\winre /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\WinPE-SRT_fr-fr.cab"

    Dism /Add-Package /Image:C:\mount\winre /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\WinPE-WDS-Tools_fr-fr.cab"

    Dism /Add-Package /Image:C:\mount\winre /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\WinPE-WMI_fr-fr.cab"

    Dism /Add-Package /Image:C:\mount\winre /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\WinPE-StorageWMI_fr-fr.cab"

    Dism /Add-Package /Image:C:\mount\winre /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\WinPE-HTA_fr-fr.cab"
    ```

    Das **Windows PE-WLAN-Paket** ist nicht sprachspezifische und muss nicht hinzugefügt werden, wenn andere Sprachen hinzufügen.

3.  Wenn Sie Sprachpakete für Japan, Korea oder China hinzufügen, fügen Sie hinzu, die Schriftart-Pakete für diese Sprachen. Es folgt ein Beispiel für Japan:

    ``` syntax
    Dism /image:C:\mount\winre /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\WinPE-Font Support-JA-JP.cab"
    ```

    Weitere Informationen finden Sie unter [Windows PE: Hinzufügen von Paketen (optionalen Komponenten Verweis)](winpe-add-packages--optional-components-reference.md).

4.  Um Speicherplatz freizugeben und den Wiederherstellungsprozess beschleunigen, entfernen Sie nicht benötigte Sprachen. Umkehren Sie zur Vermeidung von Problemen mit Abhängigkeiten die Reihenfolge.

    Beachten Sie, dass das **Windows PE-WLAN-Paket** ist nicht sprachspezifische und sollte nicht entfernt werden.

    ``` syntax
    Dism /Remove-Package /Image:C:\mount\winre /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\en-us\WinPE-HTA_en-us.cab"

    Dism /Remove-Package /Image:C:\mount\winre /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\en-us\WinPE-StorageWMI_en-us.cab"

    Dism /Remove-Package /Image:C:\mount\winre /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\en-us\WinPE-WMI_en-us.cab"

    Dism /Remove-Package /Image:C:\mount\winre /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\en-us\WinPE-WDS-Tools_en-us.cab"

    Dism /Remove-Package /Image:C:\mount\winre /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\en-us\WinPE-SRT_en-us.cab"

    Dism /Remove-Package /Image:C:\mount\winre /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\en-us\WinPE-SecureStartup_en-us.cab"

    Dism /Remove-Package /Image:C:\mount\winre /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\en-us\WinPE-Scripting_en-us.cab"

    Dism /Remove-Package /Image:C:\mount\winre /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\en-us\WinPE-EnhancedStorage_en-us.cab"

    Dism /Remove-Package /Image:C:\mount\winre /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\en-us\WinPE-Rejuv_en-us.cab"

    Dism /Remove-Package /Image:C:\mount\winre /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\en-us\lp.cab"
    ```

## <a name="span-idbkmkadddriversspanspan-idbkmkadddriversspanspan-idbkmkadddriversspanstep-3-adding-boot-critical-drivers"></a><span id="BKMK_AddDrivers"></span><span id="bkmk_adddrivers"></span><span id="BKMK_ADDDRIVERS"></span>Schritt 3: Hinzufügen von wichtigen Treibern


Stellen Sie sicher, dass Sie alle Drittanbieter-Treiber, die Ihr Gerät Verweis benötigt zu starten, wie Speicher oder Video Treiber hinzufügen. Wenn Sie ein Windows-Abbild mithilfe von Windows Imaging und Konfiguration Designer (ICD) Treiber erforderliche hinzugefügt haben, müssen sie das Windows RE-Abbild in das Windows-Abbild hinzugefügt werden.

**Hinzufügen eines wichtigen Treibers**

1.  Entzippen Sie bei Bedarf oder Entpacken Sie die Treiberdatei vom Gerätehersteller Ihres.
2.  Identifizieren Sie die Treiber-Installationsdatei (.inf), und fügen Sie es.

    ``` syntax
    Dism /Image:C:\mount\winre /Add-Driver /Driver:"C:\SampleDriver\driver.inf" 
    ```

    wobei *C:\\SampleDriver\\driver.inf* ist der Speicherort der INF-Datei.

## <a name="span-idbkmkaddcustomtoolsspanspan-idbkmkaddcustomtoolsspanspan-idbkmkaddcustomtoolsspanstep-4-adding-a-custom-tool"></a><span id="BKMK_AddCustomTools"></span><span id="bkmk_addcustomtools"></span><span id="BKMK_ADDCUSTOMTOOLS"></span>Schritt 4: Hinzufügen eines benutzerdefinierten Tools


Sie können eine benutzerdefinierte zur Problembehandlung oder Diagnosetool Windows RE-Abbild hinzufügen. Finden Sie weitere Informationen finden Sie unter [Hinzufügen ein benutzerdefiniertes Tool zum Windows RE Optionen Startmenü](add-a-custom-tool-to-the-windows-re-boot-options-menu.md).

## <a name="span-idbkmkaddupdatesspanspan-idbkmkaddupdatesspanspan-idbkmkaddupdatesspanstep-5-adding-windows-updates"></a><span id="BKMK_AddUpdates"></span><span id="bkmk_addupdates"></span><span id="BKMK_ADDUPDATES"></span>Schritt 5: Hinzufügen von Windows-updates


Windows Update können Sie das Windows RE-Abbild aktualisieren gelegentlich erfordern.

-   Hinzufügen der Windows update-Paket, beispielsweise C:\\MSU\\Windows8.1-KB123456-x64.msu.

    ``` syntax
    Dism /Add-Package /PackagePath:C:\MSU\Windows8.1-KB123456-x64.msu /Image:C:\mount\winre /LogPath:AddPackage.log
    ```

## <a name="span-idstep6optimizingtheimagepart1optionalspanspan-idstep6optimizingtheimagepart1optionalspanspan-idstep6optimizingtheimagepart1optionalspanstep-6-optimizing-the-image-part-1-optional"></a><span id="Step_6__Optimizing_the_image__part_1__optional_"></span><span id="step_6__optimizing_the_image__part_1__optional_"></span><span id="STEP_6__OPTIMIZING_THE_IMAGE__PART_1__OPTIONAL_"></span>Schritt 6: Optimieren das Bild, Teil 1 (optional)

Nach dem Hinzufügen einer Sprache oder Windows Update-Paket, können Sie die Größe des endgültigen Windows RE-Pakets reduzieren, indem duplizierten Dateien gesucht und markiert die älteren Versionen als ersetzt wurden.

1.  Optimieren Sie das Bild:

    ``` syntax
    Dism /Image:c:\mount\winre /Cleanup-Image /StartComponentCleanup /ResetBase
    ```

2.  Später exportieren Sie das Bild, um die ersetzten Dateien zu entfernen.

## <a name="span-idbkmksaveimagespanspan-idbkmksaveimagespanspan-idbkmksaveimagespanstep-7-unmount-the-winre-image"></a><span id="BKMK_SaveImage"></span><span id="bkmk_saveimage"></span><span id="BKMK_SAVEIMAGE"></span>Schritt 7: Heben Sie die Bereitstellung des WinRE-Bilds


-   Heben Sie die Bereitstellung, und speichern Sie das Bild:

    ``` syntax
    Dism /Unmount-Image /MountDir:C:\mount\winre /Commit
    ```

## <a name="span-idstep8optimizingtheimagepart2optionalspanspan-idstep8optimizingtheimagepart2optionalspanspan-idstep8optimizingtheimagepart2optionalspanstep-8-optimizing-the-image-part-2-optional"></a><span id="Step_8__Optimizing_the_image__part_2__optional_"></span><span id="step_8__optimizing_the_image__part_2__optional_"></span><span id="STEP_8__OPTIMIZING_THE_IMAGE__PART_2__OPTIONAL_"></span>Schritt 8: Optimieren das Bild, Teil 2 (optional)


Wenn Sie das Bild optimiert haben, müssen Sie das Bild zu exportieren, um eine Änderung der Dateigröße zu sehen. Während des Exportvorgangs entfernt DISM Dateien, die ersetzt wurden.

1.  Exportieren Sie das Windows RE-Abbild in einer neuen Windows-Bilddatei an.

    ``` syntax
    Dism /Export-Image /SourceImageFile:c:\mount\windows\windows\system32\recovery\winre.wim /SourceIndex:1 /DestinationImageFile:c:\mount\winre-optimized.wim
    ```

2.  Ersetzen Sie das alte Windows RE-Abbild mit dem Bild neu optimiert.

    ``` syntax
    del c:\mount\windows\windows\system32\recovery\winre.wim

    copy c:\mount\winre-optimized.wim c:\mount\windows\windows\system32\recovery\winre.wim
    ```

## <a name="span-idbkmkunmountwindowsspanspan-idbkmkunmountwindowsspanspan-idbkmkunmountwindowsspanstep-9-unmount-the-windows-image"></a><span id="BKMK_UnmountWindows"></span><span id="bkmk_unmountwindows"></span><span id="BKMK_UNMOUNTWINDOWS"></span>Schritt 9: Heben Sie die Bereitstellung des Windows-Abbilds


Speichern Sie Ihre Änderungen wieder in die Windows-Basis-Image.

-   Heben Sie die Bereitstellung der Basis Windows-Image:

    ``` syntax
    Dism /Unmount-Image /MountDir:C:\mount\windows /Commit
    ```

## <a name="span-idnextstepsspanspan-idnextstepsspanspan-idnextstepsspannext-steps"></a><span id="Next_Steps"></span><span id="next_steps"></span><span id="NEXT_STEPS"></span>Nächste Schritte


Wenn Sie mithilfe von **Windows Setup**Windows bereitstellen, aktualisieren Sie die anderen Windows-Bilder in der Windows-Basisdatei (Install.wim).

Wenn Sie Ihr Bild Verweis mithilfe von **Windows PE**und **Diskpart** **DISM**bereitstellen, fahren Sie mit [Windows bereitstellen RE](deploy-windows-re.md).

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Fügen Sie ein benutzerdefiniertes Tool an den Windows RE-Optionen Startmenü](add-a-custom-tool-to-the-windows-re-boot-options-menu.md)

[Bereitstellen von Windows RE](deploy-windows-re.md)

[Bereitstellen von Drucktaste Reset-Features](deploy-push-button-reset-features.md)

[REAgentC Befehlszeilenoptionen](reagentc-command-line-options.md)
