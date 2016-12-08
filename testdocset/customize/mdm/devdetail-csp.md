---
title: DevDetail CSP
description: DevDetail CSP
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 719bbd2d-508d-439b-b175-0874c7e6c360
ms.openlocfilehash: c20ffc2353148d0f12339a5cca3ff7cd9cf779ff
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="devdetail-csp"></a>DevDetail CSP


DevDetail Konfiguration Dienstanbieters behandelt das Verwaltungsobjekt, das gerätespezifische Parameter an den Server OMA DM bereitstellt an. Diese Geräteparameter werden nicht vom Client zum Server automatisch gesendet, aber von Servern mit OMA DM Befehlen abgefragt werden.

> **Hinweis**  Dieses Dienstanbieters Konfiguration erfordert die ID\_CAP\_CSP\_FOUNDATION und ID\_CAP\_GERÄT\_MANAGEMENT\_ADMIN-Funktionen aus einer Anwendung der Netzwerk-Konfiguration zugegriffen werden.

 

Für den CSP DevDetail nicht den Befehl Replace verwendet werden, es sei denn, der Knoten bereits vorhanden ist.

Im folgenden Diagramm wird das DevDetail Konfiguration Service Provider-Management-Objekt im Strukturformat von OMA Gerätemanagement verwendet. Das Protokoll OMA-Clientbereitstellung wird für diese Konfigurationsdienstanbieter nicht unterstützt.

![Devdetail Csp (dm)](images/provisioning-csp-devdetail-dm.png)

<a href="" id="devtyp"></a>**DevTyp**  
Erforderlich. Gibt das Gerät Modell Namen /SystemProductName als Zeichenfolge zurück.

Unterstützte Vorgang ist Get.

<a href="" id="oem"></a>**OEM**  
Erforderlich. Gibt den Namen des Original Equipment Manufacturer (OEM) als Zeichenfolge zurück, wie in der Spezifikation SyncML Geräteinformationen, Version 1.1.2 definiert.

Unterstützte Vorgang ist Get.

<a href="" id="fwv"></a>**FwV**  
Erforderlich. Gibt die Firmwareversion in den Registrierungsschlüssel HKEY definiert\_LOKALE\_COMPUTER\\System\\Plattform\\DeviceTargetingInfo\\PhoneFirmwareRevision.

Für Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen), es gibt die BIOS-Version in den Registrierungsschlüssel HKEY definiert\_LOKALE\_COMPUTER\\HARDWARE\\BESCHREIBUNG\\System\\BIOS\\BIOSVersion.

Unterstützte Vorgang ist Get.

<a href="" id="swv"></a>**SwV**  
Erforderlich. Gibt die Softwareversion Windows 10 OS im Format MajorVersion.MinorVersion.BuildNumber.QFEnumber zurück. Derzeit gibt die Buildnummer die Buildnummer auf Desktop- und mobilen Buildnummer auf dem Telefon zurück. In der Zukunft möglicherweise die Build-Nummern konvergieren.

Unterstützte Vorgang ist Get.

<a href="" id="hwv"></a>**HwV**  
Erforderlich. Gibt die Hardwareversion von, in den Registrierungsschlüssel HKEY definiert\_LOKALE\_COMPUTER\\System\\Plattform\\DeviceTargetingInfo\\PhoneRadioHardwareRevision.

Für Windows-10 für desktop-Editionen, es gibt die BIOS-Version in den Registrierungsschlüssel HKEY definierte\_LOKALE\_COMPUTER\\HARDWARE\\BESCHREIBUNG\\System\\BIOS\\BIOSVersion.

Unterstützte Vorgang ist Get.

<a href="" id="lrgobj"></a>**LrgObj**  
Erforderlich. Gibt an, ob das Gerät OMA DM große Objekt verarbeiten verwendet, gemäß Definition in der Spezifikation SyncML Geräteinformationen, Version 1.1.2.

Unterstützte Vorgang ist Get.

<a href="" id="uri-maxdepth"></a>**URI/MaxDepth**  
Erforderlich. Gibt die maximale Tiefe der Management-Struktur, die das Gerät unterstützt. Der Standardwert ist NULL (0).

Unterstützte Vorgang ist Get.

Dies ist die maximale Anzahl der Segmente URI, die das Gerät unterstützt. Der Standardwert NULL (0) gibt an, dass das Gerät einen URI unbegrenzte Tiefe unterstützt.

<a href="" id="uri-maxtotlen"></a>**URI/MaxTotLen**  
Erforderlich. Gibt die maximale Gesamtlänge des URI verwendet, um einen Knoten oder Node-Eigenschaft zurück. Der Standardwert ist NULL (0).

Unterstützte Vorgang ist Get.

Dies ist die größte Zahl der Zeichen in der URI, der das Gerät unterstützt. Der Standardwert NULL (0) gibt an, dass das Gerät URI unbegrenzte Länge unterstützt.

<a href="" id="uri-maxseglen"></a>**URI/MaxSegLen**  
Erforderlich. Gibt die Gesamtlänge der URI Segmente in einen URI, der einen Knoten oder Node-Eigenschaft "addresses" zurück. Der Standardwert ist NULL (0).

Unterstützte Vorgang ist Get.

Dies ist die maximale Zeichenanzahl in einem einzelnen Segment URI das Gerät unterstützen können. Der Standardwert NULL (0) gibt an, dass das Gerät URI Segment der unbegrenzte Länge unterstützt.

<a href="" id="ext-microsoft-mobileid"></a>**Microsoft/Ext/MobileID**  
Erforderlich. Gibt die mobilen Geräte-ID der Mobilfunknetz zugeordnet zurück. Gibt 404 für Geräte, die nicht über ein Mobilfunknetz Support verfügen.

Unterstützte Vorgang ist Get.

Der Wert IMSI ist für Netzwerke g/M2 und UMTS zurückgegeben. CDMA und weltweit Telefone gibt Fehler 404 nicht gefunden Status Code wird zurück, wenn dieses Element abgefragt.

<a href="" id="ext-microsoft-localtime"></a>**Microsoft/Ext/Ortszeit**  
Erforderlich. Gibt die Ortszeit Client im ISO 8601-Format zurück.

Unterstützte Vorgang ist Get.

<a href="" id="ext-microsoft-osplatform"></a>**Microsoft/Ext/OSPlatform**  
Erforderlich. Gibt die Betriebssystemplattform des Geräts zurück. Für Windows-10 für desktop-Editionen, es gibt die ProductName in HKLM definierte\\SOFTWARE\\Microsoft\\Windows NT\\CurrentVersion\\ProductName.

Unterstützte Vorgang ist Get.

<a href="" id="ext-microsoft-processortype"></a>**Microsoft/Ext/ProcessorType**  
Erforderlich. Gibt den Typ des Prozessors des Geräts gemäß Dokumentation im SYSTEM\_INFO.

Unterstützte Vorgang ist Get.

<a href="" id="ext-microsoft-radioswv"></a>**Microsoft/Ext/RadioSwV**  
Erforderlich. Gibt die Nummer der Radio Stack Softwareversion zurück.

Unterstützte Vorgang ist Get.

<a href="" id="ext-microsoft-resolution"></a>**Microsoft/Ext/Lösung**  
Erforderlich. Gibt die Auflösung der Benutzeroberfläche des Geräts (Beispiel: "480 x 800").

Unterstützte Vorgang ist Get.

<a href="" id="ext-microsoft-commercializationoperator"></a>**Microsoft/Ext/CommercializationOperator**  
Erforderlich. Der Name der Mobilfunkbetreiber zurückgegeben, falls vorhanden; Andernfalls wird 404 zurückgegeben.

Unterstützte Vorgang ist Get.

<a href="" id="ext-microsoft-processorarchitecture"></a>**Microsoft/Ext/ProcessorArchitecture**  
Erforderlich. Gibt die Prozessorarchitektur des Geräts als "Arm" oder "X86" zurück.

Unterstützte Vorgang ist Get.

<a href="" id="ext-microsoft-devicename"></a>**Microsoft/Ext/DeviceName**  
Erforderlich. Enthält den Gerätenamen des vom Benutzer angegebener.

Unterstützung für Ersetzungsvorgang für Windows 10 Mobile wurde in Windows 10, Version 1511 hinzugefügt. Ersetzungsvorgang wird in den Desktop nicht unterstützt. Wenn Sie den Gerätenamen mithilfe dieser Knoten ändern, wird ein Dialogfeld, auf dem Gerät, das den Benutzer auffordert, neu starten. Der neue Gerätename ist nicht wirksam wird, bis das Gerät neu gestartet wird. Wenn der Benutzer im Dialogfeld abbricht, wird erneut angezeigt, bis ein Neustart auftritt.

Werttyp ist Zeichenfolge.

Unterstützte Vorgänge sind Get und ersetzen.

<a href="" id="ext-microsoft-totalstorage"></a>**Microsoft/Ext/TotalStorage**  
In Windows 10, Version 1511 hinzugefügt. Ganzzahl, die den gesamten verfügbaren Speicherplatz in MB vom ersten internen Laufwerk, auf dem Gerät angibt (kleiner als der physische Gesamtspeicher möglicherweise).

Unterstützte Vorgang ist Get.

> **Hinweis**  Dies ist nur in Windows 10 Mobile unterstützt.

 

<a href="" id="ext-microsoft-totalram"></a>**Microsoft/Ext/TotalRAM**  
In Windows 10, Version 1511 hinzugefügt. Integer-Wert, der den gesamten verfügbaren Speicherplatz auf dem Gerät in MB angibt (ist kleiner als die Gesamtmenge des physischen Arbeitsspeichers möglich).

Unterstützte Vorgang ist Get.

<a href="" id="ext-wlanmacaddress"></a>**Ext/WLANMACAddress**  
Die MAC-Adresse der aktiven WLAN-Verbindung, als eine hexadezimale Zahl 12 Ziffern.

Unterstützte Vorgang ist Get.

> **Hinweis**  Dies ist nicht für desktop-Editionen in Windows 10 unterstützt.

 

<a href="" id="volteservicesetting"></a>**VoLTEServiceSetting**  
Gibt den Dienst VoLTE aktiviert oder deaktiviert. Dies ist nur für Mobilfunkbetreiber OMA DM Servern verfügbar gemacht.

Unterstützte Vorgang ist Get.

<a href="" id="wlanipv4address"></a>**WlanIPv4Address**  
Gibt die IPv4-Adresse der aktiven Wi-Fi-Verbindung zurück. Dies ist nur der OMA DM Unternehmensserver ausgesetzt.

Unterstützte Vorgang ist Get.

<a href="" id="wlanipv6address"></a>**WlanIPv6Address**  
Gibt die IPv6-Adresse der aktiven Wi-Fi-Verbindung zurück. Dies ist nur für OMA DM Unternehmensserver verfügbar gemacht.

Unterstützte Vorgang ist Get.

<a href="" id="wlandnssuffix"></a>**WlanDnsSuffix**  
Gibt das DNS-Suffix der aktiven Wi-Fi-Verbindung zurück. Dies ist nur für OMA DM Unternehmensserver verfügbar gemacht.

Unterstützte Vorgang ist Get.

<a href="" id="wlansubnetmask"></a>**WlanSubnetMask**  
Gibt die Subnetzmaske für die aktive Wi-Fi-Verbindung zurück. Dies ist nur für Enterprise OMA DM Servern verfügbar gemacht.

Unterstützte Vorgang ist Get.

## <a name="related-topics"></a>Verwandte Themen


[Konfiguration Dienstverweis-Anbieter](configuration-service-provider-reference.md)

 

 






