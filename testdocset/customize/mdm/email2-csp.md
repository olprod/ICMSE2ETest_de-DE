---
title: EMAIL2 CSP
description: EMAIL2 CSP
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: bcfc9d98-bc2e-42c6-9b81-0b5bf65ce2b8
ms.openlocfilehash: 83b10ca465b2f84b937857fdf93b63fdeed71cf9
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="email2-csp"></a>EMAIL2 CSP


Der EMAIL2 Konfiguration-Dienstanbieter (CSP) wird verwendet, um Simple Mail Transfer Protocol (SMTP) e-Mail-Konten konfigurieren.

> **Hinweis**   Dieses Dienstanbieters Konfiguration erfordert die ID\_CAP\_CSP\_FOUNDATION und ID\_CAP\_CSP\_E-MAIL-Funktionen aus einer Anwendung der Netzwerk-Konfiguration zugegriffen werden.
Auf dem Desktop wird nur pro Benutzer Konfiguration unterstützt.

 

Das folgende Diagramm zeigt die EMAIL2 Service Provider Management Konfigurationsobjekt im Strukturformat von OMA DM sowohl OMA-Clientbereitstellung verwendet.

![email2 Csp (dm, cp)](images/provisioning-csp-email2.png)

In Windows 10 Mobile können nach Out of Box-Experience des Benutzers einen OEM oder Mobilfunkbetreiber EMAIL2 Konfigurationsdienstanbieter Sie das Gerät mit einem Mobilfunkbetreiber proprietäre Mail über das Mobilfunknetz bereitstellen. Nach der Bereitstellung, **die Startseite** hat eine Kachel für den Mailanbieter proprietäre und ist auch in der Anwendungsliste unter **Einstellungen, e-Mail & Konten**ein Link hinzu. Nachdem ein Konto von EMAIL2 CSP over-the aktualisiert wurde, wird das Gerät abgeschaltet werden muss und Back klicken Sie dann auf den Synchronisierungsstatus finden Sie unter eingeschaltet.

Wenn über das Mobilfunknetz (OTA) gesendet Konfigurationsdaten nicht verschlüsselt. Beachten Sie, dass dies ein potenzielles Sicherheitsrisiko beim Senden von vertraulichen Konfigurationsdaten wie Kennwörter ist.

<a href="" id="email2"></a>**EMAIL2**  
Der Konfiguration Service Provider Stamm-Knoten.

Unterstützte Vorgang ist Get.

<a href="" id="guid"></a>***GUID***  
Definiert einen spezifischen e-Mail-Konto. Ein global eindeutiger Bezeichner (GUID) muss für jede e-Mail-Konto auf dem Gerät generiert werden. Bereitstellung mit einem Konto mit der gleichen GUID wie eine vorhandene nicht das neue Konto erstellen und Hinzufügen der Befehl schlägt in diesem Fall fehl.

Unterstützte Vorgänge sind Get, die Sie hinzufügen und löschen.

Geschweifte um die GUID sind in der EMAIL2 Konfiguration-Dienstanbieter erforderlich.

-   Für die Bereitstellung von OMA Client können die geschweiften Klammern und der wortwörtlich so gesendet werden. Beispielsweise `<characteristic type="{C556E16F-56C4-4edb-9C64-D9469EE1FBE0}"/>`.

-   OMA DM müssen die geschweiften Klammern mit den Befehlen ASCII-Werte von 0x7B und 0x7D gesendet werden. Beispielsweise`<Target><LocURI>./Vendor/MSFT/EMAIL2/0x7BC556E16F-56C4-4edb-9C64-D9469EE1FBE0x7D</LocURI></Target>`

<a href="" id="accounticon"></a>**ACCOUNTICON**  
Optional Gibt die Position des Symbols, das Konto zugeordnet.

Unterstützte Vorgänge sind Get, hinzufügen, ersetzen und löschen.

Das Symbol Konto kann als eine Druckseite in der Liste **zu starten** oder ein Symbol in der Anwendungsliste unter **Einstellungen, e-Mail & Konten**verwendet werden. Einige Symbole werden auf dem Gerät bereits bereitgestellt. Das vorgeschlagene Symbol für POP/IMAP oder generische ActiveSync-Konten befindet sich am Res://AccountSettingsSharedRes {*Auflösung*}! s.genericmail.png %. Das vorgeschlagene Symbol für Exchange-Konten befindet sich am Res://AccountSettingsSharedRes {*Auflösung*}! s.office.outlook.png %. Benutzerdefinierte Symbole können bei Bedarf hinzugefügt werden.

<a href="" id="accounttype"></a>**ACCOUNTTYPE**  
Erforderlich. Gibt die Art des Kontos an.

Unterstützte Vorgänge sind Get, hinzufügen, ersetzen und löschen.

Gültige Werte sind:

-   E-Mail-Adresse: normale e-Mail

-   VVM: visual Voicemail

<a href="" id="authname"></a>**AUTHNAME**  
Erforderlich. Zeichenfolge, die den Namen verwendet, um den Benutzer zu einem bestimmten e-Mail Konto (auch bekannt als den Namen des Benutzers Anmeldung) autorisieren angibt.

Unterstützte Vorgänge sind Get, hinzufügen, ersetzen und löschen.

<a href="" id="authrequired"></a>**AUTHREQUIRED**  
Optional Zeichenfolge, die angibt, ob der Server für ausgehende Authentifizierung erforderlich ist.

Unterstützte Vorgänge sind Get, hinzufügen, ersetzen und löschen.

Gültige Werte sind die folgenden:

-   0 – Serverauthentifizierung wird nicht benötigt.
-   1 – Authentifizierung ist erforderlich.

> **Hinweis**  Wenn dieser Wert nicht angegeben wird, erfolgt keine SMTP-Authentifizierung. Darüber hinaus ist dies SMTPALTENABLED unterscheidet.

 

<a href="" id="authsecret"></a>**AUTHSECRET**  
Optional Eine Zeichenfolge, die das Kennwort des Benutzers angibt. Dasselbe Kennwort wird für die SMTP-Authentifizierung verwendet.

Unterstützte Vorgänge sind Get, hinzufügen, ersetzen und löschen.

<a href="" id="domain"></a>**DOMÄNE**  
Optional Zeichenfolge, die die eingehenden Server Anmeldeinformationen Domäne angibt. Auf 255 Zeichen beschränkt.

Unterstützte Vorgänge sind Get, hinzufügen, ersetzen und löschen.

<a href="" id="dwnday"></a>**DWNDAY**  
Optional Zeichenfolge, die angibt, wie viele Tage darstellen sollen e-Mail sollte vom Server heruntergeladen werden.

Unterstützte Vorgänge sind Get, hinzufügen, ersetzen und löschen.

Gültige Werte sind eine der folgenden:

-   -1: Gibt an, dass alle e-Mails, die derzeit auf dem Server heruntergeladen werden sollen.

-   7: Gibt an, dass sieben Tage darstellen sollen e-Mails heruntergeladen werden sollen.

-   14: Gibt an, dass 14 Tage darstellen sollen e-Mails heruntergeladen werden sollen.

-   30: Gibt an, dass 30 Tage darstellen sollen e-Mails heruntergeladen werden sollen.

<a href="" id="inserver"></a>**INSERVER**  
Erforderlich. Zeichenfolge, die den Namen des eingehenden den Namen des Servers gibt an, und die Portnummer. Dies ist auf 62 Zeichen beschränkt. Wenn die standardmäßige Portnummer verwendet wird, müssen Sie die Portnummer angeben. Der Wert lautet:

-   Name: Serverportnummer

Unterstützte Vorgänge sind Get, hinzufügen und ersetzen.

<a href="" id="linger"></a>**NACHLAUF VERWENDET WERDEN SOLL**  
Optional Zeichenfolge, die die Dauer zwischen e-Mail senden/empfangen Updates in Minuten angibt.

Unterstützte Vorgänge sind Get, hinzufügen, ersetzen und löschen.

Gültige Werte sind:

-   0 - e-Mail-Updates müssen manuell ausgeführt werden.

-   15 (Standard) - warten Sie 15 Minuten zwischen Updates.

-   30 - 30 Minuten zwischen Updates warten.

-   60 - warten Sie 60 Minuten zwischen Updates.

-   120 - Wartezeit für 120 Minuten zwischen Updates.

<a href="" id="keepmax"></a>**KEEPMAX**  
Optional Gibt die maximale Größe für e-Mail-Anlagen. Auf dem Server bleibt jedoch Anlagen über dieser Größe werden nicht heruntergeladen werden. Die Nachricht selbst wird heruntergeladen. Dieser Wert kann nur für IMAP4-Konten festgelegt werden.

Das Limit wird in KB angegeben.

Gültige Werte sind 0, 25, 50, 125 und 250.

Der Wert 0 bedeutet, dass keine Begrenzung erzwungen wird.

Unterstützte Vorgänge sind Get, hinzufügen, ersetzen und löschen.

<a href="" id="name"></a>**NAME**  
Optional Zeichenfolge, die den Namen des Absenders angezeigt auf einer gesendeter e-Mail angibt. Es sollte auf den Namen des Benutzers festgelegt werden. Auf 255 Zeichen beschränkt.

Unterstützte Vorgänge sind Get, hinzufügen, ersetzen und löschen.

<a href="" id="outserver"></a>**OUTSERVER**  
Erforderlich. Zeichenfolge, die den Namen der Server für ausgehende e-Mail-messaging-Dienst gibt. Beschränkt auf 62 Zeichen. Der Wert lautet:

-   Name: Serverportnummer

Unterstützte Vorgänge sind Get, hinzufügen, löschen, und ersetzen.

<a href="" id="replyaddr"></a>**REPLYADDR**  
Erforderlich. Zeichenfolge, der die Antwort e-Mail-Adresse des Benutzers (in der Regel identisch mit der e-Mail-Adresse des Benutzers) angibt. Ohne dieses schlägt fehl, Senden von e-Mails. Auf 255 Zeichen beschränkt.

Unterstützte Vorgänge sind Get, hinzufügen, löschen und ersetzen.

<a href="" id="servicename"></a>**DIENSTNAME**  
Erforderlich. Zeichenfolge, die gibt den Namen des e-Mail-Diensts zum Erstellen oder bearbeiten (bis zu 32 Zeichen).

Unterstützte Vorgänge sind Get, hinzufügen, ersetzen und löschen.

> **Hinweis**   Der Dienstanbieter für EMAIL2 Konfiguration unterstützt den Befehl OMA DM **Ersetzen** auf die Parameter **SERVICENAME** und **SERVICETYPE**nicht. Um den Namen des e-Mail-Konto oder das Diensttyp Konto zu ersetzen das vorhandenen e-Mail-Konto muss gelöscht werden, und klicken Sie dann eine neue erstellt werden muss.

 

<a href="" id="servicetype"></a>**SERVICETYPE**  
Erforderlich. Zeichenfolge gibt an, die den Typ des e-Mail-Dienst zum Erstellen oder bearbeiten (z. B. "IMAP4" oder "POP3").

Unterstützte Vorgänge sind Get, hinzufügen, ersetzen und löschen.

> **Hinweis**   EMAIL2 Konfigurationsdienstanbieter unterstützt über die Parameter **SERVICENAME** und **SERVICETYPE**nicht den Befehl OMA DM **Ersetzen** . Um den Namen des e-Mail-Konto oder das Diensttyp Konto zu ersetzen, müssen Sie das vorhandenen e-Mail-Konto gelöscht, und klicken Sie dann eine neue erstellt werden muss.

 

<a href="" id="retrieve"></a>**ABRUFEN**  
Optional Gibt die maximale Größe in Bytes für Nachrichten, die von der eingehenden e-Mail-Server abgerufen. Nachrichten über diese Größe hinaus sind abgerufen, aber abgeschnitten.

Gültige Werte sind 512, 1024, 2048, 5120 20480 und 51200.

Unterstützte Vorgänge sind Get, hinzufügen, ersetzen und löschen.

<a href="" id="serverdeleteaction"></a>**SERVERDELETEACTION**  
Optional Zeichenfolge, die angibt, wie die Nachricht auf Server gelöscht wird. Gültige Werte:

-   1 – Löschen der Nachricht auf dem server
-   2: die Nachricht auf dem Server (in den Ordner Papierkorb löschen) speichern.

Ein anderer Wert führt in standardmäßigen-Aktion, die das Transportprotokoll abhängig ist.

Unterstützte Vorgänge sind Get, hinzufügen, ersetzen und löschen.

<a href="" id="cellularonly"></a>**CELLULARONLY**  
Optional Wenn dieses Flag festgelegt ist, verwendet das Konto nur das Mobilfunknetz und nicht Wi-Fi.

Werttyp ist Zeichenfolge. Unterstützte Vorgänge sind Get, hinzufügen, ersetzen und löschen.

<a href="" id="syncingcontenttypes"></a>**SYNCINGCONTENTTYPES**  
Erforderlich. Gibt eine Bitmaske für die Inhaltstypen zum Synchronisieren von unterstützt werden (z. B.: E-Mail, Kontakte, Kalender).

-   Keine Daten (0 x 0)
-   Kontakte (0 x 1)
-   E-Mail-Nachrichten (0 x 2)
-   Termine (0 x 4)
-   Aufgaben (0 x 8)
-   Notizen (0 x 10)
-   Feeds (0 x 60)
-   Netzwerk-Foto (0x180)
-   Gruppe und Raum (0 x 200)
-   Chat (0 x 400)
-   E-Mail-Empfänger E-Mail (0 x 800)
-   Server-Link (0 x 1000)
-   Alle Elemente (0xffffffff)

Unterstützte Vorgänge sind Get, hinzufügen, ersetzen und löschen.

<a href="" id="contactsserver"></a>**CONTACTSSERVER**  
Optional Server für – Kontakte synchronisieren, wenn es sich von der e-Mail-Server ist.

Unterstützte Vorgänge sind Get, hinzufügen, ersetzen und löschen.

<a href="" id="calendarserver"></a>**CALENDARSERVER**  
Optional Server für Kalender synchronisieren, wenn es sich von der e-Mail-Server ist.

Unterstützte Vorgänge sind Get, hinzufügen, ersetzen und löschen.

<a href="" id="contactsserverrequiressl"></a>**CONTACTSSERVERREQUIRESSL**  
Optional Gibt an, ob die Verbindung mit dem Kontakt Server SSL erforderlich ist.

Unterstützte Vorgänge sind Get, hinzufügen, ersetzen und löschen.

<a href="" id="calendarserverrequiressl"></a>**CALENDARSERVERREQUIRESSL**  
Optional Gibt an, ob die Verbindung mit dem Kalenderserver SSL erforderlich ist.

Unterstützte Vorgänge sind Get, hinzufügen, ersetzen und löschen.

<a href="" id="contactssyncschedule"></a>**CONTACTSSYNCSCHEDULE**  
Optional Legt den Zeitplan für die Synchronisierung von Kontaktelementen fest.

Unterstützte Vorgänge sind Get, hinzufügen, ersetzen und löschen.

<a href="" id="calendarsyncschedule"></a>**CALENDARSYNCSCHEDULE**  
Optional Legt den Zeitplan für die Synchronisierung Kalenderelemente fest.

Unterstützte Vorgänge sind Get, hinzufügen, ersetzen und löschen.

<a href="" id="smtpaltauthname"></a>**SMTPALTAUTHNAME**  
Optional Zeichenfolge, die den Anzeigenamen des Benutzers alternative SMTP-e-Mail-Konto zugeordnet angibt.

Unterstützte Vorgänge sind Get, hinzufügen, ersetzen und löschen.

<a href="" id="smtpaltdomain"></a>**SMTPALTDOMAIN**  
Optional Zeichenfolge, die den Domänennamen für alternative SMTP-Konto des Benutzers angibt.

Unterstützte Vorgänge sind Get, hinzufügen, ersetzen und löschen.

<a href="" id="smtpaltenabled"></a>**SMTPALTENABLED**  
Optional Zeichenfolge, die angibt, ob alternative SMTP-Konto des Benutzers aktiviert ist.

Unterstützte Vorgänge sind Get, hinzufügen, ersetzen und löschen.

Der Wert "FALSE" gibt an, dass das Konto des Benutzers alternative SMTP-e-Mail deaktiviert ist. Der Wert "TRUE" gibt an, dass alternative SMTP-e-Mail-Konto des Benutzers aktiviert ist.

<a href="" id="smtpaltpassword"></a>**SMTPALTPASSWORD**  
Optional Zeichenfolge, die das Kennwort für das Konto des Benutzers alternative SMTP gibt.

Unterstützte Vorgänge sind Get, hinzufügen, ersetzen und löschen.

<a href="" id="tagprops"></a>**TAGPROPS**  
Optional Definiert eine Gruppe von Eigenschaften mit nicht standardmäßigen Elementnamen an.

Unterstützte Vorgänge sind Get, hinzufügen, ersetzen und löschen.

<a href="" id="tagprops-8128000b"></a>**TAGPROPS/8128000B**  
Optional Zeichenfolge, die angibt, ob der eingehenden e-Mail-Server SSL erforderlich ist.

Unterstützte Vorgänge sind Get, hinzufügen, ersetzen und löschen.

Wert ist eine der folgenden:

-   0 – SSL ist nicht erforderlich.
-   1 – SSL ist erforderlich.

<a href="" id="tagprops-812c000b"></a>**TAGPROPS/812C000B**  
Optional Zeichenfolge, die angibt, ob der Server für ausgehende e-Mail SSL erfordert.

Unterstützte Vorgänge sind Get und ersetzen.

Wert ist eine der folgenden:

-   0 – SSL ist nicht erforderlich.
-   1 – SSL ist erforderlich.

## <a name="remarks"></a>Hinweise


Wenn eine Anwendung entfernen oder Konfiguration Rollback-bereitgestellt wird, den CSP EMAIL2 übergibt die Anforderung auf Konfigurations-Manager, die extern die Transaktion behandelt. Wenn eine MAPI-Anwendung entfernt wird, werden die Konten, die mit diesem erstellten gelöscht und alle Nachrichten und andere Eigenschaften, die das Transportprotokoll (beispielsweise Short Message Service \[SMS\], Post Office Protocol \[POP\], oder Simple Mail Transfer Protocol \[SMTP\]) möglicherweise gespeichert haben, gehen verloren. Wenn der Versuch, erstellen ein neues e-Mail-Konto nicht erfolgreich ist, wird das neue Konto automatisch gelöscht. Wenn ein Versuch zum Bearbeiten eines vorhandenen Kontos nicht erfolgreich ist, die ursprüngliche Konfiguration wird automatisch ein Rollback (wiederhergestellt).

Für OMA DM verarbeitet EMAIL2 CSP den Befehl Replace anders als die meisten anderen Konfigurationsdienstanbieter. Für den CSP EMAIL2 Konfigurations-Manager implizit fügt das fehlende Teil des Knotens ersetzt werden oder ein Segment im Pfad des Knotens, wenn es in ausgelassen wird die &lt;LocURI&gt;&lt;/LocURI&gt; blockieren. Es gibt separate Parameter für die ausgehende Server-Anmeldeinformationen definiert. Im folgenden sind die Regeln für die Ressourcenverwendung für diese Anmeldeinformationen:

-   Die eingehende Server-Anmeldeinformationen sind (AUTHNAME, AUTHSECRET und DOMÄNE) verwendet, sofern die ausgehende Serveranmeldeinformationen festgelegt wurden.

-   Wenn einige aber nicht alle der Server für ausgehende Anmeldeinformationen Parameter sind vorhanden EMAIL2 Konfiguration Dienstanbieters Fehler berücksichtigt werden.

-   Kontodetails können nicht abgefragt werden, es sei denn, das Konto GUID bekannt ist. Derzeit besteht keine Möglichkeit zum Ausführen einer Abfrage auf oberster Ebene für Konto GUIDs.

Windows 10 Mobile unterstützt Transport Layer Security (TLS), aber dies nicht explizit über dieses Dienstanbieters Konfiguration aktiviert werden, und der Benutzer über die Benutzeroberfläche TLS kann nicht aktiviert werden. Wenn die Verbindung mit dem e-Mail-Server mit zurückgestellte SSL initiiert, der Mail-Server kann als eine Serverfunktion STARTTLS senden und TLS aktiviert werden. Die folgenden Schritte zeigen, wie TLS aktiviert.

1.  Das Gerät versucht, die Mailserver mit SSL hergestellt werden soll.

2.  Wenn die SSL-Verbindung ein Fehler auftritt, versucht das Gerät zurückgestellte SSL für Verbindung verwenden.

3.  Wenn die Verbindung über SSL und zurückgestellte SSL schlägt fehl und vom Benutzer **Server verschlüsselte (SSL) Verbindung erforderlich sind ausgewählten**, versucht das Gerät nicht einer anderen Verbindung.

4.  Wenn der Benutzer nicht **Server erfordert eine verschlüsselte (SSL) Verbindung**ausgewählt haben, versucht das Gerät eine nicht-SSL-Verbindung herzustellen.

5.  Wenn die Verbindung erfolgreich ist, verwenden eines der Verschlüsselungsprotokolle, fordert das Gerät die Serverfunktionen.

6.  Wenn eine der Funktionen, die vom Mailserver gesendet STARTTLS ist und die Verbindung zurückgestellt wird, SSL, das Gerät ermöglicht TLS. TLS wird über SSL oder nicht SSL-Verbindungen nicht aktiviert.

## <a name="related-topics"></a>Verwandte Themen


[Konfiguration Dienstverweis-Anbieter](configuration-service-provider-reference.md)

 

 






