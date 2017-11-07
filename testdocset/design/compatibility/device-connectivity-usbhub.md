---
title: Device.Connectivity.UsbHub
Description: Requirements.
ms.assetid: 
MSHAttr: 
author: beneluxboy
ms.openlocfilehash: effccc706b2391dacdc81899d840b1eee1b02092
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
<!--
# Device.Connectivity.UsbHub

 - [Device.Connectivity.UsbHub](#device.connectivity.usbhub)
-->

<a name="device.connectivity.usbhub"></a>
##Device.Connectivity.UsbHub

*Anforderungen, die nur die USB-Hubs liegen*

### <a name="deviceconnectivityusbhubidentifynumofuseraccessibleports"></a>Device.Connectivity.UsbHub.IdentifyNumOfUserAccessiblePorts

*Ein USB-Hub muss ordnungsgemäß identifizieren und melden der Anzahl der Ports, die der Benutzer zugreifen kann.*

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

Der USB-Hub muss Details enthalten, in dessen Hub Deskriptor, der das Betriebssystem für den Benutzer mit genaue Anzahl der Anzahl von downstream-seitige und Ports, der Hub unterstützt werden, verfügbar gemacht bereitstellen. Finden Sie unter USB-Spezifikation, Version 2.0, Section11.23 und USB-3.0-Spezifikation, Abschnitt 10.14. Stamm-Hubs sind von dieser Anforderung ausgenommen.

### <a name="deviceconnectivityusbhubsupportsuspend"></a>Device.Connectivity.UsbHub.SupportSuspend

*USB-Hubs müssen unterstützen die selektive suspend-Zustand und downstream-Geräte müssen nicht aus dem Bus löschen, wenn der Hub Resumes aus selektive anhalten.*

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

USB-Hubs müssen die selektive unterstützen suspend-Zustand, wie in der USB-Spezifikation und anderen Anforderungen an das Logo Programm angegeben. Nach ein Hub aus der selektiven fortgesetzt wird suspend-Zustand, alle Geräte, die angefügt wurden von der Hub und nicht entfernt wurden während der Hub angehalten wurde, muss vorhanden sein.

### <a name="deviceconnectivityusbhubusb3hubcomplieswithusb3spec"></a>Device.Connectivity.UsbHub.Usb3HubCompliesWithUsb3Spec

*3.0 USB-Hubs sind kompatibel mit der USB-3.0-Spezifikation.*

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

3.0 USB-Hubs müssen mit *der* Spezifikation für Universal Serial Bus (USB) 3.0 kompatibel sein. 

3.0 USB-Hubs müssen:

-   Übergeben Sie den USB-IF Interoperabilität-Tests

-   Übergeben Sie die USB-3.0 Hub Compliance Testsammlung

-   Übergeben Sie den USB-3.0 KA-test

### <a name="deviceconnectivityusbhubusb3reportportstatusbitscorrectly"></a>Device.Connectivity.UsbHub.Usb3ReportPortStatusBitsCorrectly

*3.0 USB-Hubs müssen immer die Port Statusbits richtig gemäß den Anweisungen in der Spezifikation USB 3.0 melden.*

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

Eine Reihe von ungültigen Portstatus bit in der aktuellen Stack Kombinationen, dass die Hub-Berichte ignoriert werden. Ungültige Kombinationen von Bits an Port Status wird als Fehler behandelt werden. Insbesondere werden Überprüfungen diese Aktionen folgen:
 

-   Zurücksetzen eines Ports

-   Anhalten und Fortsetzen eines Ports

-   System fortsetzen

Falsche Änderung Interrupts sollte ein Hub nicht gemeldet werden. Die Port Status Interrupt Weiterleitung ohne reporting Änderungen sollte ein Hub abgeschlossen werden.

### <a name="deviceconnectivityusbhubusbtypechubcompat"></a>Device.Connectivity.UsbHub.USBTypeCHubCompat

*USB-Hub Typ-C-Kompatibilität*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
</td></tr></table> 

**Beschreibung**

USB-Typ-C-Hubs müssen Multiplexers für ihre SuperSpeed Ports verwenden, damit ein einzelner Port können entweder Ausrichtung von die angefügte Plug & Play zugeordnet werden. Auf diese Weise können ein USB-C Gerät entweder Ausrichtung ohne Auswirkungen auf die Benutzeroberfläche anfügen oder verlieren Zustand.

Wenn der USB-Typ-C-Hub Strom wieder an den Host Upstream-zur ausgelegt ist, muss seine Upstream-Port als eine wird geladen UFP implementiert werden. Darüber hinaus muss ein Anfangs seiner Upstream-Port als eine DFP für Daten aufgelöst wird, eine Daten Rolle Swap initiiert; Wenn seine Upstream-Port ursprünglich als ein Empfänger Power aufgelöst wird, muss ein Power Rolle Swap initiiert werden.
