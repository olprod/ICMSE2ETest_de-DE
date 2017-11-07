---
title: "Ergebnisse für die Bewertung Speicherbedarf"
description: "Ergebnisse für die Bewertung Speicherbedarf"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: fd625d98-5d3a-401d-9639-516135f8d968
ms.prod: W10
ms.mktglfcycl: plan
ms.sitesec: msdn
ms.openlocfilehash: 19978b55118965547a8f33e0567f9a610d7b9741
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="results-for-the-memory-footprint-assessment"></a>Ergebnisse für die Bewertung Speicherbedarf


Dieses Thema enthält Informationen die Metriken, die mit der Bewertung Speicherbedarf interpretiert werden. Er enthält außerdem Hinweise zum Verwenden der Ergebnisse zu identifizieren und beheben eine Anzahl von häufig auftretender Probleme, die sich negativ auf die Kunden auswirken. Speicher ist eine wichtige Ressource, und Optimieren der Speicherverwendung stellt eine konsistente und flexible Umgebung sicher.

Diese Bewertung erstellt eine Momentaufnahme der Speicherverwendung während der eine Reihe von nach einem Neustart des Systems und unmittelbar nach der Darstellung von der Startseite in Windows 8 oder Windows 10. Es wird nicht Speicherverwendung während der normalen Computer Vorgänge ausgewertet. Jedoch können Sie die Ergebnisse der Speicherbedarf Bewertung um zu verstehen, wie Arbeitsspeicher genutzt wird vor der Anwendung gestartet werden. Viele Prozesse und Dienste sind in verwenden, mit denen die Zeit und Speicherplatz. Diese Bewertung können Sie sehen, wie Treiber und Anwendungen, die immer Auswirkung des Startvorgangs ausgeführt.

**Hinweis**  
Der zu prüfenden Computer sollte Verkaufsversionen der Treiber installiert haben, um ein genaues Bild der Arbeitsspeicher Zuweisungen erhalten möchten.

 

In diesem Thema:

-   [Ziele-Datei](#bkmk-goals)

-   [Metriken](#bkmk-memorymetrics)

-   [Probleme](#bkmk-memoryissues)

Weitere Informationen zur Bewertung, Systemanforderungen und Bewertung Einstellungen finden Sie unter [Speicherbedarf](memory-footprint.md).

## <a name="a-href-idbkmk-goalsagoals-file"></a><a href="" id="bkmk-goals"></a>Ziele-Datei


Sie können benutzerdefinierte Ziele Ihrer Verbesserungen in der Ergebnisanzeige gemessen erstellen. Ziele Dateien sind eine Ursachenanalyse-Tool, das helfen zu verstehen, wie ein PC ausgeführt wird und zum Vergleichen von PCs in Ihrem Unternehmen.

Beispielsweise Ziele für einen einfachen Laptop möglicherweise nicht die Ziele für eine große Desktopcomputer festgelegten oder Markt erwartet können sich so, dass Sie die Flexibilität benötigen, um verschiedene Ziele zu definieren und verbessert die wichtige Anforderungen als Zeit und Technologie ändern.

Wenn an das Ziel dieser Metrik ein metrischer Wert verglichen wird, wird der Status farblich in der Ansicht Ergebnis wie folgt:

-   Hellviolett bedeutet, dass das System einen größeren Benutzerkomfort verfügt und keine wahrgenommene Probleme vorliegen.

-   Mittlere Lila bedeutet, dass das Benutzererlebnis zulässige ist und Sie können das System optimieren. Überprüfen Sie die Empfehlungen und Analyse, um herauszufinden, welche Verbesserungen an das System hergestellt werden können. Dabei kann es sich um Software Änderungen, konfigurationsänderungen oder Hardware suchen handeln.

-   Dunkles Lila bedeutet, dass das System benutzerfreundlich verfügt und erhebliche Platz für Verbesserungen vorhanden ist. Überprüfen der Empfehlungen und Analyse um die Verbesserungen anzuzeigen, die mit dem System hergestellt werden kann. Dabei kann es sich um Software Änderungen, konfigurationsänderungen oder Hardware suchen handeln. Möglicherweise müssen Sie Kompromisse hochwertige übermitteln, die Windows-Erfahrung erwägen.

-   Keine Farbe bedeutet, dass keine Ziele für die Metrik definiert sind.

**Hinweis**  
In der Windows Assessment Toolkit für Windows 8 umfassen einige Bewertung Ziele Standarddateien. Zum ersten Mal anzeigen von Ergebnisse mit dieser Version der Tools wird die Ziele-Standarddatei verwendet. Jedoch können Sie auch benutzerdefinierte Ziele für Windows 8 die gleiche Weise definieren, die Sie für Windows 8.1 und Windows 10 können.

 

Sie können legen Sie die Ziele und eine Datei Ziele zu diesem Speicherort hinzufügen, bevor Sie die Benutzeroberfläche verwenden können, um die benutzerdefinierten Ziele anzuwenden. Nach dem Auswählen einer Datei Ziele wird weiterhin die Ziele-Datei sein, die für alle Ergebnisse verwendet wird, die geöffnet werden.

Zu einem Zeitpunkt kann nur eine Ziele Datei verwendet werden. Ziele für alle Bewertung sind in einer einzigen Ziele Datei festzulegen. Die Bewertungstools sucht Ziele in der folgenden Reihenfolge:

1.  Eine benutzerdefinierte Ziele-Datei

2.  Ziele, die in der Ergebnisdatei definiert sind

3.  Ziele, die im Manifest Assessment definiert sind

Sie können die Ziele Beispieldatei, das bereitgestellt wird unter ProgramFiles%\\Windows Kits\\10\\Assessment and Deployment Kit\\Windows Assessment Toolkit\\SDK\\Beispiele\\Ziele zum Erstellen Ihrer eigenen Ziele Datei.

**Hinweis**  
Eine Datei Ziele mit einem Auftrag keine Pakete, aber Sie können auf einer anderen Personen zur Freigabe speichern.

 

## <a name="a-href-idbkmk-memorymetricsametrics"></a><a href="" id="bkmk-memorymetrics"></a>Metriken


Verschiedene Faktoren beeinflussen die Speicherverwendung eines Computers. Zu diesen Faktoren zählen Architektur, Arbeitsspeicher, Edition des Betriebssystems, Grafikkonfiguration, Computerklasse, Sprache und Netzwerkkonnektivität. Speicherbedarf wird die Größe des physischen Arbeitsspeichers, die ein Programm verwendet oder während der Ausführung verweist. Speicherbedarf umfasst Folgendes:

-   Binärdateien, Dynamic Link Libraries (DLLs) und andere ausführbaren Dateien, die in den Arbeitsspeicher geladen werden

-   Dynamische Zuweisungen, einschließlich Heap/VA

-   Treiber Zuweisungen, in erster Linie im Pool, Symbol, Tabellen und Stapel

Höherer Speicherbedarf von einem Computer vertraut sind, können Sie die Möglichkeiten zur Verbesserung von Leistung und Effizienz identifizieren. Optimieren des Speichers wird erstellt ein Betriebssystem effizienter und skalierbarer, erhöht den Arbeitsspeicher, der für Anwendungen und Prozessen verfügbar ist, und verbessert die Leistung unter einer Arbeitslast erhöht oder erweitern.

Diese Bewertung liegt der Schwerpunkt auf der folgenden Nutzung des Systemspeichers:

-   Treiber Zuweisungen, die während des Startvorgangs für ausgelagerte Pool-, die nicht ausgelagerten Pools und Treiber gesperrt Seiten bereitgestellt werden.

-   Dynamische Zuweisungen, die durch Boot Applications, Antiviren- und weitere Software vorgenommen werden. Diese verbleiben im Arbeitsspeicher nach dem Startvorgang, wenn das System durchgehend leuchtet werden.

**Optimierung von belegter Arbeitsspeicher**

Speicherverwendung wirkt sich auf Leistung, da Computer mehr Code und Daten als ﬁt im physischen Arbeitsspeicher können zugreifen können. Beispiel:

-   Gesamtmenge des physischen Arbeitsspeichers ist des Arbeitsspeichers auf einem System.

-   Verfügbare Arbeitsspeicher ist der Teil dieses RAM, die für den Benutzer Applikationen verfügbar ist, nachdem die erforderlichen System- und Boot in den Arbeitsspeicher geladen wurden.

-   Verwendet enthält Arbeitsspeicher alles ausführen beim Starten abgeschlossen ist und der Desktop oder Start-Bildschirm angezeigt wird.

Die Bewertung Speicherbedarf Listet den Inhalt des Speichers in Verwendung zu Herstellern und System-Builder Optimieren der Systemleistung von den Computern, die sie erstellen. Die Bewertung werden die Arbeitsspeicher Zuweisungen Faktoren und Boot Applikationen behandelt.

Belegter Arbeitsspeicher enthält mehr als nur die Windows-Systemprozesse. Sie können dieses Assessment um zu verstehen, was im Speicher nach dem Start ist verwenden. Anschließend können Sie versuchen, senken oder einsparen einige unnötige oder übermäßig viele Arbeitsspeicher Zuweisungen in den Kategorien Arbeitsseiten, nicht ausgelagerte Arbeitsspeicher und geänderte Seiten. Optimieren der Größe des Arbeitsspeichers verwendeten hat die Auswirkung der Verschiebung, die Speicher für die Kategorie verfügbarer Arbeitsspeicher freigegeben. Dadurch wird die Menge des Arbeitsspeichers in den Kategorien freien / standby erhöht. In der folgenden Tabelle werden die Kategorien beschrieben.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Allgemeine Speicher-Kategorie</th>
<th>Unterkategorien Speicherverwendung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Gesamtspeichers</p></td>
<td><p>Belegter Arbeitsspeicher + verfügbarer Arbeitsspeicher</p></td>
</tr>
<tr class="even">
<td><p>Belegter Arbeitsspeicher</p></td>
<td><p>Arbeitsseiten nicht ausgelagerte Arbeitsspeicher + geänderte Seiten</p></td>
</tr>
<tr class="odd">
<td><p>Verfügbarer Arbeitsspeicher</p></td>
<td><p>Standby-Speicher + freien Speicher</p></td>
</tr>
</tbody>
</table>

 

Die Bewertung Speicherbedarf bietet eine ausführlichere Beschreibung der Speicherverwendung unterscheidet Task-Manager.

Die Metriken, die mit dieser Bewertung anzeigen einen quantitativen Überblick über die Verwendung von Systemspeicher. Einige der folgenden Metriken zusätzlichen Arbeitsspeicher Parameter haben, die verfügbar gemacht werden können, die **Group By** Dropdown-Liste erweitern. Die folgenden Metriken werden während der Bewertung Speicherbedarf gemessen.

### <a name="available-memory"></a>Verfügbarer Arbeitsspeicher

Die verfügbaren Arbeitsspeicher in Megabyte insgesamt wie im Task-Manager nach dem Start dargestellt. Verfügbare Arbeitsspeicher ist verwendeten Speicher Gesamtspeichers subtrahiert. Dazu gehören freien Speicher, standby-Speicher und Seiten auf der standby-Liste.

### <a name="memory-in-use"></a>Verwendeter Speicher

Die Summe der-navigierbaren Arbeitsspeicher in Megabyte und alle Zuweisungen in Prozess Arbeitsseiten oder geänderte Arbeitsseiten.

### <a name="standby-memory"></a>Standby-Speicher

Der standby Arbeitsspeicher in Megabyte. Standby-Speicher ist verfügbar, wie eine Anwendung benötigt. Der Wert der standby-Seiten ist die Menge der zwischengespeicherten Daten und Dateien, die im Arbeitsspeicher, jedoch nicht in aktiv verwendet werden.

### <a name="total-memory"></a>Gesamtspeichers

Den gesamten verfügbaren Speicherplatz in Megabyte, wie im Task-Manager nach dem Start dargestellt. Der Wert der Gesamtzahl der Seiten beträgt der Arbeitsspeicher, die angezeigt wird, nachdem das Betriebssystem seinen Anteil zuweist.

### <a name="driver-paged-allocations"></a>Treiber auf ausgelagerten Zuweisungen

**Am besten:** Entwickler, OEMs

Entwickler können diese Nummer mit der Art und Weise beeinflussen, die der Treiber implementiert wird. OEMs können diese Nummer durch Hinzufügen oder Entfernen von Geräten aus dem System beeinflussen.

Dies ist der Arbeitsspeicher, der vom Treiber zugeordnet, und es wird von der Auslagerungsdatei gesichert. Dies bedeutet, dass der Speicher ausgelagert werden auf den Datenträger, um Platz für andere Code oder Daten, und klicken Sie dann später über ein hard Fault abgerufen werden konnte. Diese Metrik nur die Daten, die von der Treiber zugeordnet ist, und schließt nicht den Speicherplatz erforderlich, um den Treiber in den Arbeitsspeicher zu laden. Weitere Informationen zu navigierbaren Code finden Sie unter [Treiber ausgelagert Code](#memmetrics-driverpagedcode).

**Detaillierte untergeordnete Metriken**

Die Bewertung unterteilt diese Zuweisungen Arbeitsspeicher von der Sitzung, die, der Sie in auftreten. Sitzung 0 wird vom System für Dienste und Prozesse verwendet. Die erste Sitzung des Benutzers ist Sitzung 1. Nicht-Sitzung enthält Zuweisungen vom System unabhängig von einer einzelnen Sitzung.

**Typische Schlüsselfaktoren Faktoren**

OEMs können diese Metrik von Hardware- oder, dessen Treiber unteren Arbeitsspeicherbedarf hat, Auslagerung beeinflussen. Darüber hinaus können OEMs die Anzahl der Geräte, auf dem System reduzieren. OEMs sollten wissen, was Treiber auf dem System und was sind Speicher, die sie verwenden.

**Analyse und Schritte zur Wiederherstellung**

Hersteller des Treibers hat die meisten Einfluss auf diese Metrik die Art und Weise, wie er entwirft den Treiber. Eine Liste der Zuweisungen aufgeladen wird an alle Treiber im System ist verfügbar. Darüber hinaus können die Treiber Herstellern WPA Spuren (gespeichert im gleichen Verzeichnis befindet wie die Ergebnisse Assessment) für die Bewertung zugewiesen werden. Diese können verwendet werden, können Bereiche der extra fette Arbeitsspeicher Zuweisungen ermitteln, die für die Untersuchungen in Reduzieren der Speicherverwendung geeignet sind.

### <a name="driver-non-paged-allocations"></a>Treiber nicht ausgelagerten Zuweisungen

**Am besten:** Entwickler, OEMs

Entwickler können diese Nummer mit der Art und Weise beeinflussen, die der Treiber implementiert wird. OEMs können diese Nummer durch Hinzufügen oder Entfernen von Geräten aus dem System beeinflussen.

Diese Metrik ähnelt der ausgelagerten Zuweisungen diese Zuweisungen physischen Arbeitsspeicher zu verwenden, die nicht ausgelagert werden können. Dies gilt für physischen Arbeitsspeicher, der fixiert ist, und daher ist nicht verfügbar für ausgelagerten Arbeitsspeicher oder andere Prozesse und Dienste verwendet werden soll. Gesichert, Arbeitsspeicher Erwerb zu viel nicht ausgelagerten Arbeitsspeicher die Menge des Arbeitsspeichers verringert, die von der Seite verwendet werden kann.

Nicht ausgelagerter Speicher Zuweisungen müssen manchmal für einen Treiber Datenstrukturen, die während der Ausführung von Interrupt Service Routinen (ISRs) zugegriffen werden müssen und zurückgestellt Prozeduraufrufe (DPCs). ISRs und DPCs werden Funktionen im Zusammenhang mit Hardwareinterrupts und Seitenfehler können nicht während der Ausführung dieser Funktionen auftreten. Deshalb muss der Treiber diese Datenstrukturen in nicht ausgelagerter Pool zuweisen, um alle Abstürze zu vermeiden.

**Detaillierte untergeordnete Metriken**

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Untergeordnete Metrik</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Treiber gesperrt Systemseiten</p></td>
<td><p>Dies ist der Arbeitsspeicher, die aus dem ausgelagerten Speicher geladen und dann vom Treiber gesperrt, bis es nicht mehr benötigt werden. Ein Beispiel hierfür wäre ein Gerät wie ein Modem, das sporadisch verwendet wird. Es ist keine beim Laden der Code für dieses Gerät, bis sie verwenden, und klicken Sie dann einige der Daten und Code muss gesperrt werden, damit es nicht ausgelagert werden kann wird.</p></td>
</tr>
<tr class="even">
<td><p>Zusammenhängenden</p></td>
<td><p>Dies ist nicht ausgelagerte zusammenhängender Arbeitsspeicher. In den Kernel-Adressraum geladenen Code muss, damit es nicht ausgelagert werden wird gesperrt werden. Dies ist eine häufige Ursache für Fehler in Treiber. Das System muss, ohne den resultierenden Codepfad So rufen eine Auslagerungsdatei müssen auf Hardwareinterrupts reagieren können.</p>
<p>Treiber gesperrt Systemseiten verweist auf eine Arbeitsspeicher Deskriptor Liste (MDL). MDL ist eine systemdefinierte-Struktur, die einen Puffer durch eine Reihe von physischen Adressen beschreibt. Ein Treiber, der direkte e/a führt erhält einen Zeiger auf eine MDL aus dem e/a-Manager, und liest und schreibt Daten über die MDL. Einige Treiber verwenden auch MDLs beim Durchführen direkter e/a zu eine Gerät e/a-Anforderung erfüllen. Der Microsoft Windows-Speicher-Manager eine MDL für ein Gerät lesen erstellt, gesperrt physische Seiten, die für das Ziel der Übertragung verwendet. Es ist jedoch nur bis zu der Speicher-Manager, um zu bestimmen, welche beibehalten und die (falls vorhanden) Seiten verwerfen.</p></td>
</tr>
<tr class="odd">
<td><p>EX</p></td>
<td><p>Dies ist die ausführbare nicht ausgelagerten Speicher, der in einem Bereich von Arbeitsspeicher zum Ausführen von Code stillgelegte zugewiesen wird.</p></td>
</tr>
<tr class="even">
<td><p>N X</p></td>
<td><p>Ein Typ von nicht ausgelagerten Pools wurde eingeführt, die nicht ausführbar ist (n x Pool). Da es nicht ausführbar ist, sichererer im Vergleich zu ausführbare nicht ausgelagerte Pool (Pool NP) ist und bietet eine bessere Schutz gegen Überlaufangriffe.</p></td>
</tr>
</tbody>
</table>

 

**Typische Schlüsselfaktoren Faktoren**

OEMs können diese Metrik durch Auslagerung Hardware- oder Treiber, unteren Arbeitsspeicherbedarf beeinflussen.

**Analyse und Schritte zur Wiederherstellung**

Der Hersteller hat die meisten Einfluss auf diese Metrik die Art und Weise wie der Treiber entwickelt. Suchen Sie nach großer Arbeitsspeicher Zuweisungen in den Ergebnissen in der Windows-Assessment-Konsole angezeigt. Darüber hinaus können die Treiber Herstellern erhalten WPA Spuren (gespeichert im gleichen Verzeichnis befindet wie die Ergebnisse Assessment) dieser Beurteilung Bereiche der Zuweisung von virtuellem Speicher extra fette suchen, die für die Untersuchungen in Reduzieren der Speicherverwendung geeignet sind.

### <a name="a-href-idmemmetrics-driverpagedcodeadriver-paged-code"></a><a href="" id="memmetrics-driverpagedcode"></a>Treiber auf ausgelagerten Code

**Am besten:** Entwickler, OEMs

Der Hersteller hat den größten Einfluss auf diese Metrik. OEMs können diese Metrik durch Auslagerung Hardware und Software Treiber, unteren Arbeitsspeicherbedarf beeinflussen.

Dies ist für den Treiber ausgelagert Code belegter Arbeitsspeicher. Dieses vorhanden ist, desto wahrscheinlicher, dass einen Teil davon auf Datenträger, erfordern ein hard Fault wieder bei Bedarf zu beenden ausgelagert wird. Dies kann zu einer bedeutende Auswirkung zur Benutzerinteraktion führen. Darüber hinaus können hohe Arbeitsspeicher Zuweisungen zu der Seite Operating System häufig verwendete Code führen, die auch wurde ist. Der, desto höher das Risiko ausgelagert ist ein schwerer Fehler treten häufig zu reaktivieren, um, mehrere verwendet.

**Detaillierte untergeordnete Metriken**

Dies ist eine Liste der die Binärdateien und die Größe des Arbeitsspeichers in Kilobyte. Sie können die Liste nach Größe sortieren, indem Sie mit der rechten Maustaste auf die Kopfzeile "Size" und "Aufsteigend sortieren" auswählen.

**Typische Schlüsselfaktoren Faktoren**

OEMs können diese Metrik durch Auslagerung Hardware- oder Treiber, unteren Arbeitsspeicherbedarf beeinflussen.

**Analyse und Schritte zur Wiederherstellung**

Der Hersteller hat die meisten Einfluss auf diese Metrik die Art und Weise wie der Treiber entwickelt. Suchen Sie nach großer Arbeitsspeicher Zuweisungen in den Ergebnissen in der Windows-Assessment-Konsole angezeigt. Darüber hinaus können die Treiber Herstellern erhalten WPA Spuren (gespeichert im gleichen Verzeichnis befindet wie die Ergebnisse Assessment) dieser Beurteilung Bereiche der extra fette Arbeitsspeicher Zuweisungen suchen, die für die Untersuchungen in Reduzieren der Speicherverwendung geeignet sind. OEMs sollten beachten, dass das Gerät zu ersetzen oder erste Treiber aktualisiert.

### <a name="driver-non-paged-code"></a>Treiber nicht ausgelagerten Code

**Am besten:** Entwickler, OEMs

Der Hersteller hat den größten Einfluss auf diese Metrik. OEMs können diese Metrik durch Auslagerung Hardware-Treiber, die unteren Arbeitsspeicherbedarf beeinflussen.

Diese Metrik ist die Menge des Arbeitsspeichers, die zugewiesen und kann nicht in die Auslagerungsdatei ausgelagert werden. Dies umfasst des Arbeitsspeichers für Code, nicht für die Daten. Dies gilt für physischen Arbeitsspeichers, die dauerhaft in Verwendung ist und daher ist für ausgelagerter Speicher nicht verfügbar.

**Detaillierte untergeordnete Metriken**

Dies ist eine Liste der die Binärdateien und die Größe des Arbeitsspeichers in Kilobyte. Sie können die Liste nach Größe sortieren, indem Sie mit der rechten Maustaste auf die Kopfzeile der **Größe** und auswählen **Absteigend sortieren**.

**Typische Schlüsselfaktoren Faktoren**

OEMs können diese Metrik durch Auslagerung Hardware- oder Treiber, unteren Arbeitsspeicherbedarf beeinflussen.

**Analyse und Schritte zur Wiederherstellung**

Der Hersteller hat die meisten Einfluss auf diese Metrik die Art und Weise wie der Treiber entwickelt. Suchen Sie nach großer Arbeitsspeicher Zuweisungen in den Ergebnissen in der Windows-Assessment-Konsole angezeigt. Darüber hinaus können die Treiber Herstellern erhalten WPA Spuren (gespeichert im gleichen Verzeichnis befindet wie die Ergebnisse Assessment) dieser Beurteilung Bereiche der extra fette Arbeitsspeicher Zuweisungen suchen, die für die Untersuchungen in Reduzieren der Speicherverwendung geeignet sind.

### <a name="process-private-pages"></a>Prozess Private Seiten

**Am besten:** OEMs

OEMs können diese Metrik durch Verringern der Anzahl der "immer ausführen" Applications (Anwendungen in den Registrierungsschlüssel ausführen oder in den Startordner) beeinflussen. OEMs sieht für Software, die sie auf der Basis der erste Microsoft-Abbild hinzugefügt haben.

Speicher ist (d. h. freigegebenen oder nicht freigegebene privat). Es spielt keine Rolle, wie der Speicher entweder über eine Zuweisung oder eine Arbeitsspeicherdatei gesichert belegt wurde. Wenn Sie zwei Microsoft Word-Dokumente öffnen, beispielsweise, Teil des Speichers (Code) zwischen den beiden Instanzen, da gemeinsam genutzt werden können ist die Anwendung identisch. Die Daten in Word-Dokumenten ist jedoch unterschiedlich jede Instanz privaten Speicher reserviert werden muss. Die Prozess Private Seiten Metrik zeigt, wie viel privaten Speicher von jeder binäre Komponente, die in den Drillthrough nach unten aufgeführten belegt wird. Diese Metrik enthält keinen gemeinsam genutzten Speicher.

Freigegebenen Speicher ist Speicher, die reserviert und an einen Prozess zugewiesen. Wenn der Kernel eine neue Anforderung für diesen Speicher, dass sie schnell Antworten kann erhält mithilfe von einfach den bereits reservierten Speicher erneut. Dies muss jedoch einen Block von read-only Memory ihr Status als "freigegebenen" verwalten. Nachdem mindestens einer der anderen Prozess möchte Schreiben auf den freigegebenen Speicher ein neuer Block zugewiesen werden, und der Kernel verwendet den neuen Block für die Anforderung "Write". Kernel muss mindestens einen Block von Arbeitsspeicher für die Anforderung zuweisen, unabhängig davon, wie viel Arbeitsspeicher geschrieben wird. Damit, auch wenn wir ein Byte in einen freigegebenen Speicher schreiben wollten, der Kernel befasst sich in Blöcken des Arbeitsspeichers damit müsste einen 4 KB-Block zuordnen.

**Detaillierte untergeordnete Metriken**

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Untergeordnete Metrik</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Active</p></td>
<td><p>Dies ist eine Liste der Binärdateien und ihren Beitrag zu Gesamtspeichers verwendet wird. Dieser Speicher ist aktiv.</p></td>
</tr>
<tr class="even">
<td><p>Standby</p></td>
<td><p>Dies ist eine Liste der Binärdateien und ihren Beitrag zu Gesamtspeichers verwendet wird. Dieser Speicher ist erforderlich, auf der standby-Liste, die Speicher ist, die noch im physischen Speicher ist aber als nicht mehr markiert wurde. Dies ist der Arbeitsspeicher, die zuerst durch neue Arbeitsspeicher vom Speichermanager ausgelagert oder verschoben werden bei Bedarf wieder in der Liste der aktiven ersetzt werden.</p></td>
</tr>
</tbody>
</table>

 

**Typische Schlüsselfaktoren Faktoren**

OEMs können diese Metrik durch Auslagerung Softwaretreiber, unteren Arbeitsspeicherbedarf beeinflussen.

**Analyse und Schritte zur Wiederherstellung**

Treiber und Softwarehersteller haben die meisten Einfluss auf diese Metrik durch die Möglichkeit, den, die entsprechenden Code entwickelt wurde. Suchen Sie nach großer Arbeitsspeicher Zuweisungen in den Ergebnissen in der Windows-Assessment-Konsole angezeigt. Darüber hinaus können der Softwarehersteller erhalten WPA Spuren (in demselben Verzeichnis wie die Bewertungsergebnisse gespeichert) dieser Beurteilung können Bereiche der extra fette Arbeitsspeicher Zuweisungen ermitteln, die Kandidaten für Untersuchungen in Speicherverwendung reduziert werden. Sorgfältige Analysen der Zuweisungen, selbst bei kleinen Datenbanken, Hilfe den Entwickler Zuweisungen suchen, die Sie hinzufügen.

### <a name="binaries-in-use"></a>Binärdateien (In Verwendung)

**Am besten:** OEMs

OEM kann diese Nummer durch Hinzufügen oder Entfernen von Geräten aus dem System beeinflussen. Darüber hinaus verwenden einige-Software und-Diensten Kernelmodus-Treiber. Suchen Sie nach Software in der Startpfad oder immer-Software und-Diensten ausgeführt. Die Software selbst kann nicht großer Arbeitsspeicher Zuweisungen anzeigen, aber wird der Prozess Abhängigkeiten, die große Arbeitsspeicherbedarf hätte haben.

Dies ist eine Liste von Binärdateien, die für deren Verwendung reserviert Arbeitsspeicher kommuniziert haben. Dies ist eine andere Möglichkeit zum Anzeigen der Daten in andere Metriken offen gelegt. Hierbei handelt es sich um alle Zuweisungen, die einer bestimmten Binärdatei zugeordnet.

**Detaillierte untergeordnete Metriken**

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Untergeordnete Metrik</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Active</p></td>
<td><p>Dies ist eine Liste der Binärdateien und ihren Beitrag zu Gesamtspeichers verwendet wird. Dieser Speicher wird verwendet.</p></td>
</tr>
<tr class="even">
<td><p>Standby</p></td>
<td><p>Dies ist eine Liste der Binärdateien und ihren Beitrag zu Gesamtspeichers verwendet wird. Dieser Speicher ist auf der standby-Liste, die Arbeitsspeicher, die noch im physischen Speicher ist aber als nicht mehr markiert wurde, ist erforderlich. Dies ist der Arbeitsspeicher, die zuerst durch neue Speicher ausgelagert vom Manager Arbeitsspeicher oder verschoben werden bei Bedarf wieder in der Liste der aktiven ersetzt werden.</p></td>
</tr>
</tbody>
</table>

 

**Typische Schlüsselfaktoren Faktoren**

OEMs können diese Metrik durch Auslagerung Hardware- oder Treiber, unteren Arbeitsspeicherbedarf beeinflussen. Darüber hinaus können OEMs die Anzahl der Geräte, auf dem System reduzieren.

**Analyse und Schritte zur Wiederherstellung**

Der Hersteller hat die meisten Einfluss auf diese Metrik die Art und Weise wie der Treiber entwickelt. Suchen Sie nach großer Arbeitsspeicher Zuweisungen in den Ergebnissen in der Windows-Assessment-Konsole angezeigt. Darüber hinaus können die Treiber Herstellern erhalten WPA Spuren (gespeichert im gleichen Verzeichnis befindet wie die Ergebnisse Assessment) dieser Beurteilung Bereiche der extra fette Arbeitsspeicher Zuweisungen suchen, die für die Untersuchungen in Reduzieren der Speicherverwendung geeignet sind.

### <a name="map-files"></a>Zuordnen von Dateien

**Am besten:** OEMs Softwarehersteller

OEMs können diese Nummer durch Hinzufügen oder Entfernen von Geräten aus dem System beeinflussen. Darüber hinaus verwenden einige-Software und-Diensten Kernelmodus-Treiber. Softwarehersteller können diese Metrik beeinflussen, durch Suchen nach anderen Methoden, um ein Feature zu implementieren, die nicht zugeordnete Arbeitsspeicher Dateien verwendet wird.

Dies ist eine Liste von Binärdateien, die zugeordneten Speichers e/a verwenden. Dies ist alle zugeordneten Speichers Arbeitsspeicher, die mit einer bestimmten Binärdatei verknüpft ist. Sie enthält Code und zugehörigen Daten (freigegebene und nicht freigegebene) mit bestimmten Binärdatei. Große Speicher abgebildeten Dateien können einen negativen Einfluss auf die Leistung haben.

**Detaillierte untergeordnete Metriken**

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Untergeordnete Metrik</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Active</p></td>
<td><p>Dies ist eine Liste der Binärdateien und ihren Beitrag zu Gesamtspeichers verwendet wird. Dieser Speicher wird verwendet.</p></td>
</tr>
<tr class="even">
<td><p>Standby</p></td>
<td><p>Dies ist eine Liste der Binärdateien und ihren Beitrag zu Gesamtspeichers verwendet wird. Dieser Speicher ist erforderlich, auf der standby-Liste, die Speicher ist, die noch im physischen Speicher ist aber als nicht mehr markiert wurde. Dies ist der Arbeitsspeicher, die zuerst durch neue Arbeitsspeicher vom Speichermanager ausgelagert oder verschoben werden bei Bedarf wieder in der Liste der aktiven ersetzt werden.</p></td>
</tr>
</tbody>
</table>

 

**Typische Schlüsselfaktoren Faktoren**

OEMs können diese Metrik durch Auslagerung Hardware- oder Treiber, unteren Arbeitsspeicherbedarf beeinflussen. Darüber hinaus können OEMs die Anzahl der Geräte, auf dem System reduzieren. Verringern Sie die Anzahl der eindeutigen Prozesse, die zu einem Zeitpunkt ausgeführt werden.

**Analyse und Schritte zur Wiederherstellung**

Große Zuweisungen Arbeitsspeicher zugeordnet sind, an einem Speicherort auf dem Datenträger können nicht in einer der von den Arbeitsspeicher vom Manager gewährten angeboten Optimierungen teilnehmen. Der Hersteller hat die meisten Einfluss auf diese Metrik die Art und Weise wie der Treiber entwickelt. Suchen Sie nach großer Arbeitsspeicher Zuweisungen in den Ergebnissen in der Windows-Assessment-Konsole angezeigt. Darüber hinaus können die Treiber Herstellern erhalten WPA Spuren (gespeichert im gleichen Verzeichnis befindet wie die Ergebnisse Assessment) dieser Beurteilung Bereiche der extra fette Arbeitsspeicher Zuweisungen suchen, die für die Untersuchungen in Reduzieren der Speicherverwendung geeignet sind.

## <a name="a-href-idbkmk-memoryissuesaissues"></a><a href="" id="bkmk-memoryissues"></a>Probleme


Es sind keine bestimmte Probleme, die für die Bewertung Speicherbedarf generiert. Dieses Assessment bietet nur Metriken Analyse der Arbeitsspeicherwerte helfen, da die Ergebnisse, die in einem Systemkonfiguration aufgeführt sind also von einer anderen unterscheiden können. Die optimale Verwendung für die Bewertung wird zum Identifizieren der Treiber, Prozesse oder Anwendungen, die viel Arbeitsspeicher verwenden. Hiermit können Sie auch Assessment zum Vergleichen von eigenständigen höherer Speicherbedarf von zwei oder mehr Computer ist.

**Hinweis**  
Diese Bewertung verwendet Symbole dafür sorgen, dass ihre Ergebnisse als Treiber Zuweisungen anstelle von Kernel-Zuweisungen Treiber Speicher anzeigen. Ohne die Verwendung von Symbolen kann die Analyse Assessment falsch Memory Allocation Quelle identifizieren. Weitere Informationen zu fehlenden Symbole und Bewertung Genauigkeit finden Sie unter [Depth Analysis Probleme](common-in-depth-analysis-issues.md).

 

### <a name="the-assessment-reports-an-exit-code-of-0x80050006"></a>Die Bewertung von Berichten Exit-Code 0x80050006

Dieser Fehler tritt auf, wenn Wartungsaufgaben auf dem PC erfasst wurden, aber nicht vor der Bewertung ausführen abgeschlossen. Dies verhindert, dass die Bewertung von ausgeführt, wie Wartungsaufgaben häufig Assessment Metriken auswirken.

Um dieses Problem zu beheben, führen Sie eine der folgenden Aktionen aus:

1.  Stellen Sie sicher, dass der Computer mit dem Netzwerk verbunden ist und auf Strom ausgeführt wird. Manuelles Initiieren Sie ausstehende Wartungsaufgaben mit dem folgenden Befehl aus einer Eingabeaufforderung mit erhöhten Rechten aus:

    `rundll32.exe advapi32.dll,ProcessIdleTasks`

2.  Deaktivieren Sie reguläre und im Leerlauf Wartungsaufgaben und beenden Sie alle Wartungsaufgaben vor der Bewertung wird ausgeführt.

### <a name="recommendations-for-driver-and-software-vendors"></a>Empfehlungen für Treiber und Softwarehersteller

-   Verwenden Sie den minimalen Arbeitsspeicher erforderlich, um diese Aufgabe zu erledigen.

-   Laden Sie nur den Speicher, die, den Sie benötigen, wenn Sie wird benötigt, und es frei, sobald Sie fertig sind, den zu.

-   Kennen Sie die verschiedenen Verfahren können Sie laden Arbeitsspeicher und verwenden Sie die entsprechenden APIs.

-   Ermitteln Sie, ob der Treibercode oder Daten benötigt, bleiben im physikalischen RAMS oder, wenn es zum an-und Abmelden ausgelagert werden zugelassen werden kann.

-   Verstehen der Auslagerungsdatei, deren Funktionsweise und es Einfluss auf hat auf Ihre Szenarien.

-   Erstellen Sie keine monolithic-Treiber, der mehrere Geräte services. Halten Sie den Treiber klein und haben nur die Aspekte des Geräts, das sie dient beheben.

### <a name="recommendations-for-oems"></a>Empfehlungen für OEMs

-   Finden Sie unter wirken sich die Treiber und Software, die Sie vor der Bereitstellung auf der Basis einer Neuinstallation Bild installieren.

-   Finden Sie in Ihrer Treiber und Softwarehersteller, für den aktuellen Versionen ihrer Software, um festzustellen, ob die Auswirkung auf Speicher reduziert werden kann.

-   Erwägen Sie einen anderen Treiber oder Softwarehersteller, die Sie mit, wie die folgende Funktionalität mit niedrigeren Auswirkung auf Systemspeichers angeben kann.

## <a name="related-topics"></a>Verwandte Themen


[Speicherbedarf](memory-footprint.md)

[Windows-Assessment-Toolkit](index.md)

[Bewertung](assessments.md)

[Schrittweise Anleitung für Windows-Bewertungen-Konsole](windows-assessment-console-step-by-step-guide.md)

[MSDN: Windows-Speicherverwaltung](http://go.microsoft.com/fwlink/?LinkId=271597)

 

 







