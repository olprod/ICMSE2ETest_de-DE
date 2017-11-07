---
title: W7 ANWENDUNG CSP
description: W7 ANWENDUNG CSP
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 10f8aa16-5c89-455d-adcd-d7fb45d4e768
ms.openlocfilehash: ee7d6b0e90ca6a0c9e847957481ceedfb3d65cb8
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="w7-application-csp"></a>W7 ANWENDUNG CSP


Der ANWENDUNG Konfiguration-Dienstanbieter, der ein APPID des w7 hat wird für ein Gerät mit einem Konto an OMA DM bootstrapping verwendet. Obwohl dieser Konfigurationsdienstanbieter zum Einrichten eines Kontos OMA DM verwendet wird, wird er über OMA-Clientbereitstellung verwaltet.

> **Hinweis**  Dieses Dienstanbieters Konfiguration erfordert die ID\_CAP\_CSP\_FOUNDATION und ID\_CAP\_GERÄT\_MANAGEMENT\_ADMIN-Funktionen, die über ein Netzwerk Konfiguration Anwendung zugegriffen werden.

 

Die folgende Abbildung zeigt den Konfigurationsdienstanbieter im Strukturformat von OMA-Clientbereitstellung verwendet.

![W7 Anwendung Csp (dm)](images/provisioning-csp-w7-application-dm.png)

> **Hinweis**   Alle Parameter Namen und charakteristische Typen müssen Groß-/Kleinschreibung und vollständig in Großbuchstaben.
APPSRV und CLIENT-Anmeldeinformationen müssen in der Bereitstellung von XML bereitgestellt werden.

 

<a href="" id="appaddr"></a>**APPADDR**  
Diese Eigenschaft wird in das w7 ANWENDUNG Merkmal verwendet, um die Adresse des Servers DM angeben.

<a href="" id="appaddr-addr"></a>**APPADDR/ADRESSE**  
Optional Der Parameter ADRESSE wird in die APPADDR-Eigenschaft zum Abrufen oder Festlegen der Adresse des Servers OMA DM verwendet. Dieser Parameter nimmt einen String-Wert.

<a href="" id="appaddr-addrtype"></a>**APPADDR/ADDRTYPE**  
Optional Der Parameter ADDRTYPE wird in die APPADDR-Eigenschaft zum Abrufen oder Festlegen des Formats des Parameters ADRESSE verwendet. Dieser Parameter nimmt einen String-Wert.

In OMA DM XML Wenn mehrere Instanzen dieses Parameters vorhanden sind, wird der erste gültige Parameterwert verwendet.

<a href="" id="appaddr-port"></a>**APPADDR-PORT**  
Dieses Merkmal wird in die APPADDR-Eigenschaft verwendet, um Portinformationen angeben.

<a href="" id="appaddr-port-portnbr"></a>**APPADDR/PORT/PORTNBR**  
Erforderlich. Der Parameter PORTNBR wird in die PORT-Eigenschaft verwendet, abzurufen oder die Nummer des Ports für die Verbindung fest. Dieser Parameter nimmt einen numerischen Wert im Zeichenfolgenformat.

<a href="" id="appauth"></a>**APPAUTH**  
Diese Eigenschaft wird in der w7 ANWENDUNG Merkmal verwendet, um die Authentifizierungsinformationen angeben.

<a href="" id="appauth-aauthdata"></a>**APPAUTH/AAUTHDATA**  
Optional Der Parameter AAUTHDATA wird in die APPAUTH-Eigenschaft zum Abrufen oder Festlegen der zusätzliche Daten, die bei der Authentifizierung verwendet. Dieser Parameter wird verwendet, um die Nonce für Digest Authentifizierungstyp auszudrücken. Dieser Parameter nimmt einen String-Wert. Der Wert dieses Parameters ist eine base64-codierte in Form einer Reihe von Bytes. Beachten Sie, dass, wenn die AAUTHTYPE DIGEST ist, als Nonce Wert in der Hashwertberechnung MD5 verwendet wird und oktale Form von binären Daten sollte bei den Hash am Geräteseite und serverseitige Berechnung verwendet werden.

<a href="" id="appauth-aauthlevel"></a>**APPAUTH/AAUTHLEVEL**  
Erforderlich. Der Parameter AAUTHLEVEL wird in die APPAUTH-Eigenschaft verwendet, um anzugeben, ob die Anmeldeinformationen für Server-Authentifizierung oder die Authentifizierung des Clients sind. Dieser Parameter nimmt einen String-Wert. Sie können diesen Wert festlegen.

Gültige Werte:

-   APPSRV - gibt an, dass der Client mit dem OMA DM Server auf der Protokollebene DM authentifiziert.

-   CLIENT - gibt an, dass der Server an den Client OMA DM Protokollebene DM authentifiziert.

<a href="" id="appauth-aauthname"></a>**APPAUTH/AAUTHNAME**  
Optional Der Parameter AAUTHNAME wird in der APPAUTH Merkmal zur Unterscheidung von OMA DM Clientnamen verwendet. Dieser Parameter nimmt einen String-Wert. Sie können diesen Wert festlegen.

<a href="" id="appauth-aauthsecret"></a>**APPAUTH/AAUTHSECRET**  
Erforderlich. Der Parameter AAUTHSECRET wird in die APPAUTH-Eigenschaft verwendet, abrufen, oder legen Sie die Authentifizierung vertraulichen Daten für den Benutzer zu authentifizieren. Dieser Parameter nimmt einen String-Wert.

<a href="" id="appauth-aauthtype"></a>**APPAUTH/AAUTHTYPE**  
Optional Der AAUTHTYPE-Parameter, der die APPAUTH-Eigenschaft wird abgerufen oder festgelegt Authentifizierungsmethode verwendet. Dieser Parameter nimmt einen String-Wert.

Gültige Werte:

-   BASIC - gibt an, dass SyncML DM "Syncml:auth – grundlegende" Authentifizierungstyp.

-   DIGEST - gibt an, dass die SyncML DM "Syncml:auth-md5" Authentifizierungstyp.

-   Wenn AAUTHLEVEL CLIENT ist, muss AAUTHTYPE DIGEST. Wenn AAUTHLEVEL APPSRV ist, kann AAUTHTYPE BASIC oder DIGEST.

<a href="" id="appid"></a>**APPID**  
Erforderlich. Parameters APPID wird in die APPLICATION-Eigenschaft verwendet, um die Typen von Anwendungsdienste verfügbar und Protokolle zu unterscheiden. Dieser Parameter nimmt einen String-Wert. Sie können abrufen oder Festlegen dieser Wert. Der einzige gültige Wert so konfigurieren Sie die OMA-Clientbereitstellung bootstrap APPID ist w7.

<a href="" id="backcompatretrydisabled"></a>**BACKCOMPATRETRYDISABLED**  
Optional Der Parameter BACKCOMPATRETRYDISABLED wird in die APPLICATION-Eigenschaft verwendet, um anzugeben, ob in der SyncHdr (mit Ausnahme der ersten) wiederholen Erneutes Senden eines Pakets mit einer älteren Protocol Version (beispielsweise 1.1).

> **Hinweis**   Dieser Parameter enthält einen Wert nicht. Das Vorhandensein dieser Parameter bedeutet, dass Abwärtskompatibilität "Wiederholen" deaktiviert ist. Wenn der Parameter nicht vorhanden ist, bedeutet dies, dass Abwärtskompatibilität "Wiederholen" aktiviert ist.

 

<a href="" id="connretryfreq"></a>**CONNRETRYFREQ**  
Optional Der Parameter CONNRETRYFREQ wird in die APPLICATION-Eigenschaft verwendet, um anzugeben, wie viele Wiederholungsversuche DM-Client ausgeführt wird, wenn Verbindungs-Manager oder WinInet-Ebene Fehler aufgetreten sind. Dieser Parameter nimmt einen numerischen Wert im Zeichenfolgenformat. Der Standardwert ist "3". Sie können diesen Parameter festlegen.

<a href="" id="defaultencoding"></a>**DEFAULTENCODING**  
Optional Der Parameter DEFAULTENCODING wird in die APPLICATION-Eigenschaft verwendet, um anzugeben, ob der DM Client WBXML oder XML für das Paket DM verwenden sollte bei der Kommunikation mit dem Server. Sie können abzurufen, oder legen Sie diesen Parameter.

Gültige Werte sind:

-   application/vnd.syncml.DM+XML (Standard)

-   application/vnd.syncml.DM+WBXML

<a href="" id="init"></a>**"INIT"**  
Optional Der Parameter "Init" wird in die APPLICATION-Eigenschaft verwendet, um anzugeben, dass der Verwaltungsserver der Client so initiieren Sie eine Sitzung Management unmittelbar nach der Genehmigung Einstellungen möchte. Wenn das aktuelle Dokument der w7 ANWENDUNG im ROM überführt werden sollen, muss der INIT-Parameter nicht vorhanden sein.

> **Hinweis**   Dieser Knoten ist nur für Mobilfunkbetreiber und MDM Servern, die versuchen, diese zu verwenden, schlägt fehl. Dieser Knoten wird im Enterprise MDM Registrierung Szenario nicht unterstützt.
Dieser Parameter erzwingt, für die Verbindung mit dem OMA DM Server versucht das Gerät. Der Verbindungsversuch schlägt fehl, wenn die XML-DATEN während der Phase der Coldinit festgelegt ist. Eine häufige Ursache für diesen Fehler ist, dass unmittelbar nach Abschluss der Coldinit der Sender nicht bereit ist.

 

<a href="" id="initialbackofftime"></a>**INITIALBACKOFFTIME**  
Optional Der Parameter INITIALBACKOFFTIME wird in die APPLICATION-Eigenschaft verwendet, die anfängliche Wartezeit in Millisekunden an, wann der DM-Client zum ersten Mal wiederholt. Die Wartezeit wächst wesentlich. Dieser Parameter nimmt einen numerischen Wert im Zeichenfolgenformat. Der Standardwert ist "16000". Sie können erhalten möchten, oder legen Sie diesen Parameter.

<a href="" id="maxbackofftime"></a>**MAXBACKOFFTIME**  
Optional Der Parameter MAXBACKOFFTIME wird in die APPLICATION-Eigenschaft verwendet, um die maximale Anzahl der Millisekunden, nach dem Paket senden Energiesparmodus angeben Fehler. Dieser Parameter nimmt numerischen Wert im Zeichenfolgenformat. Der Standardwert ist "86400000". Sie können diesen Parameter festlegen.

<a href="" id="name"></a>**NAME**  
Optional Der Parameter NAME wird in die APPLICATION-Eigenschaft verwendet, um eine Benutzeridentität lesbare Anwendung anzugeben. Dieser Parameter wird verwendet, um Teil der Registrierungspfad für die Anwendungsparameter zu definieren. Sie können diesen Parameter festlegen.

Der Parameter NAME kann Null (kein Wert) oder eine Zeichenfolge sein. Wenn kein Wert angegeben ist, wird standardmäßig der Registrierungsspeicherort auf &lt;unbenannte&gt;.

<a href="" id="protover"></a>**PROTOVER**  
Optional Der Parameter PROTOVER wird verwendet, in der ANWENDUNG Merkmal des OMA DM-Protokolls an den Server-Version unterstützt. Kein Standardwert vorausgesetzt. Die Version des Protokolls festlegen, indem dieser Knoten wird die Protokollversion übereinstimmen, die der DM-Client auf dem Server in SyncHdr im Paket 1 meldet. Wenn dieser Knoten nicht angegeben wird, wenn ein DM-Server-Konto hinzufügen, wird die aktuelle DM Protokollversion, die der Client unterstützt verwendet. In Windows Phone ist dies 1.2. Dies ist ein benutzerdefinierter Microsoft-Parameter. Sie können diesen Parameter festlegen.

Mögliche Werte:

-   1.1

-   1.2

<a href="" id="provider-id"></a>**PROVIDER-ID**  
Optional Der PROVIDER-ID-Parameter wird in die APPLICATION-Eigenschaft verwendet, um OMA DM Servern zu unterscheiden. Es gibt die Server-ID für einen Verwaltungsserver in der aktuellen Sitzung Management verwendet. Dieser Parameter nimmt einen String-Wert. Sie können diesen Parameter festlegen.

<a href="" id="role"></a>**ROLLE**  
Optional Der Parameter ROLE wird in die APPLICATION-Eigenschaft verwendet, um die Sicherheit Anwendung schieben anzugeben, der mit die DM-Sitzung ausgeführt wird, bei der Kommunikation mit dem Server DM. Die einzigen unterstützten Rollen sind 8 (Mobilfunkbetreiber) und 32 (Enterprise). Wenn dieser Parameter nicht vorhanden ist, wird die Rolle Mobilfunkbetreiber angenommen. Die Rolle kann nur durch die Enterprise-Client-Registrierung festgelegt werden. Die Enterprise-Client kann nicht die Rolle Mobilfunkbetreiber festgelegt werden. Dies ist ein benutzerdefinierter Microsoft-Parameter. Dieser Parameter nimmt einen numerischen Wert im Zeichenfolgenformat. Sie können abzurufen, oder legen Sie diesen Parameter.

<a href="" id="to-napid"></a>**ZU NAPID**  
Optional Der Parameter AN NAPID wird in der ANWENDUNG Merkmal der Netzwerk-Zugriffspunkt angeben der Client verwendet, die mit dem OMA DM Server herstellen verwendet. Wenn mehrere AN NAPID Parameter angegeben werden, wird nur der erste Wert AN NAPID gespeichert werden. Dieser Parameter nimmt einen String-Wert. Sie können diesen Parameter festlegen.

<a href="" id="usehwdevid"></a>**USEHWDEVID**  
Optional Der Parameter USEHWDEVID wird in der ANWENDUNG Merkmal zur Gerät Hardware-ID verwenden. Einen Wert ist nicht gespeichert.

-   Wenn der Parameter nicht vorhanden ist, ist das Standardverhalten verwenden eine anwendungsspezifische GUID verwendet, statt die Hardware-Geräte-ID

-   Wenn der Parameter vorhanden ist, wird die Hardware-Geräte-ID für das DM Paket an den Server gesendet an den Knoten **./DevInfo/DevID** , und in der Quelle LocURI bereitgestellt. International Mobile Abonnenten Identität (IMEI) wird bei einem g/M2 Gerät zurückgegeben.

<a href="" id="sslclientcertsearchcriteria"></a>**SSLCLIENTCERTSEARCHCRITERIA**  
Optional Der Parameter SSLCLIENTCERTSEARCHCRITERIA wird in die APPLICATION-Eigenschaft verwendet, um die Suchkriterien für Client-Zertifikat anzugeben. Dieser Parameter unterstützt die Suche nach Betreff-Attribut und Zertifikat speichern. Wenn keine anderen Kriterien angegeben werden, wird sie ignoriert.

Die Zeichenfolge ist eine Verkettung von Name/Wert-Paaren jedes Mitglied die Paar durch das Zeichen "&" getrennt. Die Namen und Werte werden durch das Zeichen "=" getrennt. Wenn mehrere Werte vorhanden sind, wird jeder Wert durch das Unicode-Zeichen "U + F000" getrennt. Enthält den Namen oder Wert Zeichen nicht in der UNRESERVED (gemäß dem RFC2396) festlegen, werden diese Zeichen pro RFC URI Escapezeichen.

Unterstützten Namen sind Betreff und Speicher; Platzhaltersuche Zertifikat wird nicht unterstützt.

Speicher gibt an, welche Zertifikatspeicher des Clients DM durchsucht werden, um die SSL-Clientzertifikat zu suchen. Der gültige Store-Wert ist mein 5CUser %. Namen der Store ist nicht zwischen Groß-und Kleinschreibung.

> **Hinweis** % EF 80 % 80 ist das UTF8 codiert Zeichen U + F000.

 

Betreff Gibt das Zertifikat zu suchen. Um beispielsweise angeben, dass Sie ein Zertifikat mit einem bestimmten Betreff-Attribut ("CN = Tester, O = Microsoft"), verwenden Sie Folgendes:

``` syntax
<parm name="SSLCLIENTCERTSEARCHCRITERIA" 
   value="Subject=CN%3DTester,O%3DMicrosoft&amp;Stores=My%5CUser" />
```

## <a name="related-topics"></a>Verwandte Themen


[Referenz zum Konfiguration Service provider](configuration-service-provider-reference.md)

 

 






