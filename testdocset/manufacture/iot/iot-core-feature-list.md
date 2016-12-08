---
author: kpacquer
Description: Here's the features you can add to Windows 10 IoT Core (IoT Core) images.
ms.assetid: cbae6949-ccfe-4015-a9b0-a269f6f30d5a
MSHAttr: PreferredLib:/library
title: IoT Core Featureliste
ms.openlocfilehash: ed12d251b3a4775483f9e1e1d65242ca12834efc
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="iot-core-feature-list"></a>IoT Core Featureliste

Es folgt die Features, die Sie Windows 10 IoT Core (IoT Core) Bilder hinzufügen können.

Hinzufügen von Features, die mit der OEMInput XML-Datei. Weitere Informationen finden Sie im [IoT Core Fertigung Guide](iot-core-manufacturing-guide.md).

## <a name="span-idretailfeaturesdefinedbymicrosoftspanspan-idretailfeaturesdefinedbymicrosoftspanspan-idretailfeaturesdefinedbymicrosoftspanretail-features-defined-by-microsoft"></a><span id="Retail_features_defined_by_Microsoft"></span><span id="retail_features_defined_by_microsoft"></span><span id="RETAIL_FEATURES_DEFINED_BY_MICROSOFT"></span>Einzelhandel mit Microsoft definierten features

Die folgende Tabelle beschreibt die Microsoft-defined Features, die von OEMs im Features-Element in der Datei **OEMInput** für **Verkaufsversion** verwendet werden können.

Beim Erstellen von Bildern für Ihr Gerät bestimmen, welche Funktionen erforderlich sind, und welche Features sind optional. 

### <a name="span-idrequiredfeaturesspanrequired-features"></a><span id="Required_features"></span>Erforderliche features

Obwohl sie angepasst werden können, müssen die folgenden Features in alle Bilder enthalten sein.

| Features              | Beschreibung                                                                                             |
|-----------------------|---------------------------------------------------------------------------------------------------------|
| **IOT\_APP\_TOOLKIT** | Fügt für Appx Installation und Verwaltung erforderlichen tools                                                |
| **IOT\_EFIESP**       | Startet das Gerät mit UEFI                                                                             |
| **IOT\_UAP\_OOBE**    | Enthält die Posteingang OOBE-app, die beim ersten Start und auch während der Installation von apps gestartet wird |

### <a name="span-idvisualstudiodebugtoolsspan-visual-studio-debug-tools"></a><span id="Visual_Studio_debug_tools"></span>Visual Studio debuggen-tools

| Features                   | Beschreibung                                                                                             |
|----------------------------|---------------------------------------------------------------------------------------------------------|
| **IOT\_CRT140**            | Fügt CRT-Binärdateien                                                                                       |
| **IOT\_DIRECTX\_TOOLS**    | Fügt DirectX-tools                                                                                      |
| **IOT\_UMDFDBG\_EINSTELLUNGEN** | Enthält Benutzermodus-Treiber Framework Debug-Einstellungen                                                      |

### <a name="span-iddevelopertoolsspandeveloper-tools"></a><span id="Developer_tools"></span>Entwicklertools

| Features                   | Beschreibung                                                                                                                 |
|----------------------------|-----------------------------------------------------------------------------------------------------------------------------|
| **IOT\_NETCMD**            | Fügt das Command-Line Tool: net.exe, zum Konfigurieren von Netzwerkkonnektivität                                              |
| **IOT\_POWERSHELL**        | Fügt der PowerShell hinzu                                                                                                             |
| **IOT\_SIREP**             | Ermöglicht SIREP-Dienst für TShell-Konnektivität                                                                               |
| **IOT\_SSH**               | Ermöglicht Secure Shell (SSH)-Konnektivität                                                                                     |
| **IOT\_TOOLKIT**           | Entwicklertools wie enthält: Debuggen von Kernel Komponenten, FTP, Netzwerk-Diagnose, grundlegende Device-Portal und XPerf. Dadurch auch die Firewallregeln lockert und verschiedene Ports ermöglicht.  **Hinweis** Es wird nicht empfohlen, dieses Feature im Einzelhandel Bild einschließlich.                                                                                           |
| **IOT\_WEBB\_EXTN**        | Aktiviert IOTCore-spezifische Extensions Windows Gerät-Portal. Das grundlegende Device Portal ist im IoT Toolkit enthalten.   |

### <a name="span-idappsspanapps-and-related-features"></a><span id="Apps"></span>Apps und die zugehörigen features
| Features                        | Beschreibung                                                                                                                 |
|---------------------------------|-----------------------------------------------------------------------------------------------------------------------------|
| **IOT\_ALLJOYN\_APP**           | Fügt die AllJoyn-Anwendung, für die Headless ZwaveAdapterAppx verwendet. Erfordert **IOT\_APP\_TOOLKIT** dieser Appx beim ersten Start zu installieren.                             |
| **IOT\_BERTHA**                 | Fügt eine Beispiel-app: "Bertha". Diese app bietet Basisversion Info und Konnektivität Status.  Erfordert **IOT\_APP\_TOOLKIT** dieser Appx beim ersten Start zu installieren.            |
| **IOT\_CP210x\_MAKERDRIVER**    | Fügt der SiliconLabs USB mit seriellen Treiber                                                                                   |
| **IOT\_GENERISCHEN\_POP**             | Fügt das generische Gerät Zielgruppenadressierung Info OS nur Updates. Neu in Windows 10 1607 Version.                                |
| **IOT\_FTSER2K\_MAKERDRIVER**   | Fügt den FTDI USB-Seriell-Treiber                                                                                          |
| **IOT\_NANORDPSERVER**          | Fügt [Remote-Anzeige-Pakete](https://developer.microsoft.com/windows/iot/docs/remotedisplay). Neu in Windows 10 1607 Version.                      |
| **IOT\_NETCMD**                 | Fügt das Command-Line Tool: net.exe, zum Konfigurieren von Netzwerkkonnektivität                                              |
| **IOT\_SHELL\_HOTKEY\_SUPPORT** | Fügt die Unterstützung für die Standard-app mithilfe eines Hotkeys zu starten: [VK_LWIN (linke Windows-Taste)](https://msdn.microsoft.com/library/windows/desktop/dd375731(v=vs.85).aspx). Neu in Windows 10 1607 Version.                                                    |  
| **IOT\_UAP\_DEFAULTAPP**        | Fügt eine Beispiel-app "Chucky". Diese app ähnelt "Bertha".  Erfordert **IOT\_APP\_TOOLKIT** dieser Appx beim ersten Start zu installieren.                             |
| **IOT\_UNIFIED\_SCHREIBEN\_FILTER** | Fügt [Unified schreiben Filter (UWF)](https://developer.microsoft.com/windows/iot/docs/uwf) , um physische Speichermedium-Schreibvorgänge zu schützen. Neu in Windows 10 1607 Version.        |

### <a name="span-idspeechdataspanspeech-data"></a><span id="Speech_data"></span>Sprachdaten

| Features                       | Beschreibung                                                                        |
|--------------------------------|------------------------------------------------------------------------------------|
| **IOT\_SPEECHDATA\_DE\_DE**    | Fügt der Sprachdaten für Deutsch                                                        |
| **IOT\_SPEECHDATA\_DE\_GB**    | Fügt Sprachdaten für Englisch (Großbritannien)                                                    |
| **IOT\_SPEECHDATA\_DE\_US**    | In Windows 10, Version 1607 veraltet. Fügen Sie dieses Feature nicht. Das Standardbild umfasst Sprachdaten für Englisch (USA). |
| **IOT\_SPEECHDATA\_ES\_ES**    | Fügt der Sprachdaten für Spanisch                                                       |
| **IOT\_SPEECHDATA\_FR\_FR**    | Fügt der Sprachdaten für Französisch                                                        |
| **IOT\_SPEECHDATA\_IT\_IT**    | Fügt der Sprachdaten für Italienisch                                                       |
| **IOT\_SPEECHDATA\_JA\_JP**    | Fügt der Sprachdaten für Japanisch. Neu in Windows 10, Version 1607                     |
| **IOT\_SPEECHDATA\_ZH\_CN**    | Fügt Sprachdaten für Chinesisch (VR CHINA)                                                 |
| **IOT\_SPEECHDATA\_ZH\_HK**    | Fügt der Sprachdaten für Chinesisch (Hongkong SAR). Neu in Windows 10, Version 1607   |
| **IOT\_SPEECHDATA\_ZH\_TW**    | Fügt der Sprachdaten für Chinesisch (Taiwan). Neu in Windows 10, Version 1607             |

### <a name="span-idfeatures-in-the-iot-core-add-onsspanfeatures-in-the-iot-core-add-ons"></a><span id="Features in the IoT Core Add-Ons"></span>Features in die IoT Core Add-Ons


| Features                  | Beschreibung                                                          |
|---------------------------|----------------------------------------------------------------------|
| **IOT\_OEM\_CustomCmd**   | Fügt der Skripts die unterstützen, Hinzufügen von OEM-Apps mit der ADK Add-Ons     |


## <a name="span-idtestfeaturesdefinedbymicrosoftspanspan-idtestfeaturesdefinedbymicrosoftspanspan-idtestfeaturesdefinedbymicrosoftspantest-features-defined-by-microsoft"></a><span id="Test_features_defined_by_Microsoft"></span><span id="test_features_defined_by_microsoft"></span><span id="TEST_FEATURES_DEFINED_BY_MICROSOFT"></span>Testen Sie die Features von Microsoft definierten

Die folgende Tabelle beschreibt die Microsoft-defined Testfeatures, die von OEMs im Features-Element in der Datei **OEMInput** für Build **Testen** NUR verwendet werden können.

| Features                         | Beschreibung                                                                                                               |
|----------------------------------|---------------------------------------------------------------------------------------------------------------------------|
| **IOT\_DEAKTIVIEREN\_TESTSIGNING**    | Deaktiviert die Common Language Runtime-Installation von Test-signierte Pakete                                                                     |
| **IOT\_DEAKTIVIEREN\_UMCI**           | Deaktiviert die Überprüfung der Integrität code                                                                                         |
| **IOT\_EFIESP\_TEST**            | UEFI-Pakete für das Starten des Test-Bilder erforderlich. Sollten nicht mit IOT_EFIESP verwendet werden                                        |
| **IOT\_AKTIVIEREN\_ADMIN**           | Neu in Windows 10, Version 1607                                                                                           |
| **IOT\_AKTIVIEREN\_TESTSIGNING**     | Laufzeit-Installation von Test-signierten Paketen ermöglicht. Ermöglicht das Test-signierter Treiber und apps ausführen (.appx)                 |
| **IOT\_KD\_ON**                  | Ermöglicht das Kernel-Debugger                                                                                                   |
| **IOT\_KDNETUSB\_EINSTELLUNGEN**      | Enthält alle Kernel-Debugger Transporten und KDNET über USB ermöglicht. Die Debug-Transport-Standardeinstellungen für dieses Feature sind eine IP-Adresse des &quot;1.2.3.4&quot;, eine Portadresse des &quot;50000&quot;, und dem Schlüssel Debugger &quot;4.3.2.1&quot;. Um die Standard-IP-Adresse 1.2.3.4 zu verwenden, führen Sie VirtEth.exe mit dem /autodebug-Flag.  Verwenden Sie beispielsweise den Befehl zum Herstellen einer Verbindung ein Kernel-Debugger an das Telefon:`Windbg -k net:port=50000,key=4.3.2.1`  **Hinweis** enthalten nicht entweder **IOT\_KDUSB\_EINSTELLUNGEN** oder **IOT\_KDNETUSB\_EINSTELLUNGEN** gegebenenfalls MTP oder IP über USB im Bild zu aktivieren. Wenn der Kernel-Debugger im Bild aktiviert ist und die Debuggen Transporten verwendet werden, um auf das Gerät eine Verbindung herstellen, Kernel-Debugger ist zur exklusiven Verwendung des USB-Ports und verhindert MTP und IP-über USB arbeiten.   |
| **IOT\_KDSERIAL\_EINSTELLUNGEN**      | Enthält alle Kernel-Debugger Transporten und ermöglicht das KDSERIAL mit den folgenden Einstellungen: 115.200 Baud, 8-Bit, keine Parität   |
| **IOT\_KDUSB\_EINSTELLUNGEN**         | Enthält alle Kernel Debugger Transporten und KDUSB ermöglicht. Der Standardwert Debug Transport Zielname für dieses Feature ist **WOATARGET**. Verwenden Sie den Befehl zum Herstellen einer Verbindung ein Kernel-Debugger an das Telefon: `Windbg -k usb:targetname=WOATARGET`. **Hinweis** Nehmen Sie keine entweder **IOT_KDUSB_SETTINGS** oder **IOT\_KDNETUSB\_EINSTELLUNGEN** MTP oder IP über USB im Bild aktivieren möchten. Wenn der Kernel-Debugger im Bild aktiviert ist und die Debuggen Transporten verwendet werden, um auf das Gerät eine Verbindung herstellen, Kernel-Debugger ist zur exklusiven Verwendung des USB-Ports und verhindert MTP und IP-über USB arbeiten.      |
| **IOT\_WDTF**                    | Enthält Komponenten für Windows-Treiber Test Framework für die Validierung HLK erforderlich                                        |

## <a name="span-iddevice-specificfeaturesspanspan-iddevice-specificfeaturesspanspan-iddevice-specificfeaturesspandevice-specific-features"></a><span id="Device-specific_features"></span><span id="device-specific_features"></span><span id="DEVICE-SPECIFIC_FEATURES"></span>Gerätespezifische features

Einige Features sind nur für bestimmte bewertungseinrichtungen erforderlich (Himbeeren Pi 2 =**RPi2**, Qualcomm Dragonboard =**DB**, Minnowboard Max =**MBM**).

| Features                             | Beschreibung                                                | Gerät                                                               |
|--------------------------------------|------------------------------------------------------------|----------------------------------------------------------------------|
| **IOT\_DISABLEBASICDISPLAYFALLBACK** | Deaktiviert den Posteingang grundlegende Render-Treiber.                    | Diese Funktion sollte nur mit Qualcomm DragonBoard (DB) verwendet werden. |
| **IOT\_DMAP\_TREIBER**                | Fügt DMAP-Treiber.                                         | Erforderlich für MBM und RPi2. Für DB unterstützt nicht.                     |
| **IOT\_EFIESP\_BCD** |Legt starten Konfigurationsdaten (BCD) für GPT-basierte Laufwerke.                    | Erforderlich für MBM.                                                    |
| **IOT\_POWER\_EINSTELLUNGEN**             | Verhindert, dass das Gerät er aufgrund von Inaktivität deaktiviert. | Erforderlich für MBM und andere X86/amd64-Plattform. **Hinweis** Der Name dieses Paket geändert von IOT\_POWER\_SETIINGS in Windows 10 1607 Version. |

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen

[Was ist in die Windows ADK IoT Core Add-ons](iot-core-adk-addons.md)

[Leitfäden zum IoT Core manufacturing](iot-core-manufacturing-guide.md)
