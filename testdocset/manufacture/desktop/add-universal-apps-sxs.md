---
author: KPacquer
Description: "Übung 6: Hinzufügen von universellen Windows-apps, Kacheln und Taskleiste pins"
MSHAttr: PreferredLib:/library/windows/hardware
title: "Übung 6: Hinzufügen von universellen Windows-apps, Kacheln und Taskleiste pins"
ms.openlocfilehash: 82258242c0a5083e95a5e8a193f28e56825eeb5c
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="span-idaddappsspanlab-6-add-universal-windows-apps-start-tiles-and-taskbar-pins"></a><span id="Add_apps"></span>Übung 6: Hinzufügen von universellen Windows-apps, Kacheln und Taskleiste pins

Hinzufügen von apps zu Ihren Bildern, um verschiedene Kunden zu unterstützen. Einige haben verschiedene Installationsverfahren:

-  **Apps für Windows universelle Plattform (UWP apps)**: Diese hinzugefügt werden kann, oder mithilfe von Tools, die in diesem Thema beschriebenen erneut installiert.    
-  **Windows-desktopanwendungen**: zeigen wir Ihnen das Hinzufügen in [Übung 12: Hinzufügen von desktopanwendungen und mit Einstellungen in Silos zusammengefasst provisioning Pakete (SPPs)](add-desktop-apps-wth-spps-sxs.md).

**Notizen** 

*    **Hinzufügen von Updates vor Sprachen.** Dazu gehören Hotfixes, die allgemein verfügbare Versionen und Servicepacks. Wenn Sie ein Update später hinzufügen möchten, müssen Sie die Sprache erneut hinzufügen.

*    **Sprachen hinzufügen, bevor Sie apps**. Dazu gehören universellen Windows-apps und -desktopanwendungen. Wenn Sie später eine Sprache hinzufügen, müssen Sie die apps erneut zu installieren.

## <a name="span-idmounttheimagespanmount-the-image"></a><span id="Mount_the_image"></span>Stellen Sie das Abbild

**Schritt 1: Stellen Sie das Abbild**

Verwenden Sie die Schritte auf [Übung 3: Hinzufügen von Gerätetreibern (INF-Format)](add-device-drivers.md) zum Bereitstellen des Abbilds. Die Kurzversion:

1.  Öffnen Sie als Administrator der Befehlszeile (**Starten** > geben **Bereitstellung** > Maustaste **Bereitstellung und Imaging Tools Umgebung** > **als Administrator ausführen**.)

2.  Erstellen Sie eine Sicherungskopie der Datei (`copy "C:\Images\Win10_x64\sources\install.wim" C:\Images\install-backup.wim`)

3.  Stellen Sie das Abbild (`md C:\mount\windows`, klicken Sie dann `Dism /Mount-Image /ImageFile:"C:\Images\install.wim" /Index:1 /MountDir:"C:\mount\windows" /Optimize`)

## <a name="span-idaddorreinstallappsspanaddreinstall-apps"></a><span id="Add_or_reinstall_apps"></span>Apps hinzufügen/erneutem installieren
    
**Schritt 2: Hinzufügen/erneuter Installation Posteingang apps (bei jedem Hinzufügen von Sprachen erforderlich)**

Beachten Sie in früheren Versionen es erforderlich, um zuerst Posteingang apps entfernt wurde. Dies ist nicht mehr erforderlich, und wenn Sie dies tun, können die Befehle fehlschlagen.

HINWEIS: Für Windows 10 Version 1607 enthalten app fasst nun nur die Abhängigkeit Pakete, die die app betreffen. Sie müssen nicht mehr welche Abhängigkeiten So installieren Sie die Datei prov.xml prüfen. Installieren Sie alle Abhängigkeit Pakete, die im Ordner gefunden.

1.  Wechseln Sie zu <https://microsoftoem.com> , und rufen Sie das zusätzliche OPK. Dieses Paket enthält die Windows-10 Version 1607 Posteingang apps. Es werden nicht monatliche Updates diese Apps. 

2.  Extrahieren Sie das Paket in einen Ordner, beispielsweise E:\apps\amd64.

3.  Hinzufügen/erneuter Installation im Posteingang apps. Das folgende Beispiel veranschaulicht die Posteingang Einstieg in die app installieren. Wiederholen Sie diese Schritte für jede der Posteingang apps (mit Ausnahme von AppConnector) durch das entsprechende Paket ersetzen.

    ``` syntax
    Dism /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\amd64\Microsoft.3DBuilder_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\amd64\Microsoft.3DBuilder_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x64.14.00.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x86.14.00.appx
    ```

    Finden Sie [Beispielskripts](windows-deployment-sample-scripts-sxs.md#Reinstall_Windows_inbox_apps).

**Schritt 3: Hinzufügen/Neuinstallation von universellen Windows apps (Optional)**

In unserem Beispiel installieren wir Office Mobile, obwohl Sie alle mit diesem Verfahren UWP app installieren können.

**Hinweis**: Installieren Sie entweder einzelnen Office-Abbild (mit oder mit Out-unbefristete oder Abonnementlizenz) oder Office Mobile (jedoch nicht beide). Office Mobile auf Geräten mit Bildschirmgröße 10.1" und unter verwendet werden muss, und nur einem Bild von Office müssen auf Geräten mit Bildschirmgröße oberhalb 10.1" verwendet werden. Für Geräte, die einen einzelnen festen Speicherlaufwerk mit weniger als 32 GB haben, können OEMs Office Mobile, unabhängig von der Bildschirmgröße vorinstallieren. Weitere Informationen finden Sie unter [Office Mobile Kommunikation](https://myoem.microsoft.com/oem/myoem/en/product/office/Pages/COMM-OfficeUnvrslAppsOPKRlsTmng.aspx).

1.  Wechseln Sie zur <https://microsoftoem.com> und möchten Sie ergänzende OPK erhalten. Dieses Paket enthält die Windows-10 Version 1607 Posteingang apps. Es werden nicht monatliche Updates diese Apps. 

2.  Extrahieren Sie das Paket in einen Ordner, beispielsweise e:\Universal_Office an.

3.  Hinzufügen/erneuter Installation Office Mobile:

    ``` syntax
    Dism /Add-ProvisionedAppxPackage /Image:"c:\mount\windows" /packagepath:"e:\Universal_Office\PC_TH1_store.16.0.6228.1011.Excelim.appxbundle_Windows10_PreinstallKit\1b0569bd5fbd41d6bf0669beb013073c.appxbundle" /dependencypackagepath:"e:\Universal_Office\PC_TH1_store.16.0.6228.1011.Excelim.appxbundle_Windows10_PreinstallKit\Microsoft.VCLibs.140.00_14.0.22929.0_x86__8wekyb3d8bbwe.appx" /licensepath:"e:\Universal_Office\PC_TH1_store.16.0.6228.1011.Excelim.appxbundle_Windows10_PreinstallKit\1b0569bd5fbd41d6bf0669beb013073c_License1.xml"

    Dism /Add-ProvisionedAppxPackage /Image:"c:\mount\windows"  /packagepath:"e:\Universal_Office\PC_TH1_store.16.0.6228.1011.Pptim.appxbundle_Windows10_PreinstallKit\7f255062294a415a974b4958961df056.appxbundle" /dependencypackagepath:"e:\Universal_Office\PC_TH1_store.16.0.6228.1011.Pptim.appxbundle_Windows10_PreinstallKit\Microsoft.VCLibs.140.00_14.0.22929.0_x86__8wekyb3d8bbwe.appx" /licensepath:"e:\Universal_Office\PC_TH1_store.16.0.6228.1011.Pptim.appxbundle_Windows10_PreinstallKit\7f255062294a415a974b4958961df056_License1.xml"

     Dism /Add-ProvisionedAppxPackage /Image:"c:\mount\windows" /packagepath:"e:\Universal_Office\PC_TH1_store.16.0.6228.1011.Wordim.appxbundle_Windows10_PreinstallKit\532f710ca9d34f0aae6af4abe0af0592.appxbundle" /dependencypackagepath:"e:\Universal_Office\PC_TH1_store.16.0.6228.1011.Wordim.appxbundle_Windows10_PreinstallKit\Microsoft.VCLibs.140.00_14.0.22929.0_x86__8wekyb3d8bbwe.appx" /licensepath:"e:\Universal_Office\PC_TH1_store.16.0.6228.1011.Wordim.appxbundle_Windows10_PreinstallKit\532f710ca9d34f0aae6af4abe0af0592_License1.xml"
    ```

    Der PackagePath, in dem Sie die app-Paket Bundle verweist.


**Schritt 4: Ändern Sie die Kachel Startmenü und Taskleiste Pin Layouts (Optional)**

Sie können separate Layouts für das standardmäßige, den, das Start werden nebeneinander angeordnet, und Taskleiste Fächer für unterschiedliche Regionen oder Märkte definieren.

1.  Erstellen Sie eine LayoutModification.xml-Datei. Für unserem Labor können Sie das Beispiel über USB-B oder [Beispiel LayoutModification.xml](windows-deployment-sample-scripts-sxs.md)verwenden. In diesem Beispiel werden zwei Gruppen namens "Fabrikam Group 1" und "Gruppe" Fabrikam "2", die Kacheln enthalten, die angewendet werden basierend auf zwei Regionen. 

    Wenn Ihre eigene LayoutModification-Datei zu erstellen:

    Um desktopanwendungen oder älteren URL (URL) Verknüpfungen hinzuzufügen, verwenden Sie das Start: DesktopApplicationTile-Tag.

     -  Für desktop-apps Wenn Sie der Anwendung Modell Mitgliedsname bekannt ist, verwenden.

     -  Erstellen Sie andernfalls für desktop-apps oder legacy URL Links, Linkdateien (LNK) entweder die legacy-Menü Start-Ordner:

         -  %APPDATA%\Microsoft\Windows\Start Menu\Programs\

         -  %ALLUSERSPROFILE%\Microsoft\Windows\Start Menu\Programs\ 

     Fügen Sie in einem späteren Abschnitt die desktopanwendungen: [Übung 12: Hinzufügen von desktopanwendungen und mit Einstellungen in Silos zusammengefasst provisioning Pakete (SPPs)](add-desktop-apps-wth-spps-sxs.md).    

2.  Fügen Sie Ihrer LayoutModification.xml Datei auf dem Windows-Abbild. Sie müssen die Datei in die folgenden Position vor dem ersten Start zu platzieren. Wenn die Datei existiert, sollten Sie den LayoutModification.XML ersetzen, die bereits im Bild enthalten ist.

    ``` syntax
    C:\Mount\Windows\Users\Default\AppData\Local\Microsoft\Windows\Shell\
    ```

3.  Wenn Sie Kacheln, die URL oder .lnk Dateien erfordern fixiert, fügen Sie die Dateien die folgenden legacy-Menü Start Verzeichnisse hinzu:
    -   ANWENDUNGSDATEN %\\Microsoft\\Windows\\Startmenü\\Programme\\
    -   %ALLUSERSPROFILE%\\Microsoft\\Windows\\Startmenü\\Programme\\

**Hinweis**  Das Start-Layout kann Benutzer ihren PC mit der integrierten Wiederherstellungstools setzt verloren. Sie erfahren, wie Sie sicherstellen, dass diese Einstellungen auf dem Gerät im [Beispielskripts](windows-deployment-sample-scripts-sxs.md)bleiben.

4.  Hinzufügen ein Layouts Taskleiste in Windows 10 1607, Version können Sie entweder hinzufügen ein ähnliches [Taskleiste Layoutdatei Änderung (Siehe hier zusätzliche Schritte)](https://msdn.microsoft.com/library/windows/hardware/mt736838.aspx), oder verwenden Sie [herkömmliche unbeaufsichtigten Einstellungen](update-windows-settings-and-scripts-create-your-own-answer-file-sxs.md). 

## <a name="span-idaddorchangelanguagesandcortanafeaturesondemandoptionalspanspan-idaddorchangelanguagesandcortanafeaturesondemandoptionalspanspan-idaddorchangelanguagesandcortanafeaturesondemandoptionalspanadd-or-change-languages-and-cortana-features-on-demand-optional"></a><span id="Add_or_change_languages_and_Cortana_features_on_demand__Optional_"></span><span id="add_or_change_languages_and_cortana_features_on_demand__optional_"></span><span id="ADD_OR_CHANGE_LANGUAGES_AND_CORTANA_FEATURES_ON_DEMAND__OPTIONAL_"></span>Hinzufügen oder Ändern von Sprachen und Cortana Features bei Bedarf (Optional)

## <a name="span-idunmounttheimagesspan-unmount-the-images"></a><span id="Unmount_the_images"></span>Heben Sie die Bereitstellung der Bilder

**Schritt 5: Heben Sie die Bereitstellung der Bilder**

1.  Schließen Sie alle Programme, die Dateien aus dem Bild zugreifen können.

2.  Commit der Änderungen, und heben Sie die Bereitstellung des Windows-Abbilds:

    ``` syntax
    Dism /Unmount-Image /MountDir:"C:\mount\windows" /Commit
    ```

    Dabei ist *C* der Laufwerkbuchstabe des Laufwerks, das das Bild enthält.

    Dieser Vorgang kann einige Minuten dauern.

## <a name="span-idtryitoutspantry-it-out"></a><span id="Try_it_out"></span>Probieren Sie es aus

**Schritt 6: Wenden Sie das Abbild auf einen neuen PC** Verwenden Sie die Schritte auf [Übung 2: Bereitstellen von Windows mithilfe eines Skripts](deploy-windows-with-a-script-sxs.md) um das Bild auf den Speicher, USB-Laufwerk zu kopieren, das Windows-Abbild und die Wiederherstellungsabbild anwenden, und starten. Die Kurzversion:

1.  Kopieren Sie die Bilddatei mit dem Speicherlaufwerk.
2.  [Boot Verweis Gerät, um Windows PE mit Windows PE USB-Taste](install-windows-pe-sxs.md).
3.  Suchen Sie nach der Laufwerkbuchstabe des Laufwerks Speicher (`diskpart, list volume, exit`).
4.  Wenden Sie das Abbild: `D:\ApplyImage.bat D:\Images\install.wim`.
5.  Die Laufwerke, auf Trennen und dann neu starten (`exit`).
    
**Schritt 7: Überprüfen Sie apps**
1.  Nach dem Starten des PCs-Option, entweder erstellen Sie ein neues Benutzerkonto zu, andernfalls drücken Sie STRG + UMSCHALT + F3 in das integrierte Administratorkonto (Dies ist auch bekannt als Überwachungsmodus) neu starten.

2.  Überprüfen Sie im Menü Start, um sicherzustellen, dass die apps verfügbar sind.

3.  Überprüfen Sie der Startmenü und Taskleiste und stellen Sie sicher, dass der gewählten apps ordnungsgemäß fixiert sind.
    
Nächster Schritt: [Übung 7: Einstellungen ändern, geben Sie die Product Keys und Ausführen von Skripts mit einer Antwortdatei (unattend.xml)]