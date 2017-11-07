---
title: VPN-CSP
description: VPN-CSP
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 05ca946a-1c0b-4e11-8d7e-854e14740707
ms.openlocfilehash: 00fe909b4a87dff6b6a62470a063e0d64e0934b1
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="vpn-csp"></a>VPN-CSP


Der Dienstanbieter für VPN-Konfiguration kann der MDM Server das VPN-Profil des Geräts zu konfigurieren. Windows-10 unterstützt IKEv2 VPN und SSL VPN-Profile. Informationen zu IKEv2 finden Sie unter [Konfigurieren IKEv2-basierter Remotezugriff](http://technet.microsoft.com/library/ff687731%28v=ws.10%29.aspx).

> **Hinweis**   VPN CSP ist in Windows 10 veraltet, und es nur in Windows 10 Mobile zur Abwärtskompatibilität unterstützt. Verwenden Sie stattdessen [VPNv2 CSP](vpnv2-csp.md) .

 

Wichtige Aspekte:

-   Für ein VPN, die ein Clientzertifikat erforderlich sind, muss der Server zuerst zu registrieren das erforderlichen Clientzertifikat vor der Bereitstellung von einem Profil VPN, um sicherzustellen, dass an dem Gerät eine funktionsfähige VPN-Profil vorhanden ist. Dies ist besonders wichtig für erzwungener Tunnel VPN.

-   VPN-Konfigurationsbefehle müssen mit dem Befehl unteilbare umbrochen werden wie im folgenden Beispiel dargestellt.

-   Nur eine VPN-Profil pro Anforderung für eine OMA Bereitstellung wird unterstützt. Mehrere VPN-Profile pro Anforderung von einem OMA Nachricht werden nicht unterstützt.

-   Für den VPN-CSP nicht den Replace-Befehl verwendet werden, wenn der Knoten bereits vorhanden ist.

Das folgende Diagramm zeigt den VPN-Konfigurationsdienstanbieter in der Strukturformat.

![Bereitstellung\-Csp\-Vpn](images/provisioning-csp-vpn.png)

<a href="" id="profilename"></a>***Profilname***  
Eindeutige Alpha numerischen Bezeichner für das Profil. Der Name der Benutzerprofildienst darf nicht mit einen Schrägstrich (/) enthalten.

Werttyp ist chr. Unterstützte Vorgänge umfassen Get, hinzufügen, ersetzen und löschen.

<a href="" id="server"></a>**Server**  
Erforderlich. Öffentliche oder routingfähige IP-Adresse oder DNS-Namen für die VPN-Gateway-Serverfarm. Sie können auf die externe IP-Adresse eines Gateways oder eine virtuelle IP-Adresse für eine Serverfarm zeigen.

Unterstützte Vorgänge sind Get, hinzufügen, und Ersetzen Sie.

Werttyp ist chr. Einige Beispiele sind 208.23.45.130 oder vpn.contoso.com.

<a href="" id="tunneltype"></a>**TunnelType**  
Optional, erforderlich aber, bei der Bereitstellung von einem 3. Partei IKEv2 VPN-Profil. Nur der Wert IKEv2 wird in dieser Version unterstützt.

Werttyp ist chr. Unterstützte Vorgänge sind Get und hinzufügen.

<a href="" id="thirdparty"></a>**ThirdParty**  
Optional, erforderlich aber werden, wenn 3. Partei SSL-VPN-Plug-in-Profil bereitstellen. Definiert eine Gruppe von-Einstellung SSL-VPN-Profil-Bereitstellung.

Unterstützte Vorgänge sind Get und hinzufügen.

<a href="" id="thirdparty-name"></a>**ThirdParty/Name**  
Erforderlich, wenn für die Bereitstellung von SSL-VPN-Profil ThirdParty definiert ist.

Werttyp ist chr. Unterstützte Vorgänge sind Get und hinzufügen.

Gültige Werte:

-   JunOS Pulse

-   SonicWall Mobile eine Verbindung herstellen

-   F5 Big-IP-Edge-Client

-   Prüfpunkt mobilen VPN

<a href="" id="thirdparty-appid"></a>**ThirdParty/AppID**  
Optional, wird aber erforderlich ist, wenn eine 3. Partei SSL-VPN-Plug-in-app aus einer Private Enterprise-Schaufenster bereitstellen. Dies ist die Produkt-ID der Anwendung Speicher zugeordnet. Der Client wird diesen ProductID-Wert verwenden, um sicherzustellen, dass nur das Unternehmen genehmigte-Plug-Ins initialisiert wird.

Werttyp ist chr. Unterstützte Vorgänge sind Get, hinzufügen, ersetzen und löschen.

<a href="" id="thirdparty-customstoreurl"></a>**ThirdParty/CustomStoreURL**  
Optional, doch erforderlich wenn ein Enterprise ist eine 3. Partei SSL-VPN-Plug-in-app aus der Private Enterprise-Schaufenster bereitstellen. Dieser Knoten gibt die URL der 3. Partei SSL-VPN-Plug-in-app.

Werttyp ist chr. Unterstützte Vorgänge sind Get, hinzufügen, ersetzen und löschen.

<a href="" id="thirdparty-customconfiguration"></a>**ThirdParty/CustomConfiguration**  
Optional Dies ist eine HTML-codierte XML-Blob für SSL-VPN-Plug-in Workflowkonfiguration, die an das Gerät zum für SSL-VPN-Plug-Ins verfügbar machen bereitgestellt wird.

Werttyp ist Char. Unterstützte Vorgänge sind Get, hinzufügen, ersetzen und löschen.

<a href="" id="roleorgroup"></a>**RoleOrGroup**  
Nicht implementiert. Optional

Werttyp ist Char. Unterstützte Vorgänge sind Get, hinzufügen, löschen, und ersetzen.

<a href="" id="authentication"></a>**Authentifizierung**  
Optionale Knoten für ThirdParty VPN-Profile für IKEv2 jedoch erforderlich. Dies ist eine Auflistung von Konfigurationsobjekten, um sicherzustellen, dass die richtigen Authentifizierungsrichtlinie, auf dem Gerät basierend auf der ausgewählten verwendet wird TunnelType.

Unterstützte Vorgänge sind Get und hinzufügen.

<a href="" id="authentication-method"></a>**Authentifizierung-Methode**  
Erforderlich für IKEv2 Profile und optional für Drittanbieter-Profile. Hiermit wird den Authentifizierungsanbieter für VPN-Client-Authentifizierung verwenden. Die EAP-Methode wird für IKEv2 Profile unterstützt.

Unterstützte Vorgänge sind Get und hinzufügen.

Werttyp ist chr.

> **Hinweis**  Verwenden Sie für EAP stattdessen/EAP Authentication.

 

<a href="" id="authentication-certificate"></a>**Authentifizierung-Zertifikat**  
Optionale Knoten. Eine Auflistung von Knoten, die einfacher Authentifizierung ermöglicht guter für Endbenutzer beim VPN verwenden. Diese und die zugehörigen untergeordneten Knoten sollte nicht für IKEv2 Profile verwendet werden.

Unterstützte Vorgänge sind Get und hinzufügen.

<a href="" id="authentication-certificate-issuer"></a>**Authentifizierung/Zertifikatsausstellers**  
Optional Filtert die installierten Zertifikate mit privaten Schlüsseln, die in der Registrierung oder TPM gespeichert. Dies kann in Verbindung mit EKU zum Filtern von bieten mehr Granularität verwendet werden.

Werttyp ist chr. Unterstützte Vorgänge sind Get, hinzufügen, löschen, und ersetzen.

> **Hinweis**  Verwenden Sie dieses Element nicht für IKev2 Profile aus.

 

<a href="" id="authentication-certificate-eku"></a>**Authentifizierung/Zertifikat/EKU**  
Optional Dieses Element erweiterte Schlüsselverwendung (EKU) wird verwendet, die installierten Zertifikate mit dem privaten Schlüssel in der Registrierung oder TPM herausfiltern. Sie können dies in Verbindung mit AUSSTELLER für eine genauere Filterung verwenden.

Werttyp ist chr. Unterstützte Vorgänge sind Get, hinzufügen, löschen, und ersetzen.

> **Hinweis**  Verwenden Sie dieses Element nicht für IKev2 Profile aus.

 

<a href="" id="authentication-certificate-cachelifetimeforprotectedcert"></a>**Authentifizierung/Zertifikat/CacheLifeTimeForProtectedCert**  
Nicht implementiert. Optional

Werttyp ist int. Unterstützte Vorgänge sind Get, hinzufügen, ersetzen und löschen.

<a href="" id="authentication-eap"></a>**Authentication-EAP**  
Erforderlich, wenn IKEv2 ausgewählt ist. Definiert den EAP Blob für IKEv2-Authentifizierung verwendet werden soll. Sie können EAP-MSCHAPv2 oder EAP-TLS verwenden. EAP Blob ist, dass HTML-codierte XML-Format in EAP-Host-Config-Schemas definiert. Sie können die Schemas in [Microsoft EAP MsChapV2 Schema](http://go.microsoft.com/fwlink/p/?LinkId=523885) und [Microsoft EAP TLS Schema](http://go.microsoft.com/fwlink/p/?LinkId=523884)suchen.

Unterstützte Vorgänge sind Get, hinzufügen, und Ersetzen Sie.

Werttyp ist chr.

<a href="" id="proxy"></a>**Proxy**  
Optionale Knoten. Eine Auflistung von Konfigurationsobjekten So aktivieren Sie einen Proxy-Unterstützung für VPN nach dem herstellen. Der Proxy für dieses Profil definiert wird angewendet, wenn dieses Profil aktiv und verbunden wird.

Unterstützte Vorgänge sind hinzufügen, löschen, und Ersetzen Sie.

<a href="" id="proxy-manual-server"></a>**/ Manuell/Proxyserver**  
Optional Legen Sie dieses Element zusammen mit PORT. Der Wert ist die Adresse des Proxyservers als einen vollqualifizierten Hostnamen oder eine IP-Adresse, beispielsweise proxy.constoso.com an.

Unterstützte Vorgänge sind Get, hinzufügen, ersetzen und löschen.

Werttyp ist chr.

<a href="" id="proxy-manual-port"></a>**Proxy-/ manuelle/Port**  
Optional Legen Sie dieses Element in Verbindung mit Server. Der Wert ist die Proxy-Serverportnummer im Bereich von 1 und 65535, beispielsweise 8080 an.

Unterstützte Vorgänge sind Get, hinzufügen, ersetzen und löschen.

Werttyp ist int.

<a href="" id="proxy-bypassforlocal"></a>**Proxy/BypassForLocal**  
Optional Wenn diese Einstellung aktiviert ist, werden alle Webanfragen auf Ressourcen in der Intranetzone an den Proxy nicht versendet. Wenn dies auf false festgelegt ist, die Einstellung deaktiviert werden sollen, und gehen alle Anfragen an den Proxy sollte. Wenn dies der Fall ist, wird die Einstellung ist aktiviert, und gehen Intranet Anforderungen nicht an den Proxy.

Unterstützte Vorgänge sind Get, hinzufügen, ersetzen und löschen.

Werttyp ist Bool.

Standard ist False.

<a href="" id="securedresources"></a>**SecuredResources**  
Optionale Knoten. Eine Auflistung von Konfigurationsobjekten, die definieren, die Aufnahme Ressource enthält für was über ein VPN gesichert werden können. Zulässige Listen werden nur angewendet, wenn Richtlinien/SplitTunnel-Element auf "true" festgelegt ist. VPN-Ausschlüsse werden nicht unterstützt.

<a href="" id="securedresources-appallowedlist-appallowedlist"></a>**SecuredResources/AppAllowedList/AppAllowedList**  
Optional Gibt eine oder mehrere ProductIDs für den Enterprise-Zeile des Geschäftsanwendungen, die für Windows an. Wenn dieses Element definiert ist, wird dann gesamten Datenverkehr aus dem angegebenen apps stammende gesichert werden über ein VPN (vorausgesetzt geschützte Netzwerke definiert ermöglicht den Zugriff). Sie werden nicht direkt umgehen die VPN-Verbindung herstellen können. Wenn das Profil automatisch ausgelöst wird, wird die VPN durch diese apps automatisch ausgelöst.

Unterstützte Vorgänge sind Get, hinzufügen, ersetzen und löschen.

Werttyp ist chr.

Beispiele für sind {F05DC613-E223-40AD-ABA9-CCCE04277CD9} und ContosoApp.ContosoCorp\_jlsnulm3s397u.

<a href="" id="securedresources-networkallowedlist-networkallowedlist"></a>**SecuredResources/NetworkAllowedList/NetworkAllowedList**  
Optional, aber erforderlich, wenn Richtlinien/SplitTunnel festgelegt ist, true für IKEv2 Profil. Gibt eine oder mehrere IP-Adressbereichen an, denen über ein VPN gesichert werden soll. Verbinden auf geschützte Ressourcen, die diese Liste entsprechen Applikationen werden über ein VPN gesichert werden. Andernfalls können sie weiterhin eine direkte Verbindung herstellen. Die IP-Adressbereiche sind in der Format-10.0.0.0/8 definiert. Wenn das Profil automatisch ausgelöst wird, wird das VPN automatisch durch diese geschützten Netzwerke ausgelöst.

Unterstützte Vorgänge sind Get, hinzufügen, ersetzen und löschen.

Werttyp ist chr.

Ein Beispiel ist 172.31.0.0/16.

<a href="" id="securedresources-namespaceallowedlist-namespaceallowedlist"></a>**SecuredResources/NameSpaceAllowedList/NameSpaceAllowedList**  
Optional Gibt einen oder mehrere Namespaces, die über ein VPN gesichert werden sollen. Alle Anfragen zu den angegebenen Namespaces sind über ein VPN gesichert. Anwendungen, die eine Verbindung mit Namespaces sind über ein VPN gesichert. Anderenfalls werden sie weiterhin eine direkte Verbindung herstellen. Namespaces sind im Format definiert \*. corp.contoso.com. Einschränkungen wie \* oder \*.\* oder \*. com.\* sind nicht zulässig. NetworkAllowedList ist erforderlich für IKEv2 Profile für den Datenverkehr ordnungsgemäß über geteilte Tunnel routing.

Unterstützte Vorgänge sind Get, hinzufügen, ersetzen und löschen.

Werttyp ist chr.

Ein Beispiel ist \*. "corp.contoso.com".

<a href="" id="securedresources-excluddedapplist-excludedapplist"></a>**SecuredResources/ExcluddedAppList/ExcludedAppList**  
Optional Gibt einen oder mehrere ProductIDs für Enterprise branchenanwendungen, die für Windows an. Wenn das Element definiert ist, werden diese apps nie VPN verwenden. Sie werden direkte Verbindung und die VPN-Verbindung zu umgehen.

Unterstützte Vorgänge sind Get, hinzufügen, ersetzen und löschen.

Werttyp ist chr.

Beispiele für sind {F05DC613-E223-40AD-ABA9-CCCE04277CD9} und ContosoApp.ContosoCorp\_jlsnulm3s397u.

<a href="" id="securedresources-excludednetworklist-excludednetworklist"></a>**SecuredResources/ExcludedNetworkList/ExcludedNetworkList**  
Optional Gibt eine oder mehrere IP-Adressen, die nie VPN verwendet werden soll. Alle Apps, die eine Verbindung mit der konfigurierten IP-Liste der ausgeschlossenen wird direkt im Internet verwenden und VPN umgehen. Werte sind in der Format-10.0.0.0/8 definiert.

Unterstützte Vorgänge sind Get, hinzufügen, ersetzen und löschen.

Werttyp ist chr.

Ein Beispiel ist 172.31.0.0/16.

<a href="" id="securedresources-excludednamespacelist-excludednamespacelist"></a>**SecuredResources/ExcludedNameSpaceList/ExcludedNameSpaceList**  
Optional Gibt einen oder mehrere Namespaces der Hosts, die nie VPN verwendet werden soll. Alle app Herstellen einer Verbindung mit der Hostliste konfigurierte ausgeschlossene im Internet verwenden und VPN umgehen. Einschränkungen wie \* oder \*.\* oder \*. com.\* sind nicht zulässig.

Unterstützte Vorgänge sind Get, hinzufügen, ersetzen und löschen.

Werttyp ist chr.

Ein Beispiel ist \*. "corp.contoso.com".

<a href="" id="securedresources-dnssuffixsearchlist-dnssuffixsearchlist"></a>**SecuredResources/DNSSuffixSearchList/DNSSuffixSearchList**  
Optional Gibt einen oder mehrere DNS-Suffixe, die an Shortname-URLs für DNS-Auflösung und Konnektivität angehängt werden.

Unterstützte Vorgänge sind Get, hinzufügen, ersetzen und löschen.

Werttyp ist chr.

Ein Beispiel ist. "corp.contoso.com".

<a href="" id="policies"></a>**Richtlinien**  
Optionale Knoten. Eine Auflistung von Konfigurationsobjekten können Sie spezifische Einschränkungen zu erzwingen.

<a href="" id="policies-splittunnel"></a>**Richtlinien/SplitTunnel**  
Optional Wenn dies auf false festgelegt ist, wechselt der gesamten Datenverkehr VPN-Gateway im Tunnelmodus erzwingen. Wenn dies auf true festgelegt ist, geht nur der bestimmte Datenverkehr auf definierte gesicherten Ressourcen VPN-Gateway.

Unterstützte Vorgänge sind Get, hinzufügen, ersetzen und löschen.

Werttyp ist Bool.

Standardwert ist True.

<a href="" id="policies-bypassforlocal"></a>**Richtlinien/ByPassForLocal**  
Optional Wenn diese Einstellung auf true festgelegt ist, können Anforderungen an lokale Ressourcen, die im gleichen Wi-Fi-Netzwerk als VPN-Client verfügbar sind das VPN umgehen. Beispielsweise sollte Wenn Unternehmensrichtlinie für VPN Force Tunnel für VPN benötigt, aber Unternehmen beabsichtigt, um den Remotebenutzer für die Verbindung lokal Media Center im Haus zu ermöglichen, klicken Sie dann diese Option auf True festgelegt sein. Der Benutzer kann VPN für Datenverkehr im lokalen Subnetz zu umgehen. Ist deaktiviert, wenn dies die Einstellung "false" festgelegt ist und dürfen keine Subnetz-Ausnahmen.

Unterstützte Vorgänge sind Get, hinzufügen, ersetzen und löschen.

Werttyp ist Bool.

Standardwert ist False.

<a href="" id="policies-trustednetworkdetection"></a>**Richtlinien/TrustedNetworkDetection**  
Optional Wenn diese Einstellung auf "true" festgelegt ist, kann nicht das VPN verbinden, wenn der Benutzer in ihrem Unternehmensnetzwerk drahtlosen ist, auf dem geschützte Ressourcen direkt auf das Gerät zugegriffen werden kann. Wenn dies auf false festgelegt ist, verbindet sich das VPN über drahtlosen Unternehmensnetzwerk. Dieser Knoten ist abhängig von der Einstellung DNSSuffix Knoten zum Erkennen von drahtlosen Unternehmensnetzwerk.

Unterstützte Vorgänge sind Get, hinzufügen, ersetzen und löschen.

Werttyp ist Bool.

Standardwert ist False.

<a href="" id="policies-connectiontype"></a>**Richtlinien/ConnectionType**  
Optional Gültige Werte sind:

-   Auslösen: Ein VPN verbindet automatisch als Clientanwendungen Konnektivität auf geschützte Ressourcen erfordern. Der Lebenszyklus des VPN basiert auf Anwendungen mit dem VPN. Empfohlene Einstellung für die Verwendung von Power-Ressourcen optimieren.

-   Manuell: Benutzer muss manuell verbinden / VPN zu trennen.

Unterstützte Vorgänge sind Get, hinzufügen, und Ersetzen Sie.

Werttyp ist chr.

Standardwert ist auslösen.

<a href="" id="dnssuffix"></a>**DNSSuffix**  
Optional, doch es ist erforderlich, um bestimmte DNS-Suffix der primären Verbindung festgelegt. Unterstützte Vorgänge sind Get, hinzufügen, löschen, und ersetzen.

Werttyp ist chr.

Ein Beispiel ist "corp.contoso.com".

## <a name="related-topics"></a>Verwandte Themen


[Konfiguration Dienstverweis-Anbieter](configuration-service-provider-reference.md)

 

 





