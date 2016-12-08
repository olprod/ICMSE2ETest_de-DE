---
author: Justinha
Description: Vorinstallieren von Apps mithilfe von DISM
ms.assetid: 707607d6-eb3a-4a5b-b52d-4d465d82f69d
MSHAttr: PreferredLib:/library/windows/hardware
title: Vorinstallieren von Apps mithilfe von DISM
ms.openlocfilehash: d041efad416d618a1cc9c24cdfa02cf5e6fe4892
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="preinstall-apps-using-dism"></a>Vorinstallieren von Apps mithilfe von DISM


Vorinstallieren von Windows Store-apps daran interessiert, aber nicht Sie OEM? Informationen zu Sideloading-apps für Organisationen finden Sie unter [Sideload-Apps mit DISM](sideload-apps-with-dism-s14.md).

Zum Installieren von Windows Store-apps in Ihren Bildern vor dem müssen Sie dem Windows Assessment and Deployment Kit (Windows ADK) verwenden. Dieser Abschnitt erläutert die Schritte zum Vorinstallieren von apps im Rahmen der Bilder.

## <a name="span-idbkmkworkwithapppackagesspanspan-idbkmkworkwithapppackagesspanspan-idbkmkworkwithapppackagesspanwork-with-app-packages"></a><span id="BKMK_WorkWithAppPackages"></span><span id="bkmk_workwithapppackages"></span><span id="BKMK_WORKWITHAPPPACKAGES"></span>Arbeiten mit app-Pakete


Für offline Bereitstellung einer app in ein Bild, können das Tool Dism.exe oder der DISM-Cmdlets in Windows PowerShell Sie eine app aus einem Ordner der entpackten Dateien hinzufügen.

**Die Paketdateien extrahieren**

1.  Navigieren Sie zu dem Ordner, in dem Sie die app-Pakete gespeichert, die Sie aus dem Dashboard Partner heruntergeladen haben.
2.  Mit der rechten Maustaste in jeder ZIP-Ordner, die Ihre app-Paket-Dateien enthält. Klicken Sie auf **Alle extrahieren** , und wählen Sie einen Speicherort zum Speichern des Pakets Dateiordner.

    Der Ordner enthält alle der entpackten Dateien für das Paket, einschließlich eines Pakets Hauptfenster, Abhängigkeit Pakete und die Lizenzdatei.

**Wichtige**   Ändern Sie den Ordner nicht, nachdem Sie die Dateien extrahiert haben. Wenn Sie ändern, hinzufügen oder entfernen Sie alle Dateien in den Ordner, die app fehl entweder während der Installation oder zu starten. Den Ordner selbst durchsuchen kann zu Problemen führen.

 

Sie müssen die Lizenzdatei auf die Paketdateien verwenden, um Ihre bereitgestellten Abbild zu testen. Erstellen Ihrer eigenen benutzerdefinierten Daten können nicht genau eine app von einem OEM vorinstalliert testen Sie.

Für offline Bereitstellung einer app in ein Bild, können das Tool Dism.exe oder der DISM-Cmdlets in Windows PowerShell Sie eine app aus einem Ordner der entpackten Dateien hinzufügen.

**Zum Vorinstallieren von einer app Store signiert mithilfe des Tools Dism.exe**

1.  Öffnen der Eingabeaufforderung für Bereitstellungstools, installiert mit der ADK Windows mit Administratorrechten aus. Geben Sie aus dem Bildschirm Start, **Bereitstellung und Imaging Tools Umgebung**, Maustaste auf das Symbol und wählen Sie **als Administrator ausführen**.
2.  Stellen Sie die für die Wartung offline Abbild. Geben Sie in der Befehlszeile Folgendes ein:

    ``` syntax
    Dism /Mount-Image /ImageFile:c:\images\myimage.wim /Index:1 /mountdir:c:\test\offline
    ```

3.  Die app auf das bereitgestellte Abbild hinzufügen. Verwenden der Option/PackagePath und die Option /DependencyPackagePath an den Speicherort des Ordners mit aller entpackten Dateien und die Abhängigkeitsdateien aus dem Speicher-Paket. / PackagePath sollten den Stammordner für die extrahierten Ordner angeben. Der Stammordner enthält die license.xml, AUMIDs.txt und alle Paketdateien. Geben Sie an der Befehlszeile Folgendes ein:

    ``` syntax
    Dism /Image:c:\test\offline /Add-ProvisionedAppxPackage /PackagePath:c:\downloads\appxpackage /DependencyPackagePath:c:\downloads\appxpackagedependency
    ```

4.  Änderungen zu speichern und das Bild aufheben. Geben Sie in der Befehlszeile Folgendes ein:

    ``` syntax
    Dism /Unmount-Image /mountdir:c:\test\offline /commit
    ```

**Zum Vorinstallieren von einer app Store signiert mithilfe von Windows PowerShell**

1.  Öffnen Sie Windows PowerShell mit Administratorrechten aus. Sie müssen Windows 10 oder Windows 8.1 werden auf dem Hostcomputer oder Installieren einer unterstützten Version von Windows PowerShell ausgeführt. Weitere Informationen finden Sie unter [Verwendung von DISM in Windows PowerShell](http://go.microsoft.com/fwlink/p/?linkid=239927).
2.  Stellen Sie das Abbild. Geben Sie an der Windows PowerShell-Eingabeaufforderung Folgendes ein:

    ``` syntax
    Mount-WindowsImage -ImagePath c:\images\myimage.wim -Index 1 -Path c:\test\offline
    ```

3.  Verwenden Sie das Cmdlet Add-AppxProvisionedPackage in Windows PowerShell zur Vorinstallation der app. Verwenden Sie die Option/PackagePath und die Option /DependencyPackagePath, um den Speicherort des Ordners mit aller entpackten Dateien und die Abhängigkeitsdateien aus dem Paket Store anzugeben. Geben Sie in Windows PowerShell ein:

    ``` syntax
    Add-AppxProvisionedPackage -Path c:\test\offline -FolderPath c:\downloads\appxpackage -DependencyPackagePath c:\downloads\appxpackagedependency
    ```

4.  Speichern Sie Änderungen zu, und trennen Sie das Bild. Geben Sie an der Windows PowerShell-Eingabeaufforderung Folgendes ein:

    ``` syntax
    Dismount-WindowsImage -Path c:\test\offline -Save
    ```

**Hinweis**   Windows Store-apps nicht im Überwachungsmodus ausgeführt. Zum Testen der Bereitstellung führen Sie Windows aus und erstellen Sie ein neues Benutzerprofil. Weitere Informationen zum Überwachungsmodus finden Sie unter [Grundlegendes zu Überwachungsmodus](http://go.microsoft.com/fwlink/p/?LinkId=311789) in der TechNet-Bibliothek.

 

**Wichtige**   Wenn Sie eine app Breitband Mobilgerät vorinstallieren, müssen Sie die SIM-Karte im PC vor dem Ausführen der Specialize Phase des Sysprep einfügen. Weitere Informationen zum Vorinstallieren von einer Mobilgerät Breitband-app finden Sie unter [Preinstall die erforderlichen Komponenten für eine Mobile Breitband Anwendung wünschen](#bkmk-broadband-intro).

 

## <a name="span-idbkmkupdateorremovepackagesspanspan-idbkmkupdateorremovepackagesspanspan-idbkmkupdateorremovepackagesspanupdate-or-remove-packages"></a><span id="BKMK_UpdateOrRemovePackages"></span><span id="bkmk_updateorremovepackages"></span><span id="BKMK_UPDATEORREMOVEPACKAGES"></span>Aktualisieren oder Entfernen von Paketen


Sie können eine vorinstallierte-app, einschließlich der Lizenz und benutzerdefinierten Datendateien, aus einer Windows-Abbild mithilfe der DISM.exe Tool oder DISM-Cmdlets in Windows PowerShell entfernen. Sie sollten die alte Version der app entfernen, bevor eine neue installieren.

**Eine vorinstallierte app mithilfe des Tools Dism.exe entfernen**

1.  Öffnen der Eingabeaufforderung für Bereitstellungstools, installiert mit der ADK Windows mit Administratorrechten aus. Auf der Startseite geben, **Bereitstellung und Imaging Tools Umgebung**, mit der rechten Maustaste in des Symbols und wählen Sie **als Administrator ausführen**.
2.  Stellen Sie die für die Wartung offline Abbild. Geben Sie an der Befehlszeile Folgendes ein:

    ``` syntax
    Dism /Mount-Image /ImageFile:c:\images\myimage.wim /Index:1 /mountdir:c:\test\offline
    ```

3.  Hier finden Sie den vollständigen Paketnamen der app, die Sie entfernen möchten. Geben Sie an der Befehlszeile Folgendes ein:

    ``` syntax
    Dism /Image:C:\test\offline /Get-ProvisionedAppxPackages
    ```

4.  Die app aus dem bereitgestellten Bild zu entfernen. Geben Sie beispielsweise an der Befehlszeile:

    ``` syntax
    Dism /Image:c:\test\offline /Remove-ProvisionedAppxPackage /PackageName:microsoft.devx.appx.app1_1.0.0.0_neutral_en-us_ac4zc6fex2zjp
    ```

    **Hinweis**   Wenn die app in einem Benutzerprofil in das Bild nicht registriert ist – beispielsweise wenn das Bild wird allgemeiner (engl.) und noch nicht bereitgestellt wurde – es wird aus dem Bild entfernt. Wenn das Windows-Abbild gestartet hat, und ein Benutzerprofil erstellt wurde, wird die bereitgestellte app für den betreffenden Benutzer registriert ist und muss mithilfe von Remove-AppxPackage-Cmdlets, nach dem Entfernen der Bereitstellung für die app entfernt werden.

     

5.  Wenn Sie die app zu aktualisieren möchten, können Sie die aktualisierte Version der app Store signiert vorinstallieren. Geben Sie an einer Eingabeaufforderung Folgendes ein:

    ``` syntax
    Dism /Image:c:\test\offline /Add-ProvisionedAppxPackage/FolderPath:c:\downloads\appxpackage
    ```

6.  Änderungen zu speichern, und heben Sie die Bereitstellung des Abbilds. Geben Sie an der Befehlszeile Folgendes ein:

    ``` syntax
    Dism /Unmount-Image /mountdir:c:\test\offline /commit
    ```

**So entfernen eine bereitgestellte app mithilfe von Windows PowerShell**

1.  Öffnen Sie Windows PowerShell mit Administratorrechten aus. Sie müssen Windows 10 oder Windows ausgeführt werden auf dem Hostcomputer 8.x oder Installieren einer unterstützten Version von Windows PowerShell. Weitere Informationen finden Sie unter [Verwendung von DISM in Windows PowerShell](http://go.microsoft.com/fwlink/?LinkId=239927).
2.  Stellen Sie das Abbild. Geben Sie an der Windows PowerShell-Eingabeaufforderung Folgendes ein:

    ``` syntax
    Mount-WindowsImage -ImagePath c:\images\myimage.wim -Index 1 -Path c:\test\offline
    ```

3.  Hier finden Sie die vollständige Paketname der app, den, die Sie entfernen möchten. Geben Sie an der Windows PowerShell-Eingabeaufforderung Folgendes ein:

    ``` syntax
    Get-AppxProvisionedPackage -Path c:\test\offline
    ```

4.  Verwenden Sie das Cmdlet Add AppxProvisionedPackage in Windows PowerShell, um die app zu entfernen. Geben Sie in Windows PowerShell ein:

    ``` syntax
    Remove-AppxProvisionedPackage -Path c:\test\offline -PackageName microsoft.devx.appx.app1_1.0.0.0_neutral_en-us_ac4zc6fex2zjp 
    ```

**Hinweis**  Wenn die app zu einem Benutzerprofil in das Bild nicht registriert ist – beispielsweise wenn das Bild wird allgemeiner (engl.) und noch nicht bereitgestellt wurde – es wird aus dem Bild entfernt. Wenn das Windows-Abbild gestartet hat, und ein Benutzerprofil erstellt wurde, wird die bereitgestellte app für den betreffenden Benutzer registriert ist und muss mithilfe von Remove-AppxPackage-Cmdlets, nach dem Entfernen der Bereitstellung für die app entfernt werden.

 

1.  Wenn Sie die app zu aktualisieren möchten, können Sie die aktualisierte Version der app Store signiert vorinstallieren. Geben Sie an der Windows PowerShell-Eingabeaufforderung Folgendes ein:

    ``` syntax
    Add- AppxProvisionedPackage -Path c:\test\offline -FolderPath c:\downloads\appxpackage
    ```

2.  Speichern Sie Änderungen zu, und trennen Sie das Bild. Geben Sie an der Windows PowerShell-Eingabeaufforderung Folgendes ein:

    ``` syntax
    Dismount-WindowsImage -Path c:\test\offline -Save
    ```

## <a name="span-idbkmkusecustomdatefilesspanspan-idbkmkusecustomdatefilesspanspan-idbkmkusecustomdatefilesspanuse-custom-data-files"></a><span id="BKMK_UseCustomDateFiles"></span><span id="bkmk_usecustomdatefiles"></span><span id="BKMK_USECUSTOMDATEFILES"></span>Verwenden benutzerdefinierter Datendateien


Apps, die auf einem PC vorinstalliert sind können benutzerdefinierte Daten, die speziell für die Installation zugreifen. Diese benutzerdefinierten Daten während der Vorinstallation der App hinzugefügt und werden zur Laufzeit verfügbar. Benutzerdefinierte Daten ermöglicht Entwicklern zum Anpassen von Features und Funktionen, einschließlich reporting-Funktionen bereitstellen einer app.

### <a name="span-idbkmkaddcustomdatafilespanspan-idbkmkaddcustomdatafilespanspan-idbkmkaddcustomdatafilespanadd-a-custom-data-file-to-a-windows-image"></a><span id="BKMK_AddCustomDataFile"></span><span id="bkmk_addcustomdatafile"></span><span id="BKMK_ADDCUSTOMDATAFILE"></span>Hinzufügen einer benutzerdefinierten Datendatei zu einem Windows-Abbild

Sie müssen die Datei für benutzerdefinierte Daten angeben, wenn Sie die app mit dem Befehlszeilentool DISM und über Windows PowerShell mit dem Cmdlet **Add-AppxProvisionedPackage** vorinstallieren. Der folgende Befehl ist für diese Vorgehensweise mit dem Tool DISM:

``` syntax
Dism /Image:C:\test\offline /Add-ProvisionedAppxPackage / FolderPath:f:\Apps\Fabrikam_KnowMyPC /CustomDataPath:f:\Contoso_Promotion.xml
```

Wenn eine Datei für benutzerdefinierte Daten im Datenspeicher für eine app bereits vorhanden ist – beispielsweise, wenn das Paket auf das Bild bereits hinzugefügt wurde – die vorhandene Datei überschrieben wird. Wenn die Installation fehlschlägt, wird nicht die Datei wiederhergestellt.

**Hinweis**  
Sie können Updates zu einer app über den Informationsspeicher freigeben, ohne dass die Datei für benutzerdefinierte Daten. Jedoch, wenn ein Benutzer die app löscht, ist die Datei für benutzerdefinierte Daten nicht mehr verfügbar, selbst wenn der Benutzer die Anwendung erneut installiert.

 

### <a name="span-idbkmktestcustomdatafilespanspan-idbkmktestcustomdatafilespanspan-idbkmktestcustomdatafilespantest-custom-data-for-preinstalled-apps"></a><span id="BKMK_TestCustomDataFile"></span><span id="bkmk_testcustomdatafile"></span><span id="BKMK_TESTCUSTOMDATAFILE"></span>Benutzerdefinierte Daten für apps vorinstallierten testen

Apps, die auf einem PC vorinstalliert sind können benutzerdefinierte Daten, die speziell für die Installation zugreifen. Diese benutzerdefinierten Daten während der Vorinstallation der App hinzugefügt und werden für die app zur Laufzeit verfügbar. Benutzerdefinierte Daten ermöglicht Entwicklern zum Anpassen von Features und Funktionen, einschließlich reporting-Funktionen bereitstellen einer app.

Die Custom.data-Datei wird an die app installiert Position angezeigt. Der Name der Custom.data ist hartcodiert und kann nicht geändert werden. Das Vorhandensein der diese Datei zu ermitteln, ob die app auf dem PC vorinstalliert wurde, kann Ihre app überprüfen. Es folgt ein Beispiel dafür, wie Sie auf die Datei Custom.data zuzugreifen.

``` syntax
var outputDiv = document.getElementById("CustomData");
Windows.ApplicationModel.Package.current.installedLocation.getFileAsync
     ("microsoft.system.package.metadata\\Custom.data").then(function (file) {
         // Read the file
         Windows.Storage.FileIO.readTextAsync(file).done(function (fileContent) {
            outputDiv.innerHTML = 
                 "App is preinstalled. CustomData contains:<br /><br />"
                 + fileContent;
         },
         function (error) {
             outputDiv.innerText = "Error reading CustomData " + error;
         });
     },
     function (error) {
         outputDiv.innerText = "CustomData was not available. App not preinstalled";
     });
```

Ihre Datei Custom.data kann den gesamten Inhalt enthalten und in einem beliebigen Format, die Ihre app benötigt werden. Die Vorinstallation stellt sie einfach Ihre app zur Verfügung. Entwickler können die Datendatei mit der Vorinstallation Partner angeben, oder Sie können in ein Format, das zum Generieren des Inhalts des Partners ermöglicht zustimmen.

### <a name="span-idtestyourcustomdataspanspan-idtestyourcustomdataspanspan-idtestyourcustomdataspantest-your-custom-data"></a><span id="Test_your_custom_data"></span><span id="test_your_custom_data"></span><span id="TEST_YOUR_CUSTOM_DATA"></span>Testen Sie Ihre benutzerdefinierten Daten

Wenn Sie erstellen und Debuggen Ihrer app in Microsoft Visual Studio, können nicht Sie die Datei Custom.data aus der app-Installationspfad zugreifen, da die app noch vorinstalliert ist nicht. Sie können die Verwendung der Custom.data-Datei durch einen Test Custom.data Datei platzieren, in der app selbst, und klicken Sie dann laden und Testen der lokalen Datei app simulieren. Ändern Sie hierzu das Codebeispiel aus:

``` syntax
("microsoft.system.package.metadata\\Custom.data").then(function (file) {
```

An:

``` syntax
("Custom.data").then(function (file) {
```

Nachdem Sie Ihre Dateiformat und den Inhalt überprüft haben, können Sie den Speicherort der Datei Custom.data für den endgültigen Speicherort, ändern, wie in der ursprünglichen obigen Beispiel dargestellt.

**So testen Sie Ihre Custom.data-Datei**

1.  Öffnen der Eingabeaufforderung für Bereitstellungstools, installiert mit der ADK Windows mit Administratorrechten aus. Geben Sie aus dem Bildschirm Start, **Bereitstellung und Imaging Tools Umgebung**, Maustaste auf das Symbol und wählen Sie **als Administrator ausführen**.
2.  Fügen Sie die Anwendung mit der Datei für benutzerdefinierte Daten hinzu:

    ``` syntax
    dism /online /Add-ProvisionedAppxPackage /PackagePath:.\CustomData_1.0.0.1_AnyCPU_Debug.appx /CustomDataPath:.\Test.txt /SkipLicense
    ```

    Wobei `/PackagePath:.\CustomData_1.0.0.1_AnyCPU_Debug.appx` verweist auf Ihrem lokalen app Test-Paket, und wo `/CustomDataPath:.\Test.txt` verweist auf die Custom.data-Datei. Werden Sie beachten Sie, dass der Dateiname die hier bereitgestellten nicht nach der Installation von Daten in Ihrer app verwendet.

    Die app verfügt nun über eine Kachel auf **der Startseite der PC-Option verwendet, um die app zu testen** . Die app sollte die Datei Custom.data zugreifen können. Falls zusätzliche Debuggen erforderlich ist, einen Debugger nach dem Starten der app aus dem Bildschirm **Start** .

    **Hinweis**   Möglicherweise müssen Sie sich abmelden und dann erneut anmelden, um die app auf dem Bildschirm **Start** angezeigt werden.

     

3.  Nach Besprechungsende Testen Ihrer app, müssen Sie die vorinstallierten Package, um weiterhin unter Verwendung der Developer-Umgebung entfernen. Zum Entfernen des vorinstallierten Pakets mithilfe von Windows PowerShell können Sie das Cmdlet **Get-AppxPackage** den Namen des vollständigen app-Paket über die Pipeline an das Cmdlet **Remove-ProvisionedAppxPackage** bereitstellen:

    `Get-AppxPackage *CustomData* | Remove-ProvisionedAppxPackage`

    Wobei `*CustomData*` ist der bekannte Teil Ihrer app-Name

## <a name="span-idbkmkbroadbandintrospanspan-idbkmkbroadbandintrospanspan-idbkmkbroadbandintrospanpreinstall-a-windows-store-device-app-or-mobile-broadband-app"></a><span id="BKMK_broadband_intro"></span><span id="bkmk_broadband_intro"></span><span id="BKMK_BROADBAND_INTRO"></span>Vorinstallieren von einer Windows Store-Gerät app oder mobilen Breitband-app


Sie können die erforderlichen Komponenten für eine Windows Store-app Gerät oder einer mobilen Breitband-app mithilfe der Plattform Abbildern Bereitstellung und Verwaltung (DISM) vorinstallieren.

**Hinweis**   In diesem Artikel ist für OEMs vorgesehen, die ein Windows Store Gerät app oder der mobilen Breitband app wird auf ihren Geräten unterstützt werden.

 

Für jede Art von app sollten zwei Dinge vorinstalliert sein, um den richtigen Windows Store-app Gerät oder mobilen Breitband-app angeben:

-   Windows Store-Gerät app, Vorinstallieren von:
    1.  Das Gerät Metadaten-Paket
    2.  Die app
-   Windows Store mobilen Breitband-app, Vorinstallieren von:
    1.  Das Service-Metadaten-Paket
    2.  Die app

**Wichtige**   Zwar unmittelbar nach Abschluss der OOBE Metadaten-Paketen und der entsprechenden apps analysiert werden, kann Benutzer möglicherweise zum Starten der app, bevor das Paket Metadaten aufgelöst wird. In diesem Fall sieht der Benutzer die Fehlermeldung Zugriff verweigert. Um dies zu vermeiden, gelten Sie das Paket Metadaten und die app für das Systemabbild ein.

 

## <a name="span-idpreinstallthedevicemetadataorservicemetadatapackagespanspan-idpreinstallthedevicemetadataorservicemetadatapackagespanspan-idpreinstallthedevicemetadataorservicemetadatapackagespanpreinstall-the-device-metadata-or-service-metadata-package"></a><span id="Preinstall_the_device_metadata_or_service_metadata_package"></span><span id="preinstall_the_device_metadata_or_service_metadata_package"></span><span id="PREINSTALL_THE_DEVICE_METADATA_OR_SERVICE_METADATA_PACKAGE"></span>Vorinstallieren der Gerätepaket für die Metadaten oder Service-Metadaten


**So installieren Sie ein Gerät Metadaten oder Service-Metadaten-Paket vor**

1.  Wenn Sie eine Windows Store-app Gerät Vorinstallieren sollte dann Sie das Gerät Metadaten-Paket erworben haben. Wenn Sie eine mobile Breitband app Vorinstallieren sollten dann Sie das Service-Metadaten-Paket erworben haben.

    **Hinweis**   Gerät Metadaten und Service-Metadaten-Paketen verwenden die gleichen Dateinamenerweiterung (.devicemetadata-ms).

     

2.  Kopieren Sie das Metadaten oder Service Metadaten-Paket des Gerät (Devicemetadata-ms-Datei) auf Ihrem Systemabbild in die **%ProgramData%\\Microsoft\\Windows\\DeviceMetadataStore** Ordner. Hierzu können Sie eine der folgenden Methoden:

    -   Vor dem Ausführen von Sysprep Online
    -   Nach der Ausführung von Sysprep mithilfe von DISM offline. Dazu:

        1.  Stellen Sie die für die Wartung offline Abbild.

            ``` syntax
            Dism /Mount-Image /ImageFile:C:\test\images\myimage.wim /index:1 /MountDir:C:\test\offline
            ```

        2.  Kopieren Sie die Paketdateien Metadaten für den Metadatenspeicher Gerät des bereitgestellten Abbilds. Beispielsweise Kopieren Sie die **0ECF2029-2C6A-41AE-9E0A-63FFC9EAD877.devicemetadata-ms** Paketdatei von Metadaten für den Metadatenspeicher Gerät **Ordner "ProgramData"\\Microsoft\\Windows\\DeviceMetadataStore**:

            ``` syntax
            copy 0ECF2029-2C6A-41AE-9E0A-63FFC9EAD877.devicemetadata-ms C:\test\offline\ProgramData\Microsoft\Windows\DeviceMetadataStore
            ```

        3.  Speichern Sie die Änderungen, und heben Sie die Bereitstellung des Abbilds.

            ``` syntax
            dism /Unmount-Image /mountdir: c:\test\offline /commit
            ```

        Weitere Informationen zur Wartung offline-Abbild finden Sie unter [DISM Overview](http://technet.microsoft.com/library/hh825236.aspx).

Weitere Informationen zum Webdienst-Metadaten finden Sie unter [Service-Metadaten](http://go.microsoft.com/fwlink/p/?LinkId=698640).

## <a name="span-idpreinstallthewindowsstoredeviceappormobilebroadbandappspanspan-idpreinstallthewindowsstoredeviceappormobilebroadbandappspanspan-idpreinstallthewindowsstoredeviceappormobilebroadbandappspanpreinstall-the-windows-store-device-app-or-mobile-broadband-app"></a><span id="Preinstall_the_Windows_Store_device_app_or_mobile_broadband_app"></span><span id="preinstall_the_windows_store_device_app_or_mobile_broadband_app"></span><span id="PREINSTALL_THE_WINDOWS_STORE_DEVICE_APP_OR_MOBILE_BROADBAND_APP"></span>Vorinstallieren der app für Windows Store-Gerät oder mobilen Breitband-app


**Zum Vorinstallieren von der app für Windows Store-Gerät oder mobilen Breitband-app**

1.  Stellen Sie die für die Wartung offline Abbild.

    ``` syntax
    Dism /Mount-Image /ImageFile:C:\test\images\myimage.wim /index:1 /MountDir:C:\test\offline
    ```

2.  Fügen Sie die app für Windows Store-Gerät oder mobilen Breitband-app auf das Bild ein.

    ``` syntax
    dism /Image:<mounted folder> /Add-ProvisionedAppxPackage /FolderPath:<appxpackage path>
    ```

3.  Speichern Sie die Änderungen, und heben Sie die Bereitstellung des Bilds.

    ``` syntax
    dism /Unmount-Image /mountdir: c:\test\offline /commit
    ```

 

 





