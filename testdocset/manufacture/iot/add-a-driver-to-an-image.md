---
author: kpacquer
Description: We'll show you one of two ways to add a driver to the image.
title: "Übung 1e: Hinzufügen eines Treibers zu einem Bild"
ms.openlocfilehash: 5962a48636841044aedb381c0cabbe59c5e11355
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="lab-1e-add-a-driver-to-an-image"></a>Übung 1e: Hinzufügen eines Treibers zu einem Bild

In dieser Übungseinheit fügen wir den Beispieltreiber: [Hello, Blinky!](https://developer.microsoft.com/windows/iot/samples/driverlab)up zu packen und bereitstellen, um die zu einem Gerät Windows 10 IoT Core.

## <a name="span-idprerequisitesspanspan-idprerequisitesspanspan-idprerequisitesspanprerequisites"></a><span id="Prerequisites"></span><span id="prerequisites"></span><span id="PREREQUISITES"></span>Erforderliche Komponenten

* Erstellen Sie einen Produktordner (Produktseite), die so eingerichtet, starten Sie auf den Standardwert (Bertha) app, siehe [Lab 1a: Erstellen eines grundlegenden Abbilds](create-a-basic-image.md) oder [Übung 1c: Fügen Sie eine Datei und einer Einstellung in der Registrierung zu einem Bild](add-a-registry-setting-to-an-image.md).

## <a name="span-idcheckforsimilardriversspancheck-for-similar-drivers"></a><span id="Check_for_similar_drivers"></span>Kontrollkästchen für ähnliche Treiber

Bevor Sie Treiber hinzufügen, sollten Sie überprüfen Ihrer vordefinierte Board Support Paket (BSP) um sicherzustellen, dass es ist nicht bereits ein ähnlichen Treiber. 

Überprüfen Sie die Liste der Treiber in der Datei beispielsweise: \\IoT-ADK-AddonKit\\Source Arm\\BSP\\Rpi2\\Pakete\\RPi2FM.xml.

- Wenn Sie kein vorhandener Treiber vorhanden ist, können Sie in der Regel nur eine hinzufügen.

- Wenn ein Treiber, aber es nicht Ihren Anforderungen erfüllen, müssen Sie den Treiber durch Erstellen einer neuen BSP ersetzen. Wir behandeln, die in [Übung 2](create-a-new-bsp.md).

## <a name="span-idcreateyourtestfilesspanspan-idcreateyourtestfilesspanspan-idcreateyourtestfilesspancreate-your-test-files"></a><span id="Create_your_test_files"></span><span id="create_your_test_files"></span><span id="CREATE_YOUR_TEST_FILES"></span>Erstellen Sie die Testdateien

-  Führen Sie die Übungen in [Der Beispiel-Treiber installieren](https://developer.microsoft.com/en-us/windows/iot/samples/driverlab1) den Hello Hauptverkaufsargument app erstellen. Erstellen Sie drei Dateien: ACPITABL.dat gpiokmdfdemo.inf und gpiokmdfdemo.sys an, die Sie zum Installieren des Treibers verwenden.

   Solange es kein Konflikt mit vorhandenen Board Support-Paket (BSP) entsteht, können Sie auch Ihren eigenen Treiber IoT Core verwenden.

-  Kopieren der Dateien: gpiokmdfdemo.sys gpiokmdfdemo.inf und ACPITABL.dat in einen Testordner, beispielsweise C:\gpiokmdfdemo\.

## <a name="span-idbuildapackageforyourdriverspanspan-idbuildapackageforyourdriverspanspan-idbuildapackageforyourdriverspanbuild-a-package-for-your-driver"></a><span id="Build_a_package_for_your_driver"></span><span id="build_a_package_for_your_driver"></span><span id="BUILD_A_PACKAGE_FOR_YOUR_DRIVER"></span>Erstellen eines Pakets für Ihre Treiber

1.  Führen Sie **C:\\IoT-ADK-AddonKit\\IoTCoreShell** als Administrator.

2.  Des Treiberpakets, wobei die INF-Datei als Basis zu erstellen:

    ``` syntax
    newdrvpkg C:\gpiokmdfdemo\gpiokmdfdemo.inf Drivers.HelloBlinky
    ```

    An den neuen Ordner **C:\\IoT-ADK-AddonKit\\Quell -&lt;Bogen&gt;\\Pakete\\Drivers.HelloBlinky\\**.

3. Kopieren Sie die Datei: in den neuen Ordner ACPITABL.dat **C:\\IoT-ADK-AddonKit\\Source -_< Bogen_>\\Pakete\\Drivers.HelloBlinky\\**.

**Stellen Sie sicher, dass die Beispieldateien im Paket sind**

1.  Aktualisieren der Treiber-Paketdefinitionsdatei, **C:\\IoT-ADK-AddonKit\\Source -&lt;Bogen&gt;\\Pakete\\Drivers.HelloBlinky\\Drivers.HelloBlinky.pkg.xml**.

    Die Standard-Paketdefinitionsdatei enthält Beispiel-XML, die Sie ändern können, um Ihre eigenen Treiberdateien hinzuzufügen.

    Falls erforderlich, aktualisieren Sie den Wert der Dateiquelle auf Ihr. SYS-Datei, und die Datei ACPITABL.dat. (Sie müssen nicht hinzufügen der. INF-Datei.)  Fügen Sie der DestinationDir von "$(runtime.drivers)".
    
    ``` syntax
    <Package xmlns="urn:Microsoft.WindowsPhone/PackageSchema.v8.00" 
         Owner="$(OEMNAME)" OwnerType="OEM" ReleaseType="Production" 
         Platform="arm" Component="Drivers" SubComponent="HelloBlinky"> 
      <Components> 
        <Driver InfSource="gpiokmdfdemo.inf"> 
          <Reference Source="gpiokmdfdemo.sys" /> 
          <Files> 
            <File Source="gpiokmdfdemo.sys"  
                  DestinationDir="$(runtime.drivers)"  
                  Name="gpiokmdfdemo.sys" /> 
            <File Source="ACPITABL.dat"  
                  DestinationDir="$(runtime.system32)"  
                  Name="ACPITABL.dat" /> 
          </Files> 
        </Driver> 
      </Components> 
    </Package> 
    ```

2.  Erstellen Sie in der Shell IoT Core das Paket.

    ``` syntax
    createpkg Drivers.HelloBlinky
    ```

    Das Paket erstellt, das als **C:\\IoT-ADK-AddonKit\\erstellen\\&lt;Bogen&gt;\\Pckg\\&lt;OEM-Name&gt;. Drivers.HelloBlinky.cab**.

    
## <a name="span-idupdateyourfeaturemanifestspanspan-idupdateyourfeaturemanifestspanspan-idupdateyourfeaturemanifestspanupdate-your-feature-manifest"></a><span id="Update_your_feature_manifest"></span><span id="update_your_feature_manifest"></span><span id="UPDATE_YOUR_FEATURE_MANIFEST"></span>Aktualisieren des Manifests feature


**Das Feature Manifest Ihrer Treiberpakets hinzufügen**

1.  Öffnen Sie die architekturspezifische Feature-Manifestdatei **C:\\IoT-ADK-AddonKit\\Quell -_< Bogen_>\\Pakete\\OEMFM.xml**

2.  Erstellen eines neuen PackageFile-Abschnitts in der XML-DATEI mit der Paketdatei aufgelistet, und geben sie einen neuen FeatureID, z. B. "OEM\_DriverHelloBlinky".

    ``` syntax      
          <PackageFile Path="%PKGBLD_DIR%" Name="%OEM_NAME%.Drivers.HelloBlinky.cab">
            <FeatureIDs>
              <FeatureID>OEM_DriverHelloBlinky</FeatureID>
            </FeatureIDs>
          </PackageFile>
    ```

    Sie können nun den Treiber für Ihr Produkt hinzufügen, indem Sie einen Verweis auf dieses Feature Manifest sein.


## <a name="span-idupdatetheprojectsconfigurationfilesspanspan-idupdatetheprojectsconfigurationfilesspanspan-idupdatetheprojectsconfigurationfilesspanupdate-the-projects-configuration-files"></a><span id="Update_the_project_s_configuration_files"></span><span id="update_the_project_s_configuration_files"></span><span id="UPDATE_THE_PROJECT_S_CONFIGURATION_FILES"></span>Aktualisieren Sie das Projekt Konfigurationsdateien

1.  Öffnen Sie Ihr Produkt Test-Konfigurationsdatei: **C:\\IoT-ADK-AddonKit\\Quell -_< Bogen_>\\Produkte\\Produkt a angezeigt\\TestOEMInput.xml**.

2.  Stellen Sie sicher, dass Ihr Manifest Feature, OEMFM.xml, in der Liste der AdditionalFMs ist. Fügen Sie es hinzu, wenn sie es nicht bereits vorhanden ist:

    ``` syntax
      <AdditionalFMs>
        <AdditionalFM>%AKROOT%\FMFiles\arm\IoTUAPNonProductionPartnerShareFM.xml</AdditionalFM>
        <AdditionalFM>%SRC_DIR%\Packages\OEMFM.xml</AdditionalFM>
      </AdditionalFMs>
    ```

3.  Fügen Sie die FeatureID für den Treiber hinzu:

    ``` syntax
    <OEM>
      <!-- Include BSP Features -->
      <Feature>RPI2_DRIVERS</Feature>
      <Feature>RPI3_DRIVERS</Feature>
      <!-- Include OEM features-->
      <Feature>OEM_AppxMain</Feature>
      <Feature>OEM_CustomCmd</Feature>
      <Feature>OEM_ProvAuto</Feature>
      <Feature>OEM_FilesAndRegKeys</Feature>
      <Feature>OEM_DriverHelloBlinky</Feature> 
    </OEM>
    ```

## <a name="span-idbuildandtesttheimagespanspan-idbuildandtesttheimagespanspan-idbuildandtesttheimagespanbuild-and-test-the-image"></a><span id="Build_and_test_the_image"></span><span id="build_and_test_the_image"></span><span id="BUILD_AND_TEST_THE_IMAGE"></span>Erstellen Sie und Testen Sie das Abbild

Erstellen und das Bild mit den gleichen Verfahren aus flash [Lab 1a: Erstellen eines grundlegenden Abbilds](create-a-basic-image.md). Kurzes Format:

1.  Erstellen Sie das Bild aus der IoT Core Shell (`buildimage ProductB Test`).
2.  Installieren Sie das Abbild: Start **Windows IoT Core Dashboard** > Klicken Sie auf der Registerkarte **Setup ein neues Gerät** > Wählen Sie **Gerätetyp: benutzerdefinierte** >
3.  Über **die heruntergeladene Datei (Flash.ffu) an die SD-Karte Flash**: Klicken Sie auf **Durchsuchen**, navigieren Sie zur Datei FFU (C:\\IoT-ADK-AddonKit\\erstellen\\&lt;Bogen&gt;\\Produktseite\\Test\\ProductB.ffu), klicken Sie dann auf **Weiter**.
4.  Geben Sie Benutzername und Kennwort (der Standardwert lautet: Minwinpc / p@ssw0rd) > die Micro SD-Karte im Gerät zu platzieren, wählen Sie sie aus, akzeptieren der Lizenzbedingungen und klicken Sie auf *Installieren**. 
5.  Platzieren Sie die Visitenkarte in das Gerät IoT, und starten sie Sie.

**Überprüfen Sie, um festzustellen, ob der Treiber funktioniert**

1.  Verwenden Sie die Verfahren in der [Hello, Blinky! Lab](https://developer.microsoft.com/windows/iot/samples/driverlab3) zum Testen des Treibers.

## <a name="span-idnextstepsspanspan-idnextstepsspanspan-idnextstepsspannext-steps"></a><span id="Next_steps"></span><span id="next_steps"></span><span id="NEXT_STEPS"></span>Nächste Schritte

[Übung 1f: Erstellen eines Abbilds Einzelhandel](build-retail-image.md)