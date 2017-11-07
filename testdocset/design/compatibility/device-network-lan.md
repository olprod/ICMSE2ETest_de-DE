---
title: Device.Network.LAN
Description: Requirements.
ms.assetid: 
MSHAttr: 
author: beneluxboy
ms.openlocfilehash: 4e1db4ead7da5faa52774f43a41e3a5fee3aaf8f
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="devicenetworklan"></a>Device.Network.LAN

 - [Device.Network.LAN.10GbOrGreater](#device.network.lan.10gborgreater)
 - [Device.Network.LAN.AzureStack](#device.network.lan.azurestack)
 - [Device.Network.LAN.Base](#device.network.lan.base)
 - [Device.Network.LAN.ChecksumOffload](#device.network.lan.checksumoffload)
 - [Device.Network.LAN.CS](#device.network.lan.cs)
 - [Device.Network.LAN.DCB](#device.network.lan.dcb)
 - [Device.Network.LAN.GRE](#device.network.lan.gre)
 - [Device.Network.LAN.IPsec](#device.network.lan.ipsec)
 - [Device.Network.LAN.KRDMA](#device.network.lan.krdma)
 - [Device.Network.LAN.LargeSendOffload](#device.network.lan.largesendoffload)
 - [Device.Network.LAN.PM](#device.network.lan.pm)
 - [Device.Network.LAN.RSC](#device.network.lan.rsc)
 - [Device.Network.LAN.RSS](#device.network.lan.rss)
 - [Device.Network.LAN.SRIOV](#device.network.lan.sriov)
 - [Device.Network.LAN.SRIOV.VF](#device.network.lan.sriov.vf)
 - [Device.Network.LAN.TCPChimney](#device.network.lan.tcpchimney)
 - [Device.Network.LAN.VMMQ](#device.network.lan.vmmq)
 - [Device.Network.LAN.VMQ](#device.network.lan.vmq)
 - [Device.Network.LAN.VXLAN](#device.network.lan.vxlan)
 - [Device.Network.LAN](#device.network.lan)

<a name="device.network.lan.10gborgreater"></a>
## <a name="devicenetworklan10gborgreater"></a>Device.Network.LAN.10GbOrGreater

10GB oder größer LAN-Anforderungen 

### <a name="devicenetworklan10gborgreatercloudstress"></a>Device.Network.LAN.10GbOrGreater.CloudStress
Ethernet-Geräte, die GRE gekapselte Packet Aufgabe verlagert implementieren müssen mit der Spezifikation entsprechen.

<table><tr><th>Gilt für</th><td><p>Windows Server 2016 X64</p></td></tr></table>

**Beschreibung**

Dies gilt für alle Ethernet-Geräte, die für Server zertifiziert wurden.  Dieser Test überprüft, dass ein Ethernetgerät die Stress einer Wolke Datacenter erfüllen kann. Ethernet-Geräte, die diese Anforderung erfüllen müssen auch die Spezifikation entsprechen und unterstützen die folgenden Features:

Alle Netzwerkadapter müssen die folgenden Device.Network.LAN Features unterstützen.  

- Basieren soll (Anforderungen 100MbOrGreater über SupportIEEE8023)
- ChecksumOffload
- LargeSendOffload
- RSS

Alle Treiber für Netzwerkkarten Betrieb mit 10Gb oder höher, das den neuen Funktionen von WS2016 implementieren (d. h., NDKPI 2.0, VMMQ, VxLAN Aufgabe abnimmt, NVGREv2 Aufgabe abnimmt, MTU für HNV, PacketDirect) müssen Sie den Test mit PCS (Private Cloud Simulator) mit dem Profil 'Grundlegende 10 GigE NIC' auf einer 4-Knoten-Clusterkonfiguration ebenfalls übergeben.


<a name="device.network.lan.azurestack"></a>
## <a name="devicenetworklanazurestack"></a>Device.Network.LAN.AzureStack

_Definiert die Anforderungen, die erfüllt sein müssen, wenn die LAN (Card, NIC) in einer Microsoft Azure-Stapel basierte private Cloud-Lösung unterstützt wird_

### <a name="devicenetworklanazurestackbasicfunction"></a>Device.Network.LAN.AzureStack.BasicFunction

_Mindestanforderungen für LAN-Karten verwendet in Microsoft Azure-Stapel (engl.)_ 

<table><tr><th>Gilt für</th><td><p>Windows Server 2016 X64</p></td></tr></table>

**Beschreibung**

Microsoft Azure-Stapel-Anforderungen für LAN-Karten (NICs) werden in der folgenden Tabelle erfasst.

<table>
    <tr><th>Feature</th><th>Anforderung ></th></tr>
    <tr><td>Device.Network.LAN.10GbOrGreater</td><td>Device.Network.LAN.10GbOrGreater.CloudStress</td></tr>
    <tr><td>Device.Network.LAN.VXLAN</td><td>Device.Network.LAN.VXLAN.VXLANPacketTaskOffloads</td></tr>
    <tr><td>Device.Network.LAN.VMQ</td><td>Device.Network.LAN.VMQ.VirtualMachineQueues</td></tr>
    <tr><td>Device.Network.LAN.VMMQ</td><td>Device.Network.LAN.VMMQ.VirtualMachineMultipleQueues</td></tr>
    <tr><td rowspan="5">Device.Network.LAN.RSS</td><td>Device.Network.LAN.RSS.RSS</td></tr>
    <tr><td>Device.Network.LAN.RSS.SetHashFunctionTypeAndValue</td></tr>
    <tr><td>Device.Network.LAN.RSS.SupportIndirectionTablesSizes</td></tr>
    <tr><td>Device.Network.LAN.RSS.SupportToeplitzHashFunction</td></tr>
    <tr><td>Device.Network.LAN.RSS.SupportUpdatesToRSSInfo</td></tr>
    <tr><td>Device.Network.LAN.MTUSize</td><td>Device.Network.LAN.MTUSize</td></tr>
    <tr><td>Device.Network.LAN.LargeSendOffload</td><td>Device.Network.LAN.LargeSendOffload.LargeSendOffload</td></tr>
    <tr><td>Device.Network.LAN.KRDMA</td><td>Device.Network.LAN.KRDMA.KRDMA</td></tr>
    <tr><td>Device.Network.LAN.GRE</td><td>Device.Network.LAN.GRE.GREPacketTaskOffloads</td></tr>
    <tr><td>Device.Network.LAN.DCB</td><td>Device.Network.LAN.DCB.DCB</td></tr>
    <tr><td>Device.Network.LAN.ChecksumOffload</td><td>Device.Network.LAN.ChecksumOffload.ChecksumOffload</td></tr>
    <tr><td rowspan="12">Device.Network.LAN.Base</td><td>Device.Network.LAN.Base.100MbOrGreater</td></tr>
    <tr><td>Device.Network.LAN.Base.32MulticastAddresses</td></tr>
    <tr><td>Device.Network.LAN.Base.AdvProperties</td></tr>
    <tr><td>Device.Network.LAN.Base.AnyBoundary</td></tr>
    <tr><td>Device.Network.LAN.Base.IPv4AndIPv6OffloadParity</td></tr>
    <tr><td>Device.Network.LAN.Base.NDISCalls</td></tr>
    <tr><td>Device.Network.LAN.Base.NDISRequirements</td></tr>
    <tr><td>Device.Network.LAN.Base.PacketFiltering</td></tr>
    <tr><td>Device.Network.LAN.Base.PreserveOSServices</td></tr>
    <tr><td>Device.Network.LAN.Base.PriorityVLAN</td></tr>
    <tr><td>Device.Network.LAN.Base.ShortPacketPadding</td></tr>
    <tr><td>Device.Network.LAN.Base.SupportIEEEE8023</td></tr>
    <tr><td rowspan="6">Device.DevFund.Server.Nano</td><td>Device.DevFund.Server.OperateInServerNano</td></tr>
    <tr><td>Device.DevFund.Server.Nano.Deployment</td></tr>
    <tr><td>Device.DevFund.Server.Nano.Diagnostics</td></tr>
    <tr><td>Device.DevFund.Server.Nano.PatchAndUpdate</td></tr>
    <tr><td>Device.DevFund.Server.Nano.MonitoringAndTelemetry</td></tr>
    <tr><td>Device.DevFund.Server.Nano.FirmwareUpdate</td></tr>
</table>

### <a name="devicenetworklanazurestackcloudstress"></a>Device.Network.LAN.AzureStack.CloudStress

_Netzwerk-Domänencontrollern, die für die Microsoft Azure-Stapel Lösungen verwendet werden müssen diese Spezifikation entsprechen._ 

<table><tr><th>Gilt für</th><td><p>Windows Server 2016 X64</p></td></tr></table>

**Beschreibung**

Private Cloudlösungen umfassen eng integrierte Software und Hardwarekomponenten für Zweigstellenstandorte mit hoher Leistung bieten. Probleme bei der in den Komponenten (Software, Hardware, Treibern, Firmware usw.) können gefährden die Lösung und beeinträchtigt alle Versprechen bezüglich Service Level Agreement (SLA) für die private Cloud vorgenommen. 

Viele dieser Probleme sind nur unter eine hohe Stress, private Cloud Simulation verfügbar gemacht. Private Cloud Simulator (PCS) können Sie zum Überprüfen der Komponente in einem cloudszenario mit und Probleme zu identifizieren. Es simuliert eine live Datacenter/Private Cloud durch VM-Arbeitslasten zu erstellen, Planen von administrative Vorgänge (Lastenausgleich, Wartung von Software/Hardware) und Einfügen von Fehlern (ungeplante Hard-und Software mit Fehlern) auf die private Cloud. 

Um diese Spezifikation entsprechen, muss der Controller PCS Testlauf mit dem "Netzwerkcontroller – AzureStack" übergeben Profil auf einer 4-Knoten-Cluster-Konfiguration.

### <a name="devicenetworklanazurestackfirmwareupdate"></a>Device.Network.LAN.AzureStack.FirmwareUpdate

_Netzwerk-Domänencontrollern, die für die Microsoft Azure-Stapel Lösungen verwendet werden müssen diese Spezifikation entsprechen._ 

<table><tr><th>Gilt für</th><td><p>Windows Server 2016 X64</p></td></tr></table>

**Beschreibung**

Gerätetreiber & Firmware Update-Tools müssen Nano Server Kompatibilität Anforderungen wie in Device.DevFund.Server.Nano erfüllen.


<a name="device.network.lan.base"></a>
## <a name="devicenetworklanbase"></a>Device.Network.LAN.Base

*LAN-Anforderungen*

### <a name="devicenetworklanbase100mborgreater"></a>Device.Network.LAN.Base.100MbOrGreater

*Ethernet-Geräten müssen 100 Mb oder mehr Link kumulativ unterstützen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Ethernet-Geräte müssen auf 100 Mb oder einer höheren Geschwindigkeit verknüpfen können.

### <a name="devicenetworklanbase32multicastaddresses"></a>Device.Network.LAN.Base.32MulticastAddresses

*Ethernet-Geräte müssen für mindestens 32 Multicastadressen Filterung unterstützt.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Ein Ethernetgerät muss die Filterung 32 oder mehr multicast-Adressen unterstützt. 

Hinweise zum Entwurf: Finden Sie unter Windows-Treiberkits, "multicast". Finden Sie im Windows-Treiberkits, "NdisReadNetworkAddress" und "MAC-Adresse".

### <a name="devicenetworklanbaseadvproperties"></a>Device.Network.LAN.Base.AdvProperties

*Ethernet-Geräte müssen schützen Sie erweiterte Eigenschaften und vollständige anspruchsvolle über erweiterte Eigenschaften bereitzustellen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Ethernet-Geräten müssen der standardisierten Registrierung Schlüsselwörter zum Steuern von erweiterter Funktionen wie bei MSDN dokumentiert entsprechen.  Geräte müssen auch Microsoft standardisiert und privaten Schlüsselwörter böswilligen Werte zu vermeiden.

### <a name="devicenetworklanbaseanyboundary"></a>Device.Network.LAN.Base.AnyBoundary

*Ethernet-Geräten müssen aus dem Puffer an alle Grenze ausgerichtet-Pakete übermittelt werden können.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Puffer Ausrichtung bezieht sich auf ein Puffer gibt an, ob eine ungerade-Byte, Word, Double Word oder andere Grenze beginnt. Geräte müssen mit einem der Pakete Bruchstücke beginnend am eine ungerade-Byte-Grenze-Pakete übermittelt werden können. Aus Gründen der Systemleistung müssen in zusammenhängenden Puffer an einem Double Wortanfang Pakete empfangen werden.

### <a name="devicenetworklanbaseipv4andipv6offloadparity"></a>Device.Network.LAN.Base.IPv4AndIPv6OffloadParity

*Ethernet-Geräte, die verlagert implementieren müssen also konsistent für IPv4 und IPv6.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Netzwerk verlagert vom Ethernet-Geräte müssen unabhängig von der IP-Protokoll verwendet konsistent, Betrieb implementiert. Offloading Parität müssen ermöglicht Windows Kunden über IPv4 und IPv6 eine konsistente und vorhersehbar bleibt Erfahrung haben.

### <a name="devicenetworklanbasendiscalls"></a>Device.Network.LAN.Base.NDISCalls

*Ethernet-Geräte müssen nur NDIS Bibliothek oder WDF System Anrufe vornehmen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Treiber für einen Ethernetgerät muss nur NDIS oder WDF Anrufe tätigen. Alle Anrufe an andere Kernel-Modus-Komponenten sind nicht zulässig. 

Hinweise zum Entwurf: Finden Sie im Windows-Treiberkits, "NDIS" und "WDF."

### <a name="devicenetworklanbasendisrequirements"></a>Device.Network.LAN.Base.NDISRequirements

*Ethernet-Geräten müssen die NDIS Anforderungen in der Windows-Treiberkits entsprechen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Alle Ethernet-Treiber müssen in der Windows-Treiberkits angegebenen NDIS entsprechen. 

Hinweise zum Entwurf:, Finden Sie unter Windows-Treiberkits "NDIS".

### <a name="devicenetworklanbasepacketfiltering"></a>Device.Network.LAN.Base.PacketFiltering

*Ethernet-Geräten müssen Paketfiltern unterstützen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Der Miniporttreiber muss alle Filtertypen in Windows-Treiberkits unterstützen. Hinweis: Filtern sollte in Hardware-Firmware ausgeführt werden.

### <a name="devicenetworklanbasepreserveosservices"></a>Device.Network.LAN.Base.PreserveOSServices

*Ethernet-Geräte Miniport Treiber/Treiber Software müssen OS Dienste nicht deaktiviert.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Ethernet-Geräte Miniport Treiber/Treiber Software müssen OS Dienste nicht deaktiviert. Einige Geräte in der Regel Silhouette Diensten wie etwa Base Filterung Engine (BFE). Dies bewirkt, dass das System aufgrund fehlender Sicherheitsfunktionen Angriffsfläche.

### <a name="devicenetworklanbasepriorityvlan"></a>Device.Network.LAN.Base.PriorityVLAN

*Ethernet-Geräte, die Link kumulativ Gigabit oder mehr implementieren müssen Priorität & VLAN-tagging nach IEEE 802.1q implementieren Spezifikation.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Dies gilt nur für Ethernet-Geräte, die Link kumulativ Gigabit oder höher implementieren. Wenn das Gerät Ethernet-Link kumulativ Gigabit oder höher nicht implementiert wird, wird dieser Anforderung nicht angewendet. Das Ethernet-Gerät und Treiber müssen einfügen und Entfernen von Priorität und VLAN-Tags unterstützen.

### <a name="devicenetworklanbaseshortpacketpadding"></a>Device.Network.LAN.Base.ShortPacketPadding

*Ethernet-Geräte müssen Sie kurze Pakete mit Konstante Daten auffüllen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Abstand, d. h. kurzen hinzugefügte Ethernet-Paketen an die minimale IEEE 802.3 Abschnitt 4.2.3.3, Paketgröße Unterlagen muss Paketgröße initialisiert werden in Nullen oder einer 8-Bit-sich wiederholenden bevor die Pakete übertragen werden. Die 802.3 Ethernet-Spezifikation erfordert Pakete, die werden kürzer als die minimale Paketgröße auf bis zu die Mindestgröße aufgefüllt werden, bevor die Pakete auf das Netzwerk übertragen werden. Der 802.3-Ethernet-Spezifikation gibt den Abstand in Inhalt keinen; Microsoft erfordert jedoch den Abstand Nullen oder eine andere Konstante Wert Sicherheitsaspekte sein. Einige Treiber aufzufüllen die Pakete mit Daten aus zuvor gesendeten Pakete; Diese Vorgehensweise ist nicht akzeptabel. 

Hinweise zum Entwurf: Neue Lösungen implementieren Textabstand Nullen empfohlen. Einige Geräte, die den Abstand in Hardware implementieren verwenden jedoch 0xffs, die welche die Sicherheitsproblem Adressen.

### <a name="devicenetworklanbasesupportieeee8023"></a>Device.Network.LAN.Base.SupportIEEEE8023

*Ethernet-Geräte müssen IEEE 802.3 entsprechen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Alle 802.3-Ethernet-Geräte müssen implementieren und IEEE 802.3-Spezifikation entsprechen.

<a name="device.network.lan.checksumoffload"></a>
## <a name="devicenetworklanchecksumoffload"></a>Device.Network.LAN.ChecksumOffload

*Netzwerkanforderungen*

### <a name="devicenetworklanchecksumoffloadchecksumoffload"></a>Device.Network.LAN.ChecksumOffload.ChecksumOffload

*Ethernet-Geräte müssen gibt die Prüfsumme implementieren.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

 

Senden und Empfangen von TCP-Prüfsumme Offloading für IPv4 und IPv6

Senden und Empfangen von IP-Prüfsumme Offloading für IPv4

Senden und Empfangen von UDP-Prüfsumme Auslagerung für IPv4 und IPv6

Unterstützung für TCP Prüfsumme standardisiert Schlüsselwörtern ist obligatorisch.

Ethernet-Geräte implementieren Prüfsumme verlagert muss die NDIS-Enumeration Schlüsselwörter verfügbar machen.

 

<a name="device.network.lan.cs"></a>
## <a name="devicenetworklancs"></a>Device.Network.LAN.CS

*Verbundenen standby-fähigen Computers (auch bekannt als Plattform) unterstützt active Energiesparmodus und Support zu, der mit dem entsprechenden ACPI Flag OS Ankündigung (NIEDRIG\_POWER\_S0\_im LEERLAUF\_GEEIGNET) in FADT. Erwartungsgemäß ist auch die Windows-Zertifizierung Anforderungen für einen verbundenen standby-Plattform erfüllen. In diesem Abschnitt werden die verbundenen standby-Anforderungen für verkabelt LAN (Ethernet).*

### <a name="devicenetworklancsnetworkwake"></a>Device.Network.LAN.CS.NetworkWake

*Verkabelten LAN (Ethernet) Geräte integriert verbunden Standby-Systemen oder Docking-Stationen Lieferumfang des Systems Netzwerk Remoteaktivierung Muster unterstützen müssen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Die spezifischen Anforderungen sind unten aufgeführt:

Aktivieren Sie auf LAN-Muster:

Verkabelten LAN-Geräten und Gerätetreibern werden erforderliche Support mindestens 32 (32) Bitmap-Muster von mindestens 128-Byte-Größe. Dieses Typs Muster bezieht sich auf flexible Bitmaps (NDIS\_PM\_WOL\_PAKET. NdisPMWoLPacketBitmapPattern) und keinen anderen Inhaltstypen, Muster.

Remoteaktivierung magischen Paket:

Verkabelten LAN-Geräten und Gerätetreibern müssen magischen Paket Aktivierung unterstützen. Unterstützung für diese Pakettyp Aktivierung ist erforderlich und ist nicht in der Anforderung 32-Bitmap-Muster enthalten.

Paket Angabe zu aktivieren:

Verkabelten LAN-Geräten und Gerätetreibern sind erforderlich zur Unterstützung von reaktivieren Paket Angabe für alle Netzwerkpakete Remoteaktivierung und zum Zwischenspeichern und, der angibt, des vollständige Netzwerkpakets die Aktivierung verursacht werden. Beachten Sie, dass dies die Device.Network.LAN.PM.WakePacket-Anforderung für verbundene Standby-fähigen Geräte ersetzt.

Hinweise zum Entwurf:

Finden Sie in der Spezifikation Power Management auf MSDN.

### <a name="devicenetworklancspresenceoffload"></a>Device.Network.LAN.CS.PresenceOffload

*Verkabelten LAN (Ethernet) Geräte integriert verbunden Standby-Systemen oder Docking-Stationen Lieferumfang des Systems Netzwerk Anwesenheit Offloading unterstützen müssen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Unterstützung für dieses Feature ist erforderlich. Die spezifischen Anforderungen sind unten aufgeführt:

ARP-Protokoll-Offloading:

Verkabelte LAN-Geräten müssen ARP-Offloading implementieren, gemäß der Spezifikation Power Management auf MSDN. Insbesondere muss die Offloading reagieren Sie auf eine ARP-Anforderung (Operation = 1) durch eine ARP-Antwort reagiert nicht mehr (Operation = 2) wie in RFC 826 (<http://tools.ietf.org/html/rfc826>) definiert.

Protokoll-Offloading NS:

Verkabelte LAN-Geräten müssen IPv6 NS-Offloading implementieren, gemäß in Power Management Spezifikation auf MSDN. Insbesondere muss die Offloading reagieren Sie auf eine Nachbaraufforderungsnachricht (Vorgang 135 =) durch eine Werbeanzeige NS Reaktion (Vorgang = 136) gemäß Definition in RFC 4861 (<http://tools.ietf.org/html/rfc4861>). Wir erfordern die Unterstützung für mindestens 2 ND-Offloading verwendet. Jeder Anforderung kann 2 Zieladressen verfügen. Der Wert, sie sollten in NDIS Werbung\_PM\_CAPABILITIES::NumNSOffloadIPv6Addresses ist die ANZAHL ANFRAGEN, nicht die Anzahl der Adressen. Wenn sie die minimalen 2 Anfragen unterstützen, sollten sie also 2 ankündigen. Der Name des Felds ist falsch und wird in den nächsten behoben werden NDIS freigeben.

Der Miniport muss gemäß Beschreibung benachbarten Discovery und -Neighbour-Anfrage-Protokoll für IPv6 RFCs genannten Protokolls implementieren.

### <a name="devicenetworklancsreliablecsconnectivity"></a>Device.Network.LAN.CS.ReliableCSConnectivity

*LAN-Gerät auf Systeme, die Standbymodus verbunden unterstützen muss zuverlässige Verbindung im Standbymodus verbunden übermitteln.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Das verkabelte LAN-Gerät wechselt nahtlos zwischen Power funktionsfähige D0 und Energiesparmodus D2/D3 während in verbunden Standby (CS). Verkabelte LAN-Gerät verwaltet OSI-Schicht 2 Link Connectivity in CS. Das verkabelte LAN-Gerät reaktiviert auf übereinstimmenden nur Aktivierungsmuster. Es gibt keine falsche reaktiviert im CS aus. Aktivierung Pakete werden ohne Verzögerung oder Pufferung übermittelt. Sperre Bildschirm apps bleiben über IPv4 und IPv6 in CS mit Kanal für die Remoteanrufsteuerung oder Pushbenachrichtigung Trigger verbunden.

Der genaue D-Wert in den Energiesparmodus hängt von den zugrunde liegenden Bustyp. Beispiel Netzwerkadapter auf USB, SDIO Bus D2 als ihre Energiesparmodus beim Netzwerkadapter auf PCI verwenden oder PCIe Bus verwenden Sie den Status D3 an.

Weitere Informationen

Ausnahmen - gilt nicht für nicht-AOAC-Geräten

### <a name="devicenetworklancswakeevents"></a>Device.Network.LAN.CS.WakeEvents

*Verkabelten LAN (Ethernet) Geräte integriert verbunden Standby-Systemen oder Docking-Stationen Lieferumfang des Systems müssen verschiedene Remoteaktivierung Triggern unterstützen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Die spezifischen Anforderungen sind unten aufgeführt: Remoteaktivierung Media Connect: verkabelt Ethernet-Geräte müssen ankündigen und Support Remoteaktivierung über Media verbinden, gemäß Definition in der Spezifikation auf MSDN. Trennen von Medien Remoteaktivierung: verkabelt Ethernet-Geräte müssen ankündigen und Support-Aktivierung auf Medien disconnect-gemäß Definition in der Spezifikation auf MSDN.

Hinweise zum Entwurf: Finden der Power Management-Spezifikation auf MSDN.

### <a name="devicenetworklancswakereasondetection"></a>Device.Network.LAN.CS.WakeReasonDetection

*Verkabelten LAN (Ethernet) Geräte integriert verbunden Standby-Systemen oder Docking-Stationen Lieferumfang des Systems müssen die Aktivierung Grund Erkennung unterstützen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Die spezifischen Anforderungen sind unten aufgeführt: Reaktivieren Grund Unterstützung: verkabelt Ethernet-Geräte müssen unterstützen Grund reaktivieren unter Einhaltung der NDIS\_STATUS\_PM\_REAKTIVIEREN\_GRUND Dokumentation auf MSDN.  Bei der Aktivierung von einer eingehenden Netzwerkpakets verursacht wird, muss die NIC erfassen, und geben Sie an, das gesamte Paket verursacht die Aktivierung für das Betriebssystem. 

Hinweise zum Entwurf: Finden Sie in der Spezifikation Power Management auf MSDN.

<a name="device.network.lan.dcb"></a>
## <a name="devicenetworklandcb"></a>Device.Network.LAN.DCB

*LAN-Anforderungen*

###  <a name="devicenetworklandcbdcb"></a>Device.Network.LAN.DCB.DCB

*Ethernet-Geräte, die Daten Center Bridging (DCB) implementieren, müssen die Spezifikation DCB einhalten*.

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Dies gilt nur für Ethernet-Geräte, die Data Center Bridging (DCB) unterstützen.

Ethernet-Geräte, die Daten Center Bridging (DCB) implementieren müssen die folgenden Anforderungen erfüllen:

 - MaxNumTrafficClasses muss zwischen 3 und 8 inklusive.
 - MaxNumEtsCapableTrafficClasses muss mindestens 2 sein.
 - MaxNumPfcEnabeldTrafficClasses muss mindestens 1 sein.
 - LEGT muss unterstützt werden.
 - PFC muss unterstützt werden.
 - Strict Priorität muss unterstützt werden.
 - iSCSI-CNAs muss Klassifizierung-Element für iSCSI-Datenverkehr (TCP-Ports 860 und 3260, Src und Ziel-Port) unterstützen.
 - FCoE CNAs muss Klassifizierung-Element für FCoE-Datenverkehr (von 0x8906 Ethertype) unterstützen.

Hinweise zum Entwurf

Finden Sie unter Bridging Spezifikation unter <http://msdn.microsoft.com/en-us/library/windows/hardware/hh451635.aspx>Rechenzentrum.

<a name="device.network.lan.gre"></a>
## <a name="devicenetworklangre"></a>Device.Network.LAN.GRE

*LAN-Anforderungen*

### <a name="devicenetworklangregrepackettaskoffloads"></a>Device.Network.LAN.GRE.GREPacketTaskOffloads

*Ethernet-Geräte, die GRE gekapselte Packet Aufgabe verlagert implementieren müssen die Spezifikation entsprechen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Dies gilt nur für Ethernet-Geräte, die implementiert werden GRE gekapselte Packet Aufgabe verlagert. Ethernet-Geräte, die GRE gekapselte Paket Aufgabe verlagert implementieren müssen der Spezifikation entsprechen und unterstützt die folgenden Aufgaben gekapselte Offloading für alle Kombinationen aus inneren/äußeren IPv4/IPv6-Header:

 - Senden Sie Prüfsumme (IPv4, TCP, UDP)
 - Empfangen Sie Prüfsumme (IPv4, TCP, UDP)
 - LSOv2
 - VMQ

<a name="device.network.lan.ipsec"></a>
## <a name="devicenetworklanipsec"></a>Device.Network.LAN.IPsec

*LAN-Anforderungen*

### <a name="devicenetworklanipsecipsec"></a>Device.Network.LAN.IPsec.IPsec

*Ethernet-Geräte, die IPSec-Aufgabe Offloading implementieren müssen erforderlichen Modi und Protokolle unterstützen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Ethernet-Geräte, die IPSec-Aufgabe Offloading unterstützen müssen Folgendes unterstützen: Version: IPSec-Aufgabe Abladung v2 NDIS Version: 6.1, 6.20, 6.30.

Ethernet-Geräte, die Aufgabe Auslagerung für Windows 8 IPsec unterstützen müssen NDIS 6.30 verwenden. Mode:

- IPv4 und IPv6-Transport  

- IPv4 und IPv6-TunnelProtocol: ESPCrypto Algorithmus:

- Implementiert werden müssen: AES-GCM (128 oder höher)

- Möglicherweise zusätzliche Algorithmen implementieren, wie in http://technet.microsoft.com/en-us/library/dd125380(v=WS.10).aspxCoexistence: Ethernet devices that support IPsec task offload and any the following offload technologies: angegeben

- Große Übertragung-Offloading - empfangen Side Scaling

- Prüfsumme abnimmt. Müssen sie auf eine Koexistenz implementieren, so, dass die Verwendung von IPsec Aufgabe abnimmt, die nicht über die Verwendung der anderen Offloading Technologien für jeden IPSec-Modus implementiert entgegen.

<a name="device.network.lan.krdma"></a>
## <a name="devicenetworklankrdma"></a>Device.Network.LAN.KRDMA

*LAN-Anforderungen*

### <a name="devicenetworklankrdmakrdma"></a>Device.Network.LAN.KRDMA.KRDMA

*Geräte, die die NetworkDirect Kernel Modus Interface (NDKPI) (auch bekannt als, im Kernelmodus RDMA, kRDMA) implementieren müssen die Netzwerk-Schnittstelle Modus direkte Kernel (NDKPI)-Spezifikation entsprechen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Dies gilt nur für Ethernet-Geräte, die die Netzwerk-Schnittstelle im Modus direkte Kernel (NDKPI)-Spezifikation implementieren. Geräte, die Netzwerk direkte Kernel Modus Interface (NDKPI) (auch bekannt als, im Kernelmodus RDMA) implementieren müssen die Netzwerk-Schnittstelle Modus direkte Kernel (NDKPI)-Spezifikation entsprechen. Version 2.0 wurde die aktuelle Spezifikation seit Juli 2014.  Übermittlungen Version 1.2 der Spezifikation NDKPI Einhaltung akzeptiert bis zu 31 Dezember 2016, jedoch nicht die Szenarien hyper zusammengeführt in Windows Server 2016 entwickelt.  Effektive Januar 1, 2017 nur NDKPI Version 2.0 kompatible Geräte akzeptiert werden.  Übermittlung für das Microsoft Azure Stapel (MAS) AQ LOGO nicht AQ müssen NDKPI Version 2.0 unterstützen.

NDKPI Version 2.0 werden drei Betriebsmodi beschrieben:

- Modus 1, ein Modus, in dem Betrieb im einheitlichen Modus unterstützt
- Modus 2, ein Modus, der auf NIC_Switch vPorts NDKPI unterstützt 
- Modus 3, einem Modus NDKPI verfügbar gemacht werden auf einen VF Treiber unterstützt

Windows-10-Client-Treiber sind nur zur Unterstützung von Modus 1 erforderlich.

Windows Server 2016 und MAS Treiber müssen Modi 1 und 2 unterstützen.

*Hinweise zum Entwurf*

Finden Sie unter der Netzwerk-Schnittstelle Modus direkte Kernel (NDKPI)-Spezifikation (Version 2.0).

<a name="device.network.lan.largesendoffload"></a>
## <a name="devicenetworklanlargesendoffload"></a>Device.Network.LAN.LargeSendOffload

*Netzwerkanforderungen*

### <a name="devicenetworklanlargesendoffloadlargesendoffload"></a>Device.Network.LAN.LargeSendOffload.LargeSendOffload

*Ethernet-Geräte müssen große senden verlagert implementieren.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Ethernet-Geräten müssen die folgende Aufgabe verlagert unterstützen:

Große senden Abladung von Version 2 für IPv4 und IPv6.

*Hinweise zum Entwurf*

Finden Sie unter Windows-Treiberkits "NDIS."

### <a name="devicenetworklanmtusize"></a>Device.Network.LAN.MTUSize

<table><tr><th>Gilt für</th><td><p>Windows Server 2016 X64</p></td></tr></table>

**Beschreibung**

Ethernet-Geräte müssen Großrahmen unterstützen. MTU Werte in der Benutzeroberfläche müssen die Ethernet-Headergröße von 14 Bytes enthalten. Die "* JumboPacket" standardisierten-Schlüsselwort in der Windows-Registrierung wird derzeit für das Festlegen der Größe der MTU verwendet und sollte als aufzählbare Wert mit unterstützten Werte, die als 1514 4088 und 9014 bleiben.

### <a name="devicenetworklanmtusizeencapoverhead"></a>Device.Network.LAN.MTUSize.EncapOverhead

<table><tr><th>Gilt für</th><td><p>Windows Server 2016 X64</p></td></tr></table>

**Beschreibung**

Ein neues Stichwort werden mit numerischen, Standardwert 0, maximale Wert 480 und schrittweise Größe 32 wird Typ gewählte "*EncapOverhead" hinzugefügt. Dieser Wert wird Verwaltungsaufwand Ethernet-Frames aufgrund virtuelles Netzwerk Überlagerung-Kapselung wie VXLAN und NVGRE berücksichtigt werden. MTU-Größe wird daher durch die Summe dieser beiden Werte Schlüsselwort außer vielleicht in der Groß-/Kleinschreibung bestimmt werden, auf dem *JumboPacket + * EncapOverhead würde einige Hardware der Netzwerkkarte Obergrenze überschreiten

Implementieren von GRE oder VxLAN verlagert Geräte müssen ebenfalls diese Anforderung integrieren.

<a name="device.network.lan.pm"></a>
## <a name="devicenetworklanpm"></a>Device.Network.LAN.PM

*LAN-Anforderungen*

### <a name="devicenetworklanpmpowmgmtndis"></a>Device.Network.LAN.PM.PowMgmtNDIS

*Ethernet-Geräte, die Anwesenheit verlagert Netzwerk implementieren müssen die Power Management-Spezifikation auf das Programm NDIS entsprechen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Ethernet-Geräten müssen ARP-Offloading gemäß Definition in der Spezifikation für Power Management auf MSDN implementieren. Insbesondere muss die Offloading reagieren Sie auf eine ARP-Anforderung (Operation = 1) durch eine ARP-Antwort reagiert nicht mehr (Operation = 2) wie in RFC 826 definiert.

Ethernet-Geräte müssen IPv6-NS-Offloading implementieren, gemäß Definition in der Spezifikation für Power Management auf MSDN. Insbesondere muss die Offloading reagieren Sie auf eine Nachbaraufforderungsnachricht (Vorgang 135 =) durch eine Werbeanzeige NS Reaktion (Vorgang = 136) gemäß Definition in RFC 4861. Geräte müssen mindestens 2 NS verlagert, jeweils mit bis zu 2 Ziel IPv6-Adressen unterstützt.

Hinweise zum Entwurf

Finden Sie in der Spezifikation Power Management auf MSDN.

Finden Sie unter RFC 826 auf <http://go.microsoft.com/fwlink/?LinkId=108718>.

Ausnahmen - Ausnahmen zu dieser Anforderung gehören: PC-Karte, CardBus-Geräte und Netzwerkgeräten externe USB-Bus betrieben Betrieb. Geräte mit 1 Gigabit schnellen Übertragung. Geräte mit Fiber Glasfaserkabel Mittel.

 

### <a name="devicenetworklanpmwakeonlanpatterns"></a>Device.Network.LAN.PM.WakeOnLANPatterns

*Ethernet-Geräte müssen Aktivierung für LAN-Muster gemäß der Spezifikation implementieren.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Implementierung muss Network Device Klasse Power Management Verweis Specification entsprechen. Ethernet-Geräte und Treiber müssen Sie mindestens acht (8) Bitmap-Muster unterstützen, da Windows bis zu acht Muster verwendet. Unterstütze magischen Paket ist erforderlich und ist nicht in der Anforderung 8-Bitmap-Muster enthalten.

*Hinweise zum Entwurf*

Implementierungsdetails sind in der Spezifikation für Power Management auf MSDN.

Ausnahme - Ausnahmen zu dieser Anforderung enthalten: PC-Karte, CardBus-Geräte und Netzwerkgeräten externe USB-Bus betrieben Betrieb. Geräte mit 1 Gigabit schnellen Übertragung. Geräte mit Fiber Glasfaserkabel Mittel. Hinweis: Das Gerät auf LAN - Aktivierung implementiert muss implementieren ordnungsgemäß basierend auf diese Anforderung unabhängig davon, ob das Gerät in die Ausnahmeliste ist.

 

### <a name="devicenetworklanpmwakepacket"></a>Device.Network.LAN.PM.WakePacket

*Ethernet-Geräte, die Paket-Erkennung reaktivieren implementieren müssen Network Device Klasse Power Management Reference Specification entsprechen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Ethernet-Geräte, die Paket-Erkennung reaktivieren implementieren müssen Network Device-Klasse Power Management Verweis Specification entsprechen. Implementierung muss Network Device-Klasse Power Management Verweis Specification unter Windows WDK erläuterten entsprechen. Die NIC ist zum Erfassen mindestens 128 ersten Byte des Pakets verursacht die Netzwerk-Aktivierung und zum Generieren einer Statusanzeige für das Betriebssystem erforderlich.

*Hinweise zum Entwurf*

Finden Sie unter der WDK Network Device Klasse Power Management Verweis Spezifikation.

<a name="device.network.lan.rsc"></a>
## <a name="devicenetworklanrsc"></a>Device.Network.LAN.RSC

*LAN-Anforderungen*

### <a name="devicenetworklanrscrsc"></a>Device.Network.LAN.RSC.RSC

*Ethernet-Geräte, die empfangen Segment zusammenfügenden (RSC) implementieren müssen mit der Spezifikation RSC entsprechen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Ethernet-Geräte, die empfangen Segment zusammenfügenden (RSC) implementieren müssen entsprechen der Spezifikation RSC und sowohl IPv4 als auch IPv6-Unterstützung benötigen.

*Hinweise zum Entwurf*

NDIS Version: 6.30

<a name="device.network.lan.rss"></a>
## <a name="devicenetworklanrss"></a>Device.Network.LAN.RSS

*LAN-Anforderungen*

### <a name="devicenetworklanrssrss"></a>Device.Network.LAN.RSS.RSS

*Ethernet-Geräte, die RSS-Implementierung*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

RSS-Unterstützung ist auf Server SKUs für alle Geräte außer SR-IOV VF Treiber erforderlich.

RSS-Unterstützung ist optional auf Client SKUs.

Ethernet-Geräte, die RSS implementieren müssen unterstützen:

 - Hash-Typen: IPv4, TCP IPv4, IPv6 und TCP IPv6
 - Mehrere Prozessorgruppen (für Miniports NDIS Version 6.20 und höher)

Anzahl von Warteschlangen (je nach Übertragungsrate):

 - Weniger als 10 Gigabit: 2
 - 10 Gigabit oder höher: 8
 - SR-IOV VF-Treiber (unabhängig von Übertragungsrate): 2
 - Dereferenzierung Tabellengröße (je nach Übertragungsrate):
 - Weniger als 10 Gigabit: 64
 - 10 Gigabit oder höher: 128
 - SR-IOV VF-Treiber (unabhängig von Übertragungsrate): 16
 - Öffentliche Ordner: SR-IOV-Treiber (unabhängig von Übertragungsrate): 64
 - Implementieren Sie alle RSS-standardisiert Schlüsselwörter
 - \*RSS
 - \*NumRSSQueues

Nachricht signalisiert unterbrochen wird erweitert (MSI-X) gemäß Definition in der Spezifikation für PCI-Version 3.0. Für Geräte mit einer Verknüpfung Geschwindigkeit von weniger als 10 Gigabit muss das Gerät 1 MSI-X-Vektor mit Unterstützung für 2 RSS-Hardware Warteschlangen verfügen. Für Geräte 10 Gigabit oder höher, das Gerät muss über eine MSI-X Vektor für jede RSS-Hardware-Warteschlange verfügen. Angenommen, wenn das Gerät verfügt über eine Verknüpfung Geschwindigkeit von 10 Gigabit und Unterstützung für 8 RSS-Hardware Warteschlangen Ankündigung benötigen klicken Sie dann es mindestens 8 MSI-X Vektoren in die Hardware.

*Hinweise zum Entwurf*

Finden Sie unter RSS standardisiert Schlüsselwörtern Spezifikation <http://msdn.microsoft.com/library/windows/hardware/ff570864.aspx>.

Darüber hinaus reservieren das Gerät beliebig viele MSI-X Tabelleneinträge CPUs im System vorhanden sind. Lesen Sie den NDIS Dokumentation Abschnitt für weitere Details <http://msdn.microsoft.com/library/windows/hardware/ff566491.aspx>MSI-X.

### <a name="devicenetworklanrsssethashfunctiontypeandvalue"></a>Device.Network.LAN.RSS.SetHashFunctionTypeAndValue

*Ethernet-Geräte, die implementiert werden RSS müssen die Hashfunktion, Hash-Typ und Hashwert für jedes angegebene Paket festgelegt.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Dies gilt nur für Ethernet-Geräte, mit die RSS implementiert. Wenn das Gerät Ethernet RSS nicht implementiert wird, wird dieser Anforderung nicht angewendet. Wenn das Netzwerkgerät RSS, alle Pakete unterstützt für die RSS-Implementierung Berechnen des Hash konnte muss RSS-Implementierung zurückgeben, die vollständige 32-Bit-Hashwert, die Hash-Funktion und die Hash-Typ für die einzelnen empfangenen Pakete, die es gibt an. Für alle Pakete Empfangs ohne Fehler für die es nicht muss die Hashfunktion generieren Hash-Typ deaktivieren. Makros NET\_PUFFER\_LISTE\_FESTGELEGT\_HASH\_GEBEN Sie NET\_PUFFER\_LISTE\_FESTGELEGT\_HASH\_-FUNKTION und NET\_PUFFER\_LISTE\_FESTGELEGT\_HASH\_WERT muss so legen Sie die zugeordneten Werte verwendet werden.

*Hinweise zum Entwurf*

Finden Sie in der MSDN-Seite für Weitere Informationen: <http://msdn.microsoft.com/en-us/library/windows/hardware/ff570726.aspx>. Finden Sie unter Windows-Treiberkits "Angibt, RSS empfangen von Daten".

### <a name="devicenetworklanrsssupportindirectiontablessizes"></a>Device.Network.LAN.RSS.SupportIndirectionTablesSizes

*Ethernet-Geräte, die RSS implementieren müssen bestimmte Größen für Dereferenzierung Tabelle unterstützen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Dies gilt nur für Ethernet-Geräte, mit die RSS implementiert. Wenn das Gerät Ethernet RSS nicht implementiert wird, wird dieser Anforderung nicht angewendet. Wenn die Netzwerkgeräte RSS unterstützt, muss die RSS-Implementierung Dereferenzierung Tabellengrößen für jede Potenz von 2 bis zur maximalen Dereferenzierung Tabellengröße unterstützt unterstützen.  Wenn 128 die maximale Dereferenzierung Tabellengröße ist, muss der Miniport beispielsweise Dereferenzierung Tabellen Größen, 2, 4, 8, 16, 32, 64 oder 128 akzeptieren. Legen Sie die Suche in der Tabelle Dereferenzierung das Ziel suchen CPU muss mithilfe von niederwertige Bits gemäß den letzten Wert erreicht werden in den Objektbezeichner\_GEN\_EMPFANGEN\_HORIZONTAL\_NumberOfLsbs Variable PARAMETER. Eine RSS-Implementierung muss den Host-Protokollstapel NumberOfLsbs auf einen beliebigen Wert zwischen 1 und 7, inklusive Einstellung unterstützen.

*Hinweise zum Entwurf*

Finden Sie unter Windows-Treiberkits "OID\_GEN\_EMPFANGEN\_HORIZONTAL\_PARAMETER."

### <a name="devicenetworklanrsssupporttoeplitzhashfunction"></a>Device.Network.LAN.RSS.SupportToeplitzHashFunction

*Ethernet-Geräte, mit die RSS implementiert, müssen die Hashfunktion Toeplitz unterstützen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Dies gilt nur für Ethernet-Geräte, die RSS implementieren. Wenn das Gerät Ethernet RSS nicht implementiert wird, wird dieser Anforderung nicht angewendet. Wenn die Netzwerkgeräte RSS unterstützen, RSS-Implementierung muss mindestens unterstützen die Toeplitz Hash-Funktion für die Typen der Pakete, die für die es als die Fähigkeit zum Generieren des Hash angekündigt (gemäß den Angaben in OID\_GEN\_EMPFANGEN\_HORIZONTAL\_FUNKTIONEN). Hierzu zählen außerdem Unterstützung für die Länge HashSecretKey von 40 Bytes.

*Hinweise zum Entwurf*

Finden Sie unter Windows-Treiberkits "RSS-Hash-Funktionen". Darüber hinaus in MSDN finden Sie weitere Informationen <http://msdn.microsoft.com/en-us/library/windows/hardware/ff570725.aspx>

### <a name="devicenetworklanrsssupportupdatestorssinfo"></a>Device.Network.LAN.RSS.SupportUpdatesToRSSInfo

*Ethernet-Geräte, die RSS implementieren müssen Updates für RSS-Informationen zu einem beliebigen Zeitpunkt unterstützen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Dies gilt nur für Ethernet-Geräte, mit die RSS implementiert. Wenn das Gerät Ethernet RSS nicht implementiert wird, wird dieser Anforderung nicht angewendet. Können Sie jederzeit eine Netzwerkgeräte RSS unterstützen, muss dies unterstützen, OID festlegen\_GEN\_EMPFANGEN\_HORIZONTAL\_PARAMETERN, einschließlich der Dereferenzierung Tabelle, NumberOfLsbs, SecretKey und HashInformation (Hash-Funktion und Hash-Typ) aktualisieren. RSS-Implementierung kann buchen Pakete nicht der Reihe nach während des Übergangs auf den neuen Status aus den vorherigen Zustand und kann eine Hardware zurückgesetzt, wenn die HashInformation, SecretKey oder NumberOfLsbs geändert ausführen. Es muss nicht ausführen, eine Hardware zurückgesetzt, wenn nur die Dereferenzierung Tabelle Inhalt geändert werden.

*Hinweise zum Entwurf*

Finden Sie unter Windows-Treiberkits "OID\_GEN\_EMPFANGEN\_HORIZONTAL\_PARAMETER."

<a name="device.network.lan.sriov"></a>
## <a name="devicenetworklansriov"></a>Device.Network.LAN.SRIOV

*Netzwerkanforderungen*

### <a name="devicenetworklansriovsriov"></a>Device.Network.LAN.SRIOV.SRIOV

*Ethernet-Geräte, die einzelnen e/a-Stamm-Virtualisierung (SR-IOV) implementieren müssen die erforderliche Funktionen unterstützen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Ein Treiber muss Microsoft-Software-Back-Kanal zu Öffentliche Ordner: VF Treiber PCIe Konfiguration Speicherplatz Anfragen verwenden.

Die Standardkonfiguration für die anfängliche Switch muss in der INF-Datei.

Die Öffentliche Ordner: INF-Datei muss die UpperRange auf "ndis5" und "Ethernet" LowerRange festgelegt.

Die INF-Datei darf keinen der \*SriovPreferred Schlüsselwort.

Datenbankseiten: zusammengeführt Filter müssen festgelegt werden, in NDIS\_REECIVED\_FILTER\_FUNKTIONEN.

SR-IOV NIC muss es sich um eine virtuelle Ethernet-Brücke (VEB) enthalten.

Wenn RSS für VF Miniports unterstützt wird, muss die NIC einen unabhängigen RSS Hash für jede Funktion physischen oder virtuellen unterstützen.

Die Öffentliche Ordner: und die VF Miniporttreiber müssen die LAN-Logo-Tests können.

Die Standard-vPort kann nicht gelöscht werden. nicht standardmäßige vPorts auf einem VF kann gelöscht werden.

Wenn SRIOV deaktiviert ist, müssen die NIC und Miniport als standard-Ethernet-NIC funktionieren

Ein SRIOV NIC müssen auch ankündigen und VMQ implementieren. Warteschlange Paar IOV nicht zugeordnet sind, für die VMQ verfügbar.

Bericht von Medien verbunden muss VF Miniport-zum Akzeptieren von Datenverkehr bereit.

VF Miniport muss eine UpperRange von "Ndisvf" und ein LowerRange von "Iovvf" angeben.

*Hinweise zum Entwurf*

Finden Sie die einzelnen Stamm e/a-Virtualisierung-Spezifikation.

<a name="device.network.lan.sriov.vf"></a>
## <a name="devicenetworklansriovvf"></a>Device.Network.LAN.SRIOV.VF

*Netzwerkanforderungen*

### <a name="devicenetworklansriovvfvf"></a>Device.Network.LAN.SRIOV.VF.VF

*Ethernet-Geräte, die einzelnen Stamm e/a-Virtualisierung (SR IOV) implementieren müssen erforderliche Funktionen unterstützen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Anforderungen für einen SRIOV VF adapter

Ein Treiber muss Microsoft-Software-Back-Kanal zu Öffentliche Ordner: VF Treiber PCIe Konfiguration Speicherplatz Anfragen verwenden.

Wenn RSS für VF Miniports unterstützt wird, muss die NIC die gleiche Anzahl von RSS wie möglich PFs unterstützen.

Alle NDIS-Gerät muss entsprechen auf NDIS sollte 6.x im Windows-Treiberkits angegebenen also die VF Geräte.

VF Miniport muss eine UpperRange von "Ndisvf" und ein LowerRange von "Iovvf" angeben.

Wenn der VF Miniport empfangen Segment zusammenfügenden (RSC) implementiert wird, muss er Einhaltung der Spezifikation RSC und erfordert sowohl IPv4 als auch IPv6-Unterstützung.

Bericht von Medien verbunden muss VF Miniport-zum Akzeptieren von Datenverkehr bereit.

*Hinweise zum Entwurf*

Finden Sie die einzelnen Stamm e/a-Virtualisierung-Spezifikation.

<a name="device.network.lan.tcpchimney"></a>
## <a name="devicenetworklantcpchimney"></a>Device.Network.LAN.TCPChimney

*TCP-Chimney-Anforderungen*

### <a name="devicenetworklantcpchimneycomplywithndis"></a>Device.Network.LAN.TCPChimney.ComplyWithNDIS

*Ethernet-Geräte, die TCP-Chimney implementieren müssen mit dem neuesten NDIS Miniport-Treibermodell entsprechen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Dies betrifft nur Ethernet-Geräte, die TCP Chimney implementieren. Wenn das Gerät Ethernet-TCP Chimney nicht implementiert wird, wird dieser Anforderung nicht angewendet. Die Spezifikation TCP Chimney auf Verbindung herstellen muss der TCP-Chimney-Teil des Geräts entsprechen.

*Hinweise zum Entwurf*

Finden Sie unter Windows-Treiberkits "Netzwerk-Geräte und Protokolle."

### <a name="devicenetworklantcpchimneycomplywithtcpipprotocol"></a>Device.Network.LAN.TCPChimney.ComplyWithTCPIPProtocol

*Ethernet-Geräte, die TCP-Chimney implementieren müssen die IETF-standard-RFCs für die TCP/IP-Protokoll-Produktfamilie entsprechen und Verhalten sich wie die Microsoft Windows (Host) TCP/IP-Protokoll-Implementierung.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Dies gilt nur für Ethernet-Geräte, die TCP-Chimney implementieren. Wenn das Gerät Ethernet-TCP Chimney nicht implementiert wird, wird dieser Anforderung nicht angewendet. Das Schlüsselwort "MUSS", sind "DARF NICHT", "REQUIRED", "GILT", "NICHT", "SHOULD", "SOLLTE NICHT", "EMPFOHLEN", "MAY" und "OPTIONAL" in dieser Anforderung interpretiert werden soll, wie in RFC 2119 beschrieben. Eine Netzwerkkarte MUSS TCP Chimney-Familie der TCP/IP-Protokoll implementieren, dass: 1. Die Implementierung der TCP/IP-Protokoll entspricht der IETF-standard-RFCs und 2. Die Implementierung der TCP/IP-Protokoll verhält sich auf die gleiche Weise wie die Implementierung der Microsoft Windows TCP/IP-Protokoll. Dies gibt an, welche die RFCs muss von der TCP Chimney NIC implementiert werden und das erwartete Verhalten in Fällen, in denen eine RFC mehrdeutige verdeutlicht. Tabelle 1 werden die RFCs aufgeführt, die ein TCP Chimney NIC implementiert werden müssen.

<html>
    <table>
        <thead>
            <tr class="header">
                <th>Beschreibenden Namen</th>
                <th>Spezifikation</th>
            </tr>
        </thead>
        <tbody>
            <tr class="odd">
                <td>Transmission Control Protocol RFCs</td>
                <td>
                    <p>
RFC 793 - Transmission Control-Protokoll<br />
RFC 813 - Fenster und Bestätigung Strategie in TCP<br />
RFC 1122\* - Requirements for Internet Hosts – Communication Layers - gesamten Abschnitt 4.2                    </p>
                    <p>RFC 1323 - TCP-Erweiterungen für hohe Leistung</p>
                    <p>RFC 2923\* - TCP Probleme mit Pfad-MTU-Ermittlung</p>
                    <p>RFC 2988\* -Netzwerke des TCP-RTO</p>
                    <p>RFC 3465\* -Zählvorgängen entsprechenden Byte</p>
                </td>
            </tr>
            <tr class="even">
                <td>TCP-Überlastung-Steuerelement</td>
                <td>
                    <p>RFC 2581\* -TCP Überlastung-Steuerelement</p>
                    <p>RFC 2582\* -neue Reno Änderung des TCP-schnelle Wiederherstellung Alg.</p>
                    <p>RFC 3042 - begrenzte übertragen</p>
                </td>
            </tr>
            <tr class="odd">
                <td>TCP Verlust Wiederherstellung</td>
                <td>
                    <p>RFC 2018\* -TCP-selektive Bestätigung Optionen</p>
                    <p>RFC 3517\* -konservativ selektiven Bestätigung (SACK)-basierte Verlust Wiederherstellung Algorithmus für TCP</p>
                </td>
            </tr>
            <tr class="even">
                <td>TCP-Sicherheit</td>
                <td>RFC Tcpm-Tcpsecure-09\* -Verbessern der TCP-Stabilität zu Blind Attacks In Fenster</td>
            </tr>
            <tr class="odd">
                <td>Internet Protocol Version 4 RFCs\*\*</td>
                <td>RFC 791, RFC 894, gemäß RFC 1042, RFC 1191, RFC 1122 - gesamten Abschnitt 3.2</td>
            </tr>
            <tr class="even">
                <td>Internet Protocol v6 RFCs\*\*</td>
                <td>RFC 1752, RFC 1981 RFC 2374 RFC 2460 RFC 2461 RFC 2675 RFC 2711 RFC 3122, RFC 3513</td>
            </tr>
            <tr class="odd">
                <td>
                    <p>\*-Es werden zugeordneten Clarifications für die RFC befolgt werden müssen. Sie sind unten aufgeführt.\*\*</p>
                    <p>-TCP Chimney Netzwerkschnittstellenkarten (NICs) DARF NICHT implementieren, legen Sie die gesamte von IP, zusammen RFCs an. In diesem Fall müssen die TCP-Chimney-Treiberkits Richtlinien für die Implementierung von Internet Protocol RFC folgen.</p>
                </td>
                <td></td>
            </tr>
        </tbody>
    </table>
</html>

Tabelle 1: Listen RFCs, dass eine TCP Chimney NIC RFC Clarifications implementiert werden müssen. Die folgenden Clarifications müssen die TCP/IP-Implementierung der TCP Chimney Netzwerkkarte folgen. RFC 11221. Abschnitt 4.2.3.4 gibt an, dass der Nagle-Algorithmus als Methode zur Vermeidung der alberne Fenster Syndrom implementiert werden SOLL. Die TCP-Chimney NIC MUSS den Nagle-Algorithmus implementieren und muss die Implementierung dieser Pseudocode: ein. Beim Senden eines Segments, MUSS die erste Phase der Vermeidung von SWS als implementiert werden:

```
Send(){..If (BytesToSend &gt; MSS ||BytesToSend &gt; MaxSndWnd /2 ||BytesToSend &gt;= BytesInCurReq ||ForceOutput){BeginSend();}else{StartSwsTimer();}                ...               

...
```

<html>
    <dl>
        <dt><i>BytesToSend</i></dt>
        <dd>
            <p>Die Anzahl der verfügbaren Bytes, die gesendet werden kann, wie von der aktuellen zulässig senden Fenster.</p>
        <dd>
        <dt><i>MSS</i></dt>
        <dd>
            <p>Maximale Segment</p>
        <dd>
        <dt><i>SizeMaxSndWnd</i></dt>
        <dd>
            <p>Die maximale Empfangsgröße Fenster, das der TCP-Peer jemals angekündigt.</p>
        <dd>
        <dt><i>BytesInCurReq</i></dt>
        <dd>
            <p>Bytes nach links in der aktuellen Anforderung gesendet.</p>
        <dd>
        <dt><i>ForceOutput</i></dt>
        <dd>
            <p>Eine Variable, die bestimmt, ob das Segment gesendet werden MUSS, aufgrund von SWS Zeitgeber ablaufen als Beispiel. Die Linie rot gibt die Abweichung von der SWS vermeiden, die implementiert werden MUSS.</p>
        <dd>
    </dl>
</html>
     
**Hinweis**&nbsp;&nbsp;&nbsp;in Pseudocode definiert das Verhalten zum Zeitpunkt des senden, nicht zur Zeit, wenn die Anforderung zum Senden von den Host TCP/IP-Stapel übergeben wird. Der Grund, warum Microsoft TCPIP-Stapel von SWS Algorithmus die oben beschriebene Weise abweicht, ist:

1. CWND Vergrößerbar in Byte. Genauer gesagt, wird CWND nicht vergrößert oder verkleinert ein Vielfaches von MSS oder PUSH Grenzen eingeschränkt. Da die TCP-Implementierung in Windows entsprechenden Byte Zählvorgängen (RFC 3465) implementiert wird, ist bisher noch weiter verstärkt.

2. Die Grenze PUSH wird bestimmt, von der TCP-Anwendung Bereitstellen von Daten gesendet werden, damit nicht gewährleistet ist mit der Größe MSS ausgerichtet werden sollen.

3. Aufgrund der \#1 und \#2, es ist sehr wahrscheinlich für die TCP-Zustandsautomat erreichen einen Punkt, an dem eine MSS übertragene versetzt wurde, und ist ein Unterordner MSS-Segment die, wenn gesendet, den Datenblock bis maximal PUSH abgeschlossen wird.

    ein. In diesem Fall ist es günstiger für TCP, diese eine untergeordnete MSS, um vollständige segmentieren Sie die Übertragung von der app-Puffer bis maximal PUSH zu senden. Der Grund, warum sie hierzu günstiger ist, ist, da die Daten an die empfangende Anwendung schneller zugestellt werden, als wenn der SWS Algorithmus des Buchstabens folgte. Zur selben Zeit stellt die Abweichung keine behandelt in erster Linie SWS erneut ein.

4. Wie im Abschnitt 4.2.2.17 beschrieben verwenden ein TCP Chimney NIC MÜSSEN Verbindung ZEIT als Auslöser zum Senden einer NULL Fenster Test und wesentlich erhöhen Sie das Intervall zwischen aufeinander folgenden Tests. Darüber hinaus MUSS der Test 1 Byte mit neue Daten enthalten.

5. <!--edit: List item 5 is as it appears in the Word version, but this needs help. -->Füllen mindestens zwei Reassemblierung Lücken TCP Chimney NIC MUSS unterstützt werden. RFC 20181. Die TCP-Chimney NIC KANN RFC 2018 implementieren. Wenn eine TCP-Chimney NIC RFC 2018 implementiert wird, MUSS auch RFC 3517.2 implementieren. Eine TCP-Chimney NIC, IST NICHT ordnungsgemäß zu implementieren, RFC 2018 MUSS verarbeiten reine Bestätigung-Pakete, die SACK-Blöcke enthalten, wie in RFC 793. RFC 25811 Abschnitt 3 beschrieben. Die TCP-Chimney NIC muss können für den Übergang zwischen mithilfe des Algorithmus langsame Start Überlastung Vermeidung Algorithmus wie angegeben in Abschnitt 3.1 verwenden. Darüber hinaus MUSS es eine Überlastung Fenster (Cwnd) implementieren langsame starten Schwellenwert (Ssthresh) anstelle von Überlastung Fenster = &gt; langsame starten Threshold.RFC 25821. Verwenden Sie die folgende Formel TCP Chimney NIC MÜSSEN anstelle in RFC 2582, Abschnitt 3 - Punkt-1:SsThresh beschrieben = Max (2\*mss min(cwnd,window\_advertised\_by\_peer)/2) RFC 29231. Die TCP-Chimney NIC ist NICHT erforderlich, die Empfehlungen in RFC 2923 beschriebenen implementieren. Stattdessen müssen die TCP-Chimney NIC TCP-Verbindung, um den Host-Stapel zum Ausführen des Black Hole Erkennung Zustandsautomat ermöglichen hochladen. Finden Sie unter Windows-Treiberkits für Details. RFC 29881. Hintergrundinformationen finden Sie unter RFC 1122 Abschnitt 4.2.3.1 und RFC 2988. TCP Chimney NIC MUSS mit den folgenden Algorithmus, der RFC 2988 geringe Ausnahmen übereinstimmt, die unter qualifiziert sind RTO-Berechnung implementieren: CalculateRto-Funktion (erste, ByRef Srtt, ByRef Rttvar, m) RttSample = Minimum (m, 30s), wenn erste Thenrttvar = m/2srtt Melse =' beachten, Rttvar wird zuerst berechnet, von der alten ' Wert der Srttrttvar (3/4) = \* Rttvar + (1/4) \* abs (Srtt - RttSample) Srtt (7/8) =\*Srtt + (1/8) \* RttSampleend IfCalculateRto = Srtt + 4 \* RttvarCalculateRto = Minimum (CalculateRto 60 s) CalculateRto = Maximum (CalculateRto 300ms) die zwei Zeilen in Rot Capture die Abweichung von RFC. Insbesondere wird davon ausgegangen, dass der TCP-Chimney NIC eine Obergrenze aufweist, bei der Berechnung des ZEIT-Werts. RFC 34651. Abschnitt 2.1 werden die Änderungen hinzu während Überlastung Vermeidung beschrieben. Verwenden Sie folgende Formel zum Berechnen von CWND während Überlastung Vermeidung einer Netzwerkkarte MUSS TCP Chimney: / / L ist 4CWnd += max ((MaxMss \* min (MaxMss \* L, BytesAcked)) /CWnd 1) Beachten Sie, dass die oben genannten Formel max ((MaxMss, MaxMss) von Cwnd, 1, wenn BytesAcked immer 1 ist wird) die Gleichung 2 in RFC 2581 entspricht. 2. Abschnitt 2.3 in RFC 3465 beschreibt den Grenzwert, L der langsame Start- und Überlastung Vermeidung; die steuert die Gründlichkeit des Algorithmus für die Anhebung der CWND ausgewählt. Ein TCP-Chimney NIC MÜSSEN verwenden einen Wert von 4 für L in Reihenfolge dafür dasselbe Verhalten wie die Windows TCP/IP-Protokoll-Implementierung aufweisen. RFC Tcpm Tcpsecure 091.     TCP Chimney Netzwerkkarten MÜSSEN befolgen Sie die Sicherheitsrichtlinien, die in Abschnitten 3, 4 und 5 des Entwurfs "TCP-Sicherheit" Internet RFC (http://tools.ietf.org/html/draft-ietf-tcpm-tcpsecure-12) erläutert. 2.     TCP befolgen Chimney NICSs der spezifischen Implementierungsdetails Windows in WDK beschrieben.

Hinweise zum Entwurf: Finden Sie unter den vollständigen Text von RFCs am <http://go.microsoft.com/fwlink/?LinkId=36702>aus.

### <a name="devicenetworklantcpchimneyhandlesoutoforderdata"></a>Device.Network.LAN.TCPChimney.HandlesOutOfOrderData

*Ethernet-Geräte, die TCP-Chimney implementieren müssen die Datenszenarien nicht der Reihe nach ordnungsgemäß verarbeiten.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Ethernet-Geräte, die TCP-Chimney implementieren müssen ordnungsgemäß nicht der Reihe nach nachfolgend beschriebene Datenszenarien behandeln: 

1. Wenn alles in der Warteschlange Reassemblierung nach einer Bankkontodaten FINNISCH eingefügt wird, MUSS die Warteschlange Reassemblierung geleert werden, durch Verwerfen des gesamten Inhalts.

2. Wenn eine TCP-Chimney NIC ein OOO FINNISCH in der Warteschlange Reassemblierung gespeichert werden, MUSS dann es nicht OOO Daten oder OOO FINNISCH hinter einer anderen OOO FINNISCH in der Warteschlange Reassemblierung gespeichert. Wenn er erhält OOO Daten oder OOO FINNISCH Segment, das zu einem solchen Konflikt führen würde, klicken Sie dann den TCP Chimney NIC MÜSSEN ablegen dieses Segment und leeren die Warteschlange Reassemblierung durch Verwerfen des gesamten Inhalts.

### <a name="devicenetworklantcpchimneyimplementsufficientlygranulartimers"></a>Device.Network.LAN.TCPChimney.ImplementSufficientlyGranularTimers

*Ethernet-Geräte, die TCP-Chimney implementieren müssen ausreichend differenzierte Zeitgeber implementieren.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Dies gilt nur für Ethernet-Geräte, die TCP-Chimney implementieren. Wenn das Gerät Ethernet-TCP Chimney nicht implementiert wird, wird dieser Anforderung nicht angewendet. Die TCP-Chimney NIC muss haben Zugriff auf den Timer (implementiert auf die NIC-Hardware) mit präzise genug Granularität und skew so, dass es ordnungsgemäß das TCP/IP-Zustandsautomat steuern kann. Die Timer Granularität muss 10 Millisekunden oder besser (niedriger als 10 ms) und der Timer skew muss so gut wie welche Timer für allgemeine Zwecke CPU enthält.

### <a name="devicenetworklantcpchimneyneighborstateobjtimestampscomplywithwdk"></a>Device.Network.LAN.TCPChimney.NeighborStateObjTimestampsComplyWithWDK

*Benachbarte Zustand Objekt Zeitstempel werden entsprechend der Details im Windows-Treiberkits implementiert.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Ein Netzwerkgerät, das TCP-Chimney implementiert muss sicherstellen, dass TCP Chimney verwaltet einen Zeitstempel für jedes Objekt der benachbarten Zustand und Überprüfung anhand der Zeitstempel für jedes Paket ein- und ausgehenden.

*Hinweise zum Entwurf*

Finden Sie unter Windows-Treiberkits "OID\_TCP\_ABNIMMT.

### <a name="devicenetworklantcpchimneysupport1024connections"></a>Device.Network.LAN.TCPChimney.Support1024Connections

*Ethernet-Geräte, die TCP Chimney implementieren müssen mindestens 1024 Verbindungen unterstützen und nicht bekannt, dass mehr Kapazität als, was die Hardware unterstützen kann abnimmt.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Dies gilt nur für Ethernet-Geräte, die TCP-Chimney implementieren. Wenn das Gerät Ethernet-TCP Chimney nicht implementiert wird, wird dieser Anforderung nicht angewendet. Ethernet-Geräte, die TCP Chimney implementieren müssen mindestens 1024 Verbindungen unterstützen und nicht bekannt, dass mehr Kapazität als, was die Hardware unterstützen kann abnimmt.

### <a name="devicenetworklantcpchimneysupport64bitaddresses"></a>Device.Network.LAN.TCPChimney.Support64bitAddresses

*Ethernet-Geräte, die TCP-Chimney implementieren müssen 64-Bit-Adressen unterstützt.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Dies gilt nur für Ethernet-Geräte, die TCP-Chimney implementieren. Wenn das Gerät Ethernet-TCP Chimney nicht implementiert wird, wird dieser Anforderung nicht angewendet. Wenn das Gerät PCI verwendet wird, muss es 64-Bit-Adressen unterstützt. Unterstützung für 64-Bit-Daten ist nicht erforderlich.


<a name="device.network.lan.vmmq"></a>
## <a name="devicenetworklanvmmq"></a>Device.Network.LAN.VMMQ

*Definiert für Ethernet-Geräte, die virtuellen Computer mehrere Warteschlangen zu implementieren.*

### <a name="devicenetworklanvmmqvirtualmachinemultiplequeues"></a>Device.Network.LAN.VMMQ.VirtualMachineMultipleQueues

*Für Ethernet-Geräte, die virtuellen Computer mehrere Warteschlangen zu implementieren*

<table><tr><th>Gilt für</th><td><p>Windows Server 2016 X64</p></td></tr></table>

**Beschreibung**

Die Implementierung muss der virtuellen Computer mehrere Warteschlangen Verweis-Spezifikation entsprechen.


<a name="device.network.lan.vmq"></a>
## <a name="devicenetworklanvmq"></a>Device.Network.LAN.VMQ

*LAN-Anforderungen*

### <a name="devicenetworklanvmqvirtualmachinequeues"></a>Device.Network.LAN.VMQ.VirtualMachineQueues

*Ethernet-Geräte, die virtuellen Computer Warteschlangen implementieren müssen der Spezifikation programmierbare Computer Warteschlangen Verweis entsprechen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Die Implementierung muss der programmierbaren Computer Warteschlangen Verweis Spezifikation entsprechen.

Es müssen mindestens vier Warteschlangen mit Filter unterstützt werden. Unterstützung für mindestens 16 Warteschlangen mit Filter wird empfohlen. Die Anzahl der erforderlichen Warteschlangen werden 16 1 Dezember 2009 für 10 Gigabit-WebParts. Die Anzahl der Warteschlangen, die erforderlich ist, einschließlich der Standard-Warteschlange.

Unterstützung von MSI-X (NDIS\_EMPFANGEN\_FILTER\_MSI\_X\_UNTERSTÜTZTE) ist erforderlich: 

| Warteschlangen       | MSI-X-Warteschlangen-Verhältnis |
|--------------|-----------------------|
| 1 bis 16      | 1:1                   |
| 17-64        | 1:2 (min 16)          |
| 65 unbegrenzt | 1:16 (min 32)         |

Filtern:

Unterstützung für VLAN-Filterung in Hardware (NDIS\_EMPFANGEN\_FILTER\_MAC\_HEADER\_VLAN\_ID\_UNTERSTÜTZTE) ist optional. Wenn implementiert, muss VLANs pro VM-Warteschlange (NumVlansPerVMQueue) &gt;= 1

Unterstützung für MAC-Filterung in Hardware (NDIS\_EMPFANGEN\_FILTER\_MAC\_HEADER\_ZIEL\_ADRESSE\_UNTERSTÜTZTE) obligatorisch ist.

Unterstützung für NDIS\_EMPFANGEN\_FILTER\_TEST\_HEADER\_GLEICH\_UNTERSTÜTZTE zwingend erforderlich ist.

Die maximale Anzahl der MAC-Header-Filter (MaxMacHeaderFilters) muss &gt;= Anzahl der Warteschlangen

Insgesamt MAC-Adressen (NumTotalMacAddresses) muss &gt;= Anzahl der Warteschlangen

MAC-Adressen pro VM-Warteschlange (NumMacAddressesPerVMQueue) muss &gt;= 1

Pro Warteschlange empfangen Angabe muss unterstützt werden (NDIS\_EMPFANGEN\_WARTESCHLANGE\_PARAMETER\_PRO\_WARTESCHLANGE\_EMPFANGEN\_ANGABE)

Dynamische VMQ-Unterstützung ist nur für Windows Server 2012 erforderlich.

Hinweise zum Entwurf

Implementierungsdetails sind in der Spezifikation ProgrammableMachine Warteschlangen, auf das Programm NDIS Connect-Website <http://msdn.microsoft.com/en-us/library/windows/hardware/ff571034.aspx>

<a name="device.network.lan.vxlan"></a>
## <a name="devicenetworklanvxlan"></a>Device.Network.LAN.VXLAN

### <a name="devicenetworklanvxlanvxlanpackettaskoffloads"></a>Device.Network.LAN.VXLAN.VXLANPacketTaskOffloads

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Dies gilt nur für Ethernet-Geräte, mit die VXLAN gekapselte Packet Aufgabe verlagert implementiert. Ethernet-Geräte, die gekapselte VXLAN Paket Aufgabe verlagert implementieren müssen Einhaltung der Spezifikation und unterstützt die folgenden Aufgaben gekapselte Offloading für alle Kombinationen aus inneren/äußeren IPv4-/ IPv6-Header:

 - Senden Sie Prüfsumme (IPv4, TCP, UDP)
 - Empfangen Sie Prüfsumme (IPv4, TCP, UDP)
 - LSOv2
 - VMQ

<a name="device.network.lan"></a>
## <a name="devicenetworklan"></a>Device.Network.LAN

### <a name="devicenetworklancloudstress"></a>Device.Network.LAN.CloudStress

*Ethernet-Geräte, die GRE gekapselte Paket Aufgabe verlagert implementieren müssen die Spezifikation entsprechen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Dies gilt für alle Ethernet-Geräte, die für Server zertifiziert wurden. Dieser Test überprüft, dass ein Ethernetgerät die Stress einer Wolke Datacenter erfüllen kann. Ethernet-Geräte, die diese Anforderung erfüllen müssen auch die Spezifikation entsprechen und unterstützen die folgenden Features:

 - Alle Netzwerkadapter muss unterstützen die folgenden Features Devie.Networking.LAN und übergeben die Private Cloud-Leistungstests

 - Basieren soll (Anforderungen 100MbOrGreater über SupportIEEE8023)

 - ChecksumOffload

 - LargeSendOffload

 - RSS

 - Netzwerkadapter für kleine Bereitstellungen Cloud bereit müssen alle oben aufgeführten Features unterstützen und

 - Haben Sie kumulativ, 10G oder höher

 - MTU-Größe

 - NVGRE

 - VXLAN

 - VMQ

Netzwerkadapter für große Bereitstellungen Cloud bereit, müssen alle oben aufgeführten Features unterstützen und

 - PacketDirect

 - DCB

 - KRDMA (iWARP oder routingfähige RoCE)

 - SRIOV

Weitere Informationen;

 - 1GigE). Netzwerkschnittstellenkarten (NICs), wenn sie alle erforderlichen Features werden NICHT unterstützen werden NICHT Logo für Server erteilt

 - 1GigE). Netzwerkschnittstellenkarten (NICs), wenn sie alle erforderlichen Features unterstützen werden Logo für Server erteilt werden

 - 1GigE). Netzwerkschnittstellenkarten (NICs), werden auch wenn sie Unterstützung für einige erweiterte Features aufgeführt, die für die Cloud bereit Netzwerkschnittstellenkarten (NICs), nicht bereit zusätzliche Qualifikation Cloud erteilt

 - 0GigE und oberhalb der Netzwerkschnittstellenkarten (NICs), wenn sie NICHT alle erforderlichen Features werden, unabhängig von der zusätzliche Features sie unterstützen unterstützen, NICHT erteilt werden Logo

 - 10GigE und oben Netzwerkschnittstellenkarten (NICs), die alle erforderlichen Features unterstützt, aber unterstützen nicht alle Features kleine Cloud für 10GigE Netzwerkschnittstellenkarten (NICs) als erforderlich, dass für die Cloud bereit aufgeführt, erteilt werden Logo

 - 10GigE oben Netzwerkschnittstellenkarten (NICs), die alle erforderlichen Features sowie alle Features für kleine Cloud Netzwerkschnittstellenkarten (NICs) unterstützen, erteilt werden nun zusätzliche Qualifikation Cloud und für kleinere Cloud-Bereitstellungen unterstützt werden

 - 10GigE und oberhalb der Netzwerkschnittstellenkarten (NICs), die alle erforderlichen Features sowie alle Features für große Cloud Netzwerkschnittstellenkarten (NICs) unterstützen, erteilt werden nun zusätzliche Qualifikation Cloud und für größere Cloud-Bereitstellungen unterstützt werden
