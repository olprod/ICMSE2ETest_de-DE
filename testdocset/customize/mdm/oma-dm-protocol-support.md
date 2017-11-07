---
title: "Unterstützung des Protokolls für OMA DM"
description: "Unterstützung des Protokolls für OMA DM"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: e882aaae-447e-4bd4-9275-463824da4fa0
ms.openlocfilehash: 993b24c5659c8985b2a1d374cd5bee671f7747cc
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="oma-dm-protocol-support"></a>Unterstützung des Protokolls für OMA DM

Der Client OMA DM kommuniziert mit dem Server über HTTPS und DM Sync (OMA DM v1. 2) als Nachrichtennutzlast verwendet. In diesem Thema werden die OMA DM-Funktionalität, die im Allgemeinen der DM-Client unterstützt. Der vollständige Erläuterung der OMA DM-Protokoll v1. 2 finden Sie unter der [OMA-Website](http://go.microsoft.com/fwlink/p/?LinkId=267526).


## <a name="in-this-topic"></a>In diesem Thema

-   [OMA DM Standards (engl.)](#oma-dm-standards)

-   [OMA DM Protokoll gemeinsame Elemente](#protocol-common-elements)

-   [Gerät-Management-Sitzung](#device-management-session)

-   [Benutzer geplant, im Vergleich zu gezielten Gerätekonfiguration](#user-targeted-vs-device-targeted-configuration)

-   [SyncML Antwortcodes](#syncml-response-codes)


## <a name="oma-dm-standards"></a>OMA DM Standards (engl.)

Die folgende Tabelle zeigt die OMA DM-Standards, die Windows verwendet.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Bereich "Allgemein"</th>
<th>Der OMA DM-Standard unterstützt wird</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="vertical-align:top"><p>Datenübertragung und Sitzung</p></td>
<td style="vertical-align:top"><ul>
<li><p>Client-initiierte HTTPS DM Remotesitzung über SSL.</p></li>
<li><p>Remotesitzung HTTPS DM über SSL.</p></li>
<li><p>Remote DM Server Initiation Benachrichtigung mit WAP Push über Short Message Service (SMS). Von Enterprise-Management verwendet nicht.</p></li>
<li><p>Remote Bootstrap mithilfe von WAP Push über SMS. Von Enterprise Management verwendet nicht.</p></li>
</ul></td>
</tr>
<tr class="even">
<td style="vertical-align:top"><p>Bootstrap XML</p></td>
<td style="vertical-align:top"><ul>
<li><p>Bereitstellung von XML OMA-Client.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td style="vertical-align:top"><p>Befehle des DM-Protokolls</p></td>
<td style="vertical-align:top"><p>Die folgende Liste enthält die Befehle, die vom Gerät verwendet werden. Weitere Informationen zu den OMA DM Command-Elemente, finden Sie unter &quot;SyncML Darstellung Protokoll Gerät Management Usage (OMA-SyncML-DMRepPro-V1_1_2-20030613-A)&quot; der [OMA-Website](http://go.microsoft.com/fwlink/p/?LinkId=267526).</p>
<ul>
<li><p>Hinzufügen (implizite hinzufügen unterstützt)</p></li>
<li><p>Warnung (DM Alarm): generische Warnung (1226) wird von Enterprise-Management-Client verwendet, wenn der Benutzer eine MDM Unenrollment Aktion vom Gerät auslöst, oder wenn ein CSP einige asynchronen Aktionen abgeschlossen ist. Gerät-Benachrichtigung (1224) wird verwendet, um dem Server ein Geräteereignis ausgelöst benachrichtigen.</p></li>
<li><p>Unteilbare: Beachten Sie, dass die Ausführung eines Befehls Hinzufügen von ersetzen auf demselben Knoten in einem unteilbare Element gefolgt wird nicht unterstützt. Verschachtelte Atomic und Get-Befehle sind nicht zulässig und Fehlercode 500 generiert.</p></li>
<li><p>Delete: Entfernt einen Knoten in der Struktur des DM sowie die gesamte Teilstruktur unter diesem Knoten, falls vorhanden</p></li>
<li><p>EXEC: Ruft eine ausführbare Datei auf dem Clientgerät</p></li>
<li><p>Get: Ruft Daten aus dem Client-Gerät; interior Knoten werden die untergeordneten Knotennamen in das Datenelement im URI-codierten Format zurückgegeben.</p></li>
<li><p>Ersetzen: Überschreibt Daten auf dem Clientgerät</p></li>
<li><p>Ergebnis: Gibt die Ergebnisse der Get-Befehl an den Server DM</p></li>
<li><p>Sequenz: Gibt die Reihenfolge, in der eine Gruppe von Befehlen verarbeitet werden müssen</p></li>
<li><p>Status: Gibt an, den Abschlussstatus eines Vorgangs (Erfolg oder Fehler)</p></li>
</ul>
<p>Wenn ein XML-Element, das nicht auf einen gültigen Befehl OMA DM ist unter einem der folgenden Elemente, wird der Statuscode 400 für dieses Element zurückgegeben:</p>
<ul>
<li><p>SyncBody</p></li>
<li><p>Unteilbare</p></li>
<li><p>Sequence</p></li>
</ul>
<p>Wenn keine CmdID in den Befehl DM bereitgestellt wird, gibt der Client in der Status-Element und den Statuscode 400 leer zurück.</p>
<p>Wenn unteilbare Elemente geschachtelt sind, werden die folgenden Statuscodes zurückgegeben:</p>
<ul>
<li><p>Geschachtelte unteilbare Befehls gibt 500 zurück.</p></li>
<li><p>Das übergeordnete unteilbare Befehl gibt 507 zurück.</p></li>
</ul>
<p>Weitere Informationen zum Befehl unteilbare finden Sie unter OMA DM Protokoll gemeinsame Elemente.</p>
<p>Durchführen eines Befehls hinzufügen, ersetzen auf demselben Knoten in einem unteilbare Element gefolgt wird nicht unterstützt.</p>
<p>LocURI kann nicht gestartet werden mit &quot; / &quot;.</p>
<p>Metadaten-XML-Tag in SyncHdr wird vom Gerät ignoriert.</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top"><p>OMA DM standard-Objekte</p></td>
<td style="vertical-align:top"><ul>
<li><p>DevInfo</p></li>
<li><p>DevDetail</p></li>
<li><p>OMA DM DMS Account-Objekten (OMA DM Version 1.2)</p></li>
</ul></td>
</tr>
<tr class="odd">
<td style="vertical-align:top"><p>Sicherheit</p></td>
<td style="vertical-align:top"><ul>
<li><p>Authentifizieren DM Server Initiation Benachrichtigung SMS Nachricht (nicht von Enterprise-Management verwendet)</p></li>
<li><p>Application Layer Basic und MD5 Clientauthentifizierung</p></li>
<li><p>Authentifizieren Sie Server mit MD5 Anmeldeinformationen auf Anwendungsebene</p></li>
<li><p>Die Datenintegrität und die Authentifizierung mit HMAC auf Anwendungsebene</p></li>
<li><p>Ebene SSL-Zertifikat basiert, Client/Server-Authentifizierung, Verschlüsselung und Integrität prüfen</p></li>
</ul></td>
</tr>
<tr class="even">
<td style="vertical-align:top"><p>Nodes</p></td>
<td style="vertical-align:top"><p>In der Struktur des OMA DM wenden die folgenden Regeln für den Knotennamen:</p>
<ul>
<li><p>&quot;.&quot; der Name des Knotens kann angehören.</p></li>
<li><p>Der Name des Knotens darf nicht leer sein.</p></li>
<li><p>Knoten darf nicht nur das (*) Sternchenzeichen sein.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td style="vertical-align:top"><p>Bereitstellen von Dateien</p></td>
<td style="vertical-align:top"><p>Bereitstellung von XML müssen wohlgeformt sein, und befolgen Sie die Definition in [SyncML Darstellung Protocol](http://go.microsoft.com/fwlink/p/?LinkId=526905) -Spezifikation.</p>
<p>Wenn ein XML-Element, das nicht auf einen gültigen Befehl OMA DM ist unter SyncBody befindet, wird der Statuscode 400 für dieses Element zurückgegeben.</p>
<div class="alert">
<strong>Hinweis</strong>  
<p>Um eine Unicode-Zeichenfolge als URI repräsentieren, zuerst codieren Sie die Zeichenfolge als UTF-8. Klicken Sie dann codieren Sie jedes UTF-8-Byte mit URI-Codierung.</p>
</div>
<div>
 
</div></td>
</tr>
<tr class="even">
<td style="vertical-align:top"><p>WBXML-Unterstützung</p></td>
<td style="vertical-align:top"><p>Windows unterstützt das Senden und Empfangen von SyncML im XML-Format und codierten WBXML-Format. Dies ist mit den DEFAULTENCODING Knoten unter der w7 ANWENDUNG Merkmal während der Registrierung konfigurierbar. Weitere Informationen zum WBXML codieren finden Sie im Abschnitt 8 der Spezifikation [SyncML Darstellung Protokoll](http://go.microsoft.com/fwlink/p/?LinkId=526905) .</p></td>
</tr>
<tr class="odd">
<td style="vertical-align:top"><p>Behandeln von large Objects</p></td>
<td style="vertical-align:top"><p>Client-Unterstützung für große Objekte auf dem Server hochgeladen wurde in Windows 10, Version 1511, hinzugefügt.</p></td>
</tr>
</tbody>
</table>


<a href="" id="protocol-common-elements"></a>
##OMA DM Protokoll gemeinsame Elemente

Gemeinsame Elemente werden von anderen Elementtypen OMA DM verwendet. Die folgende Tabelle enthält die allgemeinen OMA DM-Elemente verwendet, um die Geräte zu konfigurieren. Weitere Informationen zu OMA DM gemeinsame Elemente finden Sie unter "SyncML Darstellung Protokoll Gerät Management Usage" (OMA-SyncML-DMRepPro-V1\_1\_2-20030613-A) von der [OMA-Website](http://go.microsoft.com/fwlink/p/?LinkId=526900)zur Verfügung.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Element</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="vertical-align:top"><p>Chal</p></td>
<td style="vertical-align:top"><p>Gibt eine Herausforderung Authentifizierung an. Servers oder des Clients kann eine Herausforderung zur anderen senden, wenn keine oder unzureichende Anmeldeinformationen in der ursprünglichen Anforderungsnachricht angegeben wurden.</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top"><p>Cmd</p></td>
<td style="vertical-align:top"><p>Gibt den Namen eines OMA DM-Befehls in ein Status-Element verwiesen wird.</p></td>
</tr>
<tr class="odd">
<td style="vertical-align:top"><p>CmdID</p></td>
<td style="vertical-align:top"><p>Gibt den eindeutigen Bezeichner für ein OMA DM-Befehl.</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top"><p>CmdRef</p></td>
<td style="vertical-align:top"><p>Gibt die ID des Befehls, für welche Status oder Ergebnisse zurückgegeben werden. Dieses Element enthält den Wert des Elements CmdID der entsprechenden Anforderungsnachricht.</p></td>
</tr>
<tr class="odd">
<td style="vertical-align:top"><p>Cred</p></td>
<td style="vertical-align:top"><p>Gibt die Anmeldeinformationen für die Authentifizierung für den Absender der Nachricht an.</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top"><p>Endgültige</p></td>
<td style="vertical-align:top"><p>Gibt an, dass die aktuelle Nachricht die letzte Nachricht in das Paket wird.</p></td>
</tr>
<tr class="odd">
<td style="vertical-align:top"><p>LocName</p></td>
<td style="vertical-align:top"><p>Gibt den Anzeigenamen in den Quell- und Elementen, für das Senden einer Benutzer-ID für die MD5-Authentifizierung verwendet.</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top"><p>LocURI</p></td>
<td style="vertical-align:top"><p>Gibt die Adresse des Speicherorts Ziel oder die Quelle. Wenn die Adresse ein nicht alphanumerische Zeichen enthält, müssen sie entsprechend der URL-Codierung ordnungsgemäß geschützt.</p></td>
</tr>
<tr class="odd">
<td style="vertical-align:top"><p>MsgID</p></td>
<td style="vertical-align:top"><p>Gibt einen eindeutigen Bezeichner für eine OMA DM Sitzung angezeigt.</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top"><p>MsgRef</p></td>
<td style="vertical-align:top"><p>Gibt die ID der entsprechenden Anforderungsnachricht. Dieses Element enthält den Wert des Elements Anforderung Nachricht MsgID.</p></td>
</tr>
<tr class="odd">
<td style="vertical-align:top"><p>RespURI</p></td>
<td style="vertical-align:top"><p>Gibt den URI, der der Empfänger beim Senden einer Antwort auf diese Nachricht verwendet werden muss.</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top"><p>Sitzungs-ID</p></td>
<td style="vertical-align:top"><p>Gibt den Bezeichner der OMA DM Sitzung der enthaltenden Meldung zugeordnet.</p>
<div class="alert">
<strong>Hinweis</strong>  Wenn der Server gibt nicht dem Gerät informieren, eine neue Version (über SyncApplicationVersion Knoten im DMClient CSP) unterstützt, der Desktopclient gibt die SessionID als ganze Zahl im Dezimalformat und der mobilen Gerät Client 2 Bytes als Zeichenfolge zurückgegeben. Wenn der Server DM Sitzung Sync, Version 2.0, die in Windows 10 verwendet wird unterstützt, gibt der Desktop- und mobilen Gerät Client 2 Bytes zurück.
</div>
<div>
 
</div></td>
</tr>
<tr class="odd">
<td style="vertical-align:top"><p>Source</p></td>
<td style="vertical-align:top"><p>Gibt die Quell-Adresse der Nachricht an.</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top"><p>SourceRef</p></td>
<td style="vertical-align:top"><p>Gibt die Quelle der entsprechenden Anforderungsnachricht. Dieses Element nimmt den Wert des Quellelements Anforderung Nachricht und im Status oder Ergebnisse Element zurückgegeben wird.</p></td>
</tr>
<tr class="odd">
<td style="vertical-align:top"><p>Ziel</p></td>
<td style="vertical-align:top"><p>Gibt die Adresse des Knotens, in der DM-Struktur, die das Ziel des Befehls OMA DM ist.</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top"><p>TargetRef</p></td>
<td style="vertical-align:top"><p>Gibt die Ziel-Adresse in die entsprechenden Request-Nachricht an. Dieses Element nimmt den Wert des Zielelements Anforderung Nachricht und im Status oder Ergebnisse Element zurückgegeben wird.</p></td>
</tr>
<tr class="odd">
<td style="vertical-align:top"><p>VerDTD</p></td>
<td style="vertical-align:top"><p>Gibt den Bezeichner der Haupt-und Nebenversion der OMA DM Darstellung Protokollspezifikation verwendet, um die Nachricht darstellen.</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top"><p>VerProto</p></td>
<td style="vertical-align:top"><p>Gibt den Bezeichner der Haupt-und Nebenversion der mit der Meldung verwendet OMA DM Protocol-Spezifikation.</p></td>
</tr>
</tbody>
</table>


## <a name="device-management-session"></a>Gerät-Management-Sitzung

Eine Gerät Management (DM) Sitzung umfasst eine Reihe von Befehlen zwischen einem DM Server und Client-Gerät ausgetauscht. Der Server sendet die Befehle, die Vorgänge, die auf dem Clientgerät Management Struktur ausgeführt werden müssen. Der Client reagiert durch Senden von Befehlen, die die Ergebnisse und alle angeforderten Statusinformationen enthalten.

Eine kurze DM Sitzung kann wie folgt zusammengefasst werden:

Ein Server sendet einen Befehl Get zu einem Clientgerät zum Abrufen des Inhalts von einem Knoten der Struktur des Management. Das Gerät führt den Vorgang und antwortet mit der ein Ergebnis Befehl, der den angeforderten Inhalt enthält.

Eine Sitzung DM kann in zwei Phasen unterteilt werden:
1.  **Phase der Installation**: als Antwort auf ein Triggerereignis, sendet ein Clientgerät eine auslösenden-Nachricht an einen DM-Server. Der Exchange-Gerät und Server erforderlich, Authentifizierung und Geräteinformationen. Diese Phase wird durch Schritte 1, 2 und 3 in der folgenden Tabelle dargestellt.
2.  **Patchverwaltung Phase**: der DM Server befindet sich im Steuerelement. Befehle zur Verwaltung des an das Gerät gesendet, und das Gerät antwortet. Phase 2 beendet, wenn der Server DM mehr senden von Befehlen und beendet die Sitzung. Diese Phase wird durch die Schritte 3, 4 und 5 in der folgenden Tabelle dargestellt.

Die folgende Tabelle zeigt die Abfolge der Ereignisse während einer typischen DM-Sitzung.

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>Schritt</th>
<th>Aktion</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="vertical-align:top"><p>1</p></td>
<td style="vertical-align:top"><p>DM Client wird aufgerufen, um dem Verwaltungsserver Aufruf</p>
<p>Enterprise-Szenario – ruft der Gerät Aufgabenplan DM-Client.</p></td>
<td style="vertical-align:top"><p>Der MO-Server sendet einen Server Trigger-Nachricht an den Client DM aufrufen.</p>
<p>Die Trigger-Nachricht enthält die Server-ID und weist Clientgeräts So initiieren Sie eine Sitzung mit dem Server. Clientgeräts authentifiziert die Trigger-Nachricht und stellt sicher, dass der Server autorisiert ist, die mit diesem Kontakt kommunizieren.</p>
<p>Szenario für Enterprise - zur geplanten Zeit, den DM-Client wird aufgerufen, in regelmäßigen Abständen wieder an den Enterprise-Verwaltungsserver über HTTPS aufrufen.</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top"><p>2</p></td>
<td style="vertical-align:top"><p>Das Gerät sendet eine Meldung über eine IP-Verbindung, um die Sitzung zu starten.</p></td>
<td style="vertical-align:top"><p>Diese Nachricht enthält Geräteinformationen und Anmeldeinformationen. Client und Server führen gegenseitigen Authentifizierung über einen SSL-Kanal oder auf der Anwendungsebene DM.</p></td>
</tr>
<tr class="odd">
<td style="vertical-align:top"><p>3</p></td>
<td style="vertical-align:top"><p>Der DM Server antwortet, über eine IP-Verbindung (HTTPS).</p></td>
<td style="vertical-align:top"><p>Der Server sendet die anfänglichen Gerät Management Befehle, sofern vorhanden.</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top"><p>4</p></td>
<td style="vertical-align:top"><p>Das Gerät reagiert auf Management Server.</p></td>
<td style="vertical-align:top"><p>Diese Nachricht enthält die Ergebnisse der Ausführung der angegebenen Gerät Verwaltungsvorgänge.</p></td>
</tr>
<tr class="odd">
<td style="vertical-align:top"><p>5</p></td>
<td style="vertical-align:top"><p>Dem DM beendet die Sitzung oder einen anderen Befehl sendet.</p></td>
<td style="vertical-align:top"><p>Die Sitzung DM endet, oder Schritt 4 wird wiederholt.</p></td>
</tr>
</tbody>
</table>

 

Die Nummern in der Tabelle stellen keinen Nachricht Identifikationsnummern (MsgID) dar. Alle Nachrichten vom Server benötigen eine MsgID, der innerhalb der Sitzung eindeutig ist beginnend mit 1 für die erste Nachricht und erhöhen durch eine Schrittweite von 1 für jede zusätzliche Nachricht. Weitere Informationen zum MsgID und OMA SyncML Protokoll, finden Sie unter "OMA Gerät Management Darstellung-Protokoll (OMA-TS-DM\_RepPro V1\_2-20070209-A) von der [OMA Website](http://go.microsoft.com/fwlink/p/?LinkId=526900)verfügbar.

Wenn der Gerät Antwortcode Cred-Element in der Server-Anforderung 212 ist, ist keine weiteren Authentifizierung während der OMA DM Authentifizierung auf Anwendungsebene gegenseitige für den Rest der Sitzung DM erforderlich. Bei der MD5-Authentifizierung kann das Chal-Element zurückgegeben werden. Klicken Sie dann muss die nächste Nonce in Chal für die Digestauthentifizierung MD5 verwendet werden, wenn die nächste DM-Sitzung gestartet wird.

Wenn eine Anforderung enthält die Anmeldeinformationen und der Antwortcode auf die Anforderung 200 ist, muss die gleiche Anmeldeinformationen innerhalb der nächsten Anforderung gesendet werden. Wenn das Chal-Element enthalten ist, und die MD5-Authentifizierung erforderlich ist, wird ein neuer Digest mithilfe der nächsten Nonce über das Chal-Element für die nächste Anforderung erstellt.

Weitere Informationen zu Standard- oder MD5-Client-Authentifizierung, Serverauthentifizierung MD5, MD5-Hash und Nonce MD5, finden Sie unter die OMA Gerät Management Security-Spezifikation (OMA-TS-DM\_Security-V1\_2\_1-20080617-A), Authentifizierungsantwort Codebeispiele Verarbeitung und schrittweise OMA Gerät Management Protocol-Spezifikation (OMA-TS-DM\_Protokoll V1\_2\_1-20080617-A), von der [OMA-Website](http://go.microsoft.com/fwlink/p/?LinkId=526900)zur Verfügung.


## <a name="user-targeted-vs-device-targeted-configuration"></a>Benutzer geplant, im Vergleich zu gezielten Gerätekonfiguration

Kryptografiedienstanbieter und Richtlinien, die pro Benutzerkonfiguration unterstützt, konnte MDM Server Einstellungswerte Benutzer geplant, an das Gerät gesendet, denen der Benutzer, der MDM registriert aktiv angemeldet ist. Das Gerät benachrichtigt den Server der Anmeldestatus über eine Warnung Gerät (1224) mit Benachrichtigungstyp = in DM Pkg\#1.

Die Datenteil diese Warnung konnte eine der folgenden Zeichenfolgen sein:

-   Benutzer – der Benutzer, die für das Gerät registriert ist aktiv. MDM sendet der Server konnte Benutzer Workflowkonfiguration für Kryptografiedienstanbieter-Richtlinien, die pro Benutzerkonfiguration unterstützen
-   andere – eine andere Benutzername, aber der Benutzer verfügt nicht über ein Konto MDM. Der Server nur breit Gerätekonfiguration anwenden, z. B. Konfiguration gilt für alle Benutzer im Gerät.
-   keine – keine aktiven Benutzername. Der Server kann nur breit Gerätekonfiguration anwenden und verfügbaren Konfigurationsoptionen auf der Gerät-Umgebung (keine aktiven Benutzername beschränkt ist

Es folgt eine Warnung (Beispiel):

```
<Alert>
        <CmdID>1</CmdID>
        <Data>1224</Data>
        <Item>
            <Meta>
                <Type xmlns=”syncml:metinf”>com.microsoft/MDM/LoginStatus</Type>
                <Format xmlns=”syncml:metinf”>chr</Format>
            </Meta>
            <Data>user</Data>
        </Item>
    </Alert>
```

Der Server benachrichtigt des Geräts, ob es geplant, Benutzer ist oder Gerät Ziel Konfiguration ein Präfix an den Knoten Management-LocURL mit. / Benutzer für Benutzer geplant, Konfiguration oder. / Gerät für Gerät zielorientierten Konfiguration. Wenn kein Präfix mit standardmäßig. / Gerät oder. / Benutzer, es ist geplant, Gerät Konfiguration.

Das folgende LocURL veranschaulicht eine pro Benutzer CSP Knotenkonfiguration: **./user/vendor/MSFT/EnterpriseModernAppManagement/AppInstallation/&lt;PackageFamilyName&gt;/StoreInstall**

Das folgende LocURL veranschaulicht eine pro Gerätekonfiguration CSP-Knoten: **./device/vendor/MSFT/RemoteWipe/DoWipe**


<a href="" id="syncml-response-codes"></a>
## <a name="syncml-response-status-codes"></a>SyncML Status Antwortcodes

Wenn SyncML im OMA DM verwenden, sind Standardantwort Statuscodes, die zurückgegeben werden. Die folgende Tabelle enthält allgemeine SyncML Antwortstatuscodes wahrscheinlich angezeigt werden. Weitere Informationen zu SyncML Antwortcodes Status finden Sie im Abschnitt 10 der Spezifikation [SyncML Darstellung Protokoll](http://go.microsoft.com/fwlink/p/?LinkId=526905) .

| Statuscode | Beschreibung                                                                                                                                                                                                                       |
|-------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 200         | Der SyncML Befehl wurde erfolgreich abgeschlossen.                                                                                                                                                                                        |
| 202         | Für die Verarbeitung akzeptiert. Dies ist in der Regel einer asynchronen Operation, wie eine Anforderung an eine remote Ausführung einer Anwendung ausgeführt.                                                                                                |
| 212         | Die Authentifizierung angenommen. Normalerweise wird dies nur als Reaktion auf das SyncHdr-Element (verwendet für die Authentifizierung im Standard OMA DM) angezeigt werden. Dies möglicherweise angezeigt, wenn Sie sehen Sie sich OMA DM Protokolle jedoch Kryptografiedienstanbieter nicht in der Regel dies generieren. |
| 214         | Der Vorgang wurde abgebrochen. In der Sitzung werden die SyncML Befehl wurde erfolgreich ausgeführt, aber keine weitere Befehle verarbeitet werden.                                                                                                        |
| 215         | Nicht ausgeführt. Ein Befehl wurde nicht als Ergebnis einer Benutzerinteraktion um den Befehl abzubrechen ausgeführt.                                                                                                                                   |
| 216         | `Atomic`OK zurücksetzen. Ein Befehl wurde innerhalb einer `Atomic` Element und `Atomic` ist fehlgeschlagen. Mit diesem Befehl wurde erfolgreich zurückgesetzt.                                                                                                   |
| 400         | Ungültige Anforderung. Der angeforderte Befehl konnte aufgrund einer ungültigen Syntax nicht ausgeführt werden. Kryptografiedienstanbieter normalerweise dieser Fehler generieren nicht jedoch es angezeigt werden, wenn Ihre SyncML falsch formatiert ist.                                             |
| 401         | Ungültige Anmeldeinformationen. Der angeforderte Befehl ist fehlgeschlagen, da der Requestor ordnungsgemäße Authentifizierung bereitstellen muss. Kryptografiedienstanbieter Generieren dieser Fehler normalerweise nicht.                                                                              |
| 403         | Nicht zulässig. Der angeforderte Befehl ist fehlgeschlagen, aber der Empfänger den angeforderten Befehl verstanden.                                                                                                                                      |
| 404         | Nicht gefunden. Das angeforderte Ziel wurde nicht gefunden. Wenn Sie einen Knoten abzufragen, der nicht vorhanden ist, wird dieser Code generiert.                                                                                                               |
| 405         | Der Befehl nicht zulässig. Dies reagieren, Code generiert wird, wenn Sie versuchen, einem schreibgeschützten Knoten schreiben.                                                                                                                                 |
| 406         | Optionales Feature nicht unterstützt. Diese Antwortcode wird generiert, wenn Sie versuchen, eine Eigenschaft zugreifen, die der CSP nicht unterstützt.                                                                                                |
| 415         | Nicht unterstützter Typ oder Format. XML-Analyse oder Formatierung Fehler kann diese Antwortcode führen.                                                                                                                                  |
| 418         | Bereits vorhanden ist. Diese Antwortcode tritt auf, wenn Sie versuchen, einen Knoten hinzufügen, der bereits vorhanden.                                                                                                                                       |
| 425         | Berechtigung verweigert. Der angeforderte Befehl ist fehlgeschlagen, da der Absender nicht ausreichend Zugriffssteuerungsberechtigungen (ACL) für den Empfänger verfügt. Fehler "Zugriff verweigert" Abrufen in dieses Antwortcode normalerweise übersetzt.                 |
| 500         | Der Befehl ist fehlgeschlagen. Allgemeiner Fehler. Der Empfänger ist es nicht erfüllen die Anforderung kann unerwartete Bedingung aufgetreten. Diese Antwortcode tritt auf, wenn die SyncML DPU nicht den ursprünglichen Fehlercode zuordnen kann.       |
| 507         | `Atomic`Fehler bei. Einer der Vorgänge in einer `Atomic` blockieren fehlgeschlagen.                                                                                                                                                               |
| 516         | `Atomic`Roll Fehler zurück. Ein `Atomic` Vorgang fehlgeschlagen ist und der Befehl wurde nicht zurückgesetzt.                                                                                                                         |

 

## <a name="related-topics"></a>Verwandte Themen

[Konfiguration Dienstverweis-Anbieter](configuration-service-provider-reference.md)

 






