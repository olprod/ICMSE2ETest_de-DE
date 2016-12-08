---
title: DMAcc CSP
description: DMAcc CSP
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 43e73d8a-6617-44e7-8459-5c96f4422e63
ms.openlocfilehash: 319aa3f238870edf544db61ed818eab7da44a570
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="dmacc-csp"></a>DMAcc CSP


Der Dienstanbieter für DMAcc Konfiguration kann einen OMA Gerät Management (DM) Version 1.2 Server OMA DM Kontoobjekte behandelt werden. Der Server kann dieses Dienstanbieters Konfiguration verwenden, um ein neues Konto hinzuzufügen oder ein vorhandenes Konto, einschließlich ein Konto, das neu gestartet wurde, mit dem [Dienstanbieter für w7 ANWENDUNG Konfiguration](w7-application-csp.md) verwalten

> **Hinweis**  Dieses Dienstanbieters Konfiguration erfordert die ID\_CAP\_CSP\_FOUNDATION und ID\_CAP\_GERÄT\_MANAGEMENT\_ADMIN-Funktionen aus einer Anwendung der Netzwerk-Konfiguration zugegriffen werden.

 

Für den CSP DMAcc nicht den Replace-Befehl verwendet werden, wenn der Knoten bereits vorhanden ist.

Im folgenden Diagramm wird die DMAcc Konfiguration Service Provider Verwaltung-Objekts im Strukturformat von OMA Gerätemanagement Version 1.2 verwendet. Das Protokoll OMA-Clientbereitstellung wird von dieser Konfigurationsdienstanbieter nicht unterstützt.

![Dmacc Csp (dm)](images/provisioning-csp-dmacc-dm.png)

<a href="" id="dmacc"></a>**DMAcc**  
Erforderlich. Definiert den Stammknoten aller OMA DM-Server-Konten, die das Protokoll, Version 1.2 OMA DM verwenden.

<a href="" id="accountuid"></a>***AccountUID***  
Optional Definiert den eindeutigen Bezeichner für ein Konto OMA DM Server an, die das Protokoll, Version 1.2 OMA DM verwendet wird.

Für ein Konto [w7 Anwendungsanbieters Konfiguration-Dienst](w7-application-csp.md) neu gestartet wird dieses Element vom OMA DM-Client einen eindeutigen Namen zugewiesen. Der eindeutige Name ist die hexadezimale Darstellung des 256-Bit-SHA-2-Hash der Provider-ID ab. Der OMA DM-Server kann diese Knotenname in nachfolgende OMA DM-Sitzungen ändern.

<a href="" id="accountuid-appid"></a>***AccountUID*/AppID**  
Erforderlich. Gibt die ID für das Konto der OMA DM an.

Dieser Wert muss auf "w7" festgelegt werden.

Werttyp ist Zeichenfolge. Unterstützte Vorgänge sind Add, Get, und Ersetzen Sie.

<a href="" id="accountuid-serverid"></a>***AccountUID*/ServerID**  
Erforderlich. Gibt die OMA DM Server Eindeutiger Bezeichner für das aktuelle Benutzerkonto OMA DM an. Dieser Wert wird Groß-/Kleinschreibung beachtet.

Werttyp ist Zeichenfolge. Unterstützte Vorgänge sind Add, Get, und Ersetzen Sie.

<a href="" id="accountuid-name"></a>****AccountUID/Name**  
Optional Gibt den Anzeigenamen der Anwendung an.

Werttyp ist Zeichenfolge. Unterstützte Vorgänge sind Add, Get, und Ersetzen Sie.

<a href="" id="accountuid-prefconref"></a>***AccountUID*/PrefConRef**  
Optional Gibt die bevorzugte-Konnektivität für das Konto der OMA DM an.

Dieses Element enthält einen URI auf ein NAP-Management-Objekt oder eine GUID, mit der vom Verbindungs-Manager-Verbindung. Wenn dieses Element nicht vorhanden ist, verwendet das Gerät die Standard-Verbindung, die vom Verbindungs-Manager bereitgestellt wird.

Werttyp ist Zeichenfolge. Unterstützte Vorgänge sind Add, Get, und Ersetzen Sie.

<a href="" id="accountuid-appaddr"></a>***AccountUID*/AppAddr**  
Interior-Knoten für DM-Adresse des Servers.

Erforderlich.

<a href="" id="appaddr-objectname"></a>**AppAddr / ***_ObjectName_**  
Erforderlich. Definiert die Adresse des Servers OMA DM. Nur eine Serveradresse kann konfiguriert werden.

Beim Zuordnen des [w7 ANWENDUNG Konfigurationsdienstanbieter](w7-application-csp.md) zum DMAcc Konfiguration-Dienstanbieter ist der Name dieses Elements "1". Dies ist die erste DM Adresse in den w7 APPLICATION Configuration Dienstanbieter gefunden, andere Konten DM werden ignoriert.

<a href="" id="objectname-addr"></a>***ObjectName*/Addr**  
Erforderlich. Gibt die Adresse des OMA DM-Kontos. Die Art der Adresse gespeichert wird vom AddrType-Element angegeben.

Werttyp ist Zeichenfolge. Unterstützte Vorgänge sind Add, Get, und Ersetzen Sie.

<a href="" id="objectname-addrtype"></a>***ObjectName*/AddrType**  
Erforderlich. Gibt das Format und die Interpretation des Werts Knoten Adresse. Der Standardwert ist "URI".

Der Standardwert der "URI" gibt an, dass die OMA DM Kontoadresse in **Adresse** URI-Adresse ist. Der Wert "IPv4" gibt an, dass die OMA DM Kontoadresse im **Adresse** eine IP-Adresse ist.

Werttyp ist Zeichenfolge. Unterstützte Vorgänge sind Add, Get, und Ersetzen Sie.

<a href="" id="objectname-port"></a>****ObjectName/Port**  
Inneren Knoten Port Informationen.

Optional

<a href="" id="port-objectname"></a>**Port / ***_ObjectName_**  
Erforderlich. Nur eine Portnummer kann konfiguriert werden.

Beim Zuordnen des [w7 ANWENDUNG Konfigurationsdienstanbieter](w7-application-csp.md) zum DMAcc Konfiguration-Dienstanbieter ist der Name dieses Elements "1".

<a href="" id="objectname-portnbr"></a>***ObjectName*/PortNbr**  
Erforderlich. Gibt die Portnummer des OMA MD-Konto-Adresse an. Dies muss eine Dezimalzahl sein, die innerhalb des Bereichs einer 16-Bit-Ganzzahl ohne Vorzeichen entspricht.

Werttyp ist Zeichenfolge. Unterstützte Vorgänge sind Add, Get, und Ersetzen Sie.

<a href="" id="accountuid-aauthpref"></a>***AccountUID*/AAuthPref**  
Optional Gibt die Einstellung der Anwendung Authentifizierung an.

Der Wert "BASIC" gibt an, dass der Client Standardauthentifizierung versucht. Der Wert "DIGEST" gibt an, dass der Client MD5 Authentifizierung versucht.

Wenn dieser Wert leer ist, versucht der Client mit der Authentifizierungsmethode, die in der vorherigen Sitzung ausgehandelt werden, sofern vorhanden. Wenn der Wert leer ist, keine vorherigen Sitzung vorhanden ist und MD5 Anmeldeinformationen vorhanden sind, versuchen Sie zuerst Clients MD5-Autorisierung. Wenn die Kriterien nicht erfüllt sind, und klicken Sie dann der Client GRUNDLEGENDE Autorisierung zuerst versucht.

Werttyp ist Zeichenfolge. Unterstützte Vorgänge sind Add, Get, und Ersetzen Sie.

<a href="" id="accountuid-appauth"></a>***AccountUID*/AppAuth**  
Optional Definiert die Authentifizierungseinstellungen.

<a href="" id="appauth-objectname"></a>**AppAuth / ***_ObjectName_**  
Erforderlich. Definiert eine Gruppe von Authentifizierungseinstellungen.

Beim Zuordnen des [w7 ANWENDUNG Konfigurationsdienstanbieter](w7-application-csp.md) zum DMAcc Konfiguration-Dienstanbieter ist der Name dieses Elements denselben Namen wie der AAuthLevel-Wert ("CLRED" oder "SRVCRED").

<a href="" id="objectname-aauthlevel"></a>***ObjectName*/AAuthlevel**  
Erforderlich. Gibt die Ebene der Anwendung Authentifizierung.

Der Wert "CLCRED" gibt an, dass sich der Client Anmeldeinformationen an den Server OMA DM auf Protokollebene OMA DM authentifizieren wird. Der Wert "SRVCRED" gibt an, dass der Server Anmeldeinformationen sich an den OMA DM-Client auf der Protokollebene OMA DM authentifizieren.

Werttyp ist Zeichenfolge. Unterstützte Vorgänge sind hinzufügen und ersetzen.

<a href="" id="objectname-aauthtype"></a>***ObjectName*/AAuthType**  
Erforderlich. Gibt den Authentifizierungstyp.

Wenn die AAuthlevel "CLCRED" ist, sind die unterstützten Werte "BASIC" und "DIGEST". Wenn die AAuthlevel "SRVCRED" ist, ist der unterstützte Wert "DIGEST".

Werttyp ist Zeichenfolge. Unterstützte Vorgänge sind Add, Get, und Ersetzen Sie.

<a href="" id="objectname-aauthname"></a>***ObjectName*/AAuthName**  
Optional Gibt den Authentifizierungsnamen.

Werttyp ist Zeichenfolge. Unterstützte Vorgänge sind Add, Get, und Ersetzen Sie.

<a href="" id="objectname-aauthsecret"></a>***ObjectName*/AAuthSecret**  
Optional Gibt das Kennwort oder geheimen Schlüssel für die Authentifizierung verwendet.

Werttyp ist Zeichenfolge. Unterstützte Vorgänge sind hinzufügen und ersetzen.

<a href="" id="objectname-aauthdata"></a>***ObjectName*/AAuthData**  
Optional Gibt die nächste Nonce für die Authentifizierung verwendet.

"Nonce" verweist auf eine Zahl einmal verwendet. Es ist häufig eine zufällige oder pseudozufälligen Zahl im Authentifizierungsprotokoll ausgegeben, um sicherzustellen, dass die alten Communications in Wiederholen Angriffe nicht wiederverwendet werden kann.

Werttyp ist binary. Unterstützte Vorgänge sind hinzufügen und ersetzen.

<a href="" id="accountuid-ext"></a>****AccountUID/ext**  
Erforderlich. Definiert eine Reihe von erweiterten Parametern.

Dieses Element enthält die herstellerspezifischen Informationen über das Konto OMA DM und wird automatisch erstellt, wenn das Konto OMA DM erstellt wird.

<a href="" id="ext-microsoft"></a>**Ext/Microsoft**  
Erforderlich. Definiert eine Reihe von Microsoft-spezifischen Parametern erweitert.

Dieses Element wird automatisch erstellt, wenn das Konto OMA DM erstellt wird.

<a href="" id="microsoft-backcompatretrydisabled"></a>**Microsoft/BackCompatRetryDisabled**  
Optional Gibt an, ob wiederholen Erneutes Senden eines Pakets mit einer älteren Protocol Version (beispielsweise 1.1) in der SyncHdr auf nachfolgenden Versuche (mit Ausnahme der ersten). Der Standardwert ist "FALSE".

Der Standardwert von "FALSE" gibt an, dass abwärtskompatible Wiederholungsversuche aktiviert sind. Der Wert "TRUE" gibt an, dass abwärtskompatible Wiederholungsversuche deaktiviert sind.

Werttyp ist Bool. Unterstützte Vorgänge sind Add, Get, und Ersetzen Sie.

<a href="" id="microsoft-connretryfreq"></a>**Microsoft/ConnRetryFreq**  
Optional Gibt die Anzahl der Wiederholungsversuche, die der DM-Client ausgeführt wird, wenn Verbindungs-Manager-Ebene oder Wininet Ebene Fehler aufgetreten sind.

Der Standardwert ist 3.

Werttyp ist Integer. Unterstützte Vorgänge sind Add, Get, und Ersetzen Sie.

<a href="" id="microsoft-defaultencoding"></a>**Microsoft/DefaultEncoding**  
Optional Gibt an, ob der OMA DM Client WBXML oder XML für das Paket DM verwendet bei der Kommunikation mit dem Server. Der Standardwert ist "application/vnd.syncml.dm+xml".

Der Standardwert der "application/vnd.syncml.dm+xml" gibt an, dass XML verwendet wird. Der Wert "application/vnd.syncml.dm+wbxml" gibt an, dass WBXML verwendet wird.

Werttyp ist Zeichenfolge. Unterstützte Vorgänge sind Add, Get, und Ersetzen Sie.

<a href="" id="microsoft-initialbackofftime"></a>**Microsoft/InitialBackOffTime**  
Optional Gibt die anfängliche Wartezeit in Millisekunden an, wenn der Client OMA DM zum ersten Mal wiederholt. Die Wartezeit wächst wesentlich.

Der Standardwert ist 16000.

Werttyp ist Integer. Unterstützte Vorgänge sind Add, Get, und Ersetzen Sie.

<a href="" id="microsoft-maxbackofftime"></a>**Microsoft/MaxBackOffTime**  
Optional Dieser Knoten gibt die maximale Anzahl von Millisekunden gewartet werden soll, bevor Sie versuchen, ein Verbindungsversuch an.

Der Standardwert ist 86400000.

Werttyp ist Integer. Unterstützte Vorgänge sind Add, Get, und Ersetzen Sie.

<a href="" id="microsoft-protover"></a>**Microsoft/ProtoVer**  
Optional Gibt die OMA DM-Protokollversion, die der Server unterstützt. Es gibt keinen Standardwert.

Gültige Werte sind "1.1" und "1.2". Die Protokollversion festlegen, indem dieses Element wird die Protokollversion übereinstimmen, die der DM-Client auf dem Server in SyncHdr im Paket 1 meldet. Wenn dieses Element nicht angegeben wird, wenn ein DM-Server-Konto hinzufügen, wird die aktuelle DM Protokollversion, die der Client unterstützt. Windows-10-Clients unterstützen, Version 1.2.

Werttyp ist Zeichenfolge. Unterstützte Vorgänge sind Add, Get, und Ersetzen Sie.

<a href="" id="microsoft-role"></a>**Microsoft-Rolle**  
Erforderlich. Gibt die Rollenmaske, die die Sitzung OMA DM mit bei mit dem Server Kommunikation ausgeführt wird.

Wenn dieser Parameter nicht vorhanden ist, erhält die DM-Sitzung die Rollenmaske der OMA DM-Sitzung, die der Server erstellt. Die folgende Liste enthält die gültigen Sicherheits-Rolle Masken und deren Werte an.

-   4 = SECROLE\_OPERATOR

-   8 = SECROLE\_MANAGER

-   16 = SECROLE\_BENUTZER\_AUTH

-   128 = SECROLE\_OPERATOR\_TPS

Die zulässigen Access Rollen für diesen Knoten nicht mehr als die Rollen, die das Objekt DMAcc.

Werttyp ist Integer. Unterstützte Vorgänge sind Get und ersetzen.

<a href="" id="microsoft-usehwdevid"></a>**Microsoft/UseHWDevID**  
Optional Gibt an, ob die Hardware-ID für das ./DevInfo/DevID-Element im DM Konto verwenden, um das Gerät zu identifizieren. Der Standardwert ist "FALSE".

Der Standardwert von "FALSE" gibt an, dass eine anwendungsspezifische-GUID für die ./DevInfo/DevID statt der Hardware-Geräte-ID zurückgegeben wird

Ein Wert ist "TRUE" gibt an, dass das Hardwaregerät ID werden, sofern für das ./DevInfo/DevID-Element als auch die Quelle LocURI für OMA DM, die Packen an den Server gesendet wird. In diesem Fall:

-   G/M2-Telefonen wird die IMEI zurückgegeben.

-   Für Telefone CDMA wird die MEID zurückgegeben.

-   Dieser Wert wird für zwei SIM-Telefone aus der UICC der primären Datenzeile abgerufen.

Werttyp ist Bool. Unterstützte Vorgänge sind Add, Get, und Ersetzen Sie.

<a href="" id="microsoft-usenonceresync"></a>**Microsoft/UseNonceResync**  
Optional Gibt an, ob der OMA DM Client das Verfahren Nonce erneute Synchronisierung verwenden soll, wenn die Server-Trigger-Benachrichtigung Authentifizierung ein Fehler auftritt. Der Standardwert ist "FALSE".

Wenn die Authentifizierung fehlschlägt, weil die Server Nonce nicht die Server Nonce übereinstimmt, die auf dem Gerät gespeichert ist, kann das Gerät die Sicherung Nonce als die Nonce Server verwenden. Für dieses Verfahren erfolgreich, wenn das Gerät mit dem vorkonfigurierten Nonce Wert nicht authentifiziert ist, der Server muss dann verwenden die Sicherung Nonce beim Senden der Benachrichtigung signierte Server.

Der Standardwert von "FALSE" gibt an, dass der Client nicht versucht, die Benachrichtigung mit dem Sicherungsserver Nonce authentifizieren, wenn die gespeicherte Nonce-Authentifizierung ein Fehler auftritt. Der Wert "TRUE" gibt an, dass der Client eine Sitzung DM initiiert, wenn die Sicherungsserver Nonce empfangen wird, nach dem Fehler bei der Authentifizierung.

Werttyp ist Bool. Unterstützte Vorgänge sind Add, Get, und Ersetzen Sie.

<a href="" id="crlcheck"></a>**CRLCheck**  
Optional Verbindung mit dem Server DM (Certificate Revocation List, CRL) überprüfen können. So aktivieren Sie SSL OCSP true festgelegt.

Werttyp ist Bool. Unterstützte Vorgänge sind Add, Get, und Ersetzen Sie.

<a href="" id="disableonroaming"></a>**DisableOnRoaming**  
Optional Bestimmt, ob beim roaming der OMA DM-Client gestartet werden soll.

Werttyp ist Bool. Unterstützte Vorgänge sind Add, Get, und Ersetzen Sie.

<a href="" id="sslclientcertsearchcriteria"></a>**SSLCLIENTCERTSEARCHCRITERIA**  
Optional Der Parameter SSLCLIENTCERTSEARCHCRITERIA wird an den Client Zertifikat Suchkriterien verwendet. Dieser Parameter unterstützt Suchen nach Betreff-Attribut und Zertifikat speichert. Wenn keine anderen Kriterien angegeben werden, wird sie ignoriert.

Die Zeichenfolge ist eine Verkettung von Name/Wert-Paaren jedes Mitglied die Paar durch das Zeichen "&" getrennt. Die Namen und Werte werden durch das Zeichen "=" getrennt. Wenn mehrere Werte vorhanden sind, wird jeder Wert durch das Unicode-Zeichen "U + F000" getrennt. Enthält den Namen oder Wert Zeichen nicht in der UNRESERVED (gemäß dem RFC2396) festlegen, werden diese Zeichen pro RFC URI Escapezeichen.

Unterstützten Namen sind Betreff und speichert. Platzhaltersuche Zertifikat wird nicht unterstützt.

Speicher gibt an, welche Zertifikatspeicher des Clients DM durchsucht werden, um die SSL-Clientzertifikat zu suchen. Der gültige Store-Wert ist mein 5CUser %. Namen der Store ist nicht zwischen Groß-und Kleinschreibung.

> **Hinweis** % EF 80 % 80 das UTF8 codiert Zeichen U + F000 ist.

 

Betreff Gibt das Zertifikat zu suchen. Um beispielsweise angeben, dass Sie ein Zertifikat mit einem bestimmten Betreff-Attribut ("CN = Tester, O = Microsoft"), verwenden Sie Folgendes:

``` syntax
<parm name="SSLCLIENTCERTSEARCHCRITERIA" 
   value="Subject=CN%3DTester,O%3DMicrosoft&amp;Stores=My%5CUser" />
```

Werttyp ist Zeichenfolge. Unterstützte Vorgänge sind Add, Get, und Ersetzen Sie.

## <a name="related-topics"></a>Verwandte Themen


[Konfiguration Dienstverweis-Anbieter](configuration-service-provider-reference.md)

 

 






