---
title: Device.BusController.NFC
Description: Requirements.
ms.assetid: 
MSHAttr: 
author: beneluxboy
ms.openlocfilehash: b75a40f52f87087c798d80afe740ae0540693b2a
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="devicebuscontrollernfc"></a>Device.BusController.NFC

 - [Device.BusController.NFC](#device.buscontroller.nfc)
 - [Device.BusController.NFC.NearFieldProximity](#device.buscontroller.nfc.nearfieldproximity)
 - [Device.BusController.NFC.RadioManagement](#device.buscontroller.nfc.radiomanagement)
 - [Device.BusController.NFC.SecureElement.HCE](#device.buscontroller.nfc.secureelement.hce)
 - [Device.BusController.NFC.SmartCard](#device.buscontroller.nfc.smartcard)
 - [Device.BusController.NFC.SecureElement.UICC](#device.buscontroller.nfc.secureelement.uicc)

<a name="device.buscontroller.nfc"></a>
## <a name="devicebuscontrollernfc"></a>Device.BusController.NFC

Es empfiehlt sich, dass IHVs NFK Clienttreiber diese Schnittstelle mit dem [Microsoft NFK Klasse Erweiterung (CX)](https://msdn.microsoft.com/en-us/library/windows/hardware/dn905534.aspx)erstellen. Diese Schnittstelle wird ab Juni 2017 obligatorisch sein.

<a name="device.buscontroller.nfc.nearfieldproximity"></a>
## <a name="devicebuscontrollernfcnearfieldproximity"></a>Device.BusController.NFC.NearFieldProximity

Jeder Technologie, die implementiert die GUID\_DEVINTERFACE\_NFP Treiber-Schnittstelle in Anforderungen NFP Gerätetreibers angegeben wird als NFP Anbieter definiert und müssen alle in der Nähe Feld Nähe DDI implementierungsanforderungen innerhalb [der Spezifikation](https://msdn.microsoft.com/en-us/library/windows/hardware/jj866064.aspx)erfüllen.

### <a name="devicebuscontrollernfcnearfieldproximityattribute"></a>Device.BusController.NFC.NearFieldProximity.Attribute

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

Der NFP Anbieter muss maximale Nachrichtengröße nicht weniger als 10 KB und Übertragungsrate nicht kleiner als 16 KB pro Sekunde unterstützen.

### <a name="devicebuscontrollernfcnearfieldproximityevent"></a>Device.BusController.NFC.NearFieldProximity.Event

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

Der Anbieter NFP muss Clients DeviceArrived und DeviceDeparted Ereignisse beim Empfang oder weggehen von einem annähernd Gerät empfangen aktivieren.

### <a name="devicebuscontrollernfcnearfieldproximityndef"></a>Device.BusController.NFC.NearFieldProximity.NDEF

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

Der Anbieter NFP muss das Protokoll NDEF gemäß vom NFK Forum in die NDEF Spezifikation V1. 0 unterstützen.

### <a name="devicebuscontrollernfcnearfieldproximitypeertopeer"></a>Device.BusController.NFC.NearFieldProximity.PeerToPeer

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

Der Anbieter NFP muss unterstützen übertragen und empfangende von Daten über das Forum NFK logischen Link Control-Protokoll (LLCP) V1. 1 und v1. 0 einfache NDEF Exchange-Protokoll (SNEP) definiert.

### <a name="devicebuscontrollernfcnearfieldproximitypublish"></a>Device.BusController.NFC.NearFieldProximity.Publish

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

Der Anbieter NFP muss unterstützt, veröffentlichen und Übertragen von Nachrichten.

### <a name="devicebuscontrollernfcnearfieldproximityreliability"></a>Device.BusController.NFC.NearFieldProximity.Reliability

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

Der Anbieter NFP muss zuverlässig lesen und Schreiben von Tags.

### <a name="devicebuscontrollernfcnearfieldproximitysubscribe"></a>Device.BusController.NFC.NearFieldProximity.Subscribe

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

Der Anbieter NFP muss möglicherweise empfangen und Zustellen von Nachrichten an den abonnierten Clients.

### <a name="devicebuscontrollernfcnearfieldproximitytagoperation"></a>Device.BusController.NFC.NearFieldProximity.TagOperation

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

Der Anbieter NFP muss möglicherweise lesen, schreiben und Formatieren von Tags sowie Tags auf schreibgeschützt festlegen.

<a name="device.buscontroller.nfc.radiomanagement"></a>
## <a name="devicebuscontrollernfcradiomanagement"></a>Device.BusController.NFC.RadioManagement

Die Radio Management DDI ermöglicht es dem Aufrufer den Gerätetreiber NFK zum Festlegen der Power-Zustands für den Sender Nähe des Geräts NFK. Ein NFK Gerätetreiber muss die DDIs gemäß Implementieren der [Dokument Radio Management DDI.](https://msdn.microsoft.com/en-us/library/windows/hardware/dn905577.aspx)

### <a name="devicebuscontrollernfcradiomanagementbase"></a>Device.BusController.NFC.RadioManagement.Base

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

Der Gerätetreiber NFK muss festlegen, die den Status der Abstand zwischen den Rändern und sichere Element Sender des Geräts NFK können.

<a name="device.buscontroller.nfc.secureelement.hce"></a>
## <a name="devicebuscontrollernfcsecureelementhce-if-implemented"></a>Device.BusController.NFC.SecureElement.HCE (sofern implementiert)

Die sichere Element DDI können Anrufer an den Gerätetreiber NFK auflisten, kommunizieren mit, und Konfigurieren der sicheren Elemente vom Gerät zugegriffen werden. 

Jeder Technologie, die die GUID implementiert\_DEVINTERFACE\_NFCSE Treiber-Schnittstelle im Dokument Secure Element DDI angegeben wird als Provider NFK Secure-Element definiert und alle Secure Element DDI Implementierung-Anforderungen, die innerhalb [der Spezifikation](https://msdn.microsoft.com/en-us/library/windows/hardware/dn905485.aspx)erfüllen. 

Die sichere Element DDI ermöglicht sicheren Elemente Host Karte Emulation (HCE) basiert. Mit HCE werden Daten direkt an Anwendungen, die auf dem Host CPU weitergeleitet.

### <a name="devicebuscontrollernfcsecureelementhcebase"></a>Device.BusController.NFC.SecureElement.HCE.Base

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

Ein NFK Secure Element-Anbieter, DER HCE basierten Karte Emulation unterstützt, muss die Routingtabelle des Listen-Modus konfigurieren, HCE-basierte Anwendungen NFCC Funktionen und Routendaten melden können.

### <a name="devicebuscontrollernfcsecureelementhceevent"></a>Device.BusController.NFC.SecureElement.HCE.Event

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

Ein NFK Secure Element-Anbieter, DER HCE basierten Karte Emulation unterstützt, muss Unterstützung von Client-Abonnements für Ereignisse und muss möglicherweise Ereignisse auslösen, um anzugeben, Vorkommen für HCE wird aktiviert und deaktiviert.

### <a name="devicebuscontrollernfcsecureelementhcereliability"></a>Device.BusController.NFC.SecureElement.HCE.Reliability

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

Ein sichere NFK-Element-Anbieter, dass unterstützt das HCE basierten Karte Emulation kann muss zuverlässig Weiterleitung von Daten an den Host oder ein anderes Element sichere auf dem aktuellen entsprechend Abhören Modus routingtabellenkonfiguration***.***

<a name="device.buscontroller.nfc.smartcard"></a>
## <a name="devicebuscontrollernfcsmartcard"></a>Device.BusController.NFC.SmartCard

Die Smartcard-DDI können Anrufer der Gerätetreiber NFK auf NFK kontaktlose Smart Karten auf niedriger Ebene Smartcard-Vorgänge durchführen. Dazu gehören hört Karte Ankunft/weggehen Benachrichtigungen, beim Lesen der Metadaten der Smartcard wie ATR, UID und Historische Bytes, Ausführen von Vorgängen auf die bestimmte NFK Karte APDUs als auch die Unterstützung zum Übersetzen von APDUs Low-Level-primitiven Befehle für einige ISO14443-4-kompatiblen Karten mit Lese-/Schreibzugriff.

Jeder Technologie, die die GUID implementiert\_DEVINTERFACE\_SMARTCARD\_READER-Treiber-Schnittstelle im Dokument Smartcard DDI angegeben ist definiert als Anbieter für die Smartcard-Leser und müssen die Smartcard DDI implementierungsanforderungen entsprechen innerhalb [der Spezifikation.](https://msdn.microsoft.com/en-us/library/windows/hardware/dn905602.aspx)

### <a name="devicebuscontrollernfcsmartcardattribute"></a>Device.BusController.NFC.SmartCard.Attribute

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

Smartcard-Leser Anbieter muss möglicherweise abrufen und Festlegen von Smartcard-Attribute.

### <a name="devicebuscontrollernfcsmartcarddataexchange"></a>Device.BusController.NFC.SmartCard.DataExchange

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

Der Anbieter Smartcard-Leser muss gemäß den PC/SC Standards mit unterstützten kontaktlose SmartCard-Karten miteinander kommunizieren können. Es muss Support für PC/SC transparenten Modus enthalten. Unterstützte kontaktlose SmartCard-Karten beinhalten: MIFARE klassische (optional), MIFARE Ultraleicht, Topasgrau, Symbol, ISO14443-A/B, Felica, ISO15693.

### <a name="devicebuscontrollernfcsmartcardstate"></a>Device.BusController.NFC.SmartCard.State

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

Der Smartcard-Leser Anbieter muss möglicherweise abrufen und Festlegen der kontaktlose SmartCard-Zustand.

<a name="device.buscontroller.nfc.secureelement.uicc"></a>
## <a name="devicebuscontrollernfcsecureelementuicc-if-implemented"></a>Device.BusController.NFC.SecureElement.UICC (sofern implementiert)

Die sichere Element DDI können Anrufer an den Gerätetreiber NFK aufzählen, kommunizieren mit, und Konfigurieren der sicheren Elemente vom Gerät zugegriffen werden.

Jeder Technologie, die die GUID implementiert\_DEVINTERFACE\_NFCSE-Treiber-Schnittstelle im Dokument Secure Element DDI angegeben wird als Provider NFK Secure-Element definiert und alle Secure Element DDI Implementierung-Anforderungen, die innerhalb [der Spezifikation](https://msdn.microsoft.com/en-us/library/windows/hardware/dn905485.aspx)erfüllen.

### <a name="devicebuscontrollernfcsecureelementuiccemulation"></a>Device.BusController.NFC.SecureElement.UICC.Emulation

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

Ein NFK Secure Element-Anbieter, DER UICC basierend Karte Emulation unterstützt, können miteinander und Konfigurieren der UICC muss und muss an den Client zum Verwalten von Karte Emulationsmodus exklusiven Zugriff gewähren.

### <a name="devicebuscontrollernfcsecureelementuiccenumeration"></a>Device.BusController.NFC.SecureElement.UICC.Enumeration

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

Ein sicheren Element NFK Anbieter, der Basis UICC Karte Emulation unterstützt muss alle sicheren Elemente durchlaufen, die vom Gerät zugegriffen werden.

### <a name="devicebuscontrollernfcsecureelementuiccevent"></a>Device.BusController.NFC.SecureElement.UICC.Event

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

Ein NFK Secure Element-Anbieter, DER UICC basierend Karte Emulation unterstützt, muss Client Abonnements für Ereignisse unterstützen und muss in der Lage, Ereignisse auslösen, um Vorkommen wie Transaktionen mit einer externen Reader anzugeben.

### <a name="devicebuscontrollernfcsecureelementuiccreliability"></a>Device.BusController.NFC.SecureElement.UICC.Reliability

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

Ein NFK Secure Element-Anbieter, DER UICC basierend Karte Emulation unterstützt, muss zuverlässig Emulationsmodus Karte zu aktivieren / deaktivieren können.
