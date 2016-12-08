---
title: CPU-Analyse
description: CPU-Analyse
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 2926f382-2191-4bdd-8cd1-e01493e6daa1
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: ed79cc570943662941896ba9263b8a375f3c02e1
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="cpu-analysis"></a>CPU-Analyse


Dieses Handbuch enthält ausführliche Techniken, die Sie verwenden können Central Processing Units CPU-Problemen, Auswirkungen Assessment Metriken untersuchen.

Häufig vorkommender Probleme für die Untersuchung Identifizierung der einzelnen metrische oder das Problem Abschnitte in den Handbüchern Assessment-spezifischen Analyse. Dieses Handbuch enthält Techniken und Tools, die Sie verwenden können, um diese Probleme zu untersuchen.

Verwenden Sie die Verfahren in diesem Handbuch Windows Performance Analyzer (WPA) aus Windows Performance Toolkit (WPT). Die WPT ist Teil der Windows Assessment and Deployment Kit (Windows ADK), und es aus dem [Windows-Insider Programm](https://insider.windows.com/)heruntergeladen werden kann. Weitere Informationen finden Sie unter [Technische Referenz zu Windows Performance Toolkit](windows-performance-toolkit-technical-reference.md).

Dieses Handbuch ist in die folgenden drei Abschnitte unterteilt:

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>[Hintergrund](#cpu-guide-background)</p></td>
<td><p>In diesem Abschnitt wird beschrieben, wie CPU-Ressourcen in Windows 10 verwaltet werden.</p></td>
</tr>
<tr class="even">
<td><p>[Windows ADK Tools](#cpu-guide-adktools)</p></td>
<td><p>In diesem Abschnitt wird erläutert, wie anzeigen und Interpretieren von CPU-Informationen in der Windows ADK Toolkit.</p></td>
</tr>
<tr class="odd">
<td><p>[Techniken (engl.)](#cpu-guide-techniques)</p></td>
<td><p>Dieser Abschnitt enthält eine Auflistung von Techniken, die Sie verwenden können, zu untersuchen und Beheben von Problemen, die im Zusammenhang mit der CPU-Leistung.</p></td>
</tr>
</tbody>
</table>

 

## <a name="a-href-idcpu-guide-backgroundabackground"></a><a href="" id="cpu-guide-background"></a>Hintergrund


Dieser Abschnitt enthält eine einfache Beschreibung und eine grundlegende Besprechung auf die CPU-Leistung. Für eine umfassendere Studie zu diesem Thema empfehlen wir das Adressbuch Windows-gehenden fünfte Edition.

Modernen Computer können mehrere CPUs enthalten, die in separaten Sockets installiert sind. Jede CPU kann mehrere physische Prozessorkerne, jedes Lage ein oder zwei separate Anweisung Datenströme gleichzeitig verarbeiten hosten. Diese einzelnen Anweisung Stream-Prozessoren werden vom Windows-Betriebssystem als logische Prozessoren verwaltet.

In diesem Handbuch Prozessor und CPU-verweisen auf einen logischen Prozessor – d. h., ein Hardwaregerät, mit denen das Betriebssystem können Programm Anweisungen auszuführen.

Windows-10 verwaltet aktiv Prozessorhardware auf zwei Hauptarten: *Power Management*Gleichgewicht des Stromverbrauchs und Leistung; und *Nutzung*, um die Verarbeitung von Anforderungen von Programmen und Treiber auszugleichen.

### <a name="processor-power-management"></a>Verwaltung der Prozessor Stromversorgung

Prozessoren sind nicht immer in einen Betriebsstatus vorhanden. Wenn keine Anweisungen zur Ausführung bereit sind, versetzt Windows ein Prozessors in ein Ziel im Leerlauf Zustand (oder C-Status), als vom Windows Power-Manager bestimmt. Basierend auf Verwendungsmuster CPU, des Prozessors Ziel die C-Status über einen Zeitraum angepasst wird.

Im Leerlauf Zustände sind nummerierte Zustände aus C0 (aktiven, nicht im Leerlauf) durch stetig Zeiteinheiten Power Zustände. Zu diesen Staaten gehören C1 (angehalten jedoch weiterhin die Uhr aktiviert ist), C2 (angehalten und die Uhr ist deaktiviert) und So weiter. Die Implementierung der Status im Leerlauf ist Prozessor abhängig. Eine größere Anzahl von Status auf alle Prozessoren widerspiegelt unteren des Stromverbrauchs jedoch auch eine mehr Zeit vor der Prozessor zur Verarbeitung der Anweisung zurückgeben kann. Zeit im Leerlauf Staaten erheblich ist wirkt sich auf Energie Verwendung und Batterie Lebenszyklus.

Einige Prozessoren Leistung (P-) ausgeführt werden können und die Throttle (T-), auch wenn sie aktiv verarbeitungsanweisungen sind. P-Zustände definieren die Taktfrequenzen und Spannung Ebenen der Prozessor unterstützt. T-Staaten nicht direkt ändern die Taktfrequenz, aber Sie können die effektive Taktfrequenz durch Auslassen der der Verarbeitungsaktivität auf einige Bruchteil Zeiteinheiten senken. Die aktuellen P-T-Zustände und bestimmen zusammen, die effektive funktionieren Frequenz des Prozessors. Geringere Leistung und niedrigeren Stromverbrauchs entsprechen tieferen Frequenzen.

Der Windows Power Manager bestimmt einen entsprechenden P - und T-Status für jeden Prozessor, basierend auf CPU Verwendungsmuster und Power Systemrichtlinie. Zeitspanne für die in High Performance-Zustände sowie Zustände geringer Leistung erheblich wirkt sich auf Energie Verwendung und Batterie Lebenszyklus.

### <a name="processor-usage-management"></a>Prozessor: Einsatz Management

Windows verwendet die drei wichtigsten Abstraktionen Prozessorverwendung zu verwalten.

-   Prozesse

-   Threads

-   Zurückgestellt Prozeduraufrufe (DPCs) und Interrupt Service Routinen (ISRs)

### <a name="processes-and-threads"></a>Prozesse und Threads

Alle im Benutzermodus Programme in Windows im Kontext eines *Prozesses*ausgeführt. Ein Prozess umfasst die folgenden Attribute und Komponenten:

-   Einen virtuellen Adressbereich

-   Prioritätsklasse

-   Programmodule geladen

-   Informationen-Umgebung und-Konfiguration

-   Mindestens ein thread

Obwohl Prozesse der Anwendung Module, Kontext und Umgebung enthalten, werden diese nicht direkt geplant, führen Sie auf einem Prozessor. Stattdessen werden Threads, die von einem Prozess gehören planmäßig mit einem Prozessor ausgeführt.

Ein Thread verwaltet Kontextinformationen Ausführung. Nahezu alle Berechnung wird als Teil eines Threads verwaltet. Threadaktivität betrifft grundlegend Messungen und Systemleistung.

Da die Anzahl der Prozessoren, die in einem System eingeschränkt ist, können nicht alle Threads gleichzeitig ausgeführt werden. Windows implementiert Prozessor Time-sharing, der einen Thread für einen bestimmten Zeitraum an, bevor Sie zu einem anderen Thread der Prozessor wechselt ausgeführt wird. Der Vorgang der Wechsel zwischen Threads ein *Kontextwechsel* aufgerufen, und es erfolgt über eine Windows-Komponente der *Verteiler*aufgerufen. Der Verteiler macht Threadplanung Entscheidungen basierend auf der *Priorität*, *idealen Prozessor und die Affinität*, *Quantum*und *Zustand*.

### <a name="priority"></a>Priorität

Priorität ist ein entscheidender Faktor wie der Verteiler welcher Thread auszuführenden auswählt. Thread Priority ist eine ganze Zahl zwischen 0 und 31. Wenn ein Thread ausführbar ist und eine höhere Priorität als einer derzeit ausgeführten Thread, der niedrigerer Priorität Thread sofort getrennt ist, und der Thread höherer Priorität ist Kontextwechsel in.

Wenn ein Thread ausgeführt wird oder bereit zur Ausführung ist, können keine niedrigerer Priorität Threads ausführen, es sei denn, es gibt genug Prozessoren für beide Threads gleichzeitig ausgeführt werden oder es sei denn, der höhere Priorität Thread zur Ausführung in nur einer Teilmenge der verfügbaren Prozessoren beschränkt ist. Threads verfügen über eine Basis Priorität, die vorübergehend zu bestimmten Zeiten auf höhere Prioritäten erweitert werden kann: Angenommen, wenn der Prozess Vordergrundfenster gehört, oder wenn ein e/a abgeschlossen ist.

### <a name="ideal-processor-and-affinity"></a>Ideale Prozessor und Affinität

Ein Thread *idealen Prozessor und Affinität* bestimmen die Prozessoren auf dem ein bestimmten Thread geplant ist. Jeder Thread verfügt über eine ideale Prozessor, der von der Anwendung oder automatisch durch Windows festgelegt ist. Windows verwendet eine Roundrobin-Methode, sodass eine ungefähr gleich große Anzahl von Threads in jedem Prozess zu jedem Prozessor zugewiesen sind. Wenn möglich, plant Windows einen Thread zur Ausführung in seiner idealen Prozessor; der Thread kann jedoch gelegentlich auf andere Prozessoren ausgeführt.

Ein Thread Prozessoraffinität beschränkt die Prozessoren, auf denen ein Thread ausgeführt wird. Hierbei handelt es sich um eine stärkere Beschränkung als die Thread idealen Prozessor-Attribut. Das Programm festgelegt Affinität mithilfe von **SetThreadAffinityMask**. Affinität kann verhindern, dass Threads jemals Ausführung auf bestimmten Prozessoren.

### <a name="quantum"></a>Quantum

Kontextwechsel werden teure Vorgänge. Windows ermöglicht es Ihnen, jeden Thread für eine bestimmte Zeitspanne auszuführen, die ein *Quantum* aufgerufen wird, bevor es zu einem anderen Thread wechselt. Quantumdauer soll Reaktionsfähigkeit des Systems zu erhalten. Es wird Durchsatz durch Minimieren den Mehraufwand für Kontextwechsel maximiert. Quantum Dauer variiert zwischen Clients und Servern. Quantum Dauer werden normalerweise auf einem Server länger Durchsatz auf offensichtliche Reaktionsfähigkeit Kosten zu optimieren. Auf Clientcomputern Windows weist kürzeren Quantums insgesamt, aber ein länger Quantum an den aktuellen Vordergrundfenster zugeordneten Thread enthält.

### <a name="state"></a>Bundesland

Jeder Thread ist in einem bestimmten Ausführungszustand zu einem bestimmten Zeitpunkt vorhanden. Windows verwendet drei Zustände, die mit der Leistung von Bedeutung sind. Dies sind: *ausgeführt*, *bereit*und *wartet*.

Threads, die derzeit ausgeführt werden, sind im Zustand *ausgeführt* . Threads, die ausgeführt, können aber derzeit nicht ausgeführt werden, im Zustand *bereit* . Threads, die nicht ausgeführt werden können, da sie für ein bestimmtes Ereignis warten sind im Zustand *wartet* .

Ein Status zum Übergang wird in Abbildung 1 Thread-Statusübergänge gezeigt:

![Abbildung 1 Thread Statusübergang](images/dep-win8-cpu-techniques-figure-1-thread-state-transition.jpg)

**Abbildung 1 Thread-Statusübergänge**

Abbildung 1 Thread Statusübergänge wird wie folgt erläutert:

1.  Ein Thread im Zustand "aktiv" initiiert einen Übergang zu Waiting durch Aufrufen der Wait-Funktion wie **WaitForSingleObject** State oder **Energiesparmodus (&gt; 0)**.

2.  Eine Operation Thread oder Kernel bereitet einen Thread in der wartenden Zustand (beispielsweise **SetEvent** oder den Timer Ablauf-). Wenn ein Prozessor im Leerlauf ist oder der gelesene Thread eine höhere Priorität als einer derzeit ausgeführten Thread verfügt, kann direkt auf den Status wird ausgeführt gelesene Threads wechseln. Andernfalls wird es in der aktuelle Status versetzt.

3.  Ein Thread im Zustand bereit ist geplant, für die Verarbeitung durch den Verteiler, wenn ein laufenden Thread wartet, ergibt **(Sleep(0))**, oder das Ende des seinen Anteil erreicht.

4.  Ein Thread im Zustand "aktiv" ist gewechselt und in der aktuelle Status vom Verteiler eingefügt, wenn es mit einer höheren Priorität Thread ergibt belegt ist **(Sleep(0))**; oder seinen Anteil wann endet.

Ein Thread, der in der Anzeige für wartende vorhanden ist Zustand nicht unbedingt ein Leistungsproblem an. Die meisten Threads hohen Zeitaufwand in der wartenden Zustand, wodurch Prozessoren eingeben im Leerlauf Staaten und Energie sparen. Der Status wird ein wichtiger Faktor bei der Leistung nur, wenn ein Benutzer auf ein Thread für die Durchführung ein Vorgangs wartet.

### <a name="dpcs-and-isrs"></a>DPCs und ISRs

Zusätzlich zur von Verarbeitungsthreads reagieren Prozessoren von Hardwaregeräten wie Netzwerkkarten oder Zeitgeber auf Benachrichtigungen. Wenn ein Hardwaregerät Prozessor Aufmerksamkeit erfordert, wird ein *Interrupt*generiert. Windows reagiert auf ein Hardwareinterrupt durch Anhalten eines derzeit ausgeführten Threads und Ausführen der ISR, die den Interrupt zugeordnet ist.

Während der Zeit, dass er eine ISR ausgeführt wird kann ein Prozessor verhindert werden, andere Aktivitäten, einschließlich anderer Interrupts verarbeiten. Aus diesem Grund müssen schnell ISRs abgeschlossen ist, oder kann die Systemleistung beeinträchtigen. Um Ausführungszeit zu verringern, Planen ISRs häufig DPCs ausführbaren muss als Reaktion auf einen Interrupt ausführen. Für jeden logischen Prozessor verwaltet Windows eine Warteschlange der geplanten DPCs. DPCs haben Vorrang vor Threads auf jeder Prioritätsebene. Vor der Rückgabe von eines Prozessors auf Auftragsverarbeitungsthreads führt die DPCs aller in der Warteschlange aus.

Während der Zeit, dass ein Prozessor DPCs und ISRs ausgeführt wird können keine Threads auf dieser Prozessor ausführen. Diese Eigenschaft kann zu Problemen für Threads führen, die Arbeit an einen bestimmten Durchsatz oder mit dem genauen Zeitpunkt, wie ein Thread, der Audio- oder Videodatei wiedergegeben wird ausgeführt werden müssen. Wenn die CPU-Zeit, die zum Ausführen von DPCs und ISRs verwendet wird verhindert, dass diese Threads ausreichend Verarbeitungszeit empfangen, der Thread nicht zu den erforderlichen Durchsatz erzielen oder seine Arbeitsaufgaben rechtzeitig ausführen.

## <a name="a-href-idcpu-guide-adktoolsawindows-adk-tools"></a><a href="" id="cpu-guide-adktools"></a>Windows ADK Tools


Windows ADK schreibt Hardwareinformationen und Bewertung auf *Bewertung Ergebnisdateien*. WPA enthält ausführliche Informationen zur CPU-Auslastung in verschiedenen Diagrammen. In diesem Abschnitt wird das Verwenden des Windows ADK und WPA zum Sammeln, anzeigen und Analysieren von CPU-Leistungsdaten erläutert.

### <a name="a-href-id-------------windows-adk-assessment-results-filesa-windows-adk-assessment-results-files"></a><a href="" id="-------------windows-adk-assessment-results-files"></a>Windows ADK Assessment Ergebnisdateien

Da Windows SMP Systeme nur unterstützt, beziehen sich alle Informationen in diesem Abschnitt auf allen installierten CPUs und Kernen.

CPU-Hardware Detailinformationen steht in der `EcoSysInfo` Abschnitt ein Ergebnis Assessment unter Dateien die `<Processor><Instance id=”0”>` Knoten.

Beispiel:

``` syntax
<Processor>
  <Instance id="0">
    <ProcessorName>The name of the first CPU</ProcessorName>
    <TSCFrequency>The maximum frequency of the first CPU</TSCFrequency>
    <NumProcs>The total number of processors</NumProcs>
    <NumCores>The total number of cores</NumCores>
    <NumCPUs>The total number of logical processors</NumCPUs>
    ...and so on...
```

### <a name="wpa-graphs"></a>WPA-Diagrammen

Laden Sie eine Verfolgung in WPA, finden Sie unter den **Trace/System Konfiguration/Allgemein** und **Konfiguration Trace/System/PnP** Abschnitten der Benutzeroberfläche WPA Prozessor Hardwareinformationen.

**Hinweis**  
Alle Verfahren in diesem Handbuch auftreten in WPA.

 

### <a name="cpu-idle-states-graph"></a>CPU im Leerlauf Staaten Diagramm

Wenn in einer Ablaufverfolgung für Leerlauf Informationen gesammelt werden, wird das Diagramm **Power/CPU im Leerlauf Zustände** in der WPA-Benutzeroberfläche angezeigt. Dieses Diagramm enthält immer Daten auf den *Ziel* -Leerlauf für jeden Prozessor. Das Diagramm enthält außerdem Informationen zu jeder Prozessor *Istwert* Leerlauf Wenn dieser Zustand vom Prozessor unterstützt wird.

Jede Zeile in der folgenden Tabelle wird eine Änderung Leerlauf für das Ziel oder die tatsächlichen Zustand eines Prozessors beschrieben. Für jede Zeile im Diagramm stehen die folgenden Spalten:

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Spalte</th>
<th>Details</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>CPU</p></td>
<td><p>Der Prozessor, der von der Änderung betroffen ist.</p></td>
</tr>
<tr class="even">
<td><p>Eintrittszeit</p></td>
<td><p>Die Zeit, die der Prozessor den Leerlauf eingegeben.</p></td>
</tr>
<tr class="odd">
<td><p>Exit-Zeit</p></td>
<td><p>Die Zeit, die der Prozessor den Leerlauf beendet.</p></td>
</tr>
<tr class="even">
<td><p>Max:Duration(ms)</p></td>
<td><p>Die Zeit im Leerlauf (Standardwert Aggregation: maximal) ist.</p></td>
</tr>
<tr class="odd">
<td><p>Min:Duration(ms)</p></td>
<td><p>Die Zeit im Leerlauf (Standardwert Aggregation: Minimum) ist.</p></td>
</tr>
<tr class="even">
<td><p>Nächsten Status</p></td>
<td><p>Der Zustand, dem Prozessor nach dem aktuellen Zustand gewechselt.</p></td>
</tr>
<tr class="odd">
<td><p>Vorherige Zustand</p></td>
<td><p>Der Zustand, aus dem Prozessor vor den aktuellen Zustand gewechselt.</p></td>
</tr>
<tr class="even">
<td><p>Bundesland</p></td>
<td><p>Den aktuellen Leerlauf.</p></td>
</tr>
<tr class="odd">
<td><p>Status (Numeric)</p></td>
<td><p>Den aktuellen Leerlauf als Zahl an (beispielsweise 0 für C0).</p></td>
</tr>
<tr class="even">
<td><p>SUM:Duration(ms)</p></td>
<td><p>Die Zeit im Leerlauf (Standardwert Aggregation: Summe) ist.</p></td>
</tr>
<tr class="odd">
<td><p>Tabelle</p></td>
<td><p>Nicht verwendete</p></td>
</tr>
<tr class="even">
<td><p>Typ</p></td>
<td><p><strong>Ziel</strong> (für die Power Manager ausgewählte(n) Zustand für den Prozessor) oder <strong>Istwert</strong> (für den tatsächlichen Leerlauf des Prozessors).</p></td>
</tr>
</tbody>
</table>

 

Das Standardprofil für WPA bietet zwei Vorgaben für dieses Diagramm: **Status nach Typ CPU** und **Statusdiagramm nach Typ CPU**.

### <a name="state-by-type-cpu"></a>Status nach Typ CPU

Die Zielwerte und Istwerte sowie Zustände jede CPU werden zusammen mit der Anzahl der Zustand auf **der y-Achse im Diagramm **Zustand nach Typ CPU** ** grafisch dargestellt. Abbildung 2 CPU-Leerlauf Staaten Status nach Typ zeigt CPU den aktuelle Zustand der CPU, wie sie zwischen aktiv und Ziel im Leerlauf Zustand wechselt.

![Abbildung 2 cpu im Leerlauf Zustände durch Statustyp cpu](images/dep-win8-cpu-techniques-figure-2-cpu-idle-states-state-by-type-cpu.png)

**Abbildung 2 CPU Leerlauf Staaten nach Typ CPU**

### <a name="state-diagram-by-type-cpu"></a>State Diagramm nach Typ CPU

In diesem Diagramm werden die Zielwerte und Istwerte sowie Status der einzelnen CPU-Auslastung in Zeitachse-Format angezeigt. Jeder Zustand hat eine separate Zeile in die Zeitachse. Abbildung 3 CPU im Leerlauf Staaten Zustandsdiagramm nach Typ, zeigt CPU die gleichen Daten wie in Abbildung 2 CPU-Idle Staaten Status nach Typ CPU, in einer Zeitachsenansicht.

![Abbildung 3 cpu im Leerlauf Staaten Statusdiagramm durch geben cpu](images/dep-win8-cpu-techniques-figure-3-cpu-idle-states-state-diagram-by-type-cpu.png)

**Abbildung 3 CPU Leerlauf Staaten Diagramm nach Typ CPU**

### <a name="cpu-frequency-graph"></a>CPU-Häufigkeit Diagramm

Wenn die CPU-Häufigkeit auf einem System Datenerfassung, die mehrere P - oder T-Zustände, unterstützt wird im Diagramm **CPU Häufigkeit** in der Benutzeroberfläche WPA verfügbar sein. Jede Zeile in der folgenden Tabelle darstellt Zeit auf einer bestimmten Häufigkeitsebene für einen Prozessor. Die **Häufigkeit (MHz)** -Spalte enthält eine begrenzte Anzahl von Frequenzen, die entsprechen den P-Status und T-Zustände, die vom Prozessor unterstützt werden. Für jede Zeile im Diagramm stehen die folgenden Spalten:

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Spalte</th>
<th>Details</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>% Dauer</p></td>
<td><p>Dauer wird als Prozentsatz der gesamten CPU-Zeit im aktuell angezeigten Zeitraum ausgedrückt.</p></td>
</tr>
<tr class="even">
<td><p>Anzahl</p></td>
<td><p>Die Anzahl der Häufigkeit Änderungen (immer 1 für einzelne Zeilen).</p></td>
</tr>
<tr class="odd">
<td><p>CPU</p></td>
<td><p>Die CPU, die durch die Änderung der Häufigkeit betroffen ist.</p></td>
</tr>
<tr class="even">
<td><p>Eintrittszeit</p></td>
<td><p>Die Zeit, die CPU den P-Zustand eingegeben.</p></td>
</tr>
<tr class="odd">
<td><p>Exit-Zeit</p></td>
<td><p>Der Zeitpunkt, dass die CPU den P-Status beendet wurde.</p></td>
</tr>
<tr class="even">
<td><p>Häufigkeit (MHz)</p></td>
<td><p>Die Häufigkeit der CPU während der Zeit, die sie in der P-Zustand befindet.</p></td>
</tr>
<tr class="odd">
<td><p>Max:Duration(ms)</p></td>
<td><p>Die Zeit im P-Zustand (Standard Aggregation: maximal) ist.</p></td>
</tr>
<tr class="even">
<td><p>Min:Duration(ms)</p></td>
<td><p>Die Zeit, die den P-Status (Standard Aggregation: Minimum) aufgewendet wird.</p></td>
</tr>
<tr class="odd">
<td><p>SUM:Duration(ms)</p></td>
<td><p>Die Zeit in der P-Zustand (Standard Aggregation: Summe) ist.</p></td>
</tr>
<tr class="even">
<td><p>Tabelle</p></td>
<td><p>Nicht verwendete</p></td>
</tr>
<tr class="odd">
<td><p>Typ</p></td>
<td><p>Weitere Informationen zu den P-Zustand.</p></td>
</tr>
</tbody>
</table>

 

Das Standardprofil definiert die **Häufigkeit von CPU** Vorgabe für dieses Diagramm. Abbildung 4 CPU-Häufigkeit von CPU zeigt eine CPU Übergang zwischen drei P Zuständen:

![Abbildung 4 CPU-Häufigkeit von cpu](images/dep-win8-cpu-techniques-figure-4-cpu-frequency-by-cpu.png)

**Abbildung 4 CPU Häufigkeit von CPU**

### <a name="cpu-usage-sampled-graph"></a>CPU-Auslastung (aufgenommene) Diagramm

Die Daten, die in der **CPU-Auslastung (abgetastete)** Diagramm angezeigt werden stellt Beispiele der CPU-Aktivität, die in einem regulären Samplingintervall ausgeführt werden. In den meisten Spuren ist dies eine Millisekunde (1 ms). Jede Zeile in der Tabelle stellt ein einzelnes Beispiel.

Die Gewichtung der Stichprobe stellt die Bedeutung dieses Beispiels, relativ zu anderen Beispiele. Die Gewichtung ist der Zeitstempel des im aktuellen Beispiel abzüglich der Zeitstempel des vorherigen Beispiels gleich. Die Gewichtung ist aufgrund Fluktuationen in Systemstatus und Aktivitäten nicht immer das Sampling-Intervall genau gleich.

Abbildung 5 CPU-Sampling stellt dar, wie Daten gesammelt werden:

![Abbildung 5 CPU-sampling](images/dep-win8-cpu-techniques-figure-5-cpu-sampling.jpg)

**Abbildung 5 CPU Sampling**

Eine beliebige CPU-Aktivität, die zwischen Beispiele tritt auf, wird durch diese Samplingmethode nicht aufgezeichnet. Aktivitäten für sehr kurze Zeit wie DPCs und ISRs werden daher nicht auch im **CPU-Sampling** Diagramm dargestellt.

Für jede Zeile im Diagramm stehen die folgenden Spalten:

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Spalte</th>
<th>Details</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>% Gewicht</p></td>
<td><p>Gewicht wird als Prozentsatz der gesamten CPU-Zeit ausgedrückt, die über den sichtbaren Zeitbereich aufgewendet wird.</p></td>
</tr>
<tr class="even">
<td><p>Adresse </p></td>
<td><p>Die Adresse des Arbeitsspeichers der Funktion, die am unteren Rand des Stapels ist.</p></td>
</tr>
<tr class="odd">
<td><p>Alle Count</p></td>
<td><p>Die Anzahl der Beispiele, die durch eine Zeile dargestellt. Diese Zahl enthält Beispiele, die ausgeführt werden, wenn ein Prozessor im Leerlauf ist. Bei einzelnen Zeilen ist diese Spalte immer 1.</p></td>
</tr>
<tr class="even">
<td><p>Anzahl</p></td>
<td><p>Die Anzahl der Beispiele, dargestellt durch eine Zeile, ausgenommen Beispiele, die ausgeführt werden, wenn ein Prozessor im Leerlauf ist. Für einzelne Zeilen ist diese Spalte immer 1 (oder 0, Hinblick auf Fälle ausgeführt, wenn die CPU in den Energiesparmodus war).</p></td>
</tr>
<tr class="odd">
<td><p>CPU</p></td>
<td><p>Die 0-basierter Indexwert der CPU auf dem in diesem Beispiel durchgeführt wurde.</p></td>
</tr>
<tr class="even">
<td><p>Anzeigename</p></td>
<td><p>Der Anzeigename des aktiven Prozesses.</p></td>
</tr>
<tr class="odd">
<td><p>DPC/ISR</p></td>
<td><p>Gibt an, ob im Beispiel reguläre CPU-Auslastung, eine DPC/ISR oder Energiesparmodus gemessen.</p></td>
</tr>
<tr class="even">
<td><p>Funktion</p></td>
<td><p>Die Funktion am unteren Rand des Stapels.</p></td>
</tr>
<tr class="odd">
<td><p>Modul</p></td>
<td><p>Das Modul, das die Funktion am unteren Rand des Stapels enthält.</p></td>
</tr>
<tr class="even">
<td><p>Priorität</p></td>
<td><p>Die Priorität des ausgeführten Threads.</p></td>
</tr>
<tr class="odd">
<td><p>Prozessfarben</p></td>
<td><p>Der Name der Bild des Prozesses, der den Ausführung von Code besitzt.</p></td>
</tr>
<tr class="even">
<td><p>Name des Prozesses</p></td>
<td><p>Der vollständige Name (einschließlich Prozess-ID) des Prozesses, die den Ausführung von Code besitzt.</p></td>
</tr>
<tr class="odd">
<td><p>Stapel</p></td>
<td><p>Der Stapel des ausgeführten Threads.</p></td>
</tr>
<tr class="even">
<td><p>Thread-ID</p></td>
<td><p>Die ID des Threads ausgeführt wird.</p></td>
</tr>
<tr class="odd">
<td><p>Thread-Start-Funktion</p></td>
<td><p>Die Funktion, mit der ausgeführte Thread gestartet.</p></td>
</tr>
<tr class="even">
<td><p>Thread-Start-Modul</p></td>
<td><p>Das Modul, das die Thread-Start-Funktion enthält.</p></td>
</tr>
<tr class="odd">
<td><p>Zeitstempel</p></td>
<td><p>Die Zeit, die im Beispiel stammt.</p></td>
</tr>
<tr class="even">
<td><p>Gewicht</p></td>
<td><p>Die Zeit (in Millisekunden), die im Beispiel (d. h., die Zeit seit der letzten) dargestellt wird.</p></td>
</tr>
</tbody>
</table>

 

Das Standardprofil bietet die folgenden Vorgaben für dieses Diagramm:

-   Nutzung von CPU

-   Auslastung nach Priorität

-   Nutzung von Prozess

-   Nutzung von Prozessen und Threads

### <a name="utilization-by-cpu"></a>Nutzung von CPU

Die **CPU-Auslastung Nutzung von CPU** Darstellung zeigt, wie Arbeit zwischen Prozessoren verteilt ist. Abbildung 6 CPU-Auslastung Nutzung von CPU zeigt diese Verteilung für zwei CPUs:

![Abbildung 6 CPU-Auslastung Nutzung von cpu](images/dep-win8-cpu-techniques-figure-6-cpu-usage-utilization-by-cpu.png)

**Abbildung 6 CPU-Auslastung der Nutzung von CPU**

### <a name="utilization-by-priority"></a>Auslastung nach Priorität

**CPU-Auslastung** gruppiert nach Threadpriorität zeigt, wie hoher Priorität Auswirkungen niedrigerer Priorität Threads threads. Abbildung 7 CPU-Auslastung (abgetastete) Auslastung nach Priorität wird dieses Diagramm angezeigt:

![Abbildung 7 CPU-Auslastung bei Auslastung nach Priorität Grafik.](images/dep-win8-cpu-techniques-figure-7-cpu-usage-sampled-utilization-by-priority.png)

**Abbildung 7 CPU-Auslastung (gemessen) Auslastung nach Priorität**

### <a name="utilization-by-process"></a>Auslastung vom Prozess

**CPU-Auslastung** , die vom Prozess gruppiert sind zeigt die relative durch verarbeitet. Abbildung 8 CPU-Auslastung (abgetastete) vom Prozess wird dies voreingestellten. In diesem Beispiel Diagramm wird ein Prozess zum Verarbeiten von mehr CPU-Zeit als die andere Prozesse werden angezeigt.

![Abbildung 8 CPU-Auslastung bei Auslastung vom Prozess Grafik.](images/dep-win8-cpu-techniques-figure-8-cpu-usage-sampled-utilization-by-process.png)

**Abbildung 8 CPU-Auslastung (gemessen) Auslastung von Prozess**

### <a name="utilization-by-process-and-thread"></a>Nutzung von Prozessen und Threads

**CPU-Auslastung** , die vom Prozess gruppiert und dann nach Threads gruppiert ist zeigt die relative durch Prozesse und Threads in jedem Prozess. Abbildung 9 CPU-Auslastung (abgetastete) Auslastung nach Prozess und Thread zeigt diese vordefinierten. In diesem Diagramm werden die Threads in einem einzigen Schritt ausgewählt.

![Abbildung 9 CPU-Auslastung bei Auslastung vom Prozess Grafik.](images/dep-win8-cpu-techniques-figure-9-cpu-usage-sampled-utilization-by-process-and-thread.png)

**Abbildung 9 CPU-Auslastung (gemessen) Nutzung von Prozessen und Threads**

### <a name="cpu-usage-precise-graph"></a>CPU-Auslastung (exakt) Diagramm

Das **CPU-Auslastung (Precise)** Diagramm zeichnet Informationen, die Kontextwechsel Ereignisse zugeordnet ist. Jede Zeile stellt einen Satz von Daten, die einen einzelnen Kontextwechsel zugeordnet ist; d. h., wenn ein Thread gestartet. Daten werden für die folgenden Ereignissequenz erfasst:

1.  Der neue Thread abgeschaltet wird.

2.  Der neue Thread ist bereit zur Ausführung der readying Thread vorgenommen.

3.  Der neue Thread ist in gewechselt somit eine alte Thread Auslagerung wird.

4.  Der neue Thread wird erneut abgeschaltet.

In Abbildung 10 CPU-Auslastung genaue Diagramm fließt Zeit von links nach rechts. Die Beschriftungen Diagramm entsprechen den Spaltennamen im Diagramm **CPU-Auslastung (Precise)** . Bezeichnungen für **Zeitstempel** Spalten am oberen Rand des Diagramms angezeigt, und Beschriftungen für die **Dauer Intervall** Spalten im unteren Bereich des Diagramms angezeigt.

![Abbildung 10 CPU-Verwendung exakte Diagramm](images/dep-win8-cpu-techniques-figure-10-cpu-usage-precise-diagram.jpg)

**Abbildung 10 präzise Diagramm mit CPU-Auslastung**

Breaks in die Zeitachse in Abbildung 10 CPU-Auslastung genaue Diagramm unterteilen die Zeitachse in Regionen, die gleichzeitig auf verschiedene CPUs auftreten können. Diese Zeitpläne können überlappen, solange die Reihenfolge der nummerierten Ereignisse nicht geändert wird. Beispielsweise kann Hauptentwurfsoption Threads auf Prozessor 2 zur selben Zeit, der ein neuer Thread abgeschaltet wird ausgeführt und dann wieder anmelden auf Prozessor-1).

Informationen werden für die folgenden vier Ziele auf der Zeitachse aufgezeichnet:

-   *Neuen Thread*, der die Thread handelt, der in gewechselt wurde. Es ist der Schwerpunkt dieser Zeile im Diagramm.

-   *NewPrev Threads*, die auf früheren Zeitpunkt verweist, die in der neue Thread gewechselt wurde.

-   *Vorbereitung Thread*, sich der Thread, der den neuen Thread handelt zu verarbeitenden vorbereitet haben.

-   *Alte Thread*der Thread, der abgeschaltet wurde, wenn in der neue Thread gewechselt wurde.

Die Daten in der folgenden Tabelle bezieht sich auf jeder Zielthread:

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Spalte</th>
<th>Details</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>% CPU-Verwendung</p></td>
<td><p>Die CPU-Auslastung des neuen Threads, nachdem er geändert wird. Dieser Wert wird als Prozentsatz der gesamten CPU-Zeit im aktuell angezeigten Zeitraum ausgedrückt.</p></td>
</tr>
<tr class="even">
<td><p>Anzahl</p></td>
<td><p>Die Anzahl der Kontextwechsel, die von der Zeile dargestellt werden. Dies ist immer 1 für die einzelnen Zeilen.</p></td>
</tr>
<tr class="odd">
<td><p>Count: Sperrenwartevorgänge</p></td>
<td><p>Die Anzahl der wartet, die von der Zeile dargestellt werden. Wenn ein Thread in den Leerlauf gewechselt wird, ist dies stets 1 für einzelne Zeilen mit Ausnahme von; In diesem Fall wird es auf 0 festgelegt.</p></td>
</tr>
<tr class="even">
<td><p>CPU</p></td>
<td><p>Die CPU auf dem der Kontextwechsel aufgetreten ist.</p></td>
</tr>
<tr class="odd">
<td><p>CPU-Auslastung (ms)</p></td>
<td><p>Die CPU-Auslastung des neuen Threads nach die Option Kontext. Dies ist gleich der NewInSwitchTime jedoch in Millisekunden angezeigt wird.</p></td>
</tr>
<tr class="even">
<td><p>IdealCpu</p></td>
<td><p>Die ideale CPU vom Planer für den neuen Thread ausgewählt.</p></td>
</tr>
<tr class="odd">
<td><p>LastSwitchOutTime (s)</p></td>
<td><p>Die früheren Zeitpunkt, der der neue Thread abgeschaltet wurde.</p></td>
</tr>
<tr class="even">
<td><p>NewInPri</p></td>
<td><p>Die Priorität des neuen Threads, die in gewechselt wird.</p></td>
</tr>
<tr class="odd">
<td><p>NewInSwitchTime(s)</p></td>
<td><p>NextSwitchOutTime(s) minus SwitchInTime(s)</p></td>
</tr>
<tr class="even">
<td><p>NewOutPri</p></td>
<td><p>Die Priorität des neuen Threads beim Skalieren gewechselt.</p></td>
</tr>
<tr class="odd">
<td><p>NewPrevOutPri</p></td>
<td><p>Die Priorität des neuen Threads, wenn es zuvor abgeschaltet wurde.</p></td>
</tr>
<tr class="even">
<td><p>NewPrevState</p></td>
<td><p>Der Zustand des neuen Threads, nachdem es zuvor abgeschaltet wurde.</p></td>
</tr>
<tr class="odd">
<td><p>NewPrevWaitMode</p></td>
<td><p>Der warten Modus des neuen Threads, wenn es zuvor abgeschaltet wurde.</p></td>
</tr>
<tr class="even">
<td><p>NewPrevWaitReason</p></td>
<td><p>Der Grund, dem der neue Thread abgeschaltet wurde.</p></td>
</tr>
<tr class="odd">
<td><p>NewPriDecr</p></td>
<td><p>Die Priorität, die die Thread wirkt sich auf.</p></td>
</tr>
<tr class="even">
<td><p>NewProcess</p></td>
<td><p>Der Vorgang des neuen Threads.</p></td>
</tr>
<tr class="odd">
<td><p>NewProcess Namen</p></td>
<td><p>Der Name des Prozesses des neuen Threads, einschließlich PID.</p></td>
</tr>
<tr class="even">
<td><p>NewQnt</p></td>
<td><p>Nicht verwendet.</p></td>
</tr>
<tr class="odd">
<td><p>NewState</p></td>
<td><p>Der Zustand des neuen Threads, nachdem es in gewechselt wird.</p></td>
</tr>
<tr class="even">
<td><p>NewThreadId</p></td>
<td><p>Die Thread-ID des neuen Threads.</p></td>
</tr>
<tr class="odd">
<td><p>NewThreadStack</p></td>
<td><p>Der Stapel des neuen Threads, wenn es in gewechselt wird.</p></td>
</tr>
<tr class="even">
<td><p>NewThreadStartFunction</p></td>
<td><p>Die Startfunktion des neuen Threads.</p></td>
</tr>
<tr class="odd">
<td><p>NewThreadStartModule</p></td>
<td><p>Das Modul Start des neuen Threads.</p></td>
</tr>
<tr class="even">
<td><p>NewWaitMode</p></td>
<td><p>Der von den neuen Thread Wait-Modus.</p></td>
</tr>
<tr class="odd">
<td><p>NewWaitReason</p></td>
<td><p>Der Grund, dem der neue Thread abgeschaltet wurde.</p></td>
</tr>
<tr class="even">
<td><p>NextSwitchOutTime(s)</p></td>
<td><p>Die Zeit, die bei der neue Thread als Nächstes abgeschaltet wurde.</p></td>
</tr>
<tr class="odd">
<td><p>OldInSwitchTime(s)</p></td>
<td><p>Die Zeit, der der alte Thread in gewechselt wurde, bevor er abgeschaltet wurde.</p></td>
</tr>
<tr class="even">
<td><p>OldOutPri</p></td>
<td><p>Die Priorität des alten Threads beim abgeschaltet wurde.</p></td>
</tr>
<tr class="odd">
<td><p>OldProcess</p></td>
<td><p>Der Prozess, der den alten Thread besitzt.</p></td>
</tr>
<tr class="even">
<td><p>OldProcess Namen</p></td>
<td><p>Der Name des Prozesses, der den alten Thread, einschließlich PID besitzt.</p></td>
</tr>
<tr class="odd">
<td><p>OldQnt</p></td>
<td><p>Nicht verwendet.</p></td>
</tr>
<tr class="even">
<td><p>OldState</p></td>
<td><p>Der Zustand des alten Threads nach abgeschaltet ist.</p></td>
</tr>
<tr class="odd">
<td><p>OldThreadId</p></td>
<td><p>Die Thread-ID des alten Threads.</p></td>
</tr>
<tr class="even">
<td><p>OldThreadStartFunction</p></td>
<td><p>Die Startfunktion des alten Threads.</p></td>
</tr>
<tr class="odd">
<td><p>OldThreadStartModule</p></td>
<td><p>Das Modul Start des alten Threads.</p></td>
</tr>
<tr class="even">
<td><p>OldWaitMode</p></td>
<td><p>Die Wait-Modus des alten Threads.</p></td>
</tr>
<tr class="odd">
<td><p>OldWaitReason</p></td>
<td><p>Der Grund, dem der alte Thread abgeschaltet wurde.</p></td>
</tr>
<tr class="even">
<td><p>PrevCState</p></td>
<td><p>Die vorherigen CState des Prozessors werden soll. Wenn dies nicht der Fall ist 0 (aktiv), der Prozessor wurde im Leerlauf, bevor Kontextwechsel in der neue Thread wurde.</p></td>
</tr>
<tr class="odd">
<td><p>READY(s)</p></td>
<td><p>SwitchInTime(s) MinusReadyTime (s)</p></td>
</tr>
<tr class="even">
<td><p>ThreadId des</p></td>
<td><p>Die Thread-ID des Threads readying.</p></td>
</tr>
<tr class="odd">
<td><p>Des ThreadStartFunction</p></td>
<td><p>Die Startfunktion des readying Threads.</p></td>
</tr>
<tr class="even">
<td><p>Des ThreadStartModule</p></td>
<td><p>Das Modul Start des readying Threads.</p></td>
</tr>
<tr class="odd">
<td><p>ReadyingProcess</p></td>
<td><p>Der Prozess, der den readying Thread besitzt.</p></td>
</tr>
<tr class="even">
<td><p>ReadyingProcess Namen</p></td>
<td><p>Der Name des Prozesses, der den readying Thread, einschließlich PID besitzt.</p></td>
</tr>
<tr class="odd">
<td><p>ReadyThreadStack</p></td>
<td><p>Der von der readying Thread-Stapel.</p></td>
</tr>
<tr class="even">
<td><p>ReadyTime (s)</p></td>
<td><p>Der Zeitpunkt, wann der neue Thread Scanthreads wurde.</p></td>
</tr>
<tr class="odd">
<td><p>SwitchInTime(s)</p></td>
<td><p>Der Zeitpunkt, wann in der neue Thread gewechselt wurde.</p></td>
</tr>
<tr class="even">
<td><p>TimeSinceLast (s)</p></td>
<td><p>SwitchInTime(s) minus LastSwitchOutTime (s)</p></td>
</tr>
<tr class="odd">
<td><p>Wartet (s)</p></td>
<td><p>ReadyTime (s) minus LastSwitchOutTime (s)</p></td>
</tr>
</tbody>
</table>

 

Das Standardprofil verwendet die folgenden Vorgaben für dieses Diagramm:

-   Zeitachse von CPU

-   Vom Prozess, Thread Zeitachse

-   Verwendung der nach Priorität unter Kontext Switch beginnen

-   Nutzung von CPU

-   Vom Prozess, Thread Auslastung

### <a name="timeline-by-cpu"></a>Zeitachse von CPU

**CPU-Auslastung** auf einer Zeitskala CPU-zeigt, wie die Arbeit auf Prozessoren verteilt ist. Abbildung 11 CPU-Auslastung (exakt) Zeitachse von CPU zeigt die Zeitskala für ein System acht Prozessoren:

![Abbildung 11 CPU-Verwendung exakte Zeitachse von cpu](images/dep-win8-cpu-techniques-figure-11-cpu-usage-precise-timeline-by-cpu.png)

**Abbildung 11 CPU-Auslastung (exakt) Zeitachse von CPU**

### <a name="timeline-by-process-thread"></a>Vom Prozess, Thread Zeitachse

**CPU-Auslastung** auf der Zeitachse ein pro Prozess, pro Thread zeigt, welche Prozesse Threads zu bestimmten Zeiten ausgeführt wurde. Abbildung 12 Usage (Precise) Zeitachse vom Prozess, Thread diese Zeitachse für mehrere Prozesse zeigt:

![Abbildung 12 Nutzung genauen Zeitachse nach Prozessthread](images/dep-win8-cpu-techniques-figure-12-usage-precise-timeline-by-process-thread.png)

**Abbildung 12: Einsatz (exakt) Zeitachse vom Prozess, Thread**

### <a name="usage-by-priority-at-context-switch-begin"></a>Verwendung der nach Priorität unter Kontext Switch beginnen

Dieses Diagramm identifiziert Bursts von Thread mit hoher Priorität-Aktivität auf den einzelnen Ebenen Priorität. Abbildung 13 CPU-Auslastung (Precise) Verwendung der nach Priorität am Switch mit der Kontext zeigt die Verteilung von Prioritäten:

![Abbildung 13 CPU-Verwendung exakte Auslastung nach Priorität bei c](images/dep-win8-cpu-techniques-figure-13-cpu-usage-precise-usage-by-priority-at-context-switch-start.png)

**Abbildung 13 CPU-Auslastung (exakt) Verwendung nach Priorität unter Kontext Switch beginnen**

### <a name="utilization-by-cpu"></a>Nutzung von CPU

In diesem Diagramm ist CPU-Auslastung gruppiert und CPU-Nutzung, um anzuzeigen, wie die Arbeit auf Prozessoren verteilt ist grafisch dargestellt. Abbildung 14 CPU-Auslastung (Precise) Nutzung von CPU zeigt dieses Diagramm für ein System, das acht Prozessoren verfügt.

![Abbildung 14 CPU-Auslastung genaue Auslastung von cpu](images/dep-win8-cpu-techniques-figure-14-cpu-usage-precise-utilization-by-cpu.png)

**Abbildung 14 CPU-Auslastung (exakt) Nutzung von CPU**

### <a name="utilization-by-process-thread"></a>Nutzung von Prozess, Thread

In diesem Diagramm ist CPU-Auslastung zunächst nach Prozess und dann nach Threads gruppiert. Es zeigt der relativen Nutzung der Prozesse und Threads in jedem Prozess Abbildung 15 CPU-Auslastung (Precise) Auslastung von Prozess, Thread diese Verteilung für mehrere Prozesse:

![Abbildung 15 CPU-Verwendung exakte Auslastung vom Prozess](images/dep-win8-cpu-techniques-figure-15-cpu-usage-precise-utilization-by-process-thread.png)

**Abbildung 15 CPU-Auslastung (exakt) Nutzung von Prozess, Thread**

### <a name="dpcisr-graph"></a>DPC/ISR-Diagramm

Das Diagramm DPC/ISR ist die primäre Quelle für DPC/ISR Informationen in WPA. Jede Zeile im Diagramm stellt ein Fragment eine bestimmte Zeitspanne in dem wird eine DPC oder ISR ohne Unterbrechung ausgeführt haben. Daten werden am Anfang und Ende Fragmente erfasst. Zusätzliche Daten werden erfasst, wenn ein DPC/ISR abgeschlossen ist. Abbildung 16 DPC/ISR Diagramm zeigt, wie dies funktioniert:

![Abbildung 16 Dpc Isr Diagramm](images/dep-win8-cpu-techniques-figure-16-dpc-isr-diagram.jpg)

**Abbildung 16 DPC/ISR-Diagramm**

Abbildung 16 DPC/ISR Diagramm werden während der folgenden Aktivitäten gesammelten Daten beschrieben:

1.  **DPC/ISR-A** beginnt mit der Ausführung.

2.  Ein Interrupt Gerät, der eine höhere Interruptebene als **DPC/ISR-A** verfügt bewirkt, dass **ISR B** , **DPC/ISR ein**, wodurch beziehen, die das erste **DPC/ISR-A**-Fragment zu unterbrechen.

3.  **ISR-B** abgeschlossen ist und zum anschließenden endet das **ISR-B**-Fragment. **DPC/ISR-A** setzt die Ausführung in einem zweiten Fragment.

4.  **DPC/ISR-A** abgeschlossen ist, wodurch das zweite **DPC/ISR-A**-Fragment endet.

Eine Zeile für jedes Fragment wird in der Datentabelle angezeigt. Die Fragmente für **DPC/ISR-A** Informationsaustausch identische mit nicht-Fragment Spalten.

Die Spalten für das Diagramm DPC/ISR beschreiben Fragment auf Systemebene Informationen oder DPC/ISR Spalten auf. Jedes Fragment unterschiedliche Daten in Spalten Fragment-Ebene und identischen Daten in DPC/ISR Spalten.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Spalte</th>
<th>Details</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>% Dauer (fragmentiert)</p></td>
<td><p>Dauer (fragmentiert), ausgedrückt als Prozentsatz der gesamten CPU-Zeit über den sichtbaren Zeitraum an.</p></td>
</tr>
<tr class="even">
<td><p>% Exklusive Dauer</p></td>
<td><p>Exklusive Dauer, die als Prozentsatz der gesamten CPU-Zeit ausgedrückt wird, über den sichtbaren Zeitraum an.</p></td>
</tr>
<tr class="odd">
<td><p>% Inklusive Dauer</p></td>
<td><p>Einschließlich Dauer, die als Prozentsatz der gesamten CPU-Zeit ausgedrückt wird, über den sichtbaren Zeitraum an.</p></td>
</tr>
<tr class="even">
<td><p>Adresse </p></td>
<td><p>Die Adresse des Arbeitsspeichers der DPC oder ISR-Funktion.</p></td>
</tr>
<tr class="odd">
<td><p>Count (DPCs/ISRs)</p></td>
<td><p>Die Anzahl der DPCs/ISRs, die von dieser Zeile dargestellt werden. Dies ist immer 1 für Zeilen, die das endgültige eine DPC/ISR-Fragment darstellen. Andernfalls ist diese Anzahl 0.</p></td>
</tr>
<tr class="even">
<td><p>Count (Fragmente)</p></td>
<td><p>Die Anzahl der Fragmente, die von der Zeile dargestellt werden. Dies ist immer 1 für die einzelnen Zeilen.</p></td>
</tr>
<tr class="odd">
<td><p>CPU</p></td>
<td><p>Der Index des logischen Prozessor auf dem die DPC oder ISR ausgeführt wurde.</p></td>
</tr>
<tr class="even">
<td><p>DPC-Typ</p></td>
<td><p>Für DPC den Typ des DPC,-reguläre oder den Timer. Dieser Wert ist leer für eine ISR.</p></td>
</tr>
<tr class="odd">
<td><p>Geben Sie DPC/ISR Zeit (s)</p></td>
<td><p>Die Zeit in der Verfolgung Wenn DPC/ISR gestartet.</p></td>
</tr>
<tr class="even">
<td><p>DPC/ISR Exit Zeit (s)</p></td>
<td><p>Die Zeit vom Anfang des Trace Wenn DPC/ISR ausgeführt.</p></td>
</tr>
<tr class="odd">
<td><p>Dauer (fragmentiert) (in Millisekunden)</p></td>
<td><p>Fragment Exit Zeit (s) minus Fragment Geben Sie Zeit (s) in Millisekunden an.</p></td>
</tr>
<tr class="even">
<td><p>Exklusive Dauer (in Millisekunden)</p></td>
<td><p>Die Summe der fragmentierten Dauer in Millisekunden. Alle diese DPC/ISR.-Fragmenten</p></td>
</tr>
<tr class="odd">
<td><p>Fragment</p></td>
<td><p>Dieser Wert ist <strong>True</strong>, wenn die DPC/ISR dieser Zeile mehrere Fragmente hatten. Andernfalls ist er <strong>False</strong>.</p></td>
</tr>
<tr class="even">
<td><p>Fragment</p></td>
<td><p>Wenn dies nicht das einzige-Fragment für diese DPC/ISR war, ist dieser Wert <strong>True</strong>. Andernfalls ist er <strong>False</strong>.</p></td>
</tr>
<tr class="odd">
<td><p>Geben Sie Fragment Zeit (s)</p></td>
<td><p>Die Zeit, die das Fragment Schritte ausführen.</p></td>
</tr>
<tr class="even">
<td><p>Fragment Exit Zeit (s)</p></td>
<td><p>Die Zeit, die das Fragment beendet.</p></td>
</tr>
<tr class="odd">
<td><p>Funktion</p></td>
<td><p>Die DPC oder ISR-Funktion, die ausgeführt wurden.</p></td>
</tr>
<tr class="even">
<td><p>Inklusive Dauer (in Millisekunden)</p></td>
<td><p>DPC/ISR Exit Zeit (s) minus DPC/ISR Geben Sie Zeit (s) in Millisekunden.</p></td>
</tr>
<tr class="odd">
<td><p>MessageIndex</p></td>
<td><p>Der Index der Interrupt für Interrupts Nachricht signalisiert.</p></td>
</tr>
<tr class="even">
<td><p>Modul</p></td>
<td><p>Das Modul, das die DPC oder ISR-Funktion enthält.</p></td>
</tr>
<tr class="odd">
<td><p>Rückgabewert</p></td>
<td><p>Der Rückgabewert der DPC/ISR</p></td>
</tr>
<tr class="even">
<td><p>Typ</p></td>
<td><p>Den Typ des Ereignisses; Hierbei handelt es sich-DPC oder unterbrechen (ISR).</p></td>
</tr>
<tr class="odd">
<td><p>Vektor</p></td>
<td><p>Der Wert des der Interruptvektor auf dem Gerät.</p></td>
</tr>
</tbody>
</table>

 

Das Standardprofil verwendet die folgenden Vorgaben für dieses Diagramm:

-   \[DPC ISR; DPC/ISR\] für die Dauer nach CPU

-   \[DPC ISR, DPC/ISR\] für die Dauer nach Modul-Funktion

-   \[DPC ISR, DPC/ISR\] Zeitachse Module-Funktion

### <a name="a-href-id-dpc-isr-dpc-isr--duration-by-cpuadpcisrdpcisr-duration-by-cpu"></a><a href="" id="-dpc-isr-dpc-isr--duration-by-cpu"></a>\[DPC ISR, DPC/ISR\] für die Dauer nach CPU

DPC/ISR-Ereignisse werden von der CPU aggregiert, deren ausgeführt wurde und nach Dauer sortiert sind. Dieses Diagramm zeigt die Zuweisung von DPC Aktivität über CPUs. Abbildung 17 DPC/ISR Dauer von CPU zeigt dieses Diagramm für ein System, das acht Prozessoren verfügt.

![Abbildung 17 Dpc Isr Dauer von cpu](images/dep-win8-cpu-techniques-figure-17-dpc-isr-duration-by-cpu.png)

**Abbildung 17 DPC/ISR Dauer von CPU**

### <a name="a-href-id-dpc-isr-dpc-isr--duration-by-module--functionadpcisrdpcisr-duration-by-module-function"></a><a href="" id="-dpc-isr-dpc-isr--duration-by-module--function"></a>\[DPC ISR, DPC/ISR\] für die Dauer nach Modul-Funktion

DPC/ISR-Ereignisse werden in diesem Diagramm mithilfe des Moduls und der Funktion DPC/ISR Routinen aggregiert und nach Dauer sortiert sind. Dieses zeigt an, welche DPC/ISR Routinen, die am häufigsten verbraucht, Zeit Abbildung 18 DPC/ISR Dauer vom Modul, Funktion zeigt eine bestimmte Zeitspanne, die verursacht DPC/ISR Aktivität in zwei Modulen:

![Abbildung 18 Dpc Isr Dauer von Modulfunktion](images/dep-win8-cpu-techniques-figure-18-dpc-isr-duration-by-module-function.png)

**Abbildung 18 DPC/ISR Dauer vom Modul Funktion**

### <a name="a-href-id-dpc-isr-dpc-isr--timeline-by-module--functionadpcisrdpcisr-timeline-by-module-function"></a><a href="" id="-dpc-isr-dpc-isr--timeline-by-module--function"></a>\[DPC ISR, DPC/ISR\] Zeitachse Module-Funktion

DPC/ISR-Ereignisse werden in diesem Diagramm mithilfe des Moduls und der Funktion DPC/ISR Routinen aggregiert. Sie sind als Zeitplan grafisch dargestellt. Dieses Diagramm bietet eine detaillierte Ansicht des Zeitraums, über die DPCs/ISRs ausgeführt wurde. Dieses Diagramm kann auch zum einmaligen DPC/ISRs anzeigen fragmentiert werden können. Abbildung 19 DPC/ISR Zeitachse vom Modul zeigt Funktion eine Zeitskala der Aktivität in drei Module:

![Abbildung 19 Dpc Isr Zeitachse von Modulfunktion](images/dep-win8-cpu-techniques-figure-19-dpc-isr-timeline-by-module-function.png)

**Abbildung 19 DPC/ISR Zeitachse vom Modul Funktion**

### <a name="stack-trees"></a>Stack Strukturen

Stack Strukturen werden in den Tabellen **CPU-Auslastung (abgetastete)**, **CPU-Auslastung (Precise)** und **DPC/ISR** in WPA und ermittelte in Assessment-Berichten angezeigt. Stack Strukturen stellen die Call-Stapel, die über einen Zeitraum mit mehreren Ereignissen verknüpft sind. Jeder Knoten in der Struktur stellt ein Stack-Segment, das von einer Teilmenge der Ereignisse gemeinsam verwendet wird. Die Struktur wird von den einzelnen Stapeln erstellt und wird in Abbildung 20 Stapeln aus drei Ereignisse angezeigt:

![Abbildung 20 Stapel aus drei Ereignisse](images/dep-win8-cpu-techniques-figure-20-stacks-from-three-events.jpg)

**Abbildung 20 Stapel aus drei Ereignisse**

Abbildung 21 allgemeine Segmente identifiziert zeigt, wie gemeinsame Sequences, werden für dieses Diagramm identifiziert:

![Abbildung 21 allgemeinen Segmente identifiziert](images/dep-win8-cpu-techniques-figure-21-common-segments-identified.jpg)

**Abbildung 21 allgemeinen Segmente identifiziert**

Abbildung 22 Struktur erstellt von Stapeln zeigt, wie die allgemeinen Segmente kombiniert werden, um die Knoten einer Struktur zu bilden:

![Abbildung 22 Struktur von Stapeln erstellt](images/dep-win8-cpu-techniques-figure-22-tree-built-from-stacks.jpg)

**Abbildung 22 Struktur von Stapeln erstellt**

Die **Stapel** -Spalte in der Benutzeroberfläche WPA enthält ein – Erweiterung für jeden Knoten innerer Knotenebene. Unter Assessment gemeldete Probleme ist die Struktur zusammen mit der aggregierte Weights angezeigt. Einige in den Zweigstellen können aus dem Diagramm entfernt werden, wenn ihre Weights ein angegebenen Schwellenwerts nicht entsprechen. Im nachfolgenden Beispielstapel zeigt, wie die oben dargestellten Ereignisse im Rahmen eines Problems Assessment gemeldete angezeigt werden.

``` syntax
5ms   ModuleA!Function1
5ms   ModuleA!Function2
5ms   ModuleA!Function3
      |
4ms   |-ModuleA!Function4
4ms   |   ModuleB!Function1
      |   |
1ms   |   |-ModuleB-Function2
1ms   |   |    ModuleB-Function3
      |   |
3ms   |   |-ModuleB!Function3
3ms   |        ModuleB!Function4
      |
1ms   |-ModuleA!Function5
1ms        ModuleC!Function1
1ms        ModuleC!Function2
```

Die `<itself>` Knoten in einem Stapel gibt die Zeit, die eine Funktion selbst am unteren Rand des Stapels ist. Die `<itself>` Knoten umfasst nicht die Zeitspanne für die Funktionen, die von der übergeordneten Funktion aufgerufen werden. Dauer der *exklusiven* Zeit aufgerufen wird für die Funktion aufgewendeten.

Beispielsweise ruft **Function1** **Funktion2**. **Funktion2** aufgewendeten 2 in einer Schleife CPU-intensiver MS und eine andere Funktion, die ausgeführt wurden für 4ms aufgerufen. Dies kann durch den folgenden Stapel dargestellt werden:

``` syntax
6ms   ModuleA!Function1
      |
2ms   |-<itself>
4ms   |-ModuleA!Function2
4ms        ModuleB!Function3
4ms        ModuleB-Function4
```

## <a name="a-href-idcpu-guide-techniquesatechniques"></a><a href="" id="cpu-guide-techniques"></a>Techniken (engl.)


In diesem Abschnitt wird einen allgemeiner Ansatz zur Leistungsanalyse. Es bietet Techniken, die Sie verwenden können, allgemeine CPU-bezogene Leistungsprobleme untersuchen.

Performance-Analyse ist der Prozess, vier Schritten:

1.  Definieren Sie das Szenario und das Problem.

2.  Identifizieren Sie die Komponenten, die beteiligt sind und die relevanten Zeitbereich.

3.  Erstellen Sie ein Modell eines was passiert sollten.

4.  Mithilfe des Objektmodells zum Erkennen von Problemen und untersuchen Ursachen.

### <a name="define-the-scenario-and-the-problem"></a>Definieren des Szenarios und das Problem

Der erste Schritt bei der Leistungsanalyse ist des Szenarios und das Problem klar definiert. Viele Leistungsprobleme Einfluss auf Szenarien, die von Assessment Metriken gemessen werden. Beispiel:

Szenario 1: Eine physische Ressource ist nicht vollständig genutzt werden. Beispielsweise kann kein Server vollständig eine Netzwerkverbindung zu nutzen, da Pakete nicht schnell genug verschlüsseln kann.

Szenario 2: Eine physische Ressource ist ausgelastet mehr als sein sollte. Beispielsweise verwendet ein System erhebliche CPU-Ressourcen während einer Leerlaufzeit, die Batterie verwendet.

Szenario 3: Die Aktivitäten werden nicht mit einer Rate erforderlichen abgeschlossen. Beispielsweise werden Frames Videowiedergabe gelöscht, da die Rahmen nicht schnell genug decodiert wird.

Szenario 4: Eine Aktivität wurde verzögert. Angenommen, der Benutzer, die Internet Explorer gestartet, aber ausgeführt wurden länger als erwartet, dass eine Registerkarte öffnen.

Szenario 3 und 4 werden, wie sie im Zusammenhang mit der CPU-Ressourcen in diesem Handbuch behandelt. Szenarien 1 und 2 sind außerhalb des Gültigkeitsbereichs und werden nicht behandelt. Um diese Probleme zu analysieren, können Sie mit eine mehrdeutige Beobachtung beginnen, wie "es zu langsam ist" und zusätzliche Fragen, um das Szenario und genau das Problem zu identifizieren.

### <a name="a-href-ididentify-the-components-and-the-time-period-aidentify-the-components-and-the-time-period"></a><a href="" id="identify-the-components-and-the-time-period-"></a>Identifizieren Sie die Komponenten und den Zeitraum an

Nachdem das Szenario und das Problem identifiziert werden, können Sie ermitteln, die Komponenten, die beteiligt sind und die betreffenden Zeitraum. Die Komponenten beinhalten Hardwareressourcen, Prozesse und Threads.

Den Zeitbereich des Zinsen finde häufig durch das Identifizieren der zugeordneten Aktivitätsfeeds im Handbuch für die Analyse. Eine Aktivität ist ein Intervall zwischen ein Startereignis und ein Beendigungsereignis, die Sie auswählen und vergrößern in WPA können. Wenn eine Aktivität nicht definiert ist, finden Sie den Zeitbereich Nachrichtensymbol generische für bestimmte Ereignisse, die mit dem Szenario verknüpft sind oder suchen Sie nach Änderungen in Ressourcenverwendung, die am Anfang und Ende ein Szenario markieren können. Erfasst beispielsweise wenn die CPU wurde zwei Sekunden und vollständig vier Sekunden genutzt, und klicken Sie dann im Leerlauf erneut zwei Sekunden, die vier Sekunden des vollständigen Auslastung möglicherweise der Interessenbereich in einer Ablaufverfolgung für, die Videowiedergabe.

### <a name="create-a-model"></a>Erstellen eines Modells

Um zu verstehen, dass die Ursachen für ein Problem, benötigen Sie ein Modell eines was passiert sollten. Details des Modells beginnt mit der Problem oder ein beliebiges zugeordnete Ziel für die Metrik. beispielsweise "dieser Vorgang sollte in weniger als 5 Sekunden abgeschlossen haben."

Ein vollständiges Modell enthält Informationen über die Komponenten wie durchgeführt werden soll. Angenommen, welche Art von Kommunikation zwischen den Komponenten erwartet wird? Welche Ressourcenverwendung typisch ist? Wie lange werden Vorgänge in der Regel werden?

Häufig im Handbuch zur Bewertung von Analysis finden Sie Informationen für das Objektmodell. Wenn diese Ressource nicht verfügbar ist, können Sie einen Trace von ähnlicher Hardware und Software, die nicht das Leistungsproblem, um ein Modell zu erstellen aufweisen wird erstellen.

### <a name="use-the-model-to-identify-problems-and-then-investigate-root-causes"></a>Verwenden Sie das Modell, um Probleme zu identifizieren, und klicken Sie dann untersuchen Sie Ursachen

Nachdem Sie ein Modell haben, können Sie eine Verfolgung auf das Objektmodell zur Identifizierung von Problemen vergleichen. Beispielsweise kann ein Modell für eine bestimmte Aktivität **Anhalten Geräte** aufgerufen vorgeschlagen, dass die gesamte Aktivität in drei Sekunden ausführen sollten, während jeder Instanz einer untergeordneten Aktivität aufgerufen **Suspend &lt;Gerätename&gt; ** sollten nicht mehr als 100 ms dauern. Wenn zwei Instanzen der untergeordneten Aktivität **Suspend &lt;Gerätename&gt; ** jeder 800ms ausgeführt werden, sollten Sie die Instanzen untersuchen.

Jede Abweichung aus dem Modell kann analysiert werden, um die Ursache zu suchen. Sie sollten den Status der beteiligten Threads untersuchen, und suchen Sie nach häufige Ursachen. Einige wichtige CPU-bezogenen Ursachen, für Aktivitäten, die nicht mit einer erforderlichen Rate abschließen oder verzögert werden, werden hier beschrieben:

Direkte CPU-Auslastung: die entsprechenden Threads empfangen vollständige CPU-Ressourcen aber das erforderliche Programm wurde nicht schnell genug ausgeführt. Dies kann durch eines Ausfalls der Anwendung oder durch langsame Hardware verursacht werden.

Thread Störungen: Ein Thread nicht genug Ausführungszeit abgerufen werden, da andere Threads stattdessen ausgeführt wurden. In diesem Fall gilt der Thread Sicherstellung oder getrennt werden.

DPC/ISR Störungen: Threads konnte genug Ausführungszeit nicht erhalten, da CPUs Verarbeitung DPCs oder ISRs beschäftigt waren.

In vielen Fällen eine der folgenden Ursachen deutlich wirkt sich nicht im Thread und Threads die meiste Zeit in einem wartenden Zustand. In diesem Fall müssen Sie erkennen und Untersuchen des Ereignisses, für die der Thread wartet. Dieses Typs rekursive Untersuchung *Warten Analysis*aufgerufen, und er beginnt, durch das Identifizieren von des kritischen Weges.

### <a name="advanced-technique-wait-analysis-and-the-critical-path"></a>Fortgeschrittene Technik: Warten Sie Analysis und den kritischen Weg

Eine Aktivität ist ein Netzwerk Vorgänge, einige sequenzielle und einige Parallel, die aus einem Startereignis auf ein Endereignis. Alle Start-/End Ereignispaar in eine Verfolgung können als Aktivität angezeigt werden. Der längste Pfad über dieses Netzwerk von Vorgängen wird als kritisch bezeichnet werden. Die Dauer der Aktivität des gesamten verringern die Dauer der alle Vorgänge auf dem kritischen Pfad direkt reduziert werden, obwohl sie auch den kritischen Weg ändern kann.

Abbildung 23 Aktivität Vorgänge zeigt die Aktivitäten von drei Threads. Thread 1 sendet des Aktivitätsereignisses starten und dann wartet Thread 2 und Thread-3, um ihre Aufgaben durchzuführen. Thread-2 schließt die Aufgabe zuerst, gefolgt von Thread-3. Wenn beide Threads ihre Aufgaben abgeschlossen haben, Thread-1 ist Scanthreads und Abschluss des Aktivitätsereignisses.

![Abbildung 23 Aktivität Vorgänge](images/dep-win8-cpu-techniques-figure-23-activity-operations.jpg)

**Abbildung 23 Aktivität Vorgänge**

In diesem Szenario enthält der kritische Weg Teile eines Thread-3 und Thread-1. Diese werden in Abbildung 24 Critical Path verfolgt. Da Thread-2 nicht auf dem kritischen Pfad ist, wirkt sich die Zeit, die zum Abschließen der Aufgabe nicht die Gesamtdauer der Aktivität.

![Abbildung 24 kritischen Weg](images/dep-win8-cpu-techniques-figure-24-critical-path.jpg)

**Abbildung 24 kritischen Weg**

Der kritische Pfad ist eine Low-Level Literale Antwort auf die Frage, warum eine Aktivität so viele gedauert wie an. Nach dem Schlüssel Segmente des kritischen Weg bekannt sind, können sie analysiert werden, um die Probleme zu finden, die an die allgemeine Verzögerung beteiligen.

### <a name="general-approach-to-finding-the-critical-path"></a>Allgemeiner Ansatz zur Suche nach dem kritischen Pfad

Der erste Schritt bei der Suche nach dem kritischen Pfad ist, überprüfen Sie das Szenario-Modell, um den Zweck und Implementierung der Aktivität verstehen.

Grundlegendes zu einer Aktivität ermitteln bestimmter Vorgänge, Prozesse und Threads, die auf dem kritischen Pfad möglicherweise helfen kann. Beispielsweise kann eine Verzögerung in der **Fast Start Resume Explorer Init** -Aktivität von **RunOnce** -Anwendungen und der Explorer Initialisierung-Prozess, der beide über eine große Menge von e/a erfordern verursacht werden.

Nachdem Sie das Szenario Modell überprüft haben, überprüfen Sie, ob die Bewertung von Problemen für die betroffenen Aktivität gemeldet. In vielen Fällen ist ein Näherungswert des kritischen Pfades in Verzögerung Assessment gemeldete Probleme enthalten. Kritischen Pfades wird als Folge von Wartezeiten und bereit Aktionen angezeigt. Es kann von Anfang bis Ende als Folge von Ereignissen mit dem primären verzögerte Segment des kritischen Pfades in der Mitte der Liste gelesen werden. Der letzte Eintrag in der Liste ist die Aktion, die den Thread Scanthreads, der die Aktivität abgeschlossen.

Wenn Sie manuell für den kritischen Pfad gesucht werden müssen, sollten Sie identifizieren den Prozess und der Thread, der die Aktivität und die Arbeit Abwärtskompatibilität von Instant abgeschlossen, die die Aktivität abgeschlossen. Sie können den Prozess und Thread, der eine Aktivität und den Prozess gestartet und Thread, der eine Aktivität, durch die **Aktivitäten** Diagramm in WPA abgeschlossen identifizieren.

Das Diagramm **Aktivitäten** angezeigt, wenn die Ablaufverfolgung über eine Bewertung Ergebnisse XML-Datei geladen wird. Zum Identifizieren des Prozesses und der Thread, der eine bestimmte Aktivität zugeordnet sind, erweitern Sie im Diagramm auf die Aktivität von Interesse, und wechseln Sie die Ansicht in **Diagramm +-Tabelle**. Legen Sie den Diagrammmodus **Tabelle**. Spalten **Prozess starten**, **Starten Sie Thread-Id**, **End-Prozess**und **End Thread-Id** anzeigen für jede Aktivität in der Tabelle

Nachdem Sie das Start- und End-Prozess, der Thread und der Implementierung der Aktivität kennen, kann der kritische Weg rückwärts verfolgt werden. Start durch die Analyse des Threads, der die Aktivität, um zu bestimmen, wie dieser Thread den größten Teil seiner Zeit aufgewendet wurde abgeschlossen: ausgeführt wird, wartet oder bereit.

Erhebliche Ausführungszeit gibt an, dass direkte CPU-Auslastung auf die Dauer des kritischen Pfades beigetragen haben kann. Zeit im ready-Modus gibt an, dass andere Threads auf die Dauer des kritischen Pfades beitragen, indem Sie verhindern, dass einen Thread auf dem kritischen Pfad ausführen. Zeitaufwand für Warten Kriterien, die e/a, Zeitgeber, oder andere Threads und Prozesse auf dem kritischen Pfad für den aktuelle Thread wartete.

Jeder Thread, der den aktuellen Thread Scanthreads ist wahrscheinlich einen weiteren Link im kritischen Pfad und kann ebenfalls analysiert werden, bis die Dauer des kritischen Pfades berücksichtigt wird.

**Vorgehensweise: Suchen von kritischen Pfades in WPA**

Das folgende Verfahren wird davon ausgegangen, dass Sie eine Aktivität im Diagramm Aktivitäten identifiziert haben, für den kritischen Weg ermittelt werden soll.

1.  Sie können den Prozess, der die Aktivität abgeschlossen durch Bewegen der Aktivitätsfeeds im Diagramm **Aktivitäten** zu identifizieren.

2.  Das **CPU-Auslastung (Precise)** Diagramm hinzufügen. Zoom, um die betroffenen Aktivität und die **Nutzung von Prozess, Thread** Voreinstellung anwenden.

3.  Mit der rechten Maustaste der Spaltenüberschriften und sichtbar machen, die Spalten **ReadyThreadStack** und **CPU-Auslastung (in Millisekunden)** . Entfernen der **bereit (us) \[Max\] ** und **wartet (us) \[Max\] ** Spalten.

4.  Erweitern Sie den Zielprozess und sortieren Sie sie jeweils nach **CPU-Auslastung (in Millisekunden)**, **bereit (us) \[Summe\]**, und **wartet (us) \[Summe\]**.

5.  Suchen Sie nach der **NewThreadIds** im Prozess, der die höchste Zeitraums ausgeführt, bereit, oder warten Zustand hat.

    Threads, die in der Ausführung oder bereit Staaten erhebliche Zeit möglicherweise direkte CPU-Auslastung auf dem kritischen Pfad darstellen. Beachten Sie ihre Thread, den IDs.Threads, die den Status Inaktiv erhebliche Zeit möglicherweise auf e/a, eines Zeitgebers oder auf einem anderen Thread im kritischen Pfad wartet.

6.  Um zu ermitteln, was die Threads warten wurden, erweitern Sie in der Gruppe **NewThreadId** , um die **ReadyThreadStack**anzuzeigen.

7.  Erweitern Sie ** \[Root\]**.

8.  Stapel, die mit **KiDispatchInterrupt** beginnen beziehen sich nicht auf einen anderen Thread. Um zu ermitteln, was in diesen Stapeln Threads für wartete, erweitern Sie **KiDispatchInterrupt** , und zeigen Sie die Funktionen auf dem untergeordneten-Stapel. **IopfCompleteRequest** gibt an, dass der gelesene Thread für e/a wartete. **KiTimerExpiration** gibt an, dass der gelesene Thread für einen Zeitgeber wartete.

9.  Erweitern Sie Stapel, die nicht mit **KiDispatchInterrupt** beginnen, bis Sie einen **ReadyingProcess** und eine **ReadyingThread**angezeigt. Wenn der Prozess bereits erweitert ist, erweitern Sie den **NewThreadId** entspricht, die auf die **ReadyingThread**ein. Wiederholen Sie diesen Schritt, bis Sie einen Thread gefunden, der ausgeführt wird, bereit, ein weiterer Grund warten oder warten auf einen anderen Prozess ist. Wenn der Thread auf einem anderen Prozess wartet, wiederholen Sie dieses Verfahren mithilfe dieses Prozesses.

**Beispiel**

In diesem Beispiel wird eine Verzögerung in der Fast Start Resume Explorer Init-Aktivität. Eine Suche im Bereich **Probleme** zeigt, dass für diese Aktivität sieben Verzögerung vom Typ Probleme gemeldet werden. Jedes dieser Probleme kann als ein Segment des kritischen Pfades überprüft werden. Die folgenden wichtigen Segmente erkannt werden:

-   Thread 3872 des Prozesses TestBootStrapper.exe (3024) ist für 2.1 Sekunden unterbrochen.

-   Thread 3872 des Prozesses TestBootStrapper.exe (3024) Sekunde der CPU-Zeit verwendet.

-   Thread 3872 des Prozesses TestBootStrapper.exe (3024) leert eine Registrierungsstruktur 544 Millisekunden.

-   Thread 3872 des Prozesses TestBootStrapper.exe (3024) ausgesetzt 513 Millisekunden.

-   Threads 4052 und 4036 von Explorer.exe Lesen vom Datenträger, verursacht eine Verzögerung 461 Millisekunden.

-   Thread 3872 des Prozesses TestBootStrapper.exe (3024) entzieht 187 Millisekunden.

-   Thread 3872 des Prozesses, TestBootStrapper.exe 3,5 MB auf den Datenträger schreibt verursacht eine Verzögerung 178 Millisekunden, an.

Die Probleme anzuzeigen, dass diese Aktivität durch 5.2 Sekunden verzögert wurde. Diese Verzögerungen contribute einen großen Teil der allgemeinen Aktivitäten 6.3 Dauer. Die Anwendung TestBootStrapper.exe ist hauptsächlich für die Verzögerung verantwortlich, in erster Linie, da es andere Verarbeitungsaufgaben getrennt.

**Untersuchen von Problemen in den kritischen Weg**

1.  Zoom, um die betroffenen Region, und fügen Sie die Spalten **ReadyThreadStack** und **CPU-Auslastung (in Millisekunden)** .

2.  In diesem Fall ist Explorer.exe der Prozess, der die Aktivität abgeschlossen ist. Erweitern Sie den Prozess explorer.exe und sortieren Sie sie jeweils nach **CPU-Auslastung (in Millisekunden)**, **bereit (us) \[Summe\]**, und **wartet (us) \[Summe\]**, wie in den folgenden Abbildungen gezeigt:

    ![Abbildung 25-Aktivität, indem Sie CPU-Auslastung ms](images/dep-win8-cpu-techniques-figure-25-activity-by-cpu-usage-ms.png)

    **Abbildung 25-Aktivität, indem Sie CPU-Auslastung (ms)**

    ![Abbildung 26 Aktivität von kann jetzt uns](images/dep-win8-cpu-techniques-figure-26-activity-by-ready-us.png)

    **In Abbildung 26 Aktivität, indem Sie kann jetzt (USA)**

    ![wartet die Abbildung 27 Aktivität, indem Sie uns](images/dep-win8-cpu-techniques-figure-27-activity-by-waits-us.png)

    **Abbildung 27 Aktivität, indem Sie wartet (USA)**

3.  Sortieren nach die Spalte **CPU-Auslastung (ms)** zeigt eine obere untergeordnete Zeile 299 Millisekunden. Sortieren nach die **bereit (us) \[Summe\] ** Spalte wird eine Leiste untergeordnete Zeile des 46ms angezeigt. Sortieren nach die **wartet (us) \[Summe\] ** Spalte zeigt oberen untergeordnetes Element 5749 Millisekunden Zeile und eine zweite Zeile 4902 in Millisekunden. Da diese Zeilen erheblich auf die Verzögerung beitragen, sollten Sie sie weiter untersuchen.

4.  Erweitern Sie die Stapeln um readying Threads, siehe den folgenden Abbildungen anzuzeigen:

    ![Vorbereitung der Prozess und Thread vorbereitet](images/dep-win8-cpu-techniques-figure-28-readying-process-and-readying-thread-for-a-thread.png)

    **Abbildung 28 vorbereitet Prozess und Thread für einen Thread vorbereitet**

    ![Abbildung 29 vorbereitet Prozess und Thread für vorbereitet](images/dep-win8-cpu-techniques-figure-29-readying-process-and-readying-thread-for-another-thread.png)

    **Abbildung 29 vorbereitet Prozess und ein anderer Thread Thread vorbereitet**

    In diesem Beispiel wird die meiste des ersten Threads die Wartezeit für den Prozess RunOnce.exe zu beenden. Sie sollten untersuchen, Warum dauert der RunOnce.exe Prozess so viel Zeit in Anspruch. Der zweite Thread wartet auf dem ersten Thread und ist wahrscheinlich ein nicht signifikanter Link in der gleichen Wait Kette.

5.  Wiederholen Sie die Schritte in diesem Verfahren für RunOnce.exe ein. Die primäre Beiträge Spalte ist **wartet (USA)**, und es vier mögliche Mitwirkende hat.

6.  Erweitern Sie jeden Teilnehmer um anzuzeigen, dass die ersten drei beteiligte Personen sind jedes wartet auf die vierte Mitwirkender. Diese Situation macht die ersten drei Personen, die an die Kette Wait signifikanter. Die vierte Mitwirkender wartet auf einem anderen Prozess, TestBootStrapper.exe.

    In diesem Szenario wird in Abbildung 30 vorbereitet Vorgang und vorbereitet Thread für einen Thread in RunOnce.exe gezeigt:

    ![Abbildung 30 Vorbereitung der Prozess und Thread für vorbereitet](images/dep-win8-cpu-techniques-figure-30-readying-process-and-readying-thread-for-a-thread-in-runonce-exe.png)

    **Abbildung 30 Vorbereitung der Prozess und Thread für einen Thread in RunOnce.exe vorbereitet**

7.  Wiederholen Sie diese Schritte für TestBootStrapper.exe. Die Ergebnisse werden in den folgenden drei Abbildungen angezeigt:

    ![Abbildung 31 Threads von CPU-Auslastung ms](images/dep-win8-cpu-techniques-figure-31-threads-by-cpu-usage-ms.png)

    **In Abbildung 31 Threads CPU-Auslastung (ms)**

    ![Abbildung 32 Threads durch kann jetzt uns](images/dep-win8-cpu-techniques-figure-32-threads-by-ready-us.png)

    **Abbildung 32 Threads bereit (USA)**

    ![Abbildung 33 Threads durch Sperrenwartevorgänge uns](images/dep-win8-cpu-techniques-figure-33-threads-by-waits-us.png)

    **Abbildung 33 Threads durch wartet (USA)**

    Thread 3872 aufgewendet ungefähr 1 Sekunde ausgeführt, 2 Sekunden bereit und 1.3 Sekunden wartet. Da dieser Thread auch der readying Thread für Thread 3872 ist, werden die Zeiten ausgeführt wird und bereit wahrscheinlich zur die Verzögerung beitragen. Die Bewertung meldet die folgenden Probleme, deren Zeiten die Verzögerungen entsprechen:

    -   Thread 3872 des Prozesses TestBootStrapper.exe (3024) wird für 2.1 zweite belegt.

    -   Thread 3872 des Prozesses TestBootStrapper.exe (3024) entzieht 187 Millisekunden.

    -   Thread 3872 des Prozesses TestBootStrapper.exe (3024) Sekunde der CPU-Zeit verwendet.

8.  Um anderen Probleme beitragen, Anzeigen des Ereignisses, für welche Thread 3872 wartete. Erweitern Sie **ReadyThreadStack** zum Anzeigen von Personen, die an die 1,3 Sekunden Wartezeit, wie in Abbildung 34 Mitwirkende Wartezeit dargestellt:

    ![Abbildung 34 Beiträge zu Wartezeit](images/dep-win8-cpu-techniques-figure-34-contributors-to-wait-time.png)

    **Abbildung 34 Beiträge zu Wartezeit**

    **KiRetireDpcList** ist in der Regel I/O-bezogene und **KiTimerExpiration** eines Zeitgebers ist. Sie können anzeigen, wie die e/as und den Timerdienst initiiert wurden durch Entfernen der **ReadyThreadStack** , und klicken Sie dann die **NewThreadStack**anzeigen. In dieser Ansicht werden drei verwandte Funktionen, wie in Abbildung 35 e/as und den Timerdienst auf NewThreadStack dargestellt:

    ![Abbildung 35 IOS- und Timer auf newthreadstack](images/dep-win8-cpu-techniques-figure-35-ios-and-timer-on-newthreadstack.png)

    **In Abbildung 35 e/as und den Timerdienst auf NewThreadStack**

    Diese Ansicht gibt die folgenden Details:

    -   Thread 3872 des Prozesses TestBootStrapper.exe (3024) leert eine Registrierungsstruktur 544 Millisekunden.

    -   Thread 3872 des Prozesses TestBootStrapper.exe (3024) ausgesetzt 513 Millisekunden.

    -   Thread 3872 des Prozesses, TestBootStrapper.exe 3,5 MB auf den Datenträger geschrieben und verursacht dadurch eine Verzögerung 178 Millisekunden, an.

9.  Wenn Sie den kritischen Weg untersuchen gestartet, Sie analysiert die wichtigste Ursache warten in Explorer.exe und ignoriert alle Teile des kritischen Pfades, der aufgetreten ist, nachdem Ursache warten. Um diese zuvor disregarded Abschnitt des kritischen Pfades zu erfassen, müssen Sie der Zeitachse betrachten. **CPU-Auslastung (Precise)** hinzufügen und die **Zeitachse von Prozess Thread** Voreinstellung anwenden.

10. Filter so, dass nur die Prozesse, die als Teil des kritischen Pfades identifiziert. Das resultierende Diagramm wird in Abbildung 36 kritischen Pfad Zeitachse gezeigt:

    ![Abbildung 36 kritischen Weg Zeitachse](images/dep-win8-cpu-techniques-figure-36-critical-path-timelinee.png)

    **Abbildung 36 Critical Path Zeitachse**

    Abbildung 36 kritischen Pfad Zeitachse zeigt, dass Explorer.exe mehr Arbeit ausgeführt, nachdem er warten RunOnce.exe beendet wurde. Zoom auf den Zeitraum an, nachdem die zuvor analysiert Kette warten und einem anderen Analysen durchführen. Analyse wird in diesem Fall eine große Anzahl von Threads ein, die an Explorer.exe und keine durch den kritischen Weg klar verfolgen. In diesem Fall ist eine zusätzliche Analyse wahrscheinlich nicht bearbeitungsfähige Insights ergeben.

### <a name="direct-cpu-usage"></a>Direkte CPU-Auslastung

Aktivitäten sind häufig verzögert, da ein Thread auf dem kritischen Pfad viel CPU-Zeit verwendet. Mithilfe des Thread-Zustand-Objektmodells, sehen Sie sich, dass dieses Problem von einem Thread auf dem kritischen Pfad gekennzeichnet ist, die eine außergewöhnliche Zeitspanne im Zustand "aktiv" verbringt. Auf einige Hardware kann diese bei hoher CPU-Auslastung zu Verzögerungen beitragen.

### <a name="problem-identification"></a>Identifizierung des Problems

Viele Bewertung verwenden Heuristik zum direkten CPU-Auslastung Probleme im Zusammenhang mit zu identifizieren. Bedeutende CPU-Auslastung auf dem kritischen Pfad ist ein Problem in der folgenden Form gemeldet:

CPU verwendet, indem Prozess *P* Verzögerungen betroffene Aktivität *A* für *X* Sekunden

Dabei *P* der Prozess, der ausgeführt wird, *eine* Aktivität, und *x* ist die Zeit in Sekunden.

Wenn diese Probleme für eine Aktivität, die Verzögerungen entstehen gemeldet werden, Ursachen direkte CPU-Auslastung haben.

**Untersuchen Sie direkte CPU-Auslastung**

1.  Sie können manuell Identifizieren des Problems Schlüsseltokens für einzelne CPUs, die ein 100 entstehen % CPU-Auslastung der **CPU-Auslastung (abgetastete)** -Diagramm.

2.  Zoom auf einen Bereich von Interesse im Diagramm, und wählen Sie die Voreinstellung für die **Nutzung von Prozessen und Threads** .

    Standardmäßig zeigt die Tabelle Zeilen im oberen Bereich, der die höchste aggregierte CPU-Auslastung auf. Diese Threads auch am oberen Rand der **CPU-Auslastung (abgetastete)** Diagramm angezeigt.

    **Hinweis**  
    Auf einem System mit mehreren Prozessoren, wird ein Thread, der 100 % eines einzelnen Prozessors verwendet zum Verarbeiten von 100 werden angezeigt / (Anzahl der logischen Prozessoren). Auf dieser Art von System, kann nur der virtuelle Leerlauf-Thread (PID 0, TID 0) eine größere Prozessorverwendung als 100 anzeigen / (Anzahl der logischen Prozessoren). Wenn die Prozesse und Threads, die die meisten CPU nutzen alle Threads im kritischen Pfad entsprechen, stellen wahrscheinlich direkte CPU-Auslastung einen Faktor.

     

**Beispiel für Problem Assessment-Reported direkte CPU-Auslastung**

CPU verwenden, indem die TestUM.exe-Prozess (4024) Verzögerungen betroffene Aktivität, Fast zum Starten des Herunterfahrens TestIM.exe, 2.1 Sekunden. In diesem Beispiel wird in Abbildung 37 Thread 3208 gezeigt:

![Abbildung 37 Thread 3208](images/dep-win8-cpu-techniques-figure-37-thread-3208.png)

**Abbildung 37 Thread 3208**

### <a name="investigation"></a>Untersuchung

Nachdem Sie feststellen, dass die direkte CPU-Auslastung auf eine Verzögerung auf dem kritischen Pfad beiträgt, müssen Sie festlegen, die bestimmten Modulen und Funktionen, die auf die Verzögerung beitragen.

**Verfahren: Überprüfen eines Problems Assessment gemeldete direkte CPU-Auslastung**

Sie können ein Assessment gemeldete direkte CPU-Auslastung Problem um den kritischen Weg anzuzeigen, der durch die direkte CPU-Auslastung beeinflusst wird erweitern. Wenn Sie den Knoten zu, der der CPU-Auslastung zugeordnet ist erweitern, zeigt die Stapel aus, die der CPU-Auslastung und die zugeordnete Module zugeordnet sind. Diese Ansicht ist in Abbildung 38 erweitert CPU-Auslastung Segment dargestellt:

![Abbildung 38 erweitert Segment der cpu-Auslastung](images/dep-win8-cpu-techniques-figure-38-expanded-cpu-usage-segment.png)

**In Abbildung 38 erweitert Segment CPU-Auslastung**

**Vorgehensweise: Erkunden Sie manuell die Stapel eines Problems direkte CPU-Auslastung**

Wenn die Bewertung kein Problem gemeldet oder wenn Sie zusätzliche Überprüfung benötigen, können Sie das Diagramm **CPU-Auslastung (abgetastete)** verwenden, das Erfassen von Informationen manuell auf die Module und Funktionen, die ein CPU-Auslastung Problem beteiligt sind. Dazu müssen Sie auf den gewünschten Bereich Zoomen und zeigen Sie die Stapel, die nach der CPU-Auslastung sortiert werden.

**Erkunden Sie manuell ein Problem direkte CPU-Auslastung der Stapel**

1.  Klicken Sie auf das Menü Trace Symbole laden.

2.  Zoom der Zeitachse, um nur den Teil des kritischen Pfades anzuzeigen, die von der CPU-Problem betroffen ist.

3.  Die **Auslastung durch den Prozess und Thread** Voreinstellung anwenden.

4.  Die Anzeige die **Stack** Spalte hinzugefügt, und ziehen Sie diese Spalte rechts neben der **Thread-ID** (der Leiste links).

5.  Erweitern Sie den Prozess und Thread Stack-Strukturen angezeigt.

    Die Zeilen im Stapel sind nach **% Gewichtung der CPU-Auslastung**in absteigender Reihenfolge sortiert. Dadurch wird die interessantesten Stapel im Vordergrund. Wie Sie den auffalten, folgen Sie der Spalte **% Gewicht** , um sicherzustellen, dass sich der Fokus auf die Zeilen bleibt, denen die höchste Nutzung.

6.  Um eine Kopie des Stapels extrahieren möchten, wählen Sie alle Zeilen, mit der rechten Maustaste, und klicken Sie auf **Auswahl kopieren**.

### <a name="resolution"></a>Lösung

Sie können auf die Konfigurationsdatenbank und die Komponentenebenen aufzulösende hohen CPU-Auslastung Rechtsmittel anwenden.

Direkte CPU-Auslastung wirkt höher auf Computern, die Low-End-Prozessoren verfügen. In diesen Fällen können Sie weitere Leistung auf dem Computer hinzufügen. Oder Sie möglicherweise das Problem Module aus dem kritischen Pfad oder aus dem System zu entfernen. Wenn Sie die Komponenten ändern können, sollten Sie einen Neuentwurf Aufwand um eines der folgenden Ergebnisse zu erzielen:

-   Entfernen Sie den CPU-intensiver Code aus dem kritischen Pfad

-   Weitere CPU-effiziente Algorithmen verwenden

-   Zurückgestellt oder cache Arbeit

### <a name="thread-interference"></a>Thread Störungen

CPU-Auslastung von Threads, die nicht auf dem kritischen Pfad sind (und das sind möglicherweise nicht im Zusammenhang mit der Aktivität), können dazu führen, dass Threads, die auf dem kritischen Pfad verzögern sind. Thread Zustandsmodell zeigt, dass dieses Problem durch Threads auf dem kritischen Pfad gekennzeichnet ist, das eine ungewöhnliche Zeitspanne im Zustand bereit verbringen.

### <a name="problem-identification"></a>Identifizierung des Problems

Viele Bewertung verwenden Heuristik um Störungen-Probleme zu identifizieren. In einem der folgenden beiden Formate Sie werden gemeldet:

-   Process *P* Sicherstellung ist. Das Blockieren von verursacht eine Verzögerung auf die Aktivität betroffener *eine* *X* -ms.

-   Process *P* wird belegt. Die Unterbrechung verursacht eine Verzögerung auf die Aktivität betroffener *eine* *X* -ms.

Dabei *P* den Prozess *eine* Aktivität, und *x* ist die Zeit in Millisekunden.

Das erste Formular widerspiegelt Interferenzen Threads auf derselben Prioritätsebene wie die Thread auf dem kritischen Pfad. Die zweite Form widerspiegelt Interferenzen Threads, die sich auf einer höheren Priorität als Threads auf dem kritischen Pfad befinden.

Wenn diese Art von Problemen für eine verzögerte Aktivität gemeldet werden, kann Störungen Thread die Ursache sein. Das Diagramm **CPU-Auslastung (Precise)** können Sie um manuell das Problem zu identifizieren.

**Identifizieren von Thread Störungen Probleme**

1.  Vergrößern Sie des Intervalls, und anwenden Sie die **Nutzung von CPU** -Voreinstellung. Eine Auslastung von 100 % bei allen CPUs gibt ein Problem Störungen an.

2.  Anwenden der **Nutzung von Prozess, Thread** Voreinstellung und Sortieren nach der ersten Spalte **(us) bereit** . (Dies ist die Spalte, die die **Summe** Aggregation enthält).

3.  Erweitern Sie den Prozess der Aktivität, die betroffen ist, und suchen Sie auf dem kritischen Pfad zur Zeit für Threads bereit. Dieser Wert ist die maximale Zeitdauer, die die Verzögerung von jedem Thread Störungen Problem beheben reduziert werden kann. Ein Wert mit einer Stärke relativ zur die Verzögerung untersuchten erhebliche gibt an, dass ein Thread Störungen Problem vorhanden ist.

Abbildung 39-CPU-Auslastung beträgt 100 % und Abbildung 40 Thread Störungen Problem in diesem Szenario darstellen:

![Abbildung 39 cpu-Auslastung ist in der Nähe 100 %](images/dep-win8-cpu-techniques-figure-39-cpu-utilization-is-near-100.png)

**Abbildung 39-CPU-Auslastung beträgt 100 % in Ihrer Nähe.**

![Abbildung 40 Thread Störungen problem](images/dep-win8-cpu-techniques-figure-40-thread-interference-problem.png)

**Abbildung 40 Thread Störungen Problem**

### <a name="investigation"></a>Untersuchung

Nachdem das Problem identifiziert wurde, müssen Sie ermitteln, warum der betroffene Thread so viel im Zustand bereit Zeitaufwand.

**Vorgehensweise: Bestimmen Sie, warum ein Thread den Status kann jetzt Zeitaufwand für das**

Das Diagramm **CPU-Auslastung (Precise)** können Sie ermitteln, warum ein Thread im Zustand bereit Zeitaufwand. Sie müssen zunächst ermitteln, ob der Thread auf bestimmte Prozessoren beschränkt ist. Obwohl Sie direkt diese Informationen zu erhalten, können Sie den Verlauf der CPU-Auslastung eines Threads Zeiten mit hoher CPU-Auslastung untersuchen. Dies ist der Zeitraum, wenn Threads häufig wechseln zwischen Prozessoren im Allgemeinen.

**Bestimmen des Threads Prozessor Einschränkungen**

1.  Um die betroffenen Region vergrößern.

2.  Das **CPU-Auslastung (Precise)** Diagramm hinzufügen und die **Auslastung durch den Prozess, Thread** Voreinstellung anwenden.

3.  Verwenden Sie im Dialogfeld **Erweitert** , um eine **Cpu** -Spalte hinzuzufügen, die einen **Eindeutige Count** Aggregation Modus rechts neben der **NewThreadId**wurde.

4.  Filtert das Diagramm, um nur die Threads anzeigen, an denen Sie interessiert sind.

    Der Wert in der Spalte **Cpu** zeigt die Anzahl der Prozessoren auf denen der Thread während des aktuellen Zeitraums ausgeführt wurde. In Zeiten mit 100 % CPU-Auslastung ist ein Näherungswert diese Nummer die Anzahl der Prozessoren auf denen dieser Thread ausgeführt werden dürfen. Wenn der Wert kleiner als die Anzahl der Prozessoren verfügbar ist, ist der Thread wahrscheinlich auf bestimmte CPUs beschränkt.

    Abbildung 41 eingeschränkte Threads bietet ein Beispiel für dieses Diagramm:

    ![Abbildung 41 eingeschränkt threads](images/dep-win8-cpu-techniques-figure-41-restricted-threads.png)

    **Abbildung 41 eingeschränkt Threads**

Nachdem Sie ein Thread Prozessor Einschränkungen kennen, können Sie ermitteln, was unterbrochen oder Sicherstellung den Thread. Zu diesem Zweck müssen Sie die Intervalle Threads im Zustand bereit für identifizieren und überprüfen anschließend, welche anderen Threads oder Prozessen während diesen Intervallen ausgeführt wurden.

**Bestimmen Sie, was unterbrochen oder Sicherstellung den Thread**

1.  Erstellen Sie ein Diagramm, das zeigt, wenn der Thread im Zustand bereit war und anwenden Sie die **Nutzung von Prozess, Thread** Voreinstellung.

2.  Öffnen Sie die **Ansicht-Editor**zu, klicken Sie auf **Erweitert**, und wählen Sie auf die Registerkarte **Diagramm-Konfiguration** .

3.  **Startzeit** zu **ReadyTime (s)** und die **Dauer** auf festgelegt **(us) bereit**, wie in Abbildung 42 bereit Zeitspalten dargestellt. Klicken Sie auf **OK**.

    ![Abbildung 42 bereit Spalten](images/dep-win8-cpu-techniques-figure-42-ready-time-columns.png)

    **Abbildung 42 bereit Zeitspalten**

4.  Ersetzen Sie in der **Ansicht des Editors**die Spalte **CPU-Auslastung (%)** mit der **bereit (us) \[Summe\] ** Spalte.

5.  Wählen Sie in des Threads von Interesse ist, um ein Diagramm erstellt, die in Abbildung 43 bereit Zeit Diagramm ähnlich ist:

    ![Abbildung 43 bereit Zeit Diagramm](images/dep-win8-cpu-techniques-figure-43-ready-time-graph.png)

    **Abbildung 43 bereit Zeit Diagramm**

6.  In diesem Fall aufgewendeten Threads viel Zeit im Zustand bereit. Um die normale Priorität zu ermitteln, fügen Sie eine **durchschnittliche** Aggregation der **NewInPri** Spalte hinzu.

    In diesem Fall wird die Priorität des Threads durchschnittliche genau 8. Diese Nummer gibt an, dass es wahrscheinlich einen Hintergrundthread handelt, der nie Priorität geschieht empfängt.

7.  Nachdem die durchschnittliche Priorität bekannt ist, sehen Sie sich die CPU-Aktivität für die CPUs auf dem der Thread ausgeführt werden dürfen.

    In diesem Fall wurde der Thread bestimmt, damit nur Affinität für CPU 1.

8.  Eine andere **CPU-Auslastung (Precise)** Diagramm hinzufügen und die **Nutzung von CPU** -Voreinstellung anwenden. Wählen Sie die relevante CPUs aus.

9.  Öffnen Sie die Ansicht **Erweitert** , und fügen Sie einen Filter für die Priorität, die Sie zuvor zum Herausfiltern von diesem Thread gefunden. In diesem Szenario wird in Abbildung 44 Thread Filter angezeigt:

    ![Abbildung 44 Thread-filter](images/dep-win8-cpu-techniques-figure-44-thread-filter.png)

    **Abbildung 44 Thread-Filter**

    In Abbildung 45 CPU-Auslastung, Zeit bereit und andere Thread-Aktivität wird im oberste Diagramm die CPU-Auslastung des Threads 3548 an. Im mittlere Diagramm zeigt die Zeit, dass der Thread bereit wurde, und im unteren Diagramm zeigt die Aktivität auf die CPUs auf dem der Thread darf (in diesem Fall CPU 1) ausgeführt wurde.

    ![Abbildung 45 bereit Zeitpunkt der CPU-Verwendung und anderen Thread ac](images/dep-win8-cpu-techniques-figure-45-cpu-usage-ready-time-and-other-thread-activity.png)

    **Abbildung 45 CPU-Auslastung, Zeit bereit und andere Threadaktivität**

10. Zoom in einen Bereich, in dem der Thread wurde bereit und wurde nicht ausgeführt, für die meiste Zeit innerhalb dieses Intervalls.

11. In der **CPU-Auslastung** der linken Seite des Balkens **NewInPri** hinzu, und prüfen Sie die Ergebnisse.

    Threads oder Prozesse, die Prioritäten verfügen, die Zeitspanne zeigen Ziel Thread Priority gleich sind, dass der Thread Sicherstellung wurde. Threads oder Prozesse, die einer höheren Priorität als Zeitspanne zeigen Ziel Thread Priorität haben, dass der Thread unterbrochen wurde. Sie können die gesamte Zeit berechnen, die der Thread unterbrochen wurde durch die Zeiten aller Threads unterbrechen und Aktionen hinzufügen.

    Verwendung der Abbildung 46 nach Priorität bei der Ziel-Thread wurde bereit dargestellt, die 730ms der Threadzeit unterbrochen wurden und der Threadzeit an 300ms Sicherstellung wurden. (In dieser Abbildung wird vergrößert, um eine 1192ms Intervall.)

    ![Abbildung: 46 Einsatz nach Priorität, wenn Ziel-Thread wurde](images/dep-win8-cpu-techniques-figure-46-usage-by-priority-when-target-thread-was-ready.png)

    **Verwendung der Abbildung 46 nach Priorität beim Ziel Thread wurde bereit**

12. Um zu bestimmen, welche Threads für die Unterbrechung und Blockieren der von diesem Thread verantwortlich sind, fügen Sie die **NewProcess** Spalte rechts neben der Spalte **NewInPri** , und überprüfen Sie die Prioritätsebenen, Prozesse ausgeführt wurden. In diesem Fall wurden die Unterbrechung und blockieren hauptsächlich von einem anderen Thread in demselben Prozess und durch TestResidentApp.exe verursacht. Sie können davon ausgehen, dass diese Prozesse regelmäßigen Priorität geschieht über ihre Basis Priorität erhalten.

### <a name="resolution"></a>Lösung

Sie können die Unterbrechung oder Blockieren von Probleme beheben, durch die Konfiguration oder Komponenten ändern. Berücksichtigen Sie Folgendes:

-   Entfernen Sie die problematischen Prozesse aus dem System.

-   Passen Sie die base Priorität der problematischen Prozesse...

-   Ändern Sie die Zeit, die beim Ausführen der problematischen Prozesse. beispielsweise Verzögerung Startzeit auftreten, wenn es sich bei einem Neustart des Computers.

-   Wenn die Problem Komponenten geändert werden können, Umgestalten werden, dass weniger CPU-intensiver oder an eine niedrigere Priorität auszuführen.

### <a name="dpcisr-interference"></a>DPC/ISR Störungen

Wenn viel Prozessorzeit genutzt wird, indem Sie DPCs und ISRs ausführen, gibt es möglicherweise nicht werden ausreichend verfügbare CPU-Zeit links, um Threads ausgeführt werden. Dies kann ähnlich wie Verzögerungen für Thread Störungen verursachen. Wenn Threads Vorgänge mit einem regulären häufig auftretenden Rate durchführen müssen, kann wie unter Animation oder Videowiedergabe Interferenzen durch DPCs und ISRs betriebsbereite Problemen führen.

### <a name="problem-identification"></a>Identifizierung des Problems

Viele Bewertung verwenden Heuristik DPC/ISR-bezogene Probleme zu erkennen. DPC/ISR-Aktivität wird als verdächtigen identifiziert, wenn er als ein Problem in der folgenden Form gemeldet wird:

DPC *D* überschreitet den Schwellenwert des *m* Millisekunden *X* Zeiten während *P*. Die *n* Instanzen von diesem DPC führen Sie für insgesamt *t* Millisekunden.

*D* ist wird die DPC, *m* ist die Anzahl der Millisekunden, die den Schwellenwert für die festlegt, *x* ist die Anzahl der Male, dass die DPC *P* den Schwellenwert überschritten wird der aktuelle Prozess, *n* ist die Anzahl der Instanzen, die die DPC ausgeführt wurde und *t* ist die Zeit in Millisekunden an, denen über den Schwellenwert für die DPC ausgeführt wurde.

Das folgende Problem wird beispielsweise durch eine Bewertung gemeldet:

**DPC sdbus.sys! SdbusWorkerDpc überschreitet das Ziel der 3.0 Millisekunden 153 Zeiten während der Lebensdauer von Medien-Modul. Führen Sie die 153 Instanzen von diesem DPC für insgesamt 864 Millisekunden**

Wenn dieses Problem für eine Aktivität, das Problem Ereignissen oder Verzögerungen aufweist gemeldet wird, Ursachen DPC/ISR Aktivität haben.

**Manuell identifizieren Sie DPC/ISR Störungen**

1.  Um DPC/ISR Störungen zu ermitteln, öffnen Sie eine Verfolgung in WPA und identifizieren Sie relevante Ereignisse Problem zu. Dies sind Assessment-spezifische generische Ereignisse wie **Microsoft-Windows-Dwm-Core: ZEITPLAN\_STÖRUNG** oder **Microsoft-Windows-MediaEngine:DroppedFrame**.

2.  Neben dem Diagramm der Ereignisse fügen Sie das **Für die Dauer nach CPU DPC/ISR** -Diagramm hinzu. Wenn Spitzen **DPC/ISR Dauer von CPU** mit den Ereignissen Problem Zeile von Diagramm, möglicherweise DPC/ISRs ein Faktor für die Probleme verursacht.

3.  Vergrößern Sie für zusätzliche Daten enthält die den Zeitraum an, der auftritt, 100 ms, bevor mehrere Problem Ereignisse anzeigen. Wenn erhebliche DPC/ISR Aktivität auf einen oder mehrere Prozessoren in dem Bereich 100 ms, zeigt bevor die Ereignisse Problem aufgetreten ist, können Sie davon ausgehen, dass die Ereignisse Problem durch die Aktivität DPC/IRS verursacht wurden.

4.  Um festzustellen, ob Verzögerungen DPC/ISR Störungen verursacht, zoom einen Bereich, die einen laufenden Thread anzeigt. Notieren Sie die CPU oder CPUs auf dem dieser Thread ausgeführt wird.

5.  Im Diagramm DPC/ISR gelten die Voreinstellung **DPC/ISR Dauer von CPU** und Anzeigen der DPC/ISR-Aktivitätsfeeds auf die relevante CPUs in diesem Zeitraum.

Abbildung 47 Problem Ereignisse und DPC/ISR Aktivität zeigt, Thread 864 von iexplore.exe für die betroffenen Aktivität relevant ist. Thread 864 befindet sich in der Ansicht im Zustand "aktiv" auf CPU2 10.65 % des Zeitraums. DPC/ISR die Abbildung zeigt jedoch, dass CPU2 DPC/ISRs 10 % dieser Zeit beschäftigt war.

**Hinweis**  
Die meisten DPC/ISRs nicht so hoch wie im folgenden Beispiel dargestellt auswirken.

 

![Abbildung 47 Problem Ereignisse und Dpc Isr Aktivität](images/dep-win8-cpu-techniques-figure-47-problem-events-and-dpc-isr-activity.png)

**Abbildung Ereignisse bei Problemen mit 47 und DPC/ISR-Aktivität**

In Abbildung 48 DPC/ISR unabhängige Problem Ereignisse sind DPC/ISRs nicht in Verbindung mit zu Leistungsproblemen aufgeführt:

![Abbildung 48 Dpc Isr unabhängige Ereignisse bei Problemen](images/dep-win8-cpu-techniques-figure-48-dpc-isr-unrelated-to-problem-events.png)

**Abbildung 48 DPC/ISR unabhängige Ereignisse bei Problemen**

In Abbildung 49 Verzögerung von DPC/ISR Störungen verursacht werden DPC/ISRs dargestellt, um die Leistung beeinträchtigen:

![Abbildung 49 Verzögerung durch Dpc Isr Störungen](images/dep-win8-cpu-techniques-figure-49-delay-caused-by-dpc-isr-interference.png)

**Abbildung 49 Verzögerung aufgrund von Interferenzen DPC/ISR**

### <a name="investigation"></a>Untersuchung

Nachdem Sie feststellen, dass DPCs/ISRs im Zusammenhang mit Probleme oder Verzögerungen, müssen Sie bestimmen, welche bestimmte DPCs/ISRs beteiligt sind und warum sie häufig anfallen oder der für eine übermäßige Zeitspanne ausführen.

**Vorgehensweise: Überprüfen Sie ein Assessment gemeldete DPC/ISR Problem**

In Assessment DPC/ISR Behebung von Problemen können Sie das Problem erweitern, in dem die wichtigsten Prozesse angezeigt, die mit der DPC oder ISR. belegt werden Erweitern Sie den Stapel zum Anzeigen der DPC-Aktivitätsfeeds für den Prozess, der meisten ist im Zusammenhang mit der betroffenen Aktivität, siehe, erweitern Sie den Stapel, um zu verstehen, was die DPC unternommen hat. Abbildung 50 erweitert DPC Stapel zeigt den erweiterten Stapel:

![Abbildung 50 erweiterten Dpc stack](images/dep-win8-cpu-techniques-figure-50-expanded-dpc-stack.png)

**Abbildung 50 erweitert DPC Stack**

**Vorgehensweise: Suchen Sie nach der höchsten Dauer DPCs/ISRs und überprüfen Sie die Stapel**

Wenn Sie eine Bewertung DPC/ISR ein Problem werden keine meldet, können Sie die Diagrammen **DPC/ISR** und **CPU-Auslastung (abgetastete)** zum Abrufen von Informationen für die zutreffenden DPCs Stack verwenden. Es wird empfohlen, dass Sie eine DPC/ISR von Interesse finden, notieren Sie den Modul und Funktion und Sie dann die Beispielen im Diagramm **CPU-Auslastung (abgetastete)** zum Abrufen von Informationen mit vollständigen Stapel suchen.

**Suchen Sie nach der höchsten Dauer DPCs/ISRs, und überprüfen Sie die Stapeln**

1.  Für das Intervall von Interesse vergrößern.

2.  Wählen Sie im Diagramm DPC/ISR die voreingestellte **DPC/ISR für die Dauer nach Modul Funktion**.

    Wenn Symbole geladen sind, DPC/ISR Ereignisse nach Gesamtdauer sortiert sind, und Sie werden dann aufgeschlüsselt nach Modul und -Funktion. Die obersten Zeilen in der Liste enthalten die DPC/ISR-Ereignisse, die das Ereignis Probleme wahrscheinlich verursacht. Notieren Sie die Namen der Module und -Funktion.

3.  Wählen Sie im Diagramm **CPU-Auslastung (abgetastete)** die **Nutzung von Prozess** Voreinstellung. Standardmäßig werden diese Voreinstellung DPC/ISR Aktivität ausgeblendet.

4.  Öffnen Sie den **Editor anzeigen**, und klicken Sie auf **Erweitert**.

5.  Klicken Sie auf der Registerkarte **Filter** Ändern der Einstellung **Ausblenden von Zeilen, die dem Filter entsprechen,** **Zeilen, die dem Filter entsprechen**. Dadurch DPC/ISR Aktivitäten angezeigt werden.

6.  Entfernen der Spalte **Prozess** und fügen die **Stack** Spalte anzuzeigende DPCs/ISRs Stack sortiert.

7.  Löschen Sie die aktuelle Zeilenauswahl.

8.  Maustaste auf eine Zelle in der Spalte **Stack** , und klicken Sie dann auf **Suchen, die in dieser Spalte**.

9.  Geben Sie in Schritt2 dieses Verfahrens ein Modul und die Funktion, die Sie notiert haben.

10. Überprüfen Sie **zur aktuellen Auswahl hinzufügen**, und klicken Sie auf **Alle suchen,** um alle Instanzen der Funktion auszuwählen.

11. Nachdem alle Zeilen markiert sind, Maustaste klicken und **Aufgerufene Schmetterling/anzeigen**.

In dieser Ansicht werden die Aktivitäten dieser bestimmten Funktion, sortiert nach Gesamtdauer. Die Ansicht ähnelt eine Stapel Darstellung in der Detailansicht eines Problems Assessment gemeldet. Die **Weight** -Spalte ist ein Näherungswert die inklusive Zeit für jede Funktion im Stapel, in Millisekunden ist.

Diese Ansicht wird in Abbildung 51 aufgerufenen eine DPC sortiert nach der Ungefähre Dauer dargestellt:

![Abbildung 51 aufgerufenen für eine Dpc sortiert nach ungefähren d](images/dep-win8-cpu-techniques-figure-51-callees-of-a-dpc-sorted-by-approximate-duration.png)

**Abbildung 51 aufgerufenen für eine DPC sortiert nach Ungefähre Dauer**

**Vorgehensweise: Überprüfen Sie langer DPCs/ISRs**

Die gesamte Dauer des DPCs/ISRs ist wichtig, jedoch langer einzelne DPCs/ISRs eher verlangsamen. Im Diagramm DPC/ISR zeigt die Spalte **Inklusive Dauer (in Millisekunden)** , in absteigender Reihenfolge sortiert die maximale Dauer eines einzelnen DPC/ISRs. In einigen Assessment Profilen verfügbar ist vorgegebenen **Langen DPCs/ISRs** können Sie die Filtern in dieser Ansicht um DPCs/ISRs anzuzeigen, eine inklusive Dauer aufweisen, die größer als 1 ms ist.

**Hinweis**  
Wenn diese Voreinstellung nicht verfügbar ist, können Sie die **Ansicht des Editors**, Abschnitt **Erweitert** , um einen Filter hinzuzufügen öffnen.

 

### <a name="resolution"></a>Lösung

DPC/ISR Aktivität widerspiegelt häufig ein Hardware- oder Problem, das auf der Hardware oder Komponente behoben werden muss. Auf einer Konfigurationsebene können Sie ersetzen Sie die Hardware oder den zugehörigen Treiber auf eine feste Version aktualisieren. Auf einer Komponentenebene Hardware und Treiber sollten folgen bewährte Methoden für DPCs/ISRs aus MSDN, und sollten nach Möglichkeit Thread DPCs verwenden. Threading DPCs nicht auf der Ebene der Versendung auf Clienteditionen von Windows ausgeführt werden. Weitere Informationen zu bewährten Methoden für DPCs/ISRs finden Sie unter Richtlinien auf ISR und DPC Verhalten und Threading DPCs Einführung in.

## <a name="related-topics"></a>Verwandte Themen


[Einführung in die verkettete DPCs](http://go.microsoft.com/fwlink/?LinkId=254752)

[ISRs und DPCs der automatischen Killers](http://go.microsoft.com/fwlink/?LinkId=254751)

[Laden von Symbolen](loading-symbols.md)

[Power Management und ACPI - Architektur und Treiber](http://go.microsoft.com/fwlink/?LinkId=263460)

[Ppm-Lösung in Windows Vista und WindowsServer 2008](http://go.microsoft.com/fwlink/?LinkId=254745)

[Planen von Prioritäten](http://go.microsoft.com/fwlink/?LinkId=254748)

[Planung, Threadkontext und IRQL](http://go.microsoft.com/fwlink/?LinkId=254750)

[Windows gehenden, sechsten Edition](https://www.microsoft.com/learning/book.aspx?ID=12069)

[Windows Performance Analyzer](windows-performance-analyzer.md)

[Windows Performance Toolkit technische Referenz](windows-performance-toolkit-technical-reference.md)

 

 







