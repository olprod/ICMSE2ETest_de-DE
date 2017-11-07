---
title: Device.BusController.SdioController
Description: Requirements.
ms.assetid: 
MSHAttr: 
author: beneluxboy
ms.openlocfilehash: 042f9f773fd88cf0a97b4b6c855fff35d59014a7
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
<!--
# Device.BusController.SdioController
 - [Device.BusController.SdioController](#device.buscontroller.sdiocontroller)
-->

<a name="device.buscontroller.sdiocontroller"></a>
##Device.BusController.SdioController

### <a name="devicebuscontrollersdiocontrollercomplywithindustryspec"></a>Device.BusController.SdioController.ComplyWithIndustrySpec

*SDIO Controller muss Standards entsprechen.*

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

Secure Digital e/a (SDIO) Host Controller PCI 2.3 oder höher Anforderungen für die Schnittstelle entsprechen müssen. PCI-Konfiguration registriert und Schnittstellen-Informationen, finden Sie in der SD-Host Controller-Spezifikation, Version 1.0, Anhang A.

### <a name="devicebuscontrollersdiocontrollerwdfkmdfdriver"></a>Device.BusController.SdioController.WdfKmdfDriver

*SDIO Controller-Treiber muss eine WDF KMDF Implementierung.*

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

Treiber für den Controller SDIO muss mithilfe von Windows Treiber Framework (WDF) Kernel-Modus-Treiberframework für die Implementierung der Treiber geschrieben werden.

