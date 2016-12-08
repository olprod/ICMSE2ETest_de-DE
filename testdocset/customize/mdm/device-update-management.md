---
title: "Verwaltung der geräteaktualisierung"
description: "In der aktuellen Gerät im Querformat PC, Tablets, Telefone und Geräte IoT werden die Lösungen Mobile Device Management (MDM) als kompakte Gerät Management Technologie verbreitet immer."
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: C27BAEE7-2890-4FB7-9549-A6EACC790777
ms.openlocfilehash: 1d080a97bf0516089b4e7b0528612746c87f4f30
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="device-update-management"></a>Verwaltung der geräteaktualisierung

In der aktuellen Gerät im Querformat PC, Tablets, Telefone und Geräte IoT werden die Mobile Device Management (MDM) Lösungen als kompakte Gerät Management Technologie verbreitet immer. In Windows 10 werden wir stark Investitionen in MDMs die Management-Funktionen erweitern. Eines der wichtigsten Merkmale, die, das wir hinzufügen, ist die Möglichkeit für MDMs auf Geräten mit den neuesten Microsoft-Updates Remotesite aktuell zu halten.

Insbesondere bietet Windows 10 zusätzliche APIs, um MDMs zu aktivieren:

-   Stellen Sie sicher, dass Computern durch Konfigurieren von Richtlinien für automatische Updates ist auf dem neuesten Stand bleiben.
-   Testen von Updates auf einer kleineren Gruppe von Computern vor der unternehmensweiten Einführung durch konfigurieren, welche Updates für ein bestimmtes Gerät genehmigt werden.
-   Abrufen des Status der verwalteten Geräte Compliance dies IT können auf einfache Weise zu verstehen, die noch erkennen muss einen bestimmten Sicherheitspatch Computern oder wie auf dem neuesten Stand ist ein bestimmter Computer.

Dieses Thema bietet MDM ISVs mit den Informationen, die benötigten Verwaltung in Windows 10 implementieren.

In Windows 10 wurde das Protokoll MDM erweitert, um IT-Administratoren zum Verwalten von Updates besser zu aktivieren. Insbesondere hat Windows Konfiguration-Dienstanbieter (CSP) hinzugefügt, die Richtlinien und Aktionen für MDMs zu verfügbar zu machen:

-   Konfigurieren von Richtlinien für automatische Updates, um sicherzustellen, dass Geräte auf dem neuesten Stand bleiben.
-   Rufen Sie Compliance Geräteinformationen (die Liste der Updates, die erforderlich sind, aber noch nicht installiert).
-   Geben Sie eine pro Gerät Genehmigung Updateliste, um sicherzustellen, dass die Geräte nicht noch nicht genehmigte Updates installieren, die nicht getestet wurden.
-   Genehmigen Sie EULAs im Namen der Endbenutzer, damit die Bereitstellung auch für Updates mit EULAs automatisiert werden kann.

Die OMA DM APIs zur Angabe aktualisieren Genehmigungen und erste Compliance Verweis Statusupdates mit einer ID aktualisieren die ist eine GUID, die ein bestimmtes Update identifiziert. Die MDM natürlich wird IT lesbar verfügbar machen möchten Informationen zum Update (anstatt eine unformatierte GUID), das Update-Titel, Beschreibung, KB, einschließlich Typ (beispielsweise ein Security Update oder Service Pack) aktualisieren. Weitere Informationen finden Sie unter [ \[MS-WSUSSS\]: Windows Update Services: Server-zu-Server-Protokolls](http://go.microsoft.com/fwlink/p/?LinkId=526707).
Weitere Informationen zu der Kryptografiedienstanbieter finden Sie unter [CSP aktualisieren](update-csp.md) und Update-Richtlinie der [Richtlinie CSP](policy-configuration-service-provider.md).

Die folgende Abbildung bietet eine grundlegende Übersicht über die Funktionsweise dieser:

![Verwaltung von mobilen Geräten update](images/mdm-update-sync.png)

Das Diagramm kann grob in drei Bereiche unterteilt werden:

-   Der Verwaltungsdienst Gerät synchronisiert Aktualisierungsinformationen (Titel, Beschreibung, Anwendungsmöglichkeiten) von Microsoft Update unter Verwendung des Server-zu-Server-Sync-Protokolls (oberen Rand des Diagramms).
-   Der Dienst Gerätemanagement legt Richtlinien für automatische Updates ist, ruft Informationen zum Update von Compliance und Genehmigungen über OMA DM (linken Teil des Diagramms).
-   Das Gerät Updates von Microsoft Update verwenden Client/Server-Protokoll, ruft aber nur Updates heruntergeladen und installiert, die für das Gerät und Genehmigung sind IT (rechten Teil des Diagramms).

## <a name="a-href-idgettingupdatemetadataagetting-update-metadata-using-the-server-server-sync-protocol"></a><a href="" id="gettingupdatemetadata"></a>Erste Update-Metadaten, die unter Verwendung des Server-zu-Server-Sync-Protokolls

Microsoft Update-Katalog ist enorm und enthält viele Updates, die nicht von MDM verwalteten Geräte, einschließlich Updates für legacy Software (beispielsweise Updates zu Servern kompatible PC-Betriebssysteme und Legacyanwendungen) und eine große Anzahl von Treibern benötigt werden. Es wird empfohlen, dass die MDM verwenden Sie das Server-zu-Server-Sync-Protokoll zum Abrufen von Updatemetadaten nach Updates vom Client gemeldet.

In diesem Abschnitt wird beschrieben, wie Sie dies tun. Im folgenden Diagramm wird der Server synchronisieren Protokoll Prozess.

![MDM Servern sync](images/deviceupdateprocess2.png)

MSDN bietet viele Informationen zu den Servern Sync-Protokoll. Insbesondere:

-   Es wird eine SOAP-Protokoll, und Sie erhalten die WSDL-DATEI in [Sync-Webdienst](http://go.microsoft.com/fwlink/p/?LinkId=526727). Die WSDL-DATEI kann zum aufrufenden Proxys für viele programming Umgebungen, generieren, die Ihre Arbeitserleichterung verwendet werden.
-   Codebeispiele finden Sie in den [Beispielen Protokoll](http://go.microsoft.com/fwlink/p/?LinkId=526720). Der Beispielcode zeigt unformatierte SOAP-Befehle, die verwendet werden kann. Obwohl es noch einfacher für den Aufruf aus einer Programmiersprache wie .NET (Aufrufen der WSDL-DATEI generierten Proxys) ist. Vom Server Sync WSDL aus den vorstehenden Link MSDN generierte Stub generiert eine falsche Bindung-URL. Die URL der Bindung auf Https festgelegt werden sollte:<span></span>/ / fe2.update.microsoft.com/v6/ServerSyncWebService/serversyncwebservice.asmx.

Einige der wichtigsten wichtige Punkte:

-   Das Protokoll hat eine Autorisierung Phase (Aufrufen von GetAuthConfig, GetAuthorizationCookie und GetCookie). Im [Protokoll Beispiele](http://go.microsoft.com/fwlink/p/?LinkId=526720)die **Beispiel 1: Autorisierung** Code wird veranschaulicht, wie Sie dies tun. Obwohl dies die Autorisierung Phase aufgerufen wird, ist das Protokoll vollständig geöffnet (keine Anmeldeinformationen sind erforderlich, damit diese Phase des Protokolls ausgeführt). Diese Folge der Aufrufe muss ausgeführt werden, um ein Cookie für den Hauptteil des Sync-Protokolls zu erhalten. Zur Optimierung können Sie das Cookie Zwischenspeichern und nur erneut aufrufen in den folgenden Schritten, wenn Ihr Cookie abgelaufen ist.
-   Das Protokoll ermöglicht die MDM Update-Metadaten für eine bestimmte Aktualisierung durch Aufrufen von GetUpdateData synchronisieren. Weitere Informationen finden Sie unter [GetUpdateData](https://msdn.microsoft.com/library/dd304816.aspx) in MSDN. Die LocURI anwendbaren Updates mit ihrer Version abrufen Zahlen ist `<LocURI>./Vendor/MSFT/Update/InstallableUpdates?list=StructData</LocURI>`. Da nicht alle Updates über Sync S2S verfügbar sind, stellen Sie sicher, dass die SOAP-Fehler behandelt werden.
-   Für mobile Geräte können Sie entweder Metadaten für ein bestimmtes Update durch den aufrufenden GetUpdateData synchronisieren, oder für eine lokale lokale Lösung können Sie WSUS verwenden und die mobilen Updates manuell von der Microsoft Update-Katalog-Website importieren. Weitere Informationen finden Sie unter [Prozessflussdiagramm und Screenshots der Serverprozess synchronisieren](#process-flow-diagram-and-screenshots-of-server-sync-process).

> **Hinweis**  Auf Microsoft Update ruft Metadaten für ein bestimmtes Update Laufe der Zeit (beschreibende Informationen zu aktualisieren, Beheben von Fehlern in Anwendungsmöglichkeiten Regeln, Lokalisierung Änderungen usw.) geändert. Jedes Mal, wenn eine solche Änderung vorgenommen wird, die das Update selbst und nicht beeinträchtigt wird, wird eine neue Updateversion erstellt. Die Identität der ein Revision-Updates ist ein zusammengesetzter Schlüssel mit UpdateID (GUID) und einer RevisionNumber (Int). Die MDM sollten nicht verfügbar machen das Konzept der ein Revision-Updates auf IT. Stattdessen für jedes UpdateID (GUID) der MDM nur die Metadaten für die spätere Version des Updates (eine mit der höchsten Versionsnummer) beibehalten werden soll.


## <a name="a-href-idexamplesofupdatestructureaexamples-of-update-metadata-xml-structure-and-element-descriptions"></a><a href="" id="examplesofupdatestructure"></a>Beispiele für Update Metadaten XML-Struktur und Element Beschreibungen

Die Antwort des Anrufs GetUpdateData gibt ein Array von ServerSyncUpdateData, die die Update-Metadaten im XmlUpdateBlob-Element enthält. Das Schema der XML-Update steht unter [Protokoll Beispiele](http://go.microsoft.com/fwlink/p/?LinkId=526720)zur Verfügung. Einige der wichtigsten Elemente werden im folgenden beschrieben:

-   **UpdateID** – der eindeutige Bezeichner für ein update
-   **RevisionNumber** – Revisionsnummer für die Aktualisierung im Fall das Update wurde geändert.
-   **CreationDate** – das Erstellungsdatum dieses Update.
-   **UpdateType** – den Typ der Aktualisierung, die Folgendes enthalten kann:
    -   **Erkennungsobjekt** – Wenn diese Update Identität eine Kompatibilitätslogik darstellt
    -   **Kategorie** – eine der folgenden darstellen:
        -   Eine Produktkategorie des Updates gehört. Windows, MS Office beispielsweise das usw. an.
        -   Die Klassifizierung des Updates gehört. Treiber, Sicherheit usw..
    -   **Software** – Wenn die Aktualisierung eines Softwareupdates ist.
    -   **Treiber** – Wenn Sie das Update ist ein aktualisierter Treiber.
-   **LocalizedProperties** – stellt die Sprache, die das Update verfügbar ist, Titel und Beschreibung des Updates. Weist die folgenden Felder:
    -   **Sprache** – Code den Sprachbezeichner (LCID). En oder es.
    -   **Titel** – Titel des Updates. Beispielsweise "Windows SharePoint Services 3.0 Service Pack 3 X64 Edition (KB2526305)"
    -   **Beschreibung** – Beschreibung des Updates. Beispielsweise "bietet Windows SharePointServices 3.0 Servicepack 3 (KB2526305) die neuesten Updates für Windows SharePointServices 3.0. Nach der Installation dieses Element müssen Sie möglicherweise den Computer neu starten. Nachdem Sie diesen Artikel installiert haben, kann es entfernt werden."
-   **KBArticleID** – der KB-Artikelnummer für dieses Update, das Details zu bestimmten Update verfügt. Beispielsweise <http://support.microsoft.com/kb/2902892>.

## <a name="a-href-idrecommendedflowarecommended-flow-for-using-the-server-server-sync-protocol"></a><a href="" id="recommendedflow"></a>Empfohlene Ablauf bei der Verwendung von Server-zu-Server-Sync-Protokoll

In diesem Abschnitt wird beschrieben, einen möglichen Algorithmus zum das Sync-Protokoll für Server-zu-Server mithilfe von pull in Update-Metadaten, die MDM

Zuerst Hintergrund einige:

- Wenn Sie eine mit mehreren Mandanten MDM haben, kann die Update-Metadaten in einer freigegebenen Partition, gehalten werden, da es für alle Mandanten üblich ist.
- Dann kann ein Metadatendienst Sync implementiert werden, die in regelmäßigen Abständen Servern synchronisieren aufruft, um anderen pull in Metadaten für die IT-Updates zu werden.
- Die MDM-Komponente, DIE OMA DM-Geräte gesteuert (im nächsten Abschnitt beschrieben) verwendet, sollte der senden Synchronisierungsdienst Metadaten der Liste der erforderlichen Updates senden, die von jedem Client Ruft ab, wenn die Updates auf das Gerät nicht bereits bekannt sind.


Das folgende Verfahren beschreibt einen grundlegenden Algorithmus für einen Metadatendienst Sync:

-   Initialisierung, setzt sich aus den folgenden:
    1.  Erstellen Sie eine leere Liste von "benötigt in einen Fehler-IDs aktualisieren". Diese Liste wird durch die MDM-Dienstkomponente aktualisiert, die der OMA DM verwendet. Es wird empfohlen, Definitionsupdates nicht zu dieser Liste hinzufügen, da dies temporär (beispielsweise Defender Mitteilungen zu 4 neue Definitionsupdates pro Tag, von die jedes kumulative ist) sind.
    2.  Erstellen Sie eine leere Liste von "Produktkategorien" (oder gerne es mit einem bekannten Produktkategorie vorab auszufüllen, die Sie benötigen).
-   In regelmäßigen Abständen synchronisieren (Wir empfehlen einmal alle zwei Stunden - nicht mehr als einmal / Stunde).
    1.  Implementieren der Autorisierung Phase des Protokolls ein Cookie abrufen, wenn bereits ein Cookie nicht abgelaufen ist. Finden Sie unter **Beispiel 1: Autorisierung** im [Protokoll Beispiele](http://go.microsoft.com/fwlink/p/?LinkId=526720).
    2.  Implementieren des Metadaten-Teils des Protokolls (finden Sie unter **Beispiel 2: Metadaten und Bereitstellungen Synchronisierung** in den [Beispielen Protocol](http://go.microsoft.com/fwlink/p/?LinkId=526720)), und:
        -   Geben Sie die Update-Klassifizierung = Sicherheitsupdates und Produktkategorien = aktuelle Liste (zunächst leer) als Filter für GetRevisionIdList dieser Schritt optional ist, wenn Sie proaktiv in Sicherheitsupdates abrufen möchten.
        -   Rufen Sie GetUpdateData für alle Updates von GetRevisionIdList zurückgegeben und alle Updates in der Liste "benötigt-IDs in fault aktualisieren", wenn die Update-Metadaten nicht bereits in die DB gezogen wurde.
            -   Ist das Update auf eine neuere Version eines vorhandenen Updates (gleichen UpdateID, höhere Revisionsnummer), ersetzen Sie die vorherigen Update-Metadaten durch den neuen.
            -   Wenn die Produktkategorie Updates in der Liste "Produktkategorien" noch nicht vorhanden ist, fügen Sie ihn zu dieser Liste.
            -   Updates aus der Liste "benötigt in einen Fehler-IDs aktualisieren" entfernt, sobald sie geschaltet haben.

Dies bietet eine effiziente Möglichkeit zum in der Informationen über den Satz von Microsoft-Updates, IT pull Anforderungen zu verwalten, damit die Informationen in verschiedenen Update Management Szenarien verwendet werden kann. Beispielsweise zur Genehmigung Aktualisierungszeit Sie können pull Informationen dies IT können sehen, welche Updates diese genehmigen oder installiert für Compliance-Berichte, um festzustellen, welche Updates noch aber nicht erforderlich sind.

## <a name="a-href-idmanagingupdatesamanaging-updates-using-oma-dm"></a><a href="" id="managingupdates"></a>Verwalten von Updates mit OMA DM

Ein MDM kann Updates über OMA DM verwalten. Die Details zum verwenden und das Windows OMA DM-Protokoll eine MDM integriert, und zum Registrieren Geräte für MDM Management, wird das [Verwaltung von mobilen Geräten](mobile-device-enrollment.md) Thema dokumentiert. In diesem Abschnitt konzentriert sich auf wie diese Integration zur Unterstützung der Verwaltung von erweitern. Die wichtigsten Aspekte bei der Verwaltung von umfassen Folgendes:

-   Konfigurieren von Richtlinien für automatische Updates, um sicherzustellen, dass Geräte auf dem neuesten Stand bleiben.
-   Abrufen von Compliance Geräteinformationen (die Liste der Updates, die erforderlich sind, aber noch nicht installiert)
-   Geben Sie eine Liste pro Gerät Update Genehmigung, um sicherzustellen, dass die Geräte nicht noch nicht genehmigte Updates installieren, die nicht getestet wurden.
-   Im Namen der Endbenutzer genehmigen Sie EULAs, damit die Bereitstellung auch für Updates mit EULAs automatisiert werden können

Die folgende Liste beschreibt ein vorgeschlagenes Modell für die Anwendung von Updates.

1.  "Test Group" und "Alle-Gruppe" haben.
2.  Klicken Sie in der Gruppe Test Regeln zum automatischen einrichten alle Updates genehmigen.
3.  Richten Sie in der Gruppe alle Sie automatisch genehmigen Definitionen, wichtige Updates und Sicherheitsupdates.
4.  Für alle anderen Kategorien in die Gruppe alle Wartezeit für 7 Tage und klicken Sie dann auf automatische genehmigen. Dadurch wird der IT-Administrator unapprove Updates, die Probleme in Testgruppe angezeigt haben.

Updates werden über eine Kombination aus den [CSP aktualisieren](update-csp.md)und die Update-Teil der [Richtlinie CSP](policy-configuration-service-provider.md)konfiguriert. Finden Sie in diesen Themen Weitere Informationen zum Konfigurieren von Updates.

### <a name="update-policies"></a>Aktualisieren von Richtlinien

Das Unternehmen IT können konfigurieren AutoUpdate-Richtlinien über OMA DM mit dem [Gruppenrichtlinienobjekt CSP](policy-configuration-service-provider.md) (diese Funktionalität wird in 10 für Windows Mobile und Windows 10 Home nicht unterstützt. Es folgt das Diagramm CSP des Knotens Update im Bereich CSP Richtlinie.

Das folgende Diagramm zeigt die Update-Richtlinien in einer Struktur.

![Csp Diagramm aktualisieren](images/update-policies.png)

<a href="" id="update-activehoursend"></a>**Update/ActiveHoursEnd**  
> **Hinweis**  Diese Richtlinie steht auf Windows 10 Pro Windows 10 Enterprise, Windows 10 Education und Windows 10 Mobile Enterprise

In Windows 10, Version 1607 hinzugefügt. Ermöglicht der IT-Administrator (bei Verwendung mit **Update/ActiveHoursStart**) zum Verwalten von eines Bereichs des aktiven Stunden, in dem Update Neustarts nicht geplant werden. Dieser Wert wird die Endzeit. Es gibt 12-Stunden maximale aus Startzeit.

Unterstützte Werte sind 0 – 23, 0 ist, auf dem 00: 00 Uhr, 1 ist 1 h, Etc.

Der Standardwert ist 17 (17: 00 Uhr).

<a href="" id="update-activehoursstart"></a>**Update/ActiveHoursStart**  
> **Hinweis**  Diese Richtlinie steht auf Windows 10 Pro Windows 10 Enterprise, Windows 10 Education und Windows 10 Mobile Enterprise

In Windows 10, Version 1607 hinzugefügt. Ermöglicht die IT-Administrator (bei Verwendung mit **Update/ActiveHoursEnd**) zum Verwalten von eines Bereichs von Stunden wobei Update Neustarts nicht geplant werden. Dieser Wert wird die Startzeit. Es gibt 12-Stunden maximale aus Startzeit.

Unterstützte Werte sind 0 – 23, 0 ist, auf dem 00: 00 Uhr, 1 ist 1 h, Etc.

Der Standardwert ist 8 (8: 00).

<a href="" id="update-allowautoupdate"></a>**Update/AllowAutoUpdate**  
> **Hinweis**  Diese Richtlinie steht auf Windows 10 Pro Windows 10 Enterprise, Windows 10 Education und Windows 10 Mobile Enterprise
 
Ermöglicht der IT-Administrator zum Verwalten von Automatische Updateverhalten, um zu überprüfen, herunterladen und Installieren von Updates.

Unterstützte Vorgänge sind Get und ersetzen.

In der folgenden Liste sind die unterstützten Werte:

-   0 – benachrichtigen den Benutzer vor dem Update herunterladen. Diese Richtlinie wird vom Unternehmen verwendet, die die Endbenutzern zum Verwalten von datennutzungs-aktivieren möchte. Mit dieser Option werden Benutzer benachrichtigt, wenn Updates, die gelten für das Gerät und zum Download bereit. Benutzer können herunterladen und Installieren von Updates von der Windows Update-Systemsteuerung.
-   1 – automatische Update installieren und benachrichtigt dann den Benutzer so planen Sie einen Neustart des Geräts. Updates in Netzwerken nicht gemessene automatisch heruntergeladen und installiert während "Automatische Verwaltung", wenn das Gerät nicht verwendet wird und nicht auf Batterie ausgeführt wird. Automatische Wartung kann nicht zum Installieren von Updates für zwei Tage ist, wird Windows Update Updates sofort installieren. Wenn die Installation ein Neustart erforderlich ist, wird der Endbenutzer aufgefordert, um den Zeitplan neu starten. Der Endbenutzer hat bis zu sieben Tage so planen Sie die neu starten und anschließend ein Neustart des Geräts erzwungen wird. Aktivieren der Endbenutzers die Startzeit steuern verringert das Risiko von versehentlichen Datenverlust aufgrund von Anwendungen, die beim Herunterfahren nicht ordnungsgemäß beim Neustart des Computers nicht ausführen.
-   2 (Standard) – automatische Installieren und neu starten. Updates in Netzwerken nicht gemessene automatisch heruntergeladen und installiert während "Automatische Verwaltung", wenn das Gerät nicht verwendet wird und nicht auf Batterie ausgeführt wird. Wenn die automatische Wartung kann nicht zum Installieren von Updates für zwei Tage ist, wird Windows Update sofort Updates installieren. Wenn ein Neustart erforderlich ist, klicken Sie dann das Gerät automatisch neu gestartet wird, wenn das Gerät nicht aktiv verwendet wird. Dies ist das Standardverhalten für nicht verwaltete Geräte. Geräte schnell aktualisiert werden, aber es erhöhen das Risiko eines unbeabsichtigten Datenverluste durch eine Anwendung, die nicht herunterfahren ordnungsgemäß beim Neustart lässt.
-   3 – automatische Installieren und zu einem bestimmten Zeitpunkt starten. Die IT gibt Installation Datum und Uhrzeit an. Wenn kein Tag und die Uhrzeit angegeben sind, ist die Standardeinstellung täglich 03: 00 Uhr. Automatische Installation erfolgt zu diesem Zeitpunkt und Neustart des Geräts geschieht nach einen Countdown 15 Minuten. Wenn der Benutzer angemeldet ist, wenn Windows Neustart bereit ist, kann der Benutzer den Countdown 15 Minuten, um den Neustart zu verzögern unterbrochen werden.
-   4 – automatische Installieren und neu starten, ohne Kontrolle durch den Endbenutzer. Updates in Netzwerken nicht gemessene automatisch heruntergeladen und installiert während "Automatische Verwaltung", wenn das Gerät nicht verwendet wird und nicht auf Batterie ausgeführt wird. Wenn die automatische Wartung kann nicht zum Installieren von Updates für zwei Tage ist, wird Windows Update sofort Updates installieren. Wenn ein Neustart erforderlich ist, klicken Sie dann das Gerät automatisch neu gestartet wird, wenn das Gerät nicht aktiv verwendet wird. Diese Einstellung Option wird auch die Endbenutzer-Systemsteuerung auf schreibgeschützt.
-   5 – automatische Updates deaktivieren.

> **Wichtig**  Diese Option sollte nur für Systeme unter Einhaltung von Vorschriften, verwendet werden, wie Sie Sicherheitsupdates auch nicht abgerufen werden.
   
Wenn die Richtlinie nicht konfiguriert ist, rufen Sie Endbenutzern das Standardverhalten (automatische Installieren und neu starten).

<a href="" id="update-allowmuupdateservice"></a>**Update/AllowMUUpdateService**  
> **Hinweis**  Diese Richtlinie steht unter Windows 10 Pro, Windows 10 Enterprise und Windows 10 Bildungseinrichtungen

In Windows 10, Version 1607 hinzugefügt. Ermöglicht der IT-Administrator zum Verwalten von fest, ob nach app-Updates von Microsoft Update.

In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen oder nicht konfiguriert.
-   1 – zulässig. Updates über Microsoft Update empfangen akzeptiert.

<a href="" id="update-allownonmicrosoftsignedupdate"></a>**Update/AllowNonMicrosoftSignedUpdate**  
> **Hinweis**  Diese Richtlinie steht auf Windows 10 Pro Windows 10 Enterprise, Windows 10 Education und Windows 10 Mobile Enterprise

Ermöglicht der IT-Administrator verwalten, ob automatische Updates akzeptiert Updates von Entitäten als Microsoft signiert werden, wenn das Update an der Position UpdateServiceUrl gefunden wird. Diese Richtlinie unterstützt die Verwendung von WSUS für die 3. Partei Software- und Patch-Verteilung.

Unterstützte Vorgänge sind Get und ersetzen.

In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen oder nicht konfiguriert. Updates aus einem Intranet Microsoft Update Service Location müssen von Microsoft signiert sein.
-   1 – zulässig. Akzeptiert die Updates, die über ein Intranet Microsoft Update Service Location empfangen, wenn sie mit einem Zertifikat im Zertifikatspeicher des lokalen Computers "Vertrauenswürdige Herausgeber" gefunden signiert sind.

Diese Richtlinie gilt für desktop und lokale Veröffentlichung über WSUS 3. Partei Updates (Binärdateien und Updates auf Microsoft Update nicht gehostet) und ermöglicht IT verwalten, ob automatische Updates akzeptiert Updates von Entitäten als Microsoft signiert werden, wenn das Update auf einem Intranet Microsoft Update Service Location gefunden wird.

<a href="" id="update-allowupdateservice"></a>**Update/AllowUpdateService**  
> **Hinweis**  Diese Richtlinie steht auf Windows 10 Pro Windows 10 Enterprise, Windows 10 Education und Windows 10 Mobile Enterprise

 

Gibt an, ob das Gerät Microsoft Update, Windows Server Update Services (WSUS) oder Windows Store verwendet werden konnte.

Selbst wenn Windows Update konfiguriert ist, Updates von einer internen Updatedienst erhalten, wird es in regelmäßigen Abständen Informationen aus der öffentlichen Windows Update-Dienst so aktivieren Sie künftig zum Aktualisieren von Windows und andere Dienste wie Microsoft Update oder Windows Store abzurufen

Durch Aktivieren dieser Richtlinie wird diese Funktionalität deaktivieren und möglicherweise die Verbindung mit öffentlichen Diensten wie etwa Windows Store nicht mehr funktioniert.

In der folgenden Liste sind die unterstützten Werte:

-   0 – Update-Dienst nicht zulässig.
-   1 (Standard) – ist Updatedienst zulässig ist.

> **Hinweis**  Diese Richtlinie gilt nur bei der Desktop oder Gerät konfiguriert ist zum Herstellen eines Updatedienst mit der Richtlinie "Specify Intranet Microsoft Update Service Location".

 

<a href="" id="update-branchreadinesslevel"></a>**Update/BranchReadinessLevel**  
> **Hinweis**  Diese Richtlinie steht auf Windows 10 Pro Windows 10 Enterprise, Windows 10 Education und Windows 10 Mobile Enterprise

 

In Windows 10, Version 1607 hinzugefügt. Ermöglicht der IT-Administrator, welche zweigstellenbereitstellung ein Gerät empfängt ihre Updates von festgelegt.

In der folgenden Liste sind die unterstützten Werte:

-   16 (Standard) – Ruft den Benutzer alle anwendbaren Upgrades von aktuellen Branch (CB).
-   32 – Benutzer ruft Upgrades aus Zweig aktuell für die Business (CBB) ab.

<a href="" id="update-deferfeatureupdatesperiodindays"></a>**Update/DeferFeatureUpdatesPeriodInDays**  
> **Hinweis**  Diese Richtlinie ist auf Windows 10 Pro, Windows 10 Enterprise, Windows 10 Education verfügbar.
Da diese Richtlinie nicht gesperrt ist, erhalten Sie bei Verwendung einer Windows 10 Mobile-Gerät konfigurieren keine Fehlermeldung angezeigt. Die Richtlinie wird jedoch nicht wirksam wird.

 

In Windows 10, Version 1607 hinzugefügt. Verzögert Feature Updates für die angegebene Anzahl von Tagen an.

Unterstützte Werte sind 0 180.

<a href="" id="update-deferqualityupdatesperiodindays"></a>**Update/DeferQualityUpdatesPeriodInDays**  
> **Hinweis**  Diese Richtlinie steht auf Windows 10 Pro Windows 10 Enterprise, Windows 10 Education und Windows 10 Mobile Enterprise

 

In Windows 10, Version 1607 hinzugefügt. Verzögert Qualität Updates für die angegebene Anzahl von Tagen an.

Unterstützte Werte sind 0 bis 30.

<a href="" id="update-deferupdateperiod"></a>**Update/DeferUpdatePeriod**  
> **Hinweis**  
Diese Richtlinie steht auf Windows 10 Pro Windows 10 Enterprise, Windows 10 Education und Windows 10 Mobile Enterprise

Verwenden Sie nicht diese Richtlinie in Windows 10, Version 1607 Geräte, stattdessen die neuen Richtlinien in [Windows-10, Version 1607 für aktualisieren Management](#windows-10-version-1607-for-update-management)aufgeführt. Sie können weiterhin DeferUpdatePeriod für Windows 10, Version 1511-Geräte verwenden.

 

Ermöglicht es IT-Administratoren Update Verzögerungen für bis zu vier Wochen angeben.

Unterstützte Werte sind 0-4 ist, bezieht sich auf die Anzahl der Wochen Updates zu verzögern.

In Windows 10 Mobile Enterprise-Version 1511 Geräte legen Sie auf automatische Updates, für DeferUpdatePeriod arbeiten müssen Sie Folgendes festlegen:

-   Update/RequireDeferUpgrade muss auf 1 festgelegt werden
-   System/AllowTelemetry muss mindestens auf 1 festgelegt werden

Wenn die Richtlinie "Specify Intranet Microsoft Update Service Location" aktiviert ist, haben Sie dann die "Defer Upgrades durch" sowie "Defer Aktualisierungen durch" und "Anhalten Updates und Upgrades" Einstellungen keine Auswirkung.

Wenn die Richtlinie Telemetrie zulassen aktiviert ist und der Optionen-Wert auf 0 festgelegt ist, haben Sie dann die "Defer Upgrades durch" sowie "Defer Aktualisierungen durch" und "Anhalten Updates und Upgrades" Einstellungen keine Auswirkung.

<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<thead>
<tr class="header">
<th>Aktualisieren der Kategorie</th>
<th>Maximale Verzögerungen</th>
<th>Rückstellung Schrittweite</th>
<th>Geben Sie/Update Hinweise</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="vertical-align:top"><p>Betriebssystem aktualisieren</p></td>
<td style="vertical-align:top"><p>8 Monaten</p></td>
<td style="vertical-align:top"><p>1 Monat</p></td>
<td style="vertical-align:top"><p>Upgrade – 3689BDC8-B205-4AF4-8D4A-A63924C5E9D5</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top"><p>Update</p></td>
<td style="vertical-align:top"><p>1 Monat</p></td>
<td style="vertical-align:top"><p>1 Woche</p></td>
<td style="vertical-align:top"><div class="alert">
<strong>Hinweis</strong>  Wenn ein Computer Microsoft Update aktiviert ist, alle Microsoft-Updates in den folgenden Kategorien auch Defer beobachten / Pause Logik.
</div>
<div>
 
</div>
<ul>
<li>Sicherheitsupdate - 0FA1201D-4330-4FA8-8AE9-B877473B6441</li>
<li>Wichtige Update - E6CF1350-C01B-414D-A61F-263D14D133B4</li>
<li>Updaterollup - 28BC880E-0592-4CBF-8F95-C79B17911D5F</li>
<li>Service Pack - 68C5B0A3-D1A6-4553-AE49-01D3A7827828</li>
<li>Tools - B4832BD8-E735-4761-8DAF-37F882276DAB</li>
<li>Feature Pack - B54E7D24-7ADD-428F-8B75-90A396FA584F</li>
<li>Update - CD5FFD1E-E932-4E3A-BF74-18BF0B1BBD83</li>
<li>Treiber - EBFC1FC5-71A4-4F7B-9ACA-3B9A503104A0</li>
</ul></td>
</tr>
<tr class="odd">
<td style="vertical-align:top"><p>Andere / verzögern kann nicht</p></td>
<td style="vertical-align:top"><p>Keine Rückstellung</p></td>
<td style="vertical-align:top"><p>Keine Rückstellung</p></td>
<td style="vertical-align:top"><p>Jede Update-Kategorie, die nicht explizit über fällt in dieser Kategorie aufgelistet.</p>
<p>Definition Update - E0789628-CE08-4437-BE74-2495B842F43B</p></td>
</tr>
</tbody>
</table>

 

<a href="" id="update-deferupgradeperiod"></a>**Update/DeferUpgradePeriod**   
> **Hinweis**  
Diese Richtlinie ist auf Windows 10 Pro, Windows 10 Enterprise, Windows 10 Education verfügbar.

Da diese Richtlinie nicht gesperrt ist, erhalten Sie bei Verwendung einer Windows 10 Mobile-Gerät konfigurieren keine Fehlermeldung angezeigt. Die Richtlinie wird jedoch nicht wirksam wird.

Verwenden Sie nicht diese Richtlinie in Windows 10, Version 1607 Geräte, stattdessen die neuen Richtlinien in [Windows-10, Version 1607 für aktualisieren Management](#windows-10-version-1607-for-update-management)aufgeführt. Sie können weiterhin DeferUpgradePeriod für Windows 10, Version 1511 Geräte verwenden.

 

IT-Administratoren, zusätzliche Upgrade Verzögerungen für bis zu acht Monaten angeben können.

Unterstützte Werte sind 0 bis 8, bezieht sich auf die Anzahl der Monate Upgrades zu verzögern.

Wenn die Richtlinie "Specify Intranet Microsoft Update Service Location" aktiviert ist, haben Sie dann die "Defer Upgrades durch" sowie "Defer Aktualisierungen durch" und "Anhalten Updates und Upgrades" Einstellungen keine Auswirkung.

Wenn die Richtlinie "Telemetrie zulassen" aktiviert ist, und der Optionen-Wert auf 0 festgelegt ist, haben Sie dann die "Defer Upgrades durch", "Defer Aktualisierungen durch" und "Pause Updates und Upgrades" Einstellungen keine Auswirkung.

<a href="" id="update-excludewudrivers"></a>**Update/ExcludeWUDrivers**  
> **Hinweis**  Diese Richtlinie ist auf Windows 10 Pro, Windows 10 Enterprise, Windows 10 Education verfügbar.
Da diese Richtlinie nicht gesperrt ist, erhalten Sie bei Verwendung einer Windows 10 Mobile-Gerät konfigurieren keine Fehlermeldung angezeigt. Die Richtlinie wird jedoch nicht wirksam wird.

 

In Windows 10, Version 1607 hinzugefügt. IT-Administratoren Windows Update (WU) Treiber während der Aktualisierung ausschließen können.

In der folgenden Liste sind die unterstützten Werte:

-   0 (Standard) – zulassen Windows Update-Treiber.
-   1 – Windows Update-Treiber ausschließen.

<a href="" id="update-pausedeferrals"></a>**Update/PauseDeferrals**  
> **Hinweis**  
Diese Richtlinie steht auf Windows 10 Pro Windows 10 Enterprise, Windows 10 Education und Windows 10 Mobile Enterprise

Verwenden Sie nicht diese Richtlinie in Windows 10, Version 1607 Geräte, stattdessen die neuen Richtlinien in [Windows-10, Version 1607 für aktualisieren Management](#windows-10-version-1607-for-update-management)aufgeführt. Sie können weiterhin PauseDeferrals für Windows 10, Version 1511-Geräte verwenden.

 

Ermöglicht es IT-Administratoren, Updates und Upgrades für bis zu fünf Wochen anzuhalten. Angehaltene Rückstellungen werden nach fünf Wochen zurückgesetzt.

In der folgenden Liste sind die unterstützten Werte:

-   0 (Standard) – Rückstellungen nicht angehalten werden.
-   1 – Rückstellungen werden angehalten.

Wenn die Richtlinie "Specify Intranet Microsoft Update Service Location" aktiviert ist, haben Sie dann die "Defer Upgrades durch" sowie "Defer Aktualisierungen durch" und "Anhalten Updates und Upgrades" Einstellungen keine Auswirkung.

Wenn die Richtlinie "Telemetrie zulassen" aktiviert ist, und der Optionen-Wert auf 0 festgelegt ist, haben Sie dann die "Defer Upgrades durch", "Defer Aktualisierungen durch" und "Pause Updates und Upgrades" Einstellungen keine Auswirkung.

<a href="" id="update-pausefeatureupdates"></a>**Update/PauseFeatureUpdates**  
> **Hinweis**  Diese Richtlinie ist auf Windows 10 Pro, Windows 10 Enterprise, Windows 10 Education verfügbar.
Da diese Richtlinie nicht gesperrt ist, erhalten Sie bei Verwendung einer Windows 10 Mobile-Gerät konfigurieren keine Fehlermeldung angezeigt. Die Richtlinie wird jedoch nicht wirksam wird.

 

In Windows 10, Version 1607 hinzugefügt. Ermöglicht es IT-Administratoren Feature Updates für bis zu 60 Tage Anhalten aus.

In der folgenden Liste sind die unterstützten Werte:

-   0 (Standard) – Feature Updates werden nicht angehalten.
-   1 – Feature Updates werden angehalten, 60 Tage oder bis Wert auf 0 festlegen, je nachdem, was stattfindet.

<a href="" id="update-pausequalityupdates"></a>**Update/PauseQualityUpdates**  
> **Hinweis**  Diese Richtlinie steht auf Windows 10 Pro Windows 10 Enterprise, Windows 10 Education und Windows 10 Mobile Enterprise

 

In Windows 10, Version 1607 hinzugefügt. Ermöglicht es IT-Administratoren Qualität Updates zu unterbrechen.

In der folgenden Liste sind die unterstützten Werte:

-   0 (Standard) – Qualität Updates nicht angehalten werden.
-   1 – Qualität Updates werden angehalten 35 Tage oder bis Wert wieder auf 0 festlegen, je nachdem, welche stattfindet.

<a href="" id="update-requiredeferupgrade"></a>**Update/RequireDeferUpgrade**  
> **Hinweis**  
Diese Richtlinie steht auf Windows 10 Pro Windows 10 Enterprise, Windows 10 Education und Windows 10 Mobile Enterprise

Verwenden Sie nicht diese Richtlinie in Windows 10, Version 1607 Geräte, stattdessen die neuen Richtlinien in [Windows-10, Version 1607 für aktualisieren Management](#windows-10-version-1607-for-update-management)aufgeführt. Sie können weiterhin RequireDeferUpgrade für Windows 10, Version 1511-Geräte verwenden.

 

Ermöglicht der IT-Administrator, um ein Gerät auf CBB Zug festzulegen.

In der folgenden Liste sind die unterstützten Werte:

-   0 (Standard) – Ruft Benutzer aus der aktuellen Zweig Upgrades ab.
-   1 – Benutzer ruft Upgrades aus der aktuellen Zweig for Business ab.

<a href="" id="update-requireupdateapproval"></a>**Update/RequireUpdateApproval**  

> **Hinweis**  Diese Richtlinie steht auf Windows 10 Pro Windows 10 Enterprise, Windows 10 Education und Windows 10 Mobile Enterprise

<br>
> **Hinweis**  Wenn Sie zuvor die Richtlinie **Update/PhoneUpdateRestrictions** in früheren Versionen von Windows verwendet, ist es veraltet. Verwenden Sie stattdessen diese Richtlinie.

 

Ermöglicht der IT-Administrator, um die Updates zu beschränken, die auf einem Gerät, um nur die auf einer Updateliste Genehmigung installiert sind. Es ermöglicht der IT, akzeptieren den Endbenutzer-Lizenzvertrag (EULA) zugeordnet des genehmigten Updates im Namen der Endbenutzer. EULAs zugelassen werden, nachdem ein Update genehmigt wird.

Unterstützte Vorgänge sind Get und ersetzen.

In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht konfiguriert. Vom Gerät installiert alle anwendbaren Aktualisierungen.
-   1 – vom Gerät installiert nur die Updates, die entsprechenden und in der Liste der genehmigten Updates sind. Legen Sie diese Richtlinie auf 1, wenn IT möchte steuern die Bereitstellung von Updates auf Geräten, beispielsweise wenn die Tests vor der Bereitstellung erforderlich ist.

<a href="" id="update-scheduledinstallday"></a>**Update/ScheduledInstallDay**  
> **Hinweis**  Diese Richtlinie steht auf Windows 10 Pro Windows 10 Enterprise, Windows 10 Education und Windows 10 Mobile Enterprise

 

Ermöglicht der IT-Administrator den Tag der Installation des Updates zu planen.

Der Datentyp ist eine Zeichenfolge.

Unterstützte Vorgänge sind Get hinzufügen, löschen, und Ersetzen Sie.

In der folgenden Liste sind die unterstützten Werte:

-   0 (Standard) – täglich
-   1 – Sonntag
-   2 – Montag
-   3 – Dienstag
-   4 – Mittwoch
-   5 – Donnerstag
-   6 – Freitag
-   7 – Samstag

<a href="" id="update-scheduledinstalltime"></a>**Update/ScheduledInstallTime**  
> **Hinweis**  Diese Richtlinie steht auf Windows 10 Pro Windows 10 Enterprise, Windows 10 Education und Windows 10 Mobile Enterprise

 

Ermöglicht der IT-Administrator, um den Zeitplan für die Installation des Updates.

Der Datentyp ist eine Zeichenfolge.

Unterstützte Vorgänge sind Get hinzufügen, löschen, und Ersetzen Sie.

Unterstützte Werte sind 0 – 23, wobei 0 = 12 Uhr und 23 = 11 Uhr.

Der Standardwert ist 3.

<a href="" id="update-updateserviceurl"></a>**Update/UpdateServiceUrl**  
> **Hinweis**  Diese Richtlinie steht auf Windows 10 Pro Windows 10 Enterprise, Windows 10 Education und Windows 10 Mobile Enterprise

 

Ermöglicht das Gerät an einen WSUS-Server und Microsoft Update nicht auf Updates überprüfen. Dies ist nützlich, MDMs am Standort, die zur Aktualisierung von Geräten, die keine Verbindung zum Internet herstellen können.

Unterstützte Vorgänge sind Get und ersetzen.

In der folgenden Liste sind die unterstützten Werte:

-   Nicht konfiguriert. Das Gerät sucht nach Updates von Microsoft Update.
-   Legen Sie auf eine URL wie `http://abcd-srv:8530`. Das Gerät sucht nach Updates vom WSUS-Server an der angegebenen URL.

Beispiel

``` syntax
        <Replace>
            <CmdID>$CmdID$</CmdID>
            <Item>
                <Meta>
                    <Format>chr</Format>
                    <Type>text/plain</Type>
                </Meta>
                <Target>
                    <LocURI>./Vendor/MSFT/Policy/Config/Update/UpdateServiceUrl</LocURI>
                </Target>
                <Data>http://abcd-srv:8530</Data>
            </Item>
        </Replace>
```

### <a name="update-management"></a>Verwaltung von

Die Enterprise IT konfigurieren den Satz von genehmigten Updates und Abrufen des Status über OMA DM, die mit dem [Update CSP](update-csp.md)Compliance können. Das folgende Diagramm zeigt die Update-CSP Struktur-Format.

![Csp Diagramm aktualisieren](images/provisioning-csp-update.png)

<a href="" id="update"></a>**Update**  
Den Stammknoten.

Unterstützte Vorgang ist Get.

<a href="" id="approvedupdates"></a>**ApprovedUpdates**  
Knoten für die Aktualisierung Genehmigungen und EULA Annahme im Namen der Endbenutzer.

> **Hinweis** Wenn die Richtlinie RequireUpdateApproval festgelegt ist, verwendet die MDM ApprovedUpdates List, um die genehmigte GUIDs zu übergeben. Diese GUIDs sollte eine Teilmenge der Liste InstallableUpdates sein.

Die MDM muss zuerst den Endbenutzer-LIZENZVERTRAG zu präsentieren IT und lassen sie ihn akzeptieren, bevor das Update genehmigt wurde. Wenn dies nicht der Fall ist eine Verletzung der rechtlichen oder vertragliche Verpflichtungen. Der Endbenutzer-Lizenzverträge aus der Update-Metadaten abgerufen werden können und haben einen eigenen EULA-ID. Es ist möglich, mehrere Updates für den gleichen EULA gemeinsam nutzen. Es ist nur erforderlich, um den Endbenutzer-LIZENZVERTRAG einmal pro EULA-ID nicht eine pro Update zu genehmigen.

Das Update Genehmigung Liste ermöglicht der IT zu genehmigen einzelne Updates Klassifikationen aktualisieren. Automatische Genehmigung durch die Update-Klassifikationen ermöglicht es IT-Definition (d. h., Updates, die Definitionen von Viren und Spyware auf Geräten) und Sicherheitsupdates (d. h., produktspezifische Updates für sicherheitsbezogene Anfälligkeit) automatisch genehmigen. Die Genehmigung Updateliste unterstützt nicht die Deinstallation des Updates durch Aufheben der Genehmigung der bereits installierten Updates. Updates werden basierend auf UpdateID genehmigt, und ein UpdateID muss nur einmal genehmigt werden. Ein Update UpdateID und RevisionNumber sind Teil der UpdateIdentity-Typ. Ein UpdateID kann mehrere UpdateIdentity GUIDs aufgrund von Änderungen an der Einstellung RevisionNumber zugeordnet werden. MDM Services müssen von einer UpdateID basierend auf den neuesten RevisionNumber zum Abrufen des neuesten Metadaten für ein Update der UpdateIdentity synchronisieren. Allerdings Genehmigung von vorgangsaktualisierungen UpdateID basiert.

> **Hinweis**  Für den Build Windows 10 möglicherweise der Client neu starten, nachdem Weitere Updates hinzugefügt werden müssen.

 

Unterstützte Vorgänge sind Get und hinzufügen.

<a href="" id="approvedupdates-approved-update-guid"></a>**ApprovedUpdates / ***_genehmigt Update-Guid_**  
Gibt an, das Update-GUID.

Um eine Klasse von Updates automatisch genehmigen können Sie das [Update Klassifikationen](http://go.microsoft.com/fwlink/p/?LinkId=526723) GUIDs festlegen. Es wird dringend empfohlen die DefinitionsUpdates Klassifizierung (E0789628-CE08-4437-BE74-2495B842F43B), an die für Antischadsoftware-Signaturen verwendet werden. Gibt es in regelmäßigen Abständen veröffentlicht werden (mehrmals täglich). Einige Unternehmen möchten möglicherweise auch automatisch genehmigen von Sicherheits-Updates, damit sie schnell bereitgestellt angezeigt.

Unterstützte Vorgänge sind Get und hinzufügen.

Beispiel Syncml:

```
<LocURI>./Vendor/MSFT/Update/ApprovedUpdates/%7ba317dafe-baf4-453f-b232-a7075efae36e%7d</LocURI>
```

<a href="" id="approvedupdates-approved-update-guid-approvedtime"></a>* *ApprovedUpdates /*genehmigt Update Guid*/ApprovedTime**  
Gibt die Zeitspanne, die das Update genehmigt wird.

Unterstützte Vorgänge sind Get und hinzufügen.

<a href="" id="failedupdates"></a>**FailedUpdates**  
Gibt an, die genehmigten Updates, die nicht auf einem Gerät installieren.

Unterstützte Vorgang ist Get.

<a href="" id="failedupdates-failed-update-guid"></a>**FailedUpdates / ***_Fehler beim Update Guid_**  
Aktualisieren Sie Bezeichner der UpdateIdentity-GUID, die ein Update darstellen, die Fehler beim Herunterladen oder installieren.

Unterstützte Vorgang ist Get.

<a href="" id="failedupdates-failed-update-guid-hresult"></a>* *FailedUpdates /*Fehler beim Update Guid*/HResult**  
Die Aktualisierung schlug fehl.

Unterstützte Vorgang ist Get.

<a href="" id="failedupdates-failed-update-guid-status"></a>* *FailedUpdates /*Fehler beim Update Guid*/Status**  
Gibt den Status Updatefehlern (beispielsweise herunterladen, installieren).

Unterstützte Vorgang ist Get.

<a href="" id="installedupdates"></a>**InstalledUpdates**  
Die Updates, die auf dem Gerät installiert werden.

Unterstützte Vorgang ist Get.

<a href="" id="installedupdates-installed-update-guid"></a>**InstalledUpdates / ***_Guid Update installiert_**  
UpdateIDs, die die Updates installiert sind, auf einem Gerät darstellen.

Unterstützte Vorgang ist Get.

<a href="" id="installableupdates"></a>**InstallableUpdates**  
Die Updates, die entsprechenden und noch nicht auf dem Gerät installiert sind. Dazu gehören Updates, die noch nicht genehmigt werden.

Unterstützte Vorgang ist Get.

<a href="" id="installableupdates-installable-update-guid"></a>**InstallableUpdates / ***_installierbares Update-Guid_**  
Update-IDs, die die Updates anwendbar und nicht auf einem Gerät installierten darstellen.

Unterstützte Vorgang ist Get.

<a href="" id="installableupdates-installable-update-guid-type"></a>* *InstallableUpdates /*installierbares Update Guid*/Type**  
Der Wert der UpdateClassification des Updates. Gültige Werte sind:

-   0 – keine
-   1 – Sicherheit
-   2 = kritisch

Unterstützte Vorgang ist Get.

<a href="" id="installableupdates-installable-update-guid-revisionnumber"></a>* *InstallableUpdates /*installierbares Update Guid*/RevisionNumber**  
Die Revisionsnummer für die Aktualisierung, die Server-zu-Server-Synchronisierung zum Abrufen der Metadaten für das Update übergeben werden muss.

Unterstützte Vorgang ist Get.

<a href="" id="pendingrebootupdates"></a>**PendingRebootUpdates**  
Die Updates, die für die Durchführung die Update-Sitzung ein Neustart erforderlich.

Unterstützte Vorgang ist Get.

<a href="" id="pendingrebootupdates-pending-reboot-update-guid"></a>**PendingRebootUpdates / ***_Ausstehender Neustart Update Guid_**  
Bezeichner für den Neustartstatus ausstehender zu aktualisieren.

Unterstützte Vorgang ist Get.

<a href="" id="pendingrebootupdates-pending-reboot-update-guid-installedtime"></a>* *PendingRebootUpdates /*Ausstehender Neustart Update Guid*/InstalledTime**  
Die Zeit, die das Update installiert ist.

Unterstützte Vorgang ist Get.

<a href="" id="lastsuccessfulscantime"></a>**LastSuccessfulScanTime**  
Die letzte erfolgreiche Scan-Zeit.

Unterstützte Vorgang ist Get.

<a href="" id="deferupgrade"></a>**DeferUpgrade**  
Upgrades verzögert, bis die nächste Periode.

Unterstützte Vorgang ist Get.


## <a name="a-href-idwindows10version1607forupdatemanagementa-windows-10-version-1607-for-update-management"></a><a href="" id="windows10version1607forupdatemanagement"></a>Windows-10, Version 1607 für die Verwaltung

Hier sind die neuen Richtlinien in Windows 10, Version 1607 im [Bereich CSP Richtlinie](policy-configuration-service-provider.md)hinzugefügt. Sie sollten diese Richtlinien für die neue Windows 10, Version 1607-Geräte verwenden.

-   Update/ActiveHoursEnd
-   Update/ActiveHoursStart
-   Update/AllowMUUpdateService
-   Update/BranchReadinessLevel
-   Update/DeferFeatureUpdatePeriodInDays
-   Update/DeferQualityUpdatePeriodInDays
-   Update/ExcludeWUDriversInQualityUpdate
-   Update/PauseFeatureUpdates
-   Update/PauseQualityUpdates

Hier wird die Liste der entsprechenden Group Policy Settings in HKLM\\Software\\Richtlinien\\Microsoft\\Windows\\Windows Update.

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>GPO-Taste</th>
<th>Type</th>
<th>Wert</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="vertical-align:top"><p>BranchReadinessLevel</p></td>
<td style="vertical-align:top"><p>REG_DWORD</p></td>
<td style="vertical-align:top"><p>16: Systemen dauert Feature Updates auf der aktuellen Verzweigung (CB) Zug</p>
<p>32: Systemen dauert Feature Updates auf den aktuellen Zweig für Unternehmen</p>
<p>Andere Wert oder nicht vorhanden: erhalten alle anwendbaren Aktualisierungen (CB)</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top"><p>DeferQualityUpdates</p></td>
<td style="vertical-align:top"><p>REG_DWORD</p></td>
<td style="vertical-align:top"><p>1: aufschieben Qualität Updates</p>
<p>Andere Wert oder nicht vorhanden: Qualität Updates nicht verzögern</p></td>
</tr>
<tr class="odd">
<td style="vertical-align:top"><p>DeferQualityUpdatesPeriodInDays</p></td>
<td style="vertical-align:top"><p>REG_DWORD</p></td>
<td style="vertical-align:top"><p>0-30: Tagen an, die Qualität Updates zurückstellen</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top"><p>PauseQualityUpdates</p></td>
<td style="vertical-align:top"><p>REG_DWORD</p></td>
<td style="vertical-align:top"><p>1: unterbrechen Qualität Updates</p>
<p>Andere Wert oder nicht vorhanden: Qualität Updates nicht anhalten</p></td>
</tr>
<tr class="odd">
<td style="vertical-align:top"><p>DeferFeatureUpdates</p></td>
<td style="vertical-align:top"><p>REG_DWORD</p></td>
<td style="vertical-align:top"><p>1: zurückstellen Feature-Updates</p>
<p>Anderen Wert oder nicht vorhanden: nicht verzögern Feature-Updates</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top"><p>DeferFeatureUpdatesPeriodInDays</p></td>
<td style="vertical-align:top"><p>REG_DWORD</p></td>
<td style="vertical-align:top"><p>0-180: Tage zu verzögern Feature-Updates</p></td>
</tr>
<tr class="odd">
<td style="vertical-align:top"><p>PauseFeatureUpdates</p></td>
<td style="vertical-align:top"><p>REG_DWORD</p></td>
<td style="vertical-align:top"><p>1: Unterbrechen der Feature-Updates</p>
<p>Andere Wert oder nicht vorhanden: Feature Updates nicht anhalten</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top"><p>ExcludeWUDriversInQualityUpdate</p></td>
<td style="vertical-align:top"><p>REG_DWORD</p></td>
<td style="vertical-align:top"><p>1: Ausschließen WU-Treiber</p>
<p>Andere Wert oder nicht vorhanden: bieten WU-Treiber</p></td>
</tr>
</tbody>
</table>

 

Hier wird die Liste der älteren Richtlinien, die noch für die Abwärtskompatibilität unterstützt werden. Sie können diese für Windows 10, Version 1511 Geräte verwenden.

-   Update/RequireDeferUpgrade
-   Update/DeferUpgradePeriod
-   Update/DeferUpdatePeriod
-   Update/PauseDeferrals

Für Windows Update für Unternehmen sieht die Liste der unterstützten Richtlinien auf Windows 10 Mobile Enterprise aus:

-   Für Windows 10, Version 1511 (Build 10586): Update RequireDeferUpgrade/Update/DeferUpdatePeriod und Update/PauseDeferrals. Sie DeferUpdatePeriod und PauseDeferrals der RequireDeferUpgrade ist auf 1 festgelegt werden soll, im Wesentlichen für ein Gerät, auf dem 1511, die Windows-Updates für Geschäftsrichtlinien bedeutet, kann nur festlegen, wenn ein Gerät für CBB konfiguriert ist stattfinden.
-   Für Windows 10, Version 1607 (Build 14393): Update/BranchReadinessLevel, Update/DeferQualityUpdatesPeriodInDays und/PauseQualityUpdates Update. In 1607 hinzugefügt wir Support, in dem Sie können Windows Update für Geschäftsrichtlinien beim Konfigurieren ein Geräts für CB/CBB konfiguriert ist – Wartung.

> **Hinweis**  
Richtlinien für Windows Update für Unternehmen, die beim Festlegen von Richtlinien für beide Windows 10, Version 1607 und Windows 10, Version, dass 1511 Ausführung auf 1607, und klicken Sie dann 1607 Richtlinien werden (1607 sammeln 1511) konfiguriert unterstützt.

Für Richtlinien unterstützt Windows Update für Unternehmen Wenn Sie auf einem Gerät unter 1607 1511 Richtlinien festlegen, die Sie erhalten das erwartete Verhalten für 1511 Richtlinien.

 

## <a name="a-href-iduserexperiencescreenshotaupdate-management-user-experience-screenshot"></a><a href="" id="userexperiencescreenshot"></a>Aktualisieren von Management User Experience screenshot

Die folgenden Screenshots der Administratorkonsole zeigt die Liste der Updatetitel, Genehmigungsstatus und zusätzliche Metadaten-Felder.

![MDM Update Management-screenshot](images/deviceupdatescreenshot1.png)

![MDM Update Management Metadaten-screenshot](images/deviceupdatescreenshot2.png)


## <a name="a-href-idsyncmlexampleasyncml-example"></a><a href="" id="syncmlexample"></a>SyncML-Beispiel

Legen Sie AutoUpdate zu benachrichtigen und verzögern.

``` syntax
<SyncML xmlns="SYNCML:SYNCML1.1">
    <SyncBody>
        <Replace xmlns="">
            <CmdID>1</CmdID>
            <Item>
                <Meta>
                    <Format>int</Format>
                    <Type>text/plain</Type>
                </Meta>
                <Target>
                    <LocURI>./Vendor/MSFT/Policy/Config/Update/AllowUpdateService</LocURI>
                </Target>
                <Data>0</Data>
            </Item>
            <CmdID>2</CmdID>
            <Item>
                <Meta>
                    <Format>int</Format>
                    <Type>text/plain</Type>
                </Meta>
                <Target>
                    <LocURI>./Vendor/MSFT/Policy/Config/Update/RequireDeferUpgrade </LocURI>
                </Target>
                <Data>0</Data>
            </Item>
            <CmdID>3</CmdID>
            <Item>
                <Meta>
                    <Format>int</Format>
                    <Type>text/plain</Type>
                </Meta>
                <Target>
                    <LocURI>./Vendor/MSFT/Policy/Config/Update/RequireUpdateApproval </LocURI>
               </Target>
                <Data>0</Data>
            </Item>
        </Replace>
       <Final/>
    </SyncBody>
</SyncML>
```

## <a name="process-flow-diagram-and-screenshots-of-server-sync-process"></a>Prozessflussdiagramm und Screenshots des Servers Prozess synchronisieren

Die folgenden Diagramm und Screenshots anzeigen Ablauf der Geräteupdates mithilfe von Windows Server Update Services und Microsoft Update-Katalog

![MDM Device Update Management-screenshot](images/deviceupdatescreenshot3.png)![MDM Device Update Management-screenshot](images/deviceupdatescreenshot4.png)![MDM Device Update Management-screenshot](images/deviceupdatescreenshot5.png)![MDM Device Update Management-screenshot](images/deviceupdatescreenshot6.png)![MDM Device Update Management-screenshot](images/deviceupdatescreenshot7.png)![MDM Device Update Management-screenshot](images/deviceupdatescreenshot8.png)![MDM Device Update Management-screenshot](images/deviceupdatescreenshot9.png)

 






