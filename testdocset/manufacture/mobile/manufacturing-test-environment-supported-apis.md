---
author: kpacquer
Description: "Umgebung für Manufacturing unterstützt APIs"
ms.assetid: a51f7722-ccca-4571-9f07-3ff512a0ddaa
MSHAttr: PreferredLib:/library/windows/hardware
title: "Fertigung testumgebung unterstützt APIs"
ms.openlocfilehash: e8ec1abf9e4a027ef4f83a476ea16b292942caf6
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="manufacturing-test-environment-supported-apis"></a>Umgebung für Manufacturing unterstützt APIs


Die Fertigung Test Environment (Migrationstabellen-EDITOR) unterstützt-APIs und Techniken zur für die Verwendung in der Produktion. In diesem Abschnitt wird beschrieben, die bestimmten Bibliotheken, die im Migrationstabellen-EDITOR unterstützt werden.

## <a name="span-idmmoslibspanspan-idmmoslibspanmmoslib"></a><span id="mmos.lib"></span><span id="MMOS.LIB"></span>MMOS. LIB


MMOS. LIB stellt eine Spiegelung-Schnittstelle für die Windows 8-mincore.lib. Allgemeine Informationen zu mincore.lib finden Sie unter [Windows-API-Sätze](http://msdn.microsoft.com/library/windows/desktop/Hh802935.aspx).

Die primäre Benutzermodus systemeigene APIs für die Verwendung im Migrationstabellen-EDITOR werden in den MMOS-Bibliothek (lib)-Dateien installiert durch Windows Driver Kit (WDK) als WPDKCONTENTROOT % definiert\\Lib\\ Ordner.

## <a name="span-idsupportedapisspanspan-idsupportedapisspanspan-idsupportedapisspansupported-apis"></a><span id="Supported_APIs"></span><span id="supported_apis"></span><span id="SUPPORTED_APIS"></span>Unterstützte APIs


Die folgenden Abschnitte enthalten eine Vorschau der Features, die der bereitgestellten MMOS APIs für das Testen ermöglichen. Weitere Informationen zu den MMOS unterstützt APIs in einer zukünftigen Version dieser Dokumentation bereitgestellt werden. Die Unterordner des API-Header und Windows SDK-Header befinden sich der "%ProgramFiles(x86)%\\Windows Kits\\10\\enthalten\\" Ordner. Diese APIs können im Benutzermodus-Anwendungen für MMOS verwendet werden. Weitere Informationen zum Erstellen und Ausführen MMOS ASP.NET-Anwendungen finden Sie im Thema [MMOS entwickeln, Testen Applications](develop-mmos-test-applications.md) .

### <a name="span-idmicrophoneaudioandaudioroutingspanspan-idmicrophoneaudioandaudioroutingspanspan-idmicrophoneaudioandaudioroutingspanmicrophone-audio-and-audio-routing"></a><span id="Microphone__audio_and_audio_routing"></span><span id="microphone__audio_and_audio_routing"></span><span id="MICROPHONE__AUDIO_AND_AUDIO_ROUTING"></span>Mikrofon, Audio- und audio-routing

Die Audio- und audio-routing-APIs können Test apps So testen Sie die Audio- und audio-routing-Funktionen. Einige Szenarien, Test, die apps testen können spielen Frequenzen auf jedem der verschiedenen audio-Endpunkte. Das Mikrofon kann mit den audio-APIs getestet werden. Die folgenden Header-Dateien enthalten die Audio- und audio-routing-APIs.

-   Mmos\\audiotunerapi.h

-   Mmos\\audiotunerdef.h

-   Mmos\\audiotunerprop.h

-   Km\\Ksmedia\_phone.h

-   Um\\deklariert

-   Um\\avrt.h (Windows SDK)

-   CTime.h (Windows SDK)

-   Um\\audioclient.h (Windows SDK)

-   Um\\mmdeviceapi.h (Windows SDK)

-   Um\\functiondiscoverykeys.h (Windows SDK)

### <a name="span-iddisplayspanspan-iddisplayspanspan-iddisplayspandisplay"></a><span id="Display"></span><span id="display"></span><span id="DISPLAY"></span>Anzeige

Sie können die Direct3D verwenden, zum Anzeigen von Informationen. Allgemeine Info finden Sie unter diesem Link MSDN [Direct3D 11 Grafiken](http://msdn.microsoft.com/library/windows/desktop/ff476080.aspx). Die folgenden Header-Dateien enthalten die D3D-APIs.

-   Um\\D3DWrapper.h

-   Um\\D3D11.h (Windows SDK)

### <a name="span-idcameraspanspan-idcameraspanspan-idcameraspancamera"></a><span id="Camera"></span><span id="camera"></span><span id="CAMERA"></span>Kamera

Die Media Foundation CaptureEngine APIs können Sie die Kamera entwickelt. Allgemeine Informationen zum Arbeiten mit Media Foundation finden Sie unter [Media Foundation Programming Reference](http://msdn.microsoft.com/library/windows/desktop/ms704847.aspx) auf MSDN. Informationen zur IMFCaptureEngine-Schnittstelle finden Sie unter in diesem Thema MSDN, [IMFCaptureEngine Schnittstelle](http://msdn.microsoft.com/library/windows/desktop/hh447846.aspx). Die folgenden Headerdateien enthalten Schnittstellen, die für das Testen der Kamera hilfreich sein können.

-   Um\\mfapi.h

-   Um\\mfobjects.h

-   Um\\mfidl.h

-   Um\\mfreadwrite.h

-   Um\\mfcaptureengine.h

-   Um\\wincodec.h

### <a name="span-idsensorsspanspan-idsensorsspanspan-idsensorsspansensors"></a><span id="Sensors"></span><span id="sensors"></span><span id="SENSORS"></span>Sensoren

Weitere Informationen zu Sensoren und APIs, die zu Testzwecken in MMOS verwendet werden, finden Sie unter dem Thema Sensoren.

### <a name="span-idledspanspan-idledspanled"></a><span id="LED"></span><span id="led"></span>LED-ANZEIGE

Die LED-APIs können Test apps zum Testen der LED-benachrichtigungs durch Aufrufen von verschiedenen IOCTLs, um die Benachrichtigung zu aktivieren, deaktivieren oder blinken GEFÜHRT. Die folgenden Header-Datei enthält die LED-APIs.

-   Mmos\\hwn.h

### <a name="span-idsdcardspanspan-idsdcardspanspan-idsdcardspansd-card"></a><span id="SD_Card"></span><span id="sd_card"></span><span id="SD_CARD"></span>SD-Karte

Die SD-Karte APIs ermöglichen Test-apps in der Treiber SD-Karte durch Aufrufen von verschiedenen IOCTLs zu Testfällen wie Lesen und Schreiben in die Karte testen. Die folgenden Header-Datei enthält die SD-Karte APIs.

-   Um\\sffdisk.h

### <a name="span-idtouchspanspan-idtouchspanspan-idtouchspantouch"></a><span id="Touch"></span><span id="touch"></span><span id="TOUCH"></span>Tippen Sie auf

Weitere Informationen zum Testen des Touch-Controllers finden Sie im Thema [Access Touch-Schnittstelle in MMOS](access-the-touch-interface-in-mmos.md) . Die folgenden Header-Dateien enthalten die Fingereingabe APIs.

-   Um\\InputDriverRawSamples.h

-   Um\\WinPhoneInput.h

### <a name="span-idvibratorspanspan-idvibratorspanspan-idvibratorspanvibrator"></a><span id="Vibrator"></span><span id="vibrator"></span><span id="VIBRATOR"></span>Vibrator

Die Vibrator APIs ermöglichen Test apps auf die Vibrator auf dem Gerät zu testen, indem Sie verschiedene IOCTLs aufrufen. Die IOCTLs zulassen der apps auf verschiedenen kumulativ und Zeiträume, in denen der Treiber Vibrator auf dem Gerät zu testen. Die folgende Headerdatei enthält die Vibrator APIs.

-   Mmos\\hwn.h

### <a name="span-idhardwarebuttonsspanspan-idhardwarebuttonsspanspan-idhardwarebuttonsspanhardware-buttons"></a><span id="Hardware_buttons"></span><span id="hardware_buttons"></span><span id="HARDWARE_BUTTONS"></span>Hardware-Schaltflächen

Weitere Informationen zu Tasten finden Sie unter der Hardware Schaltflächen Thema. Die folgende Headerdatei enthält die Taste APIs.

-   UM\\ntddkbd.h

### <a name="span-idfmradiospanspan-idfmradiospanspan-idfmradiospanfm-radio"></a><span id="FM_radio"></span><span id="fm_radio"></span><span id="FM_RADIO"></span>UKW

Die UKW ermöglichen APIs Test apps auf das Optionsfeld UKW auf dem Telefon durch Aufrufen von FM IOCTLs testen. Die IOCTLs zulassen apps zum Testen verschiedener Szenarien wie Feinabstimmung für eine Häufigkeit oder Suchvorgänge. Die folgenden Header-Dateien enthalten die UKW APIs.

-   Mmos\\audiotunerapi.h

-   Mmos\\audiotunerprop.h

### <a name="span-idwi-fispanspan-idwi-fispanspan-idwi-fispanwi-fi"></a><span id="Wi-Fi"></span><span id="wi-fi"></span><span id="WI-FI"></span>Wi-Fi

Weitere Informationen zu Wi-Fi testing APIs finden Sie im Thema [Wi-Fi Manufacturing API](wi-fi-manufacturing-api.md) . Die folgende Headerdatei enthält die Wi-Fi-APIs.

-   Um\\wifimte.h

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Aufrufen von SetScreenOff eingeben verbunden standby](calling-setscreenoff-to-enter-connected-standby.md)

 

 






