---
author: kpacquer
Description: "Dieses Handbuch führt Sie durch Erstellen von Bildern für Windows 10 IoT Core (IoT Core), die für den Einzelhandel Geräte aktualisiert und verwaltet nach Ihren Kunden übermittelt werden können."
ms.assetid: 2b208536-20fc-42da-abf3-39bfb141276d
MSHAttr: PreferredLib:/library
title: IoT Core Fertigung guide
ms.openlocfilehash: b2616268ed1e9a4fb89c77d186e92776df373b43
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="iot-core-manufacturing-guide"></a>IoT Core Fertigung guide

Planen Sie Geräte, auf denen Windows 10 IoT Core mass-producing? Verwenden Sie die [Windows ADK IoT Core Add-ons](iot-core-adk-addons.md) Bilder erstellen, die Sie schnell auf neue Geräte flash können. 

Sie können **Bilder zu testen**, erstellen, die Tools für schnell zugreifen und diese Geräte ändern enthalten. Gut werden Test Bilder:
-  Entwickler, Hardwareherstellern und Hersteller (OEMs), die versuchen, neue Gerätedesigns.
-  Hobbyprogrammierer und Organisationen, die Geräte im Netzwerk nicht vernetzte oder gesteuerte Umgebungen ausgeführt werden sollen erstellen.

Sie können **Retail Bilder**, Erstellen sicherer für öffentliche oder Unternehmensnetzwerk kann beim weiterhin Updates empfangen hergestellt werden.

Sie können die Anpassungen, einschließlich apps, Einstellungen, Hardwarekonfigurationen und Board Support Packages (BSPs) hinzufügen.

OEM-Schreibweise von Bildern benötigen Sie die Anpassungen in Paketdateien (CAB) einbinden. Pakete ermöglichen OEMs, ODMs, Entwickler und Microsoft arbeiten zusammen, die Sicherheit und Feature-Updates auf Geräte bieten, ohne auf die Arbeit der anderen stomping erleichtern.


## <a name="span-idscenariosspanspan-idscenariosspanspan-idscenariosspanscenarios"></a><span id="Scenarios"></span><span id="scenarios"></span><span id="SCENARIOS"></span>Szenarien
-   [Abrufen von Tools zum Anpassen von Windows IoT Core benötigt](set-up-your-pc-to-customize-iot-core.md)
-   [Übung 1a: Erstellen eines grundlegenden Abbilds](create-a-basic-image.md)
-   [Übung 1 b: hinzufügen eine app für das Abbild](deploy-your-app-with-a-standard-board.md)
-   [Übung 1c: Hinzufügen einer Datei und eine Einstellung in der Registrierung zu einem Bild](add-a-registry-setting-to-an-image.md)
-   [Übung 1 t: Hinzufügen von Netzwerk- und anderen Paket bereitstellungseinstellungen zu einem Bild](add-a-provisioning-package-to-an-image.md)
-   [Übung 1e: Hinzufügen eines Treibers zu einem Bild](add-a-driver-to-an-image.md)
-   [Übung 1f: Erstellen eines Abbilds Einzelhandel](build-retail-image.md)
-   [Übung 2: Erstellen Ihrer eigenen Board Support-Paket](create-a-new-bsp.md)
-   [Übung 3: Aktualisieren Sie Ihre apps](../../service/iot/updating-iot-core-apps.md)

[(Der vorherigen Version dieses Handbuchs): IoT Core Bereitstellung und Imaging](iot-core-deployment-and-imaging.md)
## <a name="span-idconceptsspanspan-idconceptsspanspan-idconceptsspanconcepts"></a><span id="Concepts"></span><span id="concepts"></span><span id="CONCEPTS"></span>Konzepte

Die exemplarischen Vorgehensweise können als Leitfaden Sie um Ihre Test und die Verkaufsversion Bilder zu erstellen. Allgemein:

1.  Testen Sie Ihre Anpassungen, einschließlich apps, Einstellungen, Treiber und BSPs, um sicherzustellen, dass sie funktionieren.
2.  Installieren Sie Zertifikate auf Ihrem PC und Packen Sie die Anpassungen in CAB-Dateien.
2.  Erstellen Sie ein Test-Image, Anpassungen zusammen mit der IoT Kernpaket und alle Updates vom Hardwarehersteller enthält.
3.  Das Bild zu einem Gerät Flash und zu testen. Verwenden Sie die Testtools integriert die Test-Bilder, um alle neuen Probleme zu behandeln.
4.  Wenn es funktioniert, melden Sie Ihre Anpassungen und erneutes Packen sie in neue CAB-Dateien.
5.  Erstellen Sie ein Bild Retail mit Ihren signierten Dateien und verwenden Sie, um neue Geräte herstellen.

![IOT Core Image-Erstellungsprozess](images/oemworkflow.png)

### <a name="span-idpackagesspanspan-idpackagesspanspan-idpackagesspanpackages"></a><span id="Packages"></span><span id="packages"></span><span id="PACKAGES"></span>Pakete

Pakete sind die logische Bausteine IoT Core. Sie enthalten alle Dateien, Bibliotheken, registrierungseinstellungen, ausführbare Dateien, und Daten auf dem Gerät. Von Systemdateien Treiber muss jede Komponente in einem Paket enthalten sein. Diese modulare Architektur für eine genauere Steuerung des Updates ermöglicht: ein Paket ist die kleinste gewartet werden Einheit auf dem Gerät.

Jedes Paket enthält:
-   Der Inhalt des Pakets, wie etwa eine binäre signierten Treiber oder einer signierten Appx Binär.
-   Eine Paketdefinition (. pkg.xml) Datei gibt den Inhalt des Pakets und, wo das endgültige Bild platziert werden soll. Finden Sie unter % SRC\_DIR %\\Pakete\\ verschiedene Beispiele für Paketdateien Verzeichnis.
-   Eine Signatur. Dies kann ein Zertifikat Test- oder Retail sein.

Die `pkggen` Tool kombiniert diese Elemente zu signierte Pakete. Unsere Beispiele enthalten Skripts: `createpkg`, `createprovpkg` und `createupdatepkgs`, welcher Anruf Pkggen-Pakete für unsere Treibern, apps und Einstellungen zu erstellen.

Der Vorgang ist ähnlich, die von Windows Mobile, 10 verwendet. Weitere Informationen zum Erstellen von Lösungspaketen finden Sie unter [Erstellen von mobilen Pakete](https://msdn.microsoft.com/library/windows/hardware/dn756642).

### <a name="span-idfeaturemanifestsfmsspanspan-idfeaturemanifestsfmsspanspan-idfeaturemanifestsfmsspanfeature-manifests-fms"></a><span id="Feature_manifests__FMs_"></span><span id="feature_manifests__fms_"></span><span id="FEATURE_MANIFESTS__FMS_"></span>Feature-Manifeste (FMs)

Nachdem Sie alles in Pakete versetzt haben, verwenden Sie FM-Dateien zur Liste der von Paketen in das endgültige Image angehören.

Sie können beliebig viele FMs in ein Bild wie gewünscht. In diesem Handbuch finden Sie es in der folgenden FMs:

-   **OEMFM.xml** enthält Features, die auf einem Gerät, wie die app und einer Bereitstellung Paket OEM hinzugefügt werden kann.
-   **BSPFM.xml** enthält Features, die einem Hardwarehersteller verwenden könnten, um eine Pinnwand zu definieren. Beispielsweise OEM\_RPi2FM.xml enthält alle Features für 2 Pi Brombeere verwendet wird.
-   **ProdFM.xml** enthält Features, die IoT Core bilden. ProdFM bezieht sich auf eine vollständig signiert Version des Betriebssystems.

Der Prozess ähnelt, wird von Windows 10 Mobile. Finden Sie weitere Informationen finden Sie unter [Feature Dateiinhalten manifest](https://msdn.microsoft.com/library/windows/hardware/dn756745).

Sie können die Features hinzufügen, indem Sie diese Tags aufgelistet:

-   &lt;BasePackages&gt;: Pakete, die Sie stets in Bildern, beispielsweise enthalten, Ihre Basis-app.
-   &lt;Features&gt;\\&lt;OEM&gt;: andere einzelne Pakete, die speziell für ein bestimmtes Produktentwurf sein könnten.

### <a name="span-idcreatingtheimageimggenandtheimageconfigurationfileoeminputxmlspanspan-idcreatingtheimageimggenandtheimageconfigurationfileoeminputxmlspanspan-idcreatingtheimageimggenandtheimageconfigurationfileoeminputxmlspancreating-the-image-imggen-and-the-image-configuration-file-oeminputxml"></a><span id="Creating_the_image__ImgGen_and_the_image_configuration_file__OEMInput.xml_"></span><span id="creating_the_image__imggen_and_the_image_configuration_file__oeminput.xml_"></span><span id="CREATING_THE_IMAGE__IMGGEN_AND_THE_IMAGE_CONFIGURATION_FILE__OEMINPUT.XML_"></span>Erstellen des Abbilds: ImgGen und die Konfiguration der Bild-Datei (OEMInput.xml)

Wenn das endgültige Bild erstellen möchten, verwenden Sie die `imggen` Tool mit einer Konfiguration Bilddatei **OEMInput.xml-Datei**.

Dies sind dieselben Tools zum Erstellen von Windows 10 Mobile Bilder verwendet. Finden Sie weitere Informationen finden Sie unter [OEMInput Dateiinhalten](https://msdn.microsoft.com/library/windows/hardware/dn756778).

Die Bild-Konfigurationsdatei enthält:

-   Die Feature-Manifeste (FMs) und die Pakete, die Sie jeweils einzeln installieren möchten.
-   Ein **SoC** Chip-Bezeichner, der verwendet wird, können Sie die Partitionen Gerät einrichten. Dieser Wert ist erforderlich, selbst wenn Sie eine der aufgeführten Geräte nicht verwenden. Starten Sie den Wert für die Hardware, die das Gerät am ehesten entspricht:

    **RPi2**: Brombeere Pi 2 oder Brombeere Pi 3 (ARM)

    **MBM**: Intel Minnowboard Max (x86)

    **DB**: Qualcomm DragonBoard (ARM32)

-   Die ReleaseType ( **Produktion** oder **Test**).

    **Verkaufsversionen**: Es wird empfohlen, einem frühen Zeitpunkt erstellen Retail Bilder in Ihren Entwicklungsprozess, um sicherzustellen, dass alles funktioniert, wenn Sie bereit sind, liefern.

    Diese Builds enthalten alle Security Features aktiviert.

    Für die Verwendung dieses Buildtyps müssen alle des Codes signiert werden mithilfe von Code der Verkaufsversion (nicht-Test) Signieren von Zertifikaten.

    Ein Beispiel finden Sie unter % SRC\_DIR %\\Produkte\\SampleA\\RetailOEMInput.xml.

    **Test erstellt**: Verwenden Sie diese, um neue Versionen der apps und Treiber erstellt, indem Sie und Ihre Hardware Hersteller Partner zu testen.

    Diese Builds verfügen über einige Features deaktiviert, wodurch Test signiert oder Produktion signierte Pakete verwenden.

    Diese Builds enthalten außerdem Entwicklertools wie Debug Transport, SSH und PowerShell, die Sie verwenden können, Problembehandlung unterstützen soll.

    Ein Beispiel finden Sie unter % SRC\_DIR %\\Produkte\\SampleA\\TestOEMInput.xml.

    <table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th align="left"></th>
    <th align="left">Verkaufsversionen</th>
    <th align="left">Testen von builds</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td align="left">Bildtyp-Version</td>
    <td align="left">ReleaseType: <strong>Produktion</strong></td>
    <td align="left">ReleaseType: <strong>Test</strong></td>
    </tr>
    <tr class="even">
    <td align="left">Pakettyp Version</td>
    <td align="left">Nur Produktionstyp-Pakete werden unterstützt.</td>
    <td align="left">Produktion-Typ oder Testtyp werden unterstützt.</td>
    </tr>
    <tr class="odd">
    <td align="left">Test-signierte Pakete</td>
    <td align="left">Nicht unterstützt</td>
    <td align="left">Unterstützt
    <p>IOT_ENABLE_TESTSIGNING Feature muss eingeschlossen werden.</p></td>
    </tr>
    <tr class="even">
    <td align="left">Überprüfung der Integrität Code</td>
    <td align="left">Unterstützt. Diese Option ist standardmäßig aktiviert.</td>
    <td align="left">Nicht unterstützt
    <p>IOT_DISABLE_UMCI Feature muss eingeschlossen werden.</p></td>
    </tr>
    </tbody>
    </table>

### <a name="span-idboardsupportpackagesspanspan-idboardsupportpackagesspanspan-idboardsupportpackagesspanboard-support-packages-bsps"></a><span id="Board_Support_Packages"></span><span id="board_support_packages"></span><span id="BOARD_SUPPORT_PACKAGES"></span>Board Support Packages (BSPs)
Board Support Packages enthalten eine Reihe von Software, Treibern und Boot-Konfigurationen für einen bestimmten Pinnwand, in der Regel von einer Pinnwand Hersteller bereitgestellt wird. Der Pinnwand Hersteller vorsehen in regelmäßigen Abständen Updates für die Pinnwand, die Geräte erhalten und anwenden können. 

## <a name="span-idokletstryitspanspan-idokletstryitspanspan-idokletstryitspanok-lets-try-it"></a><span id="OK__let_s_try_it_"></span><span id="ok__let_s_try_it_"></span><span id="OK__LET_S_TRY_IT_"></span>OK ist, versuchen Sie es!

Beginnen Sie hier: [Abrufen von Tools zum Anpassen von Windows IoT Core benötigt](set-up-your-pc-to-customize-iot-core.md).

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen

[Informieren Sie sich über Windows 10 IoT Core](https://developer.microsoft.com/windows/iot/iotcore)

[IoT Core-Entwicklerressourcen](https://developer.microsoft.com/windows/iot)

[Was ist in die Windows ADK IoT Core Add-ons](iot-core-adk-addons.md)

[IoT Core Featureliste](iot-core-feature-list.md)

[Command-Line Options IoT Core Add-ons](iot-core-adk-addons-command-line-options.md)

 

 



