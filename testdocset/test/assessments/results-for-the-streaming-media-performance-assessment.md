---
title: "Ergebnisse für die Streaming Media-Performance-Bewertung"
description: "Ergebnisse für den Streaming Media-Performance-Bewertung"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 238eba8e-fe97-4422-be7a-88e4e232de8a
ms.prod: W10
ms.mktglfcycl: plan
ms.sitesec: msdn
ms.openlocfilehash: f421fe7cece1fc2f86d13579cccaddd70b9dc3fb
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="results-for-the-streaming-media-performance-assessment"></a>Ergebnisse für die Streaming Media-Performance-Bewertung


Die Leistung für Streaming Media-Bewertung hilft Ihnen bewerten und ein Computer, streaming Media-Leistung verbessern. Diese Bewertung verwendet eine streaming Serveranwendung, die bereitgestellt wird, auf einem lokalen Computer oder auf einem Remoteserver. Die Bewertung startet Internet Explorer® 10 und gibt wieder dem Media-Inhalten von Anfang bis Ende oder zu einem angegebenen Zeitpunkt. Klicken Sie dann, Internet Explorer wird geschlossen, und Ergebnisse werden generiert.

Dieses Thema enthält Anleitungen zum Verständnis der Ergebnisse von Streaming Media-Performance-Bewertung zusätzlich zu Anweisungen zur Verwendung dieser Ergebnisse identifizieren und beheben häufig auftretender Probleme, die sich negativ auf die streaming Media-Erfahrung auswirken. Obwohl Internet Explorer als streaming-Client in der Analyse verwendet wird, können die Verfahren in diesem Thema behandelten zur Verbesserung der allgemeinen streaming Media-Erfahrung von Windows angewendet werden.

In diesem Thema:

-   [Ziele-Datei](#bkmk-goals)

-   [Metriken](#bkmk-metrics)

-   [Probleme](#bkmk-streamingissues)

Weitere Informationen über diese Bewertung, Systemanforderungen und Bewertung Einstellungen finden Sie unter [Streaming Media-Leistung](streaming-media-performance.md).

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

 

## <a name="a-href-idbkmk-metricsametrics"></a><a href="" id="bkmk-metrics"></a>Metriken


Das Streaming Media Performance Assessment meldet Audio- und Videodaten Störung Metriken. Anstatt direkt unterstellt die Anzahl der video-Fehler aufgetreten ist, werden Probleme basierend auf human Wahrnehmung klassifiziert. Die meisten Personen starten, video und audio wird Wesen-synchronisierte im Bereich von 80ms zu 160ms. Die Anzahl der aufeinander folgenden Frames, die Fehler in einem 30 f/s video können, bevor es wahrgenommen werden kann, innerhalb dieses Zeitraums wird berechnet. Basierend auf der Anzahl der aufeinander folgenden Frames, die Fehler aufweisen, video Probleme werden klassifiziert als Hauptversion, Mittel oder Nebenversion Probleme wie folgt:

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Anzahl der aufeinander folgenden Rahmen mit Fehler</th>
<th>Störung Klassifikation</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>1</p></td>
<td><p>Minor Störung</p></td>
</tr>
<tr class="even">
<td><p>2 bis 4</p></td>
<td><p>Mittlere Störung</p></td>
</tr>
<tr class="odd">
<td><p>&gt;= 5</p></td>
<td><p>Haupt-Störung</p></td>
</tr>
</tbody>
</table>

 

Die Dauer von 60 Sekunden Wiedergabedauer der Arbeitslast Assessment kann in Intervallen von 1 Sekunde 60 unterteilt werden. Basierend auf den Typ der Probleme, die in ein Intervall aufgetreten sind, wird jedem Intervall als ein Intervall Haupt-, Mittel, minor oder Nein Störung klassifiziert. Beispielsweise ist ein Intervall von mittlere Störung in der mindestens eine mittlere Fehler aufgetreten ist, aber keine Haupt-Fehler festgestellt wurde. In ähnlicher Weise ist ein Intervall von Nebenversionen Störung in der mindestens eine kleinere Fehler aufgetreten ist, aber keine Probleme mittleren oder großen festgestellt wurden.

Standardmäßig wird dieses Assessment 3 Iterationen Arbeitslast ausgeführt. Das Video wird jedoch 5 Zeiten während 3 Iterationen wiedergegeben. Die erste Iteration ist Internet Explorer nicht initialisiert werden, und klicken Sie dann 3 video Playbacks für die Berechnung der Metriken vorhanden sind. Bewerten die Ergebnisse ist die letzte Iteration.

-   Die **Iteration Schulungen**. Dies ist die erste Iteration, um sicherzustellen, dass Internet Explorer-DLLS geladen werden.

-   **Timing Iterationen**. Diese Iterationen dienen als Grundlage für die metrischen Werte. Die metrischen Werte sind diese drei Iterationen durchschnittlich an. Generieren standardmäßig drei vollständige Iterationen von 60 Sekunden über streaming StreamingMediaAssessment.etl Trace-Dateien, die zur Berechnung der Metriken verwendet werden. Während dieser Iterationen ist nur oberflächliche Protokollierung zur Reduzierung des Verarbeitungsaufwands Instrumentation auf generierten Metriken aktiviert. Dementsprechend werden detaillierte Diagnosebericht Ereignisse in dieser Datei Trace nicht erfasst.

-   **Analyse Iteration**. Diese Iteration werden Informationen gesammelt, während das Assessment ausgeführt wird und als Grundlage für die Probleme, die durch die Bewertung generiert dient. Hierbei handelt es sich um eine vollständige Iteration über streaming 60 Sekunden. Während dieser Iteration wird die ausführliche Protokollierung aktiviert, um detaillierte Diagnoseinformationen zu erfassen. Die Ablaufverfolgungsdatei, die in dieser Iteration (StreamingMediaAssessmentDiagTrace.etl) generiert wird wird durch die Bewertung zum Erkennen von Medien-bezogene Probleme auf dem System analysiert.

Links zu den Tracedateien sind im Detailbereich in der Benutzeroberfläche verfügbar. Um die Werte für einzelne Iterationen, in der Ansicht Ergebnisse finden Sie unter Maustaste auf die Spaltenüberschrift Ergebnisse und wählen Sie dann auf **Iterationen anzeigen**.

## <a name="a-href-idbkmk-streamingissuesaissues"></a><a href="" id="bkmk-streamingissues"></a>Probleme


Diese Bewertung führt eine Problemanalyse der erweiterten und enthält Links zu Windows Performance Analyzer (WPA) von Problemen, die identifiziert werden. In den meisten Fällen können Sie den Link WPA detaillierte Analyse von Problemen, die angezeigt werden. Wenn WPA geöffnet wird, möglicherweise zusätzliche Details zum Datenträger oder CPU-Aktivität je nach Art des Problems identifiziert werden. Informationen zu Problemen eingehenderen Analysen und Empfehlungen finden Sie unter [Häufige Probleme der Depth-Analyse](common-in-depth-analysis-issues.md).

Wenn die Bewertung gestartet wird, überprüft es bestimmte vorläufige auf dem Computer, mit denen sichergestellt, dass konsistente Ergebnisse über verschiedene Verwendungsmöglichkeiten der Bewertung generiert werden können. Verschiedene Warnung kann in den Ergebnissen zur Bewertung angezeigt werden, wenn die Warnung nicht behandelt werden, bevor die Bewertung ausgeführt wird. Klicken Sie nach Abschluss der Streaming Media-Bewertung basierend auf der automatisierte Analyse der Diagnose Ablaufverfolgungsdatei, generiert die Bewertung Probleme bei Media Probleme im System identifiziert. Diese Probleme können in WPA analysiert werden. Zusätzlich zum Reagieren auf die generierten Probleme, kann zusätzliche manuelle Analyse erfolgen auf der Diagnose Ablaufverfolgungsdatei mithilfe von WPA und GPUView, ein Tool, das in der Windows Performance Toolkit enthalten ist.

Dieser Abschnitt enthält:

-   [Häufige Probleme](#bkmk-streamingproblems)

-   [Überprüfen Sie vor dem Warnungen](#bkmk-precheck)

-   [Analysieren von generierten Probleme](#bkmk-streaminganalyze)

-   [Korrelation von Probleme](#bkmk-streamingglitches)

-   [Software im Vergleich zu decodieren von Hardware](#bkmk-streamingsoftware)

-   [GPU hoher Auslastung](#bkmk-streaminggpu)

-   [Die Bewertung von Berichten Exit-Code 0x80050006](#exitcode)

### <a name="a-href-idbkmk-streamingproblemsacommon-problems"></a><a href="" id="bkmk-streamingproblems"></a>Häufige Probleme

Einige der wichtigsten Ursachen für audio-Fehler umfassen Folgendes:

-   **Langer unterbrechen Service Routinen (ISR) und zurückgestellt Verfahren Anrufe (DPC)**

    Eine ISR ist eine Gerätetreiberroutine, dass der Interruptverteiler überträgt die Steuerung, wenn ein Gerät einen Interrupt ausgegeben. Führen im Windows-e/a-Objektmodell ISRs bei einer hohen Geräte Interrupt Request Level (IRQL), so, dass sie so wenig Arbeit wie möglich zu vermeiden auf niedrigerer Ebene Interrupts unnötig ausführen. Eine ISR Warteschlangen in der Regel eine DPC, der mit einem niedrigeren IRQL, zum Ausführen der restlichen Interrupt Verarbeitung ausgeführt wird. DPCs sollten nicht mehr als 100 Mikrosekunden ausführen und ISRs sollten nicht länger als 25 Mikrosekunden ausführen. Zusätzlich zu anderen Systemleistung möglicherweise beeinflusst, langer ISRs und DPCs Verzögerungen in das audio-Modul, die audio-Fehler führen. Eine ISR oder für die Dauer, die größer als 1 ms auf 3 ms ausgeführt DPC kann Medien in einem System beeinträchtigen. Ähnlich wie in langer ISRs und DPCs, häufig verwendeten ISRs und DPCs (ein ISR/DPC Ansturm) kann ähnliche Effekte auf die Leistung haben. Solche ISR und DPC Probleme werden in der Regel im Netzwerk, Speicherung und Graphics-Treiber gefunden. Die Bewertung generiert eine Warnung für langer ISR/DPC zwischen 1 ms auf 3 ms und ein Fehler für größer als 3 ms dauern. Weitere Informationen finden Sie unter [Generiert Probleme analysieren](#bkmk-streaminganalyze).

-   **Kernel-Arbeitsthreads Versendung Ebene ausgeführt**

    Zusätzlich zur DPCs möglicherweise einige Kernel-Arbeitsthreads auch Versendung Ebene ausgeführt werden (IRQL = 2). Ebenso können diese auch verlangsamen, die audio-Fehler führen. Um solche Fälle zu erkennen, suchen Sie für niedrige Priorität System, ausführen ununterbrochenen für lange dauern threads ohne wird abgebrochen.

-   **Blockieren von Client-side**

    Dies ist, wenn die Quelle von Datenträger oder Netzwerk schnell genug Echtzeit decodieren und Rendering zu lesen kann. Beispiel des Datenträgers möglicherweise mithilfe eines harte Seitenfehlers verursachter werden und daher Beispiele können nicht vom Datenträger in eine schnellere gelesen werden als in Echtzeit gegenseitig.

Die oberen des video-Fehler folgende Ursachen haben:

1.  **Downstream-Engpass**: Blockieren der Quelle (Datenträger ist verursachter)

2.  **Mitten Engpass**: Decoder ist überlastet (Software oder Hardware Decoder ist verursachter)

3.  **Upstream-Engpass**: GPU ist Transfers angeschlossenen oder bei langsamen Memory

### <a name="a-href-idbkmk-precheckapre-check-warnings"></a><a href="" id="bkmk-precheck"></a>Überprüfen Sie vor dem Warnungen

Bevor Sie beginnen, die Bewertung (das Video streaming), wird das Streaming Media Performance Assessment einige Tests vor dem auf dem System ausgeführt. Wenn diese vor dem Prüfungen ausfallen, generiert die Bewertung Fehler und Warnungen. Während Fehler die Bewertung Ausführung zu blockieren, Warnungen werden nicht blockieren und zulassen die Bewertung, um den Vorgang fortzusetzen. Die folgenden: einige wichtigen vor Prüfungen, die Bewertungsergebnisse zu beeinflussen

-   **Stromversorgung ist erforderlich (Warnung)**

    Es wird empfohlen Auswirkungen auf die Bewertungsergebnisse zur der Streaming Media Performance-Bewertung auf einem Computer ausgeführt, der Stromversorgung, verwendet da einige Geräte, auf dem Computer abwärts skalieren können während der Ausführung auf Batterie;.

-   **Die Ausführung mit VGA ist Treiber nicht (Warnung) empfohlen**

    Fehlende Anzeige-Treibern wie Microsoft Standardanzeige-Treiber kann dazu führen, dass zusätzliche video-Fehler. Um genaue Ergebnisse zu erhalten, stellen Sie sicher, dass die richtigen Anzeigetreiber installiert sind, bevor Sie die Bewertung ausführen. Führen Sie für weitere Details zur Treibern die Bewertung der [Treiber die Überprüfung](driver-verification.md) .

-   **Die Ausführung ohne einer aktiven audio Rendering-Gerät nicht wird empfohlen, (Warnung)**

    Es sind keine audio-Rendering-Geräte auf dem System, möglicherweise einige der Bewertungsergebnisse im Zusammenhang mit Audio nicht exakt sein. Wenn Sie die Audiogeräte verfügen, installieren Sie Treiber für diese vor dem Ausführen der Bewertung. Wenn keine integrierten Lautsprecher in dem Computer vorhanden sind, verbinden Sie einen Kopfhörer oder Lautsprecher audio-Ausgang des Computers zum Beheben des Problems.

-   **Remote-Sitzung wird (Warnung) nicht empfohlen werden.**

-   Um genauere Ergebnisse zu erhalten, wird empfohlen, dass die Bewertung lokal auf dem Computer (anstatt eine Remotedesktopsitzung) ausgeführt wird.

-   **Mehrere Bildschirme (Warnung)**

    Um genauere Ergebnisse zu erhalten, wird empfohlen, die Bewertung auf einem Computer, der nur einen einzelnen Monitor angefügt wurde ausgeführt. Da die Bewertung Internet Explorer im Kioskmodus (Vollbild) auf einem einzelnen Monitor System startet ist Internet Explorer Fenster nur auf oberster Ebene auf dem Desktop zusammengesetzte sein. Auf einem Computer mit mehreren Bildschirmen möglicherweise anderen Fenstern der obersten Ebene. Dies kann die Bewertungsergebnisse beeinflussen.

### <a name="a-href-idbkmk-streaminganalyzeaanalyzing-generated-issues"></a><a href="" id="bkmk-streaminganalyze"></a>Analysieren von generierten Probleme

In den meisten Fällen können Sie den Link WPA detaillierte Analyse von Problemen, die generiert werden. Dadurch wird die StreamingMediaAssessmentDiagTrace.etl in WPA mit einem entsprechenden Profil für die Analyse des Problems geöffnet. In WPA können Sie das Problem in **Problemdetails und Bereiche der Untersuchung** des Problems eingrenzen erweitern. Informationen zu Problemen eingehenderen Analysen und Empfehlungen finden Sie unter [Häufige Probleme der Depth-Analyse](common-in-depth-analysis-issues.md).

### <a name="a-href-idbkmk-streamingglitchesacorrelating-glitches"></a><a href="" id="bkmk-streamingglitches"></a>Korrelation von Probleme

Nach der Analyse die Probleme, die durch die Bewertung generiert, kann zusätzliche Analyse von diagnostic Trace in WPA öffnen, und klicken Sie dann mithilfe des Links **Streaming Media-Analyse** durchgeführt werden. Dies beginnt WPA mit einer Ansicht für streaming Media Trace Analyse geeignet ist.

Die erste Tabelle von Interesse ist, der bietet eine hierarchische Ansicht der Aktivitäten (oder Intervallen) während der Analyse Iteration der Bewertung eingetreten Tabelle mit den **Aktivitäten** . Beispielsweise können folgende Intervalle überprüft werden:

-   Streaming Media Assessment – Stamm Intervall der Bewertung, den gesamten Trace übergreifende.

-   Streaming Media Assessment Iteration – ein Intervall für jede Iteration der Bewertung in der Ablaufverfolgungsdatei; Standardmäßig wird der Diagnose Trace nur eine Iteration enthalten.

-   Der Arbeitslast – ein Intervall für jede in der Iteration video Arbeitslast. Standardmäßig ist die einzige 1080p Arbeitslast vorhanden.

-   Media Engine Lebensdauer – das Intervall, in dem das Video Arbeitslast per Streaming übertragen wurden.

Wenn Sie ein Intervall von Interesse Trace finden, wählen Sie das Intervall in WPA, und vergrößern Sie der Auswahl bis zum Eingrenzen der Analysis.

Störung Ereignisse protokolliert wurden in der Tabelle **Generische Ereignisse** angezeigt werden können (unten am häufigsten in der Registerkarte WPA Analyse Tabelle). Wählen Sie die **Störung Ereignisse** in der Tabelle Generische Ereignisse Voreinstellung zum Filtern nach der erforderlichen Störung. Müssen mehrere dieser Ereignisse Störung in der Verfolgung gibt eine relativ schlechte streaming Erfahrung im System an. Um den Grund für diesen Fehler zu analysieren, versuchen Sie, diese mit Diagrammen von anderen zusammenfassenden Tabellen in WPA korrelieren. Durch Korrelation die Störung Ereignisse mit anderen zusammenfassenden Tabellen, können mögliche Probleme im System identifiziert werden.

### <a name="a-href-idbkmk-streamingsoftwareasoftware-vs-hardware-decoding"></a><a href="" id="bkmk-streamingsoftware"></a>Software im Vergleich zu decodieren von Hardware

Software oder Hardware Decodierung kann für das h. 264-Video, in dieser Bewertung gestreamt wird, Decodierung verwendet werden. Wenn Decodierung des h. 264-video die Grafikkarte im System nicht unterstützt, wird der Software für die Decodierung verwendet. Mit der Software erfolgt die Decodierung Arbeit statt der GPU CPU. In diesem Fall kann die CPU verursachter sein. Dadurch kann nicht mit den Echtzeit Decodierung Anforderungen des Videostreams, wodurch Probleme halten.

Die Möglichkeit, Hardware Decodierung mit kann durch die von der Grafikkarte unterstützt DXVA2 Modi ermittelt werden. DXVA2 Modi mit DXVA2\_ModeH264\_VLD Präfix (z. B. DXVA2\_ModeH264\_VLD\_FGT) anzugeben, dass die Grafikkarte Hardware Decodierung des h. 264-Video unterstützen kann. Die von der Grafikkarte unterstützt DXVA2 Modi aus der JobResults-XML-Datei in das folgende XML-Element abgerufen werden können: /AxeJobResults/ MachineConfiguration/EcoSysInfo/Graphics/DXVA2Modes. Speicherort der JobResults XML-Datei wird im Detailbereich Ergebnisansicht angezeigt.

### <a name="a-href-idbkmk-streaminggpuahigh-gpu-utilization"></a><a href="" id="bkmk-streaminggpu"></a>GPU hoher Auslastung

Video-Fehler können auch aufgrund von Upstream-Engpass verursacht werden, wenn die GPU verursachter ist. GPU Auslastung kann durch Öffnen den Diagnose Streaming Media-Trace in das Tool GPUView dargestellt werden. Das Tool gelesenen GPUView angemeldet Video und Kernel-Ereignisse aus einem Ereignis Ablaufverfolgungs-Protokolldatei (ETL) und stellt die Daten grafisch dar. Das Tool GPUView ist Teil des Windows Performance Toolkit und steht an folgendem Speicherort nach der Installation: "%ProgramFiles(x86)%\\Windows Kits\\10\\Windows Performance Toolkit\\Gpuview\\GPUView.exe". Streaming Media diagnostic Trace hat einen Pfad, ähnelt: "&lt;Verzeichnis&gt;\\000\_StreamingMedia\\StreamingMediaAssessmentDiagTrace.etl".

GPUView kann verwendet werden, um die Leistung der Grafiken processing Unit (GPU) und der Zentralprozessor () bei direct Memory Access (DMA) Puffer Verarbeitung (und alle anderen video Verarbeitung) auf der Videohardware zu bestimmen. Entwickler und Tester können GPUView verschiedene Arten von Ereignissen anzeigen, die auf ungewöhnliche Bedingungen wie Probleme, Verzögerungen Vorbereitung und schlechter Synchronisierung führen können. Weitere Informationen zu GPUView finden Sie unter der Dokumentation – Hilfedatei, GPUView.chm, die mit dem Tool installiert ist.

### <a name="a-href-idexitcodeathe-assessment-reports-an-exit-code-of-0x80050006"></a><a href="" id="exitcode"></a>Die Bewertung von Berichten Exit-Code 0x80050006

Dieser Fehler tritt auf, wenn Wartungsaufgaben auf dem PC erfasst wurden, aber nicht vor der Bewertung ausführen abgeschlossen. Dies verhindert, dass die Bewertung von ausgeführt, wie Wartungsaufgaben häufig Assessment Metriken auswirken.

Um dieses Problem zu beheben, führen Sie eine der folgenden Aktionen aus:

1.  Stellen Sie sicher, dass der Computer mit dem Netzwerk verbunden ist und auf Strom ausgeführt wird. Manuelles Initiieren Sie ausstehende Wartungsaufgaben mit dem folgenden Befehl aus einer Eingabeaufforderung mit erhöhten Rechten aus:

    `rundll32.exe advapi32.dll,ProcessIdleTasks`

2.  Deaktivieren Sie reguläre und im Leerlauf Wartungsaufgaben und beenden Sie alle Wartungsaufgaben vor der Bewertung wird ausgeführt.

## <a name="related-topics"></a>Verwandte Themen


[Streaming Media-Leistung](streaming-media-performance.md)

[Assessment Toolkit technische Referenz zu Windows](windows-assessment-toolkit-technical-reference.md)

[Bewertung](assessments.md)

[Häufige Probleme von eingehenderen Analysen](common-in-depth-analysis-issues.md)

[Standby Energie-Effizienz verbunden](connected-standby-energy-efficiency.md)

 

 







