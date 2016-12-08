---
title: W4 ANWENDUNG CSP
description: W4 ANWENDUNG CSP
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: ef42b82a-1f04-49e4-8a48-bd4e439fc43a
ms.openlocfilehash: bcfc6b320710de33fdacbaf60a5baabd0e14648f
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="w4-application-csp"></a>W4 ANWENDUNG CSP


Verwenden einer **ANWENDUNG** Konfiguration Service Provider, der ein APPID des w4 Multimedia Messaging Service (MMS) konfigurieren.

Die standardmäßigen Sicherheitsrollen werden in den Stamm Merkmale und zuordnen jeder untergeordnete Knoten definiert, es sei denn, die untergeordneten Knoten bestimmte Berechtigung gewährt wird. Die standardmäßigen Sicherheitsrollen sind Manager, Operator und Operator – TPS.

> **Hinweis**   Dieses Dienstanbieters Konfiguration erfordert die ID\_CAP\_CSP\_FOUNDATION und ID\_CAP\_CSP\_W4\_ANWENDUNG Funktionen, die über ein Netzwerk Konfiguration Anwendung zugegriffen werden.

 

Das folgende Diagramm zeigt den Konfigurationsdienstanbieter im Strukturformat von OMA-Clientbereitstellung verwendet.

![W4 Anwendung Csp (cp)](images/provisioning-csp-w4-application-cp.png)

<a href="" id="appid"></a>**APPID**  
Erforderlich. Dieser Parameter nimmt einen String-Wert. Zum Konfigurieren von MMS der einzige unterstützte Wert ist "w4".

<a href="" id="name"></a>**NAMEN**  
Optional Gibt eine Benutzer – lesbare Anwendungsidentität. Dieser Parameter wird auch verwendet, um Teil der Registrierungspfad für die Anwendungsparameter zu definieren.

Dieser Parameter nimmt einen String-Wert. So konfigurieren Sie den NAME-Parameter die möglichen Werte sind:

-   Zeichenfolge mit dem Namen.

-   kein Wert angegeben

> **Hinweis**  MDM Server sollte erneut ANWENDUNGSNAME/zu DMAcc nach einem Upgrade, da dieser Wert auf der Benutzeroberfläche angezeigt wird, aber nicht auf Windows Phone 8.1 gespeichert und können nicht auf Windows-10 migriert.

 

Wenn kein Wert angegeben ist, wird standardmäßig der Registrierungsspeicherort auf &lt;unbenannte&gt;.

Wenn `Name` ist größer als 40 Zeichen wird auf 40 Zeichen abgeschnitten.

<a href="" id="to-proxy"></a>**-PROXY**  
Erforderlich. Gibt eine logische Proxy mit einer passenden PROXY-ID. Es ist nur möglich, verweisen auf Proxys in der gleichen Bereitstellungsdatei definiert sind. Es kann nur einen Proxy aufgelistet werden.

Der AN-PROXY-Wert muss auf den Wert der PROXY-ID in PXLOGICAL festgelegt werden, den MMS-Proxy auf definiert.

<a href="" id="to-napid"></a>**ZU NAPID**  
Erforderlich. Gibt den Access Point Identification Netzwerknamen (NAPID) in der Bereitstellung Datei definiert. Dieser Parameter nimmt einen String-Wert. Es ist nur möglich, finden Sie unter Netzwerkzugriffspunkten innerhalb der gleichen Bereitstellungsdatei (mit Ausnahme von Wenn das INTERNET-Attribut in die NAPDEF-Eigenschaft festgelegt wird) definiert sind. Weitere Informationen zu der NAPDEF Merkmal finden Sie unter [NAPDEF Konfigurationsdienstanbieter](napdef-csp.md).

<a href="" id="addr"></a>**ADRESSE**  
Erforderlich. Gibt die Adresse des Anwendungsservers MMS als Zeichenfolge. So konfigurieren Sie den Parameter ADRESSE die möglichen Werte sind:

-   Ein URI (Uniform Resource Identifier)

-   Eine IPv4-Adresse dargestellt im Dezimalformat mit Punkten als Trennzeichen

-   Einen vollqualifizierten Internetdomänennamen

<a href="" id="ms"></a>**MS**  
Optional Die maximale autorisierten Größe in KB für multimedia-Inhalt. Dieser Parameter nimmt einen numerischen Wert im Zeichenfolgenformat. Wenn der Wert keine Zahl ist oder kleiner als oder gleich 10 ist, wird ignoriert und ausgehende MMS wird nicht geändert werden.

## <a name="remarks"></a>Hinweise


Windows Phone MMS unterstützt keine Benutzer – auswählbar Profile. Während mehrere MMS Profile bereitgestellt und gleichzeitig gespeichert werden können, ist das zuletzt empfangene Profil aktiv.

Wenn die Bereitstellung von XML für ein Profil mit einem vorhandenen Namen, die Werte empfangen wird, dass Profil mit den neuen Werten überschrieben werden.

Weitere Informationen zu den Parametern von w4 ANWENDUNG Konfiguration-Dienstanbieter und deren Verwendungsweise verwendet werden, finden Sie unter dem OMA MMS Konformität-Dokument (OMA-TS-MMS-CONF-V1\_3-20051027-C) von der [OMA-Website](http://go.microsoft.com/fwlink/p/?LinkId=526900)zur Verfügung.

## <a name="related-topics"></a>Verwandte Themen


[Konfiguration Dienstverweis-Anbieter](configuration-service-provider-reference.md)

 

 






