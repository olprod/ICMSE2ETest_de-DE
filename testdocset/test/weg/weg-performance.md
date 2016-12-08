
# <a name="performance-windows-10-engineering-guide"></a>Leistung – Windows 10 Engineering Guide

Microsoft Corporation

August 2015

### <a name="abstract"></a>Abstrakte

Die Leistung Windows Engineering Guidance (WEG) bietet einen Überblick zur Bereitstellung von leistungsstarke und effiziente Power PCs für Kunden-Partnern. In diesem Dokument identifiziert Verkaufschancen messen, analysieren und Verbessern der Leistung in wichtige Bereiche, einschließlich Akkulaufzeit, Erfahrung navigieren und das streaming von Medien. OEM ODM und IHV Partner können außerdem Anleitungen finden Sie im dieses WEG zum Entwickeln und Auswählen von Windows Store-apps, die auf Ihrem System und Links zu verwandter Dokumentation effizient ausgeführt.

Version: 1.1

### <a name="copyright-information"></a>Copyright-Informationen

In diesem Dokument wird bereitgestellt "als-ist". In diesem Dokument, einschließlich URLS und anderer Verweise auf Internetwebsites, enthaltenen Informationen und Sichten können ohne vorherige Ankündigung geändert werden.

Einige Beispiele für die in diesen Beispielen werden lediglich zur Veranschaulichung bereitgestellt und sind frei erfunden. Ähnlichkeit oder Verbindung ist rein zufällig.

In diesem Dokument wird nicht Ihnen keinerlei Rechte an geistigem Eigentum in einem Microsoft-Produkt bereitstellen. Sie können kopieren und verwenden Sie dieses Dokument zur internen Referenz vervielfältigen. Sie können dieses Dokument ändern, zur internen Referenz vervielfältigen. Dieses Dokument ist vertraulich und proprietäre an Microsoft. Es ist anzugeben, und gemäß einer vertraulichkeitsvereinbarung verwendet werden kann.

© Microsoft 2016. Alle Rechte vorbehalten.

### <a name="trademark-information"></a>Informationen zu Marken

Microsoft und Windows sind Marken der Microsoft-Unternehmensgruppe. Eine vollständige Liste der Microsoft-Marken finden Sie in der [Liste der Microsoft-Marken](http://go.microsoft.com/fwlink/?LinkID=287088) (http://www.microsoft.com/en-us/legal/intellectualproperty/Trademarks/EN-US.aspx) online. Alle anderen Marken sind Eigentum ihrer jeweiligen Inhaber.



# <a name="introduction"></a>Einführung

Wie Sie auf die nächste Generation der Technologie, weiterhin Kunden leistungsstarke und effiziente Power PCs auf Sie zukommt. Kunden fordern, dass heutigen PCs vom Umfang der modernen Web zu ermöglichen, Akkulaufzeit und einem unterschiedlichen Portfolio leistungsstarke Software bereitstellen. Weitere Kunden erwarten, dass neue Geräte bereitstellen, die immer auf und immer verbundenen Erfahrung mit Mobiltelefonen und, denen nur in einem PC verbunden Standby aktiviert werden kann.

Die Leistung Windows Engineering Guide (WEG) enthält Anleitungen zum eine hervorragende Windows auf einem PC leistungsstarke Erlebnis. In diesem Dokument identifiziert Verkaufschancen messen, analysieren und Verbessern der Leistung in wichtige Bereiche, einschließlich Akkulaufzeit, Web durchsuchen, und das streaming von Medien. OEM ODM und IHV Partner können außerdem Anleitungen finden Sie im dieses WEG zum Entwickeln und Auswählen von Windows Store-apps, die auf die Systeme effizient ausgeführt.

Dieses Dokument enthält die Tools und Leitfäden zur vollständigen Stellen verwenden der Windows-Features für mechanische, Hardware, Firmware, Software und Fertigung Ingenieure und ist nicht Adresse Geschäfts- und marketing-Benutzergruppen. Die Themen umfassen das Optimieren der Leistung während der folgenden bewährten Methoden von Fertigung und beim Entwickeln und Bereitstellen von Treibern, apps, Firmware und Hardware. Diese Anleitung gilt für traditionelle X86-basierte PCs als auch für Geräte, die verbundenen Standby anbieten. Dies gilt für Consumer und kommerziellen Märkten.

![Wichtige](images/note-important.gif)**wichtige**&nbsp;&nbsp;&nbsp;WEG von der Leistung sollte nicht die Windows-Kompatibilität Hardwareanforderungen und OEM-Richtlinie Dokument (OPD) kommunizieren. WHCR und OPD haben Vorrang auf Informationen in der Leistung WEG. Sie müssen die WHCR und OPD entsprechen.

## <a name="document-updates"></a>Dokument-updates

| Datum der Aktualisierung | Beschreibung |
|--------------|------------------------------------------|
| April 2015   | Erste Version von Version 1.0 für Windows 10 |
| April 2015   | Hinzugefügte Version 1.1 Url-Text für links |


# <a name="delivering-a-great-experience-with-low-memory"></a>Spielt eine großartige Erfahrung mit wenig Arbeitsspeicher

Die Menge des Arbeitsspeichers zur Verfügung haben eine bedeutende Auswirkung auf gesamten Benutzeroberfläche von allgemeinen Reaktionsfähigkeit des Systems, Reaktionsfähigkeit beim Wechsel zwischen apps für Windows Store-Stil und Akkulaufzeit bis hin. Dies sind alle sehr wichtige zu berücksichtigende Faktoren beim Auswerten der allgemeinen Erfahrung mit wenig Arbeitsspeicher.
(Nicht genügend Arbeitsspeicher ist 1 GB RAM auf 32-Bit-Windows und 2 GB RAM auf 64-Bit-Windows).

## <a name="considerations"></a>Erwägungen

Es gibt mehrere Aufgaben, die ein OEM, IHV und ISV berücksichtigen, wenn eine Speichermangel Zielgerät müssen aus.

### <a name="drivers-and-apps"></a>Treiber und apps

#### <a name="overall-baseline-memory-footprint"></a>Allgemeine Baseline Speicherbedarf

Typische Baseline Retail 32-Bit-Windows-Abbild beansprucht ungefähr 400 MB im Hinblick auf den verwendeten Speicher nach dem Starten (wie gemessen, verwenden die Bewertung Speicherbedarf in ADK).
Zulassen, dass für Reserve 10 % oder 100 MB auf 1 GB, verlässt dies Speicher für 2-3-apps werden im physischen Speicher, fast Umschalten zwischen der apps aktivieren. Je größer der Basisbetriebssystems Arbeitsspeicherbedarf; der kleinere der Arbeitsspeicher, um den Benutzer und apps.

Wichtige Faktoren, die geplante OS Speicherbedarf auswirkt sind Treiber und vorinstallierte Software, einschließlich Modul apps, Gerät desktop-apps und Updater Software, um ein paar zu nennen.

-   **Treiber Bilanz:** Dazu gehören Treibercode und zugehörige Zuweisungen. Nicht navigierbaren Speicher (oder Inhalt, die im physischen Speicher vorhanden sein müssen und können nicht ausgelagert) ist äußerst wichtig, wie sie eine feste Kosten im Hinblick auf arbeitsspeichernutzung während der Lebensdauer des Systems beinhaltet, wie die meisten Treiber jederzeit im Arbeitsspeicher vorhanden sind. Aktuelle hardwareanforderungen Zertifizierung abdecken-navigierbaren Zuweisungen - MDL/benachbart Arbeitsspeicher Zuweisungen Treibercode nicht ausgelagerten und nicht ausgelagerten Pools für einzelne pro Treiber.

    [Device.DevFund.Memory.DriverFootprint](http://msdn.microsoft.com/en-us/library/windows/hardware/jj124553.aspx)


-   **Hardware Arbeitsspeicher Reservierung:** Dazu gehören Arbeitsspeicher "machen Sie-Outs," vermindert die Speichermenge OS sichtbar, die für Windows verfügbar ist und im Kontext von Speichermangel Geräte äußerst wichtig ist. Aktuelle hardwareanforderungen Zertifizierung bieten Budgets für verschiedene RAM-Konfigurationen:

    [System.Fundamentals.Firmware.HardwareMemoryReservation](http://msdn.microsoft.com/en-us/library/windows/hardware/jj128256.aspx)


-   **Vorinstallierte Software und Malware apps:** Dazu gehören Services/zusätzliche Prozesse, die während des Startvorgangs starten und aktiv sein, während der Lebensdauer einer Sitzung. Der Satz von vorinstallierte Software, die Prozesse beim Start führt sorgfältig berücksichtigt und Budget werden müssen.

Aus der Sicht OS mehrere Verbesserungen wurden zur Reduzierung der Laufzeitfehler Speicherbedarf unter Windows, um mehr Speicher für Benutzer und ihre apps verfügbar zu machen. (Weitere Informationen finden Sie unter [verkürzen Runtime Arbeitsspeicher in Windows 8](https://blogs.msdn.microsoft.com/b8/2011/10/07/reducing-runtime-memory-in-windows-8/), Blogbeitrag auf MSDN.) Es ist wichtig, um sicherzustellen, dass OEMs, unabhängigen Hardwareanbietern, ISVs und Microsoft-partner zu verbessern die Präsenz in jeden dieser Bereiche und Geräte mit sorgfältige liefern eine hervorragende Kundenzufriedenheit konfigurieren.

### <a name="storage"></a>Storage

#### <a name="disk-performance"></a>Datenträgerleistung: 

In einer Konfiguration mit wenig Arbeitsspeicher Windows nutzt die Auslagerungsdatei und Austauschen von Inhalten aus dem Speicher und somit die Leistung des zugrunde liegenden Datenträgers ist entscheidend für die Bereitstellung einer reibungslose und reaktionsschnelle Benutzeroberfläche zur Verfügung. Hardwareanforderungen für die Zertifizierung Anleitungen auf wichtige Leistungsmetriken für die Speicherung auf verbunden Standby-Geräten. (Weitere Informationen finden Sie unter [Device.Storage Anforderungen](https://msdn.microsoft.com/en-us/library/windows/hardware/jj134356.aspx) auf MSDN.)

Windows verfügt über Mechanismen reduzieren die Speicherverwendung angehaltenen Windows Store-apps und über effiziente sequenzielle Datenträger-e/a fortsetzen. (Weitere Informationen finden Sie unter [Reclaiming Arbeitsspeicher von apps im Metro-Stil](https://blogs.msdn.microsoft.com/b8/2012/04/17/reclaiming-memory-from-metro-style-apps/), Blogbeiträgen auf MSDN.) Beispiel: haben Sie eine 120 MB-app, die muss vom Datenträger auf Resume - einem Datenträger gelesen werden, die sequenzielle bietet Lese-Leistung von 60 MB/s dauert 2 Sekunden für diese app wieder vom Datenträger gelesen werden, während ein Datenträger, der bietet 120 MB/s nur 1 Sekunde bis zu seinen Inhalt in den Arbeitsspeicher zu bringen dauern wird. eMMC und SSD-Speicher bieten sequenzielle Lese Änderungsraten ungefähr 120-150MB/s, während typische Rotation Datenträger kumulativ von etwa 50 MB/s haben. Laufzeit-Richtlinien in Windows stellen Kompromisse basierend auf speicherleistung und langsamer Datenträger (z. B. HDD und HHDD), die möglicherweise langsamer app Switch/Multitasking Erfahrung und erhöhte app Beendigungen führen werden.

#### <a name="disk-endurance"></a>Datenträger endurance

Die Endurance oder Lebensdauer-Rotation Speicher wie SSDs und eMMC Datenträger proportional zum das Gesamtvolumen der Daten, die mit verschiedenen anderen Faktoren (Arbeitslast, die Ausrichtung der Schreibvorgänge usw.) auf das Gerät geschrieben werden.
Auf einem Gerät 1 GB werden ein größerer Datenträger der Schreibvorgänge in einen Speicher der Speicherkapazität, erhält das ist ein wichtiger Aspekt beim Auswählen des Webparts.

Endurance variiert erheblich basierend auf der Hersteller (Block Größenauswahl, Typen von flash-Speicher usw..). Derzeit stehen keine standardisierten Verfahren Endurance messen. Es wird empfohlen, dass Partner Datenträger Endurance vor der Durchführung von Gerät auswahlentscheidungen bewerten.

## <a name="recommended-goals"></a>Empfohlene Ziele

Hinweis: Die folgende Tabelle enthält Ziele für 32-Bit-Windows-Systeme. Die Speicher Leistung Anleitung ist für das Speichermedium Boot und mit der kleinere der 2 % getesteten oder 1 GB freier Speicherplatz vorhanden.

<table>
<thead>
<tr class="header">
<th>Kategorie</th>
<th>Metrisch</th>
<th>Ziele</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<th rowspan="9">Geplante Speicherbedarf</th>
<td colspan="2"><strong>Systemebene</strong></td>
<!--Empty cell in colspan-->
</tr>
<tr class="even">
<!--Empty cell in rowspan-->
<td>
<p>&nbsp;&nbsp;&nbsp;Treiber nicht auf ausgelagerten Code</p>
</td>
<td>&lt;20 MB</td>
</tr>
<tr class="odd">
<!--Empty cell in rowspan-->
<td>
<p>&nbsp;&nbsp;&nbsp;Treiber nicht ausgelagerten Zuweisungen</p>
</td>
<td>&lt;30 MB</td>
</tr>
<tr class="even">
<!--Empty cell in rowspan-->
<td>
<p>&nbsp;&nbsp;&nbsp;Hardware Arbeitsspeicher Reservierung</p>
</td>
<td>&lt;130 MB</td>
</tr>
<tr class="odd">
<!--Empty cell in rowspan-->
<td>
<p>&nbsp;&nbsp;&nbsp;Insgesamt aktiv Private Seiten zum Starten des Apps Services, Aufgaben</p>
</td>
<td>&lt;40 MB</td>
</tr>
<tr class="even">
<!--Empty cell in rowspan-->
<td colspan="2"><strong>Pro Treiber (nicht ausgelagerter Zuweisungen)</strong></td>
<!--Empty cell in colspan-->
</tr>
<tr class="odd">
<!--Empty cell in rowspan-->
<td>&nbsp;&nbsp;&nbsp;Treiber Locked/benachbart Arbeitsspeicher Zuweisungen</td>
<td>12 MB für alle Treibertypen von</td>
</tr>
<tr class="even">
<!--Empty cell in rowspan-->
<td>&nbsp;&nbsp;&nbsp;Nicht ausgelagerter Zuweisungen</td>
<td>
<p>&lt;= 6 MB für GPU-Treiber</p>
<p>&lt;= 4 MB für andere Treiber</p>
</td>
</tr>
<tr class="odd">
<!--Empty cell in rowspan-->
<td>&nbsp;&nbsp;&nbsp;Treibercode nicht ausgelagerter</td>
<td>&lt;= 10 MB für GPU Treiber &lt;= 1,66 MB für andere Treiber</td>
</tr>
<tr class="even">
<th>Zum Starten des apps Speicherbedarf</th>
<td><strong>Autostart-Programme, Dienste und Aufgaben (einschließlich Modul)</strong></td>
<td>&lt;40 MB</td>
</tr>
<tr class="odd">
<th rowspan="13">Datenträgerleistung</th>
<td colspan="2"><strong>Zufällige Leistung</strong></td>
<!--Empty cell in colspan-->
</tr>
<tr class="even">
<!--Empty cell in rowspan-->
<td>
<p>&nbsp;&nbsp;&nbsp;4 KB schreiben IOPs, gemessen über einen Bereich von 1 GB</p>
</td>
<td>&gt;= 200 IOPs</td>
</tr>
<tr class="odd">
<!--Empty cell in rowspan-->
<td>
<p>&nbsp;&nbsp;&nbsp;4 KB schreiben IOPs, gemessen über einen Bereich von 10 GB</p>
</td>
<td>&gt;= 50 IOPs</td>
</tr>
<tr class="even">
<!--Empty cell in rowspan-->
<td>
<p>&nbsp;&nbsp;&nbsp;64 KB schreiben IOPs, gemessen über einen Bereich von 1 GB</p>
</td>
<td>&gt;= 25 IOPs</td>
</tr>
<tr class="odd">
<!--Empty cell in rowspan-->
<td>
<p>&nbsp;&nbsp;&nbsp;4 KB lesen IOPs, gemessen über einen Bereich von 10 GB</p>
</td>
<td>&gt;= 2000 IOPs</td>
</tr>
<tr class="even">
<!--Empty cell in rowspan-->
<td>
<p>&nbsp;&nbsp;&nbsp;4 KB 2:1 Lese-/Schreibvorgänge IOPs, gemessen über Bereich von 1 GB</p>
</td>
<td>&gt;= 500 IOPs</td>
</tr>
<tr class="odd">
<!--Empty cell in rowspan-->
<td>
<p>&nbsp;&nbsp;&nbsp;4 KB 2:1 Lese-/Schreibvorgänge IOPs, gemessen über einen Bereich von 10 GB</p>
</td>
<td>&gt;= 140 IOPs</td>
</tr>
<tr class="even">
<!--Empty cell in rowspan-->
<td colspan="2"><strong>Sequenzielle Leistung</strong></td>
<!--Empty cell in colspan-->
</tr>
<tr class="odd">
<!--Empty cell in rowspan-->
<td>
<p>&nbsp;&nbsp;&nbsp;Schreiben Sie Geschwindigkeit (64 KB e/a), über einen Bereich von 10 GB</p>
</td>
<td>&gt;= 40 MB/s</td>
</tr>
<tr class="even">
<!--Empty cell in rowspan-->
<td>
<p>&nbsp;&nbsp;&nbsp;Schreiben Sie Geschwindigkeit (1 MB e/a), über einen Bereich von 10 GB</p>
</td>
<td>&gt;= 40 MB/s</td>
</tr>
<tr class="odd">
<!--Empty cell in rowspan-->
<td>
<p>&nbsp;&nbsp;&nbsp;Lesen Sie die Geschwindigkeit (64 KB e/a), über einen Bereich von 10 GB</p>
</td>
<td>&gt;60 MB/s = † (120 MB/s)</td>
</tr>
<tr class="even">
<!--Empty cell in rowspan-->
<td colspan="2"><strong>Gerät e/a-Wartezeit</strong></td>
<!--Empty cell in colspan-->
</tr>
<tr class="odd">
<!--Empty cell in rowspan-->
<td>
<p>&nbsp;&nbsp;&nbsp;Maximale Wartezeit</p>
</td>
<td>&lt;500 Millisekunden</td>
</tr>
<tr class="even">
<th>Datenträger Endurance</th>
<td><strong>Lebensdauer</strong></td>
<td>&gt;= 2 bis 3 Jahre</td>
</tr>
</tbody>
</table>

## <a name="measuring-memory-using-the-windows-assessment-and-deployment-kit-adk"></a>Messen der Speicher mit dem Windows Assessment and Deployment Kit (ADK)

Die Arbeitsspeicher-Bilanz Bewertung in ADK bietet eine quantitativen der Baseline Speicherbedarf für unterschiedliche Konfigurationen im Vergleich zu eines Betriebssystemabbilds Retail.

### <a name="related-resources"></a>Verwandte Ressourcen

-   Leitfaden für die Bewertung Speicherbedarf wird ausgeführt und Sammeln von Daten: [http://msdn.microsoft.com/en-us/library/windows/hardware/hh825365.aspx](http://msdn.microsoft.com/en-us/library/windows/hardware/hh825365.aspx)

-   Grundlegendes zu den Ergebnissen: [http://msdn.microsoft.com/en-us/library/windows/hardware/jj130826.aspx#BKMK_Goals](http://msdn.microsoft.com/en-us/library/windows/hardware/jj130826.aspx#BKMK_Goals)

## <a name="guidance"></a>Anleitung

<!-- No content provided here in the original Word file. -->

### <a name="for-oem"></a>Für OEM

OEMs haben einen erheblichen Einfluss auf die Auswahl von Hardware-Treiber und vorinstallierte Software, die direkten Einfluss auf die Speicherbedarf des Systems.

-   Vor der Bereitstellung zu verstehen und Bewerten der Auswirkungen der Treiber und Software installieren auf der Basis einer Neuinstallation Bild und stellen Sie sicher, dass sie innerhalb der empfohlenen Ziele oben sind:

<!-- -->

-   Treiber Bilanz: Dies kann durch Reduzieren der Anzahl der Treiber oder Hardware/Treiber, niedrigere speicheranforderungen auswählen

-   Vorinstalliert Software/Antivirus: Reduzieren der Anzahl der Standard 'ausführen-always' Prozesse zum Starten einer (durch vorinstallierte Software eingeführt) sowie eine Anleitung, steht Sie Verbrauchern bestimmte Anwendungen oder Funktionen aktivieren, falls erforderlich

<!-- -->

-   Sollten Sie einen anderen Treiber oder Softwarehersteller, die Sie, mit entsprechenden Funktionalität mit niedrigeren Auswirkung auf Systemspeichers angeben kann verwenden

<!-- -->

-   Wenden Sie sich an Ihren Treiber und Softwarehersteller für den aktuellen Versionen ihrer Software, um festzustellen, ob sie die Auswirkung auf Speicher beeinträchtigen können

    -   Geben Sie Feedback zu Ihren Partnern auf bestimmte Treiber oder Software, die größer als die empfohlenen Speicherverwendung und Spuren/Protokolle aus dem Assessment Toolkit aufweisen

### <a name="for-ihvisv"></a>Für IHV/ISV

Unabhängigen Hardwareanbietern, die übermitteln können effiziente Treiber können OEMs zum Erstellen von 1 GB-Systemen, die Consumer eine großartige Erfahrung ermöglichen im Arbeitsspeicher.

-   Sicherstellen Sie, dass die Hardware Teile Zertifizierung über (besonders nicht auslagerbaren Speicherbedarf für Treiber) und Leistung für Speicherhardware und Speicherverwendung ausführen immer Apps für Applikationen erfüllen

-   Werden Sie mit Speicherverwendung mithilfe eines Modells 'Zahlen für die Wiedergabe' werden, da nur wie und wann erforderlichen Funktionen effizientesten verwendet

    -   Vermeiden Sie die Konfiguration der Treiber zur Unterstützung von Features, die nur für Systeme mit 1 GB erforderlich sind (beispielsweise plattformspezifische Treiberpakete, die Hardware erkennen und Laden Sie spezifischen Code erstellen)

    -   Minimieren der Common Language Runtime Kosten – den mindestens erforderlichen bei Bedarf Speicher reservieren und frei, sobald Sie fertig sind (beispielsweise Puffer zur Unterstützung von RAID-Speicher sind nicht erforderlich, wenn der Benutzer explizit konfiguriert)

-   Nutzen Sie Tools zu verstehen und Speicherbedarf verbessern.

    -   Die folgenden Talk beschreibt die Vorgehensweise zum Verkleinern zusammen mit verfügbaren tools\
        Reduzierung der Arbeitsspeicherbedarf der Treiber und Apps: <http://channel9.msdn.com/events/BUILD/BUILD2011/HW-141T>

### <a name="for-antimalware-app-isv"></a>Für Modul app ISV

Modul apps können Baseline des Betriebssystems Arbeitsspeicher Speicherbedarf und benutzerfreundlichkeit beim für die Leistung nicht optimiert erheblich beeinträchtigen.

-   Stellen Sie sicher, dass der Anzahl und Speicherbedarf von 'ausführen-always' Services/Prozesse minimal wie möglich sind. Beispiel:

<!-- -->

-   Im Idealfall nur ein Prozess/Dienst für Echtzeitsuche

-   Andere Prozesse für das Aktualisieren von antivirus Definitions, die mit der Benutzeroberfläche für den Benutzer usw. sollte erstellt werden, nur, wenn als Reaktion auf Benutzereingaben oder Benachrichtigungen benötigt und beendet werden, sollten wenn Vorgänge abgeschlossen sind.

<!-- -->

-   Werden Sie mit Speicherverwendung für den Prozess 'ausführen-always' effizientesten verwendet

    -   Verwalten Sie eine Datenstruktur zum Darstellen von Signaturen und Laden nur bestimmte Teile bei Bedarf

    -   Benutzeroberfläche sollte nicht gestartet werden, es sei denn, die explizit durch den Benutzer (beispielsweise Popups, die unmittelbar nach dem Start öffnen) angefordert.

<!-- -->

-   Windows verfügt über eine Kerngruppe von Windows-APIs und zugehörige Dokumentation zum Optimieren der Leistung bereitgestellt.

    -   Optimieren der Signatur laden und Wartung über die Verwendung von Komprimierung <http://msdn.microsoft.com/en-us/library/ee915356(v=PROT.13).aspx>

    -   Verwalten des Caches für zuvor überprüften Dateien Arbeit minimieren

    -   Verwenden Sie wenig Arbeitsspeicher und CPU-/ auf Datenträger Prioritäten für die Minimierung der Auswirkungen

        -   SetPriorityClass\
            <http://msdn.Microsoft.com/en-us/library/ms686219 (v=vs.85).aspx>

        -   SetThreadPriority\
            <http://msdn.Microsoft.com/en-us/library/ms686277 (v=vs.85).aspx>

-   Fokus auf Speicherbedarf im Leerlauf, um sicherzustellen, dass diese Speicherbedarf im Leerlauf ist &lt; 15 MB auch als während Vollzugriff auf das Systemscans und Echtzeit Überprüfung um Speicherbedarf so weit wie möglich, während diese Szenarien zu reduzieren.

## <a name="validation"></a>Überprüfung

Zum Bewerten und Speicherverwendung durch die Prozesse und Treiber geprüft haben, verwenden Sie die Bewertung Speicherbedarf in ADK aus. Nachdem die Bewertung ausgeführt, öffnen Sie den Bericht im Tool zur Bewertung Windows-Konsole (WAC) und extrahieren Sie die relevanten Metriken, die mit der folgenden Anleitung zu.

### <a name="system-level"></a>Systemebene 

Systemweite Arbeitsspeicher Metriken finden Sie im Bewertungsbericht zur. Im folgende Screenshot werden **In Verwendung Gesamtspeichers**, **Driver_Non-Paged Code** und **Zuweisungen** Metriken behandelt.

![Speicherbedarf in der Windows-Assessment-Konsole angezeigt.](images/weg-wac-memory-footprint-highlighted.png)

### <a name="per-driver"></a>Pro Treiber

#### <a name="non-paged-code"></a>Code nicht ausgelagerter

Um die speziellen nicht ausgelagerten Code Beteiligung der einzelnen Treiber zu erhalten, erweitern Sie die Metrik **Driver_Non-Paged Code** .

![Speicherverwendung durch Treiber nicht ausgelagerten Code in Windows Assessment Konsole (WAC) dargestellt.](images/weg-wac-driver-non-paged-code.png)

#### <a name="non-paged-allocations"></a>Nicht ausgelagerter Zuweisungen

Um den bestimmten nicht ausgelagerten Zuweisungen einzelne Treiber zu erhalten, erweitern Sie **Driver Non-Paged Zuweisungen** metrische und select **Group by - &gt; (kein Rahmen)**.

![Nicht ausgelagerter Zuweisungen für Treiber in Windows Assessment Konsole (WAC) dargestellt.](images/weg-wac-driver-non-paged-allocations.png)

### <a name="span-idtoc375143139-classanchorspan-idtoc375143455-classanchorspan-idtoc375165809-classanchorspan-idtoc426441280-classanchorspanspanspanspanper-process"></a><span id="_Toc375143139" class="anchor"><span id="_Toc375143455" class="anchor"><span id="_Toc375165809" class="anchor"><span id="_Toc426441280" class="anchor"></span></span></span></span>Pro Prozess

Zum Abrufen der Anzahl der aktiven private Seiten von einzelnen Prozessen (Applications, Diensten oder Aufgaben) auf dem System, erweitern Sie die Metrik **Prozess Private Seiten** , und wählen Sie die **aktiven** untergeordneten Metrik.

In der folgenden Abbildung werden Windows Defender (MsMpEng.exe-Prozess) 14.9 MB Arbeitsspeicher über seine private Arbeitssatzes genutzt.

Um zu überprüfen, dass das Ziel des Vorgangs 40 MB für Autostart-Programme und Dienste und Aufgaben erzielt werden, identifizieren Sie jeden Prozess in dieser Liste vorinstallierte Software zugeordnet und Berechnen der Summe.

![Aktive private Seiten Prozesse in der Windows-Assessment-Konsole (WAC) dargestellt.](images/weg-wac-process-private-pages-in-use.png)

# <a name="delivering-a-great-startup-and-shutdown-experience"></a>Spielt eine großartige Erfahrung beim Starten und beenden

Dieser Abschnitt enthält eine Übersicht über die Erfahrung schnellen Start und unsere Empfehlungen Partnern das beste ein-/ausschalten Kunden zu übermitteln.

PCs sind aktiviert und deaktiviert oft einen Tag. Ein PC möglicherweise heruntergefahren, Energiesparmodus oder Ruhezustand je nach Verwendungsmuster und die Funktion Batterie Lebensdauer des Geräts. Beim Starten ist der ersten Benutzeroberfläche für Benutzer mit einem Gerät und einer wiederkehrenden Funktionalität für die Lebensdauer des Geräts. Kunden Telemetrie gibt an, dass Benutzer starten, und fahren Sie ihren PC auf mindestens einmal pro Tag. Standby verbunden Funktion verringert die Häufigkeit, mit der ein Gerät gestartet werden muss, aber starten möglicherweise erforderliche Software-Firmware Updates Batterie, und größeren konfigurationsänderungen an dem Gerät.

Beginnend mit Windows 8.x, die Geschwindigkeit des Übergangs ein-/ausschalten ist wesentlich größer als in früheren Versionen von Windows. Das zuvor verwendete Benutzer Interaktionsmodell wurde mit Schlüssel Boot unterbrechen drückt alternative Startpfade an. Mit einer wesentlich schneller Startzeit Boot Unterbrechung nicht sinnvoll sind und sich negativ auf die Boot-Erfahrung auswirken.
Bisher war es wichtig, beenden den Startvorgang so früh wie möglich für Entscheidungspunkte, wie ein anderes Betriebssystem starten, da Abwärtskompatibilität sein und sollte eine lange und langsam war.
Es wurde auch wesentlich einfacher mit langsamer Start Zeiten Zeiträume erstellen, in denen diese Tastatureingaben erkannt und aktiviert werden konnte. Dies ist nicht mehr die Groß-/Kleinschreibung in Windows 8.x und Windows-10.

Die Standard-Start-Leistung bietet durch die Nutzung von erheblich verbesserte Technologie Ruhezustand. Um die wurde verbessert die Leistung der ein-/ausschalten Erfahrung zu verstehen, finden Sie unter diesem Dokument im Abschnitt [Ruhezustand (S4) anhalten und fortsetzen](#z1) . Die Aspekte in diesem Abschnitt beschreiben das Benutzermodell für die schnelle ein-/ausschalten Übergänge, Optionen im Zusammenhang mit dieser Übergänge und die Erlebnis durch OEMs/ODMs erforderlichen Komponenten.

## <a name="considerations"></a>Erwägungen

Die wichtigste Quelle von Boot Verzögerung ist die Teiler OEM-Software. Schneller Start Buchen ein-/ausschalten stellt rund um 50 % der gesamten Bootzeit und wird vom ersten und Drittanbieter-Prozesse, die beim Systemstart gestartet direkt beeinflusst.

-   Dienste werden möglicherweise weiterhin fortsetzen

-   Zum Starten des apps: Standardschacht andauernde Verknüpfungen, OEM Statusindikatoren usw.

-   Antivirus-Aktivität

Alle oben genannten nutzen System Ressourcen (CPU und Datenträger) Ergebnis in auf einem, das andere oder beide Blockierungsvorgänge. Dies kann die Gerät nicht reagiert, Verzögerung app Zeiten zu starten, oder schneller lag tätigen oder langsam.

Berücksichtigen Sie ein-/ausschalten Leistung optimieren sollten Sie folgende Punkte:

-   Bestimmen, welche nicht Posteingang 1 ^ St ^- oder 3rd Party Prozesse geladen ist und auf dem System ausgeführt werden.

-   Bestimmen Sie, was beim Start über run-Schlüssel-Registrierung gestartet wird.

    -   IHV Hardware-bezogenen Prozesse werden hauptsächlich hier gefunden.

-   Vermeiden Sie einschließlich von verwaltetem Code Prozesse in der Startpfad.

-   Verwendung Techniken verzögert Prozesse beim Systemstart gestartet.

-   Sollten Sie konvertieren traditionellen desktop-apps in Windows Store-apps, wie sie sich beim Start verursachen nicht.

    -   Arbeiten Sie mit unabhängigen Hardwareanbietern Windows Store-Gerät apps verwenden können.

-   Verstehen Sie Arbeitsspeicher Verbrauch Effekt ein-/ausschalten Übergangszeiten.

    -   Optimieren der Leistung von Arbeitsspeicher belegt, um die Hiberfile zu verkleinern.

    -   Verwenden Sie den neuen Hiberfile Diagnose-Modus.

    -   Es wird nicht empfohlen, dass Sie Hybriden auf Laptops aktivieren und Ultraportables, da dies ein Hiberfile Reserve generiert (S3) anhalten.

-   Migrieren von Updater-Prozesse, um die Uhr zu verwenden, um die Anzahl der geladenen Prozesse zu verringern.

-   Vertraut gemacht haben Sie, dass dieser Datenträgerdurchsatz für ein-/Ausschalten von entscheidender Bedeutung ist gering.

    -   Lese-/Schreibzeiten Hiberfile darstellen durchschnittlich 50 % der Datei Boot zum Bildschirm Startzeit.

    -   Die meisten Systeme werden beim Start Bindung.

    -   Eine schnellere HDD/SSD können die Auswirkungen der eine erhebliche Software geladen wird geladen und initialisiert beim Start minimieren.

    -   Sie sollten die CPU-Leistung und Arbeitsspeicherkapazität abstimmen.

-   Erkennen Sie, dass Hybrid Laufwerke ein-/Ausschalten der Leistung von Vorteil sind.

    -   Das neue Feature für hybride Hinweise Laufwerk verwendet.

### <a name="fast-startup"></a>Schneller Start

Beginnend mit Windows 8.x, das Standardszenario Herunterfahren und neu starten wurde aktualisiert und mit dem Namen als schneller Start. Schneller Start beginnt mit des Herunterfahrens und enthält Schreiben von Daten auf dem Datenträger in eine Möglichkeit, die ähnlich wie Ruhezustand funktioniert. Ein wesentliche Unterschied ist, dass benutzersitzungen für alle (Sitzung 1) abgemeldet und die weiteren Informationen in die Hiberfile geschrieben wird. Beim Starten des PCs aus diesem Zustand statt über den vollständigen Startvorgang, in dem Windows, Treibern, Geräte und Dienste werden initialisiert, lädt Windows den zuvor initialisierten Zustand Lesen aus der Hiberfile. Dadurch wird der Vorgang des Abrufens zum Sperren oder im Menü Start beschleunigt.

Die Verwendung von Ruhezustand Technologie wird erweitert, um eine neue Standard starten und Herunterfahren-Anwendung erstellt, die viel schneller als eine vollständige Boot ist.

![Diagramm der Phasen in fast beim Starten und beenden.](images/weg-diagram-fast-startup-boot-shutdown.png)

Die schnellere starten und Herunterfahren Sequenz verwendet die Ruhezustand Infrastruktur auf den PC im Ruhezustand platzieren. Im Gegensatz zu einer vollständigen Herunterfahren starten und die Sitzung des Benutzers wird geschlossen, und klicken Sie dann eine Ruhezustand ausgeführt wird. Daher ist die Ruhezustand Datei vereinfacht Ruhezustand und Resume viel schneller viel kleiner. In den folgenden Schritten nutzt außerdem die Parallelisierung Optimierungen an.

Treiber oder apps mit Systemdienst und Systemintegratoren erstellen Entwickler sollten auch der Treiberprobleme wie Speicherverluste besonders sorgfältig sein. Während der Treiber Qualität immer wichtige wurde, die oben Zeit zwischen Kernel Neustarts möglicherweise wesentlich länger als in früheren Versionen von Windows, da Benutzer initiiert Herunterfahren, Kernel, Treibern und Diensten beibehalten und wiederhergestellt, nicht neu gestartet.

### <a name="full-boot"></a>Vollständige boot

Die folgende Liste enthält die Aspekte, die zum Starten des am besten zu ermöglichen.

-   Des Lastenausgleichs für CPU-Leistung, Leistung und Speicherkapazität.

-   Optimieren der UEFI Lese-routing Performance.

-   Sicherstellen Sie, dass Treiber Endknoten Knoten Geräte fast Resume-Richtlinien zu befolgen.

-   Stellen Sie sicher, dass Treiber ihre S0 Set-Power IRPs so schnell wie möglich, um zu verhindern, dass andere Geräte Abrufen ihrer S0 Set-Power IRPs abschließen.

-   Treiber und Dienste gegen Speicherverluste zu überprüfen.

-   Registrieren eines Dienstes Empfang von Power Management Ereignisse Benachrichtigung nur, wenn es unbedingt erforderlich ist.

-   Treiber müssen nicht warten, für die Durchführung die S\_IRP bis D\_IRP abgeschlossen ist, da dies andere Geräte erhalten, deren S verhindert werden\_IRPs, die Verzögerungen Serialisierung und erhöhen insgesamt Zeit anhalten.

### <a name="shutdown-api-behavior"></a>Problem beim Herunterfahren API

Um die beste Kompatibilität mit apps sicherzustellen und ermöglicht die bestmögliche Leistung für neue apps, wurden neue Flags zum Anfordern einer beim Herunterfahren für den schnellen Start erstellt. Die folgende Tabelle beschreibt die neuen Flags und das Verhalten für das Beenden APIs. Ausführliche Informationen zu diesen APIs und Flags stehen auf MSDN.

| API                          | Problem beim Herunterfahren |
|------------------------------|------------------------------------------------------------------------------------|
| **InitiateSystemShutdownEx** | Immer führt eine vollständige Herunterfahren |
| **InitiateSystemShutdown**   | Immer führt eine vollständige Herunterfahren |
| **InitiateShutdown**         | Führt ein Herunterfahren für den schnellen Start mit der Verwendung von das HERUNTERFAHREN\_HYBRID-Flag |
| **ExitWindowsEx**            | Führt ein Herunterfahren für den schnellen Start mit der Verwendung von der EWX\_HYBRID\_HERUNTERFAHREN-Flag |

### <a name="distinguishing-when-a-hibernate-or-a-shutdown-for-fast-startup-will-occur"></a>Unterscheidung nach dem Ruhezustand oder ein Herunterfahren für den schnellen Start werden wird

Gerätetreiber erhalten eine Benachrichtigung für den Übergang zu einem S5 Ziel Power Zustand beim Herunterfahren statt der Ruhezustand Zustand S4, die den tatsächlichen Power-Status ist. Dadurch wird die Treiber zu einer anderen Aktivierung Verhalten für den schnellen Start nach einem Herunterfahren festlegen möchten. Ziel und effektiven Zustände befinden sich im System\_Power\_Zustand\_Context-Struktur.

Für die meisten Geräte wird der Unterschied zwischen S4 und S5 Remoteaktivierung Verhalten auf der Ebene der Bus-Treiber gesteuert. Wenn Sie Ihren eigenen Bustreiber implementieren und diese unterscheiden müssen, wenden Sie sich an Ihrem Microsoft-Partner, zusätzliche Informationen. Es folgen einige bewährten Methoden, mit deren Hilfe ein Erlebnis schneller Start:

-   Balance CPU-Leistung, datenträgerleistung und Kapazität

-   Optimieren der UEFI lesen routing-Leistung

-   Stellen Sie sicher, dass Treiber von untergeordneten Knoten Geräten fast Richtlinien fortsetzen, müssen

-   Sicher, dass Treiber ihre S0 Set-Power IRPs so schnell wie möglich, um zu verhindern, dass andere Geräte Abrufen ihrer S0 Set-Power IRPs ausführen

-   Vermeiden Sie apps auf Start, mit Ausnahme von Modul und Gerät apps starten.

-   Nie starten Sie beim Start von RunOnce apps

-   Vermeiden Sie apps in der Startpfad verwaltetem code

-   Verzögerung beim Starten nicht kritischen Apps mithilfe des Taskplaners

-   Treiber und Dienste gegen Speicherverluste zu überprüfen

-   Registrieren eines Dienstes Empfang von Power Management Ereignisse Benachrichtigung nur, wenn es unbedingt erforderlich

-   Treiber müssen für die Durchführung die S nicht warten\_IRP bis D\_IRP abgeschlossen ist, da dies andere Geräte erhalten, deren S verhindert werden\_IRPs, Verzögerungen Serialisierung und erhöhen insgesamt Zeit anhalten

### <a name="hibernate-s4-suspend-and-resume"></a>Ruhezustand (S4) anhalten und fortsetzen

In einem Übergang Ruhezustand werden der Inhalt des Speichers in eine Datei auf dem primären Systemlaufwerk geschrieben. Dieser Vorgang behält den Status des Windows-apps und -Geräte. Bei der kombinierten Arbeitsspeicherbedarf gesamten physikalischen Speicher nutzt, muss die Datei Ruhezustand sein groß genug ist, um sicherzustellen, dass genügend Speicherplatz zum Speichern der gesamte Inhalt des physischen Arbeitsspeichers vorhanden ist.
Da Daten in einen permanenten Speicher geschrieben werden, nicht die DRAM verwalten muss Self aktualisieren und ausgeschaltet werden können. Dies führt zu sehr niedrige Power zeichnen, ähnelt das PC, in dem Zustand.

#### <a name="user-scenarios-for-hibernate"></a>Benutzerszenarien für Ruhezustand 

Dies sind die wichtigen Szenarien, die erfordern Ruhezustand PCs heute unter Windows-Technologie:

-   **Doze Ruhezustand:** Ein System ist links im Leerlauf und automatisch in den Ruhezustand Übergänge.

-   **Kritische Batterie:** Windows Ruhezustand automatisch den PC-Option, um Datenverlust zu vermeiden, wenn Batterie heraus ausgeführt wurde.

-   **Zur Bedingung:** Ein System erreicht eine vordefinierte Temperatur an, die automatische System Power unten benötigt, um Kreis zu schützen.

-   **Benutzer initiiert werden:** Ein Benutzer, den markiert Ruhezustand, um den aktuellen Benutzerstatus mit minimal Power speichern zeichnen.

Obwohl dieser Liste als den Bedürfnissen weiterentwickelt kann und Funktionen von PCs weiterentwickelt, es wird davon ausgegangen, dass weiterhin verwenden viele PCs Ruhezustand, insbesondere wenn verbundenen Standby nicht möglich.

#### <a name="hibernate-phase"></a>Ruhezustand Phase

![Diagramm der Ruhezustand Phase.](images/weg-diagram-hibernate-phase.png)

In dieser Phase Windows durchläuft den verschiedenen Komponenten der Phasen Ruhezustand geschieht und anschließend den Status des Benutzers Kontext und System speichert aufgefordert. Die Daten werden komprimiert und auf den Datenträger geschrieben. Das System der Prozessorkerne auf dem System verwendet, um die Daten im Arbeitsspeicher zu komprimieren und einen Prozessor verwendet, wenn die Daten auf den Datenträger geschrieben. Sobald alle Daten ist auf den Datenträger geschrieben Windows benachrichtigt die Firmware, dass es zum Herunterfahren bereit ist.

Die Benachrichtigung Firmware erfolgt durch Schreiben in den Energiesparmodus Typ registriert mit Werten, die im S4-Objekt gemäß Definition im ACPI 4, Abschnitt 4.5, Tabelle 4 bis 13 und Abschnitt 7.3.4 bereitgestellt wurden. Dies gibt an der Firmware auf nächste schalten ein Lebenslauf statt einen vollständigen Neustart versucht wird.

#### <a name="resume-phase"></a>Resume-phase

![Diagramm der Phase fortsetzen.](images/weg-diagram-resume-phase.png)

Ruhezustand Resume beginnt mit der Firmware POST, das eine vollständige Boot ähnlich ist. Der Windows-Start-Manager erkennt, dass eine fortsetzen aus dem Ruhezustand erforderlich ist eine gültige Ruhezustand Datei erkennen und das System wieder hochfahren weist, den Inhalt der Arbeitsspeicher und alle architektonische Register wiederherstellen. Im Fall einer Resume Ruhezustand werden der Inhalt des Speichers vom Datenträger gelesen, dekomprimiert und wiederhergestellt, Ihr System in den genauen Zustand, die beim es Ruhezustand versetzt wurde. Nachdem der Arbeitsspeicher-Inhalt wird wiederhergestellt, die Geräte neu gestartet werden und der Computer ausgeführt gibt, bereit für die Anmeldung.

Beachten Sie, dass zwar Gerätetreiber und Dienste benachrichtigt werden, sie nicht neu gestartet werden. Sie sind einfach in dem Zustand wiederhergestellt in denen sie sich zum Zeitpunkt die Ruhezustand Phase ist aufgetreten.

Die Wiederherstellung des Systemspeichers wird in 2 Phasen unterteilt. Die erste Phase erfolgt, um eine minimale Teil des Kernel, wiederherzustellen, die Sie für die Durchführung die Wiederherstellung Arbeitsspeicher für den Rest des Systems verwendet wird. Die erste Phase hat mit einer einzelnen Prozessorkern-Umgebung ausgeführt werden. Aber nach der minimale Teil des Systemspeichers wiederhergestellt wird, können alle Prozessorkerne, der ursprünglich und Wiederherstellung von Daten für das restliche die fortsetzen, wodurch erheblich beschleunigen des Prozess zu parallelisieren verwendet werden.

Der Vorgang wird noch verbessert, indem rechts-Größe den Verschlüsselung/Entschlüsselung Algorithmus, basierend auf den Funktionen des Prozessors.

Die Parallelisierung Optimierungen sind nur auf Systeme, die auf denen System garantieren kann, dass sie alle Daten von Ihnen angegebenen, die es die minimale-Umgebung verfügbaren darauf möglicherweise, verfügbar. Es kann nicht so verwendet werden, wenn Komponenten, die auf dem Absturz Dump ab, die während der Ruhezustand Wiederaufnahme des Betriebs verwendet wird, auch die minimale Umgebung angehören deklariert wurde noch nicht. Wenn Sie erstellen eine solche Komponente, wie ein Absturz Dump Filtertreiber oder ein Gerät mit einem Pfad für das separate Absturzabbild, wenden Sie sich an Microsoft, damit wir Sie durch diesen Vorgang führen kann.

### <a name="firmware-post"></a>Firmware POST

POST-schnelleres reduzieren die Gesamtdauer von Power bei verwendbaren Zustand.
Da Windows schneller Start wesentlich schneller ist, können POST ein wichtiger Anteil der insgesamt Startzeit dar. Weitere Informationen zu POST-Anforderungen ist in der Windows-Hardware-Zertifizierung Anforderungen dokumentiert. Unsere Analyse zeigt, dass die Dauer des POST-Anforderungen auf Plattformen erreicht werden, die vollständig auflisten und Aktivieren einer umfassenden Hardwarekomponenten in älter als Version – Betrieb-Umgebung.

Seit Windows 8 sind alle PCs liefern ihre Firmware basierend auf der Spezifikation Unified Extensible Firmware Interface (UEFI) 2.3.1 oder höher erforderlich. Da viele Systeme auf ältere, legacy Firmware Entwürfe basieren, sind Verkaufschancen zum Optimieren des Firmware Entwurfs um schnelleres POST besser zu berücksichtigen.

![Diagramm der Initialisierung des Datenflusses UEFI-Architektur.](images/weg-diagram-uefi-firmware-flow.png)

Die Architektur UEFI fließt über mehrere Phasen der Initialisierung Firmware und -Zielplattform fest. Basierend auf diesen klar definierten Phasen, sind verschiedene Entwurfsaspekte, die Dauer des POST beeinträchtigen könnten.

#### <a name="security-sec"></a>Sicherheit (s)

In der Phase s führt eine Plattform zum Extrahieren, dekomprimieren und Überprüfung der Plattform Microcode auf eine SPI NOR Flash gespeichert. Zu diesem Zeitpunkt ist die Plattform von Power-on Initialisierung RAM und einen Bus. Im folgenden werden Aspekte in dieser Phase.

-   Ist der Microcode speziell für die SKU oder Allgemein auf mehrere Plattformen? Die Größe der Microcode wird dekomprimierung beeinträchtigen, RAM und Validierung von übertragen.

    Berücksichtigen Sie Umgestalten von Microcode so gering wie möglich sein.

-   Kann die Geschwindigkeit der SPI NOR flash Bus werden erhöht? Viele Plattformen unterstützt mehrere Taktrate für das SPI NOR flash-Webpart. Sie sind häufig auf einen niedrigeren Taktfrequenz (beispielsweise 16 MHz) Betrieb und erhöht werden können.

    Berücksichtigen Sie zunehmende Bus-Geschwindigkeit zur Senkung der Wartezeit in Microcode Übertragung von NOR Flash RAM.

-   Hat die Plattform genügend NOR Flash? Um Kosten zu sparen, sind mit dem bare minimale NOR Teil aus, was höhere Komprimierung von Microcode und größer Kosten für dekomprimierung vielen Plattformen ausgelegt.

-   Berücksichtigen Sie ein größerer NOR flash-Webpart zum Speichern von Code mit weniger Komprimierung.

Komprimierung, Entwurf und Übertragung von Microcode Lastenausgleich kann die Leistung wie oft POST steigern. Am Ende des s kopiert der überprüften Microcode den Rest der UEFI Kernel und der Umgebung aus NOR Flash in den Arbeitsspeicher.

#### <a name="pre-efi-initialization-pei"></a>Älter als Version EFI Initialisierung (PEI)

Sobald der Kernel RAM ist, wird die Plattform initialisiert den Kernel und gestartet wird, um die Integrität der im Code, Systemtabelle und andere Elemente zu überprüfen.
Berücksichtigen Sie Entwerfen einer UEFI Kernel an, der für Ihre Plattform optimiert wurde und keine generische nicht optimierten Kernelmodus. Optimierungen können Folgendes umfassen:

-   Flags während Kernel kompilieren basiert, die Speicherpuffern optimieren.

-   Verknüpfen mit Modulen, die nicht für die Plattform Initialisierung erforderlich sind.

Wenden Sie sich an den Firmware Designern für Ideen zum Optimieren der UEFI Kernelmodus.

#### <a name="driver-execution-environment-dxe"></a>Treiber Execution Environment (DXE)

Zu diesem Zeitpunkt werden der Initialisierung, Core UEFI und 3. Partei DXE Treiber geladen. Von der Firmware Designer bereitgestellten Tools verwenden, kann der Besitzer identifizieren, die die geringsten leistungsfähige DXE Treiber sind, und prüfen, ob dieser Code optimiert werden kann.

Ein weiterer Aspekt in dieser Phase positioniert die Anzahl der DXE-Treiber geladen. Die Plattform sollte nur Treiber geladen werden, die zum Gewährleisten eines Neustarts und hängen nicht optional Hardware erforderlich. Endgültiges Design hängt Zielauswahl starten.

#### <a name="boot-device-selection-bds"></a>Boot Geräteauswahl (BDS)

Auswahl des Boot-Geräts ist der letzte Schritt bei der Initialisierung von Plattform vor der Übergabe an den Windows. In diesem Schritt bestimmt die Firmware auf welchen Geräten Boot vorhanden sind und welche eine zur Ausführung übergeben.
Sorgfältige Planung und Optimierungen der Boot-Variablen werden den Übergang zu den Windows-Startladeprogramm beeinträchtigen.

#### <a name="usb-enumeration"></a>USB-Aufzählung

USB-Enumeration ist ein Teil des BEITRAGS, das eine längere Zeit dauern wird. Mit neuen Änderungen in Windows 8 ist die standardmäßige Boot Groß-/Kleinschreibung nicht mehr erforderlich, USB-Enumeration. Sie können zusätzliche POST-Time-Optimierungen Hersteller Ihres Silicon und Firmware erhalten.

Wir empfehlen, dass der USB aufgelistet werden, wenn die Startreihenfolge festgelegt ist, z. B., alle anderen Pfade zu starten:

-   Wenn andere Optionen in der Startreihenfolge, beispielsweise wenn Windows, wechseln Sie Startoptionen einen USB-Klasse Boot-Eintrag am oberen Rand der Startreihenfolge Fügt einer höheren vorhanden sind.

-   Ist die eine weiter Boot-Variable festgelegt verursacht ein anderes Boot-Gerät verwendet werden.

-   Fehler beim Starten unmittelbar vorhergehenden dar.

### <a name="apps"></a>Apps

Desktop-apps, die sich in der Startpfad wirkt sich ein-/ausschalten Übergang und Energie-Effizienz. Task-Manager werden auch desktop-apps, die hohe Auswirkungen haben kennzeichnen und benachrichtigt den Benutzer zu desktop-apps, die immer ausgeführt werden. Weitere Informationen finden Sie unter [Start Apps](http://go.microsoft.com/fwlink/?LinkId=309749) (https://msdn.microsoft.com/library/hh848065.aspx). Anstelle der automatischen Starten desktop-apps, wird dringend empfohlen, dass Sie automatische Wartung und diese nur bei Bedarf ausführen.

## <a name="recommended-goals"></a>Empfohlene Ziele

![Wichtige](images/note-important.gif)**wichtige**&nbsp;&nbsp;&nbsp;allen Ziele definiert BIOS Initialisierungszeit ausschließen.

Um eine Great on/off Erfahrung zu übermitteln, empfiehlt es sich, dass ein PC diese Ziele erfüllt:

| **Szenario**             | **Tablet (CS)** | **Konvertiert werden kann.** | **Notizbuch** | **All-in-One** |
|--------------------------|-----------------|-----------------|--------------|----------------|
| Schneller Start (Sekunden)   | &lt;25         | &lt;= 15        | &lt;= 15     | &lt;= 15       |
| Hiberfile Größe (MB)      | &lt;300        | &lt;= 300       | &lt;= 300    | &lt;= 300      |
| Standby fortsetzen Sie (Sekunden) | Nicht zutreffend  | &lt;= 7         | &lt;= 7      | &lt;= 5        |

<br/>
<table>
<tr>
<th>Metrisch</th>
<th>Einheit</th>
<th>Ziel</th>
</tr>
<tr>
<td>
<p><strong>Anzahl der Prozesse durch Ausführen der Registrierungsschlüssel gestartet wurden</strong></p>
<p>Definiert als die Gesamtzahl der Prozesse auf jedem Start Run-Schlüssel mit gestartet wurden. Wirkt sich direkt auf Post-ein-/ausschalten Ressourcenverwendung (CPU und Datenträger).</p>
<p>Gefunden verfolgen einige ETW-Ereignisse in der schneller Start ablaufverfolgungen (mithilfe der generische Ereignisse-Tabelle):</p>
<p>Anbietername: Microsoft-Windows-Shell-CoreTask: Explorer\_ExecutingFromRunKeyOpcode: Win: Start</p>
<p>Feld \#1 des Ereignisses (Befehl) enthält die Befehlszeile verwendet, um die Prozesse zu starten.</p>
</td>
<td>
<p>count</p>
</td>
<td>
<p>&lt;10</p>
</td>
</tr>
<tr>
<td>
<p><strong>Normaler Priorität lesen Datenträger-e/a beim schnellen Start Post ein/aus</strong></p>
<p>Diese Metrik kann direkt über die Bewertungsergebnisse in der Windows-Assessment-Konsole unter abgerufen werden:</p>
<p>Insgesamt Boot &gt; Post On/Off &gt; insgesamt Datenträgerverwendung &gt; normaler Priorität liest (Bytes)</p>
</td>
<td>
<p>MB</p>
</td>
<td>
<p>&lt;30</p>
</td>
</tr>
</table>


## <a name="validation-and-testing"></a>Hinweise zur Überprüfung und testen

Sie können das Windows Assessment Toolkit zur Verbesserung der Leistung des Computers über Mindestanforderungen hinaus verwenden. Windows-Analysen, die im Zusammenhang mit ein-/ausschalten Erfahrung umfassen:

-   Fast Start-Bewertung

-   Vollständige Start- und Herunterfahren Bewertung

-   Standby-Bewertung

-   Assessment Ruhezustand

Die neuen Versionen der Fast Start und Ruhezustand Bewertung enthalten eine *Hiberfile* Diagnosemodus an. In diesem Modus erleichtert die Faktoren und apps, die zum großen Hiberfile Größe beitragen zu erkennen und Treiber, die von mehreren Stufen Resume implementiert nicht erkennt.

Es gibt zwei Hauptkategorien von Seiten im Arbeitsspeicher und sollte in der Hiberfile in Bezug auf System Evaluation: Treiber nicht ausgelagerten Pools Seiten und app-Dienste private arbeiten Seiten festgelegt.

Der neue Modus hilft Ihnen, zu verstehen, welche Software Komponenten für die Speicherverwendung verbessert werden müssen.

<a name="tools-and-technical-reference"></a>Tools und technische Referenz
-----------------------------

Sie können erfahren Sie mehr über die Erfahrung ein-/ausschalten, und Laden Sie Tools, mit denen Sie die Leistung von diesen Ressourcen zu analysieren:

| Titel der Ressource                     | Inhaltstyp | Beschreibung                                                                                                                                                                                                                 | Verknüpfung |
|------------------------------------|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------|
| Zum Starten des Apps                       | Artikel      | Sind einige der Effekte, die auf einem Windows-Gerät zum Starten des apps aufweisen und bietet Anleitungen für Entwickler (ISV/IHV) und OEMs überdenken der Verwendungsmuster Startup apps um Akkulaufzeit und Reaktionsfähigkeit zu verbessern. | [MSDN](http://go.microsoft.com/fwlink/?LinkID=309749) (https://msdn.microsoft.com/library/hh848065.aspx) |
| Ergebnisse für die Bewertung ein-/ausschalten | Document     | Dank Interpretieren von den Ergebnissen der On/Off Bewertung (Start-Leistung (Fast Start), Boot-Leistung (vollständige Boot), dem Standbymodus Leistung und Ruhezustand Leistung.                                          | [MSDN](http://msdn.microsoft.com/en-us/library/windows/hardware/jj130812.aspx) (https://msdn.microsoft.com/en-us/library/windows/hardware/jj130812.aspx) |


# <a name="delivering-a-great-browsing-experience"></a>Ein hervorragendes Browsen zu ermöglichen

In diesem Abschnitt konzentriert sich auf einige der Leistung Herausforderungen und was Sie tun können, um eine hervorragende Internet Explorer Web-browsing-Erfahrung für Ihre Kunden zu übermitteln.

Da alle Webbrowser im heutigen Markt ähnliche Standards unterstützen, wird die Leistung schnell ein wichtiges Unterscheidungsmerkmal von Kunden. Consumer, die diesem alle apps, die sie verwenden, einschließlich Browsern, die Leistung interessiert sind.

## <a name="considerations"></a>Erwägungen

Modul apps wirken sich auf Internet Explorer Webbrowser-Leistung. Seite des Ladens eine Messung der wie lange es dauert, starten Sie den Browser, und navigieren Sie zu einer Seite, stellen einen wichtigen Bestandteil des Benutzererlebnisses.
Es ist wichtig, dass Sie verstehen, und beachten Sie, was Sie installieren möchten, klicken Sie auf Ihrem PC, wie sie Ihre Kunden auswirkt und welche Wahrnehmung Abrufen der Leistung des Produkts.

### <a name="how-antimalware-apps-affect-browsing"></a>Einfluss auf Modul apps durchsuchen

Antischadsoftware wirkt sich auf Durchsuchen Geschwindigkeit und Fluidität in vier Hauptkategorien. Wie einem Browser Modul verlangsamen kann zählen:

<ol style="list-style-type: decimal">
<li>
<p>Störungen im Netzwerk und die Datenträgertypen</p>
<ul>
<li>
<p>Ausgehende Datenverkehr netzwerkverzögerungen</p>
</li>
<li>
<p>Datenträger Access Störungen</p>
</li>
<li>
<p>Reduzierte Netzwerk Parallelität</p>
</li>
</ul>
</li>
<li>
<p>Störungen im JavaScript</p>
<ul>
<li>
<p>Wiederherstellen der Vorversion JavaScript Skriptmodul</p>
</li>
<li>
<p>Umleiten von Anrufen von JavaScript</p>
</li>
<li>
<p>Dynamische JavaScript Ausführung beteiligt sind.</p>
</li>
</ul>
</li>
<li>
<p>Visual Störungen</p>
<ul>
<li>
<p>Redundante Layout Arbeit</p>
</li>
<li>
<p>Mit Website-Code konkurrieren</p>
</li>
</ul>
</li>
<li>
<p>Allgemeine Störungen</p>
<ul>
<li>
<p>Synchrone Kommunikation zwischen Servern</p>
</li>
<li>
<p>Ändern von Internet Explorer Annahmen</p>
</li>
</ul>
</li>
</ol>

### <a name="selecting-antimalware-apps"></a>Auswählen von Modul-apps

Es gibt mehrere zu berücksichtigende Faktoren beim ein Modul Produkt auswählen auf Ihrem PC eingeschlossen. Der ADK Bewertungsfragen oder andere Testtools können Sie die Auswirkungen Leistungseinbußen in Ihrem PC und Akkulaufzeit quantifiziert.

Behalten Sie im Hinterkopf, denen Sie keinen verzichten Leistung, um ein hohes Maß an Schutz haben. Viele Modul erstklassige Produkte führen außerdem sehr gut in die Bewertung.

![Wichtige](images/note-important.gif)**wichtige**&nbsp;&nbsp;&nbsp;der ADK Bewertung misst nicht die Sicherheitsebene von Modul Produkte bereitgestellt. Viele dritte Berichte messen und vergleichen die Effektivität der verschiedenen Modul Pakete.

## <a name="recommended-goals"></a>Empfohlene Ziele

Um eine hervorragende Internet Explorer-Erfahrung zu übermitteln, sollte ein PC die folgenden Zielsetzungen:

| **Szenario**                                                        | **Tablet (CS)** | **Konvertiert werden kann.** | **Notizbuch** | **AIO**   |
|---------------------------------------------------------------------|-----------------|-----------------|--------------|-----------|
| IE-Sicherheit Software Auswirkungen Assessment: Seite anzuzeigen (Sekunden) | &lt;= 1,5       | &lt;0,5       | &lt;0,5 =    | &lt;= 0,5 |
| IE-Startup (Benutzer Perceived)(seconds)                                | &lt;= 1.0       | &lt;= 0,5       | &lt;= 0,5    | &lt;= 0,5 |

## <a name="validation-and-testing"></a>Hinweise zur Überprüfung und testen

Sie können das Windows-Bewertungen Toolkit zum Verbessern der Leistung des Computers über Mindestanforderungen hinaus verwenden. Windows-Analysen, die im Zusammenhang mit Internet Explorer gehören:

<dl>
<dt>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<strong>Internet Explorer zum Starten des Performance-Bewertung</strong></dt>
<dd>
<p>Enthält Komponenten, die die Zeit auswirken können, die benötigt wird, um Internet Explorer zu starten. Die Bewertung misst die Zeit bis zur vollständig eine leere Seite rendern, einschließlich die Ladezeit der der IExplore.exe verarbeiten und die Frame-Erstellung und Registerkarte Intervalle. Auch die Auswirkung des alle Erweiterungen, Add-Ins und Symbolleisten auf dem System installierte gemessen. Es ist keine Netzwerk- oder Browser-Leistung gemessen.</p>
</dd>
<dt>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<strong>Internet Explorer Software Sicherheitsrisiko Bewertung</strong></dt>
<dd>
<p>Measures Aspekte von Internet Explorer, die vom Modul apps und andere Browser-add-ins in der Regel betroffen sind. Die Bewertung misst die Auswirkungen der Sicherheits-Software auf die Anzeigedauer, CPU-Zeit und Ressourcenverwendung von Internet Explorer.</p>
</dd>
</dl>

### <a name="internet-explorer-security-software-impact-assessment"></a>Internet Explorer Software Sicherheitsrisiko Bewertung

IE Software Auswirkungen Bestandsaufnahme ist für die direkte Verwendung relevantere browsing Szenarien messen und konzentriert sich auf die Modul-Auswirkung auf die Browser Internet Explorer-Leistung.

Modul und Browser-add-ins haben einen großen Einfluss auf der Windows-Erfahrung. Durch die Anzahl der Bewertung, die deren Einfluss widerspiegeln erweitern, helfen wir Ihnen ein besseres Verständnis von deren allgemeine Einfluss auf die Benutzer zu entwickeln.

![](images/note-regular.gif)**Hinweis**beachten&nbsp;&nbsp;&nbsp;es wird empfohlen, dass Sie ihre Ergebnisse zu einem bereinigten Windows-Abbild (mit Windows Defender ausgeführt) auf dem gleichen System, um die Auswirkungen von der ausgewählten 3rd Party Modul Lösung eingeführt quantifiziert immer vergleichen.

Dieses Assessment behandelt Seitennavigation und JavaScript-Leistung, beide werden an das Browsen Zentraladministration. Es wird eine Seite, um eine Anzahl von Leistungskennzahlen Engpässe Übung gestartet:

-   Erhebliche Verwendung von JavaScript

-   Erhebliche Netzwerkauslastung

-   Komplexe Formatierung Seite

Wenn die Analyse durchführen, beziehen sich auf vollständige Seite Load Dauer und verwendbar Seite Metriken:

-   Laden der Seite Dauer abschließen

-   Gibt die gesamte Zeit, die verstreicht, bevor die Test-Webseite in Internet Explorer vollständig geladen ist. Die Dauer von Laden der Seite gemessen, bis Internet Explorer CPU-Auslastung relativ stabil ist.

-   Laden der Seite zu verwendbar

-   Schätzt die Zeit, die zwischen dem Laden der Seite verstrichen ist und wann die Seite verwendbar ist. Diese Metrik basiert von Leistungsereignisse.

Mehrere Authentifizierungstypen Auswirkungen können ermittelt werden:

- **Netzwerk- und Störungen** wird in der Regel im Netzwerk Anforderung Metriken und insgesamt CPU-Auslastung angezeigt.

- **JavaScript Interferenzen** können in JavaScript metrischen oder Netzwerk-Anforderung Metriken anzeigen.

- **Visual Störungen** wird im Dokument zeichnet Metriken.


# <a name="delivering-a-great-media-experience"></a>Spielt eine hervorragende Media-Erfahrung

Eine außergewöhnliche Media-Wiedergabe und Erfassung wünschen ist Störung frei, geringe Latenz und Energie an. Sie können die Leistung der Medienwiedergabe, Real-Time Communications und Webcam Capture Szenarien auf Ihren Windows-Geräten mit Tests in den ADK und HLK bewerten.

## <a name="considerations"></a>Erwägungen

Ein Gerät, das bietet eine hervorragende Medien Erfahrung bietet Störung frei Audio, Video Störung frei und Long-Akkulaufzeit.


### <a name="glitch-free-audio"></a>Audiogenuss

Um Audiogenuss zu erzielen, müssen keine akustische Knackgeräusche oder Diskontinuitäten in den Audiostream vorhanden sein. Für die Kommunikation in Echtzeit Szenarien muss die Audiodaten Störung frei und außerdem erfüllen den gleichen geringer Latenz, den Benutzer fest, wenn auf einem herkömmlichen Telefon sprechen.

Einige audio-Fehler werden während der Verarbeitung der audio-Samples verursacht, bevor sie an den Audiotreiber gerendert werden. Die Media-Pipeline wird mithilfe von Ereignissen sich diese Probleme mit Event Tracing for Windows (ETW) instrumentiert werden. Tools wie Media eXperience Analyzer (MXA) können verwendet werden, um die Ursache für Probleme einzuschränken.

### <a name="glitch-free-video"></a>Video Störung frei

Es gibt zwei Arten von Videoqualität:

-   *Zeitliche Qualität* ist fehlerhaft, wenn die Medien Engine Pipeline angehalten ist und eine Diskontinuität bei der Verarbeitung der Videoframes. Videoframes gelöscht oder verspätet präsentiert werden, und möglicherweise für das menschliche Auge erkennbar.

    Beispiele für zeitliche video-Fehler sind Verzögerungen in der Hardware und die Pipeline Threads, die von Engpässen oder höhere Priorität eingeführt werden auf dem System funktionieren.

    Zeitliche Qualität wirkt sich auf:

    -   Schneller Start. Wie schnell das Video lädt und beginnt, wiedergegeben werden sollen.

    -   A/v-Synchronisierung. Gibt an, ob die Audio- und Videostreams starten und gleichzeitig beenden und derselbe beibehalten haben.

    -   Seek Wartezeit. Wie schnell zur nächsten Folie gewechselt, und reverse-Funktionen auf User-Befehle reagieren.

        -Pipelines für die Wiedergabe und Erfassung instrumentiert mit video ablageereignissen Störung und Daten, die verwendet werden kann, um die zeitliche Videoqualität zu messen. Die Pipeline nutzt die Multimedia Class Scheduler (MMCSS)-Dienst. Dieser Dienst ist in der Planer integriert und wird sichergestellt, dass dringende Verarbeitung in der Pipeline Media priorisiert Zugriff auf die CPU-Ressourcen empfängt. Multimedia-apps können ohne das Verweigern CPU-Ressourcen zu apps mit niedrigerer Priorität als einen Großteil der CPU wie möglich. Erfahren Sie mehr über MMCSS auf [MSDN](http://msdn.microsoft.com/en-us/library/windows/desktop/ms684247(v=vs.85).aspx) (https://msdn.microsoft.com/en-us/library/windows/desktop/ms684247 (v=vs.85).aspx).

-   *Räumliche Qualität* bezieht sich auf den Videostream während der Medienwiedergabe oder wenn der Inhalt codiert ist beschädigt. Der Decodierung oder video Verarbeitung Testphase Videowiedergabe können ein horizontale oder vertikale oder Makro Blockierung verursachen.

### <a name="long-battery-life"></a>Lange Akkulaufzeit

Windows unterstützt Hardware-Offloading und einige andere Power einsparungen Features, mit die Sie Mitbewerberprodukten Akkulaufzeit während Media Arbeitslasten übermitteln können. Dazu zählen:

-   *Abladung von audio* - Nutzung audio-Offloading auf Plattformen, die Offloading-Unterstützung verfügen.

-   *Mit mehreren Ebene Überlagerung (MPO)* - verschiedene Chipsätze bieten Unterstützung für MPO dem video Verarbeitung auf Hardware verschiebt. Diese Funktion verringert etwa 50 %, was energieeinsparungen bei und erhöhte Störung von Standorten Bandbreite Arbeitsspeicherbedarf.

-   *[Direkte kippen (https:/msdn.microsoft.com/en-us/library/windows/hardware/dn653329(v=vs.85).aspx)](https://msdn.microsoft.com/en-us/library/windows/hardware/dn653329(v=vs.85).aspx)
    & [Unabhängige kippen](http://msdn.microsoft.com/en-us/library/windows/hardware/dn457716(v=vs.85).aspx) (https://msdn.microsoft.com/en-us/library/windows/hardware/dn457716 (v=vs.85).aspx)* -
    Bypassess der DWM und spiegelt Flächen direkt an die GPU Arbeitsspeicher Kopien Vollbild Videowiedergabe entfernen.

-   *Niedrige Refresh Rate Wiedergabe* - Media-Modul apps auf das kleinste Vielfache die Aktualisierungsrate löschen, die der Bereich in der Vollbildansicht unterstützt. Beispielsweise bei der Wiedergabe von Videoinhalten in der app XBox Video 24fps auf einem System, die ein LCD-Anzeige verfügt, die Aktualisierungsrate 48 hz unterstützt, wird die Pipeline Media die Aktualisierungsrate aus 60 bis 48 hz gelöscht werden.

-   *Batching* - basierend im Vollbildmodus Wiedergabemodus, Medien Engine, apps Prozess und die Warteschlange auf mehrere Frames dargestellt werden. 

Medien Erfahrung Analyzer, ein Analyse-Tool können Sie überprüfen, ob die oben aufgeführten Funktionen beschäftigt sind. Darüber hinaus können Sie zum Korrelieren Stromverbrauchs generierte instrumentiert Stromversorgungen mit Systemaktivitäten in einem ETW-Protokoll erfasst.

![Diagramme der Power-Daten und Systemaktivitäten Media Oberfläche Analyzer angezeigt.](images/weg-mxa-screen-regions-power-data-system-activity.png)

### <a name="impact-of-third-party-drivers-and-apps"></a>Auswirkung der Treiber von Drittanbietern und apps

Drittanbieter-Treiber und apps sind häufig zum Ausführen einer Aufgabe schnell und für diese Aufgaben vorgesehen. Sie möglicherweise mit einer Priorität ausgeführt, durch die Ressource Einschränkungen für die Media-Pipeline wird. In einigen Fällen sind Treiber von Drittanbietern, die unter Versendung Ebene für längere Zeit ausgeführt (10 ms) und Dienstprogramme schwer code in anderen Fällen die Priorität der ihre Threads an, die in Priorität 22 ausgeführt. Gemäß der folgenden Überprüfung und testing im Abschnitt können Drittanbieter-apps und Treiber Verzögerungen in der Pipeline Media einführen und die Audio- und Videodaten Probleme aufgeführt.

## <a name="recommended-goals"></a>Empfohlene Ziele

Um eine hervorragende Media Wiedergabe zu übermitteln, sollte ein Windows-Gerät die folgenden Ziele erfüllen. Diese Leistung und die Qualitätsziele gelten für Windows Store-apps und desktop-apps. Sie gelten für Posteingang und Wiedergabe von Drittanbieter-apps.

|   Metrische Priorität   |   Metrisch                                                   | Außergewöhnliche          |
|---------------------|------------------------------------------------------------|----------------------|
| 0                   | Audio-Fehler bei der Wiedergabe stabilen Zustand                | 0                    |
| 0                   | Video-Fehler und Daten löscht während der Wiedergabe stabilen Zustand | 0                    |
| 1                   | Audio und video Fehler Löscht Daten beim Starten oder beenden  | 0                    |
| 1                   | A/v-Synchronisierung                                           | &lt;25 ms           |
| 1                   | ISR/DPC Dauer                                           | &lt;25 Mikrosekunden |
| 2                   | Wartezeit beim Starten                                            | &lt;1 Sekunde           |
| 2                   | Seek Wartezeit                                               | &lt;500 ms          |

Um bieten eine hervorragende Echtzeitkommunikation und erfassen wünschen, ein Windows-Gerät sollte die Leistungsziele beschrieben, in der Windows-Hardware und Zertifizierung (HCK) getestet, die in die Überprüfung aufgelistet und im nachfolgenden Abschnitt testen.

## <a name="validation-and-testing"></a>Hinweise zur Überprüfung und testen

Hardware Lab Kit (HLK) können Sie sicherstellen, dass Ihr Windows-Gerät Windows erfüllt.

Im Zusammenhang mit der Medienwiedergabe HLK Tests umfassen Folgendes:

<dl>
<dt>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<strong>HD-Wiedergabe Störung frei-Test</strong></dt>
<dd>
<p>Gibt wieder 1080p Videoinhalten und meldet die Anzahl von Audio- und zeitliche Probleme aufgeführt. Bei diesem Test kann optional verbose Leistung Spuren, die analysiert werden können Analysis Leistungstools generieren, wie Analyzer Medienfunktionen.</p>
</dd>
</dl>

Das Windows Assessment Toolkit können zur Verbesserung der Leistung des Geräts Windows über Mindestanforderungen hinaus. Windows-Analysen, die im Zusammenhang mit der Medienwiedergabe umfassen: 

<dl>
<dt>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<strong>Streaming Media-Leistung</strong></dt>
<dd>
<p>Misst die streaming Media Qualität HTML5 Videowiedergabe in Internet Explorer. Ausführliche ETW-Protokolle enthalten Informationen für die Diagnose von die Ursache für die identifizierten des Tests Leistungsprobleme erforderlich. Es wird empfohlen, dass Sie den streaming-Server auf einem System eingerichtet, die sich auf dem Client unterscheidet.</p>
<ul>
<li>
<p>Zweites System im Netzwerk zum Hosten von streaming Serverprozess erfordert</p>
</li>
<li>
<p>Befolgen Sie die Anweisungen in [A Remote Server einrichten für die Bewertung der Streaming Media-Leistung](http://msdn.microsoft.com/en-us/library/windows/hardware/hh825310.aspx) auf MSDN (https://msdn.microsoft.com/en-us/library/windows/hardware/hh825310.aspx) an den Server einrichten.</p>
</li>
<li>
<p>Ändern Sie Parameter zur Bewertung die Serverkonfiguration entsprechend. Beispiel: ![Settings in Windows Assessment Konsole (WAC) für die Bewertung der Leistung der streaming Media-Server.](images/weg-wat-settings-streaming-media-performance.png)</p>
</li>
</ul>
</dd>
<dt><strong>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Lokale Media Wiedergabe Energie Effizienz Arbeitslast</strong></dt>
<dd>
<p>Misst die Akkulaufzeit während der Wiedergabe HTML5 1080p h. 264-Inhalt.</p>
</dd>
</dl>


### <a name="analyzing-audio-and-video-glitches"></a>Analysieren von Audio- und Probleme

Medien Erfahrung Analyzer gibt ein Trace Visualisierungstool im Microsoft Download Center. Hiermit können Sie die Ursache des zeitliche Qualitätsprobleme ermitteln. Die allgemeine Herangehensweise an Störung Analysis kann in vier Schritte unterteilt werden:

1.  Erfassen eines ETW melden Sie sich mit Windows Performance Aufzeichnung (WPR) während einer Media Wiedergabe Arbeitslast.

2.  Vergrößern Sie die Audio- und Videodaten Störung oder Daten ablageereignissen.

3.  Suchen Sie nach Engpässen oder unerwarteten Verzögerungen bei der CPU, GPU, Datenträger oder Netzwerk.

4.  Sammeln von unterstützenden Informationen wie Stapel und Analysen Screenshots aufrufen.

5.  Benachrichtigen Sie und erkundigen Sie sich bei dem Besitzer der Komponenten Verzögerungen oder Fehler einführen.

Audio-und Videodaten setzt oder Fehler in drei Kategorien aufgeschlüsselt: downstream, mitten und Upstream-.

#### <a name="downstream"></a>Downstream

Tritt auf, wenn die Quelle nicht von der Festplatte oder Netzwerk schnell genug in Echtzeit decodieren und Rendering zu lesen kann. Beispiel des Datenträgers möglicherweise mithilfe eines harte Seitenfehlers verursachter werden und daher Beispiele können vom Datenträger in Echtzeit oder schneller nicht gelesen werden. Häufig Blockieren der Quelle Seite erzeugt Daten ablageereignissen.

#### <a name="midstream"></a>Mitten

Entschlüsseln von einem geschützte Stream Verzögerungen, Decodierung ist langsamer als die in Echtzeit oder verzögert die Frames auf der GPU Präsentation. Dies kann durch einen Engpass in der Decoder Hardware- oder oder anderen Systemaktivitäten diese Medienkomponenten stört verursacht werden.

#### <a name="upstream"></a>Upstream-

In dieser Phase die Pipeline decodiert und präsentiert Rahmens hat, aber möglicherweise Verzögerungen bei der Desktop-Manager (DWM) oder den Graphics-Stapel. Upstream-Engpässe können auftreten, wenn die GPU angeschlossenen oder bei langsamen Speicher übertragen wird. Diese Medien Erfahrung Analyzer Screenshot ist ein Beispiel dafür, wie zum Visualisieren ein Upstream-Engpass in ETW aufgezeichnet.

![Visualisierung in Media bemerken Analyzer von einer Upstream-Engpass mit Bereichen des Bildschirms zur Identifikation markiert.](images/weg-mxa-screen-visualization-upstream-bottleneck.jpg)

<dl>
<dt>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Ein Bereich</dt>
<dd>
<p>Die vertikalen Linien sind video Störung vom Media-Modul, das ausgelöst wird.</p>
</dd>
<dt>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Systemsteuerung B</dt>
<dd>
<p>Dieses Diagramm zeigt eine der GPU Knoten bei 99 % Auslastung ausgeführt wird.</p>
</dd>
<dt>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Systemsteuerung C</dt>
<dd>
<p>Jede Zeile zeigt die GPU DMA Vorgänge auf den einzelnen Knoten. Der Knoten in der Mitte mit den Ereignissen grün markiert sind Transfers Memory.</p>
</dd>
<dt>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Systemsteuerung D</dt>
<dd>
<p>Dieses Diagramm zeigt den Betrag in der GPU CPU-Warteschlange beim Verarbeiten der DWM Vorgänge aufgewendete Zeit. Dies ist ein Beispiel einer Upstream-Flasche Pfeilende, wobei die GPU ausgelastet Transfers Memory Verarbeitung und Vorgänge, die in Echtzeit-Anforderung der Präsentation die Videoframes auf dem Bildschirm zu rendern.</p>
</dd>
</dl>

Media eXperience Analyzer können eine Analyse und Visualisierung Leistungstool, Analysieren von Problemen mit der Leistung auf Ihrem Gerät Windows Media. Media eXperience Analyzer enthält spezielle Ansichten für die Diagnose von Leistungsproblemen bei der Aufzeichnung und Wiedergabe Szenarien.
Häufige Ursachen für Audio- und Probleme, die mit diesem Tool Sie finden unter anderem:

<dl>
<dt>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Langer Interrupt Service Routinen (ISR) und zurückgestellte Prozeduraufrufe (DPC)</dt>
<dd>
<p>Eine *ISR* geschieht, wenn die Interruptverteiler überträgt die Steuerung an eine Gerät Treiber Routine Wenn ein Gerät einen Interrupt ausgegeben. Führen im Modell Windows e/a ISRs bei einer hohen Geräte Interrupt Request Level (IRQL), so, dass sie so wenig Arbeit wie möglich, auf niedrigerer Ebene Interrupts unnötig Blockierung vermeiden ausführen. Eine ISR Warteschlangen in der Regel eine DPC, der mit einem niedrigeren IRQL, zum Ausführen der restlichen Interrupt Verarbeitung ausgeführt wird. DPCs sollte nicht mehr als 100 Mikrosekunden führen und ISRs sollte nicht mehr als 25 Mikrosekunden.</p>
<p>Zusätzlich zu anderen System leistungsbezogene können langer ISRs und DPCs Verzögerungen in das audio-Modul, die audio-Fehler führen.
Eine ISR oder DPC für mehr als 1 bis 3 ms ausführen kann Medien auf einem System beeinträchtigen. Wie langer ISRs und DPCs können häufige ISRs und DPCs (ein ISR/DPC Ansturm) ähnliche Effekte auf die Leistung haben.
Solche ISR und DPC Probleme werden in der Regel im Netzwerk, Speicherung und Graphics-Treiber gefunden. Die Bewertung generiert eine Warnung für langer ISR/DPCs zwischen 1 und 3 ms und einen Fehler für mehr als 3 ms dauern.</p>
</dd>
<dt>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Kernel-Arbeitsthreads Versendung Ebene ausgeführt</dt>
<dd>
<p>Zusätzlich zur DPCs, möglicherweise einige Kernel-Arbeitsthreads auch Versendung Ebene ausgeführt werden (IRQL = 2). Diese können auch verlangsamen, die in audio-Fehler. Suchen Sie zum Erkennen von solchen Verzögerungen für niedrige Priorität System, ausführen ununterbrochenen für lange dauern threads ohne wird abgebrochen.</p>
</dd>
</dl>

Die folgenden Anweisungen Checklisten sollte in OEM Entwurf und Testphasen der neuen Windows-Geräte integriert werden.

Power Einsparungen Anleitung Prüfliste

-   Verwenden Sie Hardware-Offloading und niedrigen Refresh Rate Bereiche

-   Optimieren der Einstellungen von Adaptive Beleuchtung Steuerelement (CABC)

-   Optimieren der Leistung von Standardeinstellungen für Bildschirm Helligkeit

-   Entfernen von Printf Debug-Protokollierung von Treibern

-   Windows ADK Energie Effizienz lokale Videowiedergabe Assessment ausgeführt werden soll, vergleichbare Energie-Effizienz testen Sie Tool oder eine vergleichbare Test Measure Verbrauchern Verwendungsszenarien und Umgebungen

-   Minimieren Sie extra fette Hintergrundaktivitäten bei wichtige Media-Szenarios

-   Wichtige Medieninhalten auf AC und DC testen

Prüfliste für die Medienwiedergabe Anleitungen Störung frei

-   Stream Premium Inhalt mit HDMI-Ausgabe an TV

-   Wiedergeben Sie Premium-Inhalte auf DLNA TV Wiedergabe zu verwenden und Miracast

-   Vergewissern Sie sich Videos Xbox und Xbox Musik Erfahrungen

Anleitung Störung frei Prüfliste für die Echtzeitkommunikation und Webcam Erfassung

-   Optimieren der Firmware zum Optimieren der Leistung von Audio- und Videoqualität Verarbeitung

-   Überprüfen der Front- und Back-Kameras verwenden Posteingang & 3rd Party Capture-apps

-   Können Sie mithilfe der HLK und Skype/Lync Zertifizierung Tests eine außergewöhnliche-Erlebnis

-   Verweisen Sie auf das Dokument Hardware Windows Engineering Anleitungen ausführliche Hilfestellungen zur Behebung räumliche Qualitätsprobleme wie Kameras erfassen verschwommen oder dunkle Bilder

## <a name="tools-and-technical-reference"></a>Tools und technische Referenz

<!--No content provided here in the original Word file.-->

### <a name="media-experience-analyzer"></a>Medienfunktionen Analyzer (engl.)

Medien Erfahrung Analyzer ist die empfohlene Performance Analysis-Tool für die Diagnose von Audio- und Probleme. Dieses Tool ist ein Tool zur Analyse von Leistung, spezialisierte Ansichten für die Diagnose von Diskontinuitäten in der multimedia Speicherplatz und Verzögerungen bei der Grafiken Stack bereitstellt. Sie können eine größere Gruppe von Analysten diagnostizieren zeitliche Leistung und Qualität ermittelte durch HCK Tests oder manuelle Tests Leistung. Medien Erfahrung Analyzer verarbeitet ETW-ablaufverfolgungen während der Ausführung von Audio- und Videowiedergabe Szenarien erfasst.
Das Tool Visualisierung eine Breite Palette von Kernel- und Benutzermodus-Ereignissen, die während der Tracingsitzung ausgelöst. Sie können auf einfache Weise korrelieren Instrumentationsdaten aus verschiedenen Komponenten und führen Ursachenanalyse. Dieses Tool nicht konkrete Lösungen für die identifizierten Problemen vorzuschlagen, aber es bietet ausführliche Daten und Beweis für Entwickler, Partnern oder Komponente Besitzer.

| Titel der Ressource                                                                 | Inhaltstyp       | Beschreibung                                                                                                                                                                                                                                                                                                                                                                                                                                     | Verknüpfung
|--------------------------------------------------------------------------------|--------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Optimieren von Windows-Geräten                                                     | Video und PowerPoint-Folien | Führt die Leistungstools und Testkits zum Optimieren der Leistung auf Windows-Geräten verwendet. In dieser Übersicht legt die Grundlagen zum Erstellen von Windows-Gerät, die fast-Boot und Browser starten, leicht lesbare und reaktionsschnelle Benutzeroberfläche und Störung kostenlose multimedia-Erlebnis bietet.                                                                                                                                                                   | [Channel 9](http://channel9.msdn.com/Events/WinHEC/2015/OWD204) (http://channel9.msdn.com/Events/WinHEC/2015/OWD204) |
| Übung WinHEC Medien                                                               | Doc                | WinHEC Media Labor, dass spielt eine geringe Latenz und Störung ausfallsichere Erfahrung, Audio- und Videodownloads Wiedergabequalität Störung kostenlose Wiedergabe Test in Hardware Lab Kit (HLK) erörtert, wie Audio überprüfen erfolgt.                                                                                                                                                                                                                               | [Channel 9](http://channel9.msdn.com/Events/WinHEC/2015/OWDHOL301) (http://channel9.msdn.com/Events/WinHEC/2015/OWDHOL301) |
| Übersicht über die Batterie Lebensdauer                                                          | Video und PowerPoint-Folien | Übersicht über die verschiedenen Aspekte der entwerfen und Versand eines Systems bietet, die eine lange Akkulaufzeit, wenn das System auf und in dem Standbymodus ist. Themen umfassen: Modellierung und optimieren, die Bodenfläche Power während der Bildschirm auf optimieren und Strom Standby, Standby Modi: verbunden Standby (CS), und modernen Standby (MS), Energie Schätzung Engine und reporting vor dem Laden des Auswirkungen Software auf Akkulaufzeit und Einführung in die Batterie Bildschirmschoner UX | [Channel 9](http://channel9.msdn.com/Events/WinHEC/2015/OWD202) (http://channel9.msdn.com/Events/WinHEC/2015/OWD202) |
| Media Wiedergabe Apps – Audio und Video-Leistung                              | Artikel            | Wenn Sie eine app entwickeln, die Audio- und Videodateien verwendet, sollten Sie einige wichtige Leistungsaspekte sein. In diesem Dokument werden die wichtigsten Bereiche für die erste Medienwiedergabe leistungsstarke in Windows Store-apps mithilfe von JavaScript zusammengefasst.                                                                                                                                                                                               | [MSDN](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh848311.aspx) (https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh848311.aspx) |
| Optimieren der Videowiedergabe (Windows Store-apps mit JavaScript und HTML) | Artikel            | Enthält Informationen über das MsIsLayoutOptimalForPlayback-Attribut.                                                                                                                                                                                                                                                                                                                                                                          | [MSDN](http://go.microsoft.com/fwlink/?LinkId=311550) (https://msdn.microsoft.com/library/windows/apps/hh452785.aspx) |
| Verarbeitung von Audiosignalen Hardware übergeben                                            | Artikel            | Enthält Informationen zu den audio-Verschiebung in Windows 8 und wie diese Unterstützung Audiotreiber verfügbar machen kann Audiofunktionen an den Windows-audio-Stapel übergeben.                                                                                                                                                                                                                                                                         | [MSDN](http://go.microsoft.com/fwlink/?LinkId=311551) (https://msdn.microsoft.com/en-us/library/windows/hardware/dn302038 (v=vs.85).aspx) |

# <a name="delivering-a-great-app-experience"></a>Übermitteln eine großartige app-Benutzeroberfläche

<!--No content provided here in the original Word file.-->

## <a name="building-fast-fluid-and-power-efficient-windows-store-apps"></a>Erstellen Sie fast, Unze und Power effiziente Windows Store-apps

Spielt eine hervorragende Windows-Erfahrung ist nicht auf Firmware und Hardwarekomponenten beschränkt. Die Qualität der apps ist eine Hauptkomponente in eine umfangreiche Windows-Erfahrung bereitstellen. In diesem Abschnitt sind unsere Empfehlungen und Aspekte zur app-Entwicklung.

### <a name="tools-and-technical-reference"></a>Tools und technische Referenz

| Titel der Ressource                                                                         | Inhaltstyp | Beschreibung                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         | Link herunterladen
|----------------------------------------------------------------------------------------|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Windows 8-Apps mit HTML-, CSS- und JS Programming MS Press                             |  Book        |  Kostenloses online Buch, das mehrere Zeiger zum Entwerfen und Erstellen der Windows-Apps mit einer guten Leistung hat                                                                                                                                                                                                                                                                                                                                                                                                                                           |  [MSDN](http://blogs.msdn.com/b/microsoft_press/archive/2012/10/29/free-ebook-programming-windows-8-apps-with-html-css-and-javascript.aspx) (http://blogs.msdn.com/b/microsoft\_press/archive/2012/10/29/free-ebook-programming-windows-8-apps-with-html-css-and-javascript.aspx) |
| Erstellen von Windows Store-apps mithilfe von HTML5 hohe Leistung                               |  Video       |  ERSTELLEN Sie Video zum Erstellen von Windows Store-apps mithilfe von HTML5 hohen Leistung                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |  [Channel 9](http://channel9.msdn.com/Events/Build/BUILD2011/APP-162T) (http://channel9.msdn.com/Events/Build/BUILD2011/APP-162T) |
| 50 Leistung tricks So machen Sie Ihre Windows Store-apps und Websites mithilfe von HTML5 schneller     |  Video       |  ZUSAMMENSTELLEN Sie Video für 50 Performance Tricks, stellen Sie Ihre Windows Store-apps und -Websites mithilfe von HTML5 schneller                                                                                                                                                                                                                                                                                                                                                                                                                                                  |  [Channel 9](http://channel9.msdn.com/Events/Build/BUILD2011/PLAT-386T) (http://channel9.msdn.com/Events/Build/BUILD2011/PLAT-386T) |
| Leistung – empfohlene Vorgehensweisen für Windows Store-apps mit C++ C\#, und Visual Basic     |  Artikel     |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |  [MSDN](http://msdn.microsoft.com/en-us/library/windows/apps/Hh750313.aspx) (https://msdn.microsoft.com/en-us/library/windows/apps/Hh750313.aspx) |
| Allgemeine bewährte Methoden für die Leistung                                                 |  Artikel     |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |  [MSDN](http://msdn.microsoft.com/en-us/library/windows/apps/hh994633.aspx) (https://msdn.microsoft.com/en-us/library/windows/apps/hh994633.aspx) |
| Leistung – empfohlene Vorgehensweisen für Windows Store-apps mithilfe von JavaScript                     |  Artikel     |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |  [MSDN](http://msdn.microsoft.com/en-us/library/windows/apps/hh465194.aspx) (https://msdn.microsoft.com/en-us/library/windows/apps/hh465194.aspx) |
| Analysieren der Leistung von Windows Store-apps                                        |  Artikel     |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |  [MSDN](http://msdn.microsoft.com/en-us/library/windows/apps/hh696636.aspx) (https://msdn.microsoft.com/en-us/library/windows/apps/hh696636.aspx) |
| Gewusst wie: Verbessern der Leistung in Ihrer app im Metro Formatvorlage                                     |  Artikel     |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |  [MSDN](http://blogs.msdn.com/b/windowsappdev/archive/2012/04/03/how-to-improve-performance-in-your-metro-style-app.aspx) (http://blogs.msdn.com/b/windowsappdev/archive/2012/04/03/how-to-improve-performance-in-your-metro-style-app.aspx) |
| Bekämpfung Leistungskiller: allgemeine Leistungsprobleme im Zusammenhang mit Metro formatieren apps        |  Artikel     |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |  [MSDN](http://blogs.msdn.com/b/windowsappdev/archive/2012/04/05/tackling-performance-killers-common-performance-problems-with-metro-style-apps.aspx) (http://blogs.msdn.com/b/windowsappdev/archive/2012/04/05/tackling-performance-killers-common-performance-problems-with-metro-style-apps.aspx) |
| Zeitpunkt und Leistung APIs                                                            |  Artikel     |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |  [MSDN](http://msdn.microsoft.com/en-us/library/windows/apps/hh767418.aspx) (https://msdn.microsoft.com/en-us/library/windows/apps/hh767418.aspx) |
| Analysieren von Speicherverwendung in Windows Store-apps                                           |  Artikel     |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |  [MSDN](http://msdn.microsoft.com/en-us/library/windows/apps/jj819177.aspx) (https://msdn.microsoft.com/en-us/library/windows/apps/jj819177.aspx) |
| Analysieren die Codequalität der Windows Store-apps mit Visual Studio-Code-Analyse      |  Artikel     |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |  [MSDN](http://msdn.microsoft.com/en-us/library/windows/apps/hh441471.aspx) (https://msdn.microsoft.com/en-us/library/windows/apps/hh441471.aspx) |
| HTML-Performance-Tool in Visual Studio 2012-Update 2                                   |  Tool        |  Dieses Tool ist, damit Entwickler Lösung von Problemen mit Reaktionsfähigkeit der Benutzeroberfläche (Warum wird meine Benutzeroberflächen-Thread blockiert?) und Wartezeit in visual Updates vorgesehen (Meine Benutzeroberflächen-Thread reagiert jedoch optischen Änderungen werden dauert länger als erwartet angezeigt). Dazu Freigabe-einem ganzheitlichen Satz von "Ereignisse" (logische Kategorisierung der CPU-Auslastung), die eine bestimmte Zeitspanne, die sowohl die Anwendungslogik als auch Plattform enthält aufgetreten Verhalten, die im Namen der Anwendung (z. B. Layout, GC, Netzwerk-Anforderung, Bild entschlüsselungszeit) aufgetreten sind.|  [Microsoft.com](http://support.microsoft.com/kb/2797912) (https://support.microsoft.com/en-us/kb/2797912/) | 
| Performance-Analyzer für HTML5-apps                                                    |  Tool        |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |  [MSDN](http://msdn.microsoft.com/en-us/library/windows/apps/jj553524.aspx) (https://msdn.microsoft.com/en-us/library/windows/apps/jj553524.aspx) |
| Windows-App-Zertifizierungskit                                                          |  Kit         |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |  [MSDN](http://msdn.microsoft.com/en-US/windows/apps/jj572486) (https://dev.windows.com/en-us/develop/app-certification-kit) |
| HTML-ListView Optimierung Leistungsbeispiel                                            |  Codebeispiel |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |  [MSDN](http://code.msdn.microsoft.com/windowsapps/ListView-performance-39fb71f0) (https://code.msdn.microsoft.com/windowsapps/ListView-performance-39fb71f0) |
| Optimieren der Leistung der Präsentation – DXGI Swapchain Drehung Beispiel                     |  Codebeispiel |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |  [MSDN](http://code.msdn.microsoft.com/windowsapps/DXGI-swap-chain-rotation-21d13d71) (https://code.msdn.microsoft.com/windowsapps/DXGI-swap-chain-rotation-21d13d71) |
| XAML-ListView Beispielpaket                                                              |  Codebeispiel |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |  [MSDN](http://code.msdn.microsoft.com/windowsapps/XAML-ListView-sample-pack-0ec6b60f) (http://code.msdn.microsoft.com/windowsapps/XAML-ListView-sample-pack-0ec6b60f) |

## <a name="analyzing-windows-store-apps-performance-with-the-adk"></a>Analysieren der Leistung von Windows Store-apps mit der ADK

Windows Performance Analyzer in der ADK 8.1 werden neue Funktionen/Diagramme insbesondere die Leistung von Windows Store-apps analysieren vorgestellt.

| Titel der Ressource                                                          | Inhaltstyp | Beschreibung                                                                                                                                                                                                                                                       | Link herunterladen |
|-------------------------------------------------------------------------|--------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------|
| App-Leistung: Das geistige Modell für die Interaktion mit der Plattform     | Video        | In dieser Sitzung bietet ein besseres Verständnis der Interaktion zwischen Ihrer app und die Plattform. Mit diesem Wissen können Sie die Tools zum Beheben von Leistungsproblemen verwenden können                                                                                         | [Channel 9](http://channel9.msdn.com/Events/Build/2013/3-097) (http://channel9.msdn.com/Events/Build/2013/3-097) |
| App-Leistung: Planen von weniger als Neuentwurf Kosten                | Video        | In dieser Sitzung wird den Wert der bewerten und Entwerfen mit Korrektur im Hinterkopf früh im Entwicklungsprozess veranschaulichen. Sie lernen Tools und Techniken zum Bewerten der Leistung in beiden verwalteten apps, die XAML verwenden und apps, die HTML5 verwenden.               | [Channel 9](http://channel9.msdn.com/Events/Build/2013/2-098) (http://channel9.msdn.com/Events/Build/2013/2-098) |
| App-Leistung: Von UX-API für 5 Schlüsselszenarien                     | Video        | Diese Talk bietet ein Szenario-centric Einblick in die End-to-End zum hervorragende Performance 5 Schlüsselszenarien – Einführung, Resume, schwenken, Größe und Aussetzung bereit. Zur Verfügung stehenden Zeit, können wir erörtern Animationen, allgemeine Reaktionsfähigkeit und App-Installation. | [Channel 9](http://channel9.msdn.com/Events/Build/2013/3-099) (http://channel9.msdn.com/Events/Build/2013/3-099) |
| App-Leistung: Windows Performance Toolkit                        | Video        | In dieser Sitzung wird eine Einführung zu Windows Performance Toolkit (WPT). Wir werden das Tool leistungsstarken Funktionen durchlaufen. Zeigen wir Ihnen, wie Sie Ihre Windows Store-app zu analysieren, damit Sie Ihre Kunden verbessert werden kann                            | [Channel 9](http://channel9.msdn.com/Events/Build/2013/3-100) (http://channel9.msdn.com/Events/Build/2013/3-100) |


# <a name="delivering-an-image-with-high-quality-windows-store-apps"></a>Übermitteln ein Bild mit hoher Qualität Windows Store-apps

Weitere Informationen zum Bereitstellen von Windows Store-apps in Ihre Windows-Abbilder finden Sie unter Windows Engineering Guide für Apps und Store. Nachdem die apps bereitgestellt wurden, können Sie messen die Aktivierung und Mal jeder App auf das Bild geladen fortsetzen.

## <a name="recommended-goals"></a>Empfohlene Ziele

In der folgenden Tabelle zeigt die minimale Ziele für die app-Aktivierung, basierend auf unsere Research Benutzer.

| Szenario-Aufgaben                            | Ziel |
|----------------------------------------------|----------------------------|
| App-Aktivierungszeit (Einführung von kalt Zustand) | Zwischen 1 und 3 Sekunden |
| App Resume-Zeit                              | Zwischen 500 ms und 1 Sekunde |


## <a name="validation-and-testing"></a>Hinweise zur Überprüfung und testen

Das Windows Assessment Toolkit können Sie um die Leistung Ihrer Apps über Mindestanforderungen hinaus zu verbessern. Windows-Analysen, die im Zusammenhang mit apps Erfahrung umfassen:

-   Windows Store-apps Performance-Bewertung

-   Um die app Resume Zeiten zu messen, übernehmen Sie die Einstellungen empfohlen.

-   Um die app-Aktivierung (Einführung von kalt Zustand) Zeiten zu messen, stellen Sie sicher, dass Sie die Option "Neu starten jedes Windows Store-app" in den Parametern Assessment auswählen.

## <a name="tools-and-technical-reference"></a>Tools und technische Referenz

| Titel der Ressource                | Inhaltstyp | Beschreibung                       | Link herunterladen |
|-------------------------------|--------------|-----------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Windows Store-App-Leistung | Artikel      | Offizielle Bewertungsdokumentation | [MSDN](http://msdn.microsoft.com/en-us/library/windows/hardware/dn246955.aspx) (https://msdn.microsoft.com/en-us/library/windows/hardware/dn246955.aspx?f=255 & MSPPError = 2147217396) |


# <a name="delivering-a-great-energy-efficiency-experience-with-modern-standby"></a>Spielt eine hervorragende Energie Effizienz Erfahrung mit modernen Standby

Die Anzahl von Systemen, die mit geringer Leistung S0 im Leerlauf ist drastisch erhöhen. Wir erwarten, dass weitere Systeme verwenden die immer im Handumdrehen Power Modell anstelle der traditionellen S3/S4 Power-Modell.
Windows 10 werden einige Änderungen zur Unterstützung dieser Trend vorgestellt.

Das neue Power-Modell in Windows 10, aufgerufen, moderne Standby (MS) ermöglicht Systeme mit einem Festplattenlaufwerk und/oder eine Netzwerkkarte, die nicht alle der Anforderungen für Windows unterstützt 8.x verbunden dem Standbymodus weiterhin nutzen des Objektmodells Energiesparmodus im Leerlauf. *Windows 8.x Standby verbunden ist ein Spezialfall Windows 10 modernen Standby berücksichtigt werden können.*

Weitere Informationen zu diesem neuen Power schlagen Sie [Einführung modernen Standby-](https://connect.microsoft.com/site1304/Downloads/DownloadDetails.aspx?DownloadID=55993) (https://connect.microsoft.com/site1304/Downloads/DownloadDetails.aspx?DownloadID=55993), Whitepaper.

*Unterste zur Laufzeit im Leerlauf Plattform Zustand* (DRIPS) ist, wenn das System möglichst wenig Power möglich, durch die Bodenfläche Power begrenzt belegt. Bei deaktiviertem der Bildschirm verbundene standby-Sitzung beginnt, und das System wird über mehrere Phasen in einem Energiesparmodus verschieben. Wenn das System in den niedrigsten Power Zustand befindet, sagen wir, dass das System im DRIPS befindet. Das System wird nicht in DRIPS beim Ausführen von Aufgaben wie das Empfangen von e-Mails, aktualisiert live Kacheln mit neuen Inhalt, VoIP-Anrufe oder jede andere Hintergrundaufgabe, die Strom verbraucht entgegennehmen. Die mehr Zeit, die das System im DRIPS verbringt, bevor der Bildschirm wieder aktiviert ist, ist die Akkulaufzeit länger.

![Beachten Sie](images/note-regular.gif)**Hinweis**&nbsp;&nbsp;&nbsp;insgesamt modernen Standby Sitzungszeit = DRIPS Zeit + nicht DRIPS Zeit

Die Leistung WEG bietet hilfreiche Informationen zum:

-   Führen Sie vor, dass ein System hervorragende Akkulaufzeit verfügt, wenn im modernen Standby ausgeführt.

-   Identifizieren und Beheben von Problemen, die moderne Standby betreffen.

Weitere Informationen zur Funktionsweise der modernen Standby finden Sie hier:

| Titel der Ressource                                                       | Inhaltstyp | Beschreibung                                                                                                                                                                                                                                                                        | Link herunterladen |
|----------------------------------------------------------------------|--------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Einführung in die moderne Standby                                       | Whitepaper  | Das neue Power-Modell in Windows 10, aufgerufen, moderne Standby (MS) ermöglicht Systeme mit einem Festplattenlaufwerk und/oder eine Netzwerkkarte, die nicht alle der Anforderungen für Windows unterstützt 8.x verbunden dem Standbymodus weiterhin nutzen des Objektmodells Energiesparmodus im Leerlauf.                        | [Eine Verbindung herstellen](https://connect.microsoft.com/site1304/Downloads/DownloadDetails.aspx?DownloadID=55993) (https://connect.microsoft.com/site1304/Downloads/DownloadDetails.aspx?DownloadID=55993) |
| Übersicht über die Diskussion zu WinHEC 2015 Batterie Lebensdauer Optimierung                  | Video        | Modellieren und optimieren, schalten Sie die Bodenfläche Power während der Bildschirm eingeschaltet und standby optimieren                                                                                                                                                                                                 | [Channel9](http://channel9.msdn.com/Events/WinHEC/2015/OWD202) (http://channel9.msdn.com/Events/WinHEC/2015/OWD202) |
| WinHEC 2015 Akkulaufzeit: Debuggen von Power Problemen mit Standby Talk | Video        | Windows-10 CS/MS Power Übergang Flow, Systemintegration, Auswirkung Unterkomponenten auf System, Power Management für Speicher, Netzwerke und verbundene USB-Geräte, Prozess für die Analyse Batterie ausgleichen Probleme und SleepStudy und Windows Performance Analyzer (WPA) Tools (Übersicht) | [Channel9](http://channel9.msdn.com/Events/WinHEC/2015/OWD200) (http://channel9.msdn.com/Events/WinHEC/2015/OWD200) |
| WinHEC 2015 Akkulaufzeit: Debuggen von Power Problemen mit Standby Lab  | Übung-Dokument | Diese Übungseinheit wird gezeigt, wie die Energieeffizienz von einem Standby verbunden oder modernen Standby-System überprüfen                                                                                                                                                                        | [Channel9](http://channel9.msdn.com/Events/WinHEC/2015/OWDHOL304) (http://channel9.msdn.com/Events/WinHEC/2015/OWDHOL304) |
| Einführung in die verbundenen Standby                                    | Document     | Details der verbundenen standby wünschen, Software Auswirkungen von verbundenen Standby und hardwareanforderungen verbundenen Standby auf qualifizierten Systemen zu aktivieren.                                                                                                                       | [MSDN](http://go.microsoft.com/fwlink/?LinkId=306985) (https://msdn.microsoft.com/en-us/library/windows/hardware/dn481216 (v=vs.85).aspx) |
| Grundlegendes zu Standby verbunden                                      | Video        | In dieser Sitzung bietet eine Übersicht über verbundene Standby, einschließlich der wichtigsten Benutzerszenarien Systemarchitektur und technische Anforderungen.                                                                                                                                             | [Channel9](http://go.microsoft.com/fwlink/?LinkId=306986) (http://channel9.msdn.com/events/BUILD/BUILD2011/HW-456T) |
| Desktop-Aktivität Moderator                                           | Artikel      | Übersicht über DAM-Funktion                                                                                                                                                                                                                                                            | [MSDN](http://go.microsoft.com/fwlink/?LinkId=306987) (https://msdn.microsoft.com/en-us/library/hh848040 (v=vs.85).aspx) |


## <a name="considerations"></a>Erwägungen

Um die Effizienz der Plattform Power optimieren, müssen Sie Folgendes berücksichtigen:

- [Wie wirkt sich auf Hardware modernen Standby](#how-hardware-affects-modern-standby)
- [Entwerfen Sie ein Bild zuordnen OEM der modernen Standby zu optimieren](#how-to-design-an-oem-image-to-improve-the-modern-standby-experience)
- [Wie apps modernen Standby auswirken](#how-apps-affect-modern-standby)
- [Wie Sie realistische Testergebnisse abrufen](#how-to-get-realistic-test-results)
- [Gewusst wie: Berechnen des Energieverbrauchs](#how-to-calculate-power-consumption)

### <a name="how-hardware-affects-modern-standby"></a>Wie wirkt sich auf Hardware modernen Standby

Hardwarekomponenten, unterschiedliche Abständen w im aktiven Modi und modernen Standby verwenden. Sie können die Leistung von Hardwarekomponenten, um festzustellen, ob sie zu einer die modernen Standby-Erfahrung Verschlechterung sowie das Arbeiten mit dem Hersteller zur Verbesserung der Effizienz bewerten.

### <a name="how-to-design-an-oem-image-to-improve-the-modern-standby-experience"></a>Entwerfen Sie ein OEM-Bild, das der modernen Standby zu optimieren

Der Entwurf des vollständigen Windows-Abbild kann verbessern oder zu einer Verschlechterung die modernen Standby-Erfahrung. Sie können in allen Phasen des Image Entwurfs- und zu einem frühen Zeitpunkt Identifizieren von Leistungsproblemen Designentscheidungen basierend auf den Ergebnissen Tests ausführen.

### <a name="how-apps-affect-modern-standby"></a>Wie apps modernen Standby auswirken

Windows Store-apps Verbinden mit vielen Quellen und direkt mit Hardwaregeräten integrieren. Apps können während der modernen Standby, wie live Kacheln aktualisieren oder Wiedergeben von Hintergrundmusik bestimmte Aufgaben ausführen. Diese Aufgaben zeichnen mehr Leistung von der Batterie.

In einigen Fällen muss eine Windows Store-app einen vom Benutzer gestarteten werden, bevor für moderne Standby angehalten wird Vorgang abgeschlossen sein. Für diese Art von Aktivität gibt es bestimmte Affordances, mit die die app für eine bestimmte Zeitspanne weiterhin ausgeführt werden können. Einige apps können auch verhindern, dass ein Gerät modernen Standbymodus. Sie können apps bewerten, in das Windows-Abbild, um festzustellen, ob sie zu einer die modernen Standby-Erfahrung Verschlechterung, und mit der app-Entwickler zur Verbesserung der Effizienz arbeiten.

### <a name="how-to-get-realistic-test-results"></a>Wie Sie realistische Testergebnisse abrufen

Sie können Tests basierend auf der Hardware und Software Konfiguration des Computers zum Abrufen von Ergebnis genauer anpassen. Beispielsweise können Sie Tests mit Antischadsoftware aktiviert, auf dem PC ausführen.

### <a name="how-to-calculate-power-consumption"></a>Gewusst wie: Berechnen des Energieverbrauchs

Sie können die Rate des Stromverbrauchs für Ihren PC in verschiedenen Szenarien, einschließlich modernen Standby abschätzen. Klicken Sie dann können Tests überprüfen Schätzung der Kosten und Leistungsprobleme aufgrund von einzelnen Komponenten zu ermitteln. Um weitere Informationen zum Berechnen des Stromverbrauchs finden Sie unter dem Dokument Batterie Aspekte.

## <a name="self-hosting-and-user-testing"></a>Self-hosting und Benutzer zu testen

Es wird empfohlen, dass Sie ein Self-Hosting Programm Fehler finden und verbessern Sie die endgültige Qualität für moderne Standby-Systeme verfügen. Einige Fehler können nur über die Benutzer von Self-Hosting und real testen identifiziert werden. Bereiche, um den Fokus sollte die folgenden Szenarien umfassen:

-   CS Geben Sie Exit/Zuverlässigkeit und Leistung
-   Thermals
-   Reaktion/performance
-   Konnektivität
-   Akkulaufzeit


## <a name="recommended-goals"></a>Empfohlene Ziele

Das Gerät Batteriekapazität und Strom sollte sorgfältig analysiert werden, um Ihre Batterie Lebensdauer Ziele zu erreichen. Messen Sie Verbrauchern Verwendungsszenarien und präzise Akkulaufzeit des Geräts project-Umgebungen.

In der folgenden Tabelle zeigt die minimale Zielvorgaben für die Akkulaufzeit, basierend auf unsere Research Benutzer. Sie sollten auch Ihre Batterie Lebensdauer Ziele mit-Market-Produkte vergleichen.

| Szenario-Aufgaben            | Ziel |
|------------------------------|------------------------------|
| Moderne Standby               | &gt;= 9 Tage der Akkulaufzeit |
| Audiowiedergabe (Anzeige deaktiviert) | &gt;= 125 Stunden |

DRIPS % höher ist eine wichtige Metrik zu ermitteln, ob ein bestimmtes System gut oder schlecht Akkulaufzeit während einer Sitzung modernen Standby aufweist.

| DRIPS %   | Auswertung |
|-----------|------------|
| 98 – 100  | Ausgezeichnet |
| 95 – 97.9 | Sehr gut |
| 90 – 94.9 | Eine gute |
| 80 – 89,9 | Fair |
| &lt;80   | Schlecht |


## <a name="validation-and-testing"></a>Hinweise zur Überprüfung und testen

<!--No content was provided here in the original Word file.-->

### <a name="generating-a-report-on-battery-life-estimates-and-history-by-using-powercfgexe"></a>Generieren einen Bericht über Batterie Lebensdauer Schätzungen und Verlaufslisten mithilfe PowerCfg.exe

Das Tool PowerCfg.exe wird mit Windows installiert. Das Tool PowerCfg.exe können Batterie Lebensdauer Inkonsistenzen auf Ihrem PC zu identifizieren.
PowerCfg.exe verwendet System Tracing in Windows-Betriebssystems, Berichtsdetails Batterie Nutzung, einschließlich den Status über einen Zeitraum 72 Stunden. Batterie-Verwendungsbericht werden Power-Verwendungsdaten angezeigt, auch wenn der PC-Option nicht in einen aktiven Zustand war.

Generieren eines Verwendungsberichts Batterie, öffnen Sie ein Eingabeaufforderungsfenster mit erhöhten Rechten, und führen Sie den folgenden Befehl: **powercfg.exe /batteryreport/Output c:\\Berichte\\batterylife.html**

Der Batterie Verwendungsbericht enthält Informationen zu Akkus Gebühr Kapazität der Batterie zurückgehen einige Monate in den PC, den Status und Batterie Kanalisation gelangen lassen während der letzten 72 Stunden, einen Verlauf der Batterie Verwendung und Änderungen installiert und eine Batterie Lebensdauer Schätzung basierend auf den tatsächlichen Verlauf des PCs.

Weitere Informationen über das Tool PowerCfg.exe finden Sie unter [Command-Line Options PowerCfg](http://go.microsoft.com/fwlink/?LinkId=264942) (https://technet.microsoft.com/en-us/library/hh824902.aspx).

### <a name="generating-a-report-on-modern-standby-issues-by-using-sleepstudy"></a>Generieren eines Berichts auf modernen Standby Probleme mithilfe von SleepStudy

SleepStudy ist ein neues Windows-Diagnose-Tool, das moderne Standby unterstützt. Es überwacht modernen Standby PC Verhalten und bietet bearbeitungsfähige Diagnose auf modernen Standby Akkulaufzeit. Es steht nur für PCs CS aktiviert.

SleepStudy generiert eine Zusammenfassung der Topthemen schlechte modernen Standby Akkulaufzeit verursacht. Um den Bericht zu erhalten, führen Sie Powercfg /sleepstudy Befehl in einer Eingabeaufforderung mit erhöhten Rechten. Dieses neue Tool ist nützlich, wenn Sie planen, suchen und Fehler selektieren Self-hosting Programms.

Weitere Informationen zum Tool /SleepStudy PowerCfg finden Sie unter [verbundene standby SleepStudy](https://msdn.microsoft.com/en-us/library/windows/hardware/dn495346(v=vs.85).aspx) (https://msdn.microsoft.com/en-us/library/windows/hardware/dn495346 (v=vs.85).aspx).

Es folgt ein Beispiel. Diesem Bildschirm zeigt PC-Info, einschließlich Name des Aufnahmegeräts, Firmware und Build-Version. Das Diagramm zeigt die entleerungsrate im modernen Standby-Modus.

![Beispieldiagramm des Satzes von dargestellt in den Energiesparmodus versetzt wird Studie abzuleiten.](images/weg-sleepstudy-chart-drain-rate.jpg)

Dies ist der pro Sitzungstabelle. In diesem Beispiel wurde die Sitzung 3 die höchste entleerungsrate. Indem Sie darauf klicken, wird die nächste Detailebene zum Identifizieren der möglichen hier geöffnet.

Die Spalte **Energie Änderung** stellt den Betrag dar Energie ein Ausgleich vorgenommen von der Batterie (in mWh) in einer bestimmten CS-Sitzung. Die **Änderungsrate** Spalte stellt die durchschnittliche Stromverbrauchs (in mW) in einer bestimmten CS-Sitzung.

![Tabelle in den Energiesparmodus versetzt wird Studie Daten zu der Rate der abzuleiten in einem Beispiel angezeigt.](images/weg-sleepstudy-table-drain-rate.jpg)

In diesem Beispiel ist ein UART-Treiber, der die gesamte Zeit in dieser Sitzung aktivem vorhanden. Dies kann als Ausgangspunkt für eine ausführlichere Untersuchung verwendet werden.

![In dem Beispiel in den Energiesparmodus versetzt wird Studie dargestellt hier.](images/weg-sleepstudy-screen-top-offenders.jpg)

#### <a name="automating-connected-standby-testing-by-using-pwrtestexe"></a>Automatisieren von standby Testen mit PwrTest.exe verbunden

Das Tool PwrTest.exe können im Microsoft Windows Treiber Kit (WDK) Sie um den Status, einschließlich verbundenen Standby zu erfassen Prozessor Power Management und Batterie aus dem System über einen bestimmten Zeitraum zu durchlaufen.

**Zum Ausführen von einem verbundenen standby Szenario mit PwrTest.exe**

1. Installieren Sie das [WDK](http://go.microsoft.com/fwlink/?LinkId=226411)(https://msdn.microsoft.com/en-US/windows/hardware/gg454513).

2. Navigieren Sie an einer Eingabeaufforderung auf die PwrTest.exe-Version, die mit die Architektur des Computers übereinstimmt. Geben Sie zum Beispiel: **cd C:\\WDK\\Tools\\PowerManagement\\i386**

3. Führen Sie mit der **Option/cs** PwrTest.exe. Außerdem können Sie geben Sie die Anzahl der Zyklen (**/c/c**) Verzögerungszeit zwischen Übergänge in Sekunden (**/d/d**), und beenden Zeit in Sekunden (**/p/p**). Geben Sie zum Beispiel: **pwrtest.exe/cs /c:4 /p:120 /d:150**

![Beachten Sie](images/note-regular.gif)**Hinweis**&nbsp;&nbsp;&nbsp;das verbundene standby Szenario muss den virtuelle Power Schaltfläche Treiber.
Dieser Treiber installiert ist durch die Windows Gerät testen Framework (WDTF), die sich im WDK 8 befindet.

Die Protokolldatei für PwrTest.exe verbundenen standby Szenario enthält Informationen zu Übergänge zwischen den Status.

Verbundene Standby Hardware Compatibility Belastungstests können Sie die Parameter wie die Anzahl der Testzyklen und Verzögerungen zwischen Testzyklen angeben.

Weitere Informationen finden Sie unter [PwrTest](http://go.microsoft.com/fwlink/?LinkId=306989) (https://msdn.microsoft.com/en-us/library/windows/hardware/ff550682 (v=vs.85).aspx).

# <a name="delivering-a-great-energy-efficiency-experience"></a>Spielt eine hervorragende Energie Effizienz Erfahrung

Batterie Leben und weniger Energie Effizienz werden in den aktivsten Themen bei modernen Netzwerken. Letzte Studien zeigen, dass 76 % der Verbraucher Akkulaufzeit als "sehr wichtig" bewerten bei der Auswahl ein Tablet und mobilen PC. Aufgrund ihrer Rolle als einen Wettbewerbsvorteil dar ist die Akkulaufzeit entscheidend.

Es ist wichtig, einen ganzheitlichen Ansatz zur Optimierung des Energieverbrauchs (w verwendet) auf der Basis Hardwareplattform Windows, Windows-Abbild und Extensions (Treiber, Teiler Software, Dienste usw.).

## <a name="considerations"></a>Erwägungen

Die Energie Effizienz und Batterie Lebensdauer des Computers ist in jeder Phase des Prozesses entwerfen und entwickeln betroffen.

### <a name="how-to-select-battery-capacity"></a>Auswählen von Batteriekapazität

Bestimmen Sie Ihre Batterie Lebensdauer Ziele,-Design, soll-Kosten und der Zielmarkt für Ihren PC wählen Sie eine entsprechende Batteriekapazität erleichtern. Berücksichtigen Sie dies in einer frühen Phase der Planung und Entwicklung Phase so, dass Sie mit enden nicht zu klein der Batterie für Ihre Ziele zu erreichen.
Weitere Informationen zum Modellieren Batterie Lebensdauer Runtime finden Sie unter *Batterie Richtlinien* Dokument enthaltene die WEGs auf Verbinden.

### <a name="how-to-design-an-oem-image-to-improve-battery-life"></a>Gewusst wie: Entwerfen eines OEM-Bild zur Verbesserung der Akkulaufzeit

Beim Entwurf einer vollständigen Windows-Abbild kann verbessern oder Batterie Leistung beeinträchtigen. Ihre Auswahl von apps, Treiber und Power-Pläne kann beispielsweise die Stromverbrauchs des PCs ändern.

Sie können in allen Phasen des Image Entwurfs- und zu einem frühen Zeitpunkt Identifizieren von Leistungsproblemen Designentscheidungen basierend auf den Ergebnissen Tests ausführen.

## <a name="recommended-goals"></a>Empfohlene Ziele

Die Ziele in diesem Abschnitt beschriebenen sind vorgesehen, mit denen Sie eine voll integrierte Plattform entwerfen, die eine Einsparung Akkulaufzeit bietet, während der Ausführung von Windows. Die Ziele beschrieben keine Zusage für Windows bereit sind, sind sie Zielvorgaben für die Sie an die Hardware erfüllt. Die Ziele werden ständig basierend auf Feedback von Ökosystempartner, Windows-Entwicklung und Plattform Power Management Validierung angepasst.

Sorgfältig analysieren Sie des Geräts Batteriekapazität, und schalten Sie zeichnen auf Ihre Batterie Lebensdauer Ziele zu erreichen. Messen Sie Verbrauchern Verwendungsszenarien und präzise Akkulaufzeit des Geräts project-Umgebungen.

Die folgende Tabelle enthält, was unsere Benutzer Research gibt an, die Leiste Mindestqualität gemäß den Erwartungen der Benutzer ist. Sie sollten auch Ihre Batterie Lebensdauer Ziele mit-Market-Produkte vergleichen. Verfügbar in der Windows-Bewertung und Deployment Kit (ADK), eine vergleichbare Energie Effizienz speicherinternes Testtool oder eine vergleichbare Test Windows-Batterie Assessment Test können Verwendungsszenarien Verbrauchern und Umgebungen Akkulaufzeit überprüfen gemessen.

| Szenario                                                                      | Tablet (CS)     | Konvertiert werden kann.     | Notizbuch |
|-------------------------------------------------------------------------------|-----------------|-----------------|--------------|
| Batterie Lebensdauer Videowiedergabe @ 150-200 NT abhängig von Formfaktor (in Stunden) | &gt;= 12        | &gt;= 6         | &gt;= 5 |


| Metrisch                               | Ziel |
|--------------------------------------|--------|
| System Timer-Lösung              | 15 ms |
| Maximale Prozessor Status auf DC und AC<br/>(Prozessor Power Management)<br/>Gilt nicht für verbundene Standby-fähigen Systeme. |   100 % |

                                         


## <a name="validation-and-testing"></a>Hinweise zur Überprüfung und testen

Das Windows Assessment Toolkit, eine vergleichbare Energie Effizienz speicherinternes Testtool oder eine vergleichbare Test können Sie Verbrauchern Verwendungsszenarien und Umgebungen zum Verbessern der Leistung des Computers über Mindestanforderungen hinaus messen. Windows-Bewertungen im Zusammenhang mit der aktiven Arbeitslast Akkulaufzeit zählen:

<dl>
<dt>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<strong>Im Leerlauf Energie Effizienz Auftrag</strong></dt>
<dd>
<p>Bezeichnet die Probleme mit Software, Treiber und Geräte während System im Leerlauf, die Ihr System vorgegebenen Energie-Effizienz reduzieren.</p>
</dd>
<dt>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<strong>Führen Sie nach unten Auftrag Batterie</strong></dt>
<dd>
<p>Akkulaufzeit während einer normalen System Verwendungsszenario misst und meldet Probleme mit der Effizienz Energie im Leerlauf Zeiträumen des Systems.</p>
<p>Dieser Auftrag enthält die Arbeitslast im Leerlauf Energieeffizienz und einer lokalen Video Wiedergabe Energie-Effizienz Arbeitslast.</p>
</dd>
</dl>


### <a name="changes-in-energy-efficiency-job-parameters-for-adk-81"></a>Änderungen in Energie-Effizienz Auftrag Parametern für ADK 8.1

Es wurden einige Änderungen an der Benutzeroberfläche in der ADK 8.1 Energie-Effizienz Auftragsparameter:

-   Wenn das Kontrollkästchen **Schleife Arbeitslasten bis angegebenen Batterie Ebene** ausgewählt ist, wird die Bewertung nur eine Schleife alle ausgewählten Arbeitslast ausgeführt.

-   Wenn Sie die Option zum **generieren Diagnoseinformationen** erhalten **Diagnose**, Sie die Spuren während der Ausführung der Arbeitslast erfassen wird.

    -   **Erstellen von Power Profil Probleme** wird Powercfg.exe /energy Daten erfassen und dem Bericht hinzugefügt.

    -   **Analyse Trace sammeln** können Sie eine erweiterte im Leerlauf Analysis Trace Erfassen der 3 Minuten lang ausgeführt wird und sammelt CPU Sampling-Stapel.

Die ADK 8.0 Szenarien können klicken Sie dann in der folgenden übersetzt werden:

-   Kurzer ohne Diagnose

    -   Wählen Sie die **Schleife Arbeitslasten bis zum angegebenen Niveau**.

        Deaktivieren Sie die **Diagnoseinformationen generieren**.

-   Kurzer mit Diagnose

    -   Wählen Sie die **Schleife Arbeitslasten bis zum angegebenen Niveau**.

    -   Überprüfen Sie die **Diagnoseinformationen generieren**und **Erstellen von Power Profil Probleme** und **Sammeln Analysis Trace**.

-   Nur Diagnose

    -   Deaktivieren Sie das Kontrollkästchen Sie **Schleife Arbeitslasten bis zum angegebenen Niveau**.

    -   Überprüfen Sie die **Diagnoseinformationen generieren**und **Erstellen von Power Profil Probleme** und **Sammeln Analysis Trace**.

### <a name="configure-your-pc-for-testing"></a>Konfigurieren Sie den PC zu Testzwecken

Ein prozessorintensive Treiber, eine falsche Firmware-Einstellung oder eine schlecht konfigurierte Power-Einstellung kann eine erhebliche Steigerung des Stromverbrauchs verursachen. Beim Entwerfen und Systemtests, probieren Sie mehrere Konfigurationen des folgenden Aspekten, die das beste Gleichgewicht zwischen Energieeffizienz und Leistung zu erzielen. Verwenden Sie die Testergebnisse zur Verbesserung der wieder in den Entwurf von Ihrem PC und das Windows-Abbild um eine hervorragende aktiven Arbeitslast Akkulaufzeit übermitteln.

<dl>
<dt>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<strong>Analysieren von Hardwarekomponenten</strong></dt>
<dd>
<p>Bitten Sie Hardwarehersteller für ihre Energieverbrauchs Testergebnisse für jede Hardwarekomponente.</p>
</dd>
<dt>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<strong>Analysieren von Treibern</strong></dt>
<dd>
<p>Jede neuen Treiber für Auswirkung auf die Akkulaufzeit zu überprüfen. Wie jeder neuer Treiber für das System hinzugefügt wurde, beachten Sie ihre Auswirkung auf Stromverbrauchs. Einen leistungsschwachen Treiber kann die Systemleistung erheblich beeinträchtigen.</p>
</dd>
<dt>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<strong>Analysieren von apps, Dienste und andere software</strong></dt>
<dd>
<p>Jede neue app und der dazugehörigen Systemdienst Auswirkung auf die Akkulaufzeit zu überprüfen. Sobald das System jede neue app hinzugefügt wird, beachten Sie den Effekt des Stromverbrauchs. Eine ineffiziente app kann die Systemleistung erheblich beeinträchtigen.</p>
</dd>
<dt>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<strong>Konfigurieren von Power-Pläne</strong></dt>
<dd>
<p>Optimieren der Leistung von Windows Power-Plan-Einstellungen des Lastenausgleichs für leistungsanforderungen und Akkulaufzeit. Dies gilt nicht für verbundener Standby-aktivierte Systeme.</p>
</dd>
<dt>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<strong>Testen Sie die Leistungsfähigkeit des PCs</strong></dt>
<dd>
<p>Vergleichen Sie die gesamte Leistung des PCs verwendet nur die installierten Treiber eine Windows-Installation mit hoch.
Einige PCs haben eine Abnahme 40 % Akkulaufzeit gezeigt, wenn vorinstallierten apps und Power Richtlinien auf das Bild hinzugefügt werden.</p>
</dd>
</dl>

Wir empfehlen die Verwendung der folgenden Einstellungen Umgebung beim Testen der Akkulaufzeit auf Ihrem PC. Diese Einstellungen hilft Ihnen, konsistente und zuverlässige Daten für realistische Benutzerszenarien abzurufen.

<table>
<thead>
<tr class="header">
<th>Komponente</th>
<th>Einstellung</th>
<th>Hinweise</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Anzeigen der Einstellung</strong></td>
<td>Helligkeit = 150-200 NT je nach Formfaktor</td>
<td>Helligkeit wird auf desktop weißem Hintergrund mit der Helligkeit Anzeige in der Mitte des Bildschirms platziert gemessen.</td>
</tr>
<tr class="even">
<td><strong>Power-Richtlinie</strong></td>
<td><p>Lastenausgleich</p>
<p>Anzeigen von Abblenden Timeout deaktiviert</p>
<p>Anzeigen von Timeout deaktiviert</p>
<p>Adaptive Helligkeit deaktiviert</p>
<p>S3 Timeout deaktiviert (gilt nicht für Systemen, die mit der verbundenen dem Standbymodus)</p>
<p>S4 Timeout deaktiviert</p></td>
<td>n/v</td>
</tr>
<tr class="odd">
<td><strong>Sender</strong></td>
<td><p>Wi-Fi <em>und</em> verbunden</p>
<p>Alle anderen radios auf, aber nicht verbunden</p></td>
<td>Verbinden Sie mit einem Consumer-Klasse drahtlosen Router, der Internetzugriff hat</td>
</tr>
<tr class="even">
<td><strong>Andere Netzwerke</strong></td>
<td>Ethernet getrennt</td>
<td><p>Trennen Sie vor dem Starten der test</p>
<p>Nach Abschluss der Batterie kurzer Verbindung wieder her</p></td>
</tr>
</tbody>
</table>



## <a name="tools-and-technical-reference"></a>Tools und technische Referenz

Erfahren Sie mehr über die Akkulaufzeit und Tools zur Leistung von diesen Ressourcen analysieren herunterladen können:

| Titel der Ressource                                               | Inhaltstyp | Beschreibung                                                                                                                                                                                                                                                                | Link herunterladen |
|--------------------------------------------------------------|--------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------|
| Windows Assessment and Deployment Kit<br/><br/>Im Leerlauf Energie-Effizienz und Batterie ausführen unten Aufträge | Tool | Die Windows-ADK hilft Ihnen bei Energie-Effizienz auf Ihrem PC zu messen. | Verwenden Sie die neuesten Windows ADK Drop aus verbinden |
| : Windows Engineering Bereitschaft Batterie Lebensdauer Schulung | Referenz    | Enthält Informationen zum Benutzer Research, mithilfe der Tools ADK und eine Batterie auswählen.  | [Eine Verbindung herstellen](http://go.microsoft.com/fwlink/?LinkId=306535) (https://connect.microsoft.com/site1304/Downloads/DownloadDetails.aspx?DownloadID=48261) |
| Bereitstellung von Leistung und Akkulaufzeit                | Video        | Beschreibt, wie leistungsfähige und weniger Energie effizientere Erfahrungen auf das gesamte Spektrum der Windows 8-Plattformen erstellen. Hier erfahren Sie, app Entwurfs- und Methoden, die die maximieren die Leistung von apps und des Energieverbrauchs als Ganzes.                                  | [Channel9](http://go.microsoft.com/fwlink/?LinkId=306082) (http://channel9.msdn.com/events/BUILD/BUILD2011/HW-459T) |
| Verbesserte Akkulaufzeit und Energie-Effizienz                 | Video        | Veranschaulicht, wie Windows ADK vereinfacht hat konsistent Akkulaufzeit, messen und Energie Effizienz Probleme identifizieren und beheben. Erfahren Sie, wie Batterie Lebensdauer Bewertung konfigurieren und Workflows zur Bewertung für Szenarien mit mehreren entwerfen.  |  [Channel9](http://go.microsoft.com/fwlink/?LinkId=306083) (http://channel9.msdn.com/events/BUILD/BUILD2011/HW-149P) |
| Ergebnisse für im Leerlauf Energie-Effizienz                           | Document     | Dieses Thema hilft Ihnen die interpretiert werden die Ergebnisse, die mit einer Energie-Effizienz Auftrag, der die Arbeitslast im Leerlauf verwendet. |  [MSDN](http://msdn.microsoft.com/en-us/library/windows/hardware/jj130809.aspx) (https://msdn.microsoft.com/en-us/library/windows/hardware/jj130809.aspx)  |
| Batterie Lebensdauer Lösungen                                | Document     | Führen Gliederungen Probleme und Lösungen für die Erweiterung der Akkulaufzeit für tragbaren Computern, die das Betriebssystem Windows 7. Systementwurfs Power-Richtlinien und Vorinstallation konfigurationsempfehlungen bietet auch als konfigurationsempfehlungen testen. | [MSDN](http://go.microsoft.com/fwlink/?LinkId=306534) (https://msdn.microsoft.com/en-us/library/windows/hardware/dn641606 (v=vs.85).aspx) |
| Verwenden von PowerCfg für System Energie-Effizienz ausgewertet werden soll          | Document     | Bietet Informationen über die Funktionalität des Dienstprogramms "PowerCfg" für die Auswertung System Energieeffizienz für Betriebssysteme der Windows-Produktfamilie.  | [MSDN](http://go.microsoft.com/fwlink/?LinkId=306533) (https://msdn.microsoft.com/en-US/library/windows/hardware/dn550976) |


# <a name="instrumenting-your-code-with-etw"></a>Den Code mit ETW Instrumentation

Ereignis Tracing for Windows (ETW) ist eine Funktion Hochgeschwindigkeits Tracing in Windows integriert. Mithilfe eines Zwischenspeichern und Protokollierungsergebnisse Mechanismus im Betriebssystem-Kernel implementiert bietet ETW eine Infrastruktur für Ereignisse, die vom Benutzermodus (apps) und Kernel-Modus-Komponenten (Treiber) ausgelöst.
ETW kann für System und app-Diagnose, Problembehandlung und Leistungsüberwachung verwendet werden. In der Vergangenheit wurde Tracing verwendet, um unerwartetes Verhalten sowohl in Hardware und apps diagnostizieren. Es wurde kürzlich einer steigenden Nachfrage nach verwalten und Überwachen der Leistung und Systemstabilität nötig erfüllen. Leistungsanalyse in Umgebungen für Entwicklung und Produktion änderte daher ein wichtiger Bestandteil der Welt Netzwerke. Im Gegensatz zu Ausfällen und Fehlern-bezogenen Leistung Probleme sind schwer zu erkennen und zu diagnostizieren, da sie häufig Konfigurations- und Arbeitslast abhängig sind. Protokollierung in einer produktionsumgebung bietet wichtige Daten zum Ermitteln von Problemursachen Leistung ausstellt, sowie die kapazitätsplanung und Bewertung.

Die ETW-Mechanismus können Sie Tracing Sitzungen dynamisch, wodurch es möglich, wird capture ausführliche Protokollierung in produktionsumgebungen ohne Neustart oder app Neustart des Systems an.

In diesem Abschnitt erfahren Sie, wie Sie ETW verwenden, um genaue Leistung Messung und Analyse durchzuführen.

-   Kernelmodus-Treibercode
-   Herkömmliche desktop Prozesse und Dienste
-   Windows Store-apps (C\#)

## <a name="overview"></a>Übersicht

Es folgen einige Merkmale ETW vorteilhaft:

<dl>
<dt>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<strong>Robuste</strong></dt>
<dd>
<p>Effiziente Pufferung und Protokollierung Mechanismen bereitgestellt.
Der Verfolgung Puffer wird durch den Kernel verwaltet. Verfolgen ETW ist app Abstürze und hängt immun. Im Fall eines WAN-System werden nicht gespeicherten Ereignisse in ein Speicherabbild zugegriffen werden.</p>
</dd>
<dt>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<strong>Dynamische</strong></dt>
<dd>
<p>Tracing Sitzungen kann werden gestartet, beendet, neu konfiguriert und dynamisch ohne Neustart oder app Systemneustart angehalten. ETW bietet mehrere Unterhaltungsmodi um verschiedene Auflagen erfüllen.</p>
</dd>
<dt>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<strong>In Windows integriert</strong></dt>
<dd>
<p>Als die app Controller erforderlich keine zusätzlichen Tools. Windows verfügt über einige Posteingang Controller sowie Consumer-apps.</p>
</dd>
<dt>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<strong>Lightweight</strong></dt>
<dd>
<p>Der Aufwand für historische Tracing und gespeicherte Protokolldateien optimiert werden, damit app oder System Auswirkungen auf die Leistung nicht. Der Protokollierungsmechanismus verwendet Kernel-Modus-Puffer, die, Aufwand aus Tracing beschränkt ist von einem separaten Writerthread auf den Datenträger geschrieben werden soll.</p>
</dd>
</dl>

Nur waren grundlegende textbasierte Tracing Mechanismen verfügbar in Windows vor Windows 2000. **DbgPrint**() und ( **DebugPrint**) APIs hatten. Debugger erforderlich, und in der Regel waren nicht dynamisch gesteuert. Die Windows-Authentifizierungsmechanismus Tracing über einen Zeitraum entwickelt und heute vier verschiedene Tracing Mechanismen verfügbar sind. Die Unified Ereignis Logging API-Satz in Windows Vista wurden ETW und Ereignisprotokoll API-Sätzen zusammengeführt.
Dies bietet Benutzern und Entwicklern einen einheitlichen Mechanismus zum Auslösen von Ereignissen.

Es gibt drei Arten von Ereignissen:

1.  Softwareablaufverfolgung (WPP) für Windows und klassische ETW

2.  Managed Objektformat (MOF): MOF ist eine Möglichkeit zum Beschreiben der WMI-Objekte und aktivieren und Decodieren Ereignisse.

3.  Manifest-basierte: eine XML-basierte unified Tracing Definition in Windows Vista eingeführt wurde. Eine XML-Datei enthält Elemente für Ereignisse, die ein Anbieter schreibt. Weitere Informationen finden Sie unter [Schreiben einer Instrumentation Manifest](http://go.microsoft.com/fwlink/?LinkId=309789) (https://msdn.microsoft.com/library/dd996930.aspx).

![](images/note-regular.gif)**Hinweis**beachten&nbsp;&nbsp;&nbsp;die Anleitung in diesem Abschnitt wird ausschließlich auf Manifest-Ereignis Instrumentation konzentrieren.

Es folgen einige wichtige Merkmale von ETW:

-   Entwickler können entscheiden, die richtigen Sätze von Implementierung basierend auf beabsichtigten Verwendung (z. B. Printf wie WPP-Implementierung ist einfach, hinzufügen, die für das debugging Zweck Ereignisse)

-   Die Infrastruktur verwaltet häufig verwendete Informationen wie Zeitstempel, Funktionsnamen und Quelle Datei Zeilennummern

-   Die gleiche Implementierung wird für Benutzer Modus apps und Kernel-Modus-Komponenten verwendet.

-   Darauf ist in Absturz speichert und live debuggen möglich

-   Es kann in den Kernel-Debugger für eine in Echtzeit Ansicht umgeleitet werden

-   Real-Time-Ansicht

-   Protokolldateien werden in eine binäre Protokolldatei (ETL-Datei) gespeichert.

-   Es unterstützt mehrere Prozesse, die Protokollierung

-   Hohe Durchsatz

-   Protokolldateien können auf einem anderen Computer angezeigt werden

-   Unterstützt die kreisförmige Pufferung für kontinuierliche Protokollierung und Überwachung

-   Sie können in einer der Kanäle basierend auf die Zielgruppe gruppiert werden

## <a name="etw-architecture"></a>ETW-Architektur

Es gibt vier Hauptkomponenten in ETW: Anbieter, Sitzung, Controller und Consumer.

![Diagramm der vier Hauptkomponenten der Architektur ETW.](images/weg-diagram-etw-architecture-four-components.png)

### <a name="provider"></a>Provider

Ein *Anbieter* ist eine instrumentierte Komponente, die Ereignisse generiert. Ein Anbieter kann eine Benutzer-Modus-app, einem Kernelmodus-Treiber oder die Windows-Kernel selbst sein. Zusätzlich zur festen Ereignisdaten (Kopfzeile) kann ein Ereignis Benutzerdaten auszuführen.

Ein *Ereignis* ist eine ereignisbasierte Darstellung der Daten. Eine eingehende Analyse können die Daten verwendet werden. Ein Ereignis kann auch verwendet werden, um Leistungsindikatoren zu erstellen. *Die Leistungsindikatoren* enthalten eine Beispiel-basierte Ansicht der Daten. Eine kleine Gruppe von Daten zum Anzeigen des aktuellen Status, beispielsweise e/a-Bytes pro Sekunde und Interrupts pro Sekunde in der Regel enthalten.

Ein Anbieter muss in ETW registrieren und Ereignisse aus den Code durch Aufrufen der ETW-Protokollierung APIs senden. Anbieter Register ein Rückruf zum Aktivieren und Funktion Benachrichtigung deaktivieren, sodass tracing kann aktiviert und dynamisch deaktiviert werden.

### <a name="session"></a>Sitzung

Die ETW-Sitzung Infrastruktur arbeitet als eine anspruchsvollere Broker, die die Ereignisse aus einem oder mehreren Dienstanbietern an die Consumer leitet. Eine Sitzung ist ein Kernelobjekt, das Ereignisse in Kernel Puffer erfasst und sendet sie an eine angegebene Datei oder in Echtzeit Consumer-Prozess. Mehrere Anbieter können auf eine einzige Sitzung, die zum Sammeln von Daten aus mehreren Quellen Benutzern ermöglicht, zugeordnet werden.

### <a name="controller"></a>Controller

Ein Domänencontroller startet, beendet oder eine Sitzung Trace aktualisiert. Eine Sitzung ist eine Einheit für die Protokollierung. Anbieter sind zugeordnet (an eine bestimmte Sitzung oder aktiviert). Ein Controller aktiviert und deaktiviert Anbieter, sodass sie das Senden von Ereignissen in ETW starten können. Controller-Funktionen mit den Tools von Microsoft bereitgestellten aufgerufen werden können, oder Sie können Ihre eigenen app schreiben.

Logman.exe ist eine in-Box-Controller-app. Windows Performance Aufzeichnung (WPR) in Windows Performance Toolkit ist der empfohlene Controller-Vorgang.

### <a name="consumer"></a>Consumer

Ein *Consumer* ist eine app, die eine protokollierten Ablaufverfolgungsdatei (ETL-Datei), liest oder Ereignisse in einer Sitzung aktiven Trace in Echtzeit erfasst und verarbeitet Ereignisse. Ereignisanzeige und Ressource Systemmonitor sind im Feld ETW Consumer apps.

Windows Performance Analyzer (WPA) in Windows Performance Toolkit ist der empfohlene Consumer-Vorgang.

## <a name="implementing-etw-instrumentation"></a>Implementieren von ETW-instrumentation

<!--There was no content provided here in the original Word file.-->

### <a name="plan-your-instrumentation"></a>Planen Sie die instrumentation

Entscheiden Sie, wo Sie in Ihrem Code ETW-Ereignisse protokolliert werden. Dies sollte Korrelation mit wichtige Benutzerszenarien oder häufige Verwendungsszenarien, die Sie messen, analysieren und schließlich verbessern möchten. Dies sind einige Beispiele für was instrumentiert werden konnte:

-   Status ändert sich
-   Anfang/Ende erhebliche Vorgänge
-   Erstellen und Löschen von Ressourcen
-   Andere Ereignisse im Zusammenhang mit der Leistung und Zuverlässigkeit
-   Debug-Ereignisse

### <a name="create-a-manifest-file-and-implement-your-provider"></a>Erstellen einer Manifestdatei und Implementieren des Anbieters

Manifest-basierte ETW-Ereignisse können im Benutzermodus-apps, einschließlich der Dienste, als auch im Kernelmodus Modus Komponenten wie Treibern, die mithilfe einer XML-Datei, die das *manifest-Ereignis*aufgerufen implementiert werden. Weitere Informationen finden Sie unter [Event Tracing-Funktionen](http://go.microsoft.com/fwlink/?LinkId=309791) (https://msdn.microsoft.com/library/windows/desktop/aa363795.aspx).

Ein Manifest Ereignis ist in die folgenden Abschnitte unterteilt:

<dl>
<dt>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<strong>Provider-Definition: &lt;Anbieter&gt;</strong></dt>
<dd>
<p>Enthält den Namen und die GUID des Anbieters ein, die Sie erstellen und den Speicherort der Binärdatei des instrumentiert wird (schließlich die Instrumentation Ressourcen benötigt von ETW-Framework mit).</p>
</dd>
<dt>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<strong>Ereignisnutzlast: &lt;Vorlagen&gt;</strong></dt>
<dd>
<p>Enthält Definitionen für die Datentypen, die als Nutzlast in den Ereignissen eingeschlossen werden. Typen sind verfügbar:</p>
<ul>
<li>
<p>Mit und ohne Vorzeichen 8-Bit, 16 Bit, 32-Bit- und 64-Bit-Ganzzahlen</p>
</li>
<li>
<p>ANSI und Unicode-Zeichenfolgen</p>
</li>
<li>
<p>Float und double</p>
</li>
<li>
<p>Boolescher Wert, Binary, GUID, Zeiger, FILETIME, SYSTEMTIME, SID und HexInt32</p>
</li>
</ul>
</dd>
<dt>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<strong>Statische Ereignisdaten</strong></dt>
<dd>
<p>Verwendet, um Hilfe zu interpretieren, Sortieren und gruppieren Sie die Ereignisse.</p>
<ul>
<li>
<p>&lt;Aufgaben&gt; definieren die Namen der Vorgänge (oder Aufgaben), die instrumentiert wird sind.</p>
</li>
<li>
<p>&lt;Opcodes&gt; definieren die Typen von Operationen, die Sie für Ihre Ereignisse wie die Start, Stop-Ereignis zum Begrenzen von Vorgänge zeitlich das Informationszwecken-Ereignis für das Protokollieren von Debugdaten erstellen möchten und so weiter.</p>
</li>
<li>
<p>Ereignisdefinition: &lt;Ereignisse&gt;</p>
<p>Verbindet Nutzlast und statische Daten. Code gibt Ereignisse gemäß Definition durch die in diesem Abschnitt aufgeführt ist.</p>
</li>
</ul>
</dd>
</dl>


Es folgt ein Beispiel für ein Ereignis Manifest:

```
<provider
    guid="{3877cf22-0702-4dfc-965e-7fdc7780cd74}"
    name="MyEventProvider"
    symbol="MY_EVENT_PROVIDER"
    messageFileName="%temp%\MyProviderBinary.exe"
    resourceFileName="%temp%\MyProviderBinary.exe“
    >
  <templates>
    <template tid="T_MyProvider_1">
      <data inType="win:Int32" name="Operation Id" />
      <data inType="win:Int32" name="Memory Allocated (MB)" />
    </template>
  </templates>
  <opcodes>
    <opcode name="DebugInfo" symbol="_DebugInfo" value="10"/>  
  </opcodes>
  <tasks>
    <task name="OpMemAllocation" symbol="OpMemAllocation_Task" value="1“
          eventGUID="{87ebca33-bf25-442c-9256-82ba484586e8}"/>
  </tasks>
  <events>
    <event symbol="DebugInfo" template="T_MyProvider_1" value="200" 
       task="OpMemAllocation" opcode="DebugInfo" />
  </events>
```

Um die Manifestdatei zu schreiben, können Sie Folgendes verwenden:

-   Manifest-Generator (ECManGen.exe), im Platform SDK verfügbar.

-   Visual Studio (Eventman.xsd), im Platform SDK verfügbar.

### <a name="compile-the-event-manifest"></a>Kompilieren Sie das Ereignis manifest

Im nächste Schritt wird zum Kompilieren des Manifests mithilfe des Tools [Nachricht Compiler](http://go.microsoft.com/fwlink/?LinkId=309792) (<https://msdn.microsoft.com/library/windows/desktop/aa385638.aspx>) (mc.exe), die im Platform SDK verfügbar ist. Dadurch werden einige Dateien, die zum Instrumentieren, kompilieren und Erstellen des instrumentierten Codes generiert:

<dl>
<dt>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<strong>ManifestFileName.h</strong></dt>
<dd>Enthält Ereignisdeskriptoren im Code verwenden.</dd>
<dt>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<strong>ManifestFileName.rc</strong></dt>
<dd>Eine Ressourcencompiler Skript.</dd>
<dt>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<strong>MSG00001.bin</strong></dt>
<dd>Eine Sprachenressource.</dd>
<dt>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<strong>ManifestFileNameTEMP.bin</strong></dt>
<dd>Eine Vorlagenressource (Anbieter und Metadaten).</dd>
</dl>

Wenn Code im Benutzermodus kompiliert werden sollen, geben Sie Folgendes:

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**mc.exe-um** \[ *ManifestFileName*\]

Zum Kompilieren von Kernel-Moduscode geben Folgendes ein:

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**MC.exe km** \[ *ManifestFileName*\]

Verwaltete Kompilierung oder JavaScript-Code Geben Sie Folgendes:

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**MC.exe cs** \[ *ManifestFileName*\]<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**MC.exe - css** \[ *ManifestFileName*\]<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**MC.exe generateProjections** \[ *ManifestFileName*\]

### <a name="update-your-code"></a>Aktualisieren Sie den code

Im nächste Schritt wird der Code Instrumentation hinzugefügt. Führen Sie Visual Studio, fügen Sie der Headerdatei vom Compiler Nachricht generiert und vergessen Sie nicht die Ressourcendatei in das Programm zu erstellen.

Suchen Sie nach in der Kopfzeile, welche Makros (oder Klassenmethoden) in Ihrem Code aufrufen zu erhalten:

-   EventRegister&lt;*YourProviderName*&gt;

    Zum Registrieren des Anbieters (am Anfang der app) verwendet.

-   EventUnregister&lt;*YourProviderName*&gt;

    Zum Aufheben der Registrierung des Anbieters (am Ende der app) verwendet.

-   EventWrite

Ein Makro (oder -Methode) für jedes Ereignis im Manifest definierten (in der &lt;Ereignisse&gt; Knoten).

Sobald Ihr Code ordnungsgemäß instrumentiert ist, können Sie die Binärdatei erstellen.

Treiber finden Sie die Beispieldatenbank [EventDrv](http://go.microsoft.com/fwlink/?LinkId=256109) (https://code.msdn.microsoft.com/windowshardware/Eventdrv-42894135) auf MSDN. Registrieren Sie den Treiber als Ereignis vertraut, mithilfe von Kernelmodus ETW-EtwRegister-Funktion:

-   Fügen Sie diese Funktion in Ihrer Routine "DriverEntry" nach Code erstellt und initialisiert das Objekt.

-   Übereinstimmen Sie den Aufruf der Funktion EtwRegister mit einem Aufruf von EtwUnregister des Treibers Unload-Routine.

### <a name="log-and-visualize-events"></a>Melden Sie sich und Visualisieren Ereignisse

Nachdem Sie eine ordnungsgemäß instrumentierte Komponente verfügen, können Sie auf einem Testsystem Protokollieren von Ereignissen starten. Sie müssen zuerst, das System für die Protokollierung durch Registrieren des Anbieters mithilfe von Wevtutil des Posteingangs vorzubereiten.

1.  Kopieren Sie die Komponente an die Position, die durch das Attribut ResourceFileName im Manifest angegeben wurde:

    **Xcopy/y** *MyProviderBinary.exe* **%Temp%**

2.  Registrieren Sie die Anbieter:

    **Wevtutil um** *etwmanifest.man*<br/>
    **Wetvutil Sofortnachrichten** *etwmanifest.man*

3.  Stellen Sie sicher, dass der Anbieter angezeigt wird:

    **Logman-Abfrage-Anbieter** 

    Ihre Provider Name/GUID wird in der Liste angezeigt.

Beachten Sie, dass Ereignismetadaten in die instrumentierte Binärdatei, nicht in der Manifestdatei gespeichert ist. Wevtutil So installieren Sie ein Manifest auf dem PC mit versetzt einen Link in der Registrierung Herstellen einer Verbindung mit der Anbieter GUID die Binärdatei, die die Ereignismetadaten enthält. Der Name und Pfad der der Binärdatei stammt aus der Manifestdatei zur Verfügung gestellt. Sie können die Manifestdatei später verwerfen.

Dies bedeutet, dass die Binärdatei, die die Ereignismetadaten enthält auch verfügbar und können geladen werden muss, auf dem Computer unverändert verwenden Sie zum Decodieren. WPR/Xperf ist den Prozess besser portierbar, indem er die Metadaten in der Verfolgung einfügt.

Vom Dienstanbieter auf diesem System installiert ist, können Sie eine Tracingsitzung zum Sammeln von Ereignissen von der Komponente in einer ETL-Datei starten. Sie können Windows Performance-Aufzeichnung (WPR) oder Xperf, das Befehlszeilentool sowohl in Windows Performance Toolkit verfügbar.

1.  Starten Sie Protokollierung:

    **Xperf** **-Starten** *MySession* **-on** *MyEventProvider* **-f** *MySession.etl*

    In dieser Zeile Befehl **-Starten** bietet der Veranstaltung-Auflistung einen Namen, und **-auf** ETW teilt mit, dass Sie Ereignisse in dieser Sitzung aus Ihrem Anbieter zu erfassen möchten. (Es kann mehrere **-auf** Argumenten.)

2.  Führen Sie Ihre Arbeitslast.

3.  Beenden Sie die Protokollierung:

    **Xperf** **-Beenden** *MySession*

Nachdem Sie eine ETL-Datei haben, können sie mit dem Windows Performance Analyzer Tool öffnen und Visualisieren der Ereignisse mit generische Ereignisse Diagramm und Tabelle.

![Diagramm und Diagramme, die generische Ereignisse im Windows Performance Advisor (WPA).](images/weg-wpa-screen-generic-events-graph-and-table.jpg)

# <a name="performance-tools"></a>Leistungstools

Microsoft bietet Tools zur Verbesserung der Leistung des Geräts. Testtools von anderen Herausgebern können Sie messen und Verbessern der Leistung von sowie Ihre Geräte.

Dieser Abschnitt enthält Informationen zu den Windows ADK und Downloadlinks für die Windows-ADK und andere Tools von Microsoft Leistung.

## <a name="download-performance-tools"></a>Leistungstools herunterladen

Sie können diese Tools zum Bewerten und Verbessern der Leistung von Ihrem PC herunterladen.

<table>
<thead>
<tr class="header">
<th><strong>Tool</strong></th>
<th><strong>Beschreibung</strong></th>
<th><strong>Link herunterladen</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Windows Assessment and Deployment Kit (ADK)</td>
<td><p>Tools zum Bewerten und Bereitstellen von Windows-Bilder. Tools können in der Windows-ADK zur Verbesserung der Leistung des Computers unter Windows über die Mindestanforderungen für die Windows-HCK.</p>
<p>Enthält:</p>
<ul>
<li><p>Windows-Assessment-Toolkit</p></li>
<li><p>Windows-Assessment-Services</p></li>
<li><p>Windows Performance Toolkit (WPT)</p></li>
</ul></td>
<td>Verwenden Sie die neuesten ADK Drop aus verbinden.</td>
</tr>
<tr class="even">
<td>Windows Hardware Lab Kit (HLK)</td>
<td>Tools zu prüfen, ob Ihr Computer Windows die Kompatibilität erfüllt. Die Leistungstools können in Windows ADK zur Verbesserung der Leistung des Computers über die Windows HLK Anforderungen.</td>
<td>Verwenden Sie die neuesten HCK Drop aus verbinden.</td>
</tr>
<tr class="odd">
<td>PowerCFG.exe</td>
<td><p>Des Posteingangs Power Schemas (auch benannte Power Pläne), die Status verfügbar Standbymodus zu steuern, die den Status der einzelnen Geräte und das System analysiert verwendet für häufig vorkommender Probleme Energie-Effizienz und Akkulaufzeit gesteuert.</p>
<p>Eine <a href="http://go.microsoft.com/fwlink/p/?LinkID=264942">MSDN-Dokumentation</a> (https://technet.microsoft.com/en-us/library/hh824902.aspx?f=255&amp;MSPPError = 2147217396) neue Funktionen wie /sleepstudy möglicherweise noch nicht enthalten.</p></td>
<td>Posteingang.</td>
</tr>
<tr class="even">
<td>PwrTest.exe</td>
<td><p>Testen Sie Tool, mit dem ermöglicht Entwicklern, Testern und Systemintegratoren Übung und Aufzeichnen von Power Management-Informationen aus dem System. Sie können PwrTest automatisieren Standbymodus und Übergänge fortsetzen und Prozessor Power Management und Batterie Informationen aus dem System über einen Zeitraum aufzeichnen verwenden.</p>
<p>Weitere Informationen finden Sie unter <a href="http://go.microsoft.com/fwlink/?LinkId=309778">PwrTest</a> (https://msdn.microsoft.com/library/windows/hardware/ff550682.aspx).</p></td>
<td>Verfügbar in WDK (siehe unten).</td>
</tr>
<tr class="odd">
<td>Medienfunktionen Analyzer (engl.)</td>
<td>Media-Leistung, Qualität und Power-Analysetool, das vom Entwickler und Tester zum Optimieren der Geräte, auf denen Windows Media Szenarien verwendet wird. Mit diesem Tool können Sie die Fehler im Medienwiedergabe, erfassen Webcam und Real-Time Communications HCK Anforderungen zu analysieren.</td>
<td><a href="http://www.microsoft.com/en-us/download/details.aspx?id=43105">Downloadcenter</a> (http://www.microsoft.com/en-us/download/details.aspx?id=43105)</td>
</tr>
<tr class="even">
<td>Professional für Visual Studio 2012</td>
<td>Visual Studio Professional 2012 ist ein professionelles IDE, die die Aufgaben erstellen, Debuggen und Bereitstellen von Software für Windows, Microsoft Office und das Web vereinfacht.</td>
<td><a href="http://go.microsoft.com/fwlink/?LinkId=309780">MSDN</a><br />
(https://msdn.microsoft.com/en-us/windows/hardware/gg454513)</td>
</tr>
<tr class="odd">
<td>Windows-Treiberkits (WDK)</td>
<td>WDK integriert mit Visual Studio Professional 2012, um eine vollständige Umgebung für das Entwickeln, bereitstellen, testen und Debuggen Treiber bereitzustellen.</td>
<td>Verwenden Sie die neuesten WDK-Drop aus verbinden.</td>
</tr>
</tbody>
</table>


# <a name="understanding-the-windows-adk-tools"></a>Grundlegendes zu den Windows ADK-tools

Das Windows Assessment Toolkit und Windows Performance Toolkit besteht aus dem Windows Assessment and Deployment Kit (ADK). Zusammen bieten sie eine vollständige Lösung für das Auswerten gesamtleistung Computer und Automatisieren der Bereitstellung von Windows-Betriebssystems auf neuen PCs.

In diesem Abschnitt konzentriert sich auf das Windows Assessment Toolkit. Die Bewertungsergebnisse dienen zum potenzielle Probleme, die Hardware und apps, die Sie entwickeln vorhanden einen minimalen Auswirkung auf die Akkulaufzeit, Leistung beim Starten und Zeit zum Herunterfahren ist und reagieren, diagnostizieren. Die gleichen Bewertungsfragen stehen für OEMs, ISVs, unabhängigen Hardwareanbietern, Anhänger und andere Mitglieder der Community herstellen ein gemeinsamen Framework messen, vergleichen und überprüfen Sie verschiedene Aspekte der Qualität.

Wichtige Unternehmensziele können mithilfe des Windows Assessment Toolkit erreicht werden:

<dl>
<dt>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<strong>Messen und vergleichen</strong></dt>
<dd>
<p>Die Daten können Sie die Komponenten (apps, Treiber oder beides) mit anderen ähnlichen Komponenten vereinfachen Sie Ihre entscheidungsfindungen Empfehlungen und Mitbewerberprodukten benchmarking verglichen werden soll.</p>
</dd>
<dt>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<strong>Verbessern der Qualität</strong></dt>
<dd>
<p>Sie können eigenständig oder umfassen Partner, um eine Komponente (app, Treiber oder beides) gemäß den Anweisungen in vordefinierte Qualitätskriterien zu erstellen.</p>
</dd>
<dt>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<strong>Nachverfolgen der Qualität</strong></dt>
<dd>
<p>Erstellen eines Prozesses für die Qualität der Komponentenversionen effizient nachverfolgen und Regressionen nach jeder Iteration erkennen können.</p>
</dd>
</dl>


Das Assessment Toolkit ist in der Regel in folgenden Szenarien verwendet:

<table>
<thead>
<tr class="header">
<th>Szenario</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>&quot;Schwarz-Feld&quot;</td>
<td>Führen Sie einen vordefinierten Auftrag, und überprüfen Sie die Ergebnisse für ungewöhnliche Werte oder Anzeichen für Probleme mit Treibern, die Speicherverwendung oder andere Bereiche, die die Bewertung Adresse.</td>
</tr>
<tr class="even">
<td>Vergleichen der Ergebnisse</td>
<td><ul>
<li><p>Führen Sie eine einzelne Bewertung mithilfe der empfohlenen Einstellungen auf einem beliebigen Computer, auf denen ein unterstütztes Betriebssystem ausgeführt wird.</p></li>
<li><p>Verwenden Sie die Windows-AC zum Verpacken des Auftrags auf einem anderen Computer ausgeführt.</p></li>
<li><p>Speichern Sie die Ergebnisse auf eine Freigabe, damit Sie diese vergleichen können.</p></li>
<li><p>Vergleichen Sie die Ergebnisse von einem beliebigen Computer unter Windows mit denen der anderen Betriebssystem um Unterschiede zu identifizieren.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td>Bereinigten computer</td>
<td>Führen Sie Bewertung auf einem bereinigten Computer, die nur das Betriebssystem um System Basiswerte zu ermitteln.</td>
</tr>
<tr class="even">
<td>Computer mit hinzugefügten Hardware oder app-Komponenten</td>
<td>Fügen Sie neuer Hardware oder apps auf das Computersystem bereinigten hinzu und dann erneut führen Sie, um die Ergebnisse mit bereinigten Computer Ergebnissen Vergleichen der Bewertung aus.</td>
</tr>
<tr class="odd">
<td>Erstellen von Analysen</td>
<td>Verwenden Sie öffentliche APIs, um entwickeln oder Erweitern einer Bewertung oder integrieren Sie Bewertung in Ihre Tools und die Infrastruktur.</td>
</tr>
</tbody>
</table>

Weitere Informationen finden Sie unter [Windows-Analysen und Deployment Kit](http://go.microsoft.com/fwlink/?LinkId=206587) (https://msdn.microsoft.com/en-us/library/windows/hardware/hh825420.aspx).

<table>
<thead>
<tr class="header">
<th>Tool</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Windows-Assessment-Toolkit</td>
<td><p>Tools, zu ermitteln und Bewertung auf einem einzigen PC ausgeführt. <em>Bewertung</em> werden die Aufgaben, die Benutzeraktivität simulieren und den Status des PCs untersuchen. Bewertung Metriken für die verschiedenen Aspekte des Systems generieren und Vorschläge, für dessen Verbesserung. Das Windows Assessment Toolkit umfasst:</p>
<ul>
<li><p>Windows-Assessment-Konsole</p></li>
<li><p>Bewertung</p></li>
</ul>
<p>Weitere Informationen finden Sie unter <a href="http://go.microsoft.com/fwlink/?LinkId=214554">Windows Assessment Toolkit</a> (https://msdn.microsoft.com/en-us/library/windows/hardware/hh825508.aspx).</p></td>
</tr>
<tr class="even">
<td>Windows-Assessment-Services</td>
<td><p>App für die Remoteverwaltung von Einstellungen, PCs, Bilder und Bewertung in einer laborumgebung, auf dem Windows Assessment Services installiert ist. Diese app kann auf jedem PC ausgeführt, Zugriff auf den Server sind, auf denen Windows Assessment Services ausgeführt wird.</p>
<p>Weitere Informationen finden Sie unter <a href="http://go.microsoft.com/fwlink/?LinkId=215628">Windows Assessment Services</a> (https://msdn.microsoft.com/en-us/library/windows/hardware/hh825573.aspx).</p></td>
</tr>
<tr class="odd">
<td>Windows Performance Toolkit (WPT)</td>
<td><p>Tools zum Erfassen Systemereignisse mithilfe von Event Tracing for Windows und ein Tool zur Analyse von Leistungsdaten in eine grafische Benutzeroberfläche. Enthält:</p>
<ul>
<li><p>Windows Performance Aufzeichnung</p></li>
<li><p>Windows Performance Analyzer</p></li>
<li><p>Xperf</p></li>
</ul>
<p>Weitere Informationen finden Sie unter <a href="http://go.microsoft.com/fwlink/?LinkId=228914">Windows Performance Toolkit</a> (https://msdn.microsoft.com/en-us/library/hh162945.aspx).</p></td>
</tr>
<tr class="even">
<td>Assessment Ausführung Engine (AXE)</td>
<td><p>Assessment Ausführung Engine (AXE) können Sie verwalten, und führen Sie Windows-System-Bewertungen. AXE bietet Infrastruktur erforderlich zum Verwalten von Analysen über ein UX-Tool oder ein Skript Bewertung, stellen Maßangaben Rohdaten in Ergebnisse verarbeiten, führen Sie die Diagnose und veröffentlichen die Ergebnisse.</p>
<p>Weitere Informationen finden Sie unter <a href="http://go.microsoft.com/fwlink/?LinkId=309781">Assessment Execution Engine</a> (https://msdn.microsoft.com/library/windows/desktop/hh437709.aspx).</p></td>
</tr>
</tbody>
</table>


## <a name="understanding-the-windows-performance-toolkit"></a>Grundlegendes zu Windows Performance Toolkit

| Titel der Ressource                                               | Inhaltstyp  | Beschreibung                                                                                                                                                                                                                                                                                                                 | Verknüpfung |
|--------------------------------------------------------------|---------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------|
| Windows Performance Analyzer                                 | Dokumentation | WPT Dokumentation und videos                                                                                                                                                                                                                                                                                                | [MSDN](https://msdn.microsoft.com/en-us/library/windows/hardware/hh448170.aspx) (https://msdn.microsoft.com/en-us/library/windows/hardware/hh448170.aspx) |
| Verfahren zur Analyse der CPU                                      | Whitepaper   | Dieses Handbuch enthält ausführliche Techniken, die Sie verwenden können Central Processing Units CPU-Problemen, Auswirkungen Assessment Metriken untersuchen.                                                                                                                                                                       | [MSDN](http://msdn.microsoft.com/en-us/library/windows/desktop/jj679884.aspx) (https://msdn.microsoft.com/en-us/library/windows/desktop/jj679884.aspx) |
| Engineering-Leistung mit Windows Performance Toolkit | Video         | Windows Performance Toolkit (WPT) ist ein leistungsfähiges Tool, durch die Windows-Entwicklungsteams innerhalb von Microsoft zur Verbesserung der app und Systemleistung weit verwendet. In dieser Sitzung konzentriert sich auf die Bereitstellung von Tipps und Tricks, in einem Format Fallstudie mit Videos, für die Verwendung der WPT zusammen mit WPS Spuren zum Optimieren Ihrer eigenen apps. | [Channel 9](http://channel9.msdn.com/events/BUILD/BUILD2011/HW-59T) (http://channel9.msdn.com/events/BUILD/BUILD2011/HW-59T) |



# <a name="setting-up-a-test-environment-for-adk-and-was"></a>Einrichten einer testumgebung für ADK und WAS

Installieren von Windows Assessment Service (WAS) ist Server zu einem Server einfach. Konfigurieren der Netzwerkumgebung kann jedoch nicht so einfach. Falsche Netzwerktopologie kann aus verschiedenen Gründen Assessment Auftragsfehler verursachen. Es ist wichtig zu verstehen, Ihrer Organisation Anforderungen, Netzwerkrichtlinien und So weiter.

Bevor Sie beginnen, machen Sie sich mit diesen beiden Ressourcen:

-   [Schrittweise Anleitung für Windows Assessment Services](http://go.microsoft.com/fwlink/?LinkId=215630) (https://msdn.microsoft.com/en-us/library/windows/hardware/hh825315.aspx)

-   [Installieren von Windows Assessment Services](http://go.microsoft.com/fwlink/?LinkId=253667) (https://msdn.microsoft.com/library/windows/hardware/hh825515)

## <a name="network-topology-considerations"></a>Überlegungen zum Netzwerk-Topologie

In diesem Abschnitt werden die Punkte zu berücksichtigen, die zum Implementieren einer WAS-Infrastruktur in das Labor und einige optionalen Elemente zum Erreichen von zusätzlichen Features und der Automatisierung behandelt. Ziel ist es, ein lokales Netzwerk einrichten, können Sie besser "Hintergrundgeräusche" das, die zu Hause auftreten wird.

Diese Elemente sind erforderlich:

| Element               | Typ              | Hinweis |
|--------------------|-------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Ethernet           | Hardware          | WURDE Ethernet erfordert. Stabilität und Effizienz empfehlen wir Gigabit-Ethernet an. |
| Symbole            | Zugriff auf das Internet   | ADK des Auto-Analysis-Feature nicht ohne Symboldateien verwendet werden. Nach RTM Binärdateien des Betriebssystems über Windows Update aktualisiert werden, und die Datei darf nicht das Erfassen von aktualisierten Symboldateien praktische. Es wird empfohlen, dass Sie öffentliche Symbolserver verwenden, und die Symboldateien lokal für die Wiederverwendung zwischenspeichern.<br/><br/>Connect-Betriebssystem setzt verwenden die Pakete bereitgestellten Symbole und zwischengespeichert werden lokal auf dem Server, WAS. ||
| Wi-Fi Zugriffspunkt | Hardware          | Verbindung mit einem Wi-Fi-Netzwerk, bei der Ausführung der Energieeffizienz empfohlen. |
| DHCP-Server        | Hardware und Software | PXE-Start ist DHCP erforderlich. **WURDE der Server kann ein DHCP-Server sein**. Sie können einen Wi-Fi-Router als ein DHCP-Server verwenden. Wenn Sie nicht den Betriebssystemabbilds mithilfe von WAS über PXE-Neustart push möchten, müssen Sie nicht DHCP haben. |
| Dateifreigabe         | Hardware          | Je nachdem, wie Sie Ihre Ergebnisdateien speichern möchten. **Ergebnisse können auf dem Server, WAS auch gespeichert werden.** |
| USB-Laufwerke   | Hardware          | Sie können in Windows PE einen bare Metallen Computer WAS, beispielsweise eine Inventur starten. |

Diese Elemente sind nicht erforderlich, aber sind häufig je nach Ihren Anforderungen und Richtlinie Unternehmensnetzwerk erforderlich:

| Element                    | Typ              | Hinweis |
|-------------------------|-------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| DNS-Server              | Hardware und Software | In der Regel nicht erforderlich, einzelnes Subnetz, als Testnetzwerk ist. Wenn Sie mehrere Subnetze konfigurieren müssen, müssen Sie Namensresolution wie DNS-Server haben. |
| IP-Steuerelement Power-Switch | Hardware          | Sie können einen Schalter Power erwerben, den Sie Remote steuern können. Sie können dies um Energieeffizienz vollständig zu automatisieren. |
| USB zu Ethernet-Adapter | Hardware          | Einige Formularfaktoren keinen Ethernet. Sie können auch Wi-Fi verwenden. Es wird empfohlen, einen USB-Ethernet-Adapter mit Unterstützung für den Posteingang verwenden, damit Sie nicht entspannen Windows PE anpassen. |

Die folgende Abbildung zeigt eine mögliche Netzwerkkonfiguration.

![Diagramm eines Beispielnetzwerks von Geräten und Verbindungen.](images/web-diagram-network-example-configuration.png)

Meisten Unternehmen benötigen diese Art von testumgebung mit dem Unternehmensnetzwerk isoliert werden. Corporate IT-Richtlinien ermöglicht nicht angenommen haben einen eigenen DHCP-Server. Aber möglicherweise möchten Sie WAS zugreifen, damit Sie Remote Aufträge planen, Überwachen des Fortschritts und Überprüfen der Ergebnisse. Darüber hinaus können Leistungsdaten betroffen sein, wenn Sie sich im Unternehmensnetzwerk DUTs haben, da im Unternehmensnetzwerk besondere Netzwerkverkehr generieren kann.

Server werden in der Regel mit einem Ethernet Multiportadapter oder mehrere Ethernet-Adapter ausgestattet. Sie können wandeln Sie Ihre WAS Server mit mehreren Homeserver. Mit mehreren Homeserver verfügt über einen Ethernet-Adapter mit einer isolierten Testnetzwerk und eine andere mit dem Unternehmensnetzwerk verbunden. Mit dieser Konfiguration können Personen in Ihrer Organisation WAS ohne im Testlabor, über WASC oder Remote Desktop zugreifen.

## <a name="optional-sql-database"></a>Optional SQL-Datenbank

Windows Assessment Services können Sie auch importieren Ergebnisse von mindestens Windows Assessment Services Labs in einer zentralen Datenbank SQL konsolidierten Berichte zu erstellen. Die SQL-Datenbank ist eine optionale Komponente der WAS-Infrastruktur.

Beachten Sie, dass in dieser optional SQL Server-Datenbank gespeicherte Ergebnisse die Darstellungsschicht Assessment Plattform nicht enthalten und nicht in der Windows-Assessment-Services - Client (Windows ASC) angezeigt werden beibehalten. Diese Komponente ermöglicht das Entwickeln von benutzerdefinierten Berichten Lösungen zum Erfüllen der Anforderungen für die standardmäßig nicht behandelt WURDE / WAC reporting layer.

Den Befehl ResultsUtil können zum Konfigurieren des Servers WAS die Datenbank automatisch verwenden oder vorhandene führt zu importieren. Weitere Informationen finden Sie unter [Command-Line Options ResultsUtil](http://go.microsoft.com/fwlink/?LinkId=309787) (https://msdn.microsoft.com/library/windows/hardware/hh825313.aspx).

## <a name="symbol-files-symbol-server-symbol-cache"></a>Symbol, Dateien, Symbolserver, Symbolcache

In der Standardeinstellung WURDE legt die folgenden Informationen. Sie können diese Einstellungen mit dem Befehl Setx überschreiben, wenn Sie andere Symbolservern oder Standorten verfügen.

```
set _NT_SYMBOL_PATH=

\\<WASServer>\Relax\Symbols;srv*http://msdl.microsoft.com/download/symbols

set _NT_SYMCACHE_PATH=\\<WASServer>\Relax\Symcache
```

# <a name="onboarding-and-preparing-a-system-for-adk-testing"></a>Onboarding und Vorbereiten eines Systems ADK zu Testzwecken

**So richten Sie das Gerät ein**

1.  Schließen Sie das Gerät unter Test (DUT) an eine Stromquelle an, und schalten Sie ihn.

2.  Geben Sie die Seite Firmware Settings (z. B. drücken Sie F2 beim Starten).

3.  Legen Sie auf der Einstellungsseite für Firmware Folgendes ein:

    -   Wiederherstellen Sie alle Standardeinstellungen.

    -   Stellen Sie sicher, dass die DUT mit UEFI ohne CSM Starten konfiguriert ist.

4.  Installieren Sie das OEM-Bild auf der DUT. Wenn das Bild OEM bereits installiert ist, überspringen Sie diesen Schritt.

    Ausführen von Sysprep werksseitige unterstützt, und andere Prozesse Teil des Bereitstellungsprozesses OEM sein.

5.  Führen Sie den ersten Boot Eindruck aus.

    Verwendung &lt; *Systemmodell*&gt;-&lt;*Hardware Phase* (EV, DV- oder PV) &gt; - &lt; *Revisionsnummer* &gt; als den Computernamen (beispielsweise Frabrikam-ModelXYZ-PV-Rev. 1). Verwenden Sie immer den gleichen Namen auf, wenn bestimmtes Modell testen.

6.  Sie können ein lokales Administratorkonto anstelle von einem Microsoft-Konto für das Testen.

## <a name="policies-for-setting-up-the-device"></a>Richtlinien für das Einrichten des Geräts

-   Verkabelten oder OEMs bereitgestellte Netzwerkadapter sollte über USB-Adapter verwendet werden.

    -   Wenn Sie lokale Testen mit WAC oder vorgefertigter Aufträge verwenden, wird nicht verkabeltes LAN angewendet.

    -   Wenn Sie WAS verwenden, wird empfohlen, Analysen über verkabelten LAN bereitzustellen. Falls dies nicht möglich, sollten Sie Wireless verwenden.

    -   Aktivieren Sie nicht beim Herstellen einer Verbindung mit einem Netzwerk Freigabe.

-   UEFI sollten für alle DUTs aktiviert werden.

-   Alle DUTs sollte alle signiert zertifizierte Windows 8-Treiber vor dem Ausführen der Bewertungsfragen.

-   Keine externe Geräte sollten angeschlossen sein, es sei denn, sie mit dem System bereitgestellt werden.

    
## <a name="testing-the-device"></a>Testen das Gerät

**So testen Sie das Gerät**

<ol>
<li>
<p>Aktivieren Sie das System mit den entsprechenden Product Key ein.</p>
</li>
<li>
<p>Einige Betriebssystemkomponenten ändern Sie ihr Verhalten basierend auf einige WinSAT Metriken. Stellen Sie sicher, dass der WinSAT-Datenspeicher in den folgenden Pfad gefüllt wurde: <strong>%WINDIR%\performance\winsat\datastore\</strong></p>
<p>Sie können <strong>Winsat Prepop</strong> in einer Befehlszeile mit erhöhten Rechten ausgeführt wird oder der <a href="http://technet.microsoft.com/en-us/library/jj573887.aspx">Bereitstellung</a> (https://technet.microsoft.com/en-us/library/jj573887.aspx) folgen.</p>
</li>
<li>
<p>Führen Sie Windows Update, und installieren Sie alle Treiber und Windows-Updates (sogar optionalen Parameter).</p>
</li>
<li>
<p>Deaktivieren Sie automatische Updates, indem Sie in den Windows Update-Einstellungen auswählen <strong>nie Updates überprüfen</strong> . Sie können diesen Schritt automatisieren, indem Sie den folgenden Befehl aus einer Eingabeaufforderung mit erhöhten Rechten ausführen:</p>
<p><strong>Reg <strong>add</strong> &quot;HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\WindowsUpdate\Auto Update&quot; /v AUOptions/t REG_DWORD/d 1/f</strong></p>
</li>
<li>
<p>Verwenden Sie Geräte-Manager, um sicherzustellen, dass der DUT keine Probleme mit der Treiber oder Geräte verfügt.</p>
<img src="images/weg-device-manager-dysfunctional-device.png" width="311" height="74" alt="A dysfunctional device is identified in Device Manager."/>
<p>Untersuchen und Beheben von Problemen mit markiert alle Geräte ein &quot;! &quot;.</p>
</li>
<li>
<p>Laden Sie die neuesten Virus-Definitionsdateien und führt eine Überprüfung durch Verwenden der Standard-Modul-app.</p>
</li>
<li>
<p>Erzwingt die Ausführung von IdleTasks einmal pro Tag (wenn System getestet wird) um sicherzustellen, dass keine Wartungstasks ADK Assessment Ausführung beeinträchtigen. Führen Sie den folgenden Befehl aus einer Eingabeaufforderung mit erhöhten Rechten aus:</p>
<p><strong>Rundll32.exe advapi32.dll,ProcessIdleTasks</strong></p>
</li>
<li>
<p>Disable Windows Store aktualisiert werden, nachdem alle verfügbaren Updates anwenden.</p>
<ol type="a">
<li><p>Öffnen Sie die Einstellungen gespeichert, fahren Sie mit <strong>App-Updates</strong>.</p></li>
<li><p><strong>Meine App-Updates automatisch heruntergeladen</strong> auf <strong>Nein</strong>festgelegt.</p></li>
<li><p>Sie können diesen Schritt automatisieren, indem Sie den folgenden Befehl aus einer Eingabeaufforderung mit erhöhten Rechten ausführen:</p>
<p><strong>Hinzufügen von Reg &quot;HKLM\Software\Microsoft\Windows\CurrentVersion\WindowsStore\WindowsUpdate&quot; /v automatischen Download/t REG_DWORD/d 2/f</strong></p>
</li>
</ol>
</li>
<li>
<p>Aktivieren Sie die automatische Anmeldung.</p>
<ul>
<li>
<p>Bestimmte Bewertung Neustart des Rechners und müssen der Benutzer melden Sie sich vor dem Fortfahren der Bewertung ausführen. Seit die Bewertungsfragen oft die Startzeit messen, können Verzögerungen zurückzuführen, dass der Benutzer, der sich bei dem PC zu unvorhersehbaren Abweichung in der Metriken führen.</p>
</li>
<li>
<p>Bewährte Methode ist zum Aktivieren der automatischen Anmeldung für das Benutzerkonto, mit der Bewertung. Sie können die automatische Anmeldung konfigurieren, in der Registrierung unter dem folgenden Schlüssel: <strong>HKLM\Software\Microsoft\Windows NT\CurrentVersion\WinLogon</strong></p>
<p>Die folgenden fünf Werte sollte so konfiguriert werden.</p>
<table>
<thead>
<tr class="header">
<th>Wertname</th>
<th>Werttyp</th>
<th>Data</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>DefaultUserName</td>
<td>REG_SZ</td>
<td>&lt;<em>TestUserName</em>&gt;</td>
</tr>
<tr class="even">
<td>DefaultPassword</td>
<td>REG_SZ</td>
<td>&lt;<em>LOCALPASSWORD</em>&gt;</td>
</tr>
<tr class="odd">
<td>Automatische Anmeldung</td>
<td>REG_SZ</td>
<td>1</td>
</tr>
</tbody>
</table>
</li>
</ul>
</li>
<li>
<p>Weist das System Zugriff auf einen Server Timer, stellen Sie sicher, dass die Uhr mit der Serverzeit synchronisiert wurde. Wenn während der Ausführung der Bewertung die Systemzeit geändert wird, kann dies zu Fehlern führen.</p>
</li>
<li>
<p>Deaktivieren Sie die Windows-System-Wiederherstellung, um Systemwiederherstellung Erstellung während des Tests angeben, den Testergebnis skew würde:</p>
<p><strong>Hinzufügen von Reg &quot;HKLM\Software\Microsoft\Windows NT\CurrentVersion\SystemRestore&quot; /v RPSessionInterval/t REG_DWORD/d 0/f</strong></p>
<p><strong>REG DELETE &quot;HKLM\Software\Microsoft\Windows NT\CurrentVersion\SPP\Clients&quot; /f</strong></p>
</li>
<li>
<p>Deaktivieren Sie die Defragmentierung der geplanten Festplatte:</p>
<p><strong>SCHTASKS/Change/TN &quot;Microsoft\Windows\Defrag\ScheduledDefrag&quot; /deaktivieren</strong></p>
</li>
<li>
<p>Stellen Sie sicher, dass alle .NET Kompilierung Ziele auf dem aktuellen Stand sind:</p>
<p><strong>C:\WINDOWS\Microsoft.NET\Framework\v4.0.30319\ngen.exe executequeueditems</strong></p>
<p><strong>C:\WINDOWS\Microsoft.NET\Framework64\v4.0.30319\ngen.exe executequeueditems</strong></p>
</li>
<li>
<p>Starten Sie die DUT neu.</p>
</li>
</ol>


