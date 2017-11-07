---
author: kpacquer
Description: We'll take our test image and convert it to a retail build.
MS-HAID: p\_iot\_core.build\_retail\_image
MSHAttr: PreferredLib:/library
title: "Übung 1f: Erstellen eines Abbilds Einzelhandel"
ms.openlocfilehash: 66e8cdbd78c765dcf4399bc222c0da949a8864f2
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="lab-1f-build-a-retail-image"></a>Übung 1f: Erstellen eines Abbilds Einzelhandel

Wir '' ll haben unsere Anpassungen, die Tags zusammen und Testen Sie diese in einer Verkaufsversion. 

## <a name="span-idprerequisitesspanspan-idprerequisitesspanspan-idprerequisitesspanprerequisites"></a><span id="Prerequisites"></span><span id="prerequisites"></span><span id="PREREQUISITES"></span>Erforderliche Komponenten

-   [Übung 1a: Erstellen eines grundlegenden Abbilds](create-a-basic-image.md)
-   [Übung 1 b: hinzufügen eine app für das Abbild](deploy-your-app-with-a-standard-board.md)
-   [Übung 1c: Hinzufügen einer Datei und eine Einstellung in der Registrierung zu einem Bild](add-a-registry-setting-to-an-image.md)
-   [Übung 1 t: Hinzufügen von Netzwerk- und anderen Paket bereitstellungseinstellungen zu einem Bild](add-a-provisioning-package-to-an-image.md)
-   [Übung 1e: Hinzufügen eines Treibers zu einem Bild](add-a-driver-to-an-image.md)

## <a name="span-idaddyourapptotheretailconfigurationfilespanspan-idaddyourapptotheretailconfigurationfilespanspan-idaddyourapptotheretailconfigurationfilespanadd-your-app-to-the-retail-configuration-file"></a><span id="Add_your_app_to_the_retail_configuration_file"></span><span id="add_your_app_to_the_retail_configuration_file"></span><span id="ADD_YOUR_APP_TO_THE_RETAIL_CONFIGURATION_FILE"></span>Hinzufügen der app in die Konfigurationsdatei für den Einzelhandel

1.  Öffnen Sie Ihr Produkt Retail-Konfigurationsdatei: **C:\\IoT-ADK-AddonKit\\Source -&lt;Bogen&gt;\\Produkte\\Produkt a angezeigt\\RetailOEMInput.xml**...

2.  Fügen Sie Ihrem Feature Manifest OEMFM.xml, in der Liste der AdditionalFMs hinzu. Fügen Sie zur selben Zeit, das Feature Manifest: OEMCommonFM.xml, die den OEM enthält\_CustomCmd-Paket, das Ihre app beim ersten Start konfiguriert:

    ``` syntax
    <AdditionalFMs>
        <AdditionalFM>%AKROOT%\FMFiles\arm\IoTUAPRPi2FM.xml</AdditionalFM>
        <AdditionalFM>%AKROOT%\FMFiles\arm\RPi2FM.xml</AdditionalFM>
        <AdditionalFM>%SRC_DIR%\Packages\OEMFM.xml</AdditionalFM>
        <AdditionalFM>%COMMON_DIR%\Packages\OEMCommonFM.xml</AdditionalFM>
      </AdditionalFMs>
    ```

3.  Hinzufügen der FeatureIDs für die Ihre app-Paket, und der OEM\_CustomCmd-Paket.

    ``` syntax
    <OEM> 
       <!-- Include BSP Features -->
       <Feature>RPi2_DRIVERS</Feature> 
       <Feature>RPi3_DRIVERS</Feature>
       <!-- Include OEM features -->
       <Feature>OEM_CustomCmd</Feature> 
       <Feature>OEM_ProvAuto</Feature>
       <Feature>OEM_AppxHelloWorld</Feature> 
       <Feature>OEM_FilesAndRegKeys</Feature>
       <Feature>OEM_DriverHelloBlinky</Feature> 
    </OEM>
    ```
    
    OEM_CustomCmd ist erforderlich, um die app-Installation auslösen.
    
    Ziehen Sie in der Bereitstellung Paket ist OEM_ProvAuto erforderlich.
    
    OEM_FilesAndRegKeys, OEM_AppxHelloWorld und OEM_DriverHelloBlinky wurden Beispielpakete, die in vorherigen Übungseinheiten hinzugefügt wurden.

## <a name="span-idcopyinprovisioningpackagesspancopy-in-the-provisioning-package-from-productb-into-producta"></a><span id="Copy_in_provisioning_packages"></span>Kopieren Sie in der Bereitstellung-Paket aus Produktseite in Produkt a angezeigt.

1.  Erstellen Sie im Datei-Explorer einen neuen Ordner, C:\\IoT-ADK-AddonKit\\Produkte\\Produkt a angezeigt\\Provision

2.  Kopieren Sie die Dateien .ppkg .cat und customizations.xml in diesen Ordner.
    
    Benennen Sie die Dateien auf (Ihr Produkt name)Prov.cat und (z. B. ProductAProv.cat und ProductAProv.ppkg Ihrer Produkt-name)Prov.ppkg.

### <a name="span-idbuildandcreatetheimagespanspan-idbuildandcreatetheimagespanspan-idbuildandcreatetheimagespanbuild-and-create-the-image"></a><span id="Build_and_create_the_image"></span><span id="build_and_create_the_image"></span><span id="BUILD_AND_CREATE_THE_IMAGE"></span>Erstellen Sie und erstellen Sie das Abbild

**Erstellen Sie das Bild**

1.  [Fordern Sie ein Zertifikat zum Signieren von Code](https://msdn.microsoft.com/library/windows/hardware/hh801887(v=vs.85).aspx).

2.  Konfigurieren Sie das Cross-signiertes Zertifikat zum Signieren Retail verwendet werden. Bearbeiten Sie setsignature.cmd-Datei, um SIGNTOOL_OEM_SIGN festzulegen:

    ``` syntax
    set SIGNTOOL_OEM_SIGN=/s my /i "Issuer" /n "Subject" /ac "CrossCertRoot" /fd SHA256
    ```
    
    -  Aussteller: Aussteller des Zertifikats (finden Sie unter Certificate -> Details-Aussteller >)
    
    -  Betreff: Im Zertifikat des Antragstellers (finden Sie unter Certificate -> Details -> Betreff)
    
    -  CrossCertRoot: Microsoft bereitgestellten Rechtwinklige Zertifikat Stamm-. Finden Sie unter Cross-Zertifikatliste [Kreuzzertifikate für Kernel-Moduscode](https://msdn.microsoft.com/windows/hardware/drivers/install/cross-certificates-for-kernel-mode-code-signing#cross-certificate-list)signieren.
    
    
2.  Aktivieren Sie in der Shell IoT Core Retail Signierung.

    ``` syntax
    retailsign On
    ```
    
3.  Erstellen Sie alles, bei dem die Pakete, damit sie Einzelhandel sind angemeldet neu.

    ``` syntax
    buildpkg all
    ```

4.  Erstellen Sie in der Shell IoT Core das Bild:

    ``` syntax
    buildimage ProductA Retail
    ```

    Dadurch wird die Produktbinärdateien unter C: erstellt\\IoT-ADK-AddonKit\\erstellen\\&lt;Bogen&gt;\\Produkt a angezeigt\\Verkaufsversion\\Flash.FFU.

5.  Starten Sie **Windows IoT Core Dashboard** &gt; **Setup ein neues Gerät** &gt; **benutzerdefinierte**, und rufen Sie Ihr Bild. Tragen Sie die Micro SD-Karte das Gerät, wählen Sie sie aus, akzeptieren der Lizenzbedingungen, und klicken Sie auf **Installieren**. Damit wird die vorherige Abbildung durch unser neues Bild ersetzt.

6.  Platzieren Sie die Visitenkarte in das Gerät IoT, und starten sie Sie.

    Nach kurzer während das Gerät automatisch gestartet werden sollte, und Ihre app angezeigt werden sollte.

**Überprüfen Sie, ob alles ordnungsgemäß funktioniert**

Mit Verkaufsversionen werden Sie kann nicht in das Gerät mit dem SSH-Clients oder mithilfe von der Webschnittstelle protokolliert. Alle Dateien und Registrierungsschlüssel, denen Ihre app beruht sollten jedoch weiterhin funktionsfähig.

## <a name="span-idnextstepsspanspan-idnextstepsspanspan-idnextstepsspannext-steps"></a><span id="Next_steps"></span><span id="next_steps"></span><span id="NEXT_STEPS"></span>Nächste Schritte

- [Übung 2: Erstellen Ihrer eigenen Board Support-Paket](create-a-new-bsp.md)