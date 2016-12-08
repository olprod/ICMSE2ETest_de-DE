---
author: kpacquer
Description: We'll create some test files and registry keys to the image, again packaging them up so that they can be serviced after they reach your customers.
ms.assetid: 7ca2b835-4d36-43d9-b46f-d5d5d8410335
MSHAttr: PreferredLib:/library
title: "Übung 1c: Hinzufügen einer Datei und eine Einstellung in der Registrierung zu einem Bild"
ms.openlocfilehash: 5366dd09e57cf508a725ffad4286ef99b5ebacc4
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="lab-1c-add-a-file-and-a-registry-setting-to-an-image"></a>Übung 1c: Hinzufügen einer Datei und eine Einstellung in der Registrierung zu einem Bild

Dateien und Registrierungsschlüssel, die Sie Ihr Bild oft hinzufügen werden nicht speziell für eine Architektur. Für diese empfehlen wir, erstellen eine allgemeine-Paket, das Sie für alle Ihre Gerätearchitekturen verwenden können.
 
Wir erstellen einige Testdateien und Registrierungsschlüssel für das Bild und erneut zu packen sie einrichten, sodass sie bearbeitet werden können, nachdem sie Ihre Kunden erreichen.

Wir diese können die allgemeine Feature Manifest (OEMCommonFM.xml), die in X86, x 64 und ARM-Builds verwendet wird und weisen Sie ihr eine neues Feature-ID OEM\_FilesAndRegKeys.

Für diese Übungseinheit zunächst ein neues Produkt, Produktseite, damit später wir die IoT Beispiel-app verwenden können, zum Abrufen der IP-Adresse des unsere Gerät, und überprüfen Sie, ob unsere Dateien und Registrierungsschlüssel vorgenommen haben sie. 

## <a name="span-idprerequisitesspanspan-idprerequisitesspanspan-idprerequisitesspanprerequisites"></a><span id="Prerequisites"></span><span id="prerequisites"></span><span id="PREREQUISITES"></span>Erforderliche Komponenten

Finden Sie unter [Tools zum Anpassen von Windows IoT Core benötigt erhalten möchten](set-up-your-pc-to-customize-iot-core.md) , können Sie Ihre Techniker PC vorbereiten.

## <a name="span-idcreateyourtestfilesspanspan-idcreateyourtestfilesspanspan-idcreateyourtestfilesspancreate-your-test-files"></a><span id="Create_your_test_files"></span><span id="create_your_test_files"></span><span id="CREATE_YOUR_TEST_FILES"></span>Erstellen Sie die Testdateien

-   Erstellen Sie einige Beispieltextdateien mit dem Editor, deren TestFile1.txt und TestFile2.txt Titel.

## <a name="span-idbuildapackageforyourtestfilesspanspan-idbuildapackageforyourtestfilesspanspan-idbuildapackageforyourtestfilesspanbuild-a-package-for-your-test-files"></a><span id="Build_a_package_for_your_test_files"></span><span id="build_a_package_for_your_test_files"></span><span id="BUILD_A_PACKAGE_FOR_YOUR_TEST_FILES"></span>Erstellen eines Pakets für die Testdateien

1.  Führen Sie **C:\\IoT-ADK-AddonKit\\IoTCoreShell** als Administrator.

2.  Arbeitsordner für den Registrierungsschlüssel erstellen und Testen von Dateien, zum Beispiel:

    ``` syntax
    newcommonpkg Registry.FilesAndRegKeys
    ```

    An den neuen Ordner **C:\\IoT-ADK-AddonKit\\allgemeine\\Pakete\\Registry.FilesAndRegKeys\\**.

### <a name="span-idaddsamplefilestothepackagespanadd-sample-files-to-the-package"></a><span id="Add_sample_files_to_the_package"></span>Fügen Sie dem Paket Beispieldateien

1.  Kopieren Sie die Beispieldateien (TestFile1.txt und TestFile2.txt) in den neuen Ordner am **C:\\IoT-ADK-AddonKit\\allgemeine\\Pakete\\Registry.FilesAndRegKeys\\**.

2.  Aktualisieren die Paketdefinitionsdatei **C:\\IoT-ADK-AddonKit\\allgemeine\\Pakete\\Registry.FilesAndRegKeys\\Registry.FilesAndRegKeys.pkg.xml**:

    ein.  Entfernen Sie die Kommentarzeichen und Anweisungen.

    b.  Aktualisieren Sie die Werte des Registrierungsschlüssels auf eine neue Schlüsselname, Name und Wert enthalten.

    c.  Aktualisieren Sie die Datei Datenquellennamen TestFile1.txt und TestFile2.txt. Standardmäßig werden Dateien in C: platziert\\Windows\\System. Um den Zielspeicherort zu ändern, fügen Sie einen DestinationDir und einen Namen hinzu.
    
    Variablen wie $(runtime.root) werden in C: definiert\\Program Files (x86)\\Windows Kits\\10\\Tools\\Bin\\i386\\pkggen.cfg.xml.

    ``` syntax
      <OSComponent> 
         <RegKeys> 
             <RegKey KeyName="$(hklm.software)\$(OEMNAME)\Test">
                <RegValue Name="StringValue" Value="Test string" Type="REG_SZ"/>
                <RegValue Name="DWordValue" Value="12AB34CD" Type="REG_DWORD"/>
                <RegValue Name="BinaryValue" Value="12,AB,CD,EF" Type="REG_BINARY"/>
             </RegKey>
             <RegKey KeyName="$(hklm.software)\$(OEMNAME)\EmptyKey"/> 
         </RegKeys> 
         <Files> 
            <File Source="TestFile1.txt" /> 
            <File Source="TestFile2.txt"
                DestinationDir="$(runtime.root)\OEMInstall" Name="TestFile2.txt"/>  
         </Files> 
      </OSComponent> 
    ```

2.  Erstellen Sie in der Shell IoT Core das Paket. (Die `BuildPkg All` Befehl erstellt alles in den Quellordnern.)

    ``` syntax
    buildpkg Registry.FilesAndRegKeys
    ```

    Das Paket erstellt, das als **C:\\IoT-ADK-AddonKit\\erstellen\\&lt;Bogen&gt;\\Pckg\\&lt;OEM-Name&gt;. Registry.FilesAndRegKeys.cab**.

    Alle Pakete, die Sie erstellen werden im Ordner architekturspezifische angezeigt. Tipp: um schnell für eine andere Architektur neu konfigurieren, verwenden Sie **Setenv &lt;Bogen&gt;**, klicken Sie dann **`BuildPkg All`** alles für Ihre Architektur andere neu erstellt.

    **Problembehandlung**: Wenn eine Fehlermeldung angezeigt: "die ElementRegKeys im Namespace 'urn:Microsoft.WindowsPhone/PackageSchema.v8.00' Inhalt ist unvollständig", entfernen Sie die Kommentare und Anweisungen. Wenn Sie keinen Registrierungsschlüssel oder eine Datei einschließen möchten, entfernen Sie diese XML-Elemente an. 

## <a name="span-idupdateyourfeaturemanifestspanspan-idupdateyourfeaturemanifestspanspan-idupdateyourfeaturemanifestspanupdate-your-feature-manifest"></a><span id="Update_your_feature_manifest"></span><span id="update_your_feature_manifest"></span><span id="UPDATE_YOUR_FEATURE_MANIFEST"></span>Aktualisieren des Manifests feature

1.  Öffnen Sie die gemeinsamen Featuremanifestdatei **C:\\IoT-ADK-AddonKit\\allgemeine\\Pakete\\OEMCommonFM.xml**

2.  Erstellen eines neuen PackageFile-Abschnitts in der XML-DATEI mit der Paketdatei aufgeführt, und geben sie eine neue FeatureID, z. B. "OEM\_FilesAndRegKeys".

    ``` syntax
    <Features>
      <OEM>
        <!-- Feature definitions below -->
        <PackageFile Path="%PKGBLD_DIR%" Name="%OEM_NAME%.Registry.FilesAndRegKeys.cab">
          <FeatureIDs>
            <FeatureID>OEM_FilesAndRegKeys</FeatureID>
          </FeatureIDs>
        </PackageFile>
    ```

    Sie können nun Ihre Dateien und Registrierungsschlüssel auf Ihre Produkte hinzufügen, indem Sie einen Verweis auf dieses Feature Manifest und Feature-ID können


## <a name="span-idcreateanewproductspanspan-idcreateabasicimagespanspan-idcreateabasicimagespancreate-a-new-product"></a><span id="Create_a_new_product"></span><span id="create_a_basic_image"></span><span id="CREATE_A_BASIC_IMAGE"></span>Erstellen Sie ein neues Produkt

1.  Erstellen Sie einen neuen Produktordner. 

    ``` syntax
    newproduct ProductB
    ```

## <a name="span-idupdateyourconfigurationfilespanupdate-your-product-configuration-file"></a><span id="Update_your_configuration_file"></span>Aktualisieren Sie Ihre Produkt-Konfigurationsdatei

1.  Aktualisieren der Testkonfigurationsdatei C:\\IoT-ADK-AddonKit\\Source -_< Bogen_>\\Produkte\\Produktseite\\TestOEMInput.xml:

    Vergewissern Sie sich das Manifest Feature: **OEMCommonFM.xml** enthalten ist, entfernen Kommentarzeichen bei Bedarf.

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

2.  Aktualisieren Sie die Funktionen des Produkts enthalten: 

    ein. Stellen Sie sicher, die Beispiel-apps sind enthalten (insbesondere der app IOT_BERTHA).

    b. Hinzufügen von OEM-Funktionen: OEM_AppxMain, OEM_CustomCmd und OEM_ProvAuto, durch die Kommentierungstags entfernen (_<!----_>) in diesem Abschnitt. 

    c. Hinzufügen der FeatureID für Ihr Paket Registrierung Beispiel: OEM_FilesAndRegKeys.
    
    ``` syntax
    <Features>
      <Microsoft>
    
      ...
      
      <!-- Sample Apps, remove this when you introduce OEM Apps -->
      <Feature>IOT_BERTHA</Feature>
      <Feature>IOT_ALLJOYN_APP</Feature>
      <Feature>IOT_NANORDPSERVER</Feature>
      <Feature>IOT_SHELL_HOTKEY_SUPPORT</Feature>
      <Feature>IOT_APPLICATIONS</Feature>
      <Feature>IOT_ENABLE_ADMIN</Feature>
      </Microsoft>
      <OEM>
        <!-- Include BSP Features -->
        <Feature>RPI2_DRIVERS</Feature>
        <Feature>RPI3_DRIVERS</Feature>
        <!-- Include OEM features -->
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
4.  Geben Sie Benutzername und Kennwort (der Standardwert lautet: Minwinpc / p@ssw0rd) > die Micro SD-Karte im Gerät zu platzieren, wählen Sie sie aus, akzeptieren der Lizenzbedingungen und klicken Sie auf **Installieren**. 
5.  Platzieren Sie die Visitenkarte in das Gerät IoT, und starten sie Sie.

Nach einen Moment sollte der [IoT testen (Bertha) app](https://developer.microsoft.com/windows/iot/samples/iotdefaultapp) angezeigt werden dem grundlegende Informationen zu dem Bild angezeigt wird.

## <a name="span-idseeyourfilesspansee-if-your-files-made-it"></a><span id="See_your_files"></span>Überprüfen Sie, ob sie für Ihre Dateien vorgenommen wurde

1.  Verbinden Sie Ihre Techniker PC und das Gerät mit dem gleichen Ethernet-Netzwerk an. 

    Schließen Sie beispielsweise zum Verbinden von in einem verkabelten Netzwerk in einem Ethernet-Kabel. Schließen Sie ein Netzwerkkabel direkt von Ihrem PC-Techniker auf das Gerät zum Verbinden von direkt an das Gerät an.   

2.  Notieren Sie die IP-Adresse, beispielsweise 10.100.0.100, auf das Test-app. 

3.  Öffnen Sie auf Ihrem PC-Technikers, Datei-Explorer, und geben Sie die IP-Adresse des Geräts mit einer \\ \\ Präfix und \\c$ Suffix:

    ``` syntax
    \\10.100.0.100\c$
    ```

    Verwenden Sie die Devicename, das standardmäßige Administratorkonto und Kennwort anmelden. (Der Standardwert lautet: Minwinpc\\Administrator /p@ssw0rd)

4.  Überprüfen Sie, wenn die Dateien vorhanden sind. Schaue nach:

    \\\\10.100.0.100\c$\\Windows\\system32\\TestFile1.txt

    \\\\10.100.0.100\c$\\OEMInstall\\TestFile2.txt

## <a name="span-idseeyourregkeysspansee-if-your-registry-keys-exist"></a><span id="See_your_regkeys"></span>Überprüfen Sie, ob Ihre Registrierungsschlüssel vorhanden sein.

1.  Verbinden Sie auf der Techniker PC auf Ihrem Gerät mit einem SSH-Client, wie beispielsweise [kitten](http://the.earth.li/~sgtatham/putty/latest/x86/putty.exe). Verwenden Sie beispielsweise IP-Adresse und Port 22, um eine Verbindung mit dem Gerät, und melden Sie sich mit dem Administratorkonto und Kennwort. (Weitere Informationen finden Sie unter [SSH](https://developer.microsoft.com/en-us/windows/iot/docs/ssh).)

2.  Über die Befehlszeile im SSH-Client Abfrage an das System für den Registrierungsschlüssel.

    ``` syntax
    reg query HKLM\Software\Fabrikam\Test
    ```

    Dabei ist "Fabrikam" OEM-Name. Das Tool der Registrierung sollte Ihre Testwerte zurückgegeben.

## <a name="span-idnextstepsspanspan-idnextstepsspanspan-idnextstepsspannext-steps"></a><span id="Next_steps"></span><span id="next_steps"></span><span id="NEXT_STEPS"></span>Nächste Schritte

[Übung 1 t: Hinzufügen eines provisioning Pakets zu einem Bild](add-a-provisioning-package-to-an-image.md)
