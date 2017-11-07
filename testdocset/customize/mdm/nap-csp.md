---
title: NAP-CSP
description: NAP-CSP
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 82f04492-88a6-4afd-af10-a62b8d444d21
ms.openlocfilehash: 1d3823aa12551a37a0eca786c1f92db4d2138b74
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="nap-csp"></a>NAP-CSP


Der Dienstanbieter für NAP (Network Access Point) Konfiguration wird verwendet, um verwalten und Abfragen GPRS und CDMA Verbindungen.

> **Hinweis**   Diese Konfigurationsdienstanbieter verlangt, dass die ID\_CAP\_CSP\_FOUNDATION und ID\_CAP\_NETWORKING\_ADMIN-Funktionen, die über ein Netzwerk Konfiguration Anwendung zugegriffen werden.

 

Für den CSP NAP-nicht den Replace-Befehl verwendet werden, wenn der Knoten ist bereits vorhanden.

Im folgenden Diagramm wird die NAP-Konfiguration Service Provider Verwaltung-Objekts im Strukturformat von OMA DM verwendet. Das Protokoll OMA-Clientbereitstellung wird von dieser Konfigurationsdienstanbieter nicht unterstützt.

![NAP-Csp (dm)](images/provisioning-csp-nap.png)

<a href="" id="--vendor-msft-nap"></a>**./Vendor/MSFT/NAP**  
Stammknoten.

<a href="" id="napx"></a>***NAPX***  
Erforderlich. Definiert den Namen des Network Access Point.

Es wird empfohlen, diesen Elementnamen als eine nummerierte Knoten beginnend am 0 (null) angegeben ist. Beispielsweise um zwei Netzwerkzugriffspunkten bereitstellen möchten, verwenden Sie "NAP0" und "NAP1" als Elementnamen. Ein eindeutiger Name kann verwendet werden, falls gewünscht (beispielsweise "GPRS-NAP"), aber keine Leerzeichen in den Namen auftreten (verwenden Sie stattdessen 20 %).

<a href="" id="napx-napid"></a>***NAPX*/NAPID**  
Erforderlich. Gibt den Bezeichner der Zielnetzwerk.

Der Wert NAPID darf keine "@" Zeichen. Der Dienstanbieter für NAPDEF Konfiguration als definiert “connectionID@WAP”, dieser Wert auf "ConnectionID" festgelegt werden sollte.

<a href="" id="napx-name"></a>****NAPX/Name**  
Optional Gibt den benutzerfreundlichen Namen der Verbindung.

<a href="" id="napx-addr"></a>***NAPX*/ADDR**  
Erforderlich. Gibt die Adresse des Zielnetzwerks.

Die ADRESSE möglicherweise die URL des Access Point, den APN Namen für einen Zugriffspunkt GPRS und die Telefonnummer des ein antwortenden Modem oder einer anderen Zeichenfolge verwendet, um die Adresse des Zielnetzwerk eindeutig zu identifizieren.

<a href="" id="napx-addrtype"></a>***NAPX*/ADDRTYPE**  
Erforderlich. Gibt den Typ der Adresse zur Identifizierung des Zielnetzwerks.

In der folgenden Tabelle gezeigt, dass einige häufig ADDRTYPE-Werte und die Typen der Verbindung mit jedem Wert verwendet.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>ADDRTYPE-Wert</th>
<th>Verbindungstyp</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>E164</p></td>
<td><p>RAS-Verbindungen</p></td>
</tr>
<tr class="even">
<td><p>APN</p></td>
<td><p>GPRS-Verbindungen</p></td>
</tr>
<tr class="odd">
<td><p>ALPHA</p></td>
<td><p>Wi-Fi-basierte Verbindungen</p></td>
</tr>
</tbody>
</table>

 

<a href="" id="napx-authinfo"></a>***NAPX*/AuthInfo**  
Optionale Knoten. Gibt die Authentifizierungsinformationen angeben, einschließlich der Protocol, Benutzernamen und das Kennwort an.

<a href="" id="napx-authinfo-authtype"></a>****NAPX/AuthInfo/AuthType**  
Optional Gibt die Methode der Authentifizierung. Einige unterstützte Protokolle sind PAP, CHAP, HTTP-BASIC HTTP-DIGESTAUTHENTIFIZIERUNG, WTLS-SS, MD5.

<a href="" id="napx-authinfo-authname"></a>****NAPX/AuthInfo/AuthName**  
Optional Gibt den Benutzernamen und die Domäne an, die während der Authentifizierung verwendet werden. Dieses Feld ist in der Form *Domäne*\\*Benutzername*.

<a href="" id="napx-authinfo-authsecret"></a>****NAPX/AuthInfo/AuthSecret**  
Optional Gibt das Kennwort während der Authentifizierung verwendet.

Abfragen der dieses Feld wird eine Zeichenfolge bestehend aus sechzehn Sternchen zurückgegeben (\*).

<a href="" id="napx-bearer"></a>***NAPX*/Bearer**  
Knoten.

<a href="" id="napx-bearer-bearertype"></a>****NAPX/Bearer/BearerType**  
Erforderlich. Gibt den Netzwerktyp des Zielnetzwerks. Dies kann auf GPRS, CDMA2000, WCDMA, TDMA, CSD, DTPT, verwendeten WLAN festgelegt werden.

## <a name="related-topics"></a>Verwandte Themen


[Konfiguration Dienstverweis-Anbieter](configuration-service-provider-reference.md)

 

 






