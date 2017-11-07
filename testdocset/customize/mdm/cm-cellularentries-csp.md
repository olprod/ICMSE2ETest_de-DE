---
title: CM\_CellularEntries CSP
description: CM\_CellularEntries CSP
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: f8dac9ef-b709-4b76-b6f5-34c2e6a3c847
ms.openlocfilehash: 02286a86dbd0f96cce58a1346daab396f5c49f94
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="cmcellularentries-csp"></a>CM\_CellularEntries CSP


Die CM\_CellularEntries Konfiguration-Dienstanbieter wird verwendet, um die Einträge General Packet Radio Service (GPRS) auf dem Gerät zu konfigurieren. Jedem Datenpunkt Access g/M2 definiert.

> **Hinweis**  
Dieses Dienstanbieters Konfiguration erfordert die ID\_CAP\_NETWORKING\_ADMIN-Funktion aus einer Anwendung der Netzwerk-Konfiguration zugegriffen werden.

 

Das folgende Diagramm zeigt die CM\_CellularEntries Service Provider Management-Konfigurationsobjekt im Strukturformat von Open Mobile Allianz-Clientbereitstellung (OMA CP) verwendet. Das Protokoll OMA DM wird mit dieser Konfigurationsdienstanbieter nicht unterstützt.

![cm\-Cellularentries Csp](images/provisioning-csp-cm-cellularentries.png)

<a href="" id="entryname"></a>**_entryname_**  
Definiert den Namen der Verbindung.

Der [CMPolicy Konfiguration-Dienstanbieter](cmpolicy-csp.md) verwendet den Wert der *Entryname* , um die Verbindung zu identifizieren, die eine Richtlinie zugeordnet ist und [CM\_ProxyEntries Konfigurationsdienstanbieter](cm-proxyentries-csp.md) wird den Wert der *Entryname* verwendet, um die Verbindung zu identifizieren, die einen Proxy zugeordnet ist.

<a href="" id="alwayson"></a>**AlwaysOn**  
Typ: int Gibt an, ob der Verbindungs-Manager automatisch versuchen, mit der APN verbinden, wenn keine Verbindung verfügbar ist.

Der Wert "0" gibt an, dass AlwaysOn nicht unterstützt wird und der Verbindungs-Manager wird nur dann Verbindung mit der APN, wenn eine Anwendung die Verbindung anfordert. Diese Einstellung wird für Anwendungen, die Sie gelegentlich eine Verbindung verwenden beispielsweise ein APN empfohlen, die nur MMS steuert.

Der Wert "1" gibt an, dass AlwaysOn wird unterstützt, und der Verbindungs-Manager automatisch versucht, den APN herstellen, wenn dieses verfügbar ist. Diese Einstellung wird für allgemeine Zwecke Internet APNs empfohlen.

Es muss mindestens eine AlwaysOn-Internet-Verbindung für den Mobilfunkbetreiber bereitgestellt.

<a href="" id="authtype"></a>**AuthType**  
Optional Typ: Zeichenfolge. Gibt die Authentifizierungsmethode für die Verbindung verwendet.

Der Wert "CHAP" gibt an, das Anwendungsprotokoll der Herausforderung Handshake ab. Der Wert "PAP" gibt das Kennwort-Authentifizierungsprotokoll an. Der Wert "None" gibt an, dass die Parameter UserName und Password ignoriert werden. Der Standardwert ist "None".

<a href="" id="connectiontype"></a>**ConnectionType**  
Optional Typ: Zeichenfolge. Gibt den Typ der Verbindung, für den APN verwendet wird. Die folgenden Verbindungstypen sind verfügbar:

<table>
<colgroup>
<col width="20%" />
<col width="80%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>GPRS</p></td>
<td><p>Standard. Für GPRS-Typ-Verbindungen (GPRS + g/M2 RAND + UMTS + LZF) verwendet.</p></td>
</tr>
<tr class="even">
<td><p>CDMA</p></td>
<td><p>Für CDMA-Typ-Verbindungen (1XRTT + EVDO) verwendet.</p></td>
</tr>
<tr class="odd">
<td><p>LZF</p></td>
<td><p>Verwendet für LZF Typ Verbindungen (eHRPD + LZF) Wenn das Gerät HOME registriert wird.</p></td>
</tr>
<tr class="even">
<td><p>Vorversion</p></td>
<td><p>Verbindungen verwendet für GPRS + g/M2 RAND + UMTS.</p></td>
</tr>
<tr class="odd">
<td><p>lte_iwlan</p></td>
<td><p>Verwendet für GPRS-Typ-Verbindungen, die über WiFi übergeben werden kann</p></td>
</tr>
<tr class="even">
<td><p>iwlan</p></td>
<td><p>Verwendet für Verbindungen, die über WiFi implementiert sind nur Verschiebung</p></td>
</tr>
</tbody>
</table>

 

<a href="" id="desc-langid"></a>**DESC.LangID**  
Optional Anzeigen der Benutzeroberfläche Zeichenfolge, mit der die definierten Sprachen-ID gibt

Den Namen eines Parameters im Format Desc.langid wird als sprachspezifische Bezeichner für den angegebenen Eintrag verwendet werden. Beispielsweise einen Parameter, die als definiert `Desc.0409` mit dem Wert `"GPRS Connection"` erzwingen, dass "GPRS-Verbindung" angezeigt werden, in der Benutzeroberfläche, um diese Verbindung darstellen, wenn das Gerät auf die englische Sprache (Language-ID 0409) festgelegt ist. Beschreibungen für mehrere Sprachen können mithilfe dieser Mechanismus bereitgestellt werden, und das System wird automatisch zwischen ihnen wechseln, wenn der Benutzer auf dem Gerät spracheinstellungen ändert. Wenn keine **Desc** -Parameter für eine bestimmte Sprache bereitgestellt wird, wird das System auf den Namen verwendet, um den Eintrag erstellen festgelegt.

<a href="" id="enabled"></a>**Aktiviert**  
Gibt an, ob die Verbindung aktiviert ist.

Der Wert "0" gibt an, dass die Verbindung deaktiviert ist. Der Wert "1" gibt an, dass die Verbindung aktiviert ist.

<a href="" id="ipheadercompression"></a>**IpHeaderCompression**  
Optional Gibt an, ob die IP-Header-Komprimierung aktiviert ist.

Der Wert "0" gibt an, dass IP-Header-Komprimierung für die Verbindung deaktiviert ist. Der Wert "1" gibt an, dass IP-Header-Komprimierung für die Verbindung aktiviert ist.

<a href="" id="password"></a>**Kennwort**  
Erforderlich, wenn AuthType auf einen anderen Wert als "None" festgelegt ist. Gibt das Kennwort für die Verbindung auf den APN verwendet.

<a href="" id="swcompression"></a>**SwCompression**  
Optional Gibt an, ob Software Komprimierung aktiviert ist.

Der Wert "0" gibt an, dass Software Komprimierung für die Verbindung deaktiviert ist. Der Wert "1" gibt an, dass Software Komprimierung für die Verbindung aktiviert ist.

<a href="" id="username"></a>**Benutzername**  
Erforderlich, wenn AuthType auf einen anderen Wert als "None" festgelegt ist. Gibt den Benutzernamen für die Verbindung auf den APN verwendet.

<a href="" id="userequiresmappingspolicy"></a>**UseRequiresMappingsPolicy**  
Optional Gibt an, ob die Verbindung mit eine entsprechenden Zuordnungen Richtlinie erfordert.

Der Wert "0" gibt an, dass die Verbindung für alle allgemeinen Internetkommunikation verwendet werden kann. Der Wert "1" gibt an, dass nur die Verbindung verwendet wird, wenn eine Zuordnung Richtlinie vorhanden ist.

Wenn die multimedia messaging Service (MMS) APN nicht Datenverkehr mit Ausnahme von MMS haben, können Sie beispielsweise eine Zuordnung zu konfigurieren, die an diese Verbindung MMS Datenverkehr sendet. Klicken Sie dann, legen Sie den Wert des UseRequiresMappingsPolicy gleich "1" festgelegt, und Verbindungs-Manager wird nur die Verbindung für MMS-Datenverkehr verwendet. Ohne diese versucht Verbindungs-Manager die Verbindung für allgemeine Zwecke Internet-Datenverkehr verwendet.

<a href="" id="version"></a>**Version**  
Typ: int Gibt die XML-Versionsnummer an und wird verwendet, um sicherzustellen, dass der XML-CODE von Verbindungs-Manager Konfigurationsdienstanbieter unterstützt wird.

Dieser Wert muss "1", falls enthalten.

<a href="" id="gprsinfoaccesspointname"></a>**GPRSInfoAccessPointName**  
Gibt den logischen Namen GPRS-Gateway aus. Weitere Informationen über zulässige Werte finden Sie unter g/M2 Spezifikation 07.07 "10.1.1 definieren PDP-Kontext + CGDCONT".

<a href="" id="roaming"></a>**Roaming**  
Optional Typ: int Dieser Parameter gibt die roaming Bedingungen, unter denen die Verbindung aktiviert werden soll. Die folgenden Bedingungen sind verfügbar:

-   0 – nur Home-Netzwerk.
-   (Standardeinstellung) 1 - alle roaming Conditions (Home und roaming).
-   2 - Startseite und nationalen roaming.
-   3 - nationalen nur roaming.
-   4 - Ausland nur roaming.
-   5 – roaming nur.

<a href="" id="oemconnectionid"></a>**OEMConnectionID**  
Optional Typ: GUID. Gibt eine GUID zur Identifizierung einer bestimmten Verbindungs in das Modem verwenden. Wenn kein Wert angegeben ist, ist der Standardwert 00000000-0000-0000-0000-000000000000. Dieser Parameter wird nur auf LZF Geräten verwendet werden.

<a href="" id="apnid"></a>**ApnId**  
Optional Typ: int Gibt den Zweck der APN. Wenn kein Wert angegeben ist, ist der Standardwert "0" (kein Rahmen). Dieser Parameter wird nur auf LZF Geräten verwendet werden.

<a href="" id="iptype"></a>**IPType**  
Optional Typ: Zeichenfolge. Gibt das Netzwerkprotokoll der Verbindung. Mögliche Werte sind "IPv4", "IPv6", "IPv4v6" und "IPv4v6xlat". Wenn kein Wert angegeben ist, wird der Standardwert "IPv4".

> **Warnung**  
Verwenden Sie IPv6- oder IPv4v6xlat nicht auf einem Gerät oder Netzwerk, das IPv6 nicht unterstützt. Datenfunktionen nicht verwendet werden. Darüber hinaus werden das Gerät nicht zum roaming-Netzwerk herstellen, die keine IPv6 unterstützt, es sei denn, Sie servergespeicherte Verbindungen mit einem IPType IPv4v6 konfigurieren.

 

<a href="" id="exemptfromdisablepolicy"></a>**ExemptFromDisablePolicy**  
Wieder in Windows 10, Version 1511 hinzugefügt. Optional Typ: int Dies sollte nur für spezielle Zwecke Verbindungen angegeben werden, deren Applications ihren Status zum Deaktivieren (beispielsweise MMS) direkt verwalten. Der Wert "0" gibt an, dass der Disable-Richtlinie verwendet, die für allgemeine Zwecke Verbindungen (nicht ausgenommen) die Verbindung fällt. Der Wert "1" gibt an, dass die Verbindung ausgenommen ist. Wenn kein Wert angegeben ist, ist der Standardwert "0" (aber nicht ausgenommen).

Um MMS zuzulassen, wenn Daten auf DEAKTIVIERT festgelegt ist, legen Sie ExemptFromDisablePolicy und UseRequiresMappingsPolicy auf "1". Dies gibt an, dass die Verbindung eine dedizierte MMS-Verbindung ist und es nicht deaktiviert werden soll, wenn alle anderen Verbindungen deaktiviert sind. Daher können MMS gesendet und empfangen, wenn Daten auf DEAKTIVIERT festgelegt ist. Beachten Sie, dass das Senden von MMS beim roaming noch nicht zulässig ist.

> **Wichtige**  
Legen Sie ExemptFromDisablePolicy nicht auf "1" auf "1" ExemptFromRoaming oder UseRequiresMappingsPolicy auf "1" für allgemeine Zwecke Verbindungen.

Zur Vermeidung von UX Inkonsistenz mit bestimmten Wertkombinationen von ExemptFromDisablePolicy und AllowMmsIfDataIsOff, wenn Sie nicht ExemptFromDisablePolicy auf 1 festlegen (der Standardwert ist 0), sollten Sie:

-   Blenden Sie die Umschaltfläche für AllowMmsIfDataIsOff aus, indem AllowMmsIfDataIsOffEnabled auf 0 (Standardwert ist 1)
-   AllowMMSIfDataIsOff auf 1 festgelegt (der Standardwert ist 0)

 

<a href="" id="exemptfromroaming"></a>**ExemptFromRoaming**  
Wieder in Windows 10, Version 1511 hinzugefügt. Optional Typ: int Dies sollte nur für spezielle Zwecke Verbindungen angegeben werden, deren Applications direkt roaming zu verwalten. Es sollte niemals mit Verbindungen für allgemeine Zwecke verwendet werden. Der Wert "0" gibt an, dass die Verbindung gelten die roaming Richtlinie (nicht ausgenommen) ist. Der Wert "1" gibt an, dass die Verbindung ausgenommen ist (nicht durch die roaming Richtlinie betroffenen). Wenn kein Wert angegeben ist, ist der Standardwert "0" (aber nicht ausgenommen).

<a href="" id="tetheringnai"></a>**TetheringNAI**  
Optional Typ: int CDMA. Gibt an, ob die Verbindung einer tethering Verbindung ist. Der Wert "0" gibt an, dass die Verbindung keiner tethering Verbindung ist. Der Wert "1" gibt an, dass die Verbindung eine tethering Verbindung ist. Wenn kein Wert angegeben ist, ist der Standardwert "0".

<a href="" id="idledisconnecttimeout"></a>**IdleDisconnectTimeout**  
Optional Typ: int Gibt an, wie lange eine Verbindung bei Bedarf nicht verwendete sein kann, bevor der Verbindungs-Manager die Verbindung beendet. Dieser Wert wird in Sekunden angegeben. Gültige Wertebereich beträgt 5 bis 60 Sekunden. Wenn nicht angegeben, ist die Standardeinstellung 30 Sekunden.

> **Wichtige**  
Sie müssen den IdleDisconnectTimeout Wert angeben, beim Aktualisieren einer Verbindungs bei Bedarf, um sicherzustellen, dass der gewünschte Wert weiterhin konfiguriert ist. Wenn sie nicht angegeben wird, kann der Standardwert von 30 Sekunden verwendet werden.

 

> **Hinweis**  
Wenn Rufnummern-nach-unten/aktivierungsanforderungen zu häufig auftreten, sollte dieser Wert größer als 5 Sekunden festgelegt werden an.

 

<a href="" id="simiccid"></a>**SimIccId**  
Für einzelne SIM-Telefone ist dieser Parameter optional. Es wird jedoch dringend empfohlen, diesen Wert beim Erstellen von zukünftige Updates einbezogen werden sollen. Für duale SIM-Telefone ist dieser Parameter erforderlich. Typ: Zeichenfolge. Gibt die SIM ICCID, die die Verbindung services an.

<a href="" id="purposegroups"></a>**PurposeGroups**  
Optional Typ: Zeichenfolge. Gibt die Zwecke der Verbindung von einer durch Trennzeichen getrennte Liste von GUIDs Zweck Werte darstellt. Die folgenden Zweck Werte sind verfügbar:

-   Internet - 3E5545D2-1137-4DC8-A198-33F1C657515F
-   MMS - 53E2C5D3-D13C-4068-AA38-9C48FF2E55A8
-   SOFORTNACHRICHTEN - 474D66ED-0E4B-476B-A455-19BB1239ED13
-   SUPL - 6D42669F-52A9-408E-9493-1071DCC437BD

## <a name="additional-information"></a>Weitere Informationen


Um eine Verbindung zu löschen, müssen Sie zunächst alle zugehörigen Proxys löschen und löschen Sie die Verbindung. Im folgenden Beispiel wird gezeigt, wie den Proxy, und klicken Sie dann die Verbindung zu löschen.

``` syntax
<wap-provisioningdoc>
   <characteristic type="CM_ProxyEntries">
      <nocharacteristic type="GPRS_Proxy"/>
   </characteristic>  
   <characteristic type="CM_CellularEntries">
      <nocharacteristic type="GPRS1"/>
   </characteristic>
</wap-provisioningdoc>
```

## <a name="oma-client-provisioning-examples"></a>Beispiele für die Bereitstellung OMA-client


Eine GPRS-Verbindung konfigurieren:

``` syntax
<wap-provisioningdoc>
   <characteristic type="CM_CellularEntries">
      <characteristic type="GPRSConn">
         <parm name="ConnectionType" value="gprs" />
         <characteristic type="DevSpecificCellular">
            <parm name="GPRSInfoAccessPointName" value="apn.adatum.com" />
         </characteristic>
         <parm name="AlwaysOn" value="0" />
         <parm name="Enabled" value="1" />
      </characteristic>
   </characteristic>
</wap-provisioningdoc>
```

Konfigurieren einer LZF-Verbindung:

``` syntax
<wap-provisioningdoc>
   <characteristic type="CM_CellularEntries">
      <characteristic type="LteConn">
         <parm name="ConnectionType" value="lte" />
         <characteristic type="DevSpecificCellular">
            <parm name="GPRSInfoAccessPointName" value="INTERNET_LTE" />
         </characteristic>
         <parm name="ApnId" value="0" />
         <parm name="IPType" value="IPv4v6" />
         <parm name="Enabled" value="1" />
         <parm name="OemConnectionId" value="01234567-89AB-CDEF-0123-456789ABCDEF" />
      </characteristic> 
   </characteristic>
</wap-provisioningdoc>
```

Konfigurieren einer CDMA-Verbindung:

``` syntax
<wap-provisioningdoc>
   <characteristic type="CM_CellularEntries">
      <characteristic type="CDMAConn">
         <parm name="Version" value="1"/>
         <parm name="AuthType" value="chap" />
         <parm name="ConnectionType" value="cdma"/>
         <parm name="Enabled" value="1"/>
         <parm name="AlwaysOn" value="0"/>
         <parm name="UseRequiresMappingsPolicy" value="0"/>
         <parm name="UserName" value="user@adatum.com"/>
         <parm name="Password" value="fakeuserpassword"/>
      </characteristic>
   </characteristic>
</wap-provisioningdoc>
```

## <a name="microsoft-custom-elements"></a>Microsoft benutzerdefinierte Elemente


In der folgenden Tabelle werden die benutzerdefinierten Microsoft-Elemente, die dieser Konfigurationsdienstanbieter für OMA-Clientbereitstellung unterstützt veranschaulicht.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Element</th>
<th>Verfügbar</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>nocharacteristic</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="even">
<td><p>Merkmal-Abfrage</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="odd">
<td><p>Parameter-Abfrage</p></td>
<td><p>Ja</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>Verwandte Themen


[Konfiguration Dienstverweis-Anbieter](configuration-service-provider-reference.md)

 

 





