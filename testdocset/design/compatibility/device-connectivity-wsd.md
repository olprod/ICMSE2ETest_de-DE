---
title: Device.Connectivity.WSD
Description: Requirements.
ms.assetid: 
MSHAttr: 
author: beneluxboy
ms.openlocfilehash: 99dca45759f8de128f6cf24f70a7d4416537903e
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
<!--
# Device.Connectivity.WSD

 - [Device.Connectivity.WSD](#device.connectivity.wsd)
-->

<a name="device.connectivity.wsd"></a>
##Device.Connectivity.WSD

### <a name="deviceconnectivitywsddpws"></a>Device.Connectivity.WSD.DPWS

*Geräte verwendet oder interagieren mit den Webdiensten auf Geräte-API (WSDAPI) einzuhalten Device Profile für Web Services (DPWS)-Spezifikation*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>10 Windows Mobile x86</p>
<p>10 Windows Mobile x64</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Geräte, die Planung verwenden oder interagieren mit Microsoft Windows Implementierung von DPWS, die Webdienste auf Geräte-API (WSDAPI) müssen die Spezifikation DPWS selbst implementieren. (WSDAPI)

*Hinweise zum Entwurf*

DPWS Spezifikation verfügbar unter

<http://go.Microsoft.com/fwlink/?LinkId=109231>

### <a name="deviceconnectivitywsddpwsextensibility"></a>Device.Connectivity.WSD.DPWSExtensibility

*Geräte-Profil für Web Services-Geräte muss Nachrichten, die Erweiterbarkeit Abschnitte enthalten, Nachrichten annimmt und verarbeitet die entsprechend.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>10 Windows Mobile x86</p>
<p>10 Windows Mobile x64</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Geräte-Profil für Web Services (DPWS) Geräte muss Nachrichten akzeptieren, in der XML-CODE erweitert wurde. Wenn das Gerät den Inhalt im Abschnitt extensible versteht, kann er die Verarbeitung.

*Hinweise zum Entwurf*

DPWS Spezifikation verfügbar unter

<http://go.Microsoft.com/fwlink/?LinkId=109231>

### <a name="deviceconnectivitywsdmetadataexchange"></a>Device.Connectivity.WSD.MetadataExchange

*Geräte Profil für Web Services (DPWS) Geräte unterstützen Metadatenaustausch*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>10 Windows Mobile x86</p>
<p>10 Windows Mobile x64</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

DPWS Geräte, die Interaktion mit den Webdiensten auf Geräten API (WSDAPI) muss Metadatenaustausch gemäß Definition in der Exchange-Metadatenspezifikation unterstützen.

*Hinweise zum Entwurf*

Metadatenaustausch-Spezifikation erhalten Sie unter <http://go.microsoft.com/fwlink/?LinkId=109248>

### <a name="deviceconnectivitywsdmetadatavalid"></a>Device.Connectivity.WSD.MetadataValid

*Geräte, die Interaktion mit den Webdiensten auf Geräten (WSDAPI) erstellen, Metadaten, die das Profil Geräte für Webdienste entspricht*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>10 Windows Mobile x86</p>
<p>10 Windows Mobile x64</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Geräte, die Interaktion mit WSDAPI müssen die Metadaten in der Device Profile für Web Services-Spezifikation von Februar 2006 gemäß auffüllen.

*Hinweise zum Entwurf*

Device Profile für Web Services-Spezifikation von Februar 2006 steht unter <http://go.microsoft.com/fwlink/?LinkId=109231>

### <a name="deviceconnectivitywsdschema"></a>Device.Connectivity.WSD.Schema

*Ein netzwerkfähiges Gerät, die Geräte-Profil für Web Services (DPWS) implementiert, muss das Protokoll und Schema entsprechen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>10 Windows Mobile x86</p>
<p>10 Windows Mobile x64</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Ein netzwerkfähiges Gerät, die Geräte-Profil für Web Services (DPWS) implementiert, muss das Profil Geräte für Webdienste entsprechen vom Schema gemäß.

Das Gerät muss auch auf den Namespace-URI wie beschrieben in der Geräte-Profil für Webdienst-Spezifikation verweisen.

Ein Gerät, Web Services Description Language (WSDL) der implementiert DPWS eingehalten werden müssen, die der Logo Gerät-Klasse zugeordnet ist. Die WSDL-DATEI definiert Dienste als Sammlungen von Netzwerkendpunkte oder Ports. WSDL-Spezifikation stellt ein XML-Format für Dokumente für diesen Zweck bereit. Geräten müssen die WSDL-Version 1.1 implementieren.

*Hinweise zum Entwurf*

Finden Sie unter der Web Services Description Language (WSDL) Version 1.1 unter <http://www.w3.org/TR/2001/NOTE-wsdl-20010315>

Finden Sie das Profil Geräte für Webdienste Schema unter <http://schemas.xmlsoap.org/ws/2006/02/devprof/devicesprofile.xsd.>

Finden Sie das Profil Geräte für Webdienst-Spezifikation unter <http://specs.xmlsoap.org/ws/2006/02/devprof/devicesprofile.pdf.>

Weitere Informationen finden Sie im Windows Rally Development Kit unter <http://go.microsoft.com/fwlink/?LinkId=109368.>

### <a name="deviceconnectivitywsdwsdiscovery"></a>Device.Connectivity.WSD.WSDiscovery

*Geräte-Profil für Web Services (DPWS) Geräte Interaktion mit den Webdiensten auf Geräte-API (WSDAPI) implementieren WS-Ermittlung*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>10 Windows Mobile x86</p>
<p>10 Windows Mobile x64</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

DPWS Geräte müssen WS-Discovery WSDAPI entwickelt implementieren.

*Hinweise zum Entwurf*

WS-Discovery-Spezifikation erhalten Sie unter <http://go.microsoft.com/fwlink/?LinkId=109247>

