---
title: Erstellen einer mobilen Bild mit ImgGen.cmd
description: "Tools, die im Lieferumfang von Windows Phone 8.1: Sie ImgGen.cmd verwenden können, um ein Bild für ein Windows-10-Mobile-Gerät zu generieren, das auf Ihrer eigenen Hardware-Design oder wenn Sie nutzen MCSF Anpassung Antwortdateien und andere Ressourcen, die mit der Vorgängerversion generiert wurden."
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 284a2ca2-d973-44a4-9e6c-5caebc088c75
ms.openlocfilehash: 94c66b5a8593332c1d64a44d6c6eb347c6f7a6ff
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="build-a-mobile-image-using-imggencmd"></a>Erstellen einer mobilen Bild mit ImgGen.cmd


Tools, die im Lieferumfang von Windows Phone 8.1: Sie ImgGen.cmd verwenden können, um ein Bild für ein Windows-10-Mobile-Gerät zu generieren, das auf Ihrer eigenen Hardware-Design oder wenn Sie nutzen MCSF Anpassung Antwortdateien und andere Ressourcen, die mit der Vorgängerversion generiert wurden.

Hier wird die Übersicht über die Schritte, die Sie ergreifen können, erstellen Sie ein Bild mit ImgGen.cmd:

1.  Identifizieren Sie die Pakete zum Einschließen in das Bild. Weitere Informationen finden Sie unter [Getting-Pakete für das Bild](#gettingpackages).

2.  Die Pakete verweisen, indem Sie einen oder mehrere Feature Manifestdateien hinzugefügt und speichern Sie diese Dateien in das Stammverzeichnis für Microsoft-Pakete, beispielsweise WPDKCONTENTROOT %\\MSPackages. Weitere Informationen finden Sie unter [Specifying Pakete zum Einschließen in Bildern mithilfe des Feature-Manifestdateien](#specifyingpackagestoinclude).

3.  Führen Sie für jede Geräteplattform folgende Schritte aus:

    1.  Erstellen Sie ein *Gerät Plattform-Paket*, und speichern Sie sie in das Stammverzeichnis für Microsoft-Pakete. Weitere Informationen finden Sie unter [Festlegen von Geräteinformationen-Plattform](set-device-platform-information.md).

    2.  Verweisen auf das Gerät Plattform-Paket in einer Featuremanifestdatei mithilfe des **OEMDevicePlatformPackages** -Elements.

        Sie können mehrere Geräteplattformen in einer Featuremanifestdatei einschließen. Die OEMInput-Datei wird mithilfe der DeviceName verwenden, welches Gerät angeben.

        Image-Erstellung schlägt fehl, es sei denn, ein gültiges Gerät Plattform-Paket für das Bild angegeben wird.

4.  Erstellen einer *OEMInput-Datei* , die die Plattform, die Feature-Manifestdateien und andere Attribute verwendet, um die Definition des Bilds angibt. Weitere Informationen finden Sie unter [Erstellen einer Datei OEMInput, um das Bild zu definieren](#adding).

5.  Erstellen Sie eine Anpassungsdatei Antwort MCSF. Geben Sie mindestens die erforderlichen Plattform Geräteinformationen und die Informationen für das Netzwerk Mobilfunkbetreiber erforderlich. Weitere Informationen finden Sie unter [Antwort Anpassungsdatei](https://msdn.microsoft.com/library/windows/hardware/dn757452) und [Metadaten in DeviceTargetingInfo Telefon](https://msdn.microsoft.com/library/windows/hardware/dn772214).

    **Hinweis**  Wenn Sie multivariant Einstellungen in die Antwortdatei unterstützen möchten, werden der gleiche Satz von Bedingungen wie in der Windows-Bereitstellung in MCSF unterstützt. Finden Sie im Abschnitt *Ziel, TargetState, Bedingung und Prioritäten* in [Erstellen einer Bereitstellung Paket mit multivariant Einstellungen](https://msdn.microsoft.com/library/windows/hardware/dn916108) für eine Liste der unterstützten Bedingungen jedoch sicher, dass das Schema für eine Anpassungsdatei Antwort MCSF befolgen, wenn Sie Ihre **Ziele** in die Antwortdatei angeben.

     

6.  Führen Sie die ImgGen.cmd um das Bild zu erstellen aus. Weitere Informationen finden Sie unter [Verwenden von ImgGen.cmd zum Generieren des Bilds](#usingimggen) unten.

7.  Signieren Sie das Bild, sodass es zu einem Gerät zugeordnet werden kann. Weitere Informationen finden Sie unter [Signieren einer vollständigen flash aktualisierungsabbild (FFU)](sign-a-full-flash-update--ffu--image.md).

## <a name="a-href-idgettingpackagesagetting-packages-for-the-image"></a><a href="" id="gettingpackages"></a>Erste Pakete für das Bild


Vor dem Erstellen eines Abbilds, müssen Sie zunächst alle Pakete identifizieren, die Sie für das Bild benötigen. Es gibt im Allgemeinen drei Kategorien der Pakete, die verwendet werden, um ein Bild zu erstellen:

-   **Microsoft-Pakete**. Dazu gehören alle OS und Microsoft implementierte Treiber für beliebiges Bild benötigten Pakete als auch zusätzliche plattformspezifische Treiber und Firmware Pakete (beispielsweise Pakete für Komponenten, die spezifisch für ein bestimmtes Gerät Lösung oder SoC). Diese Pakete sind in der MobileOS enthalten und muss installiert sein, klicken Sie unter WPDKCONTENTROOT %\\MSPackages. Den folgenden Befehl können Sie den aktuellen Wert der WPDKCONTENTROOT anzeigen.

    ``` syntax
    ECHO %WPDKCONTENTROOT%
    ```

    Feature-Manifestdateien abstrakten den Speicherort und den Gruppierungen der Pakete, die Microsoft bereitstellt. Dies ermöglicht die Angabe einer Gruppe von verwandten Pakete durch eine einzelne Featurename angeben. Angeben des TESTINFRASTRUCTURE-Features umfasst beispielsweise mehrere Pakete, die Ausführung zu unterstützen. Weitere Informationen finden Sie unter [optionale Features zum Erstellen von Bildern](optional-features-for-building-images.md).

-   **SoC Hersteller Pakete**. Dazu gehören Pakete für Treiber und Firmware-Komponenten, die vom Hersteller SoC implementiert. Weitere Informationen über diese Pakete finden Sie in der Dokumentation des Herstellers SoC.

    **Hinweis**  
    Mehrere UEFI-Pakete sind erforderlich, dessen Hersteller SoC startbaren Bilder zu erstellen. Diese Pakete variieren je nach das Layout des Geräts und dessen Hersteller SoC. Die meisten der Pakete Auffüllen binary Partitionen auf dem Gerät. Weitere Informationen zum Erstellen von Lösungspaketen zum Auffüllen diese Partitionen finden Sie unter [Specifying Komponenten in einer Project-Paketdatei](https://msdn.microsoft.com/library/windows/hardware/dn789218)binäre Partition. Die EFI-Systempartition (ESP) wird von Microsoft und OEM-Inhalten aufgefüllt.

     

-   **OEM-Pakete**. Dies sind Pakete, die von OEMs für Inhalte wie Treiber und Anwendungen erstellt. Informationen zum Erstellen von Paketen finden Sie unter [Creating Pakete](creating-mobile-packages.md).

## <a name="a-href-idaddingacreating-an-oeminput-file-to-define-the-image"></a><a href="" id="adding"></a>Erstellen einer Datei OEMInput, um die Definition des Bilds


Um das Bild zu definieren, müssen Sie eine Datei *OEMInput* erstellen. Dies ist eine XML-Datei, die angibt, die folgenden:

-   Der Typ des Bilds zu generieren. Beispielsweise geben Sie, ob das Bild nur Microsoft Produktion Pakete oder eine Kombination von Produktions- und Test-Pakete in das **ReleaseType** -Element enthält, und Sie welche Auflösung das Bild in die **Lösung** -Element unterstützt.

    **Hinweis**  
    OEMs verfügen einige steuern, welche Microsoft-Pakete im Bild enthalten sind, indem Sie unterschiedliche Werte für das Element **ReleaseType** auswählen oder verweisenden Microsoft definierten Features unter dem Element **Features** . Weitere Informationen finden Sie unter [Specifying Pakete zum Einschließen in Bildern mithilfe des Feature-Manifestdateien](#specifyingpackagestoinclude) weiter unten in diesem Thema.

     

-   Die OEM-Pakete zum Einschließen in das Bild. Um anzugeben, welche OEM-Pakete in das Bild enthalten sind, erstellen Sie ein *Feature* -Manifestdatei und verweisen Sie dies in der Datei OEMInput. Weitere Informationen finden Sie unter [Specifying Pakete zum Einschließen in Bildern mithilfe des Feature-Manifestdateien](#specifyingpackagestoinclude) weiter unten in diesem Thema.

Eine vollständige Liste der unterstützten Elemente in der Datei OEMInput finden Sie unter [OEMInput Dateiinhalten](oeminput-file-contents.md).

OEMs sollten als Ausgangspunkt für ihre eigene Bilder in der MobileOS enthaltene OEMInput-Beispieldateien verwenden. Diese Beispieldateien enthalten die Anfangs-Konfiguration für eine Reihe von standard Bildtypen, einschließlich Einzelhandel, Produktion, Test und Produktion Bilder. OEMs sollten jede Datei mit den Paketen erweitern, die die Treiber, Anwendungen und anderen Komponenten, die für ihre Geräte benötigt enthalten. Diese Beispieldateien sind verfügbar unter WPDKCONTENTROOT %\\OEMInputSamples. Richtlinien zum Verwalten einer OEMInput Datei so, dass die neuesten Änderungen an den Microsoft-Beispieldateien hinein integriert werden können, finden Sie unter [Konfigurieren der Datei OEMInput zur Integration von geänderten Features aus der Microsoft-Beispielen](#configuringtheoeminputfile) weiter unten in diesem Thema.

OEMs sollten die SoC wenden, um die Feature-Manifestdateien erhalten, die für ein bestimmtes Gerät verwendet und diese in der Datei OEMInput einbeziehen.

**Hinweis**  
OEMInput XML-Datei unterstützt explizit Pfade und Umgebungsvariablen. Wenn Sie Umgebungsvariablen in Pfade zu Pakete und anderen Dateien verwenden, werden bei der Verarbeitung der OEMInput XML-Datei durch das imaging-Tool die Umgebungsvariablen erweitert. Die Beispieldateien enthalten, mit dem MobileOS verwenden die Umgebungsvariable WPDKCONTENTROOT in einigen der Pfade.

 

### <a name="image-types"></a>Bildtypen

Die folgende Tabelle enthält die Typen der Bilder mit die OEMs erstellen können und die OEMInput Beispiel als die Start-Konfiguration für jeden Bildtyp verwenden.

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>Bildtyp</th>
<th>Beschreibung</th>
<th>OEMInput-Beispiel</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Einzelhandel</p></td>
<td><p>Retail Bilder werden Bilder, die endgültige Retail-Telefone aktualisiert werden. Retail Bilder müssen Microsoft signierten Paketen verwenden, die nach dem Produktion Bilder an Microsoft übermitteln, mithilfe des Tools der OEM-Übermittlung OEMs zurückgegeben werden. Weitere Informationen finden Sie unter [Submit-Binärdateien Retail werden signiert](https://msdn.microsoft.com/library/windows/hardware/dn789223).</p>
<p>Retail Bilder umfassen Folgendes:</p>
<ul>
<li><p>Produktionsversion von Windows-Kernkomponenten in Windows 10 Mobile enthalten</p></li>
<li><p>Produktion 10 Mobile Windows-Komponenten.</p></li>
</ul></td>
<td><p>RetailOEMInput.xml</p></td>
</tr>
<tr class="even">
<td><p>Production</p></td>
<td><p>Produktion Bilder ähneln endgültigen Bilder, aber sie Test Signatur signiert OEM Komponenten sowie Produktion signierte Komponenten ausführen aktiviert haben, und möglicherweise Test-bezogenen Pakete als auch Produktion Pakete enthalten. Produktion Bilder können für engineering Arbeit sowie Mobilfunkbetreiber Versuche und andere Prozesse Zertifizierung verwendet werden. Produktion Bilder werden an Microsoft übermittelt, mithilfe des OEM-Tools zum Absenden Produktion vor dem Generieren des endgültigen Bilds von Microsoft signiert werden. Weitere Informationen finden Sie unter [Submit-Binärdateien Retail werden signiert](https://msdn.microsoft.com/library/windows/hardware/dn789223).</p>
<p>Produktion Bilder umfassen Folgendes:</p>
<ul>
<li><p>Produktionsversion des Windows-Kernkomponenten in Windows 10 Mobile enthalten.</p></li>
<li><p>Produktion 10 Mobile Windows-Komponenten.</p></li>
<li><p>Testen Sie signieren aktiviert.</p></li>
</ul></td>
<td><p>ProductionOEMInput.xml</p></td>
</tr>
<tr class="odd">
<td><p>Test</p></td>
<td><p>Test-Bilder können in außerhalb des Betriebsgeländes Testlabors So testen Sie die Funktionalität des Betriebssystems und Treiber auf einem Gerät ausgeführt werden. Test Bilder umfassen Folgendes:</p>
<ul>
<li><p>Testversion des Windows-Kernkomponenten in Windows 10 Mobile enthalten.</p></li>
<li><p>Produktion 10 Mobile Windows-Komponenten.</p></li>
<li><p>Testen der Signatur aktiviert.</p></li>
<li><p>Testanwendungen, Treibern und anderen Komponenten zum Testen des Betriebssystems in unterschiedlichen Bedingungen verwendet werden.</p></li>
</ul>
<div class="alert">
<strong>Hinweis</strong>  
<p>Um ein Bild zu generieren, OS Tools wie ipconfig.exe, kill.exe, ping.exe, minshutdown.exe, reg.exe, tracelog.exe, sc.exe und tlist.exe enthält, erstellen Sie ein Testbild.</p>
</div>
<div>
 
</div></td>
<td><p>TestOEMInput.xml</p></td>
</tr>
<tr class="even">
<td><p>Integrität</p></td>
<td><p>Integrität Bilder in außerhalb des Betriebsgeländes auszuführenden Testlabors zum Testen der Funktionen Leistung des Geräts. Integrität Bilder ähneln Produktion Bilder, durch das Hinzufügen von Komponenten zum Ausführen von Tests, die im Zusammenhang mit der Leistung.</p></td>
<td><p>HealthOEMInput.xml</p></td>
</tr>
<tr class="odd">
<td><p>Fertigung</p></td>
<td><p>Fertigung Bilder in der Fertigung-Umgebung verwendet werden. Weitere Informationen finden Sie unter [MMOS image-Definition](mmos-image-definition.md).</p></td>
<td><p>MfgOEMInput.xml</p></td>
</tr>
<tr class="even">
<td><p>Kundendienst</p></td>
<td><p>Kunden Vorsicht Bilder enthalten MMOS für den Einzelhandel Kundenszenarien Vorsicht. Weitere Informationen finden Sie unter [MMOS image-Definition](mmos-image-definition.md).</p></td>
<td><p>CustomerCareOEMInput.xml</p></td>
</tr>
</tbody>
</table>

 

### <a name="oeminput-file-example"></a>Beispiel für die Datei OEMInput

Das folgende Beispiel zeigt den Inhalt einer Beispieldatei ProductionOEMInput.xml.

``` syntax
<?xml version="1.0" encoding="utf-8" ?> 
<OEMInput xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns="http://schemas.microsoft.com/embedded/2004/10/ImageUpdate">
<Description>Test FFU generation for {SOC TYPE} with build number XXXXX</Description> 
<SOC>{PROCESSOR_NAME}</SOC> 
<SV>{SV_NAME}</SV> 
<Device>{DEVICE_NAME}</Device> 
<ReleaseType>Test</ReleaseType> 
<BuildType>fre</BuildType> 
<SupportedLanguages>
  <UserInterface>
      <Language>en-US</Language> 
  </UserInterface>
  <Keyboard>
     <Language>en-US</Language> 
  </Keyboard>
  <Speech>
    <Language>en-US</Language> 
  </Speech>
</SupportedLanguages>
<BootUILanguage>en-US</BootUILanguage> 
<BootLocale>en-US</BootLocale> 
<Resolutions>
  <Resolution>480x800</Resolution> 
</Resolutions>
<AdditionalFMs>
  <AdditionalFM>%WPDKCONTENTROOT%\FMFiles\MSOptionalFeatures.xml</AdditionalFM> 
  <!-- Add OEM FM files here -->
</AdditionalFMs>
<Features>
  <Microsoft>
    <Feature>CODEINTEGRITY_TEST</Feature> 
    <Feature>PRODUCTION_CORE</Feature> 
    <Feature>BOOTKEYACTIONS_RETAIL</Feature> 
  </Microsoft>
<!-- Insert OEM\SOC features here
  <OEM>
    <Feature>xxx</Feature>
  </OEM>
-->
</Features>
</OEMInput>
```

### <a name="a-href-idspecifyingpackagestoincludeaspecifying-packages-to-include-in-images-by-using-feature-manifest-files"></a><a href="" id="specifyingpackagestoinclude"></a>Angeben von Pakete zum Einschließen in Bildern mithilfe des Feature-Manifestdateien

Feature-Manifestdateien Geben Sie eine Reihe von Features, Pakete und apps, die verfügbar, beim Erstellen von Bildern sind. Die Datei OEMInput.xml markiert später die gewünschten Features aus innerhalb dieser Funktionsmanifeste in das Bild enthalten sein.

Neben eine Kerngruppe von Microsoft-Pakete, die jedes Bild hinzugefügt werden, sind zusätzliche Pakete, die nur für bestimmte Arten von Bildern hinzugefügt werden. Ein Testbild umfasst beispielsweise eine andere Menge von Microsoft-Pakete als eine Produktion Bild.

Der Satz von Paketen, die bestimmte Arten von Bilder enthalten sind wird mithilfe der Feature-Manifestdateien gesteuert. Feature-Manifests bieten eine umfassende Infrastruktur für das Hinzufügen von Gruppen von optionale Pakete auf verschiedene Arten von Bild erstellt. Das WDK enthält FeatureManifest namens MSOptionalFeaturesFM.xml und OEMs können auch ihre eigenen erstellen. Feature-Manifests sind im **AdditionalFMs** -Element der OEMInput XML-Datei verwiesen. Weitere Informationen über den Inhalt eines Feature-Manifests finden Sie unter [Feature Dateiinhalt manifest](feature-manifest-file-contents.md).

Wenn die OEMInput-XML-Datei ein FeatureManifest verweist, stehen mehrere Möglichkeiten, dass zusätzliche optionale Pakete enthalten sind im Bild:

-   Pakete unter dem **BasePackages** -Element in der Feature-Manifestdatei aufgeführt werden automatisch in das Bild aufgenommen.

-   Andere Pakete, die in der Feature-Manifestdatei unter Elemente aufgelistet, wie **ReleasePackages** und **DeviceSpecificPackages** enthalten sind, wenn die Bild-Definition durch die Elemente in der Feature-Manifestdatei angegebenen Parameter übereinstimmt. Beispielsweise ist die Feature-Manifestdatei ein Paket unter dem Element **ReleasePackages** aufgeführt, in dem **Test**der Versionstyp ist, ist das Paket enthalten nur, wenn die Datei OEMInput konfiguriert ist, um ein Testbild zu generieren.

-   Alle optionalen Features in der Feature-Manifestdatei definierten können in den Microsoft- **Funktionen** oder OEM-Elementen in der Datei OEMInput zusätzliche optionale Pakete hinzufügen verwiesen werden. Ein Feature ist eine Zeichenfolge, die einen oder mehrere optionale Pakete identifiziert, die in einem Bild enthalten sein können. In der Regel identifiziert ein Feature eine Reihe von Paketen, die einem bestimmten Bereich Komponente oder ein Feature zugeordnet sind. Weitere Informationen zu optional für die Verwendung in OEMInput-Dateien von Microsoft bereitgestellten Features finden Sie unter optionale Features zum Erstellen von Bildern.

-   Je nach, die mit dem Bild arbeiten kann es in der entsprechenden auszuschließende Vorabversion Features mithilfe des **ExcludePrereleaseFeatures** -Elements sein. Weitere Informationen finden Sie unter [OEMInput Dateiinhalten](oeminput-file-contents.md).

### <a name="a-href-idconfiguringtheoeminputfileaconfiguring-the-oeminput-file-to-integrate-feature-changes-from-the-microsoft-samples"></a><a href="" id="configuringtheoeminputfile"></a>Konfigurieren der OEMInput-Datei zum Integrieren von Änderungen bei Features aus der Microsoft-Beispiele

In jeder Version MobileOS möglicherweise aus der vorherigen Version von Microsoft bereitgestellten OEMInput Beispiele ändern. Beispielsweise Microsoft definierten Features zu einer Stichprobe, neue Betriebssystemkomponenten zu integrieren, die verfügbar sind, hinzugefügt werden, oder Microsoft definierten Features möglicherweise aus einer Stichprobe entfernt werden, wenn sie für einen bestimmten Bildtyp nicht mehr unterstützt werden. Um sicherzustellen, dass die richtigen Bilder für jede Version MobileOS OEMs erstellen, empfiehlt Microsoft OEMs des folgenden Vorgangs erfüllen.

1.  Struktur der **AdditionalFMs** und das Feature bezogene Elemente in der Datei OEMInput wie im folgenden Beispiel dargestellt. Enthalten Sie in jedem Abschnitt die Feature-Manifests und zunächst von der Microsoft-Beispiel angegebenen Funktionen, und fügen Sie dann die Manifeste OEM-spezifischen Features und Funktionen. Verwenden Sie Kommentare, jede Gruppe von Features und Features Manifeste deutlich zu trennen und klar, warum die einzelnen OEM-spezifischen Features in der Datei enthalten ist.

    Wenn Sie den Inhalt der **AdditionalFMs** und **Features der** Elemente in der Datei OEMInput von der Microsoft-Beispiele abweichen, enthalten Sie ausführliche Kommentare, in denen erläutert, warum die Änderungen vorgenommen wurden. Wenn alle Änderungen als vorübergehende Lösung für ein Problem eingeführt werden, sollte die Zwischenlösung erläutert, dass, die mit Engineering, dass die Datei in Zukunft ermitteln kann, ob die Änderung erhalten oder in der Microsoft-Beispiel zurückgesetzt, wenn der OEM einer neueren BSP oder Kits integriert.

    ``` syntax
    <!-- From Microsoft sample OEMInput.xml file -->
    <AdditionalFMs>
      <AdditionalFM>%WDKCONTENTROOT%\FMFiles\MSOptionalFeatures.xml</AdditionalFM> 
        <!-- Add OEM FM files here -->
    </AdditionalFMs>

    <Features>
       <Microsoft>
        <!-- Features from Microsoft OEMInput sample -->
        <!-- Additional OEM-selected features defined by Microsoft
             Include detailed comments about why each feature was chosen for this image -->
       </Microsoft>
       <OEM>
        <!-- Additional OEM-selected features defined by the OEM
             Include detailed comments about why each feature was chosen for this image  -->
       </OEM>
    </Features>
    ```

2.  Wenn der OEM integriert eine neue WDK und MobileOS freigeben, Vergleichen der **Features** Elemente in der Stichprobe OEMInput aus der neuesten Version und den gleichen Elementen in der Datei OEMInput vom OEM.

3.  Identifizieren Sie alle Änderungen auf die Microsoft-spezifische Features im aktuellen Beispiel, und die Änderungen in der **Features** -Element in der Datei OEMInput vom OEM-port.

## <a name="a-href-idusingimggenausing-imggencmd-to-generate-the-image"></a><a href="" id="usingimggen"></a>Verwenden von ImgGen.cmd zum Generieren des Bilds


ImgGen.cmd ist eine Befehlsdatei, die das imaging-Tool (ImageApp.exe) ausgeführt wird mit den entsprechenden Parametern Schwelle FFU erstellen. ImgGen.cmd wird auch eine Dienstprogramm Anwendung DeviceNodeCleanup, nach jeder Ausführung des ImageApp.exe ausgeführt. DeviceNodeCleanup ausgeführt wird sichergestellt, dass die Registrierung auf dem Entwicklungscomputer clean bleibt und Startzeit nicht erhöht. ImgGen.cmd und anderen zugehörigen Komponenten befinden sich in WPDKCONTENTROOT %\\Tools\\Bin\\i386.

ImgGen.cmd verwenden, um ein Bild zu generieren:

1.  Konfigurieren Sie Ihrem Entwicklungscomputer wie folgt:

    -   Öffnen Sie ein **Entwickler für VS2013** Eingabeaufforderungsfenster (Wenn Sie Visual Studio 2013 installiert haben) oder **ein Eingabeaufforderungsfenster** (Wenn Sie Visual Studio 2013 nicht installiert haben) als Administrator.

    -   Vergewissern Sie sich, dass die TEMP-Umgebungsvariable auf ein Verzeichnis verweist, ist nicht komprimiert oder mit der Funktionalität (Encrypting File System, EFS) verschlüsselt. Wenn das Verzeichnis, das auf die TEMP-Umgebungsvariable verweist diesen Anforderungen nicht erfüllt und Sie nicht die Variable oder das Verzeichniseigenschaften ändern möchten, können Sie auch eine BINÄRE erstellen\_ROOT-Umgebungsvariable und legen Sie es auf ein vorhandenes Verzeichnis, die auch diese Anforderungen erfüllt. Wenn keines dieser Speicherorte vorhanden, oder vorhanden, jedoch werden komprimiert oder verschlüsselt, das Bild kann nicht generiert werden und das Tool ImageApp.exe wird ein Fehler zurückgegeben.

    -   Wenn Sie Windows 8.1 ausgeführt werden, führen Sie die zusätzlichen Schritte, um die Größe des USN Journal Registrierung auf 1 Mb Build PC festzulegen.

        1.  Ändern Sie den USN Mindestgröße Registrierungsschlüssel, indem Sie ein Administrator-Eingabeaufforderung den folgenden Befehl ausführen:

            ``` syntax
            reg add HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\FileSystem  /v NtfsAllowUsnMinSize1Mb  /t REG_DWORD  /d 1
            ```

        2.  Starten Sie vor dem Erstellen eines Abbilds den Computer neu.

2.  Führen Sie in das Eingabeaufforderungsfenster ImgGen.cmd mithilfe der folgenden Syntax. Finden Sie im folgenden Abschnitt für Weitere Informationen zu den Parametern aus.

    ``` syntax
    ImgGen.cmd OutputFile OEMInputXML MSPackageRoot OEMCustomizationXML OEMCustomizationVer
    ```

### <a name="command-line-syntax-for-imggencmd"></a>Die Befehlszeilensyntax für ImgGen.cmd

In der folgenden Tabelle werden die Befehlszeilenparameter für ImgGen.cmd beschrieben.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Argument</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>Ausgabedatei</em></p></td>
<td><p>Der Name der zu erstellenden FFU-Datei. Wenn Sie keinen Pfad angeben, wird die Datei FFU im aktuellen Verzeichnis erstellt werden. Wenn Sie einen Pfad angeben, muss der angegebene Pfad bereits vorhanden sein. FFU Dateien verwenden Sie die Erweiterung Ffu.</p></td>
</tr>
<tr class="even">
<td><p><em>OEMInputXML</em></p></td>
<td><p>Der Name der OEMInput Xml-Datei, die das Bild zu erstellenden definiert. Wenn diese Datei nicht im aktuellen Verzeichnis ist, müssen Sie den Pfad zur Datei einbeziehen.</p></td>
</tr>
<tr class="odd">
<td><p><em>MSPackageRoot</em></p></td>
<td><p>Der Pfad zum Stammverzeichnis, das die Microsoft-Pakete enthält. Standardmäßig ist dies das Verzeichnis % ProgramFiles(x86) %\Windows Kits\10\MSPackages (oder den entsprechenden Pfad unter ProgramFiles% auf Computern mit einer 32-Bit-Version von Windows).</p></td>
</tr>
<tr class="even">
<td><p><em>OEMCustomizationXML</em></p></td>
<td><p>Der Pfad zu der OEM XML-Anpassungsdatei. Weitere Informationen zur Anpassung von Antwortdateien finden Sie unter <a href="https://msdn.microsoft.com/library/windows/hardware/dn75745">Antwort-Anpassungsdatei</a>
</tr>
<tr class="odd">
<td><p><em>OEMCustomizationVer</em></p></td>
<td><p>Die Versionsnummer, die für das Paket der generierten OEM-Anpassung verwendet werden.</p></td>
</tr>
</tbody>
</table>

 

### <a name="usage-samples"></a>Beispiele: Einsatz

Das folgende Beispiel zeigt die grundlegende Verwendung von ImgGen.cmd.

``` syntax
ImgGen Flash.ffu OEMInput.xml "%WPDKCONTENTROOT%\MSPackages" OEMCustomization.XML 8.1.0.1
```

### <a name="output-files"></a>Ausgabedateien

Wenn ein Bild in den Ordner in erfolgreich erstellt wird die *FFU\_Datei* Befehlszeilenargument, imaging Tools die folgenden in den Ordner der Ausgabedatei FFU Dateien Kopie:

-   &lt;*FFUName*&gt;. ImageApp.log: Diese Datei enthält alle Protokollinformationen darum, das Bild. In dieser Datei als auch im Konsolenfenster werden Fehler gemeldet.

-   &lt;*FFUName*&gt;. UpdateOutput.xml: Diese Datei beschreibt jedes der Pakete, die auf das Bild angewendet.

-   &lt;*FFUName*&gt;. UpdateHistory.xml: Diese Datei enthält eine Liste aller Update und imaging Ereignisse, die auf das Bild aufgetreten sind.

-   &lt;*FFUName*&gt;. UpdateInput.xml: Diese Datei enthält alle Pakete, die im Bild enthalten sind.

-   &lt;FFUName&gt;. PackageList.xml: Dies ist eine Liste der Paketdateien, die im Bild enthalten sind.

-   &lt;FFUName&gt;.cat: Dies ist eine Code signing Katalog, das zum Signieren des Abbilds verwendet werden kann. Weitere Informationen finden Sie unter [Signieren einer vollständigen flash Updateabbild (FFU)](sign-a-full-flash-update--ffu--image.md).

Wenn eine Antwort Anpassungsdatei angegeben wird, wird diese Datei generiert:

-   &lt;Besitzer&gt;. &lt;DeviceName&gt;. Anpassungen. &lt;Partition&gt;.spkg

Wenn keines der Anpassungen statisch Applications enthalten, wird die folgende Datei generiert.

-   &lt;Besitzer&gt;. &lt;DeviceName&gt;. CustomizationsApps.spkg

## <a name="generating-customization-packages-without-creating-an-image"></a>Generieren von Anpassung Paketen ohne erstellen ein Bild


Um eine Anpassungsdatei Antwort verarbeiten ohne Erstellung eines Bilds, verwenden Sie **CustomizationGen.cmd**. CustomizationGen.cmd gilt aller die Anpassungsregeln und die Anpassung Pakete erstellt. Es werden der letzte Schritt erstellen Sie das Bild Ffu übersprungen. Die Syntax ähnelt ImgGen.cmd.

Angenommen, um eine Antwortdatei verarbeiten und soeben erstellt haben Anpassung Pakete, verwenden Sie diesen Befehl an.

``` syntax
CustomizationGen.cmd C:\OEMCustomization OEMInput.xml "%WPDKCONTENTROOT%\MSPackages" OEMCustomization.XML 8.0.0.1
```

### <a name="command-line-syntax-for-customizationgencmd"></a>Die Befehlszeilensyntax für CustomizationGen.cmd

In der folgenden Tabelle werden die Befehlszeilenparameter für CustomizationGen.cmd beschrieben. Alle Argumente sind erforderlich.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Argument</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>OutputDirectory</em></p></td>
<td><p>Der Pfad in das Ausgabeverzeichnis für die OEM-Anpassung Pakete, die erstellt wird.</p></td>
</tr>
<tr class="even">
<td><p><em>OEMInputXML</em></p></td>
<td><p>Der Name der OEMInput Xml-Datei, die das Bild zu erstellenden definiert. Wenn diese Datei nicht im aktuellen Verzeichnis ist, müssen Sie den Pfad zur Datei einbeziehen.</p></td>
</tr>
<tr class="odd">
<td><p><em>MSPackageRoot</em></p></td>
<td><p>Der Pfad zum Stammverzeichnis, das die Microsoft-Pakete enthält. Standardmäßig ist dies das Verzeichnis % ProgramFiles(x86) %\Windows Kits\10\MSPackages (oder den entsprechenden Pfad unter ProgramFiles% auf Computern mit einer 32-Bit-Version von Windows).</p></td>
</tr>
<tr class="even">
<td><p><em>OEMCustomizationXML</em></p></td>
<td><p>Der Pfad zu der OEM XML-Anpassungsdatei.</p></td>
</tr>
<tr class="odd">
<td><p><em>OEMCustomizationVer</em></p></td>
<td><p>Dies ist die Versionsnummer, die für das generierte OEM Anpassung Paket verwendet werden.</p></td>
</tr>
</tbody>
</table>

 

## <a name="large-scale-image-generation-recommendations"></a>Im großen Maßstab Image Generation Empfehlungen


Wenn auf einer Arbeitsstation wiederholt Bilder generiert werden, ist es möglich, dass virtuelle Festplatte (VHD) Manipulation Fehler von Zeit zu Zeit auftreten können. Wenn diese Fehler auftreten, können Sie den Bild-Generierungsprozess erneut ausführen. Von ImageApp sollte automatisch alle temporäre Dateien bereinigt werden. Dieser Abschnitt bietet Hilfestellung für die Konfiguration von PCs, die generiert Bilder in einer großen automatische Generierung-Umgebung um die Anzahl der Fehler zu minimieren, die auftreten können.

Wenn Sie eine große Menge von Bilder generiert werden soll, sollten Sie folgende Aspekte:

-   Entfernen oder Deaktivieren der Antivirensoftware auf der Generation Bild PC. Das Vorhandensein von Antivirussoftware und in bestimmten Dateisystemfilter häufig verwendet, um die Aktivität, überwachen kann eine Haupt-auf das Bild Generierungsprozess auswirken. Mindestens sollte Virenscan für Eingabe- und Ausgabeparameter Verzeichnisse und auf allen Prozessen beteiligt der Build deaktiviert werden, obwohl dies nicht in der Regel den System Dateifilter von Interesse deaktiviert wird. Einige Anbieter von Antivirussoftware bieten möglicherweise Einstellungen zum Zulassen von Scan-Aktivitäten verzögert oder möglicherweise fördert die Auswirkung auf die Bild-Generierungsprozess geplant werden. Wenn zusätzliche Sicherheitsmaßnahmen direkt auf das System gegen Viren und andere Software Risiken, isoliert sind, entfernen Sie oder deaktivieren Sie die Virus-Software auf das Bild Generation PC. Vorübergehend entfernen der Virussoftware kann isolieren die Auswirkung auf den Generierungsprozess Bild zu ermitteln, ob weitere Untersuchung erforderlich ist.

-   Windows Server 2012 wird in den Microsoft-Übungseinheiten verwendet, und es wird empfohlen. Der Server sollte für maximale Datei-e/a-Leistung konfiguriert werden.

-   Image-Erstellungsprozess sollten nicht auf virtuellen Computern (VMs), sondern auf physischen Computern werden stattdessen ausgeführt.

-   Alle anderen Dienste (wie Drucken oder HTTP-Dienste), die auf das Dateisystem nicht miteinander verknüpft sind, sollte auf dem Server deaktiviert werden.

-   System-Aktivität Spuren können möglicherweise Prozesse auf Buildcomputern identifizieren, die bereitgestellten VHDs interagiert werden. Alle Interaktionen, die imaging-Tools nicht initiiert werden sollten, wenn möglich, potenziell Deaktivieren von Diensten, die auf dem Datenträger Mount ergreifen vermieden werden.

-   Die Ausgabe Laufwerke, auf dem PC sollte Write Cache Puffer geleert deaktiviert. Risiko in mit dieser Einstellung auf einem Dateiserver vorhanden ist, aber mit Bild Generation, diese Einstellung sind zulässig, wie die imaging Daten neu erstellt werden, wenn ein Stromausfall auftritt. Wenn andere Daten auf dem Server neu erstellt werden können, verwenden Sie diese Einstellung mit Vorsicht, da Daten können beschädigt werden.

## <a name="related-topics"></a>Verwandte Themen


[Erstellen und mobilen blinkende](building-and-flashing-images.md)

[Inhalt der Datei OEMInput](oeminput-file-contents.md)

[Melden Sie sich eine vollständige flash aktualisierungsabbild (FFU)](sign-a-full-flash-update--ffu--image.md)

 

 

[Senden Sie Kommentare zu diesem Thema an Microsoft] (mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback%20%5Bp_phFlashing\p_phFlashing%5D:%20Build%20a%20mobile%20image%20using%20ImgGen.cmd%20%20RELEASE:%20%2810/4/2016%29&body=%0A%0APRIVACY%20STATEMENT%0A%0AWe%20use%20your%20feedback%20to%20improve%20the%20documentation.%20We%20don't%20use%20your%20email%20address%20for%20any%20other%20purpose,%20and%20we'll%20remove%20your%20email%20address%20from%20our%20system%20after%20the%20issue%20that%20you're%20reporting%20is%20fixed.%20While%20we're%20working%20to%20fix%20this%20issue,%20we%20might%20send%20you%20an%20email%20message%20to%20ask%20for%20more%20info.%20Later,%20we%20might%20also%20send%20you%20an%20email%20message%20to%20let%20you%20know%20that%20we've%20addressed%20your%20feedback.%0A%0AFor%20more%20info%20about%20Microsoft's%20privacy%20policy,%20see%20http://privacy.microsoft.com/default.aspx. "Senden Sie Kommentare zu diesem Thema an Microsoft")





