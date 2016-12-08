---
title: PXLOGICAL Konfiguration-Dienstanbieter
description: PXLOGICAL Konfigurationsdienstanbieter
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: b5fc84d4-aa32-4edd-95f1-a6a9c0feb459
ms.openlocfilehash: 4c1ce71032e30f9b969381c8710c7da9c41cb689
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="pxlogical-configuration-service-provider"></a>PXLOGICAL Konfiguration-Dienstanbieter


Dienstanbieter PXLOGICAL Konfiguration wird verwendet, um hinzufügen, entfernen oder WAP logische und physische Proxys mithilfe von drahtlosen Zugriffspunkt oder den standardmäßigen Windows-Techniken ändern.

> **Hinweis**   Diese Konfigurationsdienstanbieter verlangt, dass die ID\_CAP\_CSP\_FOUNDATION und ID\_CAP\_NETWORKING\_ADMIN-Funktionen, die über ein Netzwerk Konfiguration Anwendung zugegriffen werden.

 

Im folgenden Diagramm wird das PXLOGICAL Konfiguration Service Provider-Management-Objekt im Strukturformat von OMA-Clientbereitstellung für die anfängliche bootstrapping des Geräts verwendet. Das Protokoll OMA DM wird von dieser Konfigurationsdienstanbieter nicht unterstützt.

![Pxlogical Csp (cp) (anfänglichen bootstrapping)](images/provisioning-csp-pxlogical-cp.png)

Im folgenden Diagramm wird das PXLOGICAL Konfiguration Service Provider-Management-Objekt im Strukturformat von OMA-Clientbereitstellung verwendet, für das Aktualisieren der bootstrapping des Geräts. Das Protokoll OMA DM wird von dieser Konfigurationsdienstanbieter nicht unterstützt.

![Pxlogical Csp (cp) (Update bootstrapping)](images/provisioning-csp-pxlogical-cp-2.png)

<a href="" id="pxphysical"></a>**PXPHYSICAL**  
Definiert eine Gruppe von logischen Proxyeinstellungen.

Das Element Mwid-Attribut ist ein Microsoft provisioning-XML-Attribut und ist optional, wenn eine NAP oder einen Proxy hinzufügen. Es ist erforderlich, wenn aktualisieren und Löschen von vorhandenen NAPs und -Proxys und dessen Wert muss festgelegt und 1.

<a href="" id="domain"></a>**DOMÄNE**  
Gibt den Proxy zugeordnete Domäne an (beispielsweise "\*.com").

Ein Windows-Gerät unterstützt nur einen Proxy, die keinen Domänenparameter oder hat einen leeren Domänenwert. D. h., unterstützt das Gerät nur ein Standardproxy. Alle Proxykonfigurationen benötigen einen Parameter "DOMAIN" mit einem nicht leeren Wert. Eine Abfrage dieses Parameters gibt eine durch Semikolons getrennte Zeichenfolge aller Domänen mit dem Proxy verknüpfte zurück.

<a href="" id="name"></a>**NAMEN**  
Gibt den Namen des logischen Proxys.

Wenn eine Liste Proxys für den Benutzer angezeigt wird, sie zusammen in einer einzelnen Zeile angezeigt werden, daher sollte die Länge dieses Werts Abkürzung für Lesbarkeit sein.

<a href="" id="port"></a>**PORT**  
Definiert die Bindungen zwischen eine Portnummer ein, und eine oder mehrere Protokollen oder Diensten.

Diese Konfigurationsdienstanbieter kann bis zu zwei Ports pro physischen Proxy akzeptieren. Eine Abfrage für diese Eigenschaft gibt Informationen zur ersten Ports.

<a href="" id="portnbr"></a>**PORTNBR**  
Gibt die Portnummer an, die bestimmte Dienste auf diesem Proxy zugeordnet.

Wenn die PORTNBR 80 oder 443 ist oder PORT Merkmal nicht vorhanden ist, wird es als HTTP-Proxy behandelt.

<a href="" id="service"></a>**SERVICE**  
Gibt den Dienst zugeordnet die Portnummer ein.

Windows unterstützt übernehmende verbindungslose WAP Push-Sitzungen über einen kurzen Textnachrichtenelement (SMS) Bearer für WAP Push Nachrichten. Internet Explorer wird keine WAP-Proxy-HTTP-Protokoll verwendet. Eine Abfrage dieses Parameters gibt eine durch Semikolons getrennte Zeichenfolge von Diensten für die ersten Ports zurück.

<a href="" id="pushenabled"></a>**PUSHENABLED**  
Gibt an, ob Push-Vorgänge aktiviert sind.

Wenn dieses Element in PXLOGICAL verwendet wird, gilt es für alle PXPHYSICAL Elemente im PXLOGICAL-Element eingebettet. Der Wert "0" gibt an, dass der Proxy Push-Operationen nicht unterstützt. Der Wert "1" gibt an, dass der Proxyserver Push-Vorgänge unterstützt.

<a href="" id="proxy-id"></a>**PROXY-ID**  
Während der anfänglichen bootstrapping verwendet. Gibt den eindeutigen Bezeichner des logischen Proxys an.

<a href="" id="proxy-id"></a>***PROXY-ID***  
Während des Updates bootstrapping verwendet. Gibt den eindeutigen Bezeichner des logischen Proxys an.

Der Name des Elements **PROXY-ID** ist identisch mit der während der anfänglichen bootstrapping übergebene Wert.

<a href="" id="trust"></a>**VERTRAUENSSTELLUNG**  
Gibt an, ob die physischen Proxys in dieser logische Proxy Berechtigungen verfügen. Die SECPOLICY\_VERTRAUENSWÜRDIGE\_WAP\_PROXY Codezugriffssicherheits-Richtlinie (4121) steuert, welche Rollen dieses Element festlegen können.

<a href="" id="pxphysical"></a>**PXPHYSICAL**  
Definiert eine Gruppe von physischen Proxyeinstellungen mit dem übergeordneten logische Proxy verknüpfte.

Mwid-Attribut für das Element ist ein Microsoft-Bereitstellung XML-Attribut und ist optional, wenn eine NAP oder einen Proxy hinzufügen. Es ist erforderlich, wenn aktualisieren und Löschen von vorhandenen NAPs und -Proxys und dessen Wert muss festlegen auf 1.

<a href="" id="physical-proxy-id"></a>**PHYSISCHE-PROXY-ID**  
Während der anfänglichen bootstrapping verwendet. Gibt den Bezeichner des physischen Proxys.

Wenn eine Liste von Proxys für den Benutzer angezeigt wird, den sie zusammen in einer einzelnen Zeile angezeigt werden, daher sollte die Länge dieses Werts Abkürzung für Lesbarkeit sein.

<a href="" id="physical-proxy-id"></a>***PHYSISCHE-PROXY-ID***  
Während des Updates bootstrapping verwendet. Gibt den Bezeichner des physischen Proxys.

Der Name des **PHYSISCHEN-PROXY-ID** -Elements ist identisch mit der während der anfänglichen bootstrapping übergebene Wert.

<a href="" id="pxaddr"></a>**PXADDR**  
Gibt die Adresse des physischen Proxys.

<a href="" id="pxaddrtype"></a>**PXADDRTYPE**  
Gibt das Format und ein Protokoll des PXADDR-Elements für einen physischen Proxy an.

Unterstützt nur die Werte sind "E164" und "IPv4".

<a href="" id="to-napid"></a>**ZU NAPID**  
Gibt den Netzwerk-Zugriffspunkt dieser physischen Proxy zugeordnet. Nur eine pro Proxy wird unterstützt.

Wenn **AN NAPID** verwendet wird, muss auch der NAP **AN NAPID** auf, deren **NAPID** verweist hinzugefügt werden.

## <a name="microsoft-custom-elements"></a>Microsoft benutzerdefinierter Elemente


Die folgende Tabelle enthält die benutzerdefinierten Elemente von Microsoft, die dieser Konfigurationsdienstanbieter für OMA-Clientbereitstellung unterstützt.

Diese Features sind nur für das Gerät Verfahren verfügbar. Darüber hinaus werden die Parameter-Abfrage und Merkmal-Abfrage-Features für alle PXPHYSICAL Proxy-Parameter für alle Typen von PXADDR nicht unterstützt. Wenn der PXPHYSICAL-Proxy PXADDRType IPv4 ist, können alle Parameter abgefragt werden. Wenn ein Mobilfunkbetreiber den AN NAPID-Parameter, der einen Proxy PXPHYSICAL fragt und E164 beim Typ des PXADDR handelt, wird beispielsweise eine Noparm zurückgegeben.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Feature</th>
<th>Verfügbar</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Parameter-Abfragen</p></td>
<td><p>Ja</p></td>
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

 

 






