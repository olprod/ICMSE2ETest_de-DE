---
title: "Ergebnisse für die Dateiverarbeitung Bewertung"
description: "Ergebnisse für die Dateiverarbeitung Bewertung"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 9f620d9c-976c-4fdf-ba52-6188b3982305
ms.prod: W10
ms.mktglfcycl: plan
ms.sitesec: msdn
ms.openlocfilehash: 709bdbf4dd47a85147333d5313cb9d96db21ce32
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="results-for-the-file-handling-assessment"></a>Ergebnisse für die Dateiverarbeitung Bewertung


Das Dateiverarbeitung Assessment bietet eine automatisierte Möglichkeit, allgemeine Dateivorgänge Übung und Metriken erfassen. Diese Bewertung misst Dauer und Durchsatz beim Kopieren, verschieben, komprimieren, extrahieren und Löschen von Dateien und Ordnern auf Ihrem Computer. Die Ergebnisse können Sie verstehen, wie gut der Computer während dieser Vorgänge ausgeführt wird.

In diesem Thema:

-   [Ziele-Datei](#bkmk-goals)

-   [Metriken](#bkmk-fileresults)

-   [Probleme](#bkmk-fileissues)

Weitere Informationen zu den Systemanforderungen finden Sie unter Arbeitslasten und Einstellungen für die Bewertung [Dateien verarbeiten](file-handling.md).

## <a name="a-href-idbkmk-goalsagoals-file"></a><a href="" id="bkmk-goals"></a>Ziele Datei


Sie können benutzerdefinierte Ziele Ihrer Verbesserungen in der Ergebnisanzeige gemessen erstellen. Ziele Dateien sind eine Ursachenanalyse Tool, das helfen zu verstehen, wie ein PC ausgeführt wird und zum Vergleichen von PCs in Ihrem Unternehmen.

Beispielsweise Ziele für einen einfachen Laptop möglicherweise nicht die Ziele für einen high-End-Desktopcomputer festgelegten oder erwartet Land/Ihrer Region möglicherweise so, dass Sie die Flexibilität, verschiedene Ziele zu definieren möchten und verbessert die wichtige Anforderungen als Zeit und Technologie ändern.

Bei dem Ziel für diese Metrik ein metrischer Wert verglichen wird, ist der Status farblich in der Ansicht Ergebnis wie folgt an:

-   Hellviolett bedeutet, dass das System einen größeren Benutzerkomfort verfügt und keine wahrgenommene Probleme vorliegen.

-   Mittlere Lila bedeutet, dass die Benutzeroberfläche zulässige ist und Sie können das System optimieren. Überprüfen Sie die Empfehlungen und Analyse, um herauszufinden, welche Verbesserungen an das System hergestellt werden können. Diese Software Änderungen, konfigurationsänderungen oder Hardware Änderungen möglich.

-   Dunkles Lila bedeutet, dass das System benutzerfreundlich verfügt und erhebliche Platz für Verbesserungen vorhanden ist. Überprüfen der Empfehlungen und Analyse, um die Verbesserungen, die das System vorgenommen werden können, finden Sie unter. Dabei kann es sich um Software Änderungen, konfigurationsänderungen oder Hardware suchen handeln. Möglicherweise müssen Sie erwägen Kompromissen, um eine hohe Qualität-Windows-Erfahrung zu übermitteln.

-   Keine Farbe bedeutet, dass es keine Ziele für die Metrik definiert sind.

**Hinweis**  
In der Windows Assessment Toolkit für Windows 8 umfassen einige Bewertung Ziele Standarddateien. Zum ersten Mal anzeigen von Ergebnisse mit dieser Version der Tools, wird die Ziele-Standarddatei verwendet. Jedoch können Sie auch benutzerdefinierte Ziele für Windows 8 die gleiche Weise definieren, die Sie für Windows 8.1 und Windows-10 können.

 

Sie können legen Sie die Ziele und eine Datei Ziele zu diesem Speicherort hinzufügen, bevor Sie die Benutzeroberfläche verwenden können, um die benutzerdefinierten Ziele anzuwenden. Nach dem Auswählen einer Datei Ziele wird weiterhin die Ziele-Datei sein, die für alle Ergebnisse verwendet wird, die geöffnet werden.

Nur eine Ziele Datei kann zu einem Zeitpunkt verwendet werden. Ziele für alle Bewertung sind in einer einzigen Ziele Datei festzulegen. Die Bewertungstools sucht Ziele in der folgenden Reihenfolge:

1.  Eine benutzerdefinierte Ziele-Datei

2.  Ziele, die in der Ergebnisdatei definiert sind

3.  Ziele, die im Manifest Assessment definiert sind

Können die Ziele-Beispieldatei, die bereitgestellt wird unter ProgramFiles%\\Windows Kits\\10\\Assessment and Deployment Kit\\Windows Assessment Toolkit\\SDK\\Beispiele\\Ziele Ihrer eigenen Ziele-Datei zu erstellen.

**Hinweis**  
Nicht in eine Datei Ziele mit einem Auftrag Pakete, jedoch können sie für andere Benutzer freigegeben gespeichert werden.

 

## <a name="a-href-idbkmk-fileresultsametrics"></a><a href="" id="bkmk-fileresults"></a>Metriken


Die Ergebnisse für die Bewertung Dateiverarbeitung zeigen die Leistung des Computers für die Kopie, verschieben, komprimieren und delete-Vorgänge. In der folgenden Tabelle werden die Metriken, die die Dateiverarbeitung Bewertung misst beschrieben.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Metrisch</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Kopieren Sie die Dauer (programmgesteuerten)</p></td>
<td><p>Zeigt die Anzahl der Sekunden an, denen der programmgesteuerten Kopiervorgang abgeschlossen hat.</p></td>
</tr>
<tr class="even">
<td><p>Kopieren Sie die Dauer (UX in Skripte integriert)</p></td>
<td><p>Zeigt die Anzahl der Sekunden an, denen der skriptgesteuerten Kopiervorgang abgeschlossen hat.</p></td>
</tr>
<tr class="odd">
<td><p>Kopieren Sie den Durchsatz (programmgesteuerten)</p></td>
<td><p>Zeigt den Durchsatz in Megabyte pro Sekunde, für die programmgesteuerte Kopiervorgang.</p></td>
</tr>
<tr class="even">
<td><p>Kopieren Sie den Durchsatz (UX in Skripte integriert)</p></td>
<td><p>Zeigt den Durchsatz in Megabyte pro Sekunde, für die Skripts Kopiervorgang.</p></td>
</tr>
<tr class="odd">
<td><p>Löschen Sie die Dauer (programmgesteuerten)</p></td>
<td><p>Zeigt die Anzahl der Sekunden an, denen der programmgesteuerten Löschvorgang ausgeführt wurden, auf Fertig stellen.</p></td>
</tr>
<tr class="even">
<td><p>Löschen Sie die Dauer (UX in Skripte integriert)</p></td>
<td><p>Zeigt die Anzahl der Sekunden, die der skriptgesteuerte Löschvorgang ausgeführt wurden, auf Fertig stellen.</p></td>
</tr>
<tr class="odd">
<td><p>Löschen von Datei Durchsatz (Programmatische)</p></td>
<td><p>Zeigt den Durchsatz Datei Dateien pro Sekunde, für die programmgesteuerte Vorgang löschen.</p></td>
</tr>
<tr class="even">
<td><p>Löschen Sie den Durchsatz (programmgesteuerten)</p></td>
<td><p>Ist den Durchsatz in Megabyte pro Sekunde, für die programmgesteuerte Vorgang löschen dargestellt.</p></td>
</tr>
<tr class="odd">
<td><p>Löschen Sie den Durchsatz (UX in Skripte integriert)</p></td>
<td><p>Ist den Durchsatz in Megabyte pro Sekunde, für die Skripts Vorgang löschen dargestellt.</p></td>
</tr>
<tr class="even">
<td><p>Dateiverarbeitung durch den</p></td>
<td><p>Bietet einen Überblick, der benötigte Zeit, die allgemeine Dateivorgänge (beispielsweise kopieren, verschieben, komprimieren und Delete) ausgeführt wurden anzeigt, auf Fertig stellen. Um ausführliche Metriken für die Dateibehandlung von angezeigt wird, erweitern Sie das Ergebnis.</p></td>
</tr>
<tr class="odd">
<td><p>Datei Organisation Metriken</p></td>
<td><p>Zeigt die Länge der Zeit programmatischen Skript-Vorgänge (beispielsweise kopieren, verschieben, komprimieren und löschen) für die fertig sind, sowie den folgenden Durchsatz für jeden Vorgang:</p>
<ul>
<li><p>Kopieren Sie die Dauer (Programmatic) MinifilterDelay (Sekunden)</p></li>
<li><p>Löschen Sie die Dauer (Programmatic) MinifilterDelay (Sekunden)</p></li>
<li><p>Verschieben der Dauer (Programmatic) MinifilterDelay (Sekunden)</p></li>
<li><p>Kopieren Sie den Durchsatz (Programmatic) (MB pro Sekunde)</p></li>
<li><p>Löschen Sie den Durchsatz (Programmatic) (MB pro Sekunde)</p></li>
<li><p>Verschieben Sie den Durchsatz (Programmatic) (MB pro Sekunde)</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Dauer (Programmatische) verschieben</p></td>
<td><p>Zeigt die Anzahl der Sekunden an, denen den programmgesteuerten, dass der Vorgang verschieben abgeschlossen hat.</p></td>
</tr>
<tr class="odd">
<td><p>Verschieben der Dauer (UX in Skripte integriert)</p></td>
<td><p>Zeigt die Anzahl der Sekunden an, denen die skriptgesteuerte, dass der Vorgang verschieben abgeschlossen hat.</p></td>
</tr>
<tr class="even">
<td><p>Verschieben Sie die Datei Durchsatz (programmgesteuerten)</p></td>
<td><p>Ist den Durchsatz Datei in Dateien pro Sekunde, für die programmgesteuerte Verschiebevorgang dargestellt.</p></td>
</tr>
<tr class="odd">
<td><p>Verschieben Sie die Datei Durchsatz (UX in Skripte integriert)</p></td>
<td><p>Ist den Durchsatz Datei in Dateien pro Sekunde, für die Skripts Verschiebevorgang dargestellt.</p></td>
</tr>
<tr class="even">
<td><p>Verschieben Sie den Durchsatz (Programmatische)</p></td>
<td><p>Ist den Durchsatz in MB pro Sekunde, für die programmgesteuerte Verschiebevorgang dargestellt.</p></td>
</tr>
<tr class="odd">
<td><p>Verschieben Sie den Durchsatz (UX in Skripte integriert)</p></td>
<td><p>Ist den Durchsatz in MB pro Sekunde, für die Skripts Verschiebevorgang dargestellt.</p></td>
</tr>
<tr class="even">
<td><p>ZIP-Dauer (UX in Skripte integriert)</p></td>
<td><p>Zeigt die Anzahl der Sekunden an, denen des Skripts Komprimierungsvorgangs abgeschlossen hat.</p></td>
</tr>
<tr class="odd">
<td><p>ZIP-Durchsatz (UX in Skripte integriert)</p></td>
<td><p>Zeigt den Durchsatz MB pro Sekunde, für die Skripts Vorgang komprimiert werden sollen.</p></td>
</tr>
<tr class="even">
<td><p>Aufheben der Markierung Zip Dauer (UX in Skripte integriert)</p></td>
<td><p>Zeigt die Anzahl der Sekunden an, denen der Vorgang skriptgesteuerte extrahieren ausgeführt wurden, auf Fertig stellen.</p></td>
</tr>
<tr class="odd">
<td><p>Aufheben der Markierung Zip-Durchsatz (UX in Skripte integriert)</p></td>
<td><p>Ist den Durchsatz in Megabyte pro Sekunde, für die Skripts Vorgang extrahieren dargestellt.</p></td>
</tr>
</tbody>
</table>

 

**Hinweis**  
Wenn Sie die **Aktivieren Minifilter Diagnosemodus** Assessment-Einstellung aktiviert, werden die Bewertungsergebnisse Minifilter Metriken enthalten. Weitere Informationen zu Minifilter Metriken und Ergebnisse finden Sie unter [Minifilter Diagnose](minifilter-diagnostics.md).

 

## <a name="a-href-idbkmk-fileissuesaissues"></a><a href="" id="bkmk-fileissues"></a>Probleme


### <a name="the-assessment-reports-an-exit-code-of-0x80050006"></a>Das Assessment Berichte Exit-Code 0x80050006

Dieser Fehler tritt auf, wenn Wartungsaufgaben auf dem PC erfasst wurden, aber nicht vor der Bewertung ausführen abgeschlossen. Dies verhindert, dass die Bewertung von ausgeführt, wie Wartungsaufgaben häufig Assessment Metriken auswirken.

Um dieses Problem zu beheben, führen Sie eine der folgenden Aktionen aus:

1.  Stellen Sie sicher, dass der Computer mit dem Netzwerk verbunden ist und auf Stromversorgung ausgeführt wird. Manuelles Initiieren Sie ausstehende Wartungsaufgaben mit dem folgenden Befehl aus einer Eingabeaufforderung mit erhöhten Rechten:

    `rundll32.exe advapi32.dll,ProcessIdleTasks`

2.  Deaktivieren Sie reguläre und im Leerlauf Wartungsaufgaben und beenden Sie alle Wartungsaufgaben vor der Bewertung wird ausgeführt.

## <a name="related-topics"></a>Verwandte Themen


[Dateiverarbeitung](file-handling.md)

[Bewertung](assessments.md)

[Standby Energie-Effizienz verbunden](connected-standby-energy-efficiency.md)

[Erstellen und Ausführen eines Energie Effizienz Auftrags](create-and-run-an-energy-efficiency-job.md)

[Minifilter Diagnose](minifilter-diagnostics.md)

[Assessment Toolkit technische Referenz zu Windows](windows-assessment-toolkit-technical-reference.md)

 

 







