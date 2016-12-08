---
title: Device.Network.Switch.AzureStack
Description: Requirements.
ms.assetid: 
MSHAttr: 
author: beneluxboy
ms.openlocfilehash: cf99e469935f2283c32c795f473765f51ecde98e
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
## <a name="devicenetworkswitchazurestack"></a>Device.Network.Switch.AzureStack

*Anforderungen für die Netzwerk-Switches, die in Microsoft Azure-Stapel verwendet basierte private Cloudlösungen*

<a name="device.network.switch.azurestack.basicfunction"></a>
### <a name="devicenetworkswitchazurestackbasicfunction"></a>Device.Network.Switch.AzureStack.BasicFunction

*Mindestanforderungen für Netzwerkswitches in Microsoft Azure-Stapel Lösungen verwendet*

<table><tr><td>Gilt für</td><td>Windows Server 2016 X64</td></tr></table>

**Beschreibung**

Eine Microsoft Azure-Stapel-Lösung für eine private Cloud muss Anforderungen für die physische Switch-Infrastruktur erfüllen. In diesem Abschnitt werden die Anforderungen aufgelistet. 

Die Microsoft Azure-Stapel-Netzwerken zu Hause wird eine rücken/Endknoten ALL Netzwerkkonfiguration für Flexibilität und einem festen Maßstab vorausgesetzt: 

- Die Endknoten-Switches bieten die Verbindung mit den Servern Compute und Speicherung in Microsoft Azure-Stapel-Lösung. 
- Die Achse Switches bieten Konnektivität zwischen anderen Endknoten Switches und Verbindung mit einem Kunden Netzwerkgeräte Rahmen.

Diese Rücken und Endknoten Switches müssen Layer 3 (L3), IP-Ebene-Konnektivität in Form von routing/Weiterleitung und Border Gateway Protocol (BGP) Unterstützung bieten.

HINWEIS: Die Details der physischen und logischen Konfiguration liegen außerhalb des Bereichs dieser Anforderungen Enumeration und werden in "Architektur gegen Microsoft Azure-Stapel" enthalten sein.

Neben die Anforderungen aufgelistet, die unter Microsoft Azure-Stapel müssen die Anforderungen zum Überprüfen von NIC und physischen Switches, um sicherzustellen, RDMA konfiguriert und ordnungsgemäß weitergeleitet.

**Anforderungen**

In der folgenden Tabelle werden physische Switch Anforderungen an die Netzwerkinfrastruktur für eine Private Cloud-Lösung Microsoft Azure-Stapel erfasst.

<table>
    <tr><th>Feature</th><th>Anforderung</th><th>Microsoft Azure-Stapel-Zertifizierung</th></tr>
    <tr><td rowspan="2">Device.Network.Switch.Manageability</td><td>Device.Network.Switch.Manageability.NetworkSwitchProfile</td><td>Wenn implementiert</td></tr>
    <tr><td>Device.Network.Switch.Manageability.NetworkSwitchProfileView</td><td>Wenn implementiert</td></tr>
</table>

Die folgenden Tabellen beschreiben die Richtungspfeile Auffassung von Microsoft Azure-Stapel Switch Anforderungen.

<table>
    <tr><th colspan="2">SWITCH-MERKMALE</th><th>Microsoft Azure-Stapel-Zertifizierung (engl.)</th></tr>
    <tr><td>OSI Layer-Unterstützung</td><td>L2 & L3 wechseln auf alle Ports</td><td>Erforderlich</td></tr>
    <tr><td>Übertragungsrate</td><td><p>Access-Befehlszeilenoption/Compute-Knoten: Mindestens 10 Gb-Ethernet-</p><p>Aggregierte Switch-Zugriff Schalter: Mindestens 10 Gb-Ethernet-</p></td><td>Erforderlich</td></tr>
    <tr><td>Durchsatz an Datenverkehr</td><td>Rate der Zeile für den L2 und L3 Datenverkehr an alle ports</td><td>Erforderlich</td></tr>
    <tr><td>Port-Funktionen</td><td>L2 und L3 wechseln auf alle Ports</td><td>Erforderlich</td></tr>
    <tr><td>Reagieren auf Protokolle</td>
        <td><p>Sowohl IPv4 als auch IPv6-Datenverkehr muss unterstützt werden.</p> 
            <p>IPv6-Unterstützung für Anweisungen MUSS in der folgenden IETF-Standards ist erforderlich:</p>
            <ul>
                <li>RFC 2460: "Internet Protocol, Version 6 (IPv6)"</li>
                <li>RFC 2461: "benachbarten Discovery for IP Version 6 (IPv6)"</li>
                <li>RFC 2462: "IPv6 automatische Konfiguration"</li>
                <li>RFC 2463: "Internet Control Message-Protokoll (ICMPv6) für das Internetprotokoll, Version 6 (IPv6) Spezifikation."</li></ul>
            <p>Switches müssen mindestens 12.000 IPv6-Host-Routen unterstützen.</p></td>
            <td>Erforderlich</td></tr>
</table>

<table>
    <tr><th colspan="2">ROUTING UND UMSCHALTEN</th><th>Microsoft Azure-Stapel-Zertifizierung (engl.)</th></tr>
    <tr><td>L3-Protokolle</td>
        <td><p>ECMP</p>
            <p>BGP (IETF RFC 4271)-basierte ECMP: derzeit BGP für Fehlertoleranz zwischen Access Switches und Aggregation Switches verwendet wird.</p>
            <p>Implementierungen sollte die Anweisungen MUSS in der folgenden IETF-Standards unterstützen:</p>
            <ul>
                <li>RFC 2545: "BGP-4 Multiprotocol Durchwahlnummern für IPv6 Inter-Domain Routing"</li>
                <li>RFC 4760: "Multiprotocol Durchwahlnummern für BGP-4"</li>
                <li>RFC 4893: "BGP-Unterstützung für 4-Byte-AS Number Speicherplatz"</li>
                <li>RFC 4456: "BGP Route Reflektion: Alternative voll Mesh interne BGP (Protokoll)"</li>
                <li>RFC 4724: "Mechanismus für BGP ordnungsgemäß neu starten"</li></ul></td>
            <td>Erforderlich</td></tr>
    <tr><td>L2-Protokolle</td><td>LLDP</td><td>Erforderlich</td></tr>
    <tr><td>Überlagerung Protokolle</td><td>VLAN – die Isolierung von verschiedenen Typen von Datenverkehr.</td><td>Erforderlich</td></tr>
    <tr><td></td><td>802.1Q Trunk</td><td>Erforderlich</td></tr>
    <tr><td>Filtern von Datenverkehr</td><td>Benötigen Sie eine Mindestanzahl von ACLS oder VRF Unterstützung</td><td>Erforderlich</td></tr>
</table>

<table>
    <tr><th colspan="2">LINK-STEUERELEMENT</th><th>Microsoft Azure-Stapel-Zertifizierung (engl.)</th></tr>
    <tr><td>Dienstqualität</td>
        <td><p>Verbesserte Datenverkehr-Auswahl (802.1Qaz)</p>
            <p>Priorität Based Ablauf Access Control (802.1 p/F und 802.1Qbb)</p></td>
        <td>Erforderlich</td></tr>
</table>

<table>
    <tr><th colspan="2">VERFÜGBARKEIT UND REDUNDANZ</th><th>Microsoft Azure-Stapel-Zertifizierung (engl.)</th></tr>
    <tr><td>Wechseln der Verfügbarkeit</td><td>Link-Aggregation in Verbindung mit NIC-teaming mit mehreren Chassis</td><td>Erforderlich</td></tr>
    <tr><td></td><td>VRRP [vorausgesetzt, dass Switches stapelbare werden oder dass der Router hoher Verfügbarkeit ist]</td><td>Erforderlich</td></tr>
</table>

<table>
    <tr><th colspan="2">VERWALTUNG</th><th>Microsoft Azure-Stapel-Zertifizierung (engl.)</th></tr>
    <tr><td>Start-Boot</td><td>Starten, Hochfahren und Vorgänge fortgesetzt werden ohne Eingreifen des einer Netzwerk-Switch-Administrator.</td><td>Erforderlich</td></tr>
    <tr><td>Überwachung</td><td>SNMP-v1or SNMP-v2</td><td>Erforderlich</td></tr>
    <tr><td>SNMP-MIBs</td><td>MIB-II (RFC 1213), LLDP, Schnittstelle MIB (RFC 2863), IF-MIB, IP-MIB, IP-FORWARD-MIB, Q-BRÜCKE-MIB, BRIDGE-MIB, LLDB-MIB, Entität MIB, IEEE8023-LAG-MIB</td><td>Erforderlich</td></tr>
    <tr><td>Ablauf, Überwachung</td><td><p>Port-Spiegelung</p><p>IPFIX</p></td><td>Wenn implementiert</td></tr>
    <tr><td>Ereignisse-Protokollierung</td><td>Syslog (für Ereignisse und Erkennung ändern)</td><td>Wenn implementiert</td></tr>
    <tr><td></td><td>Traps (Gerät muss mehrere Trapping Ziele unterstützen.)</td><td>Erforderlich</td></tr>
</table>

<table>
    <tr><th colspan="2">ZUGRIFF</th><th>Microsoft Azure-Stapel-Zertifizierung (engl.)</th></tr>
    <tr><td>Benutzer</td><td><p>Unterstützung für mehrere Benutzer, bei der Verschlüsselung von Anmeldeinformationen über ACL-basierten oder rollenbasierte (RBAC) Steuert den Zugriff</p><p>Überwachen von Benutzeraktivitäten</p></td><td>Erforderlich</td></tr>
    <tr><td>Gerätezugriffs</td><td>SSHv2</td><td>Erforderlich</td></tr>
    <tr><td>Verwendung des Zertifikats</td><td>Widerrufbare oder Zertifizierungsstelle</td><td>Erforderlich</td></tr>
    <tr><td>Authentifizierung</td><td>RADIUS</td><td>Erforderlich</td></tr>
    <tr><td>Remotezugriff</td><td>Virtuellen Switch-Schnittstelle</td><td>Erforderlich</td></tr>
</table>

Die Option sollte auch IEEE 802.1 X Authentifizierung Standard unterstützt werden.

**Drittanbieter Hyper-V-Switch-Erweiterungen**

Drittanbieter extensible wechselt für Hyper-V, Unterstützung erfassen, filtern oder Weiterleitung des Datenverkehrs im Netzwerk werden in Microsoft Azure-Stapel Lösungen nicht unterstützt.  
