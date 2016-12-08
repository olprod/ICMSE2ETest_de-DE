---
title: DevInfo CSP
description: DevInfo CSP
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: d3eb70db-1ce9-4c72-a13d-651137c1713c
ms.openlocfilehash: 4b53bfdbbdfdc5fa1e0f582757ce574f4eda1d3a
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="devinfo-csp"></a>DevInfo CSP


Der Dienstanbieter für DevInfo Konfiguration behandelt das verwaltete Objekt, das Geräteinformationen an den Server OMA DM bereitstellt. Diese Geräteinformationen wird automatisch an den Server OMA DM am Anfang jeder OMA DM Sitzung gesendet.

> **Hinweis**  Dieses Dienstanbieters Konfiguration erfordert die ID\_CAP\_CSP\_FOUNDATION und ID\_CAP\_GERÄT\_MANAGEMENT\_ADMIN-Funktionen aus einer Anwendung der Netzwerk-Konfiguration zugegriffen werden.

 

Für den CSP DevInfo nicht den Replace-Befehl verwendet werden, wenn der Knoten bereits vorhanden ist.

Das folgende Diagramm veranschaulicht das DevInfo Configuration Service Provider Management-Objekts im Strukturformat von OMA Gerätemanagement verwendet. Provisioning Protokoll OMA-Client wird von dieser Konfigurationsdienstanbieter nicht unterstützt.

![Devinfo Csp (dm)](images/provisioning-csp-devinfo-dm.png)

<a href="" id="devid"></a>**DevId**  
Erforderlich. Gibt einen global eindeutigen anwendungsspezifische Gerätebezeichner in der Standardeinstellung zurück.

Unterstützte Vorgang ist Get.

Der Parameter **UseHWDevID** des Dienstanbieters [DMAcc Konfiguration-Dienstanbieter](dmacc-csp.md) oder DMS Konfiguration kann verwendet werden, den Rückgabewert Rückgabe stattdessen eine Hardware-Geräte-ID wie folgt ändern:

-   G/M2-Telefonen wird die IMEI zurückgegeben.

-   Für Telefone CDMA wird die MEID zurückgegeben.

-   Dieser Wert wird für zwei SIM-Telefone aus der UICC der primären Datenzeile abgerufen.

-   Für Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) wird einen Anwendung bestimmte global eindeutigen Bezeichner (GUID) unabhängig vom Wert der UseHWDevID zurückgegeben.

<a href="" id="man"></a>**Man**  
Erforderlich. Gibt den Namen des OEM zurück. Für Windows-10 für desktop-Editionen, gibt es die SystemManufacturer gemäß Definition im HKEY\_LOKALE\_COMPUTER\\HARDWARE\\BESCHREIBUNG\\System\\BIOS\\SystemManufacturer.

Wenn kein Name gefunden wird, zurückgegeben "Unknown".

Unterstützte Vorgang ist Get.

<a href="" id="mod"></a>**MOD**  
Erforderlich. Gibt den Namen des Modells Hardware gemäß den Mobilfunkbetreiber zurück. Für Windows-10 für desktop-Editionen, gibt es die SystemProductName gemäß Definition im HKEY\_LOKALE\_MACHINE\\HARDWARE\\BESCHREIBUNG\\System\\BIOS\\SystemProductName.

Wenn kein Name gefunden wird, zurückgegeben "Unknown".

Unterstützte Vorgang ist Get.

<a href="" id="dmv"></a>**DmV**  
Erforderlich. Gibt die aktuelle Management Client Überarbeitung des Geräts an.

Unterstützte Vorgang ist Get.

<a href="" id="lang"></a>**Scharfe**  
Erforderlich. Gibt den aktuellen Benutzeroberfläche (UI) Spracheinstellung des Geräts durch RFC1766 definierte.

Unterstützte Vorgang ist Get.

## <a name="related-topics"></a>Verwandte Themen


[Konfiguration Dienstverweis-Anbieter](configuration-service-provider-reference.md)

 

 






