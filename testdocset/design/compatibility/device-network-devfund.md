---
title: Device.Network.DevFund
Description: Netzwerkanforderungen.
ms.assetid: 
MSHAttr: 
author: beneluxboy
ms.openlocfilehash: adedb3c206935035180c7925189d21db06e717e7
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
<!--
# Device.Network.DevFund

 - [Device.Network.DevFund](#device.network.devfund)
-->

<a name="device.network.devfund"></a>
##Device.Network.DevFund

*Netzwerkanforderungen*

### <a name="devicenetworkdevfundndisversion"></a>Device.Network.DevFund.NdisVersion

*NDIS-Geräten müssen die NDIS 6.x-Anforderungen in der Windows-Treiberkits entsprechen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>10 Windows Mobile x86</p>
<p>10 Windows Mobile x64</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Alle NDIS-Gerät muss NDIS entsprechen 6.x im Windows-Treiberkits angegeben.

*Hinweise zum Entwurf*

Finden Sie unter Windows-Treiberkits "NDIS."

### <a name="devicenetworkdevfundnpos"></a>Device.Network.DevFund.NPOS

*Netzwerkgeräte müssen No Pause auf Anhalten (NPOS) unterstützen.*

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

NDIS Miniporttreiber müssen No Pause auf Anhalten (NPOS) auf Client-SKUs unterstützen (featureunterstützung auf Server-SKUs ist optional).

*Hinweise zum Entwurf*

Finden Sie unter die Unterbrechung der No Spezifikation auf Anhalten.

### <a name="devicenetworkdevfundselectivesuspend"></a>Device.Network.DevFund.SelectiveSuspend

*NDIS Geräte müssen selektive aussetzen Anforderungen erfüllen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>10 Windows Mobile x86</p>
<p>10 Windows Mobile x64</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

NDIS Geräte müssen selektive aussetzen Anforderungen erfüllen.

