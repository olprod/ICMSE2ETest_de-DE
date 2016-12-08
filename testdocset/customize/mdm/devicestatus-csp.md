---
title: DeviceStatus CSP
description: "Der Dienstanbieter für DeviceStatus Konfiguration wird vom Unternehmen verfolgen Geräteübersicht und der Status der Einhaltung dieser Geräte ihren Unternehmensrichtlinien abgefragt."
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 039B2010-9290-4A6E-B77B-B2469B482360
ms.openlocfilehash: 4ad389c2dbc2a7162d9f71ad4a4a489293716208
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="devicestatus-csp"></a>DeviceStatus CSP


Der Dienstanbieter für DeviceStatus Konfiguration wird vom Unternehmen verfolgen Geräteübersicht und der Status der Einhaltung dieser Geräte ihren Unternehmensrichtlinien abgefragt.

Die folgende Abbildung zeigt den DeviceStatus Konfigurationsdienstanbieter im Strukturformat dar.

![Devicestatus csp](images/provisioning-csp-devicestatus.png)

<a href="" id="devicestatus"></a>**DeviceStatus**  
Der Stammknoten für den Dienstanbieter für DeviceStatus-Konfiguration.

<a href="" id="devicestatus-securebootstate"></a>**DeviceStatus/SecureBootState**  
Gibt an, ob die sichere Boot aktiviert ist. Der Wert kann eine der folgenden:

-   0 - nicht unterstützt
-   1 – aktiviert
-   2 - deaktiviert

Unterstützte Vorgang ist Get.

<a href="" id="devicestatus-cellularidentities"></a>**DeviceStatus/CellularIdentities**  
Erforderlich. Der Knoten für Abfragen auf den Karten SIM.

> **Hinweis**  Werden mehrere SIMs unterstützt.

 

<a href="" id="devicestatus-cellularidentities-imei"></a>**DeviceStatus/CellularIdentities / ***_IMEI_**  
Die eindeutige International Mobile Station Equipment Identity (IMEI) Nummer des mobilen Geräts. Ein IMEI ist für jede Karte SIM auf dem Gerät vorhanden.

<a href="" id="devicestatus-cellularidentities-imei-imsi"></a>* *DeviceStatus/CellularIdentities/*IMEI*/IMSI**  
Der International Mobile Abonnenten Identität (IMSI) die Anzahl IMEI zugeordnet.

Unterstützte Vorgang ist Get.

<a href="" id="devicestatus-cellularidentities-imei-iccid"></a>* *DeviceStatus/CellularIdentities/*IMEI*/ICCID**  
Der Chip Karte ID (ICCID) der Karte SIM die jeweilige IMEI Zahl zugeordnet.

Unterstützte Vorgang ist Get.

<a href="" id="devicestatus-cellularidentities-imei-phonenumber"></a>* *DeviceStatus/CellularIdentities/*IMEI*/PhoneNumber**  
Die Anzahl der bestimmten IMEI zugeordnete Telefonnummer.

Unterstützte Vorgang ist Get.

<a href="" id="devicestatus-cellularidentities-imei-commercializationoperator"></a>* *DeviceStatus/CellularIdentities/*IMEI*/CommercializationOperator**  
Der Dienstanbieter für mobiles oder Mobilfunkbetreiber, die bestimmte IMEI Anzahl zugeordnet.

Unterstützte Vorgang ist Get.

<a href="" id="devicestatus-cellularidentities-imei-roamingstatus"></a>* *DeviceStatus/CellularIdentities/*IMEI*/RoamingStatus**  
Gibt an, ob die SIM-Karte mit der bestimmte IMEI-Nummer verbundenen roaming ist.

Unterstützte Vorgang ist Get.

<a href="" id="devicestatus-cellularidentities-imei-roamingcompliance"></a>* *DeviceStatus/CellularIdentities/*IMEI*/RoamingCompliance**  
Boolescher Wert, der Einhaltung der Richtlinie roaming erzwungene Enterprise angibt.

Unterstützte Vorgang ist Get.

<a href="" id="devicestatus-networkidentifiers"></a>**DeviceStatus/NetworkIdentifiers**  
Der Knoten für Abfragen auf Netzwerk- und Geräte-Eigenschaften.

<a href="" id="devicestatus-networkidentifiers-macaddress"></a>**DeviceStatus/NetworkIdentifiers / ***_MacAddress_**  
MAC-Adresse der Karte drahtlosen Netzwerk. MAC-Adresse ist für jede Netzwerkkarte auf dem Gerät vorhanden.

<a href="" id="devicestatus-networkidentifiers-macaddress-ipaddressv4"></a>* *DeviceStatus/NetworkIdentifiers/*MacAddress*/IPAddressV4**  
IPv4-Adresse der Netzwerkkarte, die MAC-Adresse zugeordnet.

Unterstützte Vorgang ist Get.

<a href="" id="devicestatus-networkidentifiers-macaddress-ipaddressv6"></a>* *DeviceStatus/NetworkIdentifiers/*MacAddress*/IPAddressV6**  
IPv6-Adresse der Netzwerkkarte, die MAC-Adresse zugeordnet.

Unterstützte Vorgang ist Get.

<a href="" id="devicestatus-networkidentifiers-macaddress-isconnected"></a>* *DeviceStatus/NetworkIdentifiers/*MacAddress*/IsConnected**  
Boolescher Wert, der angibt, ob die Netzwerkkarte, die MAC-Adresse zugeordneten eine aktive Verbindung verfügt.

Unterstützte Vorgang ist Get.

<a href="" id="devicestatus-networkidentifiers-macaddress-type"></a>* *DeviceStatus/NetworkIdentifiers/*MacAddress*/Type**  
Typ der Netzwerkverbindung. Der Wert kann eine der folgenden:

-   WLAN
-   LAN
-   Unbekannt (Bluetooth- oder anderen unbekannten Netzwerkverbindungen)

Unterstützte Vorgang ist Get.

<a href="" id="devicestatus-compliance"></a>**DeviceStatus/Compliance**  
Knoten für die Compliance-Abfrage.

<a href="" id="devicestatus-compliance-encryptioncompliance"></a>**DeviceStatus/Compliance/EncryptionCompliance**  
Boolescher Wert, der Einhaltung der Unternehmensrichtlinie Verschlüsselung angibt. Der Wert kann eine der folgenden:

-   0 - nicht verschlüsselt.
-   1 – verschlüsselt

Unterstützte Vorgang ist Get.

<a href="" id="devicestatus-tpm"></a>**DeviceStatus/TPM**  
Die Version 1607, hinzugefügt. Der Knoten für die TPM-Abfrage.

Unterstützte Vorgang ist Get.

<a href="" id="devicestatus-tpm-specificationversion"></a>**DeviceStatus/TPM/SpecificationVersion**  
Die Version 1607, hinzugefügt. Zeichenfolge, die Spezifikationsversion angibt.

Unterstützte Vorgang ist Get.

<a href="" id="devicestatus-os"></a>**DeviceStatus/OS**  
Die Version 1607, hinzugefügt. Der Knoten für die Abfrage OS.

Unterstützte Vorgang ist Get.

<a href="" id="devicestatus-os-edition"></a>**DeviceStatus/OS/Edition**  
Die Version 1607, hinzugefügt. Zeichenfolge, die die Betriebssystem Edition angibt.

Unterstützte Vorgang ist Get.

<a href="" id="devicestatus-antivirus"></a>**DeviceStatus/Antivirus**  
-Version 1607, hinzugefügt. Der Knoten für die Abfrage antivirus.

Unterstützte Vorgang ist Get.

<a href="" id="devicestatus-antivirus-signaturestatus"></a>**DeviceStatus/Antivirus/SignatureStatus**  
Die Version 1607 in, hinzugefügt. Ganze Zahl, die den Status der Signatur antivirus angibt.

Gültige Werte:

-   0 – meldet die Sicherheits-Software, dass es sich nicht um die aktuellste Version ist.
-   1 (Standard) - Berichte die Sicherheits-Software, dass es sich um die aktuellste Version ist.
-   2 – nicht zutreffend. Dies wird zurückgegeben für Geräte wie das Telefon, die nicht über ein Antivirus verfügen (dabei ist nicht die API vorhanden.)

Unterstützte Vorgang ist Get.

<a href="" id="devicestatus-antivirus-status"></a>**DeviceStatus/Antivirus/Status**  
Die Version 1607, hinzugefügt. Ganze Zahl, die den Status Antivirus angibt.

Gültige Werte:

-   0 – Antivirus befindet sich auf und Überwachung
-   1 – Antivirus ist deaktiviert.
-   2 – Antivirus überwacht nicht den Geräte/PC oder einige Optionen sind deaktiviert
-   3 (Standard) – Antivirus vorübergehend nicht vollständig den Gerät/PC überwacht
-   4 – Antivirus gilt nicht für dieses Gerät. Dies wird zurückgegeben für Geräte wie das Telefon, die nicht über ein Antivirus verfügen (dabei ist nicht die API vorhanden.)

Unterstützte Vorgang ist Get.

<a href="" id="devicestatus-antispyware"></a>**DeviceStatus/Antispyware**  
Die Version 1607 in, hinzugefügt. Der Knoten für die Abfrage Antispyware.

Unterstützte Vorgang ist Get.

<a href="" id="devicestatus-antispyware-signaturestatus"></a>**DeviceStatus/Antispyware/SignatureStatus**  
-Version 1607, hinzugefügt. Ganze Zahl, die den Status der Signatur Antispyware angibt.

Unterstützte Vorgang ist Get.

<a href="" id="devicestatus-antispyware-status"></a>**DeviceStatus/Antispyware/Status**  
Die Version 1607, hinzugefügt. Ganze Zahl, die den Status der Antispywaresoftware angibt.

Unterstützte Vorgang ist Get.

<a href="" id="devicestatus-firewall"></a>**DeviceStatus-Firewall**  
Die Version 1607, hinzugefügt. Der Knoten für die Abfrage Firewall.

Unterstützte Vorgang ist Get.

<a href="" id="devicestatus-firewall-status"></a>**DeviceStatus/Firewall/Status**  
Die Version 1607, hinzugefügt. Ganze Zahl, die den Status der Firewall angibt.

Gültige Werte:

-   0 – Firewall ist auf und Überwachung
-   1 – Firewall wurde deaktiviert.
-   2 – Firewall ist nicht alle Netzwerke überwachen oder einige Regeln deaktiviert wurden
-   3 (Standard) – Firewall vorübergehend nicht alle Netzwerke überwacht
-   4: nicht zutreffend. Dies wird zurückgegeben für Geräte wie das Telefon, die nicht über ein Antivirus verfügen (dabei ist nicht die API vorhanden.)

Unterstützte Vorgang ist Get.

<a href="" id="devicestatus-uac"></a>**DeviceStatus/UAC**  
Die Version 1607, hinzugefügt. Der Knoten für die UAC-Abfrage.

Unterstützte Vorgang ist Get.

<a href="" id="devicestatus-uac-status"></a>**DeviceStatus/UAC/Status**  
Die Version 1607, hinzugefügt. Integer-Wert, der den Status der UAC angibt.

Unterstützte Vorgang ist Get.

<a href="" id="devicestatus-battery"></a>**DeviceStatus-Batterie**  
Die Version 1607, hinzugefügt. Der Knoten für die Abfrage Batterie.

Unterstützte Vorgang ist Get.

<a href="" id="devicestatus-battery-status"></a>**DeviceStatus/Batterie/Status**  
Die Version 1607, hinzugefügt. Ganze Zahl, die den Status der Batterie angibt

Unterstützte Vorgang ist Get.

<a href="" id="devicestatus-battery-estimatedchargeremaining"></a>**DeviceStatus/Batterie/EstimatedChargeRemaining**  
-Version 1607, hinzugefügt. Integer-Wert, der die geschätzten Kosten für den Umzug Energie angibt. Dies ist der Wert in **BatteryLifeTime** im zurückgegebenen [SYSTEM\_POWER\_STATUS Struktur](https://msdn.microsoft.com/library/windows/desktop/aa373232.aspx).

Der Wert ist die Anzahl der Sekunden Batterie verbleibende Nutzungsdauer, wenn das Gerät nicht an eine Stromversorgung angeschlossen ist. Wenn es an die Stromversorgung angeschlossen ist, wird der Wert-1 an. Wenn die Schätzung unbekannt ist, wird der Wert-1 ein.

Unterstützte Vorgang ist Get.

<a href="" id="devicestatus-battery-estimatedruntime"></a>**DeviceStatus/Batterie/EstimatedRuntime**  
-Version 1607, hinzugefügt. Integer-Wert, der die geschätzte Laufzeit der Batterie angibt. Dies ist der Wert in **BatteryLifeTime** im zurückgegebenen [SYSTEM\_POWER\_STATUS Struktur](https://msdn.microsoft.com/library/windows/desktop/aa373232.aspx).

Der Wert ist die Anzahl der Sekunden Batterie verbleibende Nutzungsdauer, wenn das Gerät nicht an eine Stromversorgung angeschlossen ist. Wenn es an die Stromversorgung angeschlossen ist, wird der Wert-1 an. Wenn die Schätzung unbekannt ist, wird der Wert-1.

Unterstützte Vorgang ist Get.

 

 






