---
author: kpacquer
Description: Erstellen eigener Board Support-Paket (BSP)
title: "Übung 2: Erstellen Ihrer eigenen Board Support-Paket (BSP)"
ms.openlocfilehash: 46601569c767124d94150145af56cc7a619703c3
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="lab-2-creating-your-own-board-support-package-bsp"></a>Übung 2: Erstellen Ihrer eigenen Board Support-Paket (BSP)

Eine BSP enthält eine Reihe von Gerätetreibern, die speziell für die Komponenten/Silicon in die Pinnwand verwendet werden. Diese werden von der Komponente Herstellern bereitgestellt / Halbleiterhersteller meist in Form von INF und zugehörige.sys/.dll Dateien. 

Erstellen Sie ein neues Paket für Board-Unterstützung (BSP) Wenn:

-  Erstellen eines neuen Hardare Entwurfs

-  Ersetzen einen Treiber oder eine Komponente auf eine vorhandene Hardware-design

Ob Sie eine neue BSP erstellen oder Ändern einer vorhandenen BSP, werden Sie der Besitzer. Auf diese Weise können Sie entscheiden, ob Aktualisierungen So installieren Sie auf Ihrer bewertungseinrichtungen zulässig sind.

In unserem Labor erstellen wir eine neue BSP basierend auf Brombeere Pi-2, entfernen den vorhandenen GPIO Treiber und mit dem Beispiel GPIO Treiber ersetzen: [Hello, Blinky!](https://developer.microsoft.com/windows/iot/samples/driverlab).

## <a name="span-idcreateanewbspworkingfolderspanspan-idcreateanewbspworkingfolderspanspan-idcreateanewbspfilespancreate-a-new-bsp-working-folder"></a><span id="Create_a_new_BSP_working_folder"></span><span id="create_a_new_bsp_working_folder"></span><span id="CREATE_A_NEW_BSP_FILE"></span>Erstellen Sie einen neuen BSP Arbeitsordner

1.  Erstellen Sie einen BSP Arbeitsordner, den Sie ändern möchten.

    ``` syntax
    newbsp MyRPi2
    ```

## <a name="span-idaddpackagesintothefeaturemanifestspanadd-packages-into-the-feature-manifest"></a><span id="Add_packages_into_the_feature_manifest"></span>Hinzufügen von Paketen in der Feature-Manifestdatei

1.  Öffnen Sie die Feature-Manifestdatei für die neue BSP, \\IoT-ADK-AddonKit\\Quell -&lt;Bogen&gt;\\BSP\\MyRpi2\\MyRpi2FM.xml.

    Öffnen Sie in ein anderes Fenster Manifest Feature Himbeeren Pi 2 als Vorlage verwenden.

2.  Fügen Sie die Basis-Pakete (BasePackages) hinzu.
   
    *  UEFI-Treiber für die Bootpartition (RASPBERRYPI. RPi2.BootFirmware.cab)

    *  Treiber erforderliche für UpdateOS (PA. PlatExtensions.UpdateOS.cab)

    *  Starten Sie die Konfiguration von dateneinstellungen (Microsoft-IoTUAP-RPi2-BCD-Package.cab)

    *  Obligatorische Gerätetreiber (bcm2836sdhc.cab, dwcUsbOtg.cab rpiq.cab)
       
       Beim Erstellen Ihrer eigenen BSP kommt es vor einen Treiber und einen Treiber und in einigen Fällen eine Netzwerktreiber erforderlich ist.

    *  Gerätespezifische Anpassungen
    
    **Kopieren Sie nicht in:**
    
    *  **Für die Zielgruppenadressierung Geräteinformationen (DeviceTargetingInfo.cab)**  Für Microsoft unterstützte Plattformen wie RPi2, MBM(x86) und Dragonboard ist dieses Paket erforderlich.  Für benutzerdefinierte BSPs wie der folgende darf dieses Paket nicht eingeschlossen werden. Fügen Sie stattdessen die Feature-ID: IOT_GENERIC_POP in der Datei OEMInput. Dadurch wird verhindert, dass Ihr Gerät empfangen von Updates aus dem ursprünglichen BSP Hersteller, der sich Ihre Änderungen Wischen konnte. 

        
4.  Kopieren Sie in das Gerät Layout und die Plattform Pakete (DeviceLayoutPackages, OEMDevicePlatformPackages).

    Beachten Sie, dass die OEMDevicePlatform.xml und die devicelayout.xml in einem einzelnen Paket, beispielsweise DeviceLayout.MBR4GB verpackt werden können. Das gleiche Paket dann als Eingabe in den beiden Abschnitten angegeben werden kann (beispielsweise unter <OEMDevicePlatformPackages> und <DeviceLayoutPackages>).  Weitere Informationen finden Sie unter [Gerät Layout](device-layout.md).
    
5.  Kopieren Sie in Features (Features).
    
    Kopieren Sie in der gewünschten Features. Schließen Sie aus, die Sie dem Projekt nicht angewendet werden.
    
    Kopieren Sie beispielsweise in den einzelnen der Treiber **mit Ausnahme** des vorhandenen GPIO-Treibers:
    ``` syntax
     <PackageFile Path="$(mspackageroot)\Retail\$(cputype)\$(buildtype)" Name="RASPBERRYPI.RPi2.GPIO.cab">
        <FeatureIDs>
          <FeatureID>RPI2_DRIVERS</FeatureID>
        </FeatureIDs>
      </PackageFile>
    ```
    
    Hinweis: Um Gruppierung Pakete zu erleichtern, können Sie diese in eine oder mehrere Feature-IDs zusammenfassen. Verwenden Sie beispielsweise alle optionalen Brombeere Pi-2-Treiber die Feature-ID: RPI2_DRIVERS.

6.  Fügen Sie der Treiber HelloBlinky hinzu:
    
    ``` syntax
        <PackageFile Path="%PKGBLD_DIR%" Name="%OEM_NAME%.Drivers.HelloBlinky.cab">
          <FeatureIDs>
            <FeatureID>RPI2_DRIVERS</FeatureID>
          </FeatureIDs>
        </PackageFile>
    ```

## <a name="span-idcreateanewproductfolderspanspan-idcreateanewproductandfolderspanspan-idcreateanewproductfolderspancreate-a-new-product-folder"></a><span id="Create_a_new_product_folder"></span><span id="create_a_new_product_and_folder"></span><span id="CREATE_A_NEW_PRODUCT_FOLDER"></span>Erstellt einen neuen Produktordner

1.  Erstellen Sie einen neuen Produkt Arbeitsordner, Ihren Namen BSP am Ende hinzufügen.

    ``` syntax
    newproduct ProductB MyRpi2
    ```

    Dadurch wird den Ordner erstellt: C:\\IoT-ADK-AddonKit\\Quell -&lt;Bogen&gt;\\Produkte\\Produktseite, die mit der neuen BSP verknüpft ist.

## <a name="span-idupdatetheprojectsconfigurationfilesspanspan-idupdatetheprojectsconfigurationfilesspanspan-idupdatetheprojectsconfigurationfilesspanupdate-the-projects-configuration-files"></a><span id="Update_the_project_s_configuration_files"></span><span id="update_the_project_s_configuration_files"></span><span id="UPDATE_THE_PROJECT_S_CONFIGURATION_FILES"></span>Aktualisieren Sie das Projekt Konfigurationsdateien

1.  Öffnen Sie Ihr Produkt Test-Konfigurationsdatei: **C:\\IoT-ADK-AddonKit\\Quelle Arm\\Produkte\\Produktseite\\TestOEMInput.xml**.

2.  Fügen Sie FeatureIDs hinzu:
    
    -  Hinzufügen der FeatureID: IOT_GENERIC_POP OS nur Updates abrufen.

    -  Hinzufügen der FeatureIDs: IOT_DISABLE_UMCI und IOT_ENABLE_TESTSIGNING Testbinärdateien und Pakete ermöglichen arbeiten.

    -  Optional: Hinzufügen der FeatureID für die anderen apps und Testen von Paketen: OEM_AppxHelloWorld, OEM_CustomCmd, OEM_FileAndRegKey, die Sie in Übung 1 erstellt haben.

       ``` syntax
       <Microsoft>
          <Feature>IOT_GENERIC_POP</Feature>
       ...
       </Microsoft>
    
       <OEM> 
          <Feature>RPI2_DRIVERS</Feature> 
          <Feature>PRODUCTION</Feature> 
          <Feature>IOT_DISABLE_UMCI</Feature> 
          <Feature>IOT_ENABLE_TESTSIGNING</Feature> 
          <Feature>OEM_CustomCmd</Feature> 
          <Feature>OEM_AppxHelloWorld</Feature> 
          <Feature>OEM_FileAndRegKey</Feature> 
        </OEM>
    ```

## <a name="span-idbuildandtesttheimagespanspan-idbuildandtesttheimagespanspan-idbuildandtesttheimagespanbuild-and-test-the-image"></a><span id="Build_and_test_the_image"></span><span id="build_and_test_the_image"></span><span id="BUILD_AND_TEST_THE_IMAGE"></span>Erstellen Sie und Testen Sie das Abbild

**Erstellen Sie das Bild**

1.  Erstellen Sie in der Shell IoT Core das Bild:

    ``` syntax
    createimage ProductB Test
    ```

    Dadurch wird die Produktbinärdateien unter C: erstellt\\IoT-ADK-AddonKit\\erstellen\\&lt;Bogen&gt;\\Produktseite\\Flash.FFU.

2.  Starten Sie **Windows IoT Core Dashboard** &gt; **Setup ein neues Gerät** &gt; **benutzerdefinierte**, und rufen Sie Ihr Bild. 

    Tragen Sie die Micro SD-Karte das Gerät, wählen Sie sie aus, akzeptieren der Lizenzbedingungen, und klicken Sie auf **Installieren**. Damit wird die vorherige Abbildung durch unser neues Bild ersetzt.

3.  Platzieren Sie die Visitenkarte in das Gerät IoT, und starten sie Sie.

    Nach kurzer während das Gerät automatisch gestartet werden sollte, und Ihre app angezeigt werden sollte.

**Überprüfen Sie, um festzustellen, ob der Treiber funktioniert**

1.  Verwendung der [Testen von Prozeduren in der Hello Blinky! Lab](https://developer.microsoft.com/windows/iot/samples/driverlab3) zum Testen des Treibers.

## <a name="span-idnextstepsspanspan-idnextstepsspanspan-idnextstepsspannext-steps"></a><span id="Next_steps"></span><span id="next_steps"></span><span id="NEXT_STEPS"></span>Nächste Schritte
Herzlichen Glückwunsch, Sie haben Übung 2 abgeschlossen. 

[Übung 3: Update apps](../../service/iot/updating-iot-core-apps.md)

##  <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="Related_topics"></span>Verwandte Themen
[Gerät layout](device-layout.md)