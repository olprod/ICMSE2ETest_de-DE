---
title: ActiveSync CSP
description: ActiveSync CSP
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: c65093ef-bd36-4f32-9dab-edb7bcfb3188
ms.openlocfilehash: b7cd43447bbd81d45e46deb1cc658056cd17b8a5
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="activesync-csp"></a>ActiveSync CSP


Der Dienstanbieter für ActiveSync-Konfiguration wird zum Einrichten und Ändern der Einstellungen für Exchange ActiveSync verwendet. Nachdem ein Exchange-Konto vom Dienstanbieter ActiveSync Konfiguration over-the aktualisiert wurde, wird das Gerät abgeschaltet werden muss und Back dann Synchronisierungsstatus angezeigt eingeschaltet.

Konfigurieren von Konten über diese Konfiguration Service Provider, Windows Live ActiveSync wird nicht unterstützt.

> **Hinweis**  
Die Zielbenutzer muss für den CSP eine erfolgreiche angemeldet sein. Die richtige Weise ein Konto ist, den Pfad ./User/Vendor/MSFT/ActiveSync verwenden.

Auf dem Desktop wird nur pro Benutzer Konfiguration (./User/Vendor/MSFT/ActiveSync) unterstützt. Der Pfad ./Vendor/MSFT/ActiveSync funktioniert jedoch wenn der Benutzer angemeldet ist. CSP schlägt fehl, wenn kein Benutzer angemeldet ist.

Der Pfad ./Vendor/MSFT/ActiveSync ist veraltet, jedoch weiterhin kurzfristig arbeiten.

 

Im folgende Diagramm veranschaulicht die ActiveSync-Konfiguration dienstanbieterobjekten Management im Strukturformat von Open Allianz Verwaltung mobiler Geräte (OMA DM) OMA-Clientbereitstellung und Enterprise DM verwendet.

![ActiveSync Csp (cp)](images/provisioning-csp-activesync-cp.png)

<a href="" id="--user-vendor-msft-activesync"></a>**./User/Vendor/MSFT/ActiveSync**  
Der Stammknoten für den Dienstanbieter der ActiveSync-Konfiguration.

> **Hinweis**  
Die Zielbenutzer muss für den CSP erfolgreich angemeldet sein. Die richtige Weise ein Konto ist, den Pfad ./User/Vendor/MSFT/ActiveSync verwenden.

Auf dem Desktop wird nur pro Benutzer Konfiguration (./User/Vendor/MSFT/ActiveSync) unterstützt. Der ./Vendor/MSFT/ActiveSync funktionieren jedoch, wenn der Benutzer angemeldet ist. Der CSP schlägt fehl, wenn kein Benutzer angemeldet ist.

Der Pfad ./Vendor/MSFT/ActiveSync ist veraltet, jedoch weiterhin kurzfristig arbeiten.

 

Der unterstützte Vorgang ist abrufen.

<a href="" id="accounts"></a>**Konten**  
Der Stammknoten für alle ActiveSync-Konten.

Der unterstützte Vorgang ist abrufen.

<a href="" id="account-guid"></a>***Konto GUID***  
Definiert ein bestimmtes Konto ActiveSync. Für jedes Konto ActiveSync auf dem Gerät muss ein global eindeutiger Bezeichner (GUID) generiert werden.

Unterstützte Vorgänge sind Get, die Sie hinzufügen und löschen.

Wenn Sie über OMA DM verwalten, stellen Sie sicher, immer eine eindeutige GUID verwenden. Bereitstellung mit einem Konto mit der gleichen GUID wie eine vorhandene das vorhandene Konto löscht und das neue Konto nicht erstellt.

{} Geschweiften Klammern sind erforderlich, um die GUID. Im OMA Client bereitstellen können Sie die geschweiften Klammern eingeben. Beispiel:

``` syntax
<characteristic type="{C556E16F-56C4-4EDB-9C64-D9469EE1FBE0}"/>
```

Für OMA DM müssen Sie die Werte ASCII-7 b % und %7 D für das öffnende und schließende geschweifte Klammern, jeweils verwenden. Beispiel: Wenn die GUID "C556E16F-56C4-4EDB-9C64-D9469EE1FBE0" ist, geben Sie Folgendes ein:

``` syntax
<Target>
   <LocURI>
      ./Vendor/MSFT/ActiveSync/Accounts/%7BC556E16F-56C4-4EDB-9C64-D9469EE1FBE0%7D
   </LocURI>
</Target>
```

<a href="" id="account-guid-emailaddress"></a>**/ EmailAddress *Konto GUID***  
Erforderlich. Eine Zeichenfolge, die angibt, die e-Mail-Adresse der Exchange ActiveSync-Konto zugeordnet ist.

Unterstützte Vorgänge sind Get, ersetzen und hinzufügen (kann nicht hinzugefügt werden, nachdem das Konto erstellt wird).

Diese e-Mail-Adresse vom Benutzer eingegeben wird, während des Setups und muss die vollqualifizierte e-Mail-Adressformat, beispielsweise "someone@example.com".

<a href="" id="account-guid-domain"></a>***Konto*GUID/Domain**  
Optional in Exchange. Gibt den Domänennamen des Exchange-Servers.

Unterstützte Vorgänge sind Get, ersetzen, hinzufügen und löschen.

<a href="" id="account-guid-accounticon"></a>***Konto GUID*/AccountIcon**  
Erforderlich. Eine Zeichenfolge, die den Speicherort des Symbols, das Konto zugeordnet angibt.

Unterstützte Vorgänge sind Get, ersetzen und hinzufügen (kann nicht hinzugefügt werden, nachdem das Konto erstellt wird).

Das Symbol Konto kann verwendet werden, als eine Kachel in der Liste **zu starten** oder ein Symbol in der Anwendungsliste unter **Einstellungen &gt; e-Mail & Konten**. Einige Symbole werden auf dem Gerät bereits bereitgestellt. Das vorgeschlagene Symbol für POP/IMAP oder generische ActiveSync Konten befindet sich am Res://AccountSettingsSharedRes {*Auflösung*}! % s.genericmail.png. Das vorgeschlagene Symbol für Exchange-Konten befindet sich am Res://AccountSettingsSharedRes {*Auflösung*}! % s.office.outlook.png. Benutzerdefinierte Symbole können bei Bedarf hinzugefügt werden.

<a href="" id="account-guid-accounttype"></a>***Konto GUID*/AccountType**  
Erforderlich. Eine Zeichenfolge, die angibt, die Kontenart an.

Unterstützte Vorgänge sind Get und hinzufügen (kann nicht hinzugefügt werden, nachdem das Konto erstellt wird).

Dieser Wert wird während des Setups eingegeben und kann nicht geändert werden, einmal eingegeben. Ein Exchange-Konto wird durch den Zeichenfolgenwert "Exchange" angezeigt.

<a href="" id="account-guid-accountname"></a>***Konto GUID*/AccountName**  
Erforderlich. Eine Zeichenfolge, die den Namen gibt an, der auf das Konto auf dem Gerät verweist.

Unterstützte Vorgänge sind Get, ersetzen und hinzufügen (kann nicht hinzugefügt werden, nachdem das Konto erstellt wird).

<a href="" id="account-guid-password"></a>**/ Password *Konto GUID***  
Erforderlich. Eine Zeichenfolge, die gibt das Kennwort für das Konto an.

Unterstützte Vorgänge sind Get, ersetzen, hinzufügen und löschen.

Für den Befehl Get werden nur Sternchen zurückgegeben.

<a href="" id="account-guid-servername"></a>***Konto*GUID/Servername**  
Erforderlich. Eine Zeichenfolge, die den Namen des Servers verwendet, die für das Konto angibt.

Unterstützte Vorgänge sind Get, ersetzen und hinzufügen (kann nicht hinzugefügt werden, nachdem das Konto erstellt wird).

<a href="" id="account-guid-username"></a>***Konto*GUID/UserName**  
Erforderlich. Eine Zeichenfolge, die den Benutzernamen für das Konto angibt.

Unterstützte Vorgänge sind Get und hinzufügen (kann nicht hinzugefügt werden, nachdem das Konto erstellt wird).

Der Benutzername kann geändert werden, nachdem eine Synchronisierung erfolgreich durchgeführt wurde. Der Benutzername im Format vollqualifizierten sein kann "someone@example.com", oder nur "Benutzername", je nach Kontotyp erstellt. Bei den meisten Exchange-Konten ist das Format des Benutzernamens nur "Username" für Microsoft, Google, Yahoo und die meisten POP/IMAP-Konten, das Format des Benutzernamens"someone@example.com".

<a href="" id="options"></a>**Optionen**  
Knoten für die anderen Parameter.

<a href="" id="options-calendaragefilter"></a>**Optionen/CalendarAgeFilter**  
Gibt das Zeitfenster für Kalenderelemente an das Gerät synchronisieren verwendet. Werttyp ist chr.

<a href="" id="options-logging"></a>**Optionen-Protokollierung**  
Erforderlich. Eine Zeichenfolge, die angibt, ob Diagnoseprotokoll aktiviert ist und auf welcher Ebene. Der Standardwert ist 0 (deaktiviert).

Unterstützte Vorgänge sind Get, ersetzen und hinzufügen (kann nicht hinzugefügt werden, nachdem das Konto erstellt wird).

Gültige Werte sind folgende:

-   0 (Standard) – ist die Protokollierung deaktiviert.

-   1 – grundlegende Protokollierung ist aktiviert.

-   2 - erweiterte Protokollierung ist aktiviert.

Protokollierung ist standardmäßig deaktiviert festgelegt. Der Benutzer kann dies auf Standard oder erweitert festgelegt, wenn ein Sync-Problem auftreten, die Support für Kunden Untersuchen von ist aufgefordert. Festlegen der Protokollierungsebene auf Erweitert mehr von Leistungseinbußen als grundlegende.

<a href="" id="options-mailbodytype"></a>**Optionen/MailBodyType**  
Gibt die e-Mail-Format an. Gültige Werte:

-   0 – keine
-   1 – text
-   2 - HTML
-   3 - RTF
-   4 - MIME-

<a href="" id="options-mailhtmltruncation"></a>**Optionen/MailHTMLTruncation**  
Gibt die Größe nach der e-Mails im HTML-Format abgeschnitten werden, wenn sie das mobile Gerät synchronisiert werden. Der Wert wird in KB angegeben. Ein Wert von-1 deaktiviert abschneiden.

<a href="" id="options-mailplaintexttruncation"></a>**Optionen/MailPlainTextTruncation**  
Diese Einstellung gibt an, die Größe hinter, dem Text formatiert E-mail-Nachrichten abgeschnitten werden, wenn sie an das Mobiltelefon synchronisiert werden. Der Wert wird in KB angegeben. Der Wert-1 deaktiviert abschneiden.

<a href="" id="options-usessl"></a>**Optionen/UseSSL**  
Optional Eine Zeichenfolge, die angibt, ob SSL verwendet wird.

Unterstützte Vorgänge sind Get, ersetzen und hinzufügen (kann nicht hinzugefügt werden, nachdem das Konto erstellt wird).

Gültige Werte sind:

-   0 – wird SSL nicht verwendet werden.

-   1 (Standard) - SSL verwendet wird.

<a href="" id="options-schedule"></a>**Optionen/Zeitplan**  
Erforderlich. Eine Zeichenfolge, die gibt die Zeit, bis die nächste Synchronisierung, in Minuten ausgeführt wird. Der Standardwert ist 1.

Unterstützte Vorgänge sind Get und ersetzen.

Gültige Werte sind folgende:

-   -1 (Standard) – eine Synchronisierung nur bei Elemente empfangen werden

-   0 – alle Synchronisierungen müssen manuell ausgeführt werden

-   15 - Sync alle 15 Minuten

-   30 - Sync alle 30 Minuten

-   60 - Synchronisierung – 60 Minuten

<a href="" id="options-mailagefilter"></a>**Optionen/MailAgeFilter**  
Erforderlich. Eine Zeichenfolge, die zum Synchronisieren von e-Mails Elemente auf das Gerät verwendete das Zeitfenster angibt. Der Standardwert ist 3.

Unterstützte Vorgänge sind Get und ersetzen.

Gültige Werte sind folgende:

-   0 – kein Age-Filter wird verwendet, und alle Elemente auf das Gerät synchronisiert werden.

-   2 – e-Mail nur bis zu drei Tage alt ist auf das Gerät synchronisiert.

-   3 (Standard) – E-Mail bis zu einer Woche, die alte ist für das Gerät synchronisiert.

-   4 – e-Mail bis zu zwei Wochen alten auf das Gerät synchronisiert wird.

-   5 – e-Mail bis zu einer alten Monat ist für das Gerät synchronisiert.

<a href="" id="options-contenttypes-content-type-guid"></a>**Optionen/ContentTypes / ***_Inhaltstyp GUID_**  
Definiert den Typ des Inhalts auf einzeln aktiviert/für die Synchronisierung deaktiviert werden.

Die *GUID* -Werte zulässig sind eine der folgenden:

-   E-Mail-Adresse: "{c6d47067-6e92-480e-b0fc-4ba82182fac7}"

-   Kontakte: "{0dd8685c-e272-4fcb-9ecf-2ead7ea2497b}"

-   Kalender: "{4a5d9fe0-f139-4a63-a5a4-4f31ceea02ad}"

-   Tasks: "{783ae4f6-4c12-4423-8270-66361260d4f1}"

<a href="" id="options-contenttypes-content-type-guid-enabled"></a>* *Optionen/ContentTypes/*Inhaltstyp GUID*/ aktiviert **  
Erforderlich. Eine Zeichenfolge, die angibt, ob die Synchronisierung aktiviert oder deaktiviert für den ausgewählten Inhaltstyp ist. Der Standardwert ist "1" (aktiviert).

Unterstützte Vorgänge sind Get, ersetzen und hinzufügen (kann nicht hinzugefügt werden, nachdem das Konto erstellt wird).

Gültige Werte sind folgende:

-   0 - Synchronisierung für e-Mails, Kontakte, Kalender oder Aufgaben deaktiviert.
-   1 (Standard) – Sync ist aktiviert.

<a href="" id="options-contenttypes-content-type-guid-name"></a>* *Optionen/ContentTypes/*Inhaltstyp GUID*/Name**  
Erforderlich. Eine Zeichenfolge, die den Namen des Inhaltstyps angibt.

> **Hinweis**  Dieser Knoten ist in Windows 10 zurzeit nicht funktionsfähig.

 

Unterstützte Vorgänge sind Get, ersetzen und hinzufügen (kann nicht hinzugefügt werden, nachdem das Konto erstellt wird).

Wenn Sie hinzufügen oder Ersetzen verwenden innerhalb eines unteilbare-Blocks in die SyncML CSP gibt einen Fehler und Fehler bei der Bereitstellung. Wenn Sie hinzufügen oder ersetzen außerhalb der unteilbare-Blocks ungültig; der Fehler wird ignoriert, und wie erwartet, ist das Konto eingerichtet.

<a href="" id="policies"></a>**Richtlinien**  
Der Knoten für Mail-Textkörper Typ und e-Mail-Alter Filter.

<a href="" id="policies-mailbodytype"></a>**Richtlinien/MailBodyType**  
Erforderlich. Gibt den Typ der e-Mail-Textkörper: HTML oder nur.

Werttyp ist Zeichenfolge. Unterstützte Vorgänge sind hinzufügen, abrufen, ersetzen und löschen.

<a href="" id="policies-maxmailagefilter"></a>**Richtlinien/MaxMailAgeFilter**  
Erforderlich. Gibt das Zeitfenster für die Synchronisierung e-Mail-Elemente auf das Gerät verwendet.

Werttyp ist Zeichenfolge. Unterstützte Vorgänge sind hinzufügen, abrufen, ersetzen und löschen.

## <a name="related-topics"></a>Verwandte Themen


[Konfiguration Dienstverweis-Anbieter](configuration-service-provider-reference.md)

 

 






