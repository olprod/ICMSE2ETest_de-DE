---
title: PROXY CSP
description: PROXY-CSP
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 9904d44c-4a1e-4ae7-a6c7-5dba06cb16ce
ms.openlocfilehash: f7abed0af69e96e786bfaa548174ce5cec161ad2
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="proxy-csp"></a>PROXY-CSP


Der Dienstanbieter der PROXY-Konfiguration wird verwendet, um die Proxyverbindungen konfigurieren.

> **Hinweis**  Verwendung [CM\_ProxyEntries CSP](cm-proxyentries-csp.md) anstelle von PROXY CSP, die in einer zukünftigen Version veraltet werden wird.

Dieses Dienstanbieters Konfiguration erfordert die ID\_CAP\_CSP\_FOUNDATION und ID\_CAP\_NETWORKING\_ADMIN-Funktionen, die über ein Netzwerk Konfiguration Anwendung zugegriffen werden.

 

Für den CSP PROXY kann nicht ersetzen Verwendung des Befehls, wenn der Knoten bereits vorhanden ist.

Das folgende Diagramm veranschaulicht das PROXY Configuration Service Provider Management-Objekts im Strukturformat von OMA DM verwendet. Das Protokoll OMA-Clientbereitstellung wird von dieser Konfigurationsdienstanbieter nicht unterstützt.

![Proxy-Csp (dm)](images/provisioning-csp-proxy.png)

<a href="" id="--vendor-msft-proxy"></a>**./Vendor/MSFT/Proxy**  
Stammknoten für die Proxy-Verbindung.

<a href="" id="proxyname"></a>***ProxyName***  
Definiert den Namen der Verbindung zu einem Proxy.

Es wird empfohlen, diesen Elementnamen als eine nummerierte Knoten beginnend am 0 (null) angegeben ist. Verwenden Sie beispielsweise um bereitzustellen Proxyverbindungen zwei "PROXY0" und "PROXY1" als die Elementnamen ein. Ein eindeutiger Name kann verwendet werden, falls gewünscht (beispielsweise "GPRS-NAP"), jedoch keine Leerzeichen in den Namen auftreten (verwenden Sie stattdessen 20 %).

Hinzufügen, aktualisieren und Löschung von dieser Teilstruktur von Knoten werden in einer einzigen unteilbare Transaktion angegeben.

<a href="" id="proxyname-proxyid"></a>***ProxyName*/PROXYID**  
Gibt den eindeutigen Bezeichner der Proxyverbindung.

<a href="" id="proxyname-name"></a>****ProxyName/Name**  
Gibt den benutzerfreundlichen Namen der Proxyverbindung.

<a href="" id="proxyname-addr"></a>***ProxyName*/ADDR**  
Gibt die Adresse des Proxyservers.

Dieser Wert ist möglicherweise der Netzwerkname des Servers oder einer anderen Zeichenfolge (beispielsweise eine IP-Adresse) verwendet, um die Proxy-Verbindung eindeutig zu identifizieren.

<a href="" id="proxyname-addrtype"></a>***ProxyName*/ADDRTYPE**  
Gibt den Typ der Adresse verwendet, um den Proxy-Server zu identifizieren.

Die gültigen Werte sind IPV4, IPV6, E164 ALPHA.

<a href="" id="proxyname-proxytype"></a>***ProxyName*/PROXYTYPE**  
Gibt den Typ der Proxy-Verbindung.

Je nach den ProxyID sind die gültigen Werte ISA, WAP, SOCKS oder NULL.

<a href="" id="proxyname-ports"></a>***ProxyName*/Ports**  
Knoten Port Informationen.

<a href="" id="proxyname-ports-portname"></a>****ProxyName/Ports / ***_PortName_**  
Definiert den Namen eines Ports.

Es wird empfohlen, diesen Elementnamen als eine nummerierte Knoten beginnend am 0 (null) angegeben ist. Beispielsweise zum Bereitstellen von zwei Ports verwenden Sie "PORT0" und "PORT1" als Elementnamen.

<a href="" id="proxyname-ports-portname-portnbr"></a>* * *ProxyName*/Ports/*PortName*/PortNbr**  
Gibt die Portnummer des übergeordneten Ports zugeordnet werden soll.

<a href="" id="proxyname-ports-portname-services"></a>* * *ProxyName*/Ports/*PortName*/Services**  
Knoten Services Informationen.

<a href="" id="proxyname-ports-services-servicename"></a>****ProxyName/Ports/Services / ***_ServiceName_**  
Definiert den Namen eines Diensts.

Es wird empfohlen, diesen Elementnamen als eine nummerierte Knoten beginnend am 0 (null) angegeben ist. Verwenden Sie beispielsweise um zwei Dienste bereitzustellen, "SERVICE0" und "SERVICE1" als die Elementnamen ein.

<a href="" id="proxyname-ports-services-servicename-servicename"></a>* * **ProxyName/Ports/Services/*ServiceName*/ServiceName**  
Gibt das Protokoll des übergeordneten Ports zugeordnet werden soll.

Eine häufig verwendeter Wert ist "HTTP".

<a href="" id="proxyname-conrefs"></a>***ProxyName*/ConRefs**  
Knoten für die Verbindung Referenzinformationen

<a href="" id="proxyname-conrefs-conrefname"></a>****ProxyName/ConRefs / ***_ConRefName_**  
Definiert den Namen eines Verweises Verbindung.

Es wird empfohlen, diesen Elementnamen als eine nummerierte Knoten beginnend am 0 (null) angegeben ist. Beispielsweise zum Bereitstellen von zwei Verbindungsverweise verwenden Sie "CONREF0" und "CONREF1" als Elementnamen.

<a href="" id="proxyname-conrefs-conrefname-conref"></a>* * *ProxyName*/ConRefs/*ConRefName*/ConRef**  
Gibt ein einzelnes Connectivity-Objekt die Proxy-Verbindung zugeordnet.

## <a name="related-topics"></a>Verwandte Themen


[Konfiguration Dienstverweis-Anbieter](configuration-service-provider-reference.md)

 

 





