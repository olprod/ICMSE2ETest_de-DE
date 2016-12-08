---
title: CM\_ProxyEntries CSP
description: CM\_ProxyEntries CSP
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: f4c3dc71-c85a-4c68-9ce9-19f408ff7a0a
ms.openlocfilehash: 641f4b10a71817d5b208c0479afc30c5da85504b
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="cmproxyentries-csp"></a>CM\_ProxyEntries CSP


Die CM\_ProxyEntries Konfiguration-Dienstanbieter wird verwendet, um die Proxyverbindungen auf dem mobilen Gerät konfigurieren.

> **Hinweis**  CM\_ProxyEntries CSP ist nur in Windows 10 Mobile unterstützt.

 

> **Hinweis**   Diese Konfigurationsdienstanbieter verlangt, dass die ID\_CAP\_CSP\_FOUNDATION und ID\_CAP\_NETWORKING\_ADMIN-Funktionen, die über ein Netzwerk Konfiguration Anwendung zugegriffen werden.

 

Das folgende Diagramm zeigt die CM\_ProxyEntries Service Provider Management-Konfigurationsobjekt im Strukturformat von Open Mobile Allianz-Clientbereitstellung (OMA CP) und OMA Gerät Management(OMA DM) verwendet. Unterstützung für OMA DM wurde in Windows 10, Version 1607 hinzugefügt.

![cm\-Proxyentries Csp (cp)](images/provisioning-csp-cm-proxyentries-cp.png)

<a href="" id="entryname"></a>**entryname**  
Definiert den Namen des Proxys Verbindung.

Jeder Eintrag Mobilfunk kann nur ein Proxy-Eintrag verfügen. Beispielsweise eine Internetverbindung kann nicht mehr als einen HTTP-Proxy angegeben haben, aber möglicherweise auch einen WAP-Proxy. Wenn gegenseitige Zugriff auf die gleiche APN benötigen jedoch eine Anwendung einen Proxy benötigt und die anderen Anwendung kann keinen Proxy haben, können zwei Einträge mit unterschiedlichen Namen für den gleichen APN erstellt werden.

<a href="" id="connectionname"></a>**ConnectionName**  
Gibt an, der der Namen der Verbindung an den Proxy zugeordnet ist. Dies ist der Name der APN einer Verbindung mit konfiguriert die [CM\_CellularEntries Konfigurationsdienstanbieter](cm-cellularentries-csp.md).

<a href="" id="bypasslocal"></a>**BypassLocal**  
Gibt an, ob der Proxy umgangen werden soll, wenn lokale Hosts vom Gerät zugegriffen werden.

Der Wert "0" gibt an, dass der Proxyserver umgangen für lokale Hosts deaktiviert ist. Der Wert "1" gibt an, dass der Proxyserver umgangen für lokale Hosts aktiviert ist.

<a href="" id="enable"></a>**Aktivieren**  
Gibt an, ob der Proxy aktiviert ist.

Der Wert "0" gibt an, dass der Proxy deaktiviert ist. Der Wert "1" gibt an, dass der Proxy aktiviert ist.

<a href="" id="exception"></a>**Ausnahme**  
Gibt eine Liste von externen Hosts, die den Proxyserver beim Zugriff auf umgehen soll.

Die Ausnahmeliste ist eine durch Semikolons getrennte Liste von Hostnamen. Beispielsweise würde das Umgehen des Proxys Wenn MSN oder Yahoo zugegriffen wird, der Wert für die Ausnahmeliste "www.msn.com;www.yahoo.com" sein.

<a href="" id="password"></a>**Kennwort**  
Gibt das Kennwort zum Verbinden mit dem Proxy.

Kennwörter sind nur erforderlich für WAP und SOCKS Proxys und nicht für HTTP-Proxys verwendet werden. Abfragen dieses Parameters zurückgeben eine Zeichenfolge bestehend aus Sternchen (\*).

Beim Festlegen des Kennworts, übergeben Sie dieselbe Zeichenfolge bewirkt, dass das neue Kennwort, ignoriert werden, und ändert nicht das bestehende Kennwort.

<a href="" id="port"></a>**Port**  
Gibt die Portnummer des Proxyservers an.

<a href="" id="server"></a>**Server**  
Gibt den Namen des Proxyservers an.

<a href="" id="type"></a>**Typ**  
Gibt den Typ der Proxy-Verbindung für diesen Eintrag.

In der folgenden Liste werden die zulässigen Werte für die Type-Parameter aufgezählt.

-   "0" = Null-Proxy

-   "1" = HTTP-Proxy

-   "2" = WAP-Proxy

-   "4" = SOCKS4-Proxy

-   "5" = SOCKS5-Proxys

Der Null-Proxy kann zum Zulassen des Verbindungs-Manager, ein Netzwerk durch Erstellen einer null Proxys von einem Netzwerk zu einem anderen als super Menge von einem anderen Netzwerk zu behandeln verwendet werden.

<a href="" id="username"></a>**Benutzername**  
Gibt den Benutzernamen für die Verbindung an den Proxy verwendet.

## <a name="additional-information"></a>Weitere Informationen


Sie müssen, um einen Proxy und die zugehörige Verbindung zu löschen, löschen Sie zuerst den Proxy und löschen Sie die Verbindung. Im folgenden Beispiel wird gezeigt, wie der Proxy, und klicken Sie dann die Verbindung zu löschen.

``` syntax
<wap-provisioningdoc>
   <characteristic type="CM_ProxyEntries">
      <nocharacteristic type="GPRS_Proxy"/>
   </characteristic>  
   <characteristic type="CM_CellularEntries">
      <nocharacteristic type="GPRS1"/>
   </characteristic>
</wap-provisioningdoc>
```

## <a name="microsoft-custom-elements"></a>Microsoft benutzerdefinierter Elemente


Die folgende Tabelle enthält die benutzerdefinierten Elemente von Microsoft, die dieser Konfigurationsdienstanbieter für OMA-Clientbereitstellung unterstützt.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Element</th>
<th>Verfügbar</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Parameter-Abfragen</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="even">
<td><p>nocharacteristic</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="odd">
<td><p>Merkmal-Abfrage</p></td>
<td><p>Ja</p>
<p>Rekursive Abfrage: Ja</p>
<p>Abfragen auf oberster Ebene Ebene: Ja</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>Verwandte Themen


[Konfiguration Dienstverweis-Anbieter](configuration-service-provider-reference.md)

 

 






