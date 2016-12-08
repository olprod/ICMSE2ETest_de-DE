---
author: kpacquer
Description: These tools are part of the Windows 10 IoT Core (IoT Core) ADK Add-Ons, in the \\Tools folder. To learn more about these tools, see What's in the Windows ADK IoT Core Add-ons.
ms.assetid: ae043bb0-656e-4439-bdbe-a8d370629ab7
MSHAttr: PreferredLib:/library
title: Command-Line Options IoT Core Add-ons
ms.openlocfilehash: 0e6d7edcf40c8a12207c42ec8cae03e836c52d25
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="span-idcommand-lineoptionstomanufactureiotcoreimagesspaniot-core-add-ons-command-line-options"></a><span id="command-line_options_to_manufacture_iot_core_images"></span>Command-Line Options IoT Core Add-ons

Diese Tools sind Teil der [Windows-10 IoT Core (IoT Core) ADK Add-Ons](http://go.microsoft.com/fwlink/?LinkId=735028)in der [ \\Ordner Tools](iot-core-adk-addons-command-line-options.md). Finden Sie weitere Informationen zu diesen Tools finden Sie unter [Was ist in die Windows ADK IoT Core Add-ons](iot-core-adk-addons.md).

## <a name="span-idappx2pkgcmdspanappx2pkgcmd"></a><span id="appx2pkg.cmd"></span>appx2pkg.cmd

Die Ordnerstruktur erstellt und die Vorlagendateien für ein neues Paket kopiert.

## <a name="span-idbuildagentcmdspanbuildagentcmd"></a><span id="BuildAgent.cmd"></span>BuildAgent.cmd

Erstellt FFUs für alle OEMInputSamples unter dem Verzeichnis Addon Kit. Kann zum Automatisieren der nächtliche Builds verwendet werden.

## <a name="span-idbuildimagecmdspanbuildimagecmd"></a><span id="BuildImage.cmd"></span>BuildImage.cmd

[Erstellt eine Bilddatei (FFU)](create-a-basic-image.md), mit den produktspezifischen-Paketen. CreateImage.cmd verwendet wird, enthält zusätzliche Optionen.

**Verwendung**:`buildimage [Product]/[All]/[Clean] [BuildType]`

**Parameter**:
- `ProductName`....... Name des Produkts, die erstellt werden erforderlich.
- `All`............... Alle Produkte \Products im Verzeichnis erstellt werden
- `Clean`............. Bereinigt das Ausgabeverzeichnis.  Eine der oben genannten sollte angegeben werden.
- `BuildType`......... Optional, Einzelhandel/Test, wenn beide Arten nicht angegeben werden erstellt.
- `[version]`......... Optional, Version des Pakets. Wenn nicht angegeben, verwendet er BSP_VERSION
- `[/?]`.............. Diese Zeichenfolge Usage angezeigt.

**Beispiel**:

``` syntax
buildimage SampleA Test
buildimage SampleA Retail
buildimage SampleA
buildimage All Test
buildimage All
buildimage Clean
```

## <a name="span-idbuildkitagentcmdspanbuildkitagentcmd"></a><span id="BuildKitAgent.cmd"></span>BuildKitAgent.cmd

Erstellt FFUs für alle OEMInputSamples im Paket Core-Kit. Kann zum Automatisieren der nächtliche Builds verwendet werden.

## <a name="span-idbuildkitsamplescmdspanbuildkitsamplescmd"></a><span id="BuildKitSamples.cmd"></span>BuildKitSamples.cmd

Erstellt architekturspezifische FFUs für OEMInputSamples in Core Kit-Paket.  Kann zum Automatisieren der nächtliche Builds verwendet werden.

## <a name="span-idbuildpkgcmdspanbuildpkgcmd"></a><span id="buildpkg.cmd"></span>buildpkg.cmd

Erstellt ein Paket aus \Sources-\<Bogen\>\Packages.

Buildpkg speichert das Paket in den \Build\\< Bogen\>\pkgs Ordner wie einer CAB-Datei (Beispiel: Contoso.Provisioning.Auto.cab).

Zur Problembehandlung, speichert Buildpkg Protokolle unter \Build\\< Bogen\>\pkgs\logs. 

**Verwendung**:`buildpkg [CompName.SubCompName]/[packagefile.pkg.xml]/[All]/[Clean] [version]`

**Parameter**:

-   `<CompName.SubCompName>`: Verwenden Sie diese auf das Paket mit dem Namen ComponentName.SubComponent verweisen.

-   `<packagefile.pkg.xml>`: Verwenden Sie diese, um Package, indem Sie die XML-Paketdefinitionsdatei zu verweisen.

-   `<All>`: Verwenden Sie diese zum Erstellen von allen Paketen in der \Sources-\<Bogen\>\Packages Ordner. Dies ist identisch mit der `BuildPkg All` Befehl.

-   `<Clean>`: Hiermit können alle Elemente in der \Build löschen\\< Bogen\>\pkgs Ordner. Vor dem Erstellen von allen Paketen für empfohlen.

-   `<version>`: Optional, mit denen eine Versionsnummer angeben. Wenn Sie eine nicht angeben, wird standardmäßig, die in die Variable % BSP definierten Version verwenden\_VERSION %. 

**Beispiel**:

``` syntax
buildpkg Appx.Main
buildpkg Appx.Main 10.0.1.0
buildpkg sample.pkg.xml
buildpkg sample.pkg.xml 10.0.1.0
buildpkg All
buildpkg All 10.0.2.0
buildpkg Clean
```

## <a name="span-idcreateimagecmdspancreateimagecmd"></a><span id="createimage.cmd"></span>createImage.cmd

Die Bilddatei (FFU), mit den produktspezifischen-Paketen erstellt. Verwendet die createpkg.cmd mit der Imggen-Tool und die **Parameter** in der befehlsumgebung festgelegt. Die Ausgabedateien stehen in der Build (% BUILD\_DIR %) Ordner.

CreateImage speichert die FFU % BUILD\_DIR %\\<productname>\(Test- oder Verkaufsversion) \

**Verwendung**:`createimage <productname> <buildtype>`

**Parameter**:

-   `<productname>`: Der Name des zu erstellenden Produkts.

-   `<buildtype>`: **Einzelhandel** oder **Test**

**Beispiel**:

``` syntax
createimage.cmd ProductA Retail
```


## <a name="span-idcreatepkgcmdspancreatepkgcmd"></a><span id="createpkg.cmd"></span>createpkg.cmd

Erstellt eine Definitionsdatei packen (. pkg.xml) mit dem Tool Pkggen und **Parameter** in der Umgebung von **IoTCoreShell.cmd** und **setversion.cmd**definierten festgelegt. 

Createpkg speichert das Paket in die \Build\\< Bogen\>\pkgs Ordner als CAB-Datei (Beispiel: Contoso.Provisioning.Auto.cab).

**Verwendung**:`createpkg <packagefile.pkg.xml>/<CompName.SubCompName> [version]`

**Parameter**:

-   `<packagefile.pkg.xml>`: Verwenden Sie diese Package, indem Sie die XML-Paketdefinitionsdatei zu identifizieren.

-   `<CompName.SubCompName>`: Verwenden Sie diese um das Paket mit dem Namen ComponentName.SubComponent zu identifizieren.   

-   `<version>`: Optional, mit denen eine Versionsnummer anzugeben. Wenn Sie eine nicht angeben, wird standardmäßig, die in die Variable % BSP definierten Version verwenden\_VERSION %. 


**Beispiele**:

``` syntax
createpkg %SRC_DIR%\Packages\Appx.Main\Appx.Main.pkg.xml
createpkg %SRC_DIR%\Packages\Appx.Main\Appx.Main.pkg.xml 10.0.1.0
createpkg Registry.FilesAndRegKeys 
```

## <a name="span-idcreateprovpkgcmdspancreateprovpkgcmd"></a><span id="createprovpkg.cmd"></span>createprovpkg.cmd

Erstellt ein provisioning Paket mit dem Tool icd.exe und in der Umgebung von **IoTCoreShell.cmd** und **setversion.cmd**definierten festgelegten **Parameter** an. Die Ausgabedatei (.ppkg) wird am angegebenen Ausgabespeicherort erstellt.

**Verwendung**:`createprovpkg <customizations.xml> <outputfilename>`

**Parameter**:

-   `<customizations.xml>`: Eingabedatei mit Windows Anpassungen Inhalt
-   `<outputfilename>`: Name (.ppkg) mit dem vollständigen Pfad der Ausgabedatei

**Beispiel**:

``` syntax
createprovpkg %PRJ_DIR%\Products\SampleA\Prov\customizations.xml %PRJ_DIR%\Products\SampleA\Prov\SampleAProv.ppkg
```

## <a name="span-idcreateupdatepkgscmdspancreateupdatepkgscmd"></a><span id="createupdatepkgs.cmd"></span>createupdatepkgs.cmd

Erstellt ein Update-Paket mit der Verpackung-Definitionsdateien (. pkg.xml) im Ordner "Updates". Das Tool Pkggen verwendet, und legen Sie **Parameter** in der Umgebung durch **IoTCoreShell.cmd** und **setversion.cmd**definiert.

Die Ausgabedateien werden im Buildverzeichnis gespeichert (% BUILD\_DIR %), in der \<Updatename\> Ordner.

**Verwendung**:`createupdatepkgs <updatename>`

**Parameter**:

-  `<updatename>`: Der Name des Updates.

**Beispiel**:

``` syntax
createupdatepkgs Update1
```

In diesem Beispiel wird die Ausgabe an % BUILD gespeichert\_DIR %\\Update1\\.

## <a name="span-idinf2cabcmdspaninf2cabcmd"></a><span id="inf2cab.cmd"></span>inf2cab.cmd

Konvertiert eine INF-Paket in einer CAB-Datei an.

Inf2cab speichert das Paket in den \Build\\< Bogen\>\pkgs Ordner (Beispiel: Drivers.GPIO.cab).

**Verwendung**:`inf2cab filename.inf [CompName.SubCompName]`

**Parameter**:

- `filename.inf` ........... Erforderlich, input-Datei für den Treiber.

- `<CompName.SubCompName>`.. Optional, bezieht sich auf Treiberpakets anhand des Namens ComponentName.SubComponent.

**Beispiele**:

``` syntax
inf2cab C:\test\gpiodriver.inf
inf2cab C:\test\gpiodriver.inf Drivers.GPIO
```

## <a name="span-idinf2pkgcmdspaninf2pkgcmd"></a><span id="inf2pkg.cmd"></span>inf2pkg.cmd

Die Ordnerstruktur erstellt und kopiert die Vorlagendateien für ein neues Paket

**Verwendung**:`inf2pkg input.inf [CompName.SubCompName]`
- `input.inf`............... Erforderlich, input INF-Datei
- `CompName.SubCompName`.... Optional, Standard ist Drivers.input
- `[/?]`.................... Diese Zeichenfolge: Einsatz angezeigt.

**Beispiel**:
``` syntax
inf2pkg C:\test\testdriver.inf
```

## <a name="span-idiotcoreshellcmdspanspan-idiotcoreshellcmdspaniotcoreshellcmd"></a><span id="iotcoreshell.cmd"></span><span id="IOTCORESHELL.CMD"></span>IoTCoreShell.cmd

Öffnet die IoT Core-Verwaltungsshell als Administrator. (Diese Datei ist im Stammordner und LaunchTool.cmd verwendet)

Nachdem Sie IoTCoreShell öffnen, werden Sie aufgefordert, eine Standard-Architektur auszuwählen (ARM oder X86) für die Geräte, die Sie erstellen werden können. Hierdurch wird das standardmäßige Starten der Systemvariablen festgelegt.  

## <a name="span-idlaunchtoolcmdspanlaunchtoolcmd"></a><span id="LaunchTool.cmd"></span>LaunchTool.cmd

Wird von LaunchTool.cmd (im Stammordner) zum Öffnen der IoT Core-Shell. 

## <a name="span-idnewappxpkgcmdspannewappxpkgcmd"></a><span id="newappxpkg.cmd"></span>newappxpkg.cmd

Erstellt einen neuen Arbeitsordner zum einfacheren Appx Pakete in CAB-Dateien zu konvertieren. 

Hinweis: Dieses Tool erwartet, dass ein Unterordner "Abhängigkeiten" mit der .appx Abhängigkeit Pakete mit dem Namen.

Dieser Befehl den Arbeitsordner erstellt, in der \Source-\<Bogen\>\Packages\ Ordner.

Wenn Sie diesen Befehl ohne alle Variablen auszuführen, auch sehen Sie die anderen Arbeitsordner in der \Source-\<Bogen\>\Packages\ Ordner.

**Verwendung**:`newappxpkg filename.appx [CompName.SubCompName]`

**Parameter**:

-   `filename.appx`: Erforderlich der Eingabedatei für das Paket Appx.

-   `<CompName.SubCompName>`: Optional, den mit dem Namen Arbeitsordner erstellt: ComponentName.SubComponent.

**Beispiel**:

``` syntax
newappxpkg C:\test\MainAppx_1.0.0.0_arm.appx AppX.Main
```

Weitere Informationen finden Sie unter [Übung 1 b: Hinzufügen einer app zu Ihr Bild](deploy-your-app-with-a-standard-board.md).

## <a name="span-idnewbspcmdspannewbspcmd"></a><span id="newbsp.cmd"></span>newbsp.cmd
Erstellt die Ordnerstruktur und kopiert die Vorlagendateien für das [Erstellen einer neuen Pinnwand Paket (BSP) unterstützen](create-a-new-bsp.md).

**Verwendung**:`newbsp BSPName`

**Parameter**:

- `BSPName`........... Erforderlich, Name des BSP verwendet werden

**Beispiel**:
``` syntax
newbsp CustomRPi2
```


## <a name="span-idnewcommonpkgcmdspannewcommonpkgcmd"></a><span id="newcommonpkg.cmd"></span>newcommonpkg.cmd

Erstellt einen neuen Arbeitsordner, die Sie [Hinzufügen von Dateien, Ordner, Registrierungsschlüssel, und Bereitstellung Pakete](add-a-registry-setting-to-an-image.md) als CAB-Dateien unterstützen. Können Sie nach Verwendung dieser Befehl den Befehl Buildpkg Ihre letzte CAB-Datei erstellen.

Dieser Befehl erstellt den Arbeitsordner im Ordner \Common\Packages\.

Wenn Sie diesen Befehl ohne alle Variablen ausführen, sehen Sie auch die anderen Arbeitsordner im Ordner "\Common\Packages\".

**Verwendung**:`newcommonpkg CompName.SubCompName`

**Parameter**:

-   `<CompName.SubCompName>`: Erforderlich, den mit dem Namen ComponentName.SubComponent Arbeitsordner erstellt.

**Beispiel**:

``` syntax
newcommonpkg Registry.FilesAndRegKeys
```

Weitere Informationen finden Sie unter [Übung 1c: Hinzufügen einer Datei und eine Einstellung in der Registrierung zu einem Bild](add-a-registry-setting-to-an-image.md).



## <a name="span-idnewdrvpkgcmdspannewdrvpkgcmd"></a><span id="newdrvpkg.cmd"></span>newdrvpkg.cmd

Zum [Hinzufügen eines Treibers zu einem Bild](add-a-driver-to-an-image.md)verwendet. Erstellt einen neuen Ordner, mit denen Sie die Treiberpakete in CAB-Dateien zu konvertieren. Können Sie nach Verwendung dieser Befehl den Befehl Buildpkg letzten CAB-Datei zu erstellen.

Dieser Befehl erstellt den Arbeitsordner in der \Source-\<Bogen\>\Packages\ Ordner.

Wenn Sie diesen Befehl ohne alle Variablen auszuführen, auch sehen Sie die anderen Arbeitsordner in der \Source-\<Bogen\>\Packages\ Ordner.

**Verwendung**:`newdrvpkg filename.inf [CompName.SubCompName]`

**Parameter**:

-   `filename.inf`: Erforderlich Eingabe INF-Datei für das Treiberpaket.

-   `<CompName.SubCompName>`: Optional, den mit dem Namen Arbeitsordner erstellt: ComponentName.SubComponent. Der Standardwert ist Treiber. \<Filename\>.

**Beispiel**:

``` syntax
newdrvpkg C:\test\GPIO.inf Drivers.GPIO
```

## <a name="span-idnewproductcmdspan-newproductcmd"></a><span id="newproduct.cmd"></span>NewProduct.cmd

Dient zum [Erstellen von neuen Produktbilder](create-a-basic-image.md). Erstellt ein neues Produkt-Arbeitsverzeichnis unter \Products und kopiert den Inhalt aus der Vorlagendatei.

**Verwendung**:`newproduct <productname>`

**Parameter**:

-   `<productname>`: Der Name des Produkts erstellt werden soll

**Beispiel**:

``` syntax
newproduct ProductA
```

## <a name="span-idnewupdatecmdspannewupdatecmd"></a><span id="NEWUPDATE.CMD"></span>newupdate.cmd

Erstellt eine neue Arbeitsverzeichnis unter \Updates und kopiert den Inhalt aus der Vorlagendatei.

**Verwendung**:`newupdate <UpdateName>  <Version>`

**Parameter**:

-   `<UpdateName>`: Der Name des zu erstellenden Updates

-   `<Version>`: Versionsnummer (x.y.z.a)

**Beispiel**:

``` syntax
newupdate Update2 10.0.2.0
```

## <a name="span-idretailsigncmdspanretailsigncmd"></a><span id="retailsign.cmd"></span>retailsign.cmd

Schaltet zwischen der Verwendung von Cross-Zertifizierungen für das Signieren und Aktivieren der OEM Test Signieren von Zertifikaten

**Verwendung**:`retailsign [On/Off]`

**Parameter**:
- `On` ................... Ermöglicht schneidet Zertifikat zum Signieren
- `Off`................... Deaktiviert die Rechtwinklige Zertifikat zum Signieren und ermöglicht OEM Test anmelden

**Beispiele**:

```syntax
retailsign On
retailsign Off
```


## <a name="span-idsetenvcmdspansetenvcmd"></a><span id="setenv.cmd"></span>SetEnv.cmd
Setzt die Umgebungsvariablen, einschließlich **IOTADK\_ROOT**, **ALLGEMEINE\_DIR**, **SRC\_DIR**, **BUILD\_DIR**, **PKGBLD\_DIR**, **TOOLS\_DIR**, und vieles mehr. 

Legen Sie Open setenv.cmd in einem Text-Editor, um die vollständige Liste der Variablen anzuzeigen.

**Verwendung**:`setenv <arch>`

**Parameter**:

-   `<arch>`: Architektur festgelegt werden soll. (`arm`, `x86`, or `x64`).

**Beispiel**:

``` syntax
setenv.cmd arm
```

## <a name="span-idsetoemcmdspansetoemcmd"></a><span id="setOEM.cmd"></span>setOEM.cmd
Legt den Namen Ihres Unternehmens OEM fest. Bearbeiten Sie diese Datei mit einem Text-Editor.

``` syntax
set OEM_NAME=Contoso
```


## <a name="span-idsetsignaturecmdspansetsignaturecmd"></a><span id="setsignature.cmd"></span>SetSignature.cmd
Legt die [Kernelmodus - Code Signing Kreuzzertifikate](https://msdn.microsoft.com/windows/hardware/drivers/install/cross-certificates-for-kernel-mode-code-signing)

## <a name="span-idsetversioncmdspansetversioncmd"></a><span id="setversion.cmd"></span>setVersion.cmd

Legt die [Versionsnummern](../../service/mobile/update-requirements.md) beim Erstellen eines Pakets mit **createpkg.cmd** oder provisioning-Paket mit **createprovpkg.cmd**verwendet.

In dieser Versionsinformationen gespeichert ist **% PRJ\_DIR %\\versioninfo.txt** und geladen zurück, wenn der IoT Core Shell erneut gestartet wird. Sobald der Inhalt des Pakets geändert werden, muss die Version aktualisiert werden, und alle Pakete müssen neu erstellt werden.

**Verwendung**:`setversion x.y.z.a`

**Parameter**:

-   `x.y.z.a`: Vierteilige Versionsnummer für Pakete verwendet werden soll

**Beispiel**:

``` syntax
setversion 10.0.0.1
```


<!--- ## <span id="UPDATEIMAGE.CMD"></span> updateimage.cmd


**Usage**: `updateimage <productname> <buildtype> <updatename>`

**Parameters**:

-   `<productname>`: Name of the product to be updated.
-   `<buildtype>`: **Retail** or **Test**
-   `<updatename>`: Name of the update to be applied

Description: This tool copies the specified product build and updates with the contents specified by &lt;updatename&gt; using ImageApp tool with the correct parameters set in the environment. The output files are available in the Build (%BLD\_DIR%) folder.

**Example**:

``` syntax
updateimage ProductA Retail Update1
```

Output is available at %BLD\_DIR%\\ProductA\\Update1\\Retail

-->

## <a name="span-idoldertoolsspanolder-tools"></a><span id="older_tools"></span>Ältere tools

### <a name="span-idbuildallpackagescmdspanbuildallpackagescmd"></a><span id="buildallpackages.cmd"></span>buildallpackages.cmd

Dieses Tool wurde mit dem Tool ersetzt: Buildpkg alle.

### <a name="span-idnewpkgcmdspan-newpkgcmd"></a><span id="newpkg.cmd"></span>newpkg.cmd

Dieses Tool wurde mit den Tools ersetzt: Newappxpkg, Newdrvpkg, und Newcommonpkg.

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen

[IoT Core Add-ons](iot-core-adk-addons.md)

[Leitfäden zum IoT Core manufacturing](iot-core-manufacturing-guide.md)
