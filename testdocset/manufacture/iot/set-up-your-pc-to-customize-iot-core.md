---
author: kpacquer
ms.assetid: a6243b16-54fd-4a3d-8901-4b15cebdaf40
MSHAttr: PreferredLib:/library
title: "Abrufen von Tools zum Anpassen von Windows IoT Core benötigt"
ms.openlocfilehash: e5bdd1ed8fb9ce2e5c45100d76adb9378ff6a4c0
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="get-the-tools-needed-to-customize-windows-iot-core"></a>Abrufen von Tools zum Anpassen von Windows IoT Core benötigt


Hier wird die Software, die Sie benötigen, OEM-Bildern mithilfe von Windows 10 IoT Core (IoT Core) ADK Add-Ons erstellen:

## <a name="span-idpcsanddevicesspanspan-idpcsanddevicesspanspan-idpcsanddevicesspanpcs-and-devices"></a><span id="PCs_and_devices"></span><span id="pcs_and_devices"></span><span id="PCS_AND_DEVICES"></span>PCs und Geräte


Sieht aus wie wir auf diese verwiesen wird:

-   **Techniker PC**: Ihre Arbeit PC. Dieser PC sollte mindestens 15 GB freiem Speicherplatz für die Installation der Software und zum Ändern von IoT Core Bilder verfügen.

    Sie sollten Windows 10 oder Windows 8.1 mit den neuesten Updates. Die Mindestanforderung ist Windows 7 Service Pack 1, obwohl das für Aufgaben wie das Bereitstellen zusätzlicher Tools oder problemumgehungen erfordert. ISO-Bilder.

-   **IoT Gerät**: ein Testgerät oder die Pinnwand, die alle Geräte in ein einziges Modell Zeile darstellt.

    Für unsere Beispiele benötigen Sie eine MinnowBoard Max oder Brombeere Pi 2. Weitere Optionen finden Sie unter [Optionen des Geräts](https://developer.microsoft.com/windows/iot/explore/deviceoptions).

-   Ein **HDMI-Kabel**, und einen **Monitor oder TV** mit einem dedizierten HDMI Eingabe. Dies verwenden wir, stellen Sie sicher, dass das Bild geladen wird und unserem Beispiel-apps ausgeführt werden.

## <a name="span-idstoragespanspan-idstoragespanspan-idstoragespanstorage"></a><span id="Storage"></span><span id="storage"></span><span id="STORAGE"></span>Speicher


-   Eine **Micro SD-Karte**. (Beachten Sie, wir gerade diesen für unsere Handbuch verwenden. Sie können die Geräte mit anderen Laufwerken erstellen. Erfahren Sie mehr über vorhandene [unterstützt Storage](https://developer.microsoft.com/windows/iot/docs/hardwarecompatlist#Storage) -Optionen.)

    Wenn Ihre Techniker PC Micro SD-Steckplatz enthält, benötigen Sie möglicherweise auch einen Adapter.

## <a name="span-idsoftwarespanspan-idsoftwarespanspan-idsoftwarespansoftware"></a><span id="Software"></span><span id="software"></span><span id="SOFTWARE"></span>Software

**Installieren Sie die in der folgenden Tools auf Ihrem PC-Techniker**

1.  [Windows Assessment and Deployment Kit (Windows ADK)](http://go.microsoft.com/fwlink/?LinkId=526803) einschließlich mindestens die **Bereitstellungstools** und **Imaging und Konfiguration Designer (ICD)** Features. Verwenden Sie diese Tools zum Erstellen von Bildern und Bereitstellung Pakete.

2.  [Windows-Treiberkits (WDK) 10](http://developer.microsoft.com/windows/hardware/windows-driver-kit)

3.  [IoT ISO Kernpaket](https://www.microsoft.com/download/confirmation.aspx?id=53898). Das ISO-Paket fügt IoT Core-Pakete und Feature-Manifeste verwendet, um IoT Core Bilder erstellen. Sie müssen sich mit Ihrem Microsoft-Konto anmelden. Standardmäßig werden in diese Pakete installiert **C:\\Program Files (x86)\\Windows Kits\\10\\MSPackages\\Retail**.

4.  [IoT Core ADK Add-Ons](https://github.com/ms-iot/iot-adk-addonkit/).  Klicken Sie auf **Klonen oder Laden Sie** > **ZIP herunterladen**, und Entpacken Sie es auf einen Ordner, beispielsweise **C:\\IoT-ADK-AddonKit**. In diesem Kit enthält die Beispielskripts und Basis Strukturen, die Sie zum Erstellen des Abbilds verwenden. Weitere Informationen zu den Inhalt finden Sie unter [Was ist in der Windows ADK IoT Core-Add-Ons](iot-core-adk-addons.md)).

5.  [Windows 10 IoT Core Dashboard](http://go.microsoft.com/fwlink/p/?LinkId=708576).

Anderen hilfreichen Software:

-   **Einen Text-Editor wie Notepad ++**. Sie können das Tool Editor auch verwenden, obwohl einige Dateien Sie nicht, dass Zeilenumbrüche sehen, wenn Sie jede Datei als UTF-8-Datei öffnen.

-   **Ein Komprimierungsprogramm wie etwa 7-Zip**, in dem Windows-app-Pakete Dekomprimieren kann.

-   [Visual Studio 2015](http://go.microsoft.com/fwlink/?LinkId=715695), zum Erstellen einer app in verwendet [Übung 1 b: app hinzufügen, um das Bild](deploy-your-app-with-a-standard-board.md).

-   [IoT Kern Pro ISO-Paket](https://www.microsoft.com/download/confirmation.aspx?id=53899): zum Ändern der Einstellungen für automatische Updates (verwiesen wird, in [Lab 1D: Paket bereitstellungseinstellungen zu einem Bild hinzufügen](add-a-provisioning-package-to-an-image.md).)

## <a name="span-idothersoftwarespanspan-idothersoftwarespanspan-idothersoftwarespanother-software"></a><span id="Other_software"></span><span id="other_software"></span><span id="OTHER_SOFTWARE"></span>Sonstige software


-   **Einer app für IoT Core integriert**. Verwenden Sie unsere Beispiele der [Hello, World!](https://developer.microsoft.com/windows/iot/samples/helloworld) App, obwohl Sie Ihre eigene verwenden können.

-   **Treiber für IoT Core erstellt**. Unsere Beispiele verwenden den Treiber [Hello, Blinky](https://developer.microsoft.com/windows/iot/samples/helloblinky) , obwohl Sie Ihre eigene verwenden können.

## <a name="span-idnextstepsspanspan-idnextstepsspanspan-idnextstepsspannext-steps"></a><span id="Next_steps"></span><span id="next_steps"></span><span id="NEXT_STEPS"></span>Nächste Schritte

[Übung 1a: Erstellen eines grundlegenden Abbilds](create-a-basic-image.md)