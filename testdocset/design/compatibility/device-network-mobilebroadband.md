---
title: Device.Network.MobileBroadband
Description: Requirements.
ms.assetid: 
MSHAttr: 
author: beneluxboy
ms.openlocfilehash: 0925ce9bd92ec4e19423ca607add7ec77b7abd6b
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="devicenetworkmobilebroadband"></a>Device.Network.MobileBroadband

 - [Device.Network.MobileBroadband.CDMA](#device.network.mobilebroadband.cdma)
 - [Device.Network.MobileBroadband.FirmwareUpdater](#device.network.mobilebroadband.firmwareupdater)
 - [Device.Network.MobileBroadband.GSM](#device.network.mobilebroadband.gsm)

<a name="device.network.mobilebroadband.cdma"></a>
## <a name="devicenetworkmobilebroadbandcdma"></a>Device.Network.MobileBroadband.CDMA

*Mobile Breitband*

### <a name="devicenetworkmobilebroadbandcdmacomplywithbasereq"></a>Device.Network.MobileBroadband.CDMA.ComplyWithBaseReq

*Mobile Breitband-Geräte müssen die folgenden Basis Anforderungen entsprechen.*

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

Mobile Breitband-Geräte müssen die folgenden Basis Anforderungen entsprechen:

-   NDIS 6.30 und Mobile Breitband-Treiber Modell Spezifikation Anforderungen in der Windows-Treiberkits entsprechen MUSS.

-   Power Management Spezifikationen entsprechen MUSS.

-   MUSS das Leistungsziel für verschiedene Vorgang für die verschiedenen Klasse von Geräten in der Spezifikation für Mobile Breitband-Treiber Modell erfüllen.

-   Mobile Breitband Gerätetreiber muss implementieren und die NDIS 6.30 und Mobile Breitband-Treiber Modellspezifikationen entsprechen. Alle empfohlene Implementierung gemäß den Mobile Breitband-Treiber Modellspezifikationen muss implementiert werden. Beachten Sie, dass Microsoft MB-Klassentreiber mit den oben beschriebenen Anforderungen kompatibel ist. Ein mobiles Gerät Breitband muss Richtlinie zur Verwaltung der Power unterstützen, wie in der Netzwerk-Gerät Klasse Power Management Verweis-Spezifikation, Version 2.0 beschrieben. Ein Gerät muss nach der verschiedenen OS Power-Verwaltungsvorgänge funktionsfähig sein. Ein Gerät muss die Leistungsziele beschrieben, die in der Spezifikation für Mobile Breitband-Treiber Modell erfüllen.

*Hinweise zum Entwurf*

Hilfreiche Links: Mobile Breitband-Treiber Modellspezifikationen <http://msdn.microsoft.com/en-us/library/ff560543.aspx> Network Device-Klasse Power Management Verweis Specification <http://download.microsoft.com/download/1/6/1/161ba512-40e2-4cc9-843a-923143f3456c/netpmspc.rtf>

### <a name="devicenetworkmobilebroadbandcdmafwcomplywithmbspec"></a>Device.Network.MobileBroadband.CDMA.FWComplyWithMBSpec

*USB-Schnittstelle-basierten CDMA-Klasse des Mobile Breitband Gerätefirmware einhalten muss mit USB-des IF Mobile Breitband-Schnittstelle Modell Spezifikation.*

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

Die USB-Schnittstelle-basierten CDMA Klasse des Mobile Breitband Gerät Firmware Implementierung erfüllen muss mit den USB-des IF Mobile Breitband Schnittstelle Modell (MBIM)-Spezifikation. Keine zusätzliche IHV-Treiber für die Funktionalität des Geräts benötigt werden, und das Gerät mit Microsofts Mobile Breitband (MB) Klasse Treiber Implementierung arbeiten muss.

Gerätefirmware auch entsprechen den MBIM Fehlerverzeichnis\* zusätzlich zu der MBIM 1.0-Spezifikation. In bestimmten müssen die folgenden Elemente in MBIM Fehlerverzeichnis mit kompatibel sein:

 - MEFD (MB Extended funktionale Deskriptor): Geräte mit bestimmten Firmware Operator müssen die richtige Größe MTU gemäß den Mobilfunkbetreiber Netzwerk für zertifizierte Geräte Netzbetreiber melden.

 - \*USB-IF-Verknüpfung, die nur von NCM DWG Mitglieder zugegriffen werden kann. Diese fehlerverzeichnis werden veröffentlicht werden, nachdem er genehmigt wird.

Weitere Details:

Mobile Breitband-Schnittstelle Modell Spezifikation: <http://www.usb.org/developers/devclass_docs/MBIM10.zip>

Spezifikation der mobilen Breitband-Treiber-Modell: <http://msdn.microsoft.com/library/windows/hardware/ff560543.aspx>

### <a name="devicenetworkmobilebroadbandcdmaidentitymorphing"></a>Device.Network.MobileBroadband.CDMA.IdentityMorphing

*Mobile Breitband-Geräten muss Identität Morphing unterstützen.*

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

Mobile Breitband anhand des Protokolls USB-Geräten müssen Identity Morphing unterstützen. Implementierung dieser Anforderung in der Gerätefirmware kann Gerätehersteller Vorteile der Microsoft Posteingang MB Klassen-Treiber in Windows 8 und die Flexibilität ihrer eigenen Treiber für früherer Versionen des Windows-Betriebssystemen Version 7 und unter dem übernehmen. Links zu den jeweiligen Spezifikationen werden im Abschnitt zusätzliche Informationen bereitgestellt. Zusätzliche Informationen:-Identity Morphing Spezifikation: finden Sie im MSDN.

### <a name="devicenetworkmobilebroadbandcdmaloopback"></a>Device.Network.MobileBroadband.CDMA.Loopback

*Mobile Breitbandgeräte basierend auf USB-Protokoll muss Loopback-Funktionalität für Leistung und Testen von Nutzlast Konformität implementieren.*

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

Mobile Breitband anhand des Protokolls USB-Geräte müssen in der Gerätefirmware Loopback-Funktionalität wie in der Spezifikation implementieren. Beachten Sie, dass Loopback-Funktionalität für das Datenpaket nur getestet wird, wie er in der Leistung kritischen Pfad angegeben ist. Geräte müssen den Loopbacktest für leistungsanforderungen übergeben.

Insbesondere muss Geräte unterstützen kombinierten Durchsatz von 100 Mbit/s (50 Mbit/s Uplink / downlink-50 Mbit/s) oder höher und bis zu 5 % Verlust Rate. Links zu den jeweiligen Spezifikationen werden im Abschnitt zusätzliche Informationen bereitgestellt.

Zusätzliche Informationen:

Loopback – Handbuch zur Implementierung für Gerätefirmware: <http://msdn.microsoft.com/en-us/library/windows/hardware/hh975390.aspx>

MB Miniport-Treiber Leistungsanforderungen: <http://msdn.microsoft.com/en-us/library/windows/hardware/ff557193.aspx>

### <a name="devicenetworkmobilebroadbandcdmamulticarrierfunctionality"></a>Device.Network.MobileBroadband.CDMA.MultiCarrierFunctionality

*Mobile Breitband-Geräte, die mit mehreren Netzbetreiber Feature unterstützen müssen mit mehreren Netzbetreiber Funktionalität unterstützt.*

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

Breitband Mobile Geräte, die mit mehreren Netzbetreiber Feature unterstützen müssen die Funktionalität mit mehreren Netzbetreiber unterstützen und sollten auch die folgenden Schritte aus:

-   Müssen die in der Spezifikation für Mobile Breitband-Treiber Modell verfügbar mit mehreren Netzbetreiber leistungsanforderungen erfüllen.

-   Muss auf dem Bus bleiben beim home Anbieter zu ändern.

-   Alle anwendbaren Logo-Tests für die verschiedenen Mobilfunk-Klasse-Technologien, die eine Verbindung mit das Gerät kann muss erfolgreich übergeben werden.

-   Breitband Mobilgeräten mit mehreren Netzbetreiber Feature unterstützen müssen mit mehreren Netzbetreiber leistungsanforderungen, die in der Spezifikation der mobilen Breitband-Treiber-Modell angegeben erfüllen. Mobile Breitband-Geräte, die mit mehreren Netzbetreiber Feature unterstützen müssen nicht zu einen Bus / erneute Geräteenumeration oder Power Zurücksetzen des Geräts, die in Plug & Play-erneute-Enumeration an den Windows entstehen kann, wenn die Startseite Anbieter zu ändern. Wenn das Gerät GSM und CDMA Mobilfunk-Klasse Technologien unterstützt, wird das Gerät werden, sowohl GSM als auch CDMA ausgeführt muss Logo-Tests. Damit dies ordnungsgemäß behandelt werden muss der Speicherort des Logos Test Ausführung in der Reichweite des mindestens ein g/M2 und ein CDMA Mobilfunk-Klasse Technologien sein.

### <a name="devicenetworkmobilebroadbandcdmareliablecsconnectivity"></a>Device.Network.MobileBroadband.CDMA.ReliableCSConnectivity

*Drahtloses WAN-Gerät auf Systeme, die Standbymodus verbunden unterstützen muss zuverlässige Verbindung im Standbymodus verbunden übermitteln.*

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

Das Gerät Übergänge zwischen D0 und D3 nahtlos warme Staaten während in verbunden Standby (CS). Das Gerät wird L2 & L3-Konnektivität in CS verwaltet. Das Gerät reaktiviert auf übereinstimmenden nur Aktivierungsmuster. Es gibt keine falsche reaktiviert im CS aus. Die Aktivierung Pakete werden ohne Verzögerung oder Pufferung übermittelt. RealTimeCommunication-apps bleiben Sie in CS über IPv4 und IPv6.

### <a name="devicenetworkmobilebroadbandcdmasupportusbselectivesuspend"></a>Device.Network.MobileBroadband.CDMA.SupportUSBSelectiveSuspend

*USB-basierte müssen Breitband Unterstützung von mobilen Geräten Windows Implementierung der USB selektive angehalten werden soll.*

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

USB-basierten mobile Breitband-Geräten müssen Windows unterstützen Implementierung der USB selektive anhalten (SS). Keine alternativen SS USB-Implementierung ist zulässig.

### <a name="devicenetworkmobilebroadbandcdmasupportwakeonmb"></a>Device.Network.MobileBroadband.CDMA.SupportWakeOnMB

*Mobile Breitband-Klasse von Geräten muss die folgenden Aktivierung auf mobilen Breitband-Funktionen unterstützen.*

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

Mobile Breitband-Klasse von Geräten MUSS die folgenden Aktivierung auf mobilen Breitband-Funktionen unterstützen.

-   Geräten MÜSSEN 32 Bitmap Remoteaktivierung Muster 128 Byte unterstützen.

-   Geräte MÜSSEN das System registrieren Zustand ändern Sie auf aktivieren.

-   Geräte MÜSSEN aktiviert das System auf Medien verbinden.

-   Geräte MÜSSEN das System auf Medien trennen aktivieren.

-   G/M2 und CDMA-Klasse von Geräten MUSS aktiviert werden, das System auf eine eingehende SMS-Nachricht empfangen.

-   Geräte, DIE USSD MUSS unterstützen, aktiviert das System auf eine USSD Nachricht empfangen.

-   Geräte MÜSSEN Remoteaktivierung Paket Angabe unterstützen. NIC sollte das Paket, wodurch die Aktivierung auf Hardware und übergeben, wenn das Betriebssystem für bereit ist es empfängt, cache.

Mobile Geräte-Klasse muss auf mobilen Breitband Remoteaktivierung unterstützen. Ein Gerät sollte das System oben erwähnten Ereignisse auf aktivieren. Hinweis Diese Remoteaktivierung über USSD ist nur erforderlich, wenn das Gerät meldet, dass es USSD; unterstützt Andernfalls ist optional. Finden Sie unter den folgenden MSDN-Dokumentationen für Weitere Informationen am SMS und registrieren Sie Zustand Remoteaktivierung Ereignisse.

1. NDIS\_STATUS\_WWAN\_REGISTRIEREN\_ZUSTAND

2. NDIS\_STATUS\_WWAN\_SMS\_EMPFANGEN

<a name="device.network.mobilebroadband.firmwareupdater"></a>
## <a name="devicenetworkmobilebroadbandfirmwareupdater"></a>Device.Network.MobileBroadband.FirmwareUpdater

*Mobile Breitband*

### <a name="devicenetworkmobilebroadbandfirmwareupdaterfirmwareupgrade"></a>Device.Network.MobileBroadband.FirmwareUpdater.FirmwareUpgrade

*USB-Schnittstelle basierend g/M2 und CDMA-Klasse der mobilen Breitband-Geräte, die Microsoft Firmware Update Plattform erfüllen muss implementieren, Firmware-Dienst-ID und ein Treiber UMDF basierend Firmware aktualisieren, um die aktualisierte Firmware Nutzlast auf das Gerät.*

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

USB-Schnittstelle basieren g/M2, und CDMA Klasse der mobilen Breitband Geräte, die Microsoft Firmware Update Plattform erfüllen muss Firmware ID-Gerät-Dienst (um schnell auf MSDN veröffentlicht werden) und einen UMDF basierend Firmware Update-Treiber (Richtlinien und Beispiel schnell auf MSDN veröffentlicht werden soll) für die Aktualisierung Firmware Nutzlast das Gerät implementieren.

Weitere Informationen

<a name="device.network.mobilebroadband.gsm"></a>
## <a name="devicenetworkmobilebroadbandgsm"></a>Device.Network.MobileBroadband.GSM

*Mobile Breitband*

### <a name="devicenetworkmobilebroadbandgsmcomplywithbasereq"></a>Device.Network.MobileBroadband.GSM.ComplyWithBaseReq

*Mobile Breitband-Geräte müssen die folgenden Basis Anforderungen entsprechen.*

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

Mobile Breitband-Geräte müssen die folgenden Basis Anforderungen entsprechen:

-   NDIS 6.30 und Mobile Breitband-Treiber Modell Spezifikation Anforderungen in der Windows-Treiberkits entsprechen MUSS.

-   Power Management Spezifikationen entsprechen MUSS.

-   MUSS das Leistungsziel für verschiedene Vorgang für die verschiedenen Klasse von Geräten in der Spezifikation für Mobile Breitband-Treiber Modell erfüllen.

-   Mobile Breitband Gerätetreiber muss implementieren und die NDIS 6.30 und Mobile Breitband-Treiber Modellspezifikationen entsprechen. Empfohlene Implementierung gemäß den Anforderungen Mobile Breitband-Treiber Modellspezifikationen implementiert werden. Beachten Sie, dass Microsoft MB-Klassentreiber auf oben Anforderungen kompatibel ist. Ein mobiles Gerät Breitband muss Richtlinie zur Verwaltung der Power unterstützen, wie in der Netzwerk-Gerät Klasse Power Management Verweis-Spezifikation, Version 2.0 beschrieben. Gerät muss nach der verschiedenen OS Power-Verwaltungsvorgänge funktionsfähig sein. Gerät muss die Leistungsziele beschrieben, die in der Spezifikation für Mobile Breitband-Treiber Modell erfüllen.

*Hinweise zum Entwurf*

Hilfreiche Links: Mobile Breitband-Treiber Modellspezifikationen <http://msdn.microsoft.com/en-us/library/ff560543.aspx> Network Device-Klasse Power Management Verweis Specification <http://download.microsoft.com/download/1/6/1/161ba512-40e2-4cc9-843a-923143f3456c/netpmspc.rtf>

### <a name="devicenetworkmobilebroadbandgsmeapsim"></a>Device.Network.MobileBroadband.GSM.EAPSIM

*G/M2 Klasse Breitband Mobile Geräte, die die extensible Protokoll Authentifizierungsmethode für die Zugriffszeichenfolge g/M2 (EAP-SIM) unterstützen muss EAP-SIM definiert in RFC 4186 unterstützen.*

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

G/M2 Geräte, die EAP-SIM unterstützen müssen EAP-SIM unterstützen, wie in RFC 4186 definiert.

### <a name="devicenetworkmobilebroadbandgsmfwcomplywithmbspec"></a>Device.Network.MobileBroadband.GSM.FWComplyWithMBSpec

*USB-Schnittstelle-basierten g/M2 Klasse des Mobile Breitband Gerätefirmware einhalten muss mit USB-des IF Mobile Breitband-Schnittstelle Modell Spezifikation.*

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

USB-Schnittstelle-basierten g/M2-Klasse des Mobile Breitband Gerät Firmware Implementierung entsprechen muss mit der USB-des IF Mobile Breitband Schnittstelle Modell (MBIM)-Spezifikation. Keine zusätzliche IHV-Treiber für die Funktionalität des Geräts benötigt werden, und das Gerät mit Microsofts Mobile Breitband (MB) Klasse Treiber Implementierung arbeiten muss.

Gerätefirmware auch entsprechen den MBIM Fehlerverzeichnis\* zusätzlich zu der MBIM 1.0-Spezifikation. In bestimmten müssen die folgenden Elemente in MBIM Fehlerverzeichnis mit kompatibel sein:

-   MEFD (MB Extended funktionale Deskriptor): Geräte mit bestimmten Firmware Operator müssen die richtige Größe MTU gemäß den Mobilfunkbetreiber Netzwerk für zertifizierte Geräte Netzbetreiber melden.

\*USB-IF-Verknüpfung, die nur von NCM DWG Mitglieder zugegriffen werden kann. Diese fehlerverzeichnis werden veröffentlicht werden, nachdem er genehmigt wird.

Weitere Details:

Mobile Breitband-Schnittstelle Modell Spezifikation: <http://www.usb.org/developers/devclass_docs/MBIM10.zip>

Spezifikation der mobilen Breitband-Treiber-Modell: <http://msdn.microsoft.com/library/windows/hardware/ff560543.aspx>

### <a name="devicenetworkmobilebroadbandgsmidentitymorphing"></a>Device.Network.MobileBroadband.GSM.IdentityMorphing

*Breitband MÜSSEN Identität Morphing Unterstützung von mobilen Geräten.*

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

Breitband müssen basierend auf USB-Protokoll Identität Morphing Unterstützung von mobilen Geräten. Implementierung dieser Anforderung in der Gerätefirmware kann Gerätehersteller Vorteile der Microsoft Posteingang MB Klassen-Treiber in Windows 8 und die Flexibilität ihrer eigenen Treiber für früherer Versionen des Windows-Betriebssystemen Version 7 und unter dem übernehmen. Links zu den jeweiligen Spezifikationen werden im Abschnitt zusätzliche Informationen bereitgestellt.

Zusätzliche Informationen:-Identity Morphing Spezifikation: finden Sie im MSDN.

### <a name="devicenetworkmobilebroadbandgsmloopback"></a>Device.Network.MobileBroadband.GSM.Loopback

*Breitband Mobilgeräten basierend auf USB-Protokoll MÜSSEN Loopback-Funktionalität für Leistung und Testen von Nutzlast Konformität implementieren.*

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

Breitband Mobilgeräten basierend auf dem USB-Protokoll müssen Loopback-Funktionalität wie in der Spezifikation in der Gerätefirmware implementieren. Beachten Sie, dass Loopback-Funktionalität für das Datenpaket nur getestet wird, wie er in der Leistung kritischen Pfad angegeben ist. Geräte müssen den Loopbacktest für leistungsanforderungen übergeben. Insbesondere muss Geräte unterstützen kombinierten Durchsatz von 100 Mbit/s (50 Mbit/s Uplink / downlink-50 Mbit/s) oder höher und bis zu 5 % Verlust Rate.

Links zu den jeweiligen Spezifikationen werden im Abschnitt zusätzliche Informationen bereitgestellt.

Zusätzliche Informationen:

Loopback – Handbuch zur Implementierung für Gerätefirmware: <http://msdn.microsoft.com/en-us/library/windows/hardware/hh975390.aspx>

MB Miniport-Treiber Leistungsanforderungen: <http://msdn.microsoft.com/en-us/library/windows/hardware/ff557193.aspx>

### <a name="devicenetworkmobilebroadbandgsmmulticarrierfunctionality"></a>Device.Network.MobileBroadband.GSM.MultiCarrierFunctionality

*Mobile Breitband-Geräte, die mit mehreren Netzbetreiber Feature unterstützen müssen mit mehreren Netzbetreiber Funktionalität unterstützt.*

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

Mobile Breitband Geräte, die mit mehreren Netzbetreiber Feature unterstützen müssen die Funktionalität mit mehreren Netzbetreiber unterstützen und sollten auch die folgenden Schritte aus:

Müssen die in der Spezifikation für Mobile Breitband-Treiber Modell verfügbar mit mehreren Netzbetreiber leistungsanforderungen erfüllen.

Muss auf dem Bus bleiben beim home Anbieter zu ändern.

Alle anwendbaren Logo-Tests für die verschiedenen Mobilfunk-Klasse-Technologien, die eine Verbindung mit das Gerät kann muss erfolgreich übergeben werden.

Breitband Mobilgeräten mit mehreren Netzbetreiber Feature unterstützen müssen mit mehreren Netzbetreiber leistungsanforderungen, die in der Spezifikation der mobilen Breitband-Treiber-Modell angegeben erfüllen. Mobile Breitband-Geräte, die mit mehreren Netzbetreiber Feature unterstützen müssen nicht zu einen Bus / erneute Geräteenumeration oder Power Zurücksetzen des Geräts, die in Plug & Play-erneute-Enumeration an den Windows entstehen kann, wenn die Startseite Anbieter zu ändern. Wenn das Gerät GSM und CDMA Mobilfunk-Klasse Technologien unterstützt, wird das Gerät werden, sowohl GSM als auch CDMA ausgeführt muss Logo-Tests. Damit dies ordnungsgemäß behandelt werden muss der Speicherort des Logos Test Ausführung in der Reichweite des mindestens ein g/M2 und ein CDMA Mobilfunk-Klasse Technologien sein.

 

### <a name="devicenetworkmobilebroadbandgsmmultiplepdpcontext"></a>Device.Network.MobileBroadband.GSM.MultiplePDPContext

*Unterstützung für mehrere PDP-Kontext*

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

Mit diesem Feature können apps für Windows über verschiedene PDP-Kontexte (virtuelle Kanäle) in mobilen Netzwerken kommunizieren. Mobile Operatoren verwenden unterschiedliche PDP-Kontexte zum Erstellen der differenzierten Erfahrungen und innovative Services. Drittanbieter-app-Entwickler können mit diesem Feature können hochwertige VOIP erstellen und Videostreaming guter Partnerschaft mit Mobilfunkbetreiber.

Kann mehrere PDP-Kontexte Gerätefirmware müssen der [MBIM-Spezifikation](http://www.usb.org/developers/devclass_docs/MBIM10.zip)entsprechen. Insbesondere sollten Gerätefirmware mehrere IP-Datenströme dargelegt sind im Abschnitt 10.5.12.1 in der Spezifikation für MBIM unterstützen. Dies betrifft die Unterstützung der Steuerelement-Implementierung der CIDs und IP-Datenströme für vollständige Unterstützung mehrerer PDP-Kontexte.

Gerätefirmware muss für die Verwendung durch Windows insgesamt 8 dual Bearer (IPv4 und IPv6) PDP-Kontexte unterstützen.

Dazu gehören 1 für Internet und 7 für Operator Apps zusätzliche.

Geräte sind nicht erforderlich, um die internen verfügbar zu machen, Firmware PDP Kontexte für SMS und anderen Administration Kontext Windows verwaltet.

Gerätefirmware sollte nutzen Host OS Anforderung für einen PDP-Kontext können, der bereits in seiner Firmware ordnungsgemäß behandelt werden intern verwalteten Gerät ist.

Sollten weiterhin Gerätefirmware abstrakten SMS PDP-Kontexte und Umleiten der SMS CIDs unabhängig von der Bearer verwendet werden, darunter.

### <a name="devicenetworkmobilebroadbandgsmreliablecsconnectivity"></a>Device.Network.MobileBroadband.GSM.ReliableCSConnectivity

*Drahtloses WAN-Gerät auf Systeme, die Standbymodus verbunden unterstützen muss zuverlässige Verbindung im Standbymodus verbunden übermitteln.*

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

Das Gerät Übergänge zwischen D0 und D3 nahtlos warme Staaten während in verbunden Standby (CS). Das Gerät wird L2 & L3-Konnektivität in CS verwaltet. Das Gerät reaktiviert auf übereinstimmenden nur Aktivierungsmuster. Es gibt keine falsche reaktiviert im CS aus. Die Aktivierung Pakete werden ohne Verzögerung oder Pufferung übermittelt. RealTimeCommunication-apps bleiben Sie in CS über IPv4 und IPv6.

### <a name="devicenetworkmobilebroadbandgsmsupportfastdormancy"></a>Device.Network.MobileBroadband.GSM.SupportFastDormancy

*Die Klasse g/M2 Breitband Mobile Geräte muss Fast winterlichen Mechanismus unterstützen, gemäß 3GPP in Version 8.*

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

Breitband Mobilgeräten müssen den fast winterlichen Mechanismus implementieren, wie in Revision 8 3GPP definiert.  Fast winterlichen ist eine Batterie Leben einsparungen Mechanismus für Geräte UE (Gerät des Benutzers), der die Geräte im Netzwerk in einem Kanal Energiesparmodus einzusetzen anfordern können. UE sendet (mit dem Netzwerk durch die UE gesendete) SIGNALISIERUNG VERBINDUNG VERSION ANGABE (SCRI) Nachrichten mit der IE "Signale Verbindung Version Angabe Ursache" vorhanden und auf "UE angefordert PS Daten Sitzungsende".

### <a name="devicenetworkmobilebroadbandgsmsupportusbselectivesuspend"></a>Device.Network.MobileBroadband.GSM.SupportUSBSelectiveSuspend

*USB basierte Breitband Mobile Geräte, Windows unterstützen müssen-Implementierung von USB selektive angehalten werden soll.*

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

USB-basierte Breitband Mobile Geräte unterstützen müssen Windows-Implementierung von USB-selektive anhalten (SS). Keine alternativen SS USB-Implementierung ist zulässig.

### <a name="devicenetworkmobilebroadbandgsmsupportwakeonmb"></a>Device.Network.MobileBroadband.GSM.SupportWakeOnMB

*Mobile Breitband-Klasse von Geräten muss die folgenden Aktivierung auf mobilen Breitband-Funktionen unterstützen.* 

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

Mobile Breitband-Klasse von Geräten muss die folgenden Aktivierung auf mobilen Breitband-Funktionen unterstützen.

-   Geräten MÜSSEN 32 Bitmap Remoteaktivierung Muster 128 Byte unterstützen.

-   Geräte MÜSSEN das System registrieren Zustand ändern Sie auf aktivieren.

-   Geräte MÜSSEN aktiviert das System auf Medien verbinden.

-   Geräte MÜSSEN das System auf Medien trennen aktivieren.

-   G/M2 und CDMA-Klasse von Geräten MUSS aktiviert werden, das System auf eine eingehende SMS-Nachricht empfangen.

-   Geräte, DIE USSD MUSS unterstützen, aktiviert das System auf eine USSD Nachricht empfangen.

-   Geräte MÜSSEN Remoteaktivierung Paket Angabe unterstützen. NIC sollte das Paket, wodurch die Aktivierung auf Hardware und übergeben, wenn das Betriebssystem für bereit ist es empfängt, cache.

Mobile Breitband-Klasse von Geräten muss die Aktivierung auf mobilen Breitband unterstützen. Ein Gerät sollte das System oben erwähnten Ereignisse auf aktivieren. Hinweis Diese Remoteaktivierung über USSD ist nur erforderlich, wenn das Gerät meldet, dass es USSD; unterstützt Andernfalls ist optional. Finden Sie unter den folgenden MSDN-Dokumentationen für Weitere Informationen am SMS und registrieren Sie Zustand Remoteaktivierung Ereignisse.

1.  NDIS\_STATUS\_WWAN\_REGISTRIEREN\_ZUSTAND

2.  NDIS\_STATUS\_WWAN\_SMS\_EMPFANGEN

### <a name="devicenetworkmobilebroadbandgsmussd"></a>Device.Network.MobileBroadband.GSM.USSD

*Die Klasse g/M2 mobiler Breitband Geräte, die unstrukturierten zusätzliche Service Daten (USSD) implementieren muss USSD basierend auf der Mobile Breitband Driver Model unterstützen.*

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

Windows Mobile Breitband Driver Model wird aktualisiert die vollständige Unterstützung der USSD Nachrichten senden und empfangen. Geräte, die USSD implementieren müssen USSD basierend auf der Mobile Breitband Driver Model unterstützen.

