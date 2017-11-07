---
title: HotSpot CSP
description: HotSpot CSP
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: ec49dec1-fa79-420a-a9a7-e86668b3eebf
ms.openlocfilehash: 7ab0ca7f60e27f4c131906f5562dea9b79e7c847
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="hotspot-csp"></a>HotSpot CSP


Konfiguration Dienstanbieters HotSpot wird verwendet, um konfigurieren und Aktivieren der Internet Freigabe auf dem Gerät, in dem das Gerät zum Freigeben seiner Mobilfunk Verbindungs über Wi-Fi mit bis zu acht Client-Geräte oder Computer konfiguriert werden kann.

> **Hinweis**  HotSpot CSP ist nur in Windows 10 Mobile unterstützt.

 

> **Hinweis**   Dieses Dienstanbieters Konfiguration erfordert die ID\_CAP\_CSP\_FOUNDATION-Funktion aus einer Anwendung der Netzwerk-Konfiguration zugegriffen werden.

 

Das folgende Diagramm veranschaulicht das HotSpot Configuration Service Provider Management-Objekts im Strukturformat von OMA-Clientbereitstellung verwendet. Das Protokoll OMA DM wird von dieser Konfigurationsdienstanbieter nicht unterstützt.

![Hotspot Csp (cp)](images/provisioning-csp-hotspot-cp.png)

<a href="" id="enabled"></a>**Aktiviert**  
Erforderlich. Gibt an, ob das Aktivieren der Internetfreigabe auf dem Gerät. Der Standardwert ist false.

Wenn dies anfangs auf False festgelegt ist, das Feature deaktiviert ist, und im Internet freigeben Bildschirm aus Einstellungen entfernt, sodass der Benutzer nicht darauf zugreifen kann. Konfigurationsänderungen oder Teilen Änderungen am Status der Verbindung ist nicht möglich.

Wenn dies auf true festgelegt ist, im Internet Einstellungen für die Anwendungsfreigabe Bildschirm hinzugefügt wird ist jedoch Freigabe standardmäßig deaktiviert bis auf der Benutzer wird aktiviert.

Diese Einstellung kann über das Mobilfunknetz bereitgestellt werden, aber es kann ein Neustart erforderlich, wenn Einstellungen geöffnet war, als dies bei der ersten aktiviert wurde.

<a href="" id="dedicatedconnections"></a>**DedicatedConnections**  
Optional Gibt an, die durch Semikolons getrennte Liste der Verbindungs-Manager mobilverbindungen, die gemeinsame Nutzung der Internetverbindung als öffentlichen Verbindungen verwenden.

Standardmäßig werden alle verfügbaren Verbindungen als öffentliche Verbindung verwendet werden. Dieser Knoten kann jedoch ein Mobilfunkbetreiber an einen oder mehrere Verbindungsnamen, als öffentliche Verbindungen zu verwenden.

Angegebene Verbindungen werden durch eine Richtlinie, an das Internet Service Freigabe zugeordnet werden. Alle Versuche zum Aufzählen von Verbindungs-Manager-Verbindungen für das Internet Service Freigabe gibt nur die zugeordneten Verbindungen zurück.

> **Hinweis**   Die Zuordnung Richtlinie wird auch als auch den Wert des **TetheringNAIConnection** angegebene Verbindung enthalten.

 

Wenn der angegebenen Verbindung nicht vorhanden sind, kann Internet sharing nicht gestartet, da es keine verfügbaren freigeben mobilverbindungen hat

Wenn der Anwendungsfreigabe Internetdienst bereits in einem Freigabestatus befindet, wird durch Festlegen dieser Knoten nicht erst wirksam Freigabe beendet und neu gestartet wird.

<a href="" id="tetheringnaiconnection"></a>**TetheringNAIConnection**  
Optional Gibt die Mobilfunk CDMA TetheringNAI Verbindungs-Manager-Verbindung, die gemeinsame Nutzung der Internetverbindung als eine öffentliche Verbindung verwenden.

Ein Mobilfunkbetreiber CDMA erfordert mithilfe einer Tethering NAI während Internet freigeben, verwenden sie die [CM\_CellularEntries Konfigurationsdienstanbieter](cm-cellularentries-csp.md) So stellen Sie eine Verbindung TetheringNAI bereit, und geben Sie dann die bereitgestellte Verbindung in diesem Knoten.

Angegebene Verbindungen werden durch eine Richtlinie, mit dem Internet Freigabe Service zugeordnet werden. Alle Versuche zum Aufzählen von Verbindungs-Manager-Verbindungen für das Internet Service Freigabe gibt nur die zugeordneten Verbindungen zurück.

> **Hinweis**   Die Zuordnung Richtlinie wird auch die Verbindungen, die in der **DedicatedConnections** auch angegebenen enthalten.

 

Wenn der angegebenen Verbindung nicht vorhanden sind, kann Internet sharing nicht gestartet, da es keine verfügbaren freigeben mobilverbindungen hat

Wenn der Freigabe Internetdienst bereits in einer Freigabestatus befindet, wird durch Festlegen dieser Knoten nicht werden erst nach Freigabe beendet und neu gestartet wird.

<a href="" id="maxusers"></a>**MaxUsers**  
Optional Gibt die maximale Anzahl gleichzeitiger Benutzer, die zu einem Gerät, klicken Sie in einer Freigabestatus verbunden werden können. Der Wert muss zwischen 1 und 8 inklusive. Der Standardwert ist 5.

Wenn der Freigabe Internetdienst bereits in einem Freigabestatus befindet, wird durch Festlegen dieser Knoten nicht werden erst nach Freigabe beendet und neu gestartet wird.

<a href="" id="maxbluetoothusers"></a>**MaxBluetoothUsers**  
Optional Gibt die maximale Anzahl gleichzeitiger Bluetooth-Benutzer, die während der Freigabe über Bluetooth zu einem Gerät verbunden werden können. Der Wert muss zwischen 1 und einschließlich 7. Der Standardwert ist 7.

<a href="" id="mohelpnumber"></a>**MOHelpNumber**  
Optional Ein Operator – angegeben Mobiltelefonnummer, die dem Benutzer angezeigt wird, wenn das Internet Service Freigabe kann nicht gestartet werden. Die Benutzeroberfläche zeigt eine Meldung, die dem Benutzer darüber informiert, dass sie Hilfestellung bei die angegebene Anzahl anrufen können.

<a href="" id="moinfolink"></a>**MOInfoLink**  
Optional Eine mobile Operator – angegebenen HTTP-Verknüpfung, die angezeigt wird, auf den Benutzer beim Freigeben von Internet deaktiviert ist oder das Gerät ist nicht berechtigt. Die Benutzeroberfläche zeigt eine Meldung, die dem Benutzer darüber informiert, dass Besuch die angegebene Verknüpfung für Weitere Informationen zum Aktivieren des Features.

<a href="" id="moapplink"></a>**MOAppLink**  
Optional Ein Windows-Gerät Anwendungslink, der an die vorinstallierten Anwendung zur Verfügung gestellt, durch den Mobilfunkbetreiber, der einen Benutzer das Internet Service freigeben, wenn Internetfreigabe nicht bereitgestellt wird oder der Anspruch des Mobilfunkbetreibers abonnieren helfen fällt aus. Ist das Standardformat für den Link `app://MOapp`.

<a href="" id="mohelpmessage"></a>**MOHelpMessage**  
Optional Verweis auf eine lokalisierte Zeichenfolge, die zur Verfügung gestellt, durch den Mobilfunkbetreiber, der angezeigt wird, wenn Internetfreigabe Anspruch Ausfall nicht aktiviert ist. Der Knoten nimmt eine sprachneutrale Registrierung Wert-Zeichenfolge, die im folgenden Format:

`@<path_to_res_dll>,-<str_id>`

Wobei `<path_to_res_dll>` ist der Pfad zur Ressourcen-Dll, die die Zeichenfolge enthält und `<str_id>` ist der Zeichenfolgenbezeichner. Weitere Informationen zu sprachneutrale Zeichenfolge Ressource Registrierungswerte finden Sie unter [Verwenden von Registrierung Zeichenfolge Umleitung](http://msdn.microsoft.com/library/windows/desktop/dd374120.aspx) auf MSDN.

> **Hinweis**  MOAppLink ist erforderlich, um die Einstellung MOHelpMessage verwenden.

 

<a href="" id="entitlementrequired"></a>**EntitlementRequired**  
Optional Gibt an, ob das Gerät erfordert eine Überprüfung Anspruch zu ermitteln, ob gemeinsame Nutzung der Internetverbindung muss aktiviert sein. Dieser Knoten ist auf einen Boolean-Wert festgelegt. Der Standardwert ist **True**.

Standardmäßig wird das Internet Service Freigabe Anspruch überprüfen, jedes Mal, wenn versucht wird, Internetfreigabe ermöglichen. Gemeinsame Nutzung der Internetverbindung sollte auf **False** für Geräte Netzbetreiber nicht gesperrte festgelegt werden.

<a href="" id="entitlementdll"></a>**EntitlementDll**  
Erforderlich, wenn `EntitlementRequired` festgelegt ist auf "true". Der Pfad zu der Anspruch verwendeten DLL Anspruch vornehmen überprüft, die Stellen Sie sicher, dass das Gerät zur Verwendung von Internet-Dienst auf einem Mobilfunkbetreiber Netzwerk Freigabe berechtigt ist. Der Wert ist eine Zeichenfolge, die einen gültigen Dateipfad System mit der Berechtigung DLL darstellt. In der Standardeinstellung fällt im Internet Service Freigabe Anspruch Überprüfungen aus, wenn diese Einstellung nicht vorhanden oder leer ist. Weitere Informationen finden Sie weiter unten in diesem Thema [Erstellen Sie eine DLL Ansprüche](#creating-entitlement-dll) .

<a href="" id="entitlementinterval"></a>**EntitlementInterval**  
Optional Das Zeitintervall in Sekunden zwischen Anspruch überprüft. Der Standardwert beträgt 86.400 Sekunden (24 Stunden).

Wenn eine periodische Anspruch Überprüfung fehlschlägt, wird die gemeinsame Nutzung der Internetverbindung automatisch deaktiviert.

<a href="" id="peerlesstimeout"></a>**PeerlessTimeout**  
Optional Die Timeout-Zeitraum in Minuten ein, sollten nach dem Internet Freigabe automatisch dann deaktivieren, wenn alle aktiven Clients nicht mehr vorhanden sind. Dieser Knoten kann auf einen beliebigen Wert zwischen 1 und 120 inklusive festgelegt werden. Der Wert 0 wird nicht unterstützt. Der Standardwert ist 5 Minuten.

Ein Neustart kann erforderlich sein, bevor Änderungen an diesen Knoten wirksam werden.

<a href="" id="publicconnectiontimeout"></a>**PublicConnectionTimeout**  
Optional Der Timeoutwert in Minuten ein, nach deren Freigabe von Internet automatisch If eine Verbindung mit Mobile deaktiviert ist nicht verfügbar ist. Dieser Knoten kann auf einen beliebigen Wert zwischen 1 und 60 (einschließlich) festgelegt werden. Der Standardwert ist 20 Minuten. Ein Timeout ist erforderlich, damit der Wert 0 nicht unterstützt wird.

Änderungen an dieser Knoten ist ein Neustart erforderlich.

<a href="" id="minwifikeylength"></a>**MinWifiKeyLength**  
> **Wichtige**   Dieser Parameter wird nicht mehr für Windows Phone 8.1 unterstützt. Die erzwungene minimale zulässige Länge des Schlüssels Wi-Fi ist 8.

 

<a href="" id="minwifissidlength"></a>**MinWifiSSIDLength**  
> **Wichtige**   Dieser Parameter wird nicht mehr für Windows Phone 8.1 unterstützt. Die erzwungene minimale zulässige Länge des SSID Wi-Fi ist 1.

 

## <a name="additional-requirements-for-cdma-networks"></a>Zusätzliche Anforderungen für CDMA-Netzwerke


Für CDMA-Netzwerken, eine separate Network Access Identität (NAI) für die Freigabe von Internet verwenden, eine neue Parameter, TetheringNAI, hinzugefügt wurde der [CM\_CellularEntries Konfigurationsdienstanbieter](cm-cellularentries-csp.md) Konfiguration-Dienstanbieter. Das folgende Beispiel veranschaulicht, wie Sie die Verbindung angeben.

``` syntax
<wap-provisioningdoc>
    <characteristic type="CM_CellularEntries">
        <characteristic type="TetheringNAIConn">
            <parm name="Version" value="1"/>
            <parm name="UserName" value=""/>
            <parm name="Password" value=""/>
            <parm name="TetheringNAI" value="1"/>
        </characteristic>
    </characteristic>
    <characteristic type="HotSpot">
        <parm name="Enabled" value="true" datatype="boolean"/>
        <parm name="EntitlementRequired" value="false" datatype="boolean"/>
        <parm name="TetheringNAIConnection" value="TetheringNAIConn" datatype="string"/>
    </characteristic>
</wap-provisioningdoc>
```

> **Hinweis**  CDMA-Geräte können nur jeweils eine Verbindung als aktive Daten. Dies bedeutet, dass jede Anwendung oder Dienst (wie e-Mail oder MMS), der an eine andere Verbindung gebunden ist möglicherweise nicht funktionieren, während der Freigabe von Internet aktiviert ist.

 

## <a name="a-href-idcreating-entitlement-dllacreating-an-entitlement-dll"></a><a href="" id="creating-entitlement-dll"></a>Erstellen einen Anspruch DLL


Für Mobilfunkbetreiber Netzwerke, die ein Kontrollkästchen Anspruch erfordern, muss der OEM eine DLL im Geräteabbild angeben, die eine Funktion mit der folgenden Signatur implementiert:

`ICS_ENTITLEMENT_RESULT IsEntitled(void);`

Die `EntitlementDll` Parameter des Dienstanbieters HotSpot Konfiguration muss auf eine Zeichenfolge, die den Pfad zur DLL ist festgelegt werden.

Die DLL muss Code, der auf eine bestimmte Weise signiert werden, finden Sie unter [Anmelde-Binärdateien und Paketen](https://msdn.microsoft.com/en-us/library/windows/hardware/dn789217(v=vs.85).aspx).

Während ein Anspruch Aktivieren der Internet Sharing Dienst lädt die angegebene DLL-DATEI, und rufen Sie dann die `IsEntitled` Funktion. Die Funktion muss eine Verbindung herstellen, auf dem Server zur jede erforderliche Validierung ausführen und dann eine der folgenden zurückgeben **ICS\_ANSPRUCH\_ERGEBNIS** Enumerationswerte.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Wert</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>ENTITLEMENT_SUCCESS</strong></p></td>
<td><p>Das Gerät mit dem Server herstellen kann.</p></td>
</tr>
<tr class="even">
<td><p><strong>ENTITLEMENT_FAILED</strong></p></td>
<td><p>Das Gerät darf nicht mit dem Server herstellen</p></td>
</tr>
<tr class="odd">
<td><p><strong>ENTITLEMENT_UNAVAILABLE</strong></p></td>
<td><p>Das Kontrollkästchen Anspruch ist fehlgeschlagen, da das Gerät konnte nicht wenden Sie sich an den Server oder eine Verbindung, um zu überprüfen, Anspruch zu erwerben.</p></td>
</tr>
</tbody>
</table>

 

Die Definition für den **ICS\_ANSPRUCH\_ERGEBNIS** befindet sich in der Headerdatei `IcsEntitlementh`, das im Lieferumfang von Windows Anpassung Kit.

## <a name="related-topics"></a>Verwandte Themen


[Konfiguration Dienstverweis-Anbieter](configuration-service-provider-reference.md)

 

 






