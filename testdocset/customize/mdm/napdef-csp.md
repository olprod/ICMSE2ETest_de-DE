---
title: NAPDEF CSP
description: NAPDEF CSP
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 9bcc65dd-a72b-4f90-aba7-4066daa06988
ms.openlocfilehash: 06c0d254616b64b072a32f76e3c9fa3b5f42b958
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="napdef-csp"></a>NAPDEF CSP


Der Dienstanbieter für NAPDEF Konfiguration wird verwendet, um hinzufügen, ändern oder Löschen von WAP Netzwerkzugriffspunkten (NAPs). Ausführliche Informationen zu diesen Einstellungen finden Sie in der standard WAP-Spezifikation WAP-183-ProvCont-20010724-a.

> **Hinweis**  Sie können nicht NAPDEF CSP auf dem Desktop verwenden, um die Liste Push-Proxy-Gateway (PPG) zu aktualisieren.

 

> **Hinweis**   Diese Konfigurationsdienstanbieter verlangt, dass die ID\_CAP\_CSP\_FOUNDATION und ID\_CAP\_NETWORKING\_ADMIN-Funktionen, die über ein Netzwerk Konfiguration Anwendung zugegriffen werden.

 

Das folgende Diagramm veranschaulicht das NAPDEF Configuration Service Provider Management-Objekts in der Strukturformat, OMA-Clientbereitstellung für die **anfängliche bootstrapping des Telefons**verwendet. Das Protokoll OMA DM wird von dieser Konfigurationsdienstanbieter nicht unterstützt.

![Napdef Csp (cp) (anfängliche bootstrapping)](images/provisioning-csp-napdef-cp.png)

Das folgende Diagramm veranschaulicht das NAPDEF Configuration Service Provider Management-Objekts im Strukturformat von OMA-Clientbereitstellung für das **Aktualisieren der bootstrapping des Telefons**verwendet. Das Protokoll OMA DM wird durch dieses Dienstanbieters Konfiguration nicht unterstützt.

![Napdef Csp (cp) (Update bootstrapping)](images/provisioning-csp-napdef-cp-2.png)

<a href="" id="napauthinfo"></a>**NAPAUTHINFO**  
Definiert eine Gruppe von Authentifizierungseinstellungen.

<a href="" id="authname"></a>**AUTHNAME**  
Gibt den Namen verwendet, um den Benutzer zu authentifizieren.

<a href="" id="authsecret"></a>**AUTHSECRET**  
Gibt das Kennwort verwendet, um den Benutzer zu authentifizieren.

Eine Abfrage dieses Parameters gibt Sternchen (\*) in den Ergebnissen.

<a href="" id="authtype"></a>**AUTHTYPE**  
Gibt das Protokoll verwendet, um den Benutzer zu authentifizieren.

Für dieses Element nur die zulässigen Werte sind "POP" (Password Authentication-Protokoll) und Authentifizierungsprotokolle "CHAP" (Herausforderung Handshake Authentication Protocol). Hinweis

> **Hinweis** **AuthName** und **AuthSecret** werden nicht erstellt werden, wenn **AuthType** nicht in der anfänglichen Gerätekonfiguration enthalten ist.   **AuthName** und **AuthSecret** kann nicht geändert werden, wenn **AuthType** nicht in der XML-Bereitstellungsdatei verwendet, um die Änderung vornehmen enthalten ist.

 

<a href="" id="bearer"></a>**BEARER**  
Gibt den Typ des Bearer.

Es werden nur globale System für Mobile Kommunikation (g/M2) und g/M2 General Packet Radio Services (GPRS) unterstützt.

<a href="" id="internet"></a>**INTERNET**  
Optional Gibt an, ob es eine AlwaysOn-Verbindung handelt.

**INTERNET** vorhanden, wird die Verbindung ist eine AlwaysOn-Verbindung und erfordert keine Connection Manager-Richtlinie.

Wenn **INTERNET** nicht vorhanden ist, wird die Verbindung ist keiner AlwaysOn-Verbindung, und die Verbindung erfordert eine Verbindung Manager Verbindungsrichtlinie festgelegt werden soll.

<a href="" id="local-addr"></a>**LOCAL-ADRESSE**  
Erforderlich für GPRS. Gibt die lokale Adresse des WAP-Clients für GPRS-Zugriffspunkte.

<a href="" id="local-addrtype"></a>**LOKALE ADDRTYPE**  
Erforderlich für GPRS. Gibt das das Adressformat des Elements **LOCAL-ADRESSE** .

Der Wert des LOKALEN ADDRTYPE kann "IPv4" sein.

<a href="" id="name"></a>**NAMEN**  
Gibt die Identität logische, Benutzer lesbare die NAP-DATEI.

<a href="" id="nap-address"></a>**NAP-ADRESSE**  
Gibt die Adresse des der NAP.

<a href="" id="nap-addrtype"></a>**NAP-ADDRTYPE**  
Gibt das Format und ein Protokoll des **NAP-ADRESSEN** -Elements.

Nur Access Point Name (APN) und im E164 werden unterstützt.

<a href="" id="napid"></a>**NAPID**  
Für die anfängliche bootstrapping erforderlich. Gibt den Namen der die NAP-DATEI.

Die maximale Länge des Werts **NAPID** beträgt 16 Zeichen.

<a href="" id="napid"></a>***NAPID***  
Erforderlich für bootstrapping aktualisieren. Definiert den Namen der die NAP-DATEI.

Der Name des Elements *NAPID* ist identisch mit der während der anfänglichen bootstrapping übergebene Wert. Das Microsoft-Format für NAPDEF enthält darüber hinaus die Bereitstellung Mwid der XML-Attribut. Dieses benutzerdefinierte Attribut ist optional, wenn eine NAP oder einen Proxy hinzufügen. Es ist erforderlich für *NAPID* beim Aktualisieren und Löschen von vorhandenen NAPs und -Proxys und dessen Wert muss festgelegt und 1.

## <a name="microsoft-custom-elements"></a>Microsoft benutzerdefinierter Elemente


Die folgende Tabelle enthält die benutzerdefinierten Elemente von Microsoft, die dieser Konfigurationsdienstanbieter für OMA-Clientbereitstellung unterstützt.

<table>
<colgroup>
<col width="20%" />
<col width="80%" />
</colgroup>
<thead>
<tr class="header">
<th>Elemente</th>
<th>Verfügbar</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Parameter-Abfragen</p></td>
<td><p>Ja</p>
<p>Beachten Sie, dass einige GPRS-Parameter nicht notwendigerweise den genauen denselben Wert enthalten werden als festgelegt wurde.</p></td>
</tr>
<tr class="even">
<td><p>noparm</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="odd">
<td><p>nocharacteristic</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="even">
<td><p>Merkmal-Abfrage</p></td>
<td><p>Ja</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>Verwandte Themen


[Konfiguration Dienstverweis-Anbieter](configuration-service-provider-reference.md)

 

 






