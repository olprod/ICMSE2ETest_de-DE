---
title: "Ergebnisse für die lokale Videowiedergabe Bewertung"
description: "Ergebnisse für die lokale Videowiedergabe-Bewertung"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 4b4198f1-99bd-4858-a933-5e194ed3367f
ms.prod: W10
ms.mktglfcycl: plan
ms.sitesec: msdn
ms.openlocfilehash: 02c609cafdfa18036b32a16e358dfcadb1b66ff2
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="results-for-the-local-video-playback-assessment"></a>Ergebnisse für die lokale Videowiedergabe Bewertung


Lokale Videowiedergabe Assessment Ergebnisse anzeigen Metriken und Probleme, die Energie Effizienz Probleme zu markieren. Wenn möglich, wird die Ursache des Problems Effizienz Energie identifiziert. Beispielsweise könnte es Treiber, Dienste oder Prozesse. Empfohlene Lösungen für diese Probleme stehen zur Verfügung.

Dieses Thema hilft Ihnen die interpretiert werden die Ergebnisse, die mit einer Batterie führen Sie Auftrag, der die lokale Videowiedergabe Bewertung verwendet. Er enthält außerdem Hinweise zum Verwenden der Ergebnisse zu identifizieren und beheben häufig auftretender Probleme, die sich negativ auf die Computer Akkulaufzeit auswirken.

In diesem Thema:

-   [Ziele-Datei](#bkmk-goals)

-   [Metriken](#bkmk-metrics)

-   [Probleme](#bkmk-idleissues)

Weitere Informationen zu Aufträgen Batterie führen Sie nach unten finden Sie unter [Dem Standbymodus Energie-Effizienz verbunden](connected-standby-energy-efficiency.md).

## <a name="a-href-idbkmk-goalsagoals-file"></a><a href="" id="bkmk-goals"></a>Ziele-Datei


Sie können benutzerdefinierte Ziele Ihrer Verbesserungen in der Ergebnisanzeige gemessen erstellen. Ziele Dateien sind eine Ursachenanalyse Tool, das helfen zu verstehen, wie ein PC ausgeführt wird und zum Vergleichen von PCs in Ihrem Unternehmen.

Beispielsweise Ziele für einen einfachen Laptop möglicherweise nicht die Ziele für einen high-End-Desktopcomputer festgelegten oder erwartet Land/Ihrer Region möglicherweise so, dass Sie die Flexibilität, verschiedene Ziele zu definieren möchten und verbessert die wichtige Anforderungen als Zeit und Technologie ändern.

Bei dem Ziel für diese Metrik ein metrischer Wert verglichen wird, ist der Status farblich in der Ansicht Ergebnis wie folgt an:

-   Hellviolett bedeutet, dass das System einen größeren Benutzerkomfort verfügt und keine wahrgenommene Probleme vorliegen.

-   Mittlere Lila bedeutet, dass die Benutzeroberfläche zulässige ist und Sie können das System optimieren. Überprüfen Sie die Empfehlungen und Analyse, um herauszufinden, welche Verbesserungen an das System hergestellt werden können. Diese Software Änderungen, konfigurationsänderungen oder Hardware Änderungen möglich.

-   Dunkles Lila bedeutet, dass das System benutzerfreundlich verfügt und erhebliche Platz für Verbesserungen vorhanden ist. Überprüfen der Empfehlungen und Analyse, um die Verbesserungen, die das System vorgenommen werden können, finden Sie unter. Diese Software Änderungen, konfigurationsänderungen oder Hardware Änderungen möglich. Möglicherweise müssen Sie erwägen Kompromissen, um eine hohe Qualität-Windows-Erfahrung zu übermitteln.

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

 

## <a name="a-href-idbkmk-metricsametrics"></a><a href="" id="bkmk-metrics"></a>Metriken


Die folgenden Metriken sind für die lokale Videowiedergabe Bewertung spezifisch:

### <a name="diagnostic-mode-metrics"></a>Diagnosemodus Metriken

### <a name="system-timer-resolution"></a>System Timer-Lösung

Diese Metrik stellt die Auflösung in Millisekunden an, der den Timer System.

### <a name="processes-changing-system-timer-resolution"></a>Prozesse System Timer Auflösung ändern

Diese Metrik stellt die Anzahl der Prozesse, die eine System Lösung Änderung anfordern.

### <a name="a-href-idprocesses-using--1--cpu-during-idle-periodaprocesses-using-gt1-cpu-during-idle-period"></a><a href="" id="processes-using--1--cpu-during-idle-period"></a>Verarbeitet mit &gt;1 % CPU Zeitraum im Leerlauf

Diese Metrik stellt die Anzahl der Prozesse, ausgenommen der app Videowiedergabe mit mindestens 1 % CPU-Auslastung.

### <a name="storage-read-count"></a>Speicher lesen Anzahl

Diese Metrik stellt die Gesamtzahl der Speicher Lesevorgänge während der Bewertung ausführen dar. Dies schließt die Videowiedergabe App Speicher Lesevorgänge aus.

### <a name="data-read-from-storage"></a>Aus dem Speicher gelesene XML-Daten

Diese Metrik stellt die Gesamtgröße in Kilobyte, der Daten, die während der Bewertung ausführen aus dem Speicher gelesen wurde. Dies schließt alle Daten, die von der app Videowiedergabe gelesen wurde.

### <a name="storage-write-count"></a>Anzahl von Schreibvorgängen

Diese Metrik stellt die Gesamtanzahl der Schreibvorgänge auf Speicher während der Bewertung ausführen.

### <a name="data-written-to-storage"></a>In Speicher geschriebene Daten

Diese Metrik stellt die Gesamtgröße der Daten, die in den Speicher, während der Bewertung ausgeführt geschrieben wurde in KB.

### <a name="storage-flush-count"></a>Flush Count Speicher

Diese Metrik stellt die Gesamtzahl der Speicher geleert während der Bewertung ausführen.

### <a name="a-href-idprocesses-reading---50-timesaprocesses-reading-gt-50-times"></a><a href="" id="processes-reading---50-times"></a>Lesen Sie weiter verarbeitet &gt; 50 Mal

Diese Metrik stellt die Anzahl der Prozesse, die aus dem Speicher mehr als 50 Mal während der Bewertung ausführen gelesen. Dies schließt die Videowiedergabe app.

### <a name="a-href-idprocesses-reading---1-mbaprocesses-reading-gt-1-mb"></a><a href="" id="processes-reading---1-mb"></a>Lesen Sie weiter verarbeitet &gt; 1 MB

Diese Metrik stellt die Anzahl der Prozesse, die mehr als ein Megabyte aus dem Speicher während der Bewertung ausführen gelesen. Dies schließt die Videowiedergabe app.

### <a name="processes-writing-to-storage"></a>Schreiben in einen Speicher Prozesse

Diese Metrik stellt die Anzahl der Prozess, der während der Ausführung Assessment in einen Speicher zu schreiben. Dies schließt die Videowiedergabe app.

### <a name="other-metrics"></a>Andere Metriken

### <a name="dflip-used-by-playback"></a>DFlip von Wiedergabe verwendet

Diese Metrik stellt dar, ob die DirectFlip bei der Wiedergabe der Mediendatei im Vollbildmodus aktiviert wurde.

## <a name="a-href-idbkmk-idleissuesaissues"></a><a href="" id="bkmk-idleissues"></a>Probleme


Die lokale Videowiedergabe Bewertung führt eine Problemanalyse der erweiterten und enthält Links zu Windows Performance Analyzer (WPA) von Problemen, die identifiziert werden. WPA möglicherweise zusätzliche Informationen zu dem Datenträger oder CPU-Aktivität je nach den Arten von Problemen, die identifiziert wurden darstellen. Weitere Informationen zu eingehenderen Analysen Probleme und Empfehlungen finden Sie unter, [Häufig auftretender Probleme der Depth-Analyse](common-in-depth-analysis-issues.md).

Es folgt eine Liste der Probleme, die auftreten können, wenn die lokale Videowiedergabe Bewertung ausgeführt wird.

### <a name="directflip-is-not-enabled"></a>DirectFlip ist nicht aktiviert.

Wenn DirectFlip nicht aktiviert ist, wird ein Problem generiert, die der Verbesserung der Energie-werden, die abgerufen werden kann behandelt, wenn Sie DirectFlip verwenden.

### <a name="directflip-is-not-supported"></a>DirectFlip wird nicht unterstützt.

Wenn DirectFlip nicht auf dem Display-Treiber unterstützt wird, wird ein Problem generiert, die der Verbesserung der Energie-werden, die abgerufen werden kann behandelt, wenn Sie DirectFlip verwenden.

### <a name="total-storage-write-count"></a>Anzahl von Schreibvorgängen Gesamtspeicher

Ein Problem wird immer generiert, die die Gesamtanzahl der Schreibvorgänge auf Speicherplatz sowie den Schwellenwert für die hervorgehoben. Schreiben von Daten in einen Speicher erhöht Stromverbrauchs.

### <a name="total-writes-to-storage"></a>Gesamtanzahl der Schreibzugriffe in einen Speicher

Immer wird ein Problem generiert, die die Gesamtgröße der Daten in den Speicher geschrieben wird, während der Bewertung ausgeführt werden. Schreiben von Daten in einen Speicher erhöht Stromverbrauchs.

### <a name="the-assessment-reports-an-exit-code-of-0x80050006"></a>Das Assessment Berichte Exit-Code 0x80050006

Dieser Fehler tritt auf, wenn Wartungsaufgaben auf dem PC erfasst wurden, aber nicht vor der Bewertung ausführen abgeschlossen. Dies verhindert, dass die Bewertung von ausgeführt, wie Wartungsaufgaben häufig Assessment Metriken auswirken.

Um dieses Problem zu beheben, führen Sie eine der folgenden Aktionen aus:

1.  Stellen Sie sicher, dass der Computer mit dem Netzwerk verbunden ist und auf Stromversorgung ausgeführt wird. Manuelles Initiieren Sie ausstehende Wartungsaufgaben mit dem folgenden Befehl aus einer Eingabeaufforderung mit erhöhten Rechten:

    `rundll32.exe advapi32.dll,ProcessIdleTasks`

2.  Deaktivieren Sie reguläre und im Leerlauf Wartungsaufgaben und beenden Sie alle Wartungsaufgaben vor der Bewertung wird ausgeführt.

## <a name="related-topics"></a>Verwandte Themen


[Windows-Assessment-Toolkit](windows-assessment-toolkit-technical-reference.md)

[Bewertung](assessments.md)

[Standby Energie-Effizienz verbunden](connected-standby-energy-efficiency.md)

 

 







