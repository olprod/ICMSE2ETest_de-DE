---
author: kpacquer
Description: We're now going to take an app (like the sample Hello, World! app), and package it up so that it can be serviced after it reaches your customers.
ms.assetid: a801d768-0397-4f85-b68f-bd85ddcc3f1f
MSHAttr: PreferredLib:/library
title: "Übung 1 b: hinzufügen eine app für das Abbild"
ms.openlocfilehash: 1867f00397c07604a20c5cfcaf13c496b4c830d4
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="lab-1b-add-an-app-to-your-image"></a>Übung 1 b: hinzufügen eine app für das Abbild

Wir werden jetzt eine app zu übernehmen (wie im Beispiel [Hello, World!](https://developer.microsoft.com/windows/iot/samples/helloworld) App), oben zu packen, und Erstellen einer neuen Bilddatei, die auf neue Geräte geladen werden kann. 

Verwenden Sie für Hintergrund apps die gleiche-Methode zum Installieren und führen Sie sie aus. Beachten Sie, dass nur eine app als den Standard-app alle apps, die Installation mit dieser Methode ausführen als Hintergrund apps ausgewählt werden kann.

**Hinweis**  Wie wir dieses Handbuchs Fertigung durchgehen, starten ProjectA ähnelt in C: ist das Bild SampleA\\IoT-ADK-AddonKit\\Quelle Arm\\Produkte\\SampleA.

## <a name="span-idprerequisitesspanspan-idprerequisitesspanspan-idprerequisitesspanprerequisites"></a><span id="Prerequisites"></span><span id="prerequisites"></span><span id="PREREQUISITES"></span>Erforderliche Komponenten

Wir verwenden wir erstellte aus ProjectA Image [Lab 1a: Erstellen eines grundlegenden Abbilds](create-a-basic-image.md).

## <a name="span-idcreateandtestanwindowsappspanspan-idcreateandtestanwindowsappspanspan-idcreateandtestanwindowsappspancreate-and-test-an-windows-app"></a><span id="Create_and_test_an_Windows_app"></span><span id="create_and_test_an_windows_app"></span><span id="CREATE_AND_TEST_AN_WINDOWS_APP"></span>Erstellen und Testen einer Windows-app
Wenn Sie bereits erstellt und Ihre app getestet haben, können Sie diese Schritte überspringen.

1.  Erstellen einer app. Dies kann eine beliebige app ist ausgelegt für IoT Core, als ein Appx-Paket gespeichert sein. In unserem Beispiel verwenden wir die app [Hello, World](https://developer.microsoft.com/windows/iot/samples/helloworld) .

2.  Klicken Sie in Visual Studio zum Speichern des Hello, World-app als ein Paket Appx auf **Projekt > Store > App-Pakete erstellen** > **No** > **Weiter**. 

3.  Wählen Sie **Ausgabespeicherort: C:\HelloWorld** (oder alle anderen Pfade, die Leerzeichen enthalten nicht.)
    
4.  Wählen Sie **generieren app Bundle: nie**
    
5.  Klicken Sie auf **Erstellen**.

    Visual Studio erstellt die Datei Appx in C:\HelloWorld\HelloWorld_1.0.0.0_Debug_Test 

6.  Optional: [Testen der app](test-the-app.md). Beachten Sie, dass Sie die app als Teil beim Erstellen des Projekts bereits getestet haben können. 


## <a name="span-idpackagetheappspanspan-idpackagetheappspanspan-idpackagetheappspanpackage-the-app"></a><span id="Package_the_app"></span><span id="package_the_app"></span><span id="PACKAGE_THE_APP"></span>Packen Sie die app

**Erstellen eines Pakets für eine app**

1.  Open **C:\\IoT-ADK-AddonKit\\IoTCoreShell** als Administrator.


2.  Erstellen Sie einen Ordner für die app, beispielsweise:

    ``` syntax
    newAppxPkg "C:\HelloWorld\HelloWorld_1.0.0.0_ARM_Debug_Test\HelloWorld_1.0.0.0_ARM_Debug.appx" Appx.HelloWorld
    ```

    Dadurch wird erstellt einen neuen Arbeitsordner unter C:\\IoT-ADK-AddonKit\\Source -&lt;Bogen&gt;\\Pakete\\Appx.HelloWorld, die Dateien enthält, das zur Erstellung des Pakets verwendet wird.

    Problembehandlung: Wenn die Meldung angezeigt: "das System kann nicht die angegebene Datei nicht gefunden", kann es sein, da das Paket keine definierte abhängig ist.
    
3.  Erstellen Sie in der Shell IoT Core das Paket.

    ``` syntax
    buildpkg Appx.HelloWorld
    ```

    Das Paket erstellt, das als **C:\\IoT-ADK-AddonKit\\erstellen\\&lt;Bogen&gt;\\Pckg\\&lt;OEM-Name&gt;. Appx.HelloWorld.cab**.

    Extrem Buildfehler, und korrigieren Sie diese – Dies sind häufig ein Ergebnis von Dateinamen in der Paketdefinitionsdatei wird anders enthaltenen Dateien.

## <a name="span-idupdatethefeaturemanifestspanspan-idupdatethefeaturemanifestspanspan-idupdatethefeaturemanifestspanupdate-the-feature-manifest"></a><span id="Update_the_feature_manifest"></span><span id="update_the_feature_manifest"></span><span id="UPDATE_THE_FEATURE_MANIFEST"></span>Die Aktualisierung des Feature-Manifests


**Hinzufügen von app-Paket zu der Feature-Manifestdatei**

1.  Öffnen Sie die Feature-Manifestdatei **C:\\IoT-ADK-AddonKit\\Quell -&lt;Bogen&gt;\\Pakete\\OEMFM.xml**

2.  Erstellen eines neuen PackageFile-Abschnitts in der XML-DATEI mit der Paketdatei aufgeführt, und geben sie einen neuen FeatureID, z. B. "Appx\_HelloWorld".

    ``` syntax
    <?xml version="1.0" encoding="utf-8"?>
    <FeatureManifest xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns="http://schemas.microsoft.com/embedded/2004/10/ImageUpdate">
      <BasePackages/>
      <Features>
        <OEM>
          <!-- Feature definitions below -->
          <PackageFile Path="%PKGBLD_DIR%" Name="%OEM_NAME%.Appx.Main.cab">
            <FeatureIDs>
              <FeatureID>OEM_AppxMain</FeatureID>
            </FeatureIDs>
          </PackageFile>
        <PackageFile Path="%PKGBLD_DIR%" Name="%OEM_NAME%.Appx.HelloWorld.cab">
            <FeatureIDs>
              <FeatureID>OEM_AppxHelloWorld</FeatureID>
            </FeatureIDs>
          </PackageFile>
        </OEM>
        <OEMFeatureGroups/>
      </Features>
    </FeatureManifest>
    ```

    Sie können jetzt Ihre app zu Ihrer Produkte hinzufügen einen Verweis auf dieses Feature Manifest und Feature-ID können

## <a name="span-idupdatetheprojectsconfigurationfilesspanspan-idupdatetheprojectsconfigurationfilesspanspan-idupdatetheprojectsconfigurationfilesspanupdate-the-projects-configuration-files"></a><span id="Update_the_project_s_configuration_files"></span><span id="update_the_project_s_configuration_files"></span><span id="UPDATE_THE_PROJECT_S_CONFIGURATION_FILES"></span>Aktualisieren Sie das Projekt Konfigurationsdateien

**Ersetzen des Produkts Standard-app durch Ihren eigenen**

1.  Öffnen Sie Ihr Produkt Test-Konfigurationsdatei: **C:\\IoT-ADK-AddonKit\\Quell -&lt;Bogen&gt;\\Produkte\\Produkt a angezeigt\\TestOEMInput.xml**.

2.  Vergewissern Sie sich, sowohl die Feature-Manifestdatei, OEMFM.xml und der Feature-Manifestdatei: OEMCommonFM.xml, beide im Abschnitt AdditionalFMs aufgelistet, sind.

    ``` syntax
    <AdditionalFMs>
       <!-- Including BSP feature manifest -->
       <AdditionalFM>%BSPSRC_DIR%\RPi2\Packages\RPi2FM.xml</AdditionalFM>
       <!-- Including OEM feature manifest -->
       <AdditionalFM>%COMMON_DIR%\Packages\OEMCommonFM.xml</AdditionalFM>
       <AdditionalFM>%SRC_DIR%\Packages\OEMFM.xml</AdditionalFM>
       <!-- Including the test features -->
       <AdditionalFM>%AKROOT%\FMFiles\arm\IoTUAPNonProductionPartnerShareFM.xml</AdditionalFM>
    </AdditionalFMs>
    ```

3.  Ändern Sie die Funktionen des Produkts enthalten: 

    ein. Entfernen der Beispiel-apps Test durch Hinzufügen von Kommentar-Tags: _<!----_>. (Wir diese apps erneut in nachfolgenden Übungseinheiten verwenden.)

    b. Hinzufügen von OEM-Funktionen: OEM_AppxMain, OEM_CustomCmd und OEM_ProvAuto, durch die Kommentierungstags entfernen (_<!----_>) in diesem Abschnitt. 

    c. Hinzufügen der FeatureID für Ihre app-Paket Beispiel: OEM_AppxHelloWorld.
    
    ``` syntax
    <Features>
      <Microsoft>
    
      ...
      
      <!-- Sample Apps, remove this when you introduce OEM Apps -->
      <!--
      <Feature>IOT_BERTHA</Feature>
      <Feature>IOT_ALLJOYN_APP</Feature>
      <Feature>IOT_NANORDPSERVER</Feature>
      <Feature>IOT_SHELL_HOTKEY_SUPPORT</Feature>
      <Feature>IOT_APPLICATIONS</Feature>
      <Feature>IOT_ENABLE_ADMIN</Feature>
      -->
      </Microsoft>
      <OEM>
        <!-- Include BSP Features -->
        <Feature>RPI2_DRIVERS</Feature>
        <Feature>RPI3_DRIVERS</Feature>
        <!-- Include OEM features -->
        <Feature>OEM_AppxMain</Feature>
        <Feature>OEM_CustomCmd</Feature>
        <Feature>OEM_ProvAuto</Feature>
        <Feature>OEM_AppxHelloWorld</Feature>
     </OEM>
    ```

**Legen Sie die app zum automatischen installieren, und legen Sie selbst als Standard-app**

1.  Open **C:\\IoT-ADK-AddonKit\\Source -&lt;Bogen&gt;\\Produkte\\Produkt a angezeigt\\OEMCustomization.cmd**

2.  Empfohlen: Ändern des Geräts Standard-Benutzername und Kennwort.

3.  Entfernen Sie den ersten Satz von REM-Anweisung aus dem Codeblock beginnend mit "REM wenn vorhanden C:\AppInstall\AppInstall.cmd..", auf diese Weise können den AppInstall.cmd-Befehl aus, um Ihre app automatisch installiert.

    ``` syntax
    @echo off
    REM OEM Customization Script file
    REM This script if included in the image, is called everytime the system boots.

    REM Enable Administrator User
    net user Administrator p@ssw0rd /active:yes

    if exist C:\OEMTools\InstallAppx.cmd (
        REM Run the Appx Installer. This will install the appx present in C:\OEMApps\
        call C:\OEMTools\InstallAppx.cmd
    )

    if exist C:\AppInstall\AppInstall.cmd (
        REM Enable Application Installation for onetime only, after this the files are deleted.
        call C:\AppInstall\AppInstall.cmd > %temp%\AppInstallLog.txt
        if %errorlevel%== 0 (
            REM Cleanup Application Installation Files. Change dir to root so that the dirs can be deleted
            cd \
            rmdir /S /Q C:\AppInstall
         )
    )
    ```

## <a name="span-idbuildandtesttheimagespanspan-idbuildandtesttheimagespanspan-idbuildandtesttheimagespanbuild-and-test-the-image"></a><span id="Build_and_test_the_image"></span><span id="build_and_test_the_image"></span><span id="BUILD_AND_TEST_THE_IMAGE"></span>Erstellen Sie und Testen Sie das Abbild

Erstellen und das Bild mit den gleichen Verfahren aus flash [Lab 1a: Erstellen eines grundlegenden Abbilds](create-a-basic-image.md). Kurzes Format:

1.  Erstellen Sie das Bild aus der IoT Core Shell (`buildimage ProductA Test`).
2.  Installieren Sie das Abbild: Start **Windows IoT Core Dashboard** > Klicken Sie auf der Registerkarte **Setup ein neues Gerät** > Wählen Sie **Gerätetyp: benutzerdefinierte** >
3.  Über **die heruntergeladene Datei (Flash.ffu) an die SD-Karte Flash**: Klicken Sie auf **Durchsuchen**, navigieren Sie zur Datei FFU (C:\\IoT-ADK-AddonKit\\erstellen\\&lt;Bogen&gt;\\Produkt a angezeigt\\Test\\ProductA.ffu), klicken Sie dann auf **Weiter**.
4.  Geben Sie Benutzername und Kennwort (der Standardwert lautet: Minwinpc / p@ssw0rd) > die Micro SD-Karte im Gerät zu platzieren, wählen Sie sie aus, akzeptieren der Lizenzbedingungen und klicken Sie auf **Installieren**. 
4.  Platzieren Sie die Visitenkarte in das Gerät IoT, und starten sie Sie.

Nach kurzer während das Gerät automatisch gestartet werden sollte, und Ihre app angezeigt werden sollte.

## <a name="span-idnextstepsspanspan-idnextstepsspanspan-idnextstepsspannext-steps"></a><span id="Next_steps"></span><span id="next_steps"></span><span id="NEXT_STEPS"></span>Nächste Schritte

[Übung 1c: Hinzufügen einer Datei und eine Einstellung in der Registrierung zu einem Bild](add-a-registry-setting-to-an-image.md)

 ## <a name="span-idrelatedtopicsspanspan-idrelatedtopicsspanspan-idrelatedtopicsspanrelated-topics"></a><span id="Related_topics"></span><span id="related_topics"></span><span id="RELATED_TOPICS"></span>Verwandte Themen

[Aktualisieren von apps auf Ihren Geräten IoT Core](../../service/iot/updating-iot-core-apps.md)