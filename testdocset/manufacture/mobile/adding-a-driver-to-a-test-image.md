---
title: "Hinzufügen eines Treibers dem Test-Bild"
description: "In diesem Thema zeigt, wie ein Feature erstellen und Hinzufügen zu einem Testbild."
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 9ac41806-b3c5-4cbf-8c41-cb838d7d0d52
ms.openlocfilehash: 7ef4d22ac4f404bd0636ccfb46fa8f9ea496ec08
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="adding-a-driver-to-a-test-image"></a>Hinzufügen eines Treibers dem Test-Bild


In diesem Thema zeigt, wie ein Feature erstellen und Hinzufügen zu einem Testbild.

## <a name="a-href-idprocess-overview---adding-a-driver-feature-to-a-test-imageaprocess-overview-adding-a-driver-feature-to-a-test-image"></a><a href="" id="process-overview---adding-a-driver-feature-to-a-test-image"></a>Übersicht über den Upgradeprozess – Hinzufügen eines Treiber-Features zu einem Testbild


Zum Erstellen eines Features, das einen Treiber enthält, und dem Test-Bild hinzuzufügen, führen Sie die folgenden Schritte aus.

1.  [Erstellt einen Test KMDF-Treiber](#create-test)

2.  [Generieren des Treiberpakets](#generate-the-driver)

3.  [Erstellen einer Featuremanifestdatei, die das Paket verweist](#create-a-feature)

4.  [Fügen Sie das Feature zur Datei OEMInput.xml](#add-a-feature)

5.  [Generieren und Signieren flash das Bild auf das Gerät](#generate-sign)

6.  [Stellen Sie sicher, dass die KMDFDriver1 auf dem Gerät ist](#verify)

7.  [Vergewissern Sie sich, dass der Treiber lädt mithilfe von Windows: Debuggen](#windbg)

Im folgenden Diagramm wird der Verpackung und Image Generation-Elemente, die zum Hinzufügen des Treibers an das Gerät verwendet werden.

![OEM\-Feature\-Erstellung\-Verpackung\-Szenario](images/oem-feature-creation-packaging-scenario.png)

## <a name="a-href-idwalkthrough---adding-a-driver-to-a-test-imageawalkthrough-adding-a-driver-to-a-test-image"></a><a href="" id="walkthrough---adding-a-driver-to-a-test-image"></a>Exemplarische Vorgehensweise – Hinzufügen eines Treibers zu einem Test-Abbild


In diesem Thema werden die Schritte, die Sie zum Hinzufügen eines Treibers zu einem Test-Abbild ausführen müssen. Bevor Sie mit dieser exemplarischen Vorgehensweise beginnen können, müssen Sie zuerst einen einfachen KMDF Treiber erstellen.

In dieser exemplarischen Vorgehensweise wird davon ausgegangen, dass Sie das Projekt *KmdfDriver1*benannt.

### <a name="a-href-idcreate-testacreate-a-test-kmdf-driver"></a><a href="" id="create-test"></a>Erstellt einen Test KMDF-Treiber

Um einen Test KMDF Treiber erstellen möchten, führen Sie die folgenden Schritte aus.

1.  Klicken Sie im **Projektmappen-Explorer** erweitern Sie **KmdfDriver1** , und erweitern Sie dann den **Ordner mit den Quelldateien**.

2.  Bearbeiten der Datei "Driver.c" durch klicken.

3.  Fügen Sie der **IoReportRootDevice** -Routine direkt nach der Deklaration der Variablen Abschnitt wie unten. Die **IoReportRootDevice** -Routine meldet ein Gerät, die nicht durch einen Plug & Play-Bustreiber an den Plug & Play-Manager erkannt werden. Dadurch wird den Software nur Treiber geladen bleiben.

    ``` syntax
    ...
    {
        WDF_DRIVER_CONFIG config;
        NTSTATUS status;
        WDF_OBJECT_ATTRIBUTES attributes;

       //
       // IoReportRootDevice routine reports a device that cannot be detected by 
       // a PnP bus driver to the PnP Manager. This allows our software-only
       // driver to remain loaded.  
      IoReportRootDevice(DriverObject);

        //
        // Initialize WPP tracing.
        //
        WPP_INIT_TRACING( DriverObject, RegistryPath );
        TraceEvents(TRACE_LEVEL_INFORMATION, TRACE_DRIVER, "%!FUNC! Entry");

    ... 
    ```

4.  Driver.c zu speichern.

5.  Zum Erstellen des Treibers und ein Paket zu erstellen, wählen Sie im Menü **Erstellen** auf **Projektmappe erstellen** . Visual Studio zeigt den Build Fortschritt im Fenster **Ausgabe** . (Wenn *das Ausgabefenster* nicht angezeigt wird, wählen Sie aus dem Menü **Ansicht** **Ausgabe** .)

6.  Navigieren Sie zum Anzeigen von integrierten Treiberpakets in Windows Explorer auf den Ordner **KmdfDriver1** , und dann auf **ARM\\Win8.1Debug\\**. Dieses Verzeichnis enthält die folgenden Dateien:

    -   KmdfDriver1.sys - eine Kernelmodus-Treiber-Datei.

    -   KmdfDriver1.inf - eine Informationsdatei, die Windows verwendet, um die Treiber zu installieren.

    -   KmdfDriver1.pdb – eine Datei, die Debugsymbole enthält, die für das debugging verwendet werden.

    -   KmdfDriver1.cat - eine Katalogdatei, die nicht in dieser exemplarischen Vorgehensweise verwendet wird.

    Es gibt auch Co-Installer-Dateien für die Windows Treiber Frameworks (WDF), die nicht mit Windows Phone verwendet werden.

7.  Aufgrund der Unterschiede in Windows 10 Mobile INF-Dateien verwenden wir nicht die desktop INF-Datei, die von Visual Studio generiert wird.

    ``` syntax
    ;
    ; KmdfDriver1.inf
    ;
    [Version]
    Signature="$WINDOWS NT$"
    Class=System
    ClassGuid={4d36e97d-e325-11ce-bfc1-08002be10318}
    Provider=%MSFT%
    DriverVer=11/01/2012,1.00.00.00
    BootCritical=1

    [DestinationDirs]
    DefaultDestDir = 12

    [Manufacturer]
    %StdMfg%=KMDFDriver1_DevDesc, NTARM, NTx86

    ;*******************************
    ;** models section (required) **
    ;*******************************
    ; For ARM platforms
    [KMDFDriver1_DevDesc.NTARM]
    ; DisplayName      Section          DeviceId
    ; -----------      -------          --------
    %KMDFDriver1_DevDesc%=KMDFDriver1, Root\KMDFDriver1

    ; For Win2K+
    [KMDFDriver1_DevDesc.NTx86]
    ; DisplayName       Section          DeviceId
    ; -----------       -------          --------
    %KMDFDriver1_DevDesc%=KMDFDriver1, Root\KMDFDriver1

    ;********************************
    ;* ddinstall section (required) *
    ;********************************
    [KMDFDriver1.NT]
    CopyFiles=KMDFDriver1.NT.Copy

    [KMDFDriver1.NT.Copy]
    KMDFDriver1.sys

    ;-------------- Service installation

    [KMDFDriver1.NT.Services]
    AddService = KMDFDriver1, %SPSVCINST_ASSOCSERVICE%, KMDFDriver1_Service_Inst

    [KMDFDriver1_Service_Inst]
    DisplayName    = %KMDFDriver1_DevDesc%
    ServiceType    = %SERVICE_KERNEL_DRIVER%
    StartType      = %SERVICE_SYSTEM_START%
    ErrorControl   = %SERVICE_ERROR_NORMAL%
    ServiceBinary  = %12%\KMDFDriver1.sys


    [Strings]
    SPSVCINST_ASSOCSERVICE= 0x00000002
    MSFT = "Microsoft"
    KMDFDriver1_DevDesc = "KMDF Driver 1"
    SERVICE_KERNEL_DRIVER = 1
    SERVICE_AUTO_START = 2
    SERVICE_SYSTEM_START = 1
    SERVICE_BOOT_START = 0
    SERVICE_ERROR_NORMAL = 1
    ```

8.  Signieren des Treibers über die folgenden Befehle:

    ``` syntax
    C:>set SIGN_OEM=1 
    sign KMDFDriver1.sys 
    ```

### <a name="a-href-idgenerate-the-driveragenerate-a-package-that-contains-the-driver"></a><a href="" id="generate-the-driver"></a>Generieren Sie ein Paket mit dem Treiber

Generieren Sie ein Paket, das diesem Treiber enthält, indem Sie die folgenden Schritte aus.

1.  Erstellen Sie ein Verzeichnis namens *KMDFDriver1* , und kopieren Sie die KMDFDriver1.sys und KMDFDriver1.inf-Dateien, die Sie in das Verzeichnis in Visual Studio erstellt haben.

2.  Erstellen Sie eine Textdatei mit dem Namen *KmdfDriver1. pkg.xml* , enthält die folgende XML-Paketdefinition.

    ``` syntax
    <?xml version="1.0" encoding="utf-8"?>
    <Package xmlns="urn:Microsoft.WindowsPhone/PackageSchema.v8.00"
      Owner="Contoso"
      OwnerType="OEM"     
      ReleaseType="Test"          
      Platform="DCD6000"          
      Component="Phone.Test.BaseOS"
      SubComponent="KmdfDriver1"
      Partition="MainOS"
      BinaryPartition="false">
      <Components>
        <OSComponent>
            <Files>
                <File Source="KmdfDriver1.sys" DestinationDir="$(runtime.system32)\drivers"/>
            </Files>
        </OSComponent>
        <Driver InfSource="KmdfDriver1.inf">
            <Reference Source="KmdfDriver1.sys"/>
        </Driver>
      </Components>
    </Package>
    ```

    Sie können die Attribute Besitzer und Plattform entsprechend den Namen der Name Ihrer Organisation und den Namen des Geräts aktualisieren. Diese Änderungen Attribut werden der Name der generierten Paket ändern.

    Angeben der *Windows\\System32\\Treiber* Verzeichnis auf dem Gerät mit dem Makro $(runtime.system32).

3.  Im nächste Schritt wird das Paket öffnen Sie ein Eingabeaufforderungsfenster Administrator generiert.

4.  Zeigen Sie die Umgebungsvariablen, indem Sie in das Administrator-Eingabeaufforderungsfenster eingeben **FESTGELEGT** . Suchen Sie nach *WPDKCONTENTROOT* zu bestätigen, dass die Build-Umgebung ordnungsgemäß konfiguriert ist. Sollte angezeigt werden, dass WPDKCONTENTROOT festgelegt ist. Auf einem Windows 64-Bit-PC sollte der Pfad etwa wie folgt aussehen.

    ``` syntax
    ...
    WPDKCONTENTROOT=C:\Program Files (x86)\Windows Kits\10
    ```

5.  Generieren Sie das Paket mit PkgGen. Bereitstellen Sie die Versionsnummer der 1.0.0.0. Der Parameter/config verweist auf den Speicherort der pkggen.cfg.xml Datei mit der Windows-DriverKit bereitgestellt. Der /hive-Parameter verweist auf den Speicherort der Stamm-Hive.

    ``` syntax
    C:\KmdfDriver1>PkgGen KmdfDriver1.pkg.xml /version:1.0.0.0 /variables:"HIVE_ROOT=%WPDKCONTENTROOT%\CoreSystem" /config:"%WPDKCONTENTROOT%\Tools\bin\i386\pkggen.cfg.xml"
    ```

6.  Wenn PkgGen das Paket erfolgreich erstellt, wird viele Zeilen mit Informationen angezeigt, die die Registrierung erstellten Einträge auf die bereitgestellte INF-Datei basieren. Der letzte Teil der Ausgabe werden ähnlich der folgenden.

    ``` syntax
    ... 
    info: Import Log: :      sto: Unloaded hive key '{bf1a281b-ad7b-4476-ac95-f47682
    990ce7}C:/Users/User1/AppData/Local/Temp/gs5gvfgc.pou/windows/system32/config/S
    OFTWARE'. Time = 0 ms
    info: Import Log: : <<<  Section end 2015/08/06 13:10:22.413
    info: Import Log: : <<<  [Exit status: SUCCESS]
    info: Import Log: :
    info: Import Log: :
    info: Import Log: : >>>  [Unload Offline Registry Hive - DRIVERS]
    info: Import Log: : >>>  Section start 2014/08/06 13:10:22.413
    info: Import Log: :        os: Version = 6.3.9600, Service Pack = 0.0, Suite = 0
    x0100, ProductType = 1, Architecture = x86
    info: Import Log: :       cmd: PkgGen  KmdfDriver1.pkg.xml /version:1.0.0.0 /var
    iables:"HIVE_ROOT=C:\Program Files (x86)\Windows Kits\10\CoreSystem" /con
    fig:"C:\Program Files (x86)\Windows Kits\10\Tools\bin\i386\pkggen.cfg.xml
    "
    info: Import Log: :      sto: Closed hive key '{bf1a281b-ad7b-4476-ac95-f4768299
    0ce7}C:/Users/User1/AppData/Local/Temp/gs5gvfgc.pou/windows/system32/config/DRI
    VERS'.
    info: Import Log: :      sto: Unloaded hive key '{bf1a281b-ad7b-4476-ac95-f47682
    990ce7}C:/Users/User1/AppData/Local/Temp/gs5gvfgc.pou/windows/system32/config/D
    RIVERS'. Time = 0 ms
    info: Import Log: : <<<  Section end 2014/08/06 13:10:22.513
    info: Import Log: : <<<  [Exit status: SUCCESS]
    info: Import Log: :
    info: Building package '.\Contoso.Phone.Test.BaseOS.KmdfDriver1.spkg'
    info: Adding file 'KmdfDriver1.sys' to package '.\Contoso.Phone.Test.BaseOS.Kmdf
    Driver1.spkg' as '\windows\System32\drivers\KmdfDriver1.sys'
    info: Adding file 'C:\Users\User1\AppData\Local\Temp\5bgjkx3p.j01\reg.reg' to p
    ackage '.\Contoso.Phone.Test.BaseOS.KmdfDriver1.spkg' as '\Windows\Packages\Regi
    stryFiles\Contoso.Phone.Test.BaseOS.KmdfDriver1.reg'
    info: Adding file 'C:\Users\User1\AppData\Local\Temp\5bgjkx3p.j01\regMultiSz.rg
    a' to package '.\Contoso.Phone.Test.BaseOS.KmdfDriver1.spkg' as '\Windows\Packag
    es\RegistryFiles\Contoso.Phone.Test.BaseOS.KmdfDriver1.rga'
    info: Done package ".\Contoso.Phone.Test.BaseOS.KmdfDriver1.spkg"
    info: Packages are generated to . successfully
    ```

Weitere Informationen zum Arbeiten mit Paketen finden Sie unter [Creating Pakete](creating-mobile-packages.md).

### <a name="a-href-idcreate-a-featureacreate-a-feature-manifest-file-that-references-the-package"></a><a href="" id="create-a-feature"></a>Erstellen einer Featuremanifestdatei, die das Paket verweist

Erstellen einer Featuremanifestdatei, die ein Feature DRIVER1 OEM definieren die folgenden Schritte aus.

1.  Erstellen einer Featuremanifestdatei, mit dem Namen *OEMCustomAppFM.xml* im folgenden Verzeichnis.

    ``` syntax
    %WPDKCONTENTROOT%\FMFiles
    ```

2.  Definieren Sie das Feature DRIVER1, indem das folgende XML in die Datei *OEMCustomDriverFM.xml* hinzufügen. Aktualisieren Sie den Paketnamen entsprechend der Name der Datei im vorherigen Schritt generiert.

    ``` syntax
    <?xml version="1.0" encoding="utf-8"?>  
    <FeatureManifest xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns="http://schemas.microsoft.com/embedded/2004/10/ImageUpdate">  
    <!--  DRIVER1 FM File 7/31/2014   -->
      <Features>  
        <OEM>  
          <PackageFile Path="C:\KmdfDriver1\" Name="Contoso.Phone.Test.BaseOS.KmdfDriver1">  
            <FeatureIDs>  
              <FeatureID>DRIVER1</FeatureID>  
            </FeatureIDs>  
          </PackageFile>  
        </OEM>  
      </Features>  
    </FeatureManifest>
    ```

Weitere Informationen zu Features Manifesten finden Sie unter [Feature Dateiinhalten manifest](feature-manifest-file-contents.md).

### <a name="a-href-idadd-a-featureaadd-the-feature-to-the-oeminputxml-file"></a><a href="" id="add-a-feature"></a>Fügen Sie das Feature zur Datei OEMInput.xml

Fügen Sie der Datei OEMInput.xml die DRIVER1-Feature mithilfe des folgenden Verfahrens hinzu.

1.  In dieser exemplarischen Vorgehensweise wird davon ausgegangen, dass Sie eine vorhandene, Funktionstests OEMInput-Datei, die TShell aktiviert haben. Weitere Informationen zum Erstellen von Test-Bilder finden Sie unter [Gebäude und blinkende Bilder](building-and-flashing-images.md). Weitere Informationen zum Angeben der optionale Features finden Sie unter [optionale Features zum Erstellen von Bildern](optional-features-for-building-images.md).

    Vergewissern Sie sich, für den Sie ein Testbild verwenden, das Debuggen aktiviert werden soll. Weitere Informationen finden Sie unter [optionale Features zum Erstellen von Bildern](optional-features-for-building-images.md).

2.  Bearbeiten Sie die OEMinput.xml-Datei, um die Featuremanifestdatei *OEMCustomAppFM.xml* enthalten, die Sie im vorherigen Schritt erstellt haben. Die XML-DATEN werden wie folgt.

    ``` syntax
    ...
    <AdditionalFMs>
        ...
        <AdditionalFM>%WPDKCONTENTROOT%\FMFiles\OEMCustomDriverFM.xml</AdditionalFM>
      </AdditionalFMs>
    ```

3.  In der &lt;Features&gt; Abschnitt der Datei OEMInput.xml hinzufügen das neue Feature für DRIVER1 zur Liste der vorhandenen Features.

    ``` syntax
    <Features>
      <Microsoft>
       ...
      </Microsoft>
      <OEM>
        ...
        <Feature>DRIVER1</Feature>
      </OEM>
    </Features>
    ```

### <a name="a-href-idgenerate-signagenerate-sign-and-flash-the-image-to-the-device"></a><a href="" id="generate-sign"></a>Generieren und Signieren flash das Bild auf das Gerät

Führen Sie die folgenden Schritte aus, um das Generieren und melden Sie sich das Bild flash ein.

1.  Generieren Sie das Bild mit ImgGen und die OEMInput.xml-Datei, die Sie im vorherigen Schritt angepasst.

    ``` syntax
    C:\>ImgGen Flash.ffu OEMInput.xml "%WPDKCONTENTROOT%\10\MSPackages"
    ```

2.  Bevor Sie Bilder signieren können, müssen Sie nach der Anleitung in [der signierenden Umgebung eingerichtet](https://msdn.microsoft.com/library/windows/hardware/dn789236)zuerst die Test OEM-Zertifikate auf dem Computer installieren.

3.  Melden Sie sich den generierten Katalog mit der Sign.cmd und der **/pk** -Option.

    ``` syntax
    C:\> Set SIGN_OEM=1
    C:\> Sign.cmd /pk TestSigned.cat
    ```

4.  Signieren der FFU mit der signierte Katalogdatei ImageSigner verwenden.

    ``` syntax
    C:\> ImageSigner Sign Flash.FFU Flash.Cat
    ```

5.  Flash das Bild mit FFUTool auf das Telefon an.

    ``` syntax
    C:\> FFUTool –Flash Flash.ffu
    ```

Weitere Informationen zu generieren und blinkende finden Sie unter [Gebäude und blinkende Bilder](building-and-flashing-images.md).

### <a name="a-href-idverifyaverify-that-the-kmdfdriver1-is-on-the-device"></a><a href="" id="verify"></a>Stellen Sie sicher, dass die KMDFDriver1 auf dem Gerät ist

Stellen Sie sicher, dass die KMDFDriver1 mithilfe von TShell auf dem Gerät vorhanden ist.

1.  Konfigurieren einer Verbindung TShell, um das Bild zu testen.

2.  Herstellen einer Verbindung an das Gerät mit dem **Open--Gerät** TShell Befehl. Geben Sie die MAC-Adresse des Geräts.

    ``` syntax
    PS C:\> Open-device 001122334455
    ```

3.  Vergewissern Sie sich, dass die KMDFDriver1 auf dem Gerät ist, mit dem Befehl **Dir-Gerät** TShell. Die Kurzform des Befehls DirD, wird angezeigt.

    ``` syntax
    PS C:\> DirD \KMDFDriver1.sys /s
    ```

4.  Ausgabe ähnlich der folgenden sollte angezeigt werden.

    ``` syntax
    Volume in drive C is MainOS
    Volume Serial Number is 965E-2180
    Directory of C:\windows\system32\DRIVERS
    04/21/2014  05:23 PM              8864 KMDFDriver1.sys
                   1 File(s)           8864 bytes
         Total Files Listed:
                   1 File(s)           8864 bytes
                   0 Dir(s)       409976832 bytes free
    ```

5.  Debugausgabe für KdPrint(), KdPrintEx() und DbgPrint() Nachrichten durch Festlegen eines Registrierungsschlüssels zu aktivieren. Legen Sie den Registrierungsschlüssel, sodass es persistent Neustart (für nicht Einzelhandel Bilder) wird mithilfe des Befehls TShell **RegD hinzufügen** .

    ``` syntax
    DEVICE C:\
    PS C:\Windows\system32> RegD Add "HKLM\SYSTEM\ControlSet001\Control\Session Manager\Debug Print Filter" /v DEFAULT /t REG_DWORD /d 0xFFFFFFFF

    The operation completed successfully.
    ```

6.  Vergewissern Sie sich, dass dieser Registrierungsschlüssel festgelegt wurde, mithilfe des Befehls TShell **RegD Abfrage** .

    ``` syntax
    DEVICE C:\
    PS C:\Windows\system32> RegD Query "HKLM\SYSTEM\ControlSet001\Control\Session Manager\Debug Print Filter"

    HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\Session Manager\Debug Print Filter
        DEFAULT    REG_DWORD    0xffffffff
    ```

### <a name="a-href-idwindbgaverify-that-the-driver-loads-using-windows-debug"></a><a href="" id="windbg"></a>Stellen Sie sicher, dass der Treiber lädt mithilfe von Windows: Debuggen

Führen Sie zum Anzeigen des Ladevorgangs Treiber die folgenden Schritte aus, um eine Debuganweisung im Treiber festgelegt, und schließen Sie das Gerät an den Kerneldebugger.

1.  Öffnen Sie das Treiber-Projekt in Visual Studio.

2.  Fügen Sie eine Debug Break-Anweisung in Driver.c unmittelbar nach der Deklaration der Variablen Abschnitt der Routine "DriverEntry" hinzu.

    ``` syntax
       …
        WDF_DRIVER_CONFIG config;
        NTSTATUS status;
        WDF_OBJECT_ATTRIBUTES attributes;

        // Debug break statement to stop loading of OS 
        // Debugger must be attached to allow the device to boot
         __debugbreak();
    …
    ```

    **Warnung**  
    Die Debug Break-Anweisung beenden Sie das Telefon aus einer virtuellen Festplatte gestartet, es sei denn, ein Debugger an das Gerät angeschlossen ist.

     

3.  Erstellen Sie das Projekt in Visual Studio neu.

4.  Falls erforderlich, kopieren Sie die aktualisierte sys-Datei in das Verzeichnis, mit denen Sie erstellen, um das Paket zu generieren.

5.  Wiederholen Sie dann die oben beschriebenen Schritte aus:

    1.  Generieren eines Pakets aktualisierten Treiber.

    2.  Generieren, Signieren und flash das Bild.

    **Hinweis**  
    Es ist auch möglich, die Version des Treibers aktualisieren, indem Sie die Treiberversion in der INF-Datei und dann mithilfe der IUTool zum Bereitstellen von des aktualisierten Treibers für das Telefon. Weitere Informationen zur Verwendung von IUTool finden Sie unter [IUTool.exe: Updatepakete auf einem Telefon](update-packages-on-a-phone-and-get-package-update-logs.md). Dieser Prozess ähnelt der Prozess, der zum Erstellen eines Treiberupdates verwendet wird. Weitere Informationen hierzu finden Sie unter [KMDF Gerätetreiber zu aktualisieren](../../service/mobile/update-a-kmdf-device-driver.md).

     

6.  Richten Sie eine KDNET über USB-Anschluss an das Telefon für das debugging.

7.  Starten Sie den Windows-Debugger an.

    ``` syntax
    windbg -k net:port=5000,key=1.2.3.4
    ```

8.  Nachdem das Gerät gestartet wurde, wird der Haltepunkt erreicht und Ausführen des Codes wird beendet. Der Debugger wird angegeben, dass dieser Unterbrechungspunkt erreicht wurde.

9.  Legen Sie den Symbolpfad auf den Speicherort der Windows-Treiberkits Symbole und Laden Sie Symbole neu zu.

    ``` syntax
    .SYMPATH+ C:\SYMBOLS
    .reload /f
    ```

10. Legen Sie den Quell-Pfad zum Speicherort der der c-Quellcode, den Sie zuvor in Visual Studio erstellt haben.

    ``` syntax
    .srcpath+ C:\KMDFDriver1\Source\
    ```

11. Auflisten der Aufrufliste mithilfe des Befehls **k** .

    ``` syntax
    0: kd> k
    # Child-SP RetAddr  Call Site
    00 85679c68 90fd2abe KMDFDriver1!DriverEntry+0xa
    01 85679ce0 90fd2b38 KMDFDriver1!FxDriverEntryWorker+0x6a
    02 85679d00 81770990 KMDFDriver1!FxDriverEntry+0x18
    *** ERROR: Symbol file could not be found.  Defaulted to export symbols for ntkrnlmp.exe - 
    03 85679d10 818f8004 nt!SeTokenIsAdmin+0x1790
    04 85679e10 8190d630 nt!KeFindConfigurationNextEntry+0x7c48
    05 85679e68 8185719e nt!KeHwPolicyLocateResource+0x4698
    06 85679e70 814c5e0c nt!IoReplacePartitionUnit+0x192
    07 85679e80 81460172 nt!IoAllocateIrp+0x57c
    08 85679ec8 00000000 nt!KiDispatchInterrupt+0x234a
    ```

    Die Aufrufliste ist der Kette Funktionsaufrufe, die auf die aktuelle Position des Leistungsindikators Programm geführt haben. Die Top-Funktion in der Aufrufliste ist die aktuelle Funktion, und die nächste Funktion ist die Funktion, die die aktuelle Funktion aufgerufen und so weiter.

12. Anzeigen von Symbolinformationen im Zusammenhang mit KMDFDriver1 mit dem Befehl **X** .

    ``` syntax
    0: kd> x KMDFDriver1!*
    90fd4750          KMDFDriver1!WdfDriverGlobals = 0x88ff4de8
    90fd4754          KMDFDriver1!WdfDriverStubDriverObject = 0x88fed768
    90fd4004          KMDFDriver1!__security_cookie_complement = 0x568f867
    90fd336c          KMDFDriver1!__gsfailure_xdata_end = <unknown base type 80000013>
    90fd33b4          KMDFDriver1!__memcpy_reverse_large_neon_xdata = <unknown base type 80000013>
    90fd30c0          KMDFDriver1!WPP_c0dfc8e231dc218098dc0c2ed20d6e73_Traceguids = struct _GUID [1]
    90fd30a0          KMDFDriver1!GUID_DEVINTERFACE_KmdfDriver1 = struct _GUID {e7a4cfb0-56d4-4234-bf60-fe627cb5e981}
    90fd474c          KMDFDriver1!WdfDriverStubDisplacedDriverUnload = 0x00000000
    90fd3370          KMDFDriver1!memcpy_xdata_prolog = <unknown base type 80000013>
    90fd3388          KMDFDriver1!__memcpy_forward_large_neon_xdata = <unknown base type 80000013>
    90fd4758          KMDFDriver1!WdfDriverStubOriginalWdfDriverMiniportUnload = 0x00000000
    ```

13. Listeninformationen zu den Modulen auf KMDFDriver1 mithilfe des Befehls **lm m** .

    ``` syntax
    0: kd> lm m KMDFDriver1 v
    Browse full module list
    start    end        module name
    90fd1000 90fd9000   KMDFDriver1   (private pdb symbols)  c:\kmdfdriver1\KmdfDriver1.pdb
        Loaded symbol image file: KMDFDriver1.sys
        Image path: KMDFDriver1.sys
        Image name: KMDFDriver1.sys
        Browse all global symbols  functions  data
        Timestamp:        Thu Jul 31 14:39:34 2014 (53DAB796)
        CheckSum:         000037D2
        ImageSize:        00008000
        Translations:     0000.04b0 0000.04e4 0409.04b0 0409.04e
    ```

14. Laden Sie die WDF Treiber-Erweiterungen mit dem Befehl **.load** .

    ``` syntax
    .load C:\Program Files (x86)\Windows Kits\10\Debuggers\x86\winext\Wdfkd.dll
    ```

15. Vergewissern Sie sich, dass die Erweiterung WDF Debuggen mithilfe von geladen wird die **! wdfkd.help** WDK Treiber Erweiterung Hilfebefehl.

    ``` syntax
    !wdfkd.help
    ```

16. Anzeigen von Informationen zur Verwendung Treiber die **! wdfkd.wdfdriverinfo** Befehl.

    ``` syntax
    0: kd> !wdfkd.wdfdriverinfo KMDFDriver1
    ----------------------------------
    Default driver image name: KMDFDriver1
    WDF library image name: Wdf01000
    FxDriverGlobals  0x90584008
    WdfBindInfo      0x913d8008
       Version        v1.11
    Library module   0x8283b528
       ServiceName    \Registry\Machine\System\CurrentControlSet\Services\Wdf01000
       ImageName      Wdf01000
    ----------------------------------
    Driver Handles is NULL
    ```

17. Ende der debugging Sitzung über die **%qd** beenden und Befehl trennen.

    ``` syntax
    0: kd> qd
    ```

 

 

[Senden Sie Kommentare zu diesem Thema an Microsoft] (mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback%20%5Bp_phFlashing\p_phFlashing%5D:%20Adding%20a%20driver%20to%20a%20test%20image%20%20RELEASE:%20%2810/4/2016%29&body=%0A%0APRIVACY%20STATEMENT%0A%0AWe%20use%20your%20feedback%20to%20improve%20the%20documentation.%20We%20don't%20use%20your%20email%20address%20for%20any%20other%20purpose,%20and%20we'll%20remove%20your%20email%20address%20from%20our%20system%20after%20the%20issue%20that%20you're%20reporting%20is%20fixed.%20While%20we're%20working%20to%20fix%20this%20issue,%20we%20might%20send%20you%20an%20email%20message%20to%20ask%20for%20more%20info.%20Later,%20we%20might%20also%20send%20you%20an%20email%20message%20to%20let%20you%20know%20that%20we've%20addressed%20your%20feedback.%0A%0AFor%20more%20info%20about%20Microsoft's%20privacy%20policy,%20see%20http://privacy.microsoft.com/default.aspx. "Senden Sie Kommentare zu diesem Thema an Microsoft")




