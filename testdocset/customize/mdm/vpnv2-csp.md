---
title: VPNv2 CSP
description: VPNv2 CSP
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 51ADA62E-1EE5-4F15-B2AD-52867F5B2AD2
ms.openlocfilehash: 4d2fae60d28b1a2d659028079c0bc6a3baa061c1
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="vpnv2-csp"></a>VPNv2 CSP


Der VPNv2 Konfiguration-Dienstanbieter ermöglicht den Verwaltungsserver Mobilgerät (MDM) so konfigurieren Sie das VPN-Profil des Geräts.

Hier sind die Anforderungen für diesen Kryptografiedienstanbieter:

-   VPN-Konfigurationsbefehle müssen in einer atomarisch umbrochen werden in SyncML blockieren.
-   Konfigurieren Sie die besten Ergebnisse erzielen Sie Ihre VPN-Zertifikate zunächst vor weitergeben VPN-Profile für Geräte. Wenn Sie Windows-Schutz (WIP) (vormals Enterprise Data Protection) verwenden, sollten Sie VPN zuerst konfigurieren, bevor Sie WIP Richtlinien konfigurieren.
-   Anstatt einzelne Eigenschaften ändern, folgendermaßen Sie vor, um die Änderungen vorgenommen werden können:

    -   Senden eines Delete-Befehls für die Profilname, um das gesamte Profil zu löschen.
    -   Senden Sie das gesamte Profil erneut mit neuen Werten in einem unteilbare Block eingeschlossen.

    In bestimmten Fällen können Sie direkt einige Eigenschaften ändern, aber es wird nicht empfohlen.

Die XSDs für alle EAP-Methoden sind in das Feld geliefert und finden Sie unter den folgenden Speicherorten:

-   C:\\Windows\\Schemas\\EAPHost
-   C:\\Windows\\Schemas\\EAPMethods

Das folgende Diagramm zeigt den VPNv2 Konfiguration-Dienstanbieter in der Strukturformat.

![vpnv2 Csp Diagramm](images/provisioning-csp-vpnv2-rs1.png)

<a href="" id="device-or-user-profile"></a>**Geräte oder Benutzer-Profil**  
Für das Benutzerprofil **./User/Vendor/MSFT** Pfad verwenden, und für Device-Profil **./Device/Vendor/MSFT** Pfad verwenden.

<a href="" id="vpnv2-profilename"></a>**VPNv2 /** *Profilname*  
Alpha numerische Kennung für das Profil. Der Name der Benutzerprofildienst darf nicht mit einen Schrägstrich (/) enthalten.

Unterstützte Vorgänge einschließen abrufen, die Sie hinzufügen und löschen.

> **Hinweis**  Weist den Namen des Profils ein Leerzeichen oder andere nicht alphanumerische Zeichen, müssen sie entsprechend der URL-Codierung ordnungsgemäß geschützt.

 

<a href="" id="vpnv2-profilename-apptriggerlist"></a>**VPNv2 /** *Profilname* **/AppTriggerList**  
Optionale Knoten. Liste der Anwendungen, die auf das VPN auslösen festgelegt. Wenn keines dieser apps gestartet werden und das VPN-Profil derzeit aktive Profil ist, wird dieses Profil VPN ausgelöst werden, um eine Verbindung herzustellen.

<a href="" id="vpnv2-profilename-apptriggerlist-apptriggerrowid"></a>**VPNv2 /** *Profilname* **/AppTriggerList/** *appTriggerRowId*  
Ein Bezeichner der sequenzielle ganze Zahl, der ermöglicht, sodass die Möglichkeit, mehrere-apps für App-Trigger anzugeben. Sequenzierung muss bei 0 beginnen, und überspringen Sie nicht Zahlen.

Unterstützte Vorgänge einschließen Get, hinzufügen, ersetzen und löschen.

<a href="" id="vpnv2-profilename-apptriggerlist-apptriggerrowid-app"></a>**VPNv2 /** *Profilname* **/AppTriggerList/** *appTriggerRowId* **/App**  
App-Knoten unter Zeilen-Id.

<a href="" id="vpnv2-profilename-apptriggerlist-apptriggerrowid-app-id"></a>**VPNv2 /** *Profilname* **/AppTriggerList/** *appTriggerRowId* **/App/ID**  
App-Identität, der entweder einer app-Produktfamilie Paketname oder Dateipfad ist. Der Typ wird durch die Id abgeleitet, und daher nicht im Feld App-Typ Get angegeben werden

<a href="" id="vpnv2-profilename-apptriggerlist-apptriggerrowid-app-type"></a>**VPNv2 /** *Profilname* **/AppTriggerList/** *appTriggerRowId* **/App/type**  
Gibt den Typ des **App-Id**zurück. Dieser Wert kann einer der folgenden sein:

-   PackageFamilyName - Wenn dies zurückgegeben wird, stellt der App-Id-Wert der PackageFamilyName der app. Die PackageFamilyName ist der eindeutige Name der Windows Store-Anwendung.
-   FilePath - Wenn dies zurückgegeben wird, stellt der App-Id-Wert den vollständigen Dateipfad der app. Beispielsweise `C:\Windows\System\Notepad.exe`.

Werttyp ist chr. Unterstützte Vorgang ist Get.

<a href="" id="vpnv2-profilename-routelist-"></a>**VPNv2 /** *Profilname* **/RouteList/**  
Optionale Knoten. Liste von Routen, die routing-Tabelle für VPN-Schnittstelle hinzugefügt werden soll. Dies ist erforderlich für Split Tunneling-Fall, in dem die VPN-Server-Website Weitere Subnetze verfügt, auf denen die IP-Adresse zugewiesen, die Benutzeroberfläche das Standard-Subnetz basiert.

Alle Computer mit TCP/IP macht Routingentscheidungen. Diese Entscheidungen werden von der IP-Routingtabelle gesteuert. Hinzufügen von Werten unter diesem Knoten aktualisiert die Routingtabelle mit Routen für die VPN-Schnittstelle Post-Verbindung. Die Werte unter diesem Knoten stellen das Ziel Präfix der IP-Routen. Ein Ziel-Präfix besteht aus ein Präfix für den IP-Adresse und eine Präfixlänge.

Hinzufügen einer Route hier ermöglicht Netzwerken Stapel, um den Datenverkehr zu identifizieren, der über VPN-Schnittstelle für geteilten Tunnel VPN weitergeleitet. Einige VPN-Server können dies konfigurieren, während eine Verbindung herstellen Aushandlung und diese Informationen im VPN-Profil ist nicht erforderlich. Überprüfen Sie Ihre VPN-Server-Administrator, um festzustellen, ob Sie diese Informationen im VPN-Profil benötigen.

<a href="" id="vpnv2-profilename-routelist-routerowid"></a>**VPNv2 /** *Profilname* **/RouteList/** *routeRowId*  
Eine sequenzielle ganze Zahl Bezeichner für die RouteList. Dies ist erforderlich, wenn Sie Routen hinzufügen. Sequenzierung muss bei 0 beginnen.

Unterstützte Vorgänge umfassen Get, hinzufügen, ersetzen und löschen.

<a href="" id="vpnv2-profilename-routelist-routerowid-address"></a>**VPNv2 /** *Profilname* **/RouteList/** *routeRowId* **Knotenadresse**  
Subnetzadresse im Format von/v6 IPv4-Adresse, die zusammen mit dem Präfix verwendet wird, um die Ziel-Präfix zum Senden über VPN-Schnittstelle zu bestimmen. Dies ist der Teil der IP-Adresse des Präfixes Ziel.

Unterstützte Vorgänge umfassen Get, hinzufügen, ersetzen und löschen. Werttyp ist chr. Beispiel`192.168.0.0`

<a href="" id="vpnv2-profilename-routelist-routerowid-prefixsize"></a>**VPNv2 /** *Profilname* **/RouteList/** *routeRowId* **/PrefixSize**  
Der Subnetz Präfix Größe Teil des Ziel Präfix für den Routeneintrag. Bestimmt das Ziel Präfix über VPN-Schnittstelle weitergeleitet werden, zusammen mit der Adresse verwendet.

Werttyp ist int. Unterstützte Vorgänge umfassen Get, hinzufügen, ersetzen und löschen.

<a href="" id="vpnv2-profilename-routelist-routerowid-exclusionroute"></a>**VPNv2 /** *Profilname* **/RouteList/** *routeRowId* **/ExclusionRoute**  
In Windows 10, Version 1607 hinzugefügt. Ein boolescher Wert, der angibt, wenn die Route hinzugefügte VPN-Schnittstelle oder der physikalischen Schnittstelle als Gateway verweisen soll. Gültige Werte:

-   False (Standard) - diese Route leitet Datenverkehr über VPN
-   Diese Route wird true - Datenverkehr über die physische Schnittstelle leiten.

Unterstützte Vorgänge umfassen Get, hinzufügen, ersetzen und löschen.

<a href="" id="vpnv2-profilename-domainnameinformationlist"></a>**VPNv2 /** *Profilname* **/DomainNameInformationList**  
Optionale Knoten. Name der Lösung Richtlinie Tabelle (NRPT) Regeln für das VPN-Profil.

Name Resolution Richtlinie Tabelle (NRPT) ist eine Tabelle mit Namespaces und die entsprechenden Einstellungen in der Windows-Registrierung, die das Clientverhalten DNS beim Ausgeben von Abfragen und Verarbeitungsantworten bestimmt gespeichert. Jede Zeile in der NRPT stellt eine Regel für einen Teil des Namespaces für das Abfragen von der DNS-Client Probleme. Bevor Namensabfragen Auflösung ausgegeben wird, konsultiert der DNS-Client NRPT um festzustellen, ob zusätzliche Attribute in der Abfrage festgelegt werden müssen. Nach dem Empfang der Antwort, konsultiert der Client erneut NRPT zu prüfen, ob die speziellen Anforderungen Verarbeitung oder Richtlinie. In keine NRPT arbeitet der Client basierend auf dem DNS-Server und Suffixe der Schnittstelle.

<a href="" id="vpnv2-profilename-domainnameinformationlist-dnirowid"></a>**VPNv2 /** *Profilname* **/DomainNameInformationList/** *dniRowId*  
Ein sequenzielle ganze Zahl Bezeichner für den Domänennamen Informationen. Sequenzierung muss bei 0 beginnen.

Unterstützte Vorgänge umfassen Get, hinzufügen, ersetzen und löschen.

<a href="" id="vpnv2-profilename-domainnameinformationlist-dnirowid-domainname"></a>**VPNv2 /** *Profilname* **/DomainNameInformationList/** *dniRowId* **/DomainName**  
Verwendet, um den Namespace anzugeben, auf den die Richtlinie angewendet wird. Wenn eine Namensabfrage ausgegeben wird, vergleicht der DNS-Client den Namen in der Abfrage, die alle Namespaces unter DomainNameInformationList eine Übereinstimmung gesucht. Dieser Parameter kann eine der folgenden Objekttypen sein:

-   FQDN - Domänennamen
-   Suffix - ein Domänensuffix, das auf die Abfrage Shortname für DNS-Auflösung angehängt wird. Wenn Sie ein Suffix angeben, voranstellen Sie eine **.** das DNS-Suffix.

Werttyp ist chr. Unterstützte Vorgänge umfassen Get, hinzufügen, ersetzen und löschen.

<a href="" id="vpnv2-profilename-domainnameinformationlist-dnirowid-domainnametype"></a>**VPNv2 /** *Profilname* **/DomainNameInformationList/** *dniRowId* **/DomainNameType**  
Gibt den Namespace zurück. Dieser Wert kann eine der folgenden sein:

-   FQDN - Wenn der Domänenname nicht eine **.** vorangestellt wurde und gilt nur für den vollqualifizierten Domänennamen (FQDN) eines angegebenen Hosts.
-   Suffix - Wenn der Domänenname mit eine **.** vorangestellt wurde und gilt für den angegebenen Namespace, alle Datensätze in diesen Namespace und allen Unterdomänen.

Werttyp ist chr. Unterstützte Vorgang ist Get.

<a href="" id="vpnv2-profilename-domainnameinformationlist-dnirowid-dnsservers"></a>**VPNv2 /** *Profilname* **/DomainNameInformationList/** *dniRowId* **/DnsServers**  
Liste der durch Trennzeichen getrennten DNS-Server-IP-Adressen an, die für den Namespace verwenden.

Werttyp ist chr. Unterstützte Vorgänge umfassen Get, hinzufügen, ersetzen und löschen.

<a href="" id="vpnv2-profilename-domainnameinformationlist-dnirowid-webproxyservers"></a>**VPNv2 /** *Profilname* **/DomainNameInformationList/** *dniRowId* **/WebProxyServers**  
Optional Web Proxy-Server-IP-Adresse, wenn Sie Umleiten von Datenverkehr über das Intranet Ihres.

> **Hinweis**  Derzeit wird nur eine Webproxyserver unterstützt.

 

Werttyp ist chr. Unterstützte Vorgänge umfassen Get, hinzufügen, ersetzen und löschen.

<a href="" id="vpnv2-profilename-domainnameinformationlist-dnirowid-autotrigger"></a>**VPNv2 /** *Profilname* **/DomainNameInformationList/** *dniRowId* **/AutoTrigger**  
In Windows 10, Version 1607 hinzugefügt. Optional Boolescher Wert, um festzustellen, ob die Regel für diese Domäne das VPN ausgelöst werden soll.

Wenn auf False festgelegt ist, diese Regel DomainName nicht das VPN auslöst.

Wenn auf True festgelegt ist, diese Regel DomainName VPN ausgelöst werden soll

Standardmäßig ist dieser Wert "false".

Werttyp ist Bool. Persistent

<a href="" id="vpnv2-profilename-domainnameinformationlist-dnirowid-persistent"></a>**VPNv2 /** *Profilname* **/DomainNameInformationList/** *dniRowId* **/ Persistent**  
In Windows 10, Version 1607 hinzugefügt. Ein boolescher Wert, der angibt, ob die Regel hinzugefügte beibehalten werden soll, selbst wenn das VPN nicht verbunden ist. Wert:

-   False (Standard) - dieser DomainName Regel nur angewendet wird, wenn VPN verbunden ist.
-   True - werden diese Regel DomainName immer vorhanden und angewendet.

Unterstützte Vorgänge umfassen Get, hinzufügen, ersetzen und löschen.

<a href="" id="vpnv2-profilename-trafficfilterlist"></a>**VPNv2 /** *Profilname* **/TrafficFilterList**  
Einen optionalen Knoten, der eine Liste der Regeln angibt. Nur Datenverkehr, der diese Regeln entspricht kann über VPN-Schnittstelle gesendet werden.

> **Hinweis**  Sobald ein TrafficFilterList hinzugefügt wird, werden alle Datenverkehr blockiert als derjenigen, die den Regeln entsprechen.

 

Wenn arbeitet Hinzufügen mehrerer Regeln, jede Regel basierend auf einer OR mit anderen Regeln. Jede Regel ausgeführt wird, wird jede Eigenschaft basierend auf einer UND miteinander.

<a href="" id="vpnv2-profilename-trafficfilterlist-trafficfilterid"></a>**VPNv2 /** *Profilname* **/TrafficFilterList/** *trafficFilterId*  
Ein für den Datenverkehr Filterregeln sequenzielle Integer-Bezeichner. Sequenzierung muss bei 0 beginnen.

<a href="" id="vpnv2-profilename-trafficfilterlist-trafficfilterid-app"></a>**VPNv2 /** *Profilname* **/TrafficFilterList/** *trafficFilterId* **/App**  
Pro app VPN Regel. Dadurch wird nur die apps über VPN-Schnittstelle zugelassen wird angegeben. Werttyp ist chr.

<a href="" id="vpnv2-profilename-trafficfilterlist-trafficfilterid-app-id"></a>**VPNv2 /** *Profilname* **/TrafficFilterList/** *trafficFilterId* **/App/ID**  
App-Identität für den app-basierter Datenverkehrsfilter.

Der Wert für diesen Knoten kann eine der folgenden sein:

-   PackageFamilyName - stellt diese App-Id-Wert der PackageFamilyName der app. Die PackageFamilyName ist der eindeutige Name einer Windows Store-Anwendung.
-   FilePath - dieser App-Id-Wert stellt den vollständigen Dateipfad der app. Beispielsweise `C:\Windows\System\Notepad.exe`.
-   SYSTEM – ermöglicht dieser Wert Kernel-Treiber zum Senden von Datenverkehr über VPN (beispielsweise PING oder SMB).

Werttyp ist chr. Unterstützte Vorgänge umfassen Get, hinzufügen, ersetzen und löschen.

<a href="" id="vpnv2-profilename-trafficfilterlist-trafficfilterid-app-type"></a>**VPNv2 /** *Profilname* **/TrafficFilterList/** *trafficFilterId* **/App/type**  
Gibt den Typ der ID der **App-Id**zurück.

Werttyp ist chr. Unterstützte Vorgang ist Get.

<a href="" id="vpnv2-profilename-trafficfilterlist-trafficfilterid-claims"></a>**VPNv2 /** *Profilname* **/TrafficFilterList/** *trafficFilterId* **/Claims**  
Für künftige Zwecke vorbehalten.

<a href="" id="vpnv2-profilename-trafficfilterlist-trafficfilterid-protocol"></a>**VPNv2 /** *Profilname* **/TrafficFilterList/** *trafficFilterId* **/Protocol**  
Numerische Wert zwischen 0 und 255 das IP-Protokoll zu ermöglichen, die darstellt. Beispielsweise TCP = 6 und UDP = 17.

Werttyp ist int. Unterstützte Vorgänge umfassen Get, hinzufügen, ersetzen und löschen.

<a href="" id="vpnv2-profilename-trafficfilterlist-trafficfilterid-localportranges"></a>**VPNv2 /** *Profilname* **/TrafficFilterList/** *trafficFilterId* **/LocalPortRanges**  
Eine Liste mit durch Kommas getrennte Werte angeben von lokalen Portbereiche zu ermöglichen. Beispielsweise `100-120, 200, 300-320`.

> **Hinweis**  Ports sind nur gültig, wenn das Protokoll auf TCP festgelegt ist = 6 oder UDP = 17.

 

Werttyp ist chr. Unterstützte Vorgänge umfassen Get, hinzufügen, ersetzen und löschen.

<a href="" id="vpnv2-profilename-trafficfilterlist-trafficfilterid-remoteportranges"></a>**VPNv2 /** *Profilname* **/TrafficFilterList/** *trafficFilterId* **/RemotePortRanges**  
Eine Liste mit durch Kommas getrennte Werte angibt remote Portbereiche zu ermöglichen. Beispielsweise `100-120, 200, 300-320`.

> **Hinweis**  Ports sind nur gültig, wenn das Protokoll auf TCP festgelegt ist = 6 oder UDP = 17.

 

Werttyp ist chr. Unterstützte Vorgänge umfassen Get, hinzufügen, ersetzen und löschen.

<a href="" id="vpnv2-profilename-trafficfilterlist-trafficfilterid-localaddressranges"></a>**VPNv2 /** *Profilname* **/TrafficFilterList/** *trafficFilterId* **/LocalAddressRanges**  
Eine Liste mit durch Kommas getrennte Werte angibt lokale IP-Adressbereiche zu ermöglichen.

Werttyp ist chr. Unterstützte Vorgänge umfassen Get, hinzufügen, ersetzen und löschen.

<a href="" id="vpnv2-profilename-trafficfilterlist-trafficfilterid-remoteaddressranges"></a>**VPNv2 /** *Profilname* **/TrafficFilterList/** *trafficFilterId* **/RemoteAddressRanges**  
Eine Liste mit durch Kommas getrennten Werten, die Angabe von remote IP-Adressbereiche zu ermöglichen.

Werttyp ist chr. Unterstützte Vorgänge umfassen Get, hinzufügen, ersetzen und löschen.

<a href="" id="vpnv2-profilename-trafficfilterlist-trafficfilterid-routingpolicytype"></a>**VPNv2 /** *Profilname* **/TrafficFilterList/** *trafficFilterId* **/RoutingPolicyType**  
Gibt die routing-Richtlinie an, ob ein Typ App oder Ansprüche im Datenverkehrsfilter verwendet wird. Der Bereich dieser Eigenschaft ist für diese Datenverkehr Filterregel allein auf. Der Wert kann eine der folgenden sein:

-   SplitTunnel - geht über die Schnittstelle für dieses Datenverkehr Filterregel nur den Datenverkehr bedeutete für VPN-Schnittstelle (wie vom Netzwerk Stack festgelegt). Internet-Datenverkehr kann weiterhin über die anderen Schnittstellen wechseln.
-   ForceTunnel - Regelnamen Datenverkehr, zu denen alle IP-Datenverkehr über die VPN-Schnittstelle wechseln muss.

Dies gilt nur für App-ID Datenverkehr Filterregeln basierte.

Werttyp ist chr. Unterstützte Vorgänge umfassen Get, hinzufügen, ersetzen und löschen.

<a href="" id="vpnv2-profilename-edpmodeid"></a>**VPNv2 /** *Profilname* **/EdpModeId**  
Enterprise-ID, die für das Herstellen einer Verbindung mit diesem VPN-Profil mit einer Richtlinie für den WIP erforderlich ist. Wenn dies festgelegt ist, sieht der Netzwerke-Stapel für diese Enterprise-ID in das app-Token zu ermitteln, ob der Datenverkehr zugelassen ist über VPN. Wenn das Profil aktiv ist, löst die wird auch automatisch die-VPN-Verbindung. Es wird empfohlen, nur eine solche Profil pro Gerät mit.

Darüber hinaus wirksam beim Herstellen einer Verbindung mit Windows Informationen Schutz (WIP) (früher als Enterprise Data Protection bezeichnet), des Administrators keinen Regeln AppTriggerList und TrafficFilterList getrennt in diesem Profil angeben (es sei denn, die erweiterte Konfiguration erforderlich ist) der WIP Richtlinien und App zeigt automatisch.

Werttyp ist chr. Unterstützte Vorgänge umfassen Get, hinzufügen, ersetzen und löschen.

<a href="" id="vpnv2-profilename-remembercredentials"></a>**VPNv2 /** *Profilname* **/RememberCredentials**  
Boolescher Wert (True oder False) zum Zwischenspeichern von Anmeldeinformationen. Standardwert ist "false" können also nicht Zwischenspeichern von Anmeldeinformationen führen. Wenn es sich bei Festlegung auf "true" Anmeldeinformationen nach Möglichkeit zwischengespeichert werden.

Unterstützte Vorgänge umfassen Get, hinzufügen, ersetzen und löschen.

<a href="" id="vpnv2-profilename-alwayson"></a>**VPNv2 /** *Profilname* **/AlwaysOn**  
Eine optionale Kennzeichnung Always On-Modus aktiviert. Dadurch wird das VPN unter-Anmeldung automatisch verbunden und wird in Verbindung bleiben, bis der Benutzer manuell trennt.

> **Hinweis**  Immer auf funktioniert nur für das aktive Profil. Mit geltenden Tunnel werden nicht immer auf festgelegt. Das erste Profil bereitgestellt, das automatisch ausgelöst werden können wird automatisch als aktiv festgelegt.

 

Gültige Werte:

-   False (Standard) - immer auf ist deaktiviert.
-   True - wird immer auf aktiviert.

Werttyp ist Bool. Unterstützte Vorgänge umfassen Get, hinzufügen, ersetzen und löschen.

<a href="" id="vpnv2-profilename-lockdown"></a>**VPNv2 /** *Profilname* **/LockDown**  
Sperrung Profil.

Gültige Werte:

-   False (Standard) – Dies ist kein Sperrfunktionen Profil.
-   True - ist dies ein Profil sperren.

Wenn das Profil Sperrfunktionen aktiviert ist, geschieht Folgendes:

-   Erstens wird es automatisch ein Profil "always on".
-   Zweitens kann es nie getrennt werden.
-   Dritte, wenn das Profil nicht verbunden ist, hat der Benutzer kein Netzwerk.
-   Vierte, keine anderen Profile möglicherweise verbunden oder geändert werden soll.

Ein Profil Sperrfunktionen muss vor dem Hinzufügen, entfernen oder anderen Profilen verbinden gelöscht werden.

Werttyp ist Bool. Unterstützte Vorgänge umfassen Get, hinzufügen, ersetzen und löschen.

<a href="" id="vpnv2-profilename-dnssuffix"></a>**VPNv2 /** *Profilname* **/ DnsSuffix**  
Optional Gibt an, dass eine oder mehrere DNS-Suffixe kommagetrennten. Das erste in der Liste wird auch als primäre Verbindung bestimmte DNS-Suffix für VPN-Schnittstelle verwendet. Die gesamte Liste wird auch in der SuffixSearchList hinzugefügt werden.

Werttyp ist chr. Unterstützte Vorgänge umfassen Get, hinzufügen, ersetzen und löschen.

<a href="" id="vpnv2-profilename-bypassforlocal"></a>**VPNv2 /** *Profilname* **/ByPassForLocal**  
Für künftige Zwecke vorbehalten.

<a href="" id="vpnv2-profilename-trustednetworkdetection"></a>**VPNv2 /** *Profilname* **/TrustedNetworkDetection**  
Optional Durch Kommas getrennte Zeichenfolge zum Identifizieren des vertrauenswürdigen Netzwerks. VPN wird nicht automatisch verbinden, wenn der Benutzer in ihrem Unternehmensnetzwerk drahtlosen ist, auf dem geschützte Ressourcen direkt auf das Gerät zugänglich sind.

Werttyp ist chr. Unterstützte Vorgänge umfassen Get, hinzufügen, ersetzen und löschen.

<a href="" id="vpnv2-profilename-profilexml"></a>**VPNv2 /** *Profilname* **/ProfileXML**  
In Windows 10, Version 1607 hinzugefügt. Das XML-Schema für die Bereitstellung aller Felder eines VPN. Die XSD finden Sie unter [XSD-profileXML gespeichert](vpnv2-profile-xsd.md).

Werttyp ist chr. Unterstützte Vorgänge umfassen Get, hinzufügen, ersetzen und löschen.

<a href="" id="vpnv2-profilename-proxy"></a>**VPNv2 /** *Profilname* **/ Proxy**  
Eine Auflistung von Konfigurationsobjekten So aktivieren Sie einen Proxy-Unterstützung für VPN nach dem herstellen. Der Proxy für dieses Profil definiert wird angewendet, wenn dieses Profil aktiv und verbunden ist.

<a href="" id="vpnv2-profilename-proxy-manual"></a>**VPNv2 /** *Profilname* **/Proxy/Manual**  
Optional-Knotens mit den manuellen servereinstellungen.

<a href="" id="vpnv2-profilename-proxy-manual-server"></a>**VPNv2 /** *Profilname* **/Proxy/Manual/Server**  
Optional Proxyserver-Adresse als einen vollqualifizierten Hostnamen oder eine IP-Adresse. Sie sollten dieses Element zusammen mit Port festlegen. B. proxy.contoso.com.

Werttyp ist chr. Unterstützte Vorgänge umfassen Get, hinzufügen, ersetzen und löschen.

<a href="" id="vpnv2-profilename-proxy-autoconfigurl"></a>**VPNv2 /** *Profilname* **/Proxy/AutoConfigUrl**  
Optional URL, um die Proxyeinstellungen automatisch abzurufen.

Werttyp ist chr. Unterstützte Vorgänge umfassen Get, hinzufügen, ersetzen und löschen.

<a href="" id="vpnv2-profilename-apnbinding"></a>**VPNv2 /** *Profilname* **/APNBinding**  
Für künftige Zwecke vorbehalten.

<a href="" id="vpnv2-profilename-apnbinding-providerid"></a>**VPNv2 /** *Profilname* **/APNBinding/ProviderID**  
Für künftige Zwecke vorbehalten. Optionale Knoten.

<a href="" id="vpnv2-profilename-apnbinding-accesspointname"></a>**VPNv2 /** *Profilname* **/APNBinding/AccessPointName**  
Für künftige Zwecke vorbehalten.

<a href="" id="vpnv2-profilename-apnbinding-username"></a>**VPNv2 /** *Profilname* **/APNBinding/UserName**  
Für künftige Zwecke vorbehalten.

<a href="" id="vpnv2-profilename-apnbinding-password"></a>**VPNv2 /** *Profilname* **/APNBinding/Password**  
Für künftige Zwecke vorbehalten.

<a href="" id="vpnv2-profilename-apnbinding-iscompressionenabled"></a>**VPNv2 /** *Profilname* **/APNBinding/IsCompressionEnabled**  
Für künftige Zwecke vorbehalten.

<a href="" id="vpnv2-profilename-apnbinding-authenticationtype"></a>**VPNv2 /** *Profilname* **/APNBinding/AuthenticationType**  
Für künftige Zwecke vorbehalten.

<a href="" id="vpnv2-profilename-devicecompliance"></a>**VPNv2 /** *Profilname* **/DeviceCompliance**  
In Windows 10, Version 1607 hinzugefügt. Knoten unter DeviceCompliance können verwendet werden, um AAD-basierten bedingte Zugriff für VPN aktivieren.

<a href="" id="vpnv2-profilename-devicecompliance-enabled"></a>**VPNv2 /** *Profilname* **/DeviceCompliance/Enabled**  
In Windows 10, Version 1607 hinzugefügt. Ermöglicht den Gerät Compliance Fluss vom Client. Wenn als True markiert, versucht der VPN-Client zur Kommunikation mit AAD zum Abrufen eines Zertifikats, für die Authentifizierung verwendet. Das VPN sollte Zertifikat Auth verwenden eingerichtet werden, und dem VPN-Server muss den Server von Azure Active Directory zurückgegebene vertrauen.

Werttyp ist Bool. Unterstützte Vorgänge umfassen Get, hinzufügen, ersetzen und löschen.

<a href="" id="vpnv2-profilename-devicecompliance-sso"></a>**VPNv2 /** *Profilname* **/DeviceCompliance/SSO**  
In Windows 10, Version 1607 hinzugefügt. Knoten unter SSO können verwendet werden, ein Zertifikat aus der VPN-Authentifizierungszertifikat andere für die Kerberos-Authentifizierung im Fall von Compliance-Gerät auswählen.

<a href="" id="vpnv2-profilename-devicecompliance-sso-enabled"></a>**VPNv2 /** *Profilname* **/DeviceCompliance/SSO/Enabled**  
In Windows 10, Version 1607 hinzugefügt. Wenn dieses Feld auf True festgelegt ist, wird der VPN-Client für Kerberos-Authentifizierung für ein separates Zertifikat aussehen.

Werttyp ist Bool. Unterstützte Vorgänge umfassen Get, hinzufügen, ersetzen und löschen.

<a href="" id="vpnv2-profilename-devicecompliance-sso-issuerhash"></a>**VPNv2 /** *Profilname* **/DeviceCompliance/SSO/IssuerHash**  
In Windows 10, Version 1607 hinzugefügt. Hashes für den VPN-Client für die Kerberos-Authentifizierung für das richtige Zertifikat zu suchen.

Werttyp ist chr. Unterstützte Vorgänge umfassen Get, hinzufügen, ersetzen und löschen.

<a href="" id="vpnv2-profilename-devicecompliance-sso-eku"></a>**VPNv2 /** *Profilname* **/DeviceCompliance/SSO/EKU**  
In Windows 10, Version 1607 hinzugefügt. Durch Trennzeichen getrenntes Liste EKU für den VPN-Client für die Kerberos-Authentifizierung für das richtige Zertifikat zu suchen.

Werttyp ist chr. Unterstützte Vorgänge umfassen Get, hinzufügen, ersetzen und löschen.

<a href="" id="vpnv2-profilename-pluginprofile"></a>**VPNv2 /** *Profilname* **/PluginProfile**  
VPN-Plug-in-basierte mithilfe einer Windows Store sind Knoten unter der PluginProfile erforderlich.

<a href="" id="vpnv2-profilename-pluginprofile-serverurllist"></a>**VPNv2 /** *Profilname* **/PluginProfile/ServerUrlList**  
Erforderlich für Profile-Plug-in. Durch Trennzeichen getrennte Liste der Server in der URL, Hostname oder IP-Format.

Werttyp ist chr. Unterstützte Vorgänge umfassen Get, hinzufügen, ersetzen und löschen.

<a href="" id="vpnv2-profilename-pluginprofile-customconfiguration"></a>**VPNv2 /** *Profilname* **/PluginProfile/CustomConfiguration**  
Optional Dies ist eine HTML-codierte XML-Blob für SSL-VPN-Plug-in Workflowkonfiguration einschließlich Authentifizierungsinformationen, die an das Gerät zum für SSL-VPN-Plug-ins verfügbar machen bereitgestellt wird. Wenden Sie sich an den Anbieter-Plug-In für Format und andere Details. Die meisten-Plug-Ins können auch Werte auf Grundlage der Server-Aushandlung sowie die Standardeinstellungen konfigurieren.

Werttyp ist chr. Unterstützte Vorgänge umfassen Get, hinzufügen, ersetzen und löschen.

<a href="" id="vpnv2-profilename-pluginprofile-pluginpackagefamilyname"></a>**VPNv2 /** *Profilname* **/PluginProfile/PluginPackageFamilyName**  
Erforderlich für Profile-Plug-in. Name des Pakets-Produktfamilie für das SSL-VPN-Plug-in.

Unterstützte Vorgänge umfassen Get, hinzufügen, ersetzen und löschen.

<a href="" id="vpnv2-profilename-pluginprofile-customstoreurl"></a>**VPNv2 /** *Profilname* **/PluginProfile/CustomStoreUrl**  
Für künftige Zwecke vorbehalten.

<a href="" id="vpnv2-profilename-nativeprofile"></a>**VPNv2 /** *Profilname* **/NativeProfile**  
Knoten unter NativeProfile sind erforderlich, wenn Sie eine Windows Posteingang VPN-Protokoll (IKEv2, PPTP, L2TP) verwenden.

<a href="" id="vpnv2-profilename-nativeprofile-servers"></a>**VPNv2 /** *Profilname* **/NativeProfile/Servers**  
Erforderlich für systemeigene Profile. Öffentliche oder routingfähige IP-Adresse oder DNS-Namen für das VPN-Gateway. Sie können auf die externe IP-Adresse eines Gateways oder eine virtuelle IP-Adresse für eine Serverfarm zeigen. Beispiele, 208.147.66.130 oder vpn.contoso.com.

Werttyp ist chr. Unterstützte Vorgänge umfassen Get, hinzufügen, ersetzen und löschen.

<a href="" id="vpnv2-profilename-nativeprofile-routingpolicytype"></a>**VPNv2 /** *Profilname* **/NativeProfile/RoutingPolicyType**  
Optional für systemeigene Profile. Typ des routing-Richtlinie. Dieser Wert kann eine der folgenden sein:

-   SplitTunnel - gelangen Datenverkehr über jede Schnittstelle vom Netzwerk Stack bestimmt.
-   ForceTunnel - muss alle IP-Datenverkehr über die VPN-Schnittstelle wechseln.

Werttyp ist chr. Unterstützte Vorgänge umfassen Get, hinzufügen, ersetzen und löschen.

<a href="" id="vpnv2-profilename-nativeprofile-nativeprotocoltype"></a>**VPNv2 /** *Profilname* **/NativeProfile/NativeProtocolType**  
Erforderlich für systemeigene Profile. Typ des Tunneling-Protokoll verwendet. Dieser Wert kann eine der folgenden sein:

-   PPTP
-   L2TP
-   IKEv2
-   Automatisch

Werttyp ist chr. Unterstützte Vorgänge umfassen Get, hinzufügen, ersetzen und löschen.

<a href="" id="vpnv2-profilename-nativeprofile-authentication"></a>**VPNv2 /** *Profilname* **/NativeProfile/Authentication**  
Erforderlicher Knoten für systemeigene Profil. Sie enthält Authentifizierungsinformationen für das systemeigene VPN-Profil.

<a href="" id="vpnv2-profilename-nativeprofile-authentication-usermethod"></a>**VPNv2 /** *Profilname* **/NativeProfile/Authentication/UserMethod**  
Dieser Wert kann eine der folgenden sein:

-   EAP
-   MSChapv2 (Dies wird nicht für IKEv2 unterstützt)

Werttyp ist chr. Unterstützte Vorgänge umfassen Get, hinzufügen, ersetzen und löschen.

<a href="" id="vpnv2-profilename-nativeprofile-authentication-machinemethod"></a>**VPNv2 /** *Profilname* **/NativeProfile/Authentication/MachineMethod**  
Dies ist nur in IKEv2 unterstützt.

Dieser Wert kann eine der folgenden sein:

-   Zertifikat

Werttyp ist chr. Unterstützte Vorgänge umfassen Get, hinzufügen, ersetzen und löschen.

<a href="" id="vpnv2-profilename-nativeprofile-authentication-eap"></a>**VPNv2 /** *Profilname* **/NativeProfile/Authentication/EAP**  
Erforderlich, wenn das systemeigene Profil gibt EAP-Authentifizierung an. EAP-Konfigurations-XML.

Unterstützte Vorgänge umfassen Get, hinzufügen, ersetzen und löschen.

<a href="" id="vpnv2-profilename-nativeprofile-authentication-eap-configuration"></a>**VPNv2 /** *Profilname* **/NativeProfile/Authentication/EAP/Configuration**  
HTML-codierte XML-DATEN des EAP-Konfiguration. Weitere Informationen zu EAP-Konfigurations-XML finden Sie unter [EAP-Konfiguration](eap-configuration.md).

Werttyp ist chr. Unterstützte Vorgänge umfassen Get, hinzufügen, ersetzen und löschen.

<a href="" id="vpnv2-profilename-nativeprofile-authentication-eap-type"></a>**VPNv2 /** *Profilname* **/NativeProfile/Authentication/EAP/Type**  
Für künftige Zwecke vorbehalten.

<a href="" id="vpnv2-profilename-nativeprofile-authentication-certificate"></a>**VPNv2 /** *Profilname* **/NativeProfile/Authentication/Certificate**  
Für künftige Zwecke vorbehalten.

<a href="" id="vpnv2-profilename-nativeprofile-authentication-certificate-issuer"></a>**VPNv2 /** *Profilname* **/NativeProfile/Authentication/Certificate/Issuer**  
Für künftige Zwecke vorbehalten.

<a href="" id="vpnv2-profilename-nativeprofile-authentication-certificate-eku"></a>**VPNv2 /** *Profilname* **/NativeProfile/Authentication/Certificate/EKU**  
Für künftige Zwecke vorbehalten.

<a href="" id="vpnv2-profilename-nativeprofile-cryptographysuite"></a>**VPNv2 /** *Profilname* **/NativeProfile/CryptographySuite**  
In Windows 10, Version 1607 hinzugefügt. Eigenschaften der IPSec-Tunnel.

<a href="" id="vpnv2-profilename-nativeprofile-cryptographysuite-authenticationtransformconstants"></a>**VPNv2 /** *Profilname* **/NativeProfile/CryptographySuite/AuthenticationTransformConstants**  
In Windows 10, Version 1607 hinzugefügt.

Die folgende Liste enthält gültige Werte:

-   MD596
-   SHA196
-   SHA256128
-   GCMAES128
-   GCMAES192
-   GCMAES256

Werttyp ist chr. Unterstützte Vorgänge umfassen Get, hinzufügen, ersetzen und löschen.

<a href="" id="vpnv2-profilename-nativeprofile-cryptographysuite-ciphertransformconstants"></a>**VPNv2 /** *Profilname* **/NativeProfile/CryptographySuite/CipherTransformConstants**  
In Windows 10, Version 1607 hinzugefügt.

Die folgende Liste enthält gültige Werte:

-   DES
-   DES3
-   AES128
-   AES192.
-   AES256
-   GCMAES128
-   GCMAES192
-   GCMAES256

Werttyp ist chr. Unterstützte Vorgänge umfassen Get, hinzufügen, ersetzen und löschen.

<a href="" id="vpnv2-profilename-nativeprofile-cryptographysuite-encryptionmethod"></a>**VPNv2 /** *Profilname* **/NativeProfile/CryptographySuite/EncryptionMethod**  
In Windows 10, Version 1607 hinzugefügt.

Die folgende Liste enthält gültige Werte:

-   DES
-   DES3
-   AES128
-   AES192
-   AES256

Werttyp ist chr. Unterstützte Vorgänge umfassen Get, hinzufügen, ersetzen und löschen.

<a href="" id="vpnv2-profilename-nativeprofile-cryptographysuite-integritycheckmethod"></a>**VPNv2 /** *Profilname* **/NativeProfile/CryptographySuite/IntegrityCheckMethod**  
In Windows 10, Version 1607 hinzugefügt.

Die folgende Liste enthält gültige Werte:

-   MD5
-   SHA196
-   SHA256
-   SHA384

Werttyp ist chr. Unterstützte Vorgänge umfassen Get, hinzufügen, ersetzen und löschen.

<a href="" id="vpnv2-profilename-nativeprofile-cryptographysuite-dhgroup"></a>**VPNv2 /** *Profilname* **/NativeProfile/CryptographySuite/DHGroup**  
In Windows 10, Version 1607 hinzugefügt.

Die folgende Liste enthält gültige Werte:

-   Group1
-   Group2
-   Group14
-   ECP256
-   ECP384
-   Group24

Werttyp ist chr. Unterstützte Vorgänge umfassen Get, hinzufügen, ersetzen und löschen.

<a href="" id="vpnv2-profilename-nativeprofile-cryptographysuite-pfsgroup"></a>**VPNv2 /** *Profilname* **/NativeProfile/CryptographySuite/PfsGroup**  
In Windows 10, Version 1607 hinzugefügt.

Die folgende Liste enthält gültige Werte:

-   PFS1
-   PFS2
-   PFS2048
-   ECP256
-   ECP384
-   PFSMM
-   PFS24

Werttyp ist chr. Unterstützte Vorgänge umfassen Get, hinzufügen, ersetzen und löschen.

<a href="" id="vpnv2-profilename-nativeprofile-l2tppsk"></a>**VPNv2 /** *Profilname* **/NativeProfile/L2tpPsk**  
In Windows 10, Version 1607 hinzugefügt. Die vorinstallierten Schlüssel für eine L2TP-Verbindung verwendet.

Werttyp ist chr. Unterstützte Vorgänge umfassen Get, hinzufügen, ersetzen und löschen.

## <a name="examples"></a>Beispiele


Profilbeispiel

``` syntax
<SyncML xmlns="SYNCML:SYNCML1.2" xmlns:A="syncml:metinf">
  <SyncBody>
    <Atomic>
      <CmdID>10000</CmdID>

      <!-- Configure VPN Server Name or Address (PhoneNumber=) [Comma Separated]-->
      <Add>
        <CmdID>10001</CmdID>
        <Item>
          <Target>
            <LocURI>./Vendor/MSFT/VPNv2/VPN_Demo/ProfileXML</LocURI>
          </Target>
          <Data>&lt;VPNProfile&gt;
  &lt;ProfileName&gt;VPN_Demo&lt;/ProfileName&gt;
  &lt;NativeProfile&gt;
    &lt;Servers&gt;VPNServer.contoso.com&lt;/Servers&gt;
    &lt;NativeProtocolType&gt;Automatic&lt;/NativeProtocolType&gt;
    &lt;Authentication&gt;
      &lt;UserMethod&gt;Eap&lt;/UserMethod&gt;
      &lt;Eap&gt;
        &lt;Configuration&gt;
&lt;EapHostConfig xmlns=&quot;http://www.microsoft.com/provisioning/EapHostConfig&quot;&gt; &lt;EapMethod&gt; &lt;Type xmlns=&quot;http://www.microsoft.com/provisioning/EapCommon&quot;&gt;25&lt;/Type&gt; &lt;VendorId xmlns=&quot;http://www.microsoft.com/provisioning/EapCommon&quot;&gt;0&lt;/VendorId&gt; &lt;VendorType xmlns=&quot;http://www.microsoft.com/provisioning/EapCommon&quot;&gt;0&lt;/VendorType&gt; &lt;AuthorId xmlns=&quot;http://www.microsoft.com/provisioning/EapCommon&quot;&gt;0&lt;/AuthorId&gt; &lt;/EapMethod&gt; &lt;Config xmlns=&quot;http://www.microsoft.com/provisioning/EapHostConfig&quot;&gt; &lt;Eap xmlns=&quot;http://www.microsoft.com/provisioning/BaseEapConnectionPropertiesV1&quot;&gt; &lt;Type&gt;25&lt;/Type&gt; &lt;EapType xmlns=&quot;http://www.microsoft.com/provisioning/MsPeapConnectionPropertiesV1&quot;&gt; &lt;ServerValidation&gt; &lt;DisableUserPromptForServerValidation&gt;false&lt;/DisableUserPromptForServerValidation&gt; &lt;ServerNames&gt;&lt;/ServerNames&gt; &lt;/ServerValidation&gt; &lt;FastReconnect&gt;true&lt;/FastReconnect&gt; &lt;InnerEapOptional&gt;false&lt;/InnerEapOptional&gt; &lt;Eap xmlns=&quot;http://www.microsoft.com/provisioning/BaseEapConnectionPropertiesV1&quot;&gt; &lt;Type&gt;13&lt;/Type&gt; &lt;EapType xmlns=&quot;http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV1&quot;&gt; &lt;CredentialsSource&gt; &lt;CertificateStore&gt; &lt;SimpleCertSelection&gt;false&lt;/SimpleCertSelection&gt; &lt;/CertificateStore&gt; &lt;/CredentialsSource&gt; &lt;ServerValidation&gt; &lt;DisableUserPromptForServerValidation&gt;false&lt;/DisableUserPromptForServerValidation&gt; &lt;ServerNames&gt;&lt;/ServerNames&gt; &lt;/ServerValidation&gt; &lt;DifferentUsername&gt;false&lt;/DifferentUsername&gt; &lt;PerformServerValidation xmlns=&quot;http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2&quot;&gt;false&lt;/PerformServerValidation&gt; &lt;AcceptServerName xmlns=&quot;http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2&quot;&gt;false&lt;/AcceptServerName&gt; &lt;TLSExtensions xmlns=&quot;http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2&quot;&gt; &lt;FilteringInfo xmlns=&quot;http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV3&quot;&gt; &lt;EKUMapping&gt; &lt;EKUMap&gt; &lt;EKUName&gt;Unknown Key Usage&lt;/EKUName&gt; &lt;EKUOID&gt;1.3.6.1.4.1.311.87&lt;/EKUOID&gt; &lt;/EKUMap&gt; &lt;/EKUMapping&gt; &lt;ClientAuthEKUList Enabled=&quot;true&quot;&gt; &lt;EKUMapInList&gt; &lt;EKUName&gt;Unknown Key Usage&lt;/EKUName&gt; &lt;/EKUMapInList&gt; &lt;/ClientAuthEKUList&gt; &lt;/FilteringInfo&gt; &lt;/TLSExtensions&gt; &lt;/EapType&gt; &lt;/Eap&gt; &lt;EnableQuarantineChecks&gt;false&lt;/EnableQuarantineChecks&gt; &lt;RequireCryptoBinding&gt;false&lt;/RequireCryptoBinding&gt; &lt;PeapExtensions&gt; &lt;PerformServerValidation xmlns=&quot;http://www.microsoft.com/provisioning/MsPeapConnectionPropertiesV2&quot;&gt;false&lt;/PerformServerValidation&gt; &lt;AcceptServerName xmlns=&quot;http://www.microsoft.com/provisioning/MsPeapConnectionPropertiesV2&quot;&gt;false&lt;/AcceptServerName&gt; &lt;/PeapExtensions&gt; &lt;/EapType&gt; &lt;/Eap&gt; &lt;/Config&gt; &lt;/EapHostConfig&gt;
    &lt;/Configuration&gt;
      &lt;/Eap&gt;
    &lt;/Authentication&gt;
    &lt;RoutingPolicyType&gt;SplitTunnel&lt;/RoutingPolicyType&gt;
  &lt;/NativeProfile&gt;
  &lt;DomainNameInformation&gt;
    &lt;DomainName&gt;.contoso.com&lt;/DomainName&gt;
    &lt;DNSServers&gt;10.5.5.5&lt;/DNSServers&gt;
  &lt;/DomainNameInformation&gt;
 &lt;TrafficFilter&gt;  
    &lt;App&gt;%ProgramFiles%\Internet Explorer\iexplore.exe&lt;/App&gt; 
  &lt;/TrafficFilter&gt; 
  &lt;TrafficFilter&gt;  
    &lt;App&gt;Microsoft.MicrosoftEdge_8wekyb3d8bbwe&lt;/App&gt;  
  &lt;/TrafficFilter&gt;
  &lt;Route&gt;
    &lt;Address&gt;10.0.0.0&lt;/Address&gt;
    &lt;PrefixSize&gt;8&lt;/PrefixSize&gt;
  &lt;/Route&gt;
  &lt;Route&gt;
    &lt;Address&gt;25.0.0.0&lt;/Address&gt;
    &lt;PrefixSize&gt;8&lt;/PrefixSize&gt;
  &lt;/Route&gt;
    &lt;RememberCredentials&gt;true&lt;/RememberCredentials&gt;
  &lt;/VPNProfile&gt;</Data>
        </Item>
      </Add>

    </Atomic>
    <Final/>
  </SyncBody>
</SyncML>
```

AppTriggerList

``` syntax
<!-- Internet Explorer -->
      <Add>
        <CmdID>10013</CmdID>
        <Item>
          <Target>
            <LocURI>./Vendor/MSFT/VPNv2/VPNProfileName/AppTriggerList/0/App/Id</LocURI>
          </Target>
          <Data>%PROGRAMFILES%\Internet Explorer\iexplore.exe</Data>
        </Item>
      </Add>
      <Add>
        <CmdID>10014</CmdID>
        <Item>
          <Target>
            <LocURI>./Vendor/MSFT/VPNv2/VPNProfileName/AppTriggerList/1/App/Id</LocURI>
          </Target>
          <Data>%PROGRAMFILES% (x86)\Internet Explorer\iexplore.exe</Data>
        </Item>
      </Add>
      <!-- Edge -->
      <Add>
        <CmdID>10015</CmdID>
        <Item>
          <Target>
            <LocURI>./Vendor/MSFT/VPNv2/VPNProfileName/AppTriggerList/2/App/Id</LocURI>
          </Target>
          <Data>Microsoft.MicrosoftEdge_8wekyb3d8bbwe</Data>
        </Item>
      </Add>
```

RouteList und ExclusionRoute

``` syntax
 
     <Add>
        <CmdID>10008</CmdID>
        <Item>
          <Target>
           <LocURI>./Vendor/MSFT/VPNv2/VPNProfileName/RouteList/0/Address</LocURI>
          </Target>
          <Data>192.168.0.0</Data>
        </Item>
      </Add>
      <Add>
        <CmdID>10009</CmdID>
        <Item>
          <Target>
            <LocURI>./Vendor/MSFT/VPNv2/VPNProfileName/RouteList/0/PrefixSize</LocURI>
          </Target>
          <Meta>
            <Format xmlns="syncml:metinf">int</Format>
          </Meta>
          <Data>24</Data>
        </Item>
      </Add>
      <Add>
        <CmdID>10010</CmdID>
        <Item>
          <Target>
            <LocURI>./Vendor/MSFT/VPNv2/VPNProfileName/RouteList/0/ExclusionRoute</LocURI>
          </Target>
          <Meta>
            <Format xmlns="syncml:metinf">bool</Format>
          </Meta>
          <Data>true</Data>
        </Item>
      </Add>
 
```

DomainNameInformationList

``` syntax
 
      <!-- Domain Name rule with Suffix Match with DNS Servers -->
      <Add>
        <CmdID>10013</CmdID>
        <Item>
          <Target>
            <LocURI>./Vendor/MSFT/VPNv2/VPNProfileName/DomainNameInformationList/0/DomainName</LocURI>  
          </Target>
          <Data>.contoso.com</Data>
        </Item>
      </Add>
      <Add>
        <CmdID>10014</CmdID>
        <Item>
          <Target>
            <LocURI>./Vendor/MSFT/VPNv2/VPNProfileName/DomainNameInformationList/0/DnsServers</LocURI>  
          </Target>
          <Data>192.168.0.11,192.168.0.12</Data>
        </Item>
      </Add>
 
<!-- Domain Name rule with Suffix Match with Web Proxy -->
      <Add>
        <CmdID>10013</CmdID>
        <Item>
          <Target>
            <LocURI>./Vendor/MSFT/VPNv2/VPNProfileName/DomainNameInformationList/1/DomainName</LocURI>  
          </Target>
          <Data>.contoso.com</Data>
        </Item>
      </Add>
 
      <Add>
        <CmdID>10015</CmdID>
        <Item>
          <Target>
<LocURI>./Vendor/MSFT/VPNv2/VPNProfileName/DomainNameInformationList/1/WebProxyServers</LocURI>  
          </Target>
          <Data>192.168.0.100:8888</Data>
        </Item>
      </Add>
 
<!-- Domain Name rule with FQDN Match with DNS Servers -->
 
      <Add>
        <CmdID>10016</CmdID>
        <Item>
          <Target>
            <LocURI>./Vendor/MSFT/VPNv2/VPNProfileName/DomainNameInformationList/2/DomainName</LocURI>  
          </Target>
          <Data>finance.contoso.com</Data>
        </Item>
      </Add>
      <Add>
        <CmdID>10017</CmdID>
        <Item>
          <Target>
            <LocURI>./Vendor/MSFT/VPNv2/VPNProfileName/DomainNameInformationList/2/DnsServers</LocURI>  
          </Target>
          <Data>192.168.0.11,192.168.0.12</Data>
        </Item>
      </Add>
 
<!-- Domain Name rule with FQDN Match with Proxy Server -->
 
      <Add>
        <CmdID>10016</CmdID>
        <Item>
          <Target>
            <LocURI>./Vendor/MSFT/VPNv2/VPNProfileName/DomainNameInformationList/3/DomainName</LocURI>  
          </Target>
          <Data>finance.contoso.com</Data>
        </Item>
      </Add>
      <Add>
        <CmdID>10017</CmdID>
        <Item>
          <Target>
            <LocURI>./Vendor/MSFT/VPNv2/VPNProfileName/DomainNameInformationList/3/WebProxyServers</LocURI>  
          </Target>
          <Data>192.168.0.11:8080</Data>
        </Item>
      </Add>
 
<!-- Domain Name rule for all other (any) traffic through DNS Servers -->
      <Add>
        <CmdID>10016</CmdID>
        <Item>
          <Target>
            <LocURI>./Vendor/MSFT/VPNv2/VPNProfileName/DomainNameInformationList/4/DomainName</LocURI>  
          </Target>
          <Data>.</Data>
        </Item>
      </Add>
      <Add>
        <CmdID>10017</CmdID>
        <Item>
          <Target>
            <LocURI>./Vendor/MSFT/VPNv2/VPNProfileName/DomainNameInformationList/4/DnsServers</LocURI>  
          </Target>
          <Data>192.168.0.11,192.168.0.12</Data>
        </Item>
      </Add>
 
<!-- Domain Name rule for all other (any) traffic through Proxy -->
 
      <Add>
        <CmdID>10016</CmdID>
        <Item>
          <Target>
            <LocURI>./Vendor/MSFT/VPNv2/VPNProfileName/DomainNameInformationList/5/DomainName</LocURI>  
          </Target>
          <Data>.</Data>
        </Item>
      </Add>
      <Add>
        <CmdID>10017</CmdID>
        <Item>
          <Target>
            <LocURI>./Vendor/MSFT/VPNv2/VPNProfileName/DomainNameInformationList/5/WebProxyServers</LocURI>  
          </Target>
          <Data>192.168.0.11</Data>
        </Item>
      </Add>
```

AutoTrigger

``` syntax
<Add>
        <CmdID>10010</CmdID>
        <Item>
          <Target>
            <LocURI>./Vendor/MSFT/VPNv2/VPNProfileName/DomainNameInformationList/0/AutoTrigger</LocURI>
          </Target>
          <Meta>
            <Format xmlns="syncml:metinf">bool</Format>
          </Meta>
          <Data>true</Data>
        </Item>
      </Add>
```

Persistent

``` syntax
<Add>
        <CmdID>10010</CmdID>
        <Item>
          <Target>
            <LocURI>./Vendor/MSFT/VPNv2/VPNProfileName/DomainNameInformationList/1/Persistent</LocURI>
          </Target>
          <Meta>
            <Format xmlns="syncml:metinf">bool</Format>
          </Meta>
          <Data>true</Data>
        </Item>
      </Add>
```

TrafficFilterLIst-App

``` syntax
  Desktop App
    <Add>
        <CmdID>10013</CmdID>
        <Item>
          <Target>
            <LocURI>./Vendor/MSFT/VPNv2/VPNProfileName/TrafficFilterList/0/App/Id</LocURI>
          </Target>
          <Data>%ProgramFiles%\Internet Explorer\iexplore.exe</Data>
        </Item>
      </Add>
  Store App
      <Add>
        <CmdID>10014</CmdID>
        <Item>
          <Target>
            <LocURI>./Vendor/MSFT/VPNv2/VPNProfileName/TrafficFilterList/1/App/Id</LocURI>  
          </Target>
          <Data>Microsoft.MicrosoftEdge_8wekyb3d8bbwe</Data>
        </Item>
      </Add>
  SYSTEM
      <Add>
        <CmdID>10015</CmdID>
        <Item>
          <Target>
            <LocURI>./Vendor/MSFT/VPNv2/VPNProfileName/TrafficFilterList/3/App/Id</LocURI>  
          </Target>
          <Data>SYSTEM</Data>
        </Item>
      </Add>
```

LocalPortRanges, RemotePortRanges, LocalAddressRanges, RemoteAddressRanges, RoutingPolicyType, EDPModeId, RememberCredentials, AlwaysOn, Sperrfunktionen, DnsSuffix, TrustedNetworkDetection-Protokoll

``` syntax
Protocol
      <Add>
        <CmdID>$CmdID$</CmdID>
        <Item>
          <Target>
            <LocURI>./Vendor/MSFT/VPNv2/VPNProfileName/TrafficFilterList/3/Protocol</LocURI>  
          </Target>
          <Meta>
            <Format xmlns="syncml:metinf">int</Format>
          </Meta>
          <Data>6</Data>
        </Item>
      </Add>
  LocalPortRanges
      <Add>
        <CmdID>$CmdID$</CmdID>
        <Item>
          <Target>
            <LocURI>./Vendor/MSFT/VPNv2/VPNProfileName/TrafficFilterList/3/LocalPortRanges</LocURI>  
          </Target>
          <Data>10,20-50,100-200</Data>
        </Item>
      </Add>
 
  RemotePortRanges
      <Add>
        <CmdID>$CmdID$</CmdID>
        <Item>
          <Target>
            <LocURI>./Vendor/MSFT/VPNv2/VPNProfileName/TrafficFilterList/3/RemotePortRanges</LocURI>  
          </Target>
          <Data>20-50,100-200,300</Data>
        </Item>
      </Add>
 
  LocalAddressRanges
      <Add>
        <CmdID>$CmdID$</CmdID>
        <Item>
          <Target>
            <LocURI>./Vendor/MSFT/VPNv2/VPNProfileName/TrafficFilterList/3/LocalAddressRanges/LocURI>  
          </Target>
          <Data>3.3.3.3/32,1.1.1.1-2.2.2.2</Data>
        </Item>
      </Add>
 
  RemoteAddressRanges
      <Add>
        <CmdID>$CmdID$</CmdID>
        <Item>
          <Target>
            <LocURI>./Vendor/MSFT/VPNv2/VPNProfileName/TrafficFilterList/3/RemoteAddressRanges</LocURI>  
          </Target>
          <Data>30.30.0.0/16,10.10.10.10-20.20.20.20</Data>
        </Item>
      </Add>
 
  RoutingPolicyType
<Add>
        <CmdID>$CmdID$</CmdID>
        <Item>
          <Target>
            <LocURI>./Vendor/MSFT/VPNv2/VPNProfileName/TrafficFilterList/0/RoutingPolicyType</LocURI>
          </Target>
          <Data>ForceTunnel</Data>
        </Item>
      </Add>
 
  EDPModeId
    <Add>
      <CmdID>$CmdID$</CmdID>
      <Item>
        <Target>
          <LocURI>./Vendor/MSFT/VPNv2/VPNProfileName/EDPModeID</LocURI>
        </Target>
        <Data>corp.contoso.com</Data>
      </Item>
    </Add>
 
  RememberCredentials
<Add>
        <CmdID>$CmdID$</CmdID>
        <Item>
          <Target>
            <LocURI>./Vendor/MSFT/VPNv2/VPNProfileName/RememberCredentials</LocURI>
          </Target>
          <Meta>
            <Format xmlns="syncml:metinf">bool</Format>
          </Meta>
          <Data>true</Data>
        </Item>
      </Add>
 
  AlwaysOn
      <Add>
        <CmdID>$CmdID$</CmdID>
        <Item>
          <Target>
            <LocURI>./Vendor/MSFT/VPNv2/VPNProfileName/AlwaysOn</LocURI>
          </Target>
          <Meta>
            <Format xmlns="syncml:metinf">bool</Format>
          </Meta>
          <Data>true</Data>
        </Item>
      </Add>
 
  Lockdown
<Add>
        <CmdID>$CmdID$</CmdID>
        <Item>
          <Target>
            <LocURI>./Vendor/MSFT/VPNv2/VPNProfileName/Lockdown</LocURI>
          </Target>
          <Meta>
            <Format xmlns="syncml:metinf">bool</Format>
          </Meta>
          <Data>true</Data>
        </Item>
      </Add>
 
  DnsSuffix
      <Add>
        <CmdID>$CmdID$</CmdID>
        <Item>
          <Target>
            <LocURI>./Vendor/MSFT/VPNv2/VPNProfileName/DnsSuffix</LocURI>
          </Target>
          <Data>Adatum.com</Data>
        </Item>
      </Add>
 
  TrustedNetworkDetection
     <!-- Configure Trusted Networks (TrustedNetworks=) [Comma separated] -->
      <Add>
        <CmdID>$CmdID$</CmdID>
        <Item>
          <Target>
            <LocURI>./Vendor/MSFT/VPNv2/VPNProfileName/TrustedNetworkDetection</LocURI>
          </Target>
          <Data>Adatum.com</Data>
        </Item>
      </Add>
```

Proxy - Handbuch oder AutoConfigUrl

``` syntax
Manual
      <Add>
        <CmdID>$CmdID$</CmdID>
        <Item>
          <Target>
            <LocURI>./Vendor/MSFT/VPNv2/VPNProfileName/Proxy/Manual/Server</LocURI>
          </Target>
          <Data>192.168.0.100:8888</Data>
        </Item>
      </Add>
 
  AutoConfigUrl
      <Add>
        <CmdID>$CmdID$</CmdID>
        <Item>
          <Target>
            <LocURI>./Vendor/MSFT/VPNv2/VPNProfileName/Proxy/AutoConfigUrl</LocURI>
          </Target>
          <Data>HelloWorld.com</Data>
        </Item>
      </Add>
```

Gerät Compliance - Sso

``` syntax
  Enabled
<Add>
        <CmdID>10011</CmdID>
        <Item>
          <Target>
            <LocURI>./Vendor/MSFT/VPNv2/VPNProfileName/DeviceCompliance/SSO/Enabled</LocURI>
          </Target>
          <Meta>
            <Format xmlns="syncml:metinf">bool</Format>
          </Meta>
          <Data>true</Data>
        </Item>
      </Add>
 
  IssuerHash
<Add>
        <CmdID>10011</CmdID>
        <Item>
          <Target>
            <LocURI>./Vendor/MSFT/VPNv2/VPNProfileName/DeviceCompliance/SSO/IssuerHash</LocURI>
          </Target>
          <Data>ffffffffffffffffffffffffffffffffffffffff;ffffffffffffffffffffffffffffffffffffffee</Data>
        </Item>
      </Add>
 
  Eku
<Add>
        <CmdID>10011</CmdID>
        <Item>
          <Target>
            <LocURI>./Vendor/MSFT/VPNv2/VPNProfileName/DeviceCompliance/SSO/EKU</LocURI>
          </Target>
          <Data>1.3.6.1.5.5.7.3.2</Data>
        </Item>
      </Add>
```

PluginProfile

``` syntax
PluginPackageFamilyName
      <!-- Configure VPN Server Name or Address (PhoneNumber=) [Comma Separated]-->
      <Add>
        <CmdID>10001</CmdID>
        <Item>
          <Target>
            <LocURI>./Vendor/MSFT/VPNv2/VPNProfileName/PluginProfile/ServerUrlList</LocURI>
          </Target>
          <Data>selfhost.corp.contoso.com</Data>
        </Item>
      </Add>
 
      <!-- Configure VPN Plugin AppX Package ID (ThirdPartyProfileInfo=) -->
      <Add>
        <CmdID>10002</CmdID>
        <Item>
          <Target>
            <LocURI>./Vendor/MSFT/VPNv2/VPNProfileName/PluginProfile/PluginPackageFamilyName</LocURI>
          </Target>
          <Data>TestVpnPluginApp-SL_8wekyb3d8bbwe</Data>
        </Item>
      </Add>
 
      <!-- Configure Microsoft's Custom XML (ThirdPartyProfileInfo=) -->
      <Add>
        <CmdID>10003</CmdID>
        <Item>
          <Target>
            <LocURI>./Vendor/MSFT/VPNv2/VPNProfileName/PluginProfile/CustomConfiguration</LocURI>
          </Target>
          <Data>&lt;pluginschema&gt;&lt;ipAddress&gt;auto&lt;/ipAddress&gt;&lt;port&gt;443&lt;/port&gt;&lt;networksettings&gt;&lt;routes&gt;&lt;includev4&gt;&lt;route&gt;&lt;address&gt;172.10.10.0&lt;/address&gt;&lt;prefix&gt;24&lt;/prefix&gt;&lt;/route&gt;&lt;/includev4&gt;&lt;/routes&gt;&lt;namespaces&gt;&lt;namespace&gt;&lt;space&gt;.vpnbackend.com&lt;/space&gt;&lt;dnsservers&gt;&lt;server&gt;172.10.10.11&lt;/server&gt;&lt;/dnsservers&gt;&lt;/namespace&gt;&lt;/namespaces&gt;&lt;/networksettings&gt;&lt;/pluginschema&gt;</Data>
        </Item>
      </Add>
```

NativeProfile

``` syntax
Servers
<Add>
        <CmdID>10001</CmdID>
        <Item>
          <Target>
            <LocURI>./Vendor/MSFT/VPNv2/VPNProfileName/NativeProfile/Servers</LocURI>
          </Target>
          <Data>Selfhost.corp.contoso.com</Data>
        </Item>
      </Add>
 
  RoutingPolicyType
      <Add>
        <CmdID>10007</CmdID>
        <Item>
          <Target>
            <LocURI>./Vendor/MSFT/VPNv2/VPNProfileName/NativeProfile/RoutingPolicyType</LocURI>
          </Target>
          <Data>ForceTunnel</Data>
        </Item>
      </Add>
 
  NativeProtocolType
    <!-- Configure VPN Protocol Type (L2tp, Pptp, Ikev2) -->
      <Add>
        <CmdID>10002</CmdID>
        <Item>
          <Target>
            <LocURI>./Vendor/MSFT/VPNv2/VPNProfileName/NativeProfile/NativeProtocolType</LocURI>
          </Target>
          <Data>Automatic</Data>
        </Item>
      </Add>
 
  Authentication
  UserMethod
      <!-- Configure VPN User Method (Mschapv2, Eap) -->
      <Add>
        <CmdID>10003</CmdID>
        <Item>
          <Target>
            <LocURI>./Vendor/MSFT/VPNv2/VPNProfileName/NativeProfile/Authentication/UserMethod</LocURI>
          </Target>
          <Data>Eap</Data>
        </Item>
      </Add>
 
  MachineMethod
      <!-- Configure VPN Machine Method (Certificate, Eap, PresharedKey) -->
      <Add>
        <CmdID>10004</CmdID>
        <Item>
         <Target>
            <LocURI>./Vendor/MSFT/VPNv2/VPNProfileName/NativeProfile/Authentication/MachineMethod</LocURI>
          </Target>
          <Data>Eap</Data>
        </Item>
      </Add>
 
  CryptographySuite
        <Add>
        <CmdID>10004</CmdID>
        <Item>
          <Target>
            <LocURI>./Vendor/MSFT/VPNv2/VPNProfileName/NativeProfile/Authentication/CryptographySuite/AuthenticationTransformConstants</LocURI>
          </Target>
          <Data>SHA196</Data>
        </Item>
      </Add>
      <Add>
        <CmdID>10004</CmdID>
        <Item>
          <Target>
            <LocURI>./Vendor/MSFT/VPNv2/VPNProfileName/NativeProfile/Authentication/CryptographySuite/CipherTransformConstants</LocURI>
          </Target>
          <Data>AES192</Data>
        </Item>
      </Add>
      <Add>
        <CmdID>10004</CmdID>
        <Item>
          <Target>
            <LocURI>./Vendor/MSFT/VPNv2/VPNProfileName/NativeProfile/Authentication/CryptographySuite/EncryptionMethod</LocURI>
          </Target>
          <Data>PFS2048</Data>
        </Item>
      </Add>
      <Add>
        <CmdID>10004</CmdID>
        <Item>
          <Target>
            <LocURI>./Vendor/MSFT/VPNv2/VPNProfileName/NativeProfile/Authentication/CryptographySuite/IntegrityCheckMethod</LocURI>
          </Target>
          <Data>Eap</Data>
        </Item>
      </Add>
      <Add>
        <CmdID>Group14</CmdID>
        <Item>
          <Target>
            <LocURI>./Vendor/MSFT/VPNv2/VPNProfileName/NativeProfile/Authentication/CryptographySuite/DHGroup</LocURI>
          </Target>
          <Data>SHA256</Data>
        </Item>
     </Add>
      <Add>
        <CmdID>10004</CmdID>
        <Item>
          <Target>
            <LocURI>./Vendor/MSFT/VPNv2/VPNProfileName/NativeProfile/Authentication/CryptographySuite/PfsGroup</LocURI>
          </Target>
          <Data>AES128</Data>
        </Item>
      </Add>
   
  DisableClassBasedDefaultRoute 
        <CmdID>10011</CmdID>
        <Item>
          <Target>
            <LocURI>./Vendor/MSFT/VPNv2/VPNProfileName/NativeProfile/DisableClassBasedDefaultRoute</LocURI>
          </Target>
          <Meta>
            <Format xmlns="syncml:metinf">bool</Format>
          </Meta>
          <Data>true</Data>
        </Item>
      </Add>
```

## <a name="related-topics"></a>Verwandte Themen


[Konfiguration Dienstverweis-Anbieter](configuration-service-provider-reference.md)

 

 






