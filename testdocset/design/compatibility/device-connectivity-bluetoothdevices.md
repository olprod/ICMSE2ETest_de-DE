---
title: Device.Connectivity.BluetoothDevices
Description: "Anforderungen für Geräte, die auf dem Computer über Bluetooth verbinden."
ms.assetid: 
MSHAttr: 
author: beneluxboy
ms.openlocfilehash: b5c2a3c2510fcdabbc5d9115d9879f8e328f4463
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
<!--
# Device.Connectivity.BluetoothDevices

 - [Device.Connectivity.BluetoothDevices](#device.connectivity.bluetoothdevices)
-->

<a name="device.connectivity.bluetoothdevices"></a>
##Device.Connectivity.BluetoothDevices

*Geräte, die auf den PC über Bluetooth verbinden.*

### <a name="deviceconnectivitybluetoothdevicesbluetoothdeviceidprofilever13"></a>Device.Connectivity.BluetoothDevices.BluetoothDeviceIdProfileVer13

*Geräte die Bluetooth unterstützen müssen das Gerät ID (DI) Profile, Version 1.3 oder Gerät Informationen Service (DIS), sofern gewünscht implementieren.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
</td></tr></table>

**Beschreibung**

Bluetooth-PC Peripheriegeräte müssen den Geräte-ID Datensatz gemäß dem Profil Geräte-ID, Version 1.3, für Bluetooth-BR/EDR oder das Gerät Informationen Service (DIS), Version 1.1, Bluetooth LE enthalten.

### <a name="deviceconnectivitybluetoothdevicesbluetoothhidlimiteddiscoverablemode"></a>Device.Connectivity.BluetoothDevices.BluetoothHidLimitedDiscoverableMode

*Bluetooth-HID Geräten müssen nur im Modus mit eingeschränkter eDiscovery-fähigen erkannt werden.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
</td></tr></table>

**Beschreibung**

Bluetooth-HID Geräten müssen nur im Modus mit eingeschränkter eDiscovery-fähigen erkannt werden.

### <a name="deviceconnectivitybluetoothdevicescomplementarysubsystemlist"></a>Device.Connectivity.BluetoothDevices.ComplementarySubsystemList

*Bluetooth-wireless-Technologie Subsystem Endprodukt muss Windows-Betriebssystem in der Liste komplementäre Subsystem aufgelistet.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
</td></tr></table>

**Beschreibung**

Bluetooth-Subsystem Endprodukt muss Windows-Betriebssystems in der Liste komplementäre Subsystem, wie beschrieben in Bluetooth Qualifikation Programm Referenzdokument, Version 2.1, Abschnitt 6.1, "Bluetooth-Subsysteme." aufgelistet.

### <a name="deviceconnectivitybluetoothdeviceshidinitiatedreconnect"></a>Device.Connectivity.BluetoothDevices.HidInitiatedReconnect

*HID-Geräte, die Bluetooth unterstützen müssen HID initiierte erneut eine Verbindung unterstützen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
</td></tr></table>

**Beschreibung**

Das HIDReconnectInitiate-Attribut (definiert in Bluetooth-HID Profil, 1.0, Section7.11.5, "HIDReconnectInitiate") muss aktiviert sein. Um automatisch an den Host erneut, wenn die Verbindung getrennt wird, muss das Gerät den Seitenmodus eingeben.

### <a name="deviceconnectivitybluetoothdeviceskeyboardssupportpasskeyauthentication"></a>Device.Connectivity.BluetoothDevices.KeyboardsSupportPasskeyAuthentication

*Bluetooth-Tastaturen, die eine Kopplung vereinfacht Secure implementieren müssen die Authentifizierungsmethode Hauptschlüssel unterstützen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
</td></tr></table>

**Beschreibung**

Tastaturen, mit die eine Kopplung vereinfacht Secure implementiert, müssen die Authentifizierungsmethode Hauptschlüssel unterstützen.

### <a name="deviceconnectivitybluetoothdevicessupportbluetooth21"></a>Device.Connectivity.BluetoothDevices.SupportBluetooth21

*Devicesthat Unterstützung Bluetooth muss die Anforderungen Bluetooth 2.1 implementieren.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
</td></tr></table>

**Beschreibung**

Bluetooth-Geräte müssen mit der Bluetooth 2.1 + in Bluetooth-Version 2.1 + EDR Spezifikationen beschriebenen EDR Anforderungen entsprechen.

