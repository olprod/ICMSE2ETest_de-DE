---
title: "Erstellen Sie ein Feature und in einem Bild einschließen"
description: "In diesem Thema zeigt, wie ein Feature erstellen und Hinzufügen eines Bilds."
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 85aea68e-0031-4353-9295-38d1c5d3928c
ms.openlocfilehash: 823ee6d45431df5954f25bc46763e472b0df1a91
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="create-a-feature-and-include-it-in-an-image"></a>Erstellen Sie ein Feature und fügen Sie es in einem Bild


In diesem Thema wird das Erstellen eines Features und Hinzufügen eines Bilds veranschaulicht.

## <a name="a-href-idprocess-overview---adding-a-test-app-featureaprocess-overview-adding-a-test-app-feature"></a><a href="" id="process-overview---adding-a-test-app-feature"></a>Übersicht über den Upgradeprozess – Hinzufügen eines Test-app-Features


Zum Erstellen eines Features, und fügen es zu einem Bild, müssen Sie die folgenden Schritte ausführen.

1.  Generieren Sie das Paket, das Test-app enthält.

2.  Erstellen Sie die Feature-Manifestdatei, die das Paket verweist.

3.  Fügen Sie die Feature-Manifestdatei und das Test-app-Feature zur Datei OEMInput.xml.

4.  Generieren Sie das Abbild, melden Sie sich das Bild, und es auf das Gerät flash.

5.  Stellen Sie sicher, dass das Feature erwartungsgemäß funktioniert.

![OEM\-Feature\-Erstellung\-Verpackung\-Szenario](images/oem-feature-creation-packaging-scenario.png)

## <a name="a-href-idwalkthrough---adding-a-test-app-to-a-test-imageawalkthrough-adding-a-test-app-to-a-test-image"></a><a href="" id="walkthrough---adding-a-test-app-to-a-test-image"></a>Exemplarische Vorgehensweise: Hinzufügen einer Test-app zu einer Testbild


In diesem Abschnitt werden die Schritte aus, denen Sie zum Hinzufügen einer Test-app zu einem Test-Abbild durchführen müssen. Bevor Sie mit dieser exemplarischen Vorgehensweise beginnen können, müssen Sie zuerst eine einfache Test-app erstellen. Nachdem die Anwendung erstellt wurde, können Sie mit dieser exemplarischen Vorgehensweise fortfahren.

### <a name="generate-the-test-app-package"></a>Generieren Sie das Test-app-Paket

In dieser exemplarischen Vorgehensweise wird davon ausgegangen, dass Sie bereits eine Test app mit dem Namen *TestApplication.exe*erstellt haben. Generieren Sie ein Paket, das diese app enthält, indem Sie die folgenden Schritte aus.

1.  Erstellen Sie ein Verzeichnis *TestApplication* aufgerufen und kopieren Sie die TestApplication.exe-Datei, die Sie in das Verzeichnis in Visual Studio erstellt haben.

2.  Erstellen Sie eine Textdatei mit dem Namen *TestApplication.pkg.xml* , das enthält die folgenden Paketdefinitionsdatei XML.

    ``` syntax
    <?xml version="1.0" encoding="utf-8" ?> 
      <Package xmlns="urn:Microsoft.WindowsPhone/PackageSchema.v8.00" Owner="Contoso" 
    OwnerType="OEM" 
    ReleaseType="Test" 
    Platform="DCD600" 
    Component="TestApps" 
    SubComponent="TestApplication"
    Partition="Data">

     <Macros>
      <Macro Id="testDir" Value="\test" /> 
     </Macros>
     
     <Components>
       <OSComponent>
         <Files>
           <File Source="TestApplication.exe" DestinationDir="$(testDir)" /> 
         </Files>
       </OSComponent>
      </Components>
    </Package>
    ```

    Sie können die Attribute Besitzer und Plattform entsprechend den Namen der Name Ihrer Organisation und den Namen des Geräts aktualisieren. Diese Änderungen Attribut werden der Name der generierten Paket ändern.

    Die &lt;Makro&gt; -Element wird zum Angeben der * \\Daten\\testen* Zielverzeichnis auf dem Gerät.

3.  Öffnen Sie ein Eingabeaufforderungsfenster Administrator, um das Paket zu erstellen.

4.  Anzeigen der Umgebungsvariablen durch eingeben **FESTGELEGT** , in das Eingabeaufforderungsfenster. Suchen Sie nach *WPDKCONTENTROOT* zu bestätigen, dass die Build-Umgebung ordnungsgemäß konfiguriert ist. Auf einem Windows 64-Bit-PC sollte der Pfad ungefähr folgendermaßen aussehen.

    ``` syntax
    ...
    WPDKCONTENTROOT=C:\Program Files (x86)\Windows Phone Kits\10
    ```

5.  Das Paket mit PkgGen zu generieren. Enthalten Sie die Versionsnummer der 1.0.0.0. Der Parameter/config verweist auf den Speicherort der pkggen.cfg.xml-Datei.

    ``` syntax
    C:\TestApplication>PkgGen TestApplication.pkg.xml /version:1.0.0.0 /config:" %WPDKCONTENTROOT% \Tools\bin\i386\pkggen.cfg.xml"
    ```

6.  Wenn PkgGen erfolgreich das Paket erstellt wird, sollten sie Ausgabe zurück, ähnlich der folgenden ist.

    ``` syntax
    Microsoft (C) pkggen 8.0.12134.0

    info: Using external macro file: 'C:\Program Files (x86)\Windows Phone Kits\10\
    Tools\bin\i386\pkggen.cfg.xml'
    info: Building project file C:\TestApplication\TestApplication.
    pkg.xml
    info: Building package '.\Contoso.TestApps.TestApplication.spkg'
    info: Adding file 'TestApplication.exe' to package '.\Contoso.TestApps.TestApplication.spkg' as '\test\TestApplication.exe'
    info: Done package ".\Contoso.TestApps.TestApplication.spkg"
    info: Packages are generated to . successfully
    ```

Weitere Informationen zum Arbeiten mit Paketen finden Sie unter [Creating Pakete](creating-mobile-packages.md).

### <a name="create-the-feature-manifest-file"></a>Erstellen der Feature-Manifestdatei

Erstellen eine Featuremanifestdatei, die definieren, einen TEST\_APP OEM-Feature mithilfe des folgenden Verfahrens.

1.  Erstellen einer Featuremanifestdatei, mit dem Namen *OEMCustomAppFM.xml* im folgenden Verzeichnis:

    ``` syntax
    %WPDKCONTENTROOT%\FMFiles
    ```

2.  Definieren Sie den TEST mit\_APP-Feature mithilfe der *OEMCustomAppFM.xml* -Datei den folgenden XML-CODE hinzufügen.

    ``` syntax
    <?xml version="1.0" encoding="utf-8"?>  
    <FeatureManifest xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns="http://schemas.microsoft.com/embedded/2004/10/ImageUpdate">  
    <!--  TEST_APP FM File 4/30/2015   -->
      <Features>  
        <OEM>  
          <PackageFile Path="C:\TestApplication\" Name="Contoso.TestApps.TestApplication.spkg">  
            <FeatureIDs>  
              <FeatureID>TEST_APP</FeatureID>  
            </FeatureIDs>  
          </PackageFile>  
        </OEM>  
      </Features>  
    </FeatureManifest>
    ```

Weitere Informationen zum Feature Manifeste finden Sie unter [Feature Dateiinhalten manifest](feature-manifest-file-contents.md).

### <a name="add-the-feature-to-the-oeminput-file"></a>Fügen Sie das Feature zur Datei OEMInput

Hinzufügen des TESTS\_APP OEM-Feature in die Datei OEMInput.xml die folgenden Schritte aus.

1.  In dieser exemplarischen Vorgehensweise wird davon ausgegangen, dass Sie eine vorhandene, Funktionstests OEMInput-Datei TShell verfügen. Finden Sie weitere Informationen zum Erstellen von Test-Bilder [Gebäude und blinkende Bilder](building-and-flashing-images.md). Weitere Informationen zum Angeben der optionale Features finden Sie unter [optionale Features zum Erstellen von Bildern](optional-features-for-building-images.md).

2.  Bearbeiten Sie die OEMinput.xml-Datei, um die Featuremanifestdatei *OEMCustomAppFM.xml* enthalten, die Sie im vorherigen Schritt erstellt haben. Die XML-DATEN werden wie folgt.

    ``` syntax
    ...
    <AdditionalFMs>
        ...
        <AdditionalFM>%WPDKCONTENTROOT%\FMFiles\OEMCustomAppFM.xml</AdditionalFM>
      </AdditionalFMs>
    ```

3.  Weiter unten in der &lt;Features&gt; -Abschnitt der Datei OEMInput.xml hinzufügen des neuen TESTS\_APP-Feature zur Liste der vorhandenen Features.

    ``` syntax
    <Features>
      <Microsoft>
       ...
      </Microsoft>
      <OEM>
        ...
        <Feature>TEST_APP</Feature>
      </OEM>
    </Features>
    ```

### <a name="generate-sign-and-flash-the-image"></a>Generieren und Signieren flash das Bild

Führen Sie die folgenden Schritte aus, zu generieren, Signieren und das Bild flash.

1.  Generieren Sie das Bild mit ImgGen und die OEMInput.xml-Datei, die Sie im vorherigen Schritt angepasst.

    ``` syntax
    C:\>ImgGen Flash.ffu OEMInput.xml "%WPDKCONTENTROOT%\10\MSPackages"
    ```

2.  Bevor Sie Bilder anmelden können, müssen Sie durch die Schritte in [der signierenden Umgebung eingerichtet](https://msdn.microsoft.com/library/windows/hardware/dn789236)zuerst die Test OEM-Zertifikate auf dem Computer installieren.

3.  Melden Sie sich mit der Option /pk generierten Katalog.

    ``` syntax
    C:\> Set SIGN_OEM=1
    C:\> Sign.cmd /pk TestSigned.cat
    ```

4.  Signieren Sie die FFU mit der signierte Katalogdatei ImageSigner verwenden.

    ``` syntax
    C:\> ImageSigner Sign Flash.FFU Flash.Cat
    ```

5.  Das Bild mit FFUTool auf das Telefon Flash.

    ``` syntax
    C:\> FFUTool –Flash Flash.ffu
    ```

Weitere Informationen zu generieren und blinkende finden Sie unter [Gebäude und blinkende Bilder](building-and-flashing-images.md).

### <a name="verify-that-the-testapplication-executes-as-expected"></a>Stellen Sie sicher, dass die TestApplication erwartungsgemäß ausgeführt wird

Stellen Sie sicher, dass die TestApplication erwartungsgemäß mithilfe des folgenden Verfahrens ausgeführt wird.

1.  Konfigurieren Sie eine Verbindung TShell, um das Bild zu testen.

2.  Herstellen einer Verbindung an das Gerät mit dem **Open-Gerät** TShell Befehl. Geben Sie die MAC-Adresse des Geräts.

    ``` syntax
    PS C:\> Open-device 001122334455
    ```

3.  Vergewissern Sie sich, dass die TestApplication auf dem Gerät ist, mithilfe des Befehls TShell **Dir-Gerät** . Die Kurzform des Befehls DirD ist, wird angezeigt.

    ``` syntax
    PS C:\> DirD \TestApplication.exe /s
    ```

4.  Führen Sie die Anwendung, indem Sie das Cmdlet **Exec-Gerät** im Fenster TShell eingeben. Das Cmdlet **Exec-Gerät** startet einen Prozess auf dem Gerät verbunden. In der Standardeinstellung wartet, mit dem Cmdlet **Exec-Gerät** Beenden vor der Rückgabe des Prozesses. Verwenden Sie die Option - Async sofort zurückgegeben. Verwenden Sie den – Displayoutput-Parameter, um die Ausgabe auf dem Bildschirm.

    ``` syntax
    PS C:\> ExecD -displayoutput -filename \Data\Test\TestApplication.exe
    ```

5.  Die Ausgabe sollte wie folgt angezeigt werden sollen.

    ``` syntax
    Output    : Testing console output
    Error     :
    Exit Code : 0
    ```

## <a name="related-topics"></a>Verwandte Themen


[Erstellen von Lösungspaketen](creating-mobile-packages.md)

[Erstellen und blinkende](building-and-flashing-images.md)

 

 

[Senden Sie Kommentare zu diesem Thema an Microsoft] (mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback%20%5Bp_phFlashing\p_phFlashing%5D:%20Create%20a%20feature%20and%20include%20it%20in%20an%20image%20%20RELEASE:%20%2810/4/2016%29&body=%0A%0APRIVACY%20STATEMENT%0A%0AWe%20use%20your%20feedback%20to%20improve%20the%20documentation.%20We%20don't%20use%20your%20email%20address%20for%20any%20other%20purpose,%20and%20we'll%20remove%20your%20email%20address%20from%20our%20system%20after%20the%20issue%20that%20you're%20reporting%20is%20fixed.%20While%20we're%20working%20to%20fix%20this%20issue,%20we%20might%20send%20you%20an%20email%20message%20to%20ask%20for%20more%20info.%20Later,%20we%20might%20also%20send%20you%20an%20email%20message%20to%20let%20you%20know%20that%20we've%20addressed%20your%20feedback.%0A%0AFor%20more%20info%20about%20Microsoft's%20privacy%20policy,%20see%20http://privacy.microsoft.com/default.aspx. "Senden Sie Kommentare zu diesem Thema an Microsoft")





