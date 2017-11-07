---
title: Device.Connectivity.Network.VerticalPairing
Description: "Requirements. Stamm für frühere Rallye-Technologien."
ms.assetid: 
MSHAttr: 
author: beneluxboy
ms.openlocfilehash: edea4c352a63749cd2dfd0f10ac0be02fcd0424c
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
<!--
# Device.Connectivity.Network.VerticalPairing

 - [Device.Connectivity.Network.VerticalPairing](#device.connectivity.network.verticalpairing)
-->

<a name="device.connectivity.network.verticalpairing"></a>
##Device.Connectivity.Network.VerticalPairing

*Stamm für frühere Rallye-Technologien*

### <a name="deviceconnectivitynetworkverticalpairingwcn"></a>Device.Connectivity.Network.VerticalPairing.WCN

*Ein 802.11 netzwerkfähiges Gerät, das als eine Station (Station) arbeitet muss WCN NET implementieren und grundlegende 802.11 erfüllen.*

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

Ein 802.11 netzwerkfähiges Gerät funktioniert, die als eine Station (Station) muss die folgenden Anforderungen erfüllen:

-   Das Gerät muss WCN NET implementieren und die Spezifikation entsprechen.

-   Das Gerät muss WCN NET vertikal Paarung Extensions implementieren und geben Sie an, ob ein PnP-X-Transport-Protokoll unterstützt. Wenn das Gerät ein PnP-X-Transport-Protokoll unterstützt, müssen sie richtigen Eindeutiger Bezeichner (UUID) Ausrichtung sicherstellen.

-   Wenn WCN UFD implementiert ist, müssen sie die Spezifikation entsprechen.

-   Wenn das Gerät eine Anzeige, die eine vierstellige oder 8 Ziffern Zahl anzeigen kann hat, muss es eine dynamische Windows verbinden jetzt (WCN) PIN anzeigen, ohne Benutzereingriff unterstützen. Die PIN-NUMMER muss mindestens zwei Minuten nach das Gerät eine Nachricht M2D Wireless Provisioning Services (WPS) mit dem Wert von "Windows" bei WPS Modellname-Attributs erhält angezeigt werden.

-   Wenn das Gerät keine Darstellung, die eine vierstellige oder 8 Ziffern Zahl anzeigen kann verfügen, stellen eine physische Bezeichnung dargestellte, an das Gerät, das die PIN 8 Ziffern enthält und deutlich Etiketten die PIN Wert als eine PIN-NUMMER (beispielsweise ANHEFTEN: 12345670).

-   Das Gerät muss von Wi-Fi-Allianz, einschließlich Wi-Fi-Zertifizierung, Zertifizierung Wi-Fi Protected Access 2 (WPA2) und Wi-Fi Protected Setup Zertifizierung zertifiziert sein.

*Hinweise zum Entwurf*

Implementierungsdetails finden Sie unter der WCN-NET-Spezifikation unter <http://go.microsoft.com/fwlink/?LinkId=109371> und der WCN UFD Spezifikation unter <http://go.microsoft.com/fwlink/?LinkId=109372>.

Weitere Informationen finden Sie im Whitepaper "Installieren von Wi-Fi-Geräte verwenden Rally vertikale Paarung" unter <http://www.microsoft.com/whdc/connect/rally/WiFiVerticalPair.mspx>.

Weitere Informationen finden Sie unter <http://go.microsoft.com/fwlink/?LinkId=109373> und <http://go.microsoft.com/fwlink/?LinkId=109368>.

WCN NET ist erforderlich. WCN UFD ist optional und wird für die Abwärtskompatibilität mit Geräten, die entworfen wurden, um WCN Funktionen für Windows XP mit Service Pack 2 unterstützen in Windows unterstützt.

Ein Gerät verwendet WCN NET vertikal Paarung Extensions gibt an, dass seine unterstützt PnP-X. Das Gerät muss bieten ein einzelnes UUID, die sowohl die WCN NET Austausch bereitgestellt wird und die UPnP/Webdienste für Geräte (WSD) Gerätedatei oder das Gerät UPnP/WSD UUID, in das Attribut TransportUUID der WCN NET vertikal Paarung Erweiterung bereitzustellen. Die UUID, die in UPnP oder WSD bereitgestellten muss in Kleinbuchstaben (Nachkommastellen können auch verwendet werden).

Für Implementierungen WSD, die WSD UUID, die als Endpunktadresse ein Verweis bereitgestellt wird, und des Formulars muss <code>urn:uuid:</code>. Für Implementierungen UPnP wird wird die UPnP UUID als Stamm-Device UUID bereitgestellt.

