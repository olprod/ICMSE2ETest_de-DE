---
author: kpacquer
Description: "Windows 10 IoT Core (IoT Core) Leistungsfähigkeit die von Microsoft Windows und die gesamte Bandbreite der Internet der Dinge. Entwickler können jetzt erstellen und Bereitstellen ihrer eigenen benutzerdefinierten Windows 10 Bilder für die IoT Core-Geräte in ihrer Ökosystems bereit."
ms.assetid: 800596ab-ce50-4bc0-921a-280ed63a2d75
MSHAttr: PreferredLib:/library
title: IoT Core-Bereitstellung und imaging
ms.openlocfilehash: 0bc055bccbcf2f7b6e13fce0893c1ec3d6ed094a
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="iot-core-deployment-and-imaging"></a>IoT Core Bereitstellung und imaging


Windows 10 IoT Core (IoT Core) Leistungsfähigkeit die von Microsoft Windows zusammen mit die gesamte Bandbreite der Internet der Dinge. Entwickler können jetzt erstellen und Bereitstellen ihrer eigenen benutzerdefinierten Windows 10 Bilder für die IoT Core-Geräte in ihrer Ökosystem.

## <a name="span-idintendedaudiencespanspan-idintendedaudiencespanspan-idintendedaudiencespanintended-audience"></a><span id="Intended_audience"></span><span id="intended_audience"></span><span id="INTENDED_AUDIENCE"></span>Zielgruppe


OEMs und ODMs anpassen und Bereitstellen von Bildern für IoT Geräte.

## <a name="span-iddownloadandinstallthekitsandpackagesspanspan-iddownloadandinstallthekitsandpackagesspanspan-iddownloadandinstallthekitsandpackagesspandownload-and-install-the-kits-and-packages"></a><span id="Download_and_install_the_kits_and_packages"></span><span id="download_and_install_the_kits_and_packages"></span><span id="DOWNLOAD_AND_INSTALL_THE_KITS_AND_PACKAGES"></span>Herunterladen Sie und installieren Sie der Kits und Paketen


Bevor Sie ein Bild IoT Core erstellen können:

-   Laden Sie das [Windows Assessment and Deployment Kit (ADK)](http://go.microsoft.com/fwlink/p/?LinkId=526740)
-   Laden Sie die [IoT Core OS Pakete](https://www.microsoft.com/en-us/download/details.aspx?id=53898).
-   Optional: Laden Sie die [Windows 10 IoT Kern Pro Update Steuerdatei](https://www.microsoft.com/en-us/download/details.aspx?id=53899) 

Wenn diese Installationen abgeschlossen sind, überprüfen Sie die Verzeichnisse *FMFiles* *MSPackages*und *OEMInputSamples* aufgerufen, in dem Laufwerk C:\\Program Files (x86)\\Windows Kits\\10 Directory.

## <a name="span-idcreateanimagespanspan-idcreateanimagespanspan-idcreateanimagespancreate-an-image"></a><span id="Create_an_image"></span><span id="create_an_image"></span><span id="CREATE_AN_IMAGE"></span>Erstellen Sie ein Bild


Sie haben zwei Optionen für die Tools zum Erstellen eines Abbilds für IoT Core.

-   Erstellen Sie ein Bild mit IMGGEN
-   Erstellen Sie ein Bild mit Windows Imaging und Konfiguration Designer (ICD).

Weiter unten in diesem Thema werden Sie außerdem erfahren Sie, wie Pakete, anpassen, die erfordert, dass Sie ein Bild mit einer der folgenden Tools erstellen. Wahl des geeigneten Tools Sie verwenden zum Schluss kommen ist.

### <a name="span-idoptiononecreateanimagewithimggenspanspan-idoptiononecreateanimagewithimggenspanspan-idoptiononecreateanimagewithimggenspanoption-one-create-an-image-with-imggen"></a><span id="Option_One__Create_an_image_with_IMGGEN"></span><span id="option_one__create_an_image_with_imggen"></span><span id="OPTION_ONE__CREATE_AN_IMAGE_WITH_IMGGEN"></span>Option 1: Erstellen Sie ein Bild mit IMGGEN

Die Bereitstellung und Imaging Tools Umgebung oder IMGGEN, ist ein alternatives Befehlszeilenprogramm zum Bild Konfiguration Designer. Image-Erstellung kann automatisiert oder über Skripting mit IMGGEN abgeschlossen werden.

1.  Öffnen Sie **Bereitstellung und Imaging Tools Umgebung** Anwendung durch Eingabe von **Bereitstellung und Imaging Tools Umgebung**in der Suchleiste.
2.  Legen Sie die folgenden Umgebungsvariablen in der folgenden Reihenfolge:`SET PATH=%KITSROOT%tools\bin\i386;%PATH%  SET AKROOT=%KITSROOT%`
3.  Führen Sie die folgenden Befehle basierend auf Ihrer Umgebung Gerät:
    -   **Intel Minnowboard Max:**

        `imggen.cmd IoTCore.ffu "%KITSROOT%OEMInputSamples\MBM\ProductionOEMInput.xml" "%KITSROOT%MSPackages" x86`

    -   **Himbeeren Pi 2 oder Qualcomm Dragonboard:**

        `imggen.cmd IoTCore.ffu "%KITSROOT%OEMInputSamples\RPi2\ProductionOEMInput.xml" "%KITSROOT%MSPackages" arm`

### <a name="span-idoptiontwocreateanimagewithwindowsicdspanspan-idoptiontwocreateanimagewithwindowsicdspanspan-idoptiontwocreateanimagewithwindowsicdspanoption-two-create-an-image-with-windows-icd"></a><span id="Option_Two__Create_an_image_with_Windows_ICD"></span><span id="option_two__create_an_image_with_windows_icd"></span><span id="OPTION_TWO__CREATE_AN_IMAGE_WITH_WINDOWS_ICD"></span>Option 2: Erstellen Sie ein Bild mit Windows ICD

Zum Erstellen eines Abbilds IoT-Core mit Windows ICD finden Sie unter [Erstellen und Bereitstellen ein Bilds Windows 10 IoT Core (IoT Core)](https://msdn.microsoft.com/library/windows/hardware/dn916104).

In den folgenden Abschnitten wird beschrieben, wie das Bild anpassen.

## <a name="span-idcreatecustomizedoemconfigurationpackagesspanspan-idcreatecustomizedoemconfigurationpackagesspanspan-idcreatecustomizedoemconfigurationpackagesspancreate-customized-oem-configuration-packages"></a><span id="Create_customized_OEM_configuration_packages"></span><span id="create_customized_oem_configuration_packages"></span><span id="CREATE_CUSTOMIZED_OEM_CONFIGURATION_PACKAGES"></span>Erstellen Sie benutzerdefinierte OEM-Konfiguration-Pakete


Unabhängig davon das Tool zum Erstellen Ihrer Bilds, sei es IMGGEN oder Windows ICD verwendeten, müssen Sie möglicherweise Pakete für die Geräte, die Sie bereitstellen für das branding anpassen oder eindeutige Szenarien zu ermöglichen. Anwendungen, Zertifikate und Einstellungen auf einem Gerät müssen entsprechend Ihren Angaben konfiguriert werden soll. Dies erfordert eine benutzerdefinierte Pakete.

### <a name="span-idcreatethepackagesspanspan-idcreatethepackagesspanspan-idcreatethepackagesspancreate-the-packages"></a><span id="Create_the_packages"></span><span id="create_the_packages"></span><span id="CREATE_THE_PACKAGES"></span>Erstellen Sie die Pakete

Der Prozess zum Erstellen eines Pakets gilt für IoT Core für Windows 10 Mobile unverändert. Finden Sie unter [Erstellen von mobilen Pakete](https://msdn.microsoft.com/library/dn756642) für Anweisungen, um das Paket zu erstellen.

### <a name="span-idinstallingtestcertificatesspanspan-idinstallingtestcertificatesspanspan-idinstallingtestcertificatesspaninstalling-test-certificates"></a><span id="Installing_test_certificates"></span><span id="installing_test_certificates"></span><span id="INSTALLING_TEST_CERTIFICATES"></span>Installieren von Testzertifikaten

OEM Testzertifikate bieten eine Vertrauensstellung für Paketsignaturen. Sie müssen nur einmal installiert werden. Um die Testzertifikate zu installieren

1.  Öffnen Sie die Bereitstellung und Imaging-Tools-Umgebung (IMGGEN) mit Administratorrechten.
2.  Festlegen von Umgebungsvariablen für mit den folgenden Befehlen:
    -   `set W10_KITROOT=%ProgramFiles(x86)%\Windows Kits\10`
    -   `set WPDKCONTENTROOT=%W10_KITROOT%`
    -   `set W10_TOOL=%W10_KITROOT%\bin\x86;%W10_KITROOT%\Tools\bin\i386`
    -   `set PATH=%PATH%;%W10_TOOL%;`

3.  OEM-Zertifikate mit den folgenden Befehl des Dienstprogramms zu installieren:

    `Installoemcerts.cmd`

4.  Stellen Sie sicher, W10\_KITROOT wird festgelegt, um die ProgramFiles%\\Windows Kits\\10.

### <a name="span-idauthorthefeaturemanifestxmlspanspan-idauthorthefeaturemanifestxmlspanspan-idauthorthefeaturemanifestxmlspanauthor-the-feature-manifest-xml"></a><span id="Author_the_feature_manifest_xml"></span><span id="author_the_feature_manifest_xml"></span><span id="AUTHOR_THE_FEATURE_MANIFEST_XML"></span>Autor der Feature-manifest-xml

XML-Dateien definieren den Inhalt der einzelnen Schritte für die Erstellung des Pakets sowie Bereitstellungsprozess. Windows-ICD und IMGGEN hängen ein OEM-Eingabedatei befindet sich im KITSROOT % OEMInputSamples\[Gerät\] Verzeichnis (z. B. C:\\Program Files (x86)\\Windows Kits\\10\\OEMInputSamples\\MBM). Diese OEM-Eingabedatei bezieht sich auf einer Plattform Featuremanifestdatei. Diese Datei enthält eine Liste der Pakete in der erstellten Abbild enthalten sein, und Verweise auf zusätzliche erforderlich oder optional OEM feature Manifestdateien. Weitere Informationen finden Sie unter [OEMInput Inhalt](https://msdn.microsoft.com/library/windows/hardware/dn756778). Das Feature-Manifestdatei Verweise auf die Pakete und CAB-Dateien (CAB), die in das Bild eingeschlossen werden. Weitere Informationen finden Sie unter [Feature Dateiinhalten manifest](https://msdn.microsoft.com/library/windows/hardware/dn756745). Weitere Informationen zur Verwendung von Paketen in Bildern erstellen finden Sie unter [Provisioning-Paket](https://msdn.microsoft.com/library/windows/hardware/mt147447).

Drei OEM Feature Manifestdateien für IoT Core dienen als Beispiele in den folgenden Verzeichnissen.

-   **Intel Minnowboard Max** C:\\Programmdateien (x86)\\Windows Kits\\10\\FMFiles\\X86\\MBMFM.xml
-   **Himbeeren Pi 2** C:\\Program Files (x86)\\Windows Kits\\10\\FMFiles\\Arm\\RPi2FM.xml
-   **Qualcomm Dragonboard 410 c** C:\\Program Files (x86)\\Windows Kits\\10\\FMFiles\\Arm\\QCDB410CFM.xml

Diese Manifeste enthalten die folgenden Abschnitte:

-   Basis-Paket
-   Informationen-Systempakets
-   Gerät Informationen Paket
-   Gerät-Plattform-Paket
-   Basis-featurepakets

Sie können die Basis und Features-Paketen, die in die Basis-Paket und Feature-basierte Paket Abschnitte, und wechseln Sie jeweils hinzufügen.

Es folgt eine Beispiel OEM-Feature-Manifestdatei.

```
<?xml version="1.0" encoding="utf-8"?> 
<FeatureManifest xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
   xmlns:xsd="http://www.w3.org/2001/XMLSchema" 
   xmlns="http://schemas.microsoft.com/embedded/2004/10/ImageUpdate">   
   <BasePackages>      
      <PackageFile Path="$(mspackageroot)\Retail\$(cputype)\$(buildtype)" 
         Name="OEMCoreFeature1.cab" 
         FeatureIdentifierPackage="true"/>      
      <PackageFile Path="$(mspackageroot)\Retail\$(cputype)\$(buildtype)" 
         Name="OEMCoreFeature2.cab" />   
   </BasePackages>   
   <Features>     
      <Microsoft />     
         <MSFeatureGroups />     
      <OEM>
         <PackageFile 
            Path="$(mspackageroot)\Retail\$(cputype)\$(buildtype)" 
            Name="OEMOptionalFeature1.cab"  
            FeatureIdentifierPackage="true">         
            <FeatureIDs>           
               <FeatureID>OEM_OPTIONAL_1</FeatureID>         
            </FeatureIDs>       
         </PackageFile>       
         <PackageFile Path="$(mspackageroot)\Retail\$(cputype)\$(buildtype)" 
            Name="OEMOptionalFeature2.cab" 
            FeatureIdentifierPackage="true">         
            <FeatureIDs>           
               <FeatureID>OEM_OPTIONAL_2</FeatureID>         
            </FeatureIDs>       
         </PackageFile>     
      </OEM>     
   <OEMFeatureGroups />   
   </Features> 
</FeatureManifest>
```

Es folgen Beispiele für Pakete, die Sie in Ihre IoT Core Featuremanifestdatei hinzufügen können. In beiden Fällen muss das Paket Bestandteil einer OEMFM.xml-Datei.

-   Hinzufügen einer Datei zu einem Bild.
    ```
    <?xml version="1.0" encoding="utf-8"?> 
    <Package xmlns="urn:Microsoft.WindowsPhone/PackageSchema.v8.00"    
    Owner="OEMName"    
    OwnerType="OEM"        
    ReleaseType="Test"    
    Platform="PlaformName"    
    Component="ComponentName"    
    SubComponent="SubName">    
       <Components>       
          <OSComponent>          
             <Files>             
                <File Source="$(_RELEASEDIR)\test_file1.dll"/>             
                <File Source="$(_RELEASEDIR)\toBeRenamed.dat"               
                      DestinationDir="$(runtime.system32)\test" Name="test.dat"/>          
             </Files>      
          </OSComponent>    
       </Components> 
    </Package>
    ```

-   Hinzufügen einer Einstellung in der Registrierung zu einem Bild.
    ```
    <?xml version="1.0" encoding="utf-8"?> 
    <Package xmlns="urn:Microsoft.WindowsPhone/PackageSchema.v8.00"    
    Owner="OEMName"    
    OwnerType="OEM"        
    ReleaseType="Test"    
    Platform="PlaformName"    
    Component="ComponentName"    
    SubComponent="SubName">    
       <Components>       
          <OSComponent>          
             <RegKeys>             
                <RegKey KeyName="$(hklm.software)\OEMName\test">                
                   <RegValue Name="StringValue" Value="Test string" Type="REG_SZ"/>                
                   <RegValue Name="DWordValue" Value="12AB34CD" Type="REG_DWORD"/>                
                   <RegValue Name="BinaryValue" Value="12,AB,CD,EF" Type="REG_BINARY"/>             
                </RegKey>             
                <RegKey KeyName="$(hklm.software)\OEMName\EmptyKey"/>          
             </RegKeys>       
          </OSComponent>    
       </Components> 
    </Package>
    ```

-   Hinzufügen eines Treibers zu einem Bild.
    ```
    <?xml version="1.0" encoding="utf-8"?> 
    <Package xmlns="urn:Microsoft.WindowsPhone/PackageSchema.v8.00"    
    Owner="OEMName"    
    OwnerType="OEM"        
    ReleaseType="Production"    
    Platform="PlaformName"    
    Component="ComponentName"    
    SubComponent="SubName">    
       <Components>     
          <Driver       
          InfSource="$(_RELEASEDIR)\Driver1\driver1.inf">       
             <Reference         
             Source="$(_RELEASEDIR)\Driver1\driver1.sys" />       
             <Files>         
                <File Source="$(_RELEASEDIR)\Driver1\driver1.sys" />       
             </Files>     
          </Driver>    
       </Components> 
    </Package> 
    ```

**Generieren der Pakete**

1.  Fügen Sie einen Verweis auf die Datei OEMFM.xml in der OEM-Eingabe-XML-Datei mit dem Namen **RetailOEMInput.xml** für den Einzelhandel Geräte oder **ProductionOEMInput.xml** für Produktion Geräte.
2.  Das Paket Generator-Tool (pkggen.exe) generiert-Paketen und der CAB-Dateien (. CAB-) für die Einbeziehung in das IoT Core Bild ein. Dieses Tool wird installiert, die standardmäßig in WPDKCONTENTROOT %\\Tools\\Bin\\.
3.  Öffnen Sie die Befehlszeile **Bereitstellung und Imaging Tools Umgebung** mit Administratorrechten.
4.  Geben Sie den entsprechenden PKGGEN Befehl für jedes der Pakete, die das Bild hinzugefügt werden soll.
    -   **PKGGEN für einen Treiber:**`PkgGen SampleDriver.pkg.xml /config:"%WPDKCONTENTROOT%\Tools\bin\i386\pkggen.cfg.xml" /version:1.0.0.0 /cpu:x86 /build:fre /variables:"HIVE_ROOT=%WPDKCONTENTROOT%\CoreSystem"`
    -   **PKGGEN für Datei oder ein Registrierungseintrag:**`PkgGen [package project file name] /config:"%WPDKCONTENTROOT%\Tools\bin\i386\pkggen.cfg.xml" /version:1.0.0.0 /cpu:x86 /build:fre`

    **Hinweis**  Feld/Version eines geänderten Pakets sollten immer erhöht werden, bei der Ausführung des Paket-Generators

     

5.  Kopieren Sie alle OEM-Pakete in das Verzeichnis, das Architektur des Geräts zuordnet. *Beispiel: C:\\Program Files (x86)\\Windows Kits\\10\\MSPackages\\Retail\\X86\\Fre*

### <a name="span-idaddinganoempackageduringimagecreationspanspan-idaddinganoempackageduringimagecreationspanspan-idaddinganoempackageduringimagecreationspanadding-an-oem-package-during-image-creation"></a><span id="Adding_an_OEM_package_during_image_creation"></span><span id="adding_an_oem_package_during_image_creation"></span><span id="ADDING_AN_OEM_PACKAGE_DURING_IMAGE_CREATION"></span>Hinzufügen eines OEM-Pakets während der Erstellung

Um ein OEM-Paket als Teil des Image-Erstellungsprozess Schwelle IoT Core hinzuzufügen, führen Sie die folgenden Schritte aus:

1.  Erstellen Sie das Paket aus, wie oben beschrieben, und fügen Sie sie zum Verzeichnis OEM-Pakete für das Gerät-Architektur (z. B. C:\\Program Files (x86)\\Windows Kits\\10\\MSPackages\\Retail\\X86\\Fre.
2.  Hinzufügen eine Featuremanifestdatei (OEMFM.xml), und kopieren Sie sie in das Verzeichnis der Feature-Manifestdatei (z. B. C:\\Program Files (x86)\\Windows Kits\\10\\FMFiles\\X86\\)
3.  Fügen Sie Verweise auf die Featuremanifestdatei OEM und Feature-ID in OEMInputFML.xml unter der Produktions- und Retail-Ordner.
4.  Erstellen Sie ein anderes Bild wie oben mithilfe von Windows ICD oder IMGGEN.

### <a name="span-idaddingoempackagestoadeployedimageatruntimespanspan-idaddingoempackagestoadeployedimageatruntimespanspan-idaddingoempackagestoadeployedimageatruntimespanadding-oem-packages-to-a-deployed-image-at-runtime"></a><span id="Adding_OEM_Packages_to_a_deployed_image_at_runtime"></span><span id="adding_oem_packages_to_a_deployed_image_at_runtime"></span><span id="ADDING_OEM_PACKAGES_TO_A_DEPLOYED_IMAGE_AT_RUNTIME"></span>Hinzufügen von OEM-Paketen zu einem bereitgestellten Abbild zur Laufzeit

Um ein OEM-Paket als Teil des Image-Erstellungsprozess Schwelle IoT Core hinzuzufügen, führen Sie die folgenden Schritte aus:

1.  Kopieren Sie das Paket mit dem Gerät
2.  Verbinden Sie mit dem Gerät über SSH oder Powershell
3.  Diese Befehle ausführen

    `ApplyUpdate.exe -stage C:\OEM\Package1.cab`

    `ApplyUpdate.exe -commit`

Das Gerät wird in das Update-Betriebssystem neu starten, schließen den Installationsvorgang ab und dann wieder für das Hauptfenster Betriebssystem neu starten. Je nach der Paketgröße kann dieser Schritt bis zu 10 Minuten dauern.

### <a name="span-idaddingoemfmfileandoptionalfeaturestotheoeminputxmlspanspan-idaddingoemfmfileandoptionalfeaturestotheoeminputxmlspanspan-idaddingoemfmfileandoptionalfeaturestotheoeminputxmlspanadding-oem-fm-file-and-optional-features-to-the-oem-input-xml"></a><span id="Adding_OEM_FM_file_and_optional_features_to_the_OEM_Input_XML"></span><span id="adding_oem_fm_file_and_optional_features_to_the_oem_input_xml"></span><span id="ADDING_OEM_FM_FILE_AND_OPTIONAL_FEATURES_TO_THE_OEM_INPUT_XML"></span>Hinzufügen von OEM FM-Datei und optionale Features der OEM-Eingabe-XML

Es gibt zwei Beispiel Features Manifestdateien, die als Teil des IoT Core Kits installiert. Sie können hier gefunden werden.

-   C:\\Programmdateien (x86)\\Windows Kits\\10\\OEMInputSamples\\MBM\\ProductionOEMInput.xml
-   C:\\Programmdateien (x86)\\Windows Kits\\10\\OEMInputSamples\\MBM\\RetailOEMInput.xml

### <a name="span-idauthoringoemcustomizationpackagesspanspan-idauthoringoemcustomizationpackagesspanspan-idauthoringoemcustomizationpackagesspanauthoring-oem-customization-packages"></a><span id="Authoring_OEM_Customization_Packages"></span><span id="authoring_oem_customization_packages"></span><span id="AUTHORING_OEM_CUSTOMIZATION_PACKAGES"></span>Authoring OEM Anpassung Pakete

Das Dienstprogramm OEMCustomization.cmd ermöglicht eine Anpassung Startzeitpunkt Gerät. Während der einzelnen Startreihenfolge wird dieses Script-Datei als Ergebnis einer geplanten Aufgabe aufgerufen werden. Die Skriptdatei OEMCustomization.cmd ist in das Bild in der Standardeinstellung nicht vorhanden und muss vom OEM erstellt werden. Die folgenden Anpassungen sind zulässig, und empfohlen:

1.  Aktivieren eines Benutzers mit Administratorrechte auf dem Gerät Net Benutzer Administrator "\[einfügen gewünscht Administratorkennwort\]" / Active: yes OEMCustomization.cmd erstellen. Sie müssen zum Erstellen eines Kennworts zum Ersetzen "\[einfügen gewünscht Administratorkennwort\]" im folgenden Codebeispiel wird.

    ```
    ::OEM CUSTOMIZATION Script File
    ::Enable Administrator Password
    net user Administrator "[insert desired Administrator password]" /active:yes
    ```

2.  Aktivieren Sie die Installation der OEM-Anwendung.
    ```
    ::Enable Application Installation
    call c:\OEM\AppInstall.bat
    ```

3.  So zeigen Sie auf das Skript OEMCustomization.cmd die OEMCustomization.pkg.xml Autor.
    ```
    <?xml version="1.0 encoding="utf-8"?>
    <Package
      xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
      xmlns:xsd="http://www.w3.org/2001/SMLSchema"
      Owner="OEM"
      Component="OEMApp1"
      OwnerType"OEM"
      ReleaseType="Production"
      xmlns="urn:Microsoft.WindowsPhone/PackageSchema.v8.00">
      <Components>
        <OSComponent>
          <Files>
            <File Source="C:\OEM\OEMCustomization.cmd" />
          </Files>
        </OSComponent>
      </Component>
    </Package>
    ```

4.  Erstellen Sie die CAB-Datei für das Paket pkggen.exe verwenden.
5.  Bitlocker zu aktivieren.

## <a name="span-idoemappsspanspan-idoemappsspanspan-idoemappsspanoem-apps"></a><span id="OEM_apps"></span><span id="oem_apps"></span><span id="OEM_APPS"></span>OEM-apps


Helfen Sie die Schritte beim Schreiben von apps für IoT Core, haben wir einige Batchdateien für GitHub hochgeladen. Sie müssen diese Dateien vom <https://github.com/ms-iot/content/blob/develop/en-US/Samples/AppInstaller.md> herunterladen

1.  Kopieren Sie diese Dateien auf Laufwerk C:\\OEM-Verzeichnis auf Ihrem Compute Entwicklung.
    **Hinweis**  Dateien aus GitHub möglicherweise nicht in einem benutzerfreundlichen Format für den Editor angezeigt und können in einer Entwicklungsumgebung, wie Visual Studio geöffnet werden müssen.

     

2.  Kopieren Sie die Dateien APPX und MEZ in C:\\OEM.
3.  Bearbeiten Sie die AppInstall.bat-Skriptdatei
    -   Legen Sie Defaultappx = \[Ihrer Appx Dateiname\]
    -   Legen Sie Certslist = \[Ihrer Appx-Zertifikate Namen\] (mehrere Zertifikate können hinzugefügt werden, getrennt durch ein Leerzeichen)

4.  Bearbeiten Sie die Datei DeployApp.bat
    -   Legen Sie Defaultappx = \[Ihrer Appx Dateiname\]
    -   Legen Sie Defaultappid = \[Ihre Appx ID\]
    -   Legen Sie Depenencylist = \[dadurch zählen, wenn Ihre Appxes Abhängigkeiten haben, bevor Sie Ihre Appx installiert werden die erforderlich sind. Mehrere Abhängigkeit Namen sind durch Leerzeichen getrennt sind, zulässig.

    **Hinweis**  Hinweis: OEMs müssen eine Anwendung auswählen, die auf dem Gerät "Out-of-the-Box", in der Standardeinstellung ausgeführt wird. Diese Anwendung wird nie aktualisiert. Das Betriebssystem muss, wechseln Sie wieder zum OOBE für diese Installation, um sicherzustellen, dass es besteht keine Ressourcenkonflikt während der Installation der Anwendung oder aktualisieren

     

5.  Erstellen Sie das Anwendungspaket OEMApp.pkg.xml, wie im folgenden Beispiel aufgerufen.

    ```
    <?xml version="1.0 encoding="utf-8"?>
    <Package
      xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
      xmlns:xsd="http://www.w3.org/2001/SMLSchema"
      Owner="Oem"
      Component="OEMApp1"
      OwnerType"OEM"
      ReleaseType="Production"
      xmlns="urn:Microsoft.WindowsPhone/PackageSchema.v8.00">
      <Components>
        <OSComponent>
          <Files>
            <File Source="C:\OEM\AppInstall.bat" DestinationDir="C:\Windows\AppInstall"/>
            <File Source="C:\OEM\DeployAppx.bat" DestinationDir="C:\Windows\AppInstall"/>
            <File Source="C:\OEM\OEMApp1.appx" DestinationDir="C:\Windows\AppInstall"/>
            <File Source="C:\OEM\OEMApp1.cer" DestinationDir="C:\Windows\AppInstall"/>
          </Files>
        </OSComponent>
      </Component>
    </Package>
    ```

6.  Legen Sie das erstellte Dateien und zugehörige Ressourcen wie folgt in Verzeichnissen des Geräts Development:
    -   **C:\\Windows\\appherunterladen:**
        -   AppX
        -   Abhängigkeit appx(s)
        -   Temp Appx (optional)
        -   Zertifikate
        -   AppInstall.bat
        -   DeployApp.bat
    -   **C:\\Entwicklungskit\\system32:**
        -   Oemcustomization.cmd

7.  Starten Sie das Gerät neu. Die angegebene Appx wird beim Neustart des Geräts automatisch installiert.

### <a name="span-idimage-timeconfigurationsspanspan-idimage-timeconfigurationsspanspan-idimage-timeconfigurationsspanimage-time-configurations"></a><span id="Image-time_configurations"></span><span id="image-time_configurations"></span><span id="IMAGE-TIME_CONFIGURATIONS"></span>Bild-Time-Konfigurationen

Es folgen Beispiele von Konfigurationseinstellungen, den, die Sie in Ihrer OEMImageCustomization.cmd einschließen möchten.

-   Headless-Konfiguration

    `call reg add HKEY_LOCAL_MACHINE\SYSTEM\currentcontrolset\control\wininit /v Headless /t REG_DWORD /d 1 /f`

-   Absturz Dump-Konfiguration

    `call reg add HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\CrashControl /v AutoReboot /t REG_DWORD /d 1 /f`

    `call reg add HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\CrashControl /v CrashDumpEnabled /t REG_DWORD /d 1 /f`

    `call reg add HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\CrashControl /v DedicatedDumpFile /t REG_SZ /d c:\1.sys /f`

    `call reg add HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\CrashControl /v DumpFile /t REG_EXPAND_SZ /d c:\1.dmp /f`

    `call reg add HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\CrashControl /v DumpFileSize /t REG_DWORD /d 600 /f`

### <a name="span-idrun-timeconfigurationsspanspan-idrun-timeconfigurationsspanspan-idrun-timeconfigurationsspanrun-time-configurations"></a><span id="Run-time_configurations"></span><span id="run-time_configurations"></span><span id="RUN-TIME_CONFIGURATIONS"></span>Laufzeit-Konfigurationen

Die unten aufgeführten zulässigen Runtime Einstellungen sollte in einem provisioning Paket mit Windows ICD generiert enthalten sein. Diese Einstellungen müssen in einem einzelnen Paket provisioning enthalten sein, und das provisioning-Paket in einem einzigen OEM-Paket eingebunden werden soll.

-   Zertifikate
-   Firewall-Konfiguration
-   Start-app
-   Edition-upgrade
-   Aktualisieren von Richtlinien

## <a name="span-idconfiguringiotcoreupdatesettingsspanspan-idconfiguringiotcoreupdatesettingsspanspan-idconfiguringiotcoreupdatesettingsspanconfiguring-iot-core-update-settings"></a><span id="Configuring_IoT_Core_update_settings"></span><span id="configuring_iot_core_update_settings"></span><span id="CONFIGURING_IOT_CORE_UPDATE_SETTINGS"></span>Konfigurieren von Einstellungen für IoT Core Updates


Um ein Bild, um nur OS Updates erhalten konfigurieren zu können, müssen Sie generische POP-Pakete konfigurieren. Generische POP-Paketen an den folgenden Speicherorten vorhanden sein; Ersetzen Sie diese mit den Beispielen aus der Liste aus.

-   **Intel Minnowboard Max**
    -   C:\\Program Files (x86)\\Windows Kits\\10\\MSPackages\\Retail\\X86\\Fre\\Intel.Generic.DeviceInfo.cab
    -   C:\\Program Files (x86)\\Windows Kits\\10\\MSPackages\\Verkaufsversion\\X86\\Fre\\Intel.Generic.DeviceTargetingInfo.cab
    -   Ersetzen durch: C:\\Programmdateien (x86)\\Windows Kits\\10\\FMFiles\\X86\\MBMFM.xml
-   **Himbeeren Pi 2**
    -   C:\\Program Files (x86)\\Windows Kits\\10\\MSPackages\\Retail\\ARM\\Fre\\ RASPBERRYPI. Generic.DeviceInfo.cab
    -   C:\\Program Files (x86)\\Windows Kits\\10\\MSPackages\\Retail\\ARM\\Fre\\ RASPBERRYPI. Generic.DeviceTargetingInfo.cab
    -   Ersetzen durch: C:\\Program Files (x86)\\Windows Kits\\10\\FMFiles\\Arm\\RPi2FM.xml
-   **Qualcomm Dragonboard 410c**
    -   C:\\Program Files (x86)\\Windows Kits\\10\\MSPackages\\Retail\\ARM\\Fre \\Qualcomm.Generic.DeviceInfo.cab
    -   C:\\Program Files (x86)\\Windows Kits\\10\\MSPackages\\Retail\\ARM\\Fre \\Qualcomm.Generic.DeviceTargetingInfo.cab
    -   Ersetzen durch: C:\\Program Files (x86)\\Windows Kits\\10\\FMFiles\\Arm\\QCDB410CFM.xml

## <a name="span-idcreatinganenterpriseiotcoreuapprovisioningpackagespanspan-idcreatinganenterpriseiotcoreuapprovisioningpackagespanspan-idcreatinganenterpriseiotcoreuapprovisioningpackagespancreating-an-enterprise-iot-core-uap-provisioning-package"></a><span id="Creating_an_enterprise_IoT_Core_UAP_provisioning_package"></span><span id="creating_an_enterprise_iot_core_uap_provisioning_package"></span><span id="CREATING_AN_ENTERPRISE_IOT_CORE_UAP_PROVISIONING_PACKAGE"></span>Erstellen eines Enterprise IoT Core UAP provisioning-Pakets


Gehen Sie folgendermaßen vor, um eine Bereitstellung Enterprise-Paket zu erstellen, die auf einem Gerät IoT Core bereitgestellt werden kann.

1.  Laden Sie die IoT Core Lizenzdatei, an dem Gerät Entwicklung. Weitere Informationen zu diesem Schritt finden Sie unter [IoT Core Vermarktung](https://www.windowsforiotdevices.com/).
2.  Erstellen Sie ein neues provisioning Paket, das durch Auswählen von "New-Paket-Bereitstellung" in Windows ICD, wie in der folgenden Abbildung enthält einer Datei, und klicken Sie dann auf **nächste.** ![Screenshot zeigt ICD, mit "Neue Bereitstellung Paket" hervorgehoben.](images/icdappmanager.png)
3.  Klicken Sie im Fenster **Projektdetails Geben Sie** Geben Sie einen **Namen**, **Projektordner**und optional eine **Beschreibung** des Pakets für die Bereitstellung und dann auf **Weiter**.
4.  Klicken Sie im Fenster **Wählen Sie Windows Edition** wählen Sie IoT Core aus und dann auf **Weiter**.
5.  Klicken Sie im Fenster **Importieren eines Pakets provisioning** optional auf **Fertig stellen.**
6.  Fügen Sie der Seite **Anpassungen** die Anpassung [Upgradeeditionwithlicense](https://msdn.microsoft.com/library/windows/hardware/mt573160.aspx) hinzu. Diese Anpassung bietet eine Lizenz für ein Upgrade Edition Iot Core Geräte. ![Screenshot zeigt ICD verfügbaren Anpassungen, einschließlich der Einstellungen für die Laufzeit: EditionUpgrade: UpgradeEditionWithLicense, mit dem Filename iotuapcommercial.xml eingegeben.](images/upgadeeditionwithlicense.png)
7.  Exportieren Sie des Pakets Bereitstellung durch Klicken auf den Dropdownpfeil **Exportieren** im Hauptmenü, und klicken Sie dann auswählen **Provisioning-Pakets**, die erforderlichen Paketinformationen hinzufügen, und geben Sie Optionen für das Paket. Klicken Sie auf **Weiter** , und geben Sie dann, in dem das Paket gespeichert werden soll.
8.  Klicken Sie auf **Erstellen** , um das Bild erstellen. Die Project-Informationen in der Build-Seite angezeigt wird und die Statusanzeige gibt den Status des Build an. Wenn Sie den Build abbrechen müssen, klicken Sie auf **Abbrechen**. Dies wird das aktuelle Build abgebrochen, wird der Assistent geschlossen und gelangen Sie zurück zur Seite **Anpassungen** .

    Den Erstellungsvorgang Bild wird im Fenster Ausgabe Build viel was passiert den Erstellungsvorgang angezeigt. In diesem Fenster werden:

    -   Warnungen, die während der Erstellung des Abbilds angezeigt werden können.
    -   Nachrichten an, dass die Phasen im Image verbose Build erstellen Prozess.
    -   Fehlermeldungen wie bei die Eingabe Dateien Schema fehlerhaft sind oder wenn das Bild nicht erstellen.

    Wenn Sie der Build ein Fehler auftritt, wird eine Fehlermeldung ausgegeben. Sie können das Buildprotokoll um das Problem zu identifizieren, indem Sie auf Ansicht in Editor ansehen.

    Wenn der Build erfolgreich ist, wird der Name des Bilds und seinen Speicherort angezeigt.

9.  Erstellen eines OEM-Pakets, und Text fließt um die neu erstellte provisioning Paket im OEM-Paket, wie im folgenden Beispiel:
    ```
    <?xml version="1.0" encoding="utf-8"?>
    <Package
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xmlns:xsd:"http:///www.w3.org/2001/XMLSchema"
       Owner="OEM"
       Component="Enterprise"
       SubComponent="ProvisioningPackage"
       OwnerType="OEM"
       ReleaseType="Production"
       xmlns="urn:Microsoft.WindowsPhone/PackageSchema.v8.00">
       <Components>
          <OSComponent>
             <Files>
                <File Source="C:\ICD\EnterpriseSKU\EnterpriseProvisioningPkg.ppkg" DestinationDir="C:\OEM" />
             </Files>
          </OSComponent>
       </Components>
    </Package>
    ```

10. Der letzte Schritt darin, so erstellen ein neues IoT Core Bild mit IMGGEN oder Windows ICD und fügen Sie die Bereitstellung Paketdatei gemäß [Erstellen und anwenden ein Pakets provisioning](https://msdn.microsoft.com/library/windows/hardware/dn916107).

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Laden Sie Windows 10 IoT Core](https://developer.microsoft.com/windows/iot/downloads)

 

 



