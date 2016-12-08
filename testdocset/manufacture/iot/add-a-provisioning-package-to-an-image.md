---
author: kpacquer
Description: We'll create a provisioning package that contains some sample Wi-Fi settings.
ms.assetid: d9a50f87-e8c0-48da-89e7-0cdd542ce053
MSHAttr: PreferredLib:/library
title: "Übung 1 t: Hinzufügen von Netzwerk- und anderen Paket bereitstellungseinstellungen zu einem Bild"
ms.openlocfilehash: 1664c0ded9d1259082aeca3090798f8068443573
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="lab-1d-add-networking-and-other-provisioning-package-settings-to-an-image"></a>Übung 1 t: Hinzufügen von Netzwerk- und anderen Paket bereitstellungseinstellungen zu einem Bild

Es wird ein provisioning Paket erstellen, einige Beispiel Wi-Fi-Einstellungen enthält. Provisioning Paket in Windows Imaging und Konfiguration Designer (ICD) können Hinzufügen von apps, Treibern, Features oder viele allgemeine Einstellungen, wie IT-Gerätemanagement und Richtlinien zu ändern.

Um eine Wi-Fi, Ihre Pinnwand Test benötigen Wi-Fi-Unterstützung. Sie können einen Wi-Fi-Adapter/Dongle verwenden oder Verwenden einer Pinnwand wie die Brombeere Pi-3, die integrierte Wi-Fi hat.

Für diese Übungseinheit verwenden wir die Produktseite, die die Standard-app (Bertha), enthält, die Netzwerk-Status angezeigt wird.

Andere Einstellungen, die Bereitstellung Pakete verwenden:

* **Ändern der automatische Einstellungen im Bild Runtime aktualisieren**: [Windows 10 IoT Kern Pro Steuerelement Datei aktualisieren](https://developer.microsoft.com/en-us/windows/iot/docs/createiotcorepro)   

## <a name="span-idprerequisitesspanspan-idprerequisitesspanspan-idprerequisitesspanprerequisites"></a><span id="Prerequisites"></span><span id="prerequisites"></span><span id="PREREQUISITES"></span>Erforderliche Komponenten

* Finden Sie unter [Tools zum Anpassen von Windows IoT Core benötigt erhalten möchten](set-up-your-pc-to-customize-iot-core.md) , können Sie Ihre Techniker PC vorbereiten.

* Erstellen Sie einen Produktordner (Produktseite), die so eingerichtet, starten Sie auf den Standardwert (Bertha) app, siehe [Lab 1a: Erstellen eines grundlegenden Abbilds](create-a-basic-image.md) oder [Übung 1c: Fügen Sie eine Datei und einer Einstellung in der Registrierung zu einem Bild](add-a-registry-setting-to-an-image.md).

## <a name="span-idcreateyourprovisioningpackageinwindowsicdspanspan-idcreateyourprovisioningpackageinwindowsicdspanspan-idcreateyourprovisioningpackageinwindowsicdspancreate-your-provisioning-package-in-windows-icd"></a><span id="Create_your_provisioning_package_in_Windows_ICD"></span><span id="create_your_provisioning_package_in_windows_icd"></span><span id="CREATE_YOUR_PROVISIONING_PACKAGE_IN_WINDOWS_ICD"></span>Erstellen Sie Ihre Bereitstellung Paket in Windows ICD
1.  Starten Sie **Windows Imaging und Konfiguration Designer**.

2.  Klicken Sie auf **Datei &gt; neues Projekt**.

3.  In diesem Beispiel verwenden Sie den Namen "**ProductBProv**" für den Namen des Produkts, übernehmen Sie die Standardeinstellungen, und klicken Sie auf **Weiter**.

4.  Wählen Sie **Provisioning Paket &gt; Windows 10 IoT Core**.

5.  Klicken Sie auf der Seite **Importieren ein (optional) Bereitstellung Paket** auf **Fertig stellen**.

6.  Fügen Sie eine Beispiel-Einstellung:

    1.  Erweitern Sie **Runtime Einstellungen &gt; Connectivity Profile &gt; WLAN &gt; WLANSetting &gt; SSID**.

    2.  Geben Sie den Namen einer Wi-Fi-Netzwerkname beispielsweise ContosoWiFi ist, und klicken Sie auf **Hinzufügen**.

    3.  Erweitern Sie den **SSID > WLANXmlSettings > SecurityType** und wählen Sie eine Einstellung wie **Öffnen**.

    4.  Erweitern Sie die **SSID > WLANXmlSettings > AutoConnect** , und wählen Sie eine Einstellung wie **TRUE**.

    5.  Optional: Wenn mehr als ein WLAN-Netzwerk hinzufügen möchten, wechseln Sie wieder zum WLANSetting und wiederholen Sie den Vorgang.

7.  Optional: Hinzufügen von anderen apps, Treibern und Einstellungen über die Benutzeroberfläche. Finden Sie weitere Informationen finden Sie unter [Konfigurieren Anpassungen mithilfe von Windows ICD](https://msdn.microsoft.com/library/windows/hardware/dn916109).

8.  Exportieren Sie das provisioning-Paket. Klicken Sie beispielsweise auf **exportieren &gt; Provisioning-Pakets &gt; Weiter &gt; (deaktivieren Sie das Paket verschlüsseln) &gt; Weiter &gt; erstellen**. (Weitere Informationen finden Sie finden Sie unter [Exportieren eines Pakets Bereitstellung](https://msdn.microsoft.com/library/windows/hardware/dn916110). )

9.  Bei der **Fertig!** Klicken Sie auf den Link zum **Ausgabespeicherort**Sie Seite.

**Erstellen Sie einen Ordner für die Bereitstellung-Paket in das Test-Produkt**

1.  Erstellen Sie im Datei-Explorer einen neuen Ordner, C:\\IoT-ADK-AddonKit\\allgemeine\\Produkte\\Produktseite\\Provision

    Dieser Ordner ist Struktur wird verwendet, von dem Skript: Provisioning.Auto.pkg.xml-Datei im Ordner Provisioning.Auto. Es sind keine Änderungen erforderlich.

2.  Kopieren Sie die Dateien .ppkg .cat und customizations.xml in diesen Ordner.
    
    Benennen Sie die Dateien bei Bedarf mit Ihrer Produktnamen übereinstimmt:

    *  C:\\IoT-ADK-AddonKit\\allgemeine\\Produkte\\Produktseite\\Prov\\ProductBProv.cat
    *  C:\\IoT-ADK-AddonKit\\allgemeine\\Produkte\\Produktseite\\Prov\\ProductBProv.ppkg
    *  C:\\IoT-ADK-AddonKit\\allgemeine\\Produkte\\Produktseite\\Prov\\customizations.xml    
        
3.  Optional: Aktualisieren Sie customizations.xml, indem Sie alle gewünschten Änderungen. Weitere Informationen finden Sie unter [Windows Bereitstellungsdatei Antwort](https://msdn.microsoft.com/library/windows/hardware/dn916153) .

**Die automatische Bereitstellung Skripts Konfigurationsdatei für die Feature-Manifest und Produkt hinzufügen**

1.  Überprüfen die Paketdefinitionsdatei: Provisioning.Auto.pkg.xml: C:\\IoT-ADK-AddonKit\\allgemeine\\Pakete\\Provisioning.Auto\\Provisioning.Auto.pkg.xml. 

    Stellen Sie sicher, dass die Dateiquelle ordnungsgemäß aufgelöst wird. ($PROD) Prov.ppkg löst in C:\\IoT-ADK-AddonKit\\allgemeine\\Produkte\\Produktseite\\Prov\\ProductBProv.ppkg, sollte dieser den Namen Ihrer Bereitstellung Paketdatei übereinstimmen.

    ``` syntax
    <?xml version="1.0" encoding="utf-8"?>
      <Package xmlns="urn:Microsoft.WindowsPhone/PackageSchema.v8.00"
        Owner="$(OEMNAME)"
        OwnerType="OEM"
        ReleaseType="Production"
        Platform="$(BSPARCH)"
        Component="Provisioning"
        SubComponent="Auto">
        <Components>
           <OSComponent>
           <Files>
            <!--
            Source : Provisioning is product specific, so copied from the Product directory
            Destination : Auto provisioning folder which is C:\Windows\Provisioning\Packages
            -->
            <File Source="$(PRJDIR)\Products\$(PROD)\prov\$(PROD)Prov.ppkg"
                    DestinationDir="$(runtime.windows)\Provisioning\Packages" Name="ProvAuto.ppkg"/>
            </Files>
           </OSComponent>
        </Components>
    </Package>
    ```

2.  Stellen Sie sicher, dass die Paketdefinitionsdatei **% OEM-Datei\_Name%. Provisioning.Auto.cab"** und die Feature-ID: **OEM\_ProvAuto** verwiesen wird im Allgemeinen Feature Manifest C:\\IoT-ADK-AddonKit\\allgemeine\\Pakete\\OEMCommonFM.xml:

    ``` syntax
    <PackageFile Path="%PKGBLD_DIR%" Name="%OEM_NAME%.Provisioning.Auto.cab">
      <FeatureIDs>
        <FeatureID>OEM_ProvAuto</FeatureID>
        <FeatureID>OEMCommon_ALL</FeatureID>
      </FeatureIDs>
    </PackageFile>    
    ...
    <OEMFeatureGroups>
    <!-- Feature Constraints below -->
    <!-- This ensures that only one of the Provisioning package is included -->
      <FeatureGroup Constraint="ZeroOrOne">
        <FeatureIDs>
          <FeatureID>OEM_ProvAuto</FeatureID>
          <FeatureID>OEM_ProvManual</FeatureID>        
        </FeatureIDs>
    ```

3.  Aktualisieren der Testkonfigurationsdatei C:\\IoT-ADK-AddonKit\\Source -_< Bogen_>\\Produkte\\Produktseite\\TestOEMInput.xml:

    1.  Vergewissern Sie sich das allgemeine Feature Manifest: OEMCommonFM.xml enthalten ist. (Entfernen Sie Kommentarzeichen aus, falls erforderlich.)

        ``` syntax
        <AdditionalFMs>
          <!-- Including BSP feature manifest -->
          <AdditionalFM>%BSPSRC_DIR%\RPi2\Packages\RPi2FM.xml</AdditionalFM>
          <!-- Including OEM feature manifest-->
          <AdditionalFM>%COMMON_DIR%\Packages\OEMCommonFM.xml</AdditionalFM>
          <AdditionalFM>%SRC_DIR%\Packages\OEMFM.xml</AdditionalFM>
          <!-- Including the test features -->
          <AdditionalFM>%AKROOT%\FMFiles\arm\IoTUAPNonProductionPartnerShareFM.xml</AdditionalFM>
        </AdditionalFMs>
        ```

    2.  Stellen Sie sicher, dass das Feature: OEM_ProvAuto enthalten ist. (Entfernen Sie Kommentarzeichen aus, falls erforderlich.)

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
        </OEM>
        ```

## <a name="span-idbuildandtesttheimagespanspan-idbuildandtesttheimagespanspan-idbuildandtesttheimagespanbuild-and-test-the-image"></a><span id="Build_and_test_the_image"></span><span id="build_and_test_the_image"></span><span id="BUILD_AND_TEST_THE_IMAGE"></span>Erstellen Sie und Testen Sie das Abbild

Erstellen und das Bild mit den gleichen Verfahren aus flash [Lab 1a: Erstellen eines grundlegenden Abbilds](create-a-basic-image.md). Kurzes Format:

1.  Erstellen Sie das Bild aus der IoT Core Shell (`buildimage ProductB Test`).
2.  Installieren Sie das Abbild: Start **Windows IoT Core Dashboard** > Klicken Sie auf der Registerkarte **Setup ein neues Gerät** > Wählen Sie **Gerätetyp: benutzerdefinierte** >
3.  Über **die heruntergeladene Datei (Flash.ffu) an die SD-Karte Flash**: Klicken Sie auf **Durchsuchen**, navigieren Sie zur Datei FFU (C:\\IoT-ADK-AddonKit\\erstellen\\&lt;Bogen&gt;\\Produktseite\\Test\\ProductB.ffu), klicken Sie dann auf **Weiter**.
4.  Geben Sie Benutzername und Kennwort (der Standardwert lautet: Minwinpc / p@ssw0rd) > die Micro SD-Karte im Gerät zu platzieren, wählen Sie sie aus, akzeptieren der Lizenzbedingungen und klicken Sie auf *Installieren**. 
5.  Platzieren Sie die Visitenkarte in das Gerät IoT, und starten sie Sie.

Hinweis: Die Einstellungen für "Wi-Fi-Netzwerkverbindung" in den Menüs ignorieren Sie diese Einstellungen werden nicht verwendet. 

Nach einen Moment sollte der [IoT testen (Bertha) app](https://developer.microsoft.com/windows/iot/samples/iotdefaultapp) angezeigt werden dem grundlegende Informationen zu dem Bild angezeigt wird.

**Testen Sie, um festzustellen, ob Ihre Bereitstellung Einstellungen angewendet wurden**

1.  Trennen Sie alle Netzwerkkabel vom Gerät IoT.

2.  Wählen Sie die Standardwerte. Wählen Sie auf dem Bildschirm **Wir stellen Sie eine Verbindung** aus **diesen Schritt überspringen**.

3.  Wenn Ihre drahtlose Netzwerk befinden, sollte dieser Bildschirm anzeigen im Netzwerk erfolgreich eine Verbindung hergestellt, und zeigen eine IP-Adresse für das Netzwerk.

## <a name="span-idtestnetworkconnectionsspantest-network-connections-and-upload-apps"></a><span id="Test_network_connections"></span>Testen der Netzwerkverbindungen und Hochladen von apps

Sie können auf Ihr Gerät Portalseite zu beheben Netzwerkverbindungen, apps hochladen, oder finden weitere Informationen zu dem Gerät anschließen.

1.  Verbinden der Techniker PC und das Gerät mit dem gleichen Netzwerk. 

    Schließen Sie beispielsweise zum Verbinden von in einem verkabelten Netzwerk in einem Ethernet-Kabel.  Zum Verbinden von über drahtlose sicherstellen Sie, dass sowohl der Referenzcomputer und das IoT Core Gerät mit demselben drahtlosen Netzwerk verbunden sind.    

2.  Öffnen Sie auf Ihrem PC Techniker, Internet Explorer, und geben Sie in das Gerät IP-Adresse mit einem Präfix http:// und: 8080 Suffix. 

    ``` syntax
    http://10.123.45.67:8080
    ```

3.  Geben Sie bei Aufforderung Standard-Benutzername und das Kennwort des Geräts. (Der Standardwert lautet: Administrator \p@ssw0rd)

    Das [Windows-Gerät Portal](https://developer.microsoft.com/windows/iot/win10/tools/deviceportal)wird geöffnet. Von hier aus können Sie app-Pakete hochladen, finden Sie unter welche apps installiert sind, und zwischen ihnen wechseln.

4.  Klicken Sie auf **Netzwerk** > **Profile**.  Das Profil Wi-Fi, den, das Sie erstellt haben, sollte angezeigt werden. 
    
    Das Gerät automatisch eine Verbindung mit dem Netzwerk WiFi, klicken Sie dann unter **Verfügbare Netzwerke**herstellen kann sollte ein Häkchen neben dem Netzwerk angezeigt werden, die Sie konfiguriert haben.

    Wenn Ihr Netzwerk wie akzeptieren der Lizenzbedingungen Schritte erforderlich sind, das Gerät kann keine automatische-Verbindung herstellen.

## <a name="span-idtroubleshootingspantroubleshooting"></a><span id="Troubleshooting"></span>Problembehandlung

**Überprüfen Sie Ihre broadcast Wi-Fi-Häufigkeit (mit 2,4 GHz Vs 5 GHz)**. Einige Wi-Fi-Adapter wie den integrierten Wi-Fi-Adapter auf dem Brombeere Pi 3 unterstützen nur 2,4 GHz Wi-Fi-Netzwerke. Dies ist zwar die am häufigsten verwendeten Wi-Fi broadcast Häufigkeit viele Wi-Fi-Netzwerke bei Frequenzen von 5GHz übertragen. Ändern Sie die broadcast Häufigkeit oder verwenden Sie einen anderen Adapter.

**Bestätigen, die die Paket bereitstellungseinstellungen in Ihrem Netzwerk zu arbeiten**. Verwenden Sie einen Laptop-PC, um zu testen:

1.  Trennen Sie den Laptop vom Netzwerk: Klicken Sie auf das Netzwerksymbol in der Taskleiste, wählen Sie aus der drahtlosen Netzwerk und klicken Sie auf **Trennen**. 

2.  Vergewissern Sie sich, dass das Netzwerk nicht mehr verbunden ist.

3.  Installieren des Pakets für die Bereitstellung durch Doppelklicken auf ProductAProv.ppkg. Drahtlose Netzwerk sollte automatisch eine Verbindung herstellen.

**Überprüfen Sie, wenn das Gerät das Profil hinzugefügt wurde**

1.  Verbindung mit einem Ethernet-Verbindung zu dem Gerät.

2.  Verbindung mit einem SSH-Client, wie beispielsweise [kitten](http://the.earth.li/~sgtatham/putty/latest/x86/putty.exe).

3.  Wenn verbunden, überprüfen Sie, welche Profile installiert wurden:

    ```syntax
    netsh wlan show profiles
    ``` 

    Das Netzwerk sollte in der Liste der Benutzerprofile angezeigt werden.

## <a name="span-idnextstepsspanspan-idnextstepsspanspan-idnextstepsspannext-steps"></a><span id="Next_steps"></span><span id="next_steps"></span><span id="NEXT_STEPS"></span>Nächste Schritte

[Übung 1e: Hinzufügen eines Treibers zu einem Bild](add-a-driver-to-an-image.md) 
