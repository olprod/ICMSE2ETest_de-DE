---
title: "Ergebnisse für die Windows Media Player-Leistung und die Qualität Bewertung"
description: "Ergebnisse für die Windows Media Player-Leistung und die Qualität Bewertung"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 2503b5ce-6b01-4a49-b3a3-8c4b84419152
ms.prod: W10
ms.mktglfcycl: plan
ms.sitesec: msdn
ms.openlocfilehash: 13e7eee0a0127080a112e351ae2a45bf9b94da42
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="results-for-the-windows-media-player-performance-and-quality-assessment"></a>Ergebnisse für die Windows Media Player-Leistung und die Qualität Bewertung


Die Windows Media Player-Leistung und die Qualität der Bewertung Windows Media Player startet und spielt mehrere Medienclips eine nach der anderen Funktionen für die Medienwiedergabe bewerten und erfassen die Leistung und QoE-Metriken. Die Bewertungsergebnisse zur umfassen Metriken für die Anzahl von audio und video-Fehler oder erkennbare visuelle oder akustische Fehler in die Benutzeroberfläche. Der Schwerpunkt liegt auf die Qualität und Leistung der stabilen Zustand Wiedergabe in Windows Media Player, die die Arbeitslast eines Benutzers ansehen eines Films imitiert wird. Diese Bewertung wird keine Funktionalität durch Suchvorgänge oder Anhalten nicht ausgewertet werden.

In diesem Thema:

-   [Ziele-Datei](#bkmk-goals)

-   [Metriken](#bkmk-wmpmetrics)

-   [Probleme](#bkmk-wmpissues)

Weitere Informationen zu Assessment, Systemanforderungen und Bewertung Einstellungen finden Sie unter [Windows Media Player-Leistung und die Qualität](windows-media-player-performance-and-quality.md).

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

 

## <a name="a-href-idbkmk-wmpmetricsametrics"></a><a href="" id="bkmk-wmpmetrics"></a>Metriken


Die Ergebnisse zeigen Informationen zur Leistung und die Qualität der Wiedergabe von Windows Media Player auf dem Computer. Die folgende Tabelle enthält eine kurze Beschreibung für jede Metrik, die die Windows Media Player Wiedergabe Bewertung erfasst.

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
<td><p>Gesamte Audio-setzt</p></td>
<td><p>Die Gesamtzahl der audio setzt, die während der Wiedergabe aufgezeichnet wurden.</p></td>
</tr>
<tr class="even">
<td><p>Gesamte Audio-Fehler</p></td>
<td><p>Die Gesamtzahl der audio-Fehler, die während der Wiedergabe aufgezeichnet wurden.</p>
<div class="alert">
<strong>Hinweis</strong>  
<p>Ein Fehler wird jeder erkennbare visuelle oder akustische Fehler, die Benutzeroberfläche.</p>
</div>
<div>
 
</div></td>
</tr>
<tr class="odd">
<td><p>Blockieren der gesamte Audio</p></td>
<td><p>Die Gesamtanzahl der Versuche, die während der Wiedergabe audio blockieren aufgetreten ist.</p>
<div class="alert">
<strong>Hinweis</strong>  
<p>Blockieren von Audio tritt auf, wenn die Audiodaten schnell genug auf halten mit dem Rendering oder Zusammensetzung der Datei gelesen werden können.</p>
</div>
<div>
 
</div></td>
</tr>
<tr class="even">
<td><p>Insgesamt DWM-Fehler</p></td>
<td><p>Die Gesamtanzahl der Versuche, die Desktop Window Manager (DWM) Wiedergabe-Fehler verursacht. DWM ist der Zusammensetzung des die Wiedergabe beteiligt.</p></td>
</tr>
<tr class="odd">
<td><p>Insgesamt MF Daten löscht</p></td>
<td><p>Die Gesamtanzahl der Versuche, die Microsoft Media Foundation Daten während der Wiedergabe gelöscht wurde. Weitere Informationen zu dieser Media-Plattform, finden Sie unter [MSDN: Microsoft Media Foundation](http://go.microsoft.com/fwlink/?LinkId=232723).</p></td>
</tr>
<tr class="even">
<td><p>Insgesamt Enhanced Video-Fehler</p></td>
<td><p>Insgesamt Enhanced Data Rate (EDR) video Probleme, die während der Wiedergabe aufgezeichnet wurden.</p></td>
</tr>
</tbody>
</table>

 

Weitere Informationen können für jede Metrik verfügbar sein. Um diese Informationen anzuzeigen, wählen Sie den Link an der Datei (ETL) ein. ETL-Datei wird automatisch in Windows® Performance Analyzer (WPA) zur weiteren Analyse geöffnet.

## <a name="a-href-idbkmk-wmpissuesaissues"></a><a href="" id="bkmk-wmpissues"></a>Probleme


Die Windows Media Player Wiedergabe Bewertung Probleme oder Vorschläge, nicht. Die optimale Verwendung für die Bewertung ist die Leistung des Windows Media Player-Wiedergabe von zwei oder mehr Computern vergleichen.

### <a name="the-assessment-reports-an-exit-code-of-0x80050006"></a>Die Bewertung von Berichten Exit-Code 0x80050006

Dieser Fehler tritt auf, wenn Wartungsaufgaben auf dem PC erfasst wurden, aber nicht vor der Bewertung ausführen abgeschlossen. Dies verhindert, dass die Bewertung von ausgeführt, wie Wartungsaufgaben häufig Assessment Metriken auswirken.

Um dieses Problem zu beheben, führen Sie eine der folgenden Aktionen aus:

1.  Stellen Sie sicher, dass der Computer mit dem Netzwerk verbunden ist und auf Strom ausgeführt wird. Manuelles Initiieren Sie ausstehende Wartungsaufgaben mit dem folgenden Befehl aus einer Eingabeaufforderung mit erhöhten Rechten aus:

    `rundll32.exe advapi32.dll,ProcessIdleTasks`

2.  Deaktivieren Sie reguläre und im Leerlauf Wartungsaufgaben und beenden Sie alle Wartungsaufgaben vor der Bewertung wird ausgeführt.

## <a name="related-topics"></a>Verwandte Themen


[Windows Media Player-Leistung und Qualität](windows-media-player-performance-and-quality.md)

[Windows-Assessment-Toolkit](index.md)

[Bewertung](assessments.md)

[Media transcodieren Leistung](media-transcoding-performance.md)

 

 







