---
author: kpacquer
Description: "Aktualisieren eines Gerätetreibers KMDF"
ms.assetid: e391e00a-b764-4d47-8e14-30b4446ddfb2
MSHAttr: PreferredLib:/library/windows/hardware
title: "Aktualisieren eines Gerätetreibers KMDF"
ms.openlocfilehash: edaae7f63e11c989cf8385469b7a8c60c600457c
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="update-a-kmdf-device-driver"></a>Aktualisieren eines Gerätetreibers KMDF


Wie alle anderen Komponenten, die das Betriebssystem hinzugefügt werden, sind KMDF (Kernelmodus-Treiberframework) Treiber in das Betriebssystemabbild enthalten, mithilfe von .spkg Paketdateien, auf die verwiesen wird, werden durch eine OEMInput.xml-Datei, wenn OEMs erstellt das Image.

In ähnlicher Weise werden Treiber-Updates mithilfe von Paketdateien .spkg veröffentlicht. Wie alle Paket-Updates muss die Version des Pakets für jedes Update erhöht werden; Weitere Informationen finden Sie unter [Anforderungen zu aktualisieren](update-requirements.md). Treiberupdates vorbereitet werden, muss der Wert der **-** Richtlinie für die in der Treiber-INF-Datei auch erhöht. In dieser exemplarischen Vorgehensweise zeigt Informationen zum Vorbereiten einer KMDF Gerätetreiber-Update und bestätigen Sie, dass der Treiber vom Betriebssystem geladen wird.

In diesem Thema wird davon ausgegangen, dass Sie sich vertraut mit den allgemeinen Konzepten Windows-Gerätetreiberinstallation und die Verwendung der INF-Datei zugeordnet sind. Weitere Informationen finden Sie unter [Installation Gerät und Treiber](https://msdn.microsoft.com/library/windows/hardware/ff549731).

## <a name="span-iddriverinffilesandupdatesspanspan-iddriverinffilesandupdatesspanspan-iddriverinffilesandupdatesspandriver-inf-files-and-updates"></a><span id="Driver_INF_files_and_updates"></span><span id="driver_inf_files_and_updates"></span><span id="DRIVER_INF_FILES_AND_UPDATES"></span>Treiberdateien INF-Datei und updates


Visual Studio generiert automatisch eine INF-Datei beim Erstellen eines Windows 10 Mobile KMDF Treiber Projekts. Installation des Treibers verwendet die INF-Datei in Windows direkt aus. Die INF-Datei wird jedoch in Windows 10 Mobile in einer Registrierungsdatei (reg) Einträge umgewandelt. Wenn der Treiber verpackt wird, ist die REG-Datei in der Datei .spkg enthalten.

Wenn Sie ein KMDF Treiber-Update zu erstellen, müssen zwei Versionsnummern erhöht werden: die Versionsnummer der Datei Paket .spkg und der **DriverVer** Wert in der INF-Datei.

**Version des Pakets**

Die Versionsnummer des Pakets muss dazu führen, dass das Update auf das Betriebssystem angewendet werden soll, um erhöht werden. Wenn die Updatepaket-Version nicht größer als die vorhandene Version ist, wird das Update nicht angewendet werden.

**Treiberversion INF-Datei**

Versionsnummer der INF-Datei muss erhöht werden, um führen die aktualisierten Treiber-Daten auf den aktiven Treiber-Registrierungsschlüssel in der System-Struktur angewendet werden soll. Die Version des Treibers wird in folgendem Format angegeben:

*MM*/*DD*/*YYYY*, *n*. *n*. *n*. *n*

*MM* ist Monat und *JJJJ* ist Year, gefolgt von der Versionsnummer *DD* Tag ist. Die erste Ziffer der Versionsnummer wird die Hauptversion, gefolgt von der Nebenversionen. Treiber für wird die gesamte Zeichenfolge als Versionsnummer ausgewertet. Wenn nur das Datum (*MM*/*DD*/*JJJJ*) wird erhöht, es gilt als eine neuere Version des Treibers.

## <a name="span-iddriverwalkthroughintroductionspanspan-iddriverwalkthroughintroductionspanspan-iddriverwalkthroughintroductionspandriver-walkthrough-introduction"></a><span id="Driver_walkthrough_introduction"></span><span id="driver_walkthrough_introduction"></span><span id="DRIVER_WALKTHROUGH_INTRODUCTION"></span>Einführung in die Treiber Exemplarische Vorgehensweise


Treiber Update dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben behandelt:

-   [Erstellen des Treiberpakets Version 1](#buildtheversion1)

-   [Hinzufügen des Version 1-Treibers für das Betriebssystem](#addingtheversion1)

-   [Zeigen Sie die Einstellungen der Treiber-Registrierung](#viewtheregistry)

-   [Überprüfen Sie die Registrierungsschlüssel, um zu bestätigen, dass der Treiber aktiv ist.](#examinetheregistrykeys)

-   [Erstellen des Treiberpakets Version 2](#buildingtheversion2)

-   [Hinzufügen des Version 2-Treibers für das Betriebssystem](#addingtheversion2)

-   [Vergewissern Sie sich, dass der Treiber aktiv ist.](#confirmthattheupdateddriver)

In diesem Beispiel werden die folgenden Versionsnummern verwendet:

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Treiberversion in INF-Datei</th>
<th align="left">Version des Pakets</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>11/01/2012,1.00.00.00</p></td>
<td align="left"><p>8.00.9907.12</p></td>
</tr>
<tr class="even">
<td align="left"><p>02/19/2013,1.32.00.00</p></td>
<td align="left"><p>8.00.10211.25</p></td>
</tr>
</tbody>
</table>

 

-Datei des Treibers heißt XKmdfDriver.sys, und die INF-Datei ist XKmdfDriver.inf.

**Hinweis**  
Ersetzen Sie diese Dateinamen mit dem Namen des Treibers, die Sie in dieser exemplarischen Vorgehensweise verwenden möchten.

 

Der ursprüngliche Treiber befinden sich die \\Version1 Ordner und der aktualisierten Version befinden sich im \\Version2.

Die exemplarischen Vorgehensweise wird davon ausgegangen, dass die folgenden Umgebungsvariablen sind ähnlich wie hier gezeigt wird:

``` syntax
set AK_ROOT=C:\Program Files (x86)\Windows Kits\10
set WINKIT_ROOT=C:\Program Files (x86)\Windows Kits\10
PATH=%AK_ROOT%\Tools\bin\i386;%WINKIT_ROOT%\bin\x86;%PATH%
```

## <a name="span-idbuildtheversion1spanspan-idbuildtheversion1spanspan-idbuildtheversion1spanbuild-the-version-1-driver-package"></a><span id="BuildTheVersion1"></span><span id="buildtheversion1"></span><span id="BUILDTHEVERSION1"></span>Erstellen des Treiberpakets Version 1


Verwenden Sie die folgenden Schritte aus, um den Treiber der Version 1 im Betriebssystem einzubeziehen.

1.  Kopieren Sie die Treiberdateien auf die \\Version1 Verzeichnis:

    -   XKmdfDriver.inf

    -   XKmdfdriver.pkg.xml

    -   XKmdfDriver.sys

2.  Legen Sie in der Datei XKmdfDriver.inf die `DriverVer` Richtlinie in der `[Version]` -Abschnitt wie hier gezeigt. Die hervorgehobene Zeichenfolge "11/01/2012,1.00.00.00" ist die Versionsnummer des Treibers.

    ``` syntax
    …
    [Version]
    Signature="$WINDOWS NT$"
    Class=System
    ClassGuid={4d36e97d-e325-11ce-bfc1-08002be10318}
    Provider=%MSFT%
    DriverVer=11/01/2012,1.00.00.00
    BootCritical=1

    [DestinationDirs]
    DefaultDestDir = 12
    …
    ```

3.  Das Paket-XML (XKmdfdriver.pkg.xml) für Treiber, Version 1, wird unten angezeigt. Geben Sie OEM `Owner` Name.

    ``` syntax
    <?xml version="1.0" encoding="utf-8"?>
    <Package xmlns="urn:Microsoft.WindowsPhone/PackageSchema.v8.00"
      Owner="OEMName"
      OwnerType="OEM"     
      ReleaseType="Test"
      Platform="QC8960"           
      Component="Phone.Test.BaseOS"
      SubComponent="XKmdfDriver"
      Partition="MainOS"
      BinaryPartition="false">
      <Components>
        <OSComponent>
            <Files>
                <File Source="XKmdfDriver.sys" DestinationDir="$(runtime.system32)\drivers"/>
            </Files>
        </OSComponent>
        <Driver InfSource="XKmdfDriver.inf">
            <Reference Source="XKmdfDriver.sys"/>
        </Driver>
      </Components>
    </Package>
    ```

4.  Zum Verschieben der \\Version1 Verzeichnis, legen die Paketversion wie dargestellt, und des Treiberpakets erstellen.

    ``` syntax
    cd \Version1
    set PKGVER=8.00.9907.12
    pkggen  XKmdfDriver.pkg.xml /version:%PKGVER% /build:fre /cpu:ARM /config:"%AK_ROOT%\Tools\bin\i386\pkggen.cfg.xml" /output:. /variables:"HIVE_ROOT=%AK_ROOT%\CoreSystem"
    ```

5.  Bestätigen Sie, dass die *OEMName*. Phone.Test.BaseOS.XKmdfDriver.spkg-Paket erstellt wurde.

## <a name="span-idaddingtheversion1spanspan-idaddingtheversion1spanspan-idaddingtheversion1spanadd-the-version-1-driver-to-the-os"></a><span id="AddingTheVersion1"></span><span id="addingtheversion1"></span><span id="ADDINGTHEVERSION1"></span>Hinzufügen des Version 1-Treibers für das Betriebssystem


Gehen Sie folgendermaßen vor, Treiber, Version 1 in das Betriebssystem mithilfe von IUTool und eine Produktion einschließen oder Build testen. Alternativ schließen Sie das Paket in ein Bild, und klicken Sie dann das Abbild auf dem Telefon flash.

1.  Schließen Sie das Gerät mit einem USB-Kabel an den PC.

2.  Verwenden Sie IuTool, Version 1 Treiberpakets zu einem vorhandenen Bild hinzuzufügen.

    ``` syntax
    IuTool -p OEMName.Phone.Test.BaseOS.XKmdfDriver.spkg
    ```

3.  Vergewissern Sie sich, dass die IuTool Bereitstellen des Pakets an dem Gerät konnte

## <a name="span-idviewtheregistryspanspan-idviewtheregistryspanspan-idviewtheregistryspanview-the-driver-registry-settings"></a><span id="ViewTheRegistry"></span><span id="viewtheregistry"></span><span id="VIEWTHEREGISTRY"></span>Zeigen Sie die Einstellungen der Treiber-Registrierung


Verwenden Sie das folgende Verfahren, um binden Sie das Gerät im Modus Massenspeichergerät und Anzeigen der Registrierungs.

1.  Neustart des Geräts auf den USB-Massenspeichergerät-Modus. Dies erfolgt mithilfe einer bestimmten Tastenfolge auf dem Telefon – beispielsweise gedrückter Kamera beim Einschalten einrichten.

2.  Schließen Sie das Gerät an den PC mit einem USB-Kabel an.

3.  Wenn das Gerät mit dem PC im USB-Massenspeichergerät Modus verbunden ist, wird es als ein logisches Laufwerk, auf dem PC angezeigt.

4.  Öffnen Sie ein Eingabeaufforderungsfenster als Administrator.

5.  Suchen Sie nach der Registrierungsstruktur "SYSTEM" unterhalb des Ordners ** \\WINDOWS\\SYSTEM32\\CONFIG**.

6.  Starten Sie den Registrierungseditor (Regedit.exe) auf dem PC.

7.  Klicken Sie im Registrierungs-Editor auf **Datei** &gt; Struktur **Struktur laden** und Laden Sie das SYSTEM.

8.  Geben Sie einen Namen für die importierten Struktur – in diesem Beispiel TREIBER\_VERSION1

9.  Wechseln Sie zum nächsten Abschnitt, um den Inhalt der importierten Registrierungsstruktur zu überprüfen.

## <a name="span-idexaminetheregistrykeysspanspan-idexaminetheregistrykeysspanspan-idexaminetheregistrykeysspanexamine-the-registry-keys-to-confirm-that-the-driver-is-active"></a><span id="ExamineTheRegistryKeys"></span><span id="examinetheregistrykeys"></span><span id="EXAMINETHEREGISTRYKEYS"></span>Überprüfen Sie den Registrierungsschlüssel, um zu bestätigen, dass der Treiber aktiv ist.


Wenn Windows 10 Mobile den Treiber installiert, werden in der Struktur "SYSTEM" die folgenden Registrierungsschlüsseln angezeigt:

-   Ein Treiber-spezifische Registrierungsschlüssel erstellt unter `SYSTEM\DriverDatabase`.

-   Ein aktiven Treiber Unterschlüssel wird erstellt unter `SYSTEM\ControlSet001\Enum\ROOT\XKmdfDriver`.

Diese zwei Bereiche werden in den folgenden Abschnitten erläutert. Verwenden Sie diese Informationen in der Registrierung, um festzustellen, ob der Treiber installiert werden kann und das Betriebssystem verfügt über die Hardware erkannt und installiert die richtige Version des Treibers.

### <a name="span-iddriverdatabasespanspan-iddriverdatabasespanspan-iddriverdatabasespandriver-database"></a><span id="Driver_database"></span><span id="driver_database"></span><span id="DRIVER_DATABASE"></span>Treiberdatenbank

Treiber Einstellungen sind für eine spätere Installation in mehrstufigen `SYSTEM\DriverDatabase`. Das Betriebssystem verwendet diesem Unterschlüssel, um Treiber zu installieren, wenn die neue Hardware identifiziert wird. Sie enthält:

-   Informationen zu den XKmdfDriver.inf

-   Eine bestimmte GUID `{4d36e97d-e325-11ce-bfc1-08002be10318}` , identifiziert die XKmdfDriver als ein SYSTEM-Klassentreiber kein Treiber, der einen dynamisches auflistbaren Bus (wie ACPI oder USB) verwendet. In diesem Beispiel wird einen System-Klassentreiber um die exemplarische Vorgehensweise zu vereinfachen, aber veranschaulichten Konzepte sind vergleichbar mit anderen Arten von Treiber.

Wenn das Paket installiert ist, wird die XKmkdfDriver.inf hinzugefügt `[SYSTEM\DriverDatabase\DeviceIds\{4d36e97d-e325-11ce-bfc1-08002be10318}]`, wobei `{4d36e97d-e325-11ce-bfc1-08002be10318}` Systemtreiber-GUID ist.

Im folgenden finden Sie die Systemtreiber-GUID in der `[SYSTEM\DriverDatabase\DeviceIds\Root\XKmdfDriver]` Registrierungsunterschlüssel.

``` syntax
[SYSTEM\DriverDatabase\DeviceIds\Root\XKmdfDriver]
"XKmdfDriver.inf"=hex:01,ff,00,00
[SYSTEM\DriverDatabase\DeviceIds\{4d36e97d-e325-11ce-bfc1-08002be10318}]
..
"XKmdfDriver.inf"=hex(0):
```

Klicken Sie unter der `[SYSTEM\DriverDatabase\DriverInfFiles\XKmdfDriver.inf]` Unterschlüssel, die aktive INF-Datei wird mit dem Eintrag angegeben `"Active"="xkmdfdriver.inf_arm_c8e7ab79be6b088b"`.

Die `"Active"` Eintrag zeigt auf den aktiven Treiber INF-Datei. Bei der Aktualisierung des Treiberpakets stehen mehrere INF-Einstellungen, und `"Active"` mit dem neuesten verweist.

``` syntax
[SYSTEM\DriverDatabase\DriverInfFiles\XKmdfDriver.inf]
"Active"="xkmdfdriver.inf_arm_c8e7ab79be6b088b"
@=hex(7):78,00,6b,00,6d,00,64,00,66,00,64,00,72,00,69,00,76,00,65,00,72,00,2e,\
00,69,00,6e,00,66,00,5f,00,61,00,72,00,6d,00,5f,00,63,00,38,00,65,00,37,00,\
61,00,62,00,37,00,39,00,62,00,65,00,36,00,62,00,30,00,38,00,38,00,62,00,00,\
00,00,00
"Configurations"=hex(7):58,00,4b,00,4d,00,44,00,46,00,44,00,52,00,49,00,56,00,\
45,00,52,00,2e,00,4e,00,54,00,00,00,00,00
```

Die `[SYSTEM\DriverDatabase\DriverPackages\xkmdfdriver.inf_arm_c8e7ab79be6b088b]` Unterschlüssel eine Replikation des Inhalts der XKmdfDriver.inf enthält.

``` syntax
[SYSTEM\DriverDatabase\DriverPackages\xkmdfdriver.inf_arm_c8e7ab79be6b088b]
@="XKmdfDriver.inf"
"BootCritical"=dword:00000001
"Provider"="Microsoft"
"SignerName"=""
"SignerScore"=dword:0d000003
"Version"=hex:ff,ff,05,00,00,00,00,00,7d,e9,36,4d,25,e3,ce,11,bf,c1,08,00,2b,\
e1,03,18,00,40,f9,d5,c3,b7,cd,01,00,00,00,00,00,00,01,00,00,00,00,00,00,00,\
00,00
```

Diese Unterschlüssel verweist auf den Dienst mit dem Systemtreiber verknüpft ist:

``` syntax
[SYSTEM\DriverDatabase\DriverPackages\xkmdfdriver.inf_arm_c8e7ab79be6b088b\Configurations\XKMDFDRIVER.NT]
"ConfigFlags"=dword:00000000
"Service"="XKmdfDriver"
```

In diesem Unterschlüssel legt den Treiber Beschreibungszeichenfolgen:

``` syntax
[SYSTEM\DriverDatabase\DriverPackages\xkmdfdriver.inf_arm_c8e7ab79be6b088b\Descriptors\Root\XKmdfDriver]
"Configuration"="XKMDFDRIVER.NT"
"Description"="%xkmdfdriver_devdesc%"
"Manufacturer"="%StdMfg%"
```

Diesem Unterschlüssel wird der Wert der Treiber Beschreibungszeichenfolge:

``` syntax
[SYSTEM\DriverDatabase\DriverPackages\xkmdfdriver.inf_arm_c8e7ab79be6b088b\Strings]
"xkmdfdriver_devdesc"="X KMDF Driver"
```

### <a name="span-idcontrolsetenumerationspanspan-idcontrolsetenumerationspanspan-idcontrolsetenumerationspancontrol-set-enumeration"></a><span id="Control_set_enumeration"></span><span id="control_set_enumeration"></span><span id="CONTROL_SET_ENUMERATION"></span>Steuerelement festgelegt (Aufzählung)

`[SYSTEM\ControlSet001\Enum\ROOT\XKmdfDriver]`wird erstellt, wenn das Betriebssystem erfolgreich der übereinstimmenden Gerätetreiber mit der INF-Datei installiert. Weitere Informationen finden Sie unter [HKLM\\SYSTEM\\CurrentControlSet\\Enum Registrierungsbaum](http://msdn.microsoft.com/library/windows/hardware/ff546173.aspx) auf MSDN.

Die `Control` Unterschlüssel enthält Informationen zum Steuern der Systemstart und einige Aspekte des Geräts. Weitere Informationen finden Sie unter [HKLM\\SYSTEM\\CurrentControlSet\\Steuerelement Registrierungsbaum](http://msdn.microsoft.com/library/windows/hardware/ff546165.aspx) auf MSDN.

`SYSTEM\ControlSet001\Control\Class\{4d36e97d-e325-11ce-bfc1-08002be10318}\0120`Gibt an, dass der Treiber den 120. Rang zwischen Systemtreibern verfügt. Dieser Unterschlüssel enthält den Treiberdatum und die Version, wie hier gezeigt:

``` syntax
[SYSTEM\ControlSet001\Control\Class\{4d36e97d-e325-11ce-bfc1-08002be10318}\0120]
"DriverDesc"="X KMDF Driver"
"ProviderName"="Microsoft"
"DriverDateData"=hex:00,40,f9,d5,c3,b7,cd,01
"DriverDate"="11-1-2012"
"DriverVersion"="1.0.0.0"
"InfPath"="XKmdfDriver.inf"
"InfSection"="XKMDFDRIVER.NT"
"MatchingDeviceId"="ROOT\\XKmdfDriver"
```

Der Unterschlüssel DeviceClasses enthält die Geräte-ID:

``` syntax
[SYSTEM\ControlSet001\Control\DeviceClasses\{5cdce65b-f1bc-4e15-a1f8-c541f21c43f2}\##?#ROOT#XKmdfDriver#0000#{5cdce65b-f1bc-4e15-a1f8-c541f21c43f2}]
"DeviceInstance"="ROOT\\XKmdfDriver\\0000"
```

Diese nächsten Unterschlüssel ordnet die XKmdfDriver das System ContainerId 00000000-0000-0000-Ffff-Ffffffffffff:

``` syntax
[SYSTEM\ControlSet001\Control\DeviceContainers\{00000000-0000-0000-FFFF-FFFFFFFFFFFF}\BaseContainers\{00000000-0000-0000-FFFF-FFFFFFFFFFFF}]
..
"ROOT\\XKmdfDriver\\0000"=hex(0):
..
```

`[SYSTEM\ControlSet001\Enum\ROOT\XKmdfDriver\0000]`enthält Informationen zu den installierten Treiber. Es wurde eine Instanz `XKmdfDriver\0000`:

``` syntax
[SYSTEM\ControlSet001\Enum\ROOT\XKmdfDriver\0000]
"HardwareID"=hex(7):52,00,4f,00,4f,00,54,00,5c,00,58,00,4b,00,6d,00,64,00,66,\
  00,44,00,72,00,69,00,76,00,65,00,72,00,00,00,00,00
"ConfigFlags"=dword:00000000
"DeviceReported"=dword:00000001
"Service"="XKmdfDriver"
"Capabilities"=dword:00000000
"ClassGUID"="{4d36e97d-e325-11ce-bfc1-08002be10318}"
"DeviceDesc"="@XKmdfDriver.inf,%xkmdfdriver_devdesc%;X KMDF Driver"
"Driver"="{4d36e97d-e325-11ce-bfc1-08002be10318}\\0120"
"Mfg"="@XKmdfDriver.inf,%StdMfg%;"
"ContainerID"="{00000000-0000-0000-FFFF-FFFFFFFFFFFF}"
```

`[SYSTEM\ControlSet001\services\XKmdfDriver]`die Treiberdatei "Image" Wert enthält. Es ist ASCII-Zeichen im Binärformat hexadezimale codiert. Der aktuelle Wert ist "Image" REG =\_EXPAND\_SU: "\\SystemRoot\\System32\\Treiber\\XKmdfDriver.sys". Weitere Informationen finden Sie unter [Werttypen Registrierung](http://msdn.microsoft.com/library/windows/desktop/ms724884.aspx) auf MSDN.

``` syntax
[SYSTEM\ControlSet001\services\XKmdfDriver]
"DisplayName"="@XKmdfDriver.inf,%xkmdfdriver_DevDesc%;X KMDF Driver"
"ErrorControl"=dword:00000001
"ImagePath"=hex(2):5c,00,53,00,79,00,73,00,74,00,65,00,6d,00,52,00,6f,00,6f,00,\
74,00,5c,00,53,00,79,00,73,00,74,00,65,00,6d,00,33,00,32,00,5c,00,64,00,72,\
00,69,00,76,00,65,00,72,00,73,00,5c,00,58,00,4b,00,6d,00,64,00,66,00,44,00,\
72,00,69,00,76,00,65,00,72,00,2e,00,73,00,79,00,73,00,00,00
"Start"=dword:00000001
"Type"=dword:00000001
"Owners"=hex(7):58,00,4b,00,6d,00,64,00,66,00,44,00,72,00,69,00,76,00,65,00,72,\
00,2e,00,69,00,6e,00,66,00,00,00,00,00
```

`[SYSTEM\ControlSet001\services\XKmdfDriver\Parameters\Wdf]`die Versionsnummer WDF enthält:

``` syntax
[SYSTEM\ControlSet001\services\XKmdfDriver\Parameters\Wdf]
"WdfMajorVersion"=dword:00000001
"WdfMinorVersion"=dword:0000000b
"TimeOfLastSqmLog"=hex(b):20,41,89,d7,2c,c0,cd,01
```

## <a name="span-idclosethetoolsspanspan-idclosethetoolsspanspan-idclosethetoolsspanclose-the-tools-and-eject-the-device"></a><span id="CloseTheTools"></span><span id="closethetools"></span><span id="CLOSETHETOOLS"></span>Schließen Sie die Tools und des Geräts


1.  Klicken Sie im Registrierungs-Editor auf **Datei** &gt; **Struktur entfernen** Entladen der `DRIVER_VERSION1` Struktur, sodass die PC-Registrierung in den vorherigen Zustand wiederhergestellt wird.

2.  Schließen Sie den Registrierungs-Editor.

3.  Schließen Sie das Eingabeaufforderungsfenster, und alle geöffneten Instanzen von Windows Explorer, die verwendet wurden, um den temporären Ordner anzuzeigen.

4.  Telefon (verwenden Sie **Hardware sicher entfernen und ausschließen Media** im Infobereich oder den Befehl Windows Explorer **Auswerfen** ) ausschließen, und klicken Sie dann das Gerät vom Computer trennen.

## <a name="span-idbuildingtheversion2spanspan-idbuildingtheversion2spanspan-idbuildingtheversion2spanbuild-the-version-2-driver-package"></a><span id="BuildingTheVersion2"></span><span id="buildingtheversion2"></span><span id="BUILDINGTHEVERSION2"></span>Erstellen des Treiberpakets Version 2


Wie oben beschrieben, werden die neuen Treiberversion 2/19/2013,1.32.00.00, die in einer neuen Paketversion 8.00.10211.25 enthalten sein wird.

1.  Erstellen Sie eine zweite Kopie der Treiberdateien in der \\Verzeichnis Version2.

2.  Bearbeiten Sie die Datei XKmdfDriver.inf, und ändern Sie `DriverVer` auf 02/19/2013,1.32.00.00.

3.  Fügen Sie einen neuen Registrierungswert namens "DW123" vom Typ DWORD hinzu. Das Vorhandensein dieser Schlüssel wird als zusätzliche Angabe, dass Treiber, Version 2 aktiv ist.

    ``` syntax
    [Version]
    Signature="$WINDOWS NT$"
    Class=System
    ClassGuid={4d36e97d-e325-11ce-bfc1-08002be10318}
    Provider=%MSFT%
    DriverVer=02/19/2013,1.32.00.00
    [XKMDFDRIVER.NT.HW]
    AddReg=XKMDFDRIVER.AddReg

    [XKMDFDRIVER.AddReg]
    HKR,," DW123",    %REG_DWORD%, 0x4567
    ...
    ```

4.  Verschieben Sie in der \\Verzeichnis Version2, legen Sie die Paketversion, und erstellen Sie das Paket.

    ``` syntax
    cd \Version2
    set PKGVER=8.00.10211.25
    pkggen  XKmdfDriver.pkg.xml /version:%PKGVER% /build:fre /cpu:ARM /config:"%AK_ROOT%\Tools\bin\i386\pkggen.cfg.xml" /output:. /variables:"HIVE_ROOT=%AK_ROOT%\CoreSystem"
    ```

## <a name="span-idaddingtheversion2spanspan-idaddingtheversion2spanspan-idaddingtheversion2spanadd-the-version-2-driver-to-the-os"></a><span id="AddingTheVersion2"></span><span id="addingtheversion2"></span><span id="ADDINGTHEVERSION2"></span>Hinzufügen des Version 2-Treibers für das Betriebssystem


Gehen Sie folgendermaßen vor, Treiber, Version 2 des Betriebssystems mit IUTool und eine Produktion einschließen oder testen erstellen:

1.  Schließen Sie das Gerät mit einem USB-Kabel an den PC.

2.  Verwenden Sie IuTool ein vorhandenes Bild des Treiberpakets Version 2 hinzugefügt.

    ``` syntax
    IuTool -p OEMName.Phone.Test.BaseOS.XKmdfDriver.spkg
    ```

3.  Vergewissern Sie sich, dass die IUTool Bereitstellen des Pakets an dem Gerät konnte

## <a name="span-idconfirmthattheupdateddriverspanspan-idconfirmthattheupdateddriverspanspan-idconfirmthattheupdateddriverspanconfirm-that-the-updated-driver-is-active"></a><span id="ConfirmThatTheUpdatedDriver"></span><span id="confirmthattheupdateddriver"></span><span id="CONFIRMTHATTHEUPDATEDDRIVER"></span>Vergewissern Sie sich, dass der Treiber aktiv ist.


Verwenden Sie den folgenden Vorgang um zu bestätigen, dass der Treiber aktiv ist.

1.  Verwenden Sie den oben beschriebenen Vorgang in der [Ansicht der registrierungseinstellungen Treiber](#viewtheregistry) zum Laden und Anzeigen der Registrierungsstruktur "System".

2.  DriverPackages müssen zwei wichtige INF-Registrierung-Sätze: einen für die zuvor installierten Treiber und die für den aktualisierten Treiber.

    ``` syntax
    [SYSTEM\DriverDatabase\DriverPackages\xkmdfdriver.inf_arm_6ec7dae5e1ab5fd5]
    [SYSTEM\DriverDatabase\DriverPackages\xkmdfdriver.inf_arm_c8e7ab79be6b088b]
    ```

3.  `Active`in XKmdfDriver.inf muss auf dem neuere INF-Schlüssel verweisen:

    ``` syntax
    [SYSTEM\DriverDatabase\DriverInfFiles\XKmdfDriver.inf]
    "Active"="xkmdfdriver.inf_arm_6ec7dae5e1ab5fd5"
    ```

4.  Der Treiber hat immer noch den 120. Rang unter Treiber SYSTEM-Klasse, aber das Datum und die Version aktualisiert werden sollen.

    -   "DriverDate"="2-19-2013"

    -   "DriverVersion" = "1.32.0.0"

    ``` syntax
    [SYSTEM\ControlSet001\Control\Class\{4d36e97d-e325-11ce-bfc1-08002be10318}\0120]
    "DriverDate"="2-19-2013"
    "DriverDateData"=hex:00,c0,69,0f,34,0e,ce,01
    "DriverDesc"="X KMDF Driver"
    "DriverVersion"="1.32.0.0"
    "InfPath"="XKmdfDriver.inf"
    "InfSection"="XKMDFDRIVER.NT"
    "MatchingDeviceId"="ROOT\\XKmdfDriver"
    "ProviderName"="Microsoft"
    ```

5.  Der neu hinzugefügte DWORD-Wert DW123 sollte angezeigt werden, unter der `Device Parameters` Unterschlüssel.

    ``` syntax
    [SYSTEM\ControlSet001\Enum\ROOT\XKmdfDriver\0000\Device Parameters]
    "DWORD123"="0x4567"
    ```

6.  Verwenden Sie das weiter oben in [der Tools zu schließen und das Telefon ausschließen](#closethetools) beschriebene Verfahren, um das Gerät sicher zu trennen

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Update](index.md)

 

 






