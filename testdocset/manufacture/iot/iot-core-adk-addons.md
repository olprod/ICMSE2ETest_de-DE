---
author: kpacquer
Description: "Die Windows 10 IoT Core ADK Add-Ons umfassen die Tools zum Anpassen und erstellen Sie neue Bilder für Ihre Geräte mit der apps, Board Support Packages (BSPs), Treibern, und Windows-Features, die Sie auswählen und eine Beispielstruktur, die Sie verwenden können, um schnell neue Bilder zu erstellen."
ms.assetid: 26cfbad0-9528-4f89-a174-f198ece325d4
MSHAttr: PreferredLib:/library
title: 'Windows ADK IoT Core-Add-Ons: Inhalt'
ms.openlocfilehash: e43176dccf0873db9c5a3e2e80fa6bb7df3a516c
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="windows-adk-iot-core-add-ons-contents"></a>Windows ADK IoT Core-Add-Ons: Inhalt

Die [Windows 10 IoT Core ADK Add-Ons](http://go.microsoft.com/fwlink/?LinkId=735028) umfassen die OEM-spezifische Tools Bilder für Ihre IoT Core Geräte mit Ihrer apps, Board Support Packages (BSPs), Einstellungen, Treibern und Features erstellen.

[IoT Core Fertigung Guide](iot-core-manufacturing-guide.md) führt Sie durch die Erstellung von Bildern mit diesen Tools.

## <a name="span-idrootfolderspanroot-folder"></a><span id="Root_folder"></span>Stammordner

-   **IoTCoreShell**: Startet den [IoT Core Shell Command-Line](iot-core-adk-addons-command-line-options.md#iotcoreshell.cmd).

-   **README.md**: Versionsinfo, links und Dokumentation

## <a name="span-idbuildspanspan-idbuildspanspan-idbuildspanbuild"></a><span id="Build"></span><span id="build"></span><span id="BUILD"></span>Build
Dies ist das Ausgabeverzeichnis, in dem der Build-Inhalt gespeichert werden. Er beginnt als leer.

## <a name="span-idcommonfilesspanspan-idcommonfilesspanspan-idcommonfilesspancommon-files"></a><span id="Common_files"></span><span id="common_files"></span><span id="COMMON_FILES"></span>Gemeinsame Dateien

Quelldateien für Pakete, die für alle Architekturen sind.

-   **Custom.Cmd**: Paket Einbeziehung der Oemcustomization cmd ein. Dies ist produktspezifische und nimmt die Eingabedatei aus dem Verzeichnis für das Produkt. Dadurch wird auch einen Registrierungseintrag mit den Namen des Produkts.

-   **Device.SystemInformation**: Paket so das Bild der Produktname System und der Name des Herstellers hinzu.

-   **DeviceLayout.GPT4GB**: Paket mit GPT- [Laufwerk/Partition Layout](device-layout.md) für UEFI-basierte Geräte mit 4-GB-Laufwerke.

-   **DeviceLayout.GPT2GB**: Paket mit GPT- [Laufwerk/Partition Layout](device-layout.md) für UEFI-basierte Geräte mit 2 GB Laufwerke.

-   **DeviceLayout.MBR4GB**: Paket mit MBR- [Laufwerk/Partition Layout](device-layout.md) für legacy BIOS-basierte Geräte mit 4-GB-Laufwerke.

-   **DeviceLayout.MBR2GB**: Paket mit MBR- [Laufwerk/Partition Layout](device-layout.md) für legacy BIOS-basierte Geräte mit 2 GB Laufwerke.

-   **ImageSettings.CrashSettings**: Paket mit Einstellungen für das System stürzt ab. Ersetzt das vorherige Paket: Registry.CrashSettings.

-   **ImageSettings.VideoMode**: Paket mit Einstellungen für Spitzen oder headless-Modus.

-   **OemTools.InstallTools**: Paket, das installiert automatisch OEM-apps im Ordner C:\OEMApps gefunden.

-   **Provisioning.Auto**: Paket verwendet, um [eine Bereitstellung Paket zu einem Bild hinzufügen](add-a-provisioning-package-to-an-image.md). Dies ist der bestimmten Produkt und nimmt die Eingabe Ppkg-Datei aus dem Produktverzeichnis.

-   **Provisioning.Manual**: Paket für die manuelle Bereitstellung. Dies hängt Custom.Cmd für die Bereitstellung auslösen.

-   **Registry.Version**: Paket mit Einstellungen in der Registrierung mit Informationen zu Produkt und Version.

-   **Settings.HotKey**: Beispielpaket veranschaulicht das Hinzufügen [eine Einstellung in der Registrierung zu einem Bild](add-a-registry-setting-to-an-image.md). Diese Einstellung ändert die Werte der die linke Taste Windows, Windows-rechts-Taste und die Windows Alt + nach-rechts-Taste, um fungieren als POS1-Taste.

-   **OEMCommonFM.xml**: Feature-Manifests für gängige OEM-Pakete.


## <a name="span-idsourcespanspan-idsourcespanspan-idsourcespansource-source-arm-source-x64-source-x86"></a><span id="Source"></span><span id="source"></span><span id="SOURCE"></span>Source (Quelle-Arm-, X64-Quelle, Quell-X86)
 
Quelldateien für Pakete, die für eine Architektur spezifisch sind.

### <a name="span-idbspspanspan-idbspspanbsp"></a><span id="BSP"></span><span id="bsp"></span>BSP
Quelldateien Sie Board Support Packages (BSPs) erstellen. 

Einige BSPs sind in jedem Ordner als beginnen enthalten. Sie können [Ihre eigenen BSPs erstellen](create-a-new-bsp.md) basierend auf diese Pakete.

### <a name="span-idpackagesspanspan-idpackagesspanspan-idpackagesspanpackages"></a><span id="Packages"></span><span id="packages"></span><span id="PACKAGES"></span>Pakete

-   **Appx.Main**: Beispielpaket Appx Installation, zeigt System- und Info. Sie können [Ihre eigenen app ersetzen](deploy-your-app-with-a-standard-board.md).

-   **Drivers.GPIO**: Beispiel-Paket für einen Treiber.

-   **OEMFM.xml:** Feature-Manifestdatei für OEM-Pakete

-   **versioninfo.txt:** Anzahl der aktuellen Version. Zum [Aktualisieren von apps IoT Core](../../service/iot/updating-iot-core-apps.md)verwendet.

### <a name="span-idproductsspanspan-idproductsspanspan-idproductsspanproducts"></a><span id="Products"></span><span id="products"></span><span id="PRODUCTS"></span>Produkte

Quelldatei für Produktkonfigurationen. Verwenden Sie unsere Beispiele (SampleA, SampleB, SampleC), oder [Erstellen Sie eigene](iot-core-manufacturing-guide.md)an.

### <a name="span-idupdatesspanspan-idupdatesspanspan-idupdatesspanupdates"></a><span id="Updates"></span><span id="updates"></span><span id="UPDATES"></span>Updates

Quelldateien für [app-Pakete Updates](../../service/iot/updating-iot-core-apps.md). Er beginnt mit zwei Beispiele: Update1 und. 2.

-   **UpdateVersions.txt**: Protokoll der Versionsnummern bisher verwendet.

## <a name="span-idtemplatesspanspan-idtemplatesspanspan-idtemplatesspantools"></a><span id="Templates"></span><span id="templates"></span><span id="TEMPLATES"></span>Tools

Enthält Vorlagen, die durch die [IoT Core Add-ons Command-Line Options](iot-core-adk-addons-command-line-options.md) zum Erstellen von neuen Pakete und BSPs verwendet. 

## <a name="span-idtoolsspanspan-idtoolsspanspan-idtoolsspantools"></a><span id="Tools"></span><span id="tools"></span><span id="TOOLS"></span>Tools

Enthält die [Befehlszeilenoptionen IoT Core Add-ons](iot-core-adk-addons-command-line-options.md).

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen

[Leitfäden zum IoT Core manufacturing](iot-core-manufacturing-guide.md)

[IoT Core Featureliste](iot-core-feature-list.md)


 

 



