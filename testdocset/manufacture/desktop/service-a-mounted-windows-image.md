---
author: Justinha
Description: Dienst bereitgestellten Windows-Abbilds
ms.assetid: fbfd9166-f522-4c73-a866-7d97cab32ed8
MSHAttr: PreferredLib:/library/windows/hardware
title: Dienst bereitgestellten Windows-Abbilds
ms.openlocfilehash: ae46fda9d6ecca2045f4811b42eba3d406a5ba73
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="service-a-mounted-windows-image"></a>Dienst bereitgestellten Windows-Abbilds


Das Tool Abbildern Bereitstellung und Verwaltung (DISM) können Sie ein Windows-Abbild aus einer WIM oder VHD-Datei bereitstellen und ändern. Im ersten Teil dieser exemplarischen Vorgehensweise fügen Sie ein Sprachpaket internationale Einstellungen konfigurieren und Aktivieren der Windows-Features. Im zweiten Teil entfernen ein Paket, und Upgraden Sie dann das Windows-Abbild auf eine höhere Version von Windows®.

## <a name="span-idprerequisitesspanspan-idprerequisitesspanspan-idprerequisitesspanprerequisites"></a><span id="Prerequisites"></span><span id="prerequisites"></span><span id="PREREQUISITES"></span>Erforderliche Komponenten


Zum Ausführen der exemplarischen Vorgehensweise benötigen Sie Folgendes:

-   Ein Computer, der auf die Windows ADK Tools installiert ist.

-   Eine WIM-, VHD- oder .vhdx-Datei zu aktualisieren.

-   Language Packs oder andere Pakete hinzufügen und Entfernen aus dem Bild.

## <a name="span-idproceduresspanspan-idproceduresspanspan-idproceduresspanprocedures"></a><span id="Procedures"></span><span id="procedures"></span><span id="PROCEDURES"></span>Verfahren


### <a name="span-idstep1mountanimagewithreadwritepermissionsspanspan-idstep1mountanimagewithreadwritepermissionsspanspan-idstep1mountanimagewithreadwritepermissionsspanstep-1-mount-an-image-with-readwrite-permissions"></a><span id="Step_1__Mount_an_Image_with_Read_Write_Permissions"></span><span id="step_1__mount_an_image_with_read_write_permissions"></span><span id="STEP_1__MOUNT_AN_IMAGE_WITH_READ_WRITE_PERMISSIONS"></span>Schritt 1: Bereitstellen eines Abbilds mit Lese-/Schreibberechtigungen

In diesem Schritt stellen Sie ein Windows-Abbild in einem angegebenen Verzeichnis, bereit, sodass es zum Warten verfügbar ist.

1.  Kopieren Sie eine WIM-Datei, eine VHD- oder eine .vhdx, die auf dem lokalen Laufwerk ein Windows-Abbild enthält. Beispielsweise C:\\testen\\Bilder.

2.  Klicken Sie auf **Start**, und geben Sie die **Bereitstellung**. Mit der rechten Maustaste, **Bereitstellung und Imaging Tools Umgebung** , und wählen Sie dann auf **als Administrator ausführen**.

3.  Erstellen Sie einen Ordner für das bereitgestellte Abbild. Beispielsweise C:\\testen\\offline.

4.  Führen Sie den Befehl **DISM /Get-ImageInfo** zum Abrufen der Name oder die Indexnummer für das Bild, das Sie aktualisieren möchten. Beispiel:

    ``` syntax
    Dism /Get-ImageInfo /ImageFile:C:\test\images\MyImage.wim
    ```

5.  Stellen Sie das Windows-Abbild. Beispiel:

    ``` syntax
    Dism /Mount-Image /ImageFile:C:\test\images\MyImage.wim /Index:1 /MountDir:C:\test\offline
    ```

    Da WIM-Dateien ein oder mehrere Bilder enthalten können, müssen Sie einen Index oder Name-Wert angeben. Um ein Bild aus einer virtuellen Festplatte bereitzustellen, müssen Sie angeben `/Index:1`.

### <a name="span-idstep2addpackagestotheimagespanspan-idstep2addpackagestotheimagespanspan-idstep2addpackagestotheimagespanstep-2-add-packages-to-the-image"></a><span id="Step_2__Add_Packages_to_the_Image"></span><span id="step_2__add_packages_to_the_image"></span><span id="STEP_2__ADD_PACKAGES_TO_THE_IMAGE"></span>Schritt 2: Hinzufügen von Paketen auf das Bild

In diesem Schritt fügen Sie Pakete auf das bereitgestellte Windows-Abbild.

1.  Hinzufügen von Paketen an einer Eingabeaufforderung mit erhöhten Rechten auf das bereitgestellte Windows-Abbild. Beispiel:

    ``` syntax
    Dism /Image:C:\test\offline /Add-Package /PackagePath:C:\test\packages\package1.cab /PackagePath:C:\test\packages\package2.cab
    ```

2.  Wenn Sie ein Sprachpaket hinzugefügt haben, können Sie alle internationale spracheinstellungen im bereitgestellten offline-Abbild ändern, indem Sie den folgenden Befehl eingeben:

    ``` syntax
    Dism /Image:C:\test\offline /Set-SKUIntlDefaults:fr-FR
    ```

    Optional können Sie unterschiedliche Werte für verschiedene Einstellungen, einschließlich Benutzeroberfläche Sprache, Systemgebietsschema, Benutzergebietsschema, das Gebietsschema und andere Benutzer konfigurieren. Weitere Informationen dazu, wie Sie zum Angeben der einzelnen Werte für jede dieser Einstellungen finden Sie unter [DISM Sprachen und International Befehlszeilenoptionen zum Warten](dism-languages-and-international-servicing-command-line-options.md).

3.  Commit für ausführen Sie die Änderungen an der Befehlszeile. Das Bild bleibt eingebundene, bis die Option **/Unmount-Image** verwendet wird. Beispiel:

    ``` syntax
    Dism /Commit-Image /MountDir:C:\test\offline
    ```

### <a name="span-idstep3removeapackagefromthemountedimagespanspan-idstep3removeapackagefromthemountedimagespanspan-idstep3removeapackagefromthemountedimagespanstep-3-remove-a-package-from-the-mounted-image"></a><span id="Step_3__Remove_a_Package_from_the_Mounted_Image"></span><span id="step_3__remove_a_package_from_the_mounted_image"></span><span id="STEP_3__REMOVE_A_PACKAGE_FROM_THE_MOUNTED_IMAGE"></span>Schritt 3: Entfernen eines Pakets aus der bereitgestellten Abbild

In diesem Schritt Überprüfen der Pakete, die in das Abbild installiert wurden, und klicken Sie dann ein bestimmtes Paket aus dem Bild zu entfernen.

1.  Finden Sie unter einer Eingabeaufforderung mit erhöhten Rechten die Namen der Pakete, die in Ihrem Bild sind. Beispiel:

    ``` syntax
    Dism /Image:C:\test\offline /Get-Packages
    ```

    Wenn die Liste der Pakete umfangreich ist, können Sie die Informationen in eine Textdatei ausgeben. Sie können beispielsweise hinzufügen `>C:\PackageList.txt` an das Ende der Befehlszeile.

2.  Überprüfen Sie die Liste der Pakete, die im bereitgestellten Abbild verfügbar sind, und beachten Sie die Paketidentität des Pakets.

3.  Befehlszeile geben Sie die Paketidentität eines Pakets, und aus dem bereitgestellten Bild zu entfernen. Beispiel:

    ``` syntax
    Dism /Image:C:\test\offline /Remove-Package /PackageName:Microsoft.Windows.Calc.Demo~6595b6144ccf1df~x86~en~1.0.0.0
    ```

### <a name="span-idstep4upgradetoahighereditionofwindowsspanspan-idstep4upgradetoahighereditionofwindowsspanspan-idstep4upgradetoahighereditionofwindowsspanstep-4-upgrade-to-a-higher-edition-of-windows"></a><span id="Step_4__Upgrade_to_a_Higher_Edition_of_Windows"></span><span id="step_4__upgrade_to_a_higher_edition_of_windows"></span><span id="STEP_4__UPGRADE_TO_A_HIGHER_EDITION_OF_WINDOWS"></span>Schritt 4: Upgrade auf eine höhere Version von Windows

Alle Änderungen, die Sie vornehmen, werden auch auf jede potenzielle Zieledition von Windows angewendet. Das Bild wird jeder Zieledition bereitgestellt. Die Änderungen werden beim upgrade auf eine höhere Edition von Windows nicht verloren gehen. Weitere Informationen finden Sie unter [Befehlszeilenoptionen DISM Windows Edition zum Warten](dism-windows-edition-servicing-command-line-options.md).

1.  Listen Sie an einer Eingabeaufforderung mit erhöhten Rechten die Versionen, die für das Upgrade verfügbar sind. Beispiel:

    ``` syntax
    Dism /Image:C:\test\offline /Get-TargetEditions
    ```

    Beachten Sie die Ziel-Edition-ID.

2.  Geben Sie an der Befehlszeile die Version, der Sie zum aktualisieren möchten. Beispiel:

    ``` syntax
    Dism /Image:C:\test\offline /Set-Edition:Ultimate
    ```

Endbenutzer Windows jederzeit und überall Upgrade können zum Entfernen von Dateien im Zusammenhang mit niedrigeren Versionen von Windows, die nicht verwendet werden.

### <a name="span-idstep5reducethesizeoftheimagespanspan-idstep5reducethesizeoftheimagespanspan-idstep5reducethesizeoftheimagespanstep-5-reduce-the-size-of-the-image"></a><span id="Step_5__Reduce_the_Size_of_the_Image"></span><span id="step_5__reduce_the_size_of_the_image"></span><span id="STEP_5__REDUCE_THE_SIZE_OF_THE_IMAGE"></span>Schritt 5: Verringern Sie die Größe des Bilds

In diesem Schritt Sie benötigen die Bilanz des Bilds reduzieren, indem ersetzte Komponenten zum Reduzieren der Größe des Speichers Komponente bereinigen und auch durch Zurücksetzen der Basis der ersetzte Komponenten, die können weiter verkleinern Komponente Store.

-   Führen Sie an einer Eingabeaufforderung mit erhöhten Rechten zum Reduzieren der Größe der Bilddatei an den folgenden Befehl aus:

    ``` syntax
    Dism /cleanup-image /StartComponentCleanup /ResetBase 
    ```

### <a name="span-idstep6committhechangesandunmounttheimagespanspan-idstep6committhechangesandunmounttheimagespanspan-idstep6committhechangesandunmounttheimagespanstep-6-commit-the-changes-and-unmount-the-image"></a><span id="Step_6__Commit_the_Changes_and_Unmount_the_Image"></span><span id="step_6__commit_the_changes_and_unmount_the_image"></span><span id="STEP_6__COMMIT_THE_CHANGES_AND_UNMOUNT_THE_IMAGE"></span>Schritt 6: Commit der Änderungen, und heben Sie die Bereitstellung des Abbilds

In diesem Schritt das Bild entladen und speichern die Änderungen, die Sie vorgenommen haben.

-   Heben Sie bei einer Eingabeaufforderung mit erhöhten Rechten die Bereitstellung des Abbilds und commit der Änderungen der Bilddatei an. Beispiel:

    ``` syntax
    Dism /Unmount-Image /MountDir:C:\test\offline /Commit
    ```

## <a name="span-idnextstepspanspan-idnextstepspanspan-idnextstepspannext-step"></a><span id="Next_Step"></span><span id="next_step"></span><span id="NEXT_STEP"></span>Als Nächstes


Diese exemplarische Vorgehensweise veranschaulicht die grundlegenden offline Wartung bereitgestellten Windows-Abbilds. Alle Änderungen wurden vorgenommen, um ein einzelnes Bild und beibehalten, wenn das Bild aktualisiert wurde. Das aktualisierte Abbild kann jetzt bereitgestellt werden. Da Sie die Datei auf der lokalen Festplatte kopiert haben, können Sie die ursprüngliche Bilddatei vom Server löschen. Sie können durch die neue Datei zu ersetzen oder eine Kopie der älteren Version als Referenz.

Weitere Informationen zu weiteren – Wartung offline Vorgänge, die an ein offline-Abbild ausgeführt werden können, finden Sie unter [DISM Image Management Command-Line Options](dism-image-management-command-line-options-s14.md).

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Grundlegendes zu Wartungsstrategien](understanding-servicing-strategies.md)

[Ein Windows-Abbild mithilfe von DISM Service](service-a-windows-image-using-dism.md)

[DISM - Bereitstellung Bild Wartung und Verwaltung technische Referenz für Windows](dism---deployment-image-servicing-and-management-technical-reference-for-windows.md)

 

 






