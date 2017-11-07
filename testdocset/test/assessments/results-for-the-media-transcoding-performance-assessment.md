---
title: "Ergebnisse für die Bewertung Media transcodieren Leistung"
description: "Ergebnisse für die Bewertung Media transcodieren Leistung"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 576a152d-44a7-456f-b305-8bf71dd7ac06
ms.prod: W10
ms.mktglfcycl: plan
ms.sitesec: msdn
ms.openlocfilehash: 20e73ef24431719fabe4c9563f61034feb4cf769
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="results-for-the-media-transcoding-performance-assessment"></a>Ergebnisse für die Bewertung Media transcodieren Leistung


Das Media transcodieren Performance Assessment misst eine Videodatei an ein anderes Format oder Bitrate zu ändern. Medien-Transcoding wird in mehreren Schlüsselszenarien in Windows wie PlayTo und Kamera erfassen verwendet. Grundlegendes zur Leistung bei der Media transcodieren eines Computers ist Schlüssel zur Verbesserung der benutzerfreundlichkeit. Die Bewertungsergebnisse zeigen Sie Informationen zu den transcodieren Dauer und Geschwindigkeit. Dieses Thema enthält Anleitungen zum Verständnis der Ergebnisse von Medien-Transcoding Performance-Bewertung.

In diesem Thema:

-   [Ziele Datei](#bkmk-goals)

-   [Metriken](#results)

-   [Probleme](#issues)

Weitere Informationen über die Anforderung System und Bewertung Einstellungen für die Bewertung finden Sie unter [Media transcodieren Leistung](media-transcoding-performance.md)

## <a name="a-href-idbkmk-goalsagoals-file"></a><a href="" id="bkmk-goals"></a>Ziele-Datei


Sie können benutzerdefinierte Ziele Ihrer Verbesserungen in der Ergebnisanzeige gemessen erstellen. Ziele Dateien sind eine Ursachenanalyse Tool, das helfen zu verstehen, wie ein PC ausgeführt wird und zum Vergleichen von PCs in Ihrem Unternehmen.

Beispielsweise Ziele für einen einfachen Laptop möglicherweise nicht die Ziele für einen high-End-Desktopcomputer festgelegten, oder Erwartungen Land/Ihrer Region möglicherweise so, dass Sie die Flexibilität, verschiedene Ziele zu definieren möchten und verbessert die wichtige Anforderungen als Zeit und Technologie ändern.

Wenn an das Ziel für diese Metrik ein metrischer Wert verglichen wird, wird der Status farblich in der Ansicht Ergebnis wie folgt:

-   Hellviolett bedeutet, dass das System einen größeren Benutzerkomfort verfügt und keine wahrgenommene Probleme vorliegen.

-   Mittlere Lila bedeutet, dass die Benutzeroberfläche zulässige ist und Sie können das System optimieren. Überprüfen Sie die Empfehlungen und Analyse, um herauszufinden, welche Verbesserungen an das System hergestellt werden können. Dabei kann es sich um Software Änderungen, konfigurationsänderungen oder Hardware suchen handeln.

-   Dunkles Lila bedeutet, dass das System benutzerfreundlich verfügt und erhebliche Platz für Verbesserungen vorhanden ist. Überprüfen Sie die Empfehlungen und Analyse, um die Verbesserungen, die das System vorgenommen werden können, finden Sie unter. Dabei kann es sich um Software Änderungen, konfigurationsänderungen oder Hardware suchen handeln. Möglicherweise müssen Sie die Nachteile, um eine hohe Qualität bereitzustellen, den Windows-Erfahrung erwägen.

-   Keine Farbe bedeutet, dass es keine Ziele für die Metrik definiert sind.

**Hinweis**   In der Windows Assessment Toolkit für Windows 8 umfassen einige Analysen Ziele Standarddateien. Zum ersten Mal anzeigen von Ergebnisse mit dieser Version der Tools, wird die Ziele-Standarddatei verwendet. Jedoch können Sie auch benutzerdefinierte Ziele für Windows 8 die gleiche Weise definieren, die Sie für Windows 8.1 und Windows 10 können.

 

Legen Sie die Ziele und eine Datei Ziele zu diesem Speicherort hinzufügen, bevor Sie die Benutzeroberfläche verwenden können, die benutzerdefinierte Ziele anwenden können. Nach dem Auswählen einer Datei Ziele wird weiterhin die Ziele-Datei sein, die für alle Ergebnisse verwendet wird, die geöffnet werden.

Nur eine Ziele Datei kann zu einem Zeitpunkt verwendet werden. Ziele für alle Bewertung sind in einer einzigen Ziele Datei festzulegen. Die Bewertungstools sucht Ziele in der folgenden Reihenfolge:

1.  Eine benutzerdefinierte Ziele-Datei

2.  Ziele, die in der Ergebnisdatei definiert sind

3.  Ziele, die im Manifest Assessment definiert sind

Können die Ziele Beispieldatei bereitgestellt wird, die unter ProgramFiles%\\Windows Kits\\10\\Assessment and Deployment Kit\\Windows Assessment Toolkit\\SDK\\Beispiele\\Ziele zum Erstellen Ihrer eigenen Ziele-Datei.

**Hinweis**  
Eine Datei Ziele mit einem Auftrag keine Pakete, aber Sie können auf einer anderen Personen zur Freigabe speichern.

 

## <a name="a-href-idresultsametrics"></a><a href="" id="results"></a>Metriken


Die Ergebnisse zeigen Informationen zu transcodieren Dauer und Geschwindigkeit auf dem Computer. Das Media transcodieren Performance Assessment meldet beiden Metriken, die eng begrenzt werden: **Codierung Dauer** und **Codierung Leistung**.

**Codierung** Leistungsmetrik misst die Leistung im Hinblick auf den Faktor in Echtzeit. Beispielsweise bedeutet der metrische Wert der 1.0, transcodieren durchgeführt wurden in Echtzeit; der metrischen Wert bedeutet 2.0 wurde, transcodieren zweimal schneller als in Echtzeit möglich. der metrischen Wert 0,5 bedeutet in diesem transcodieren erfolgte zweimal langsamer als Echtzeit – für 20 zweite Eingabe video, transcodieren dauert 40 Sekunden. Da die transcodieren Leistung hängt von Eingabe- und Formate und auf der Nutzung/nicht-Nutzung der Hardware Accelerations, die Bewertung eine Reihe von Tests für die Variation der weit verbreitete Eingabe führt und Ausgabe formatiert Kombinationen als auch mit Hardware einer hardwarebeschleunigten Codierung und-Decodierung aktiviert oder deaktiviert.

Die Ziele für die **Codierung** Leistungsmetrik sind:

-   &gt;1.2 ist Grün, was bedeutet, dass keine wahrgenommene Probleme vorliegen.

-   1.2 ist gelb, d. h., Sie können das System optimieren.

-   &lt;1.0 ist rot, was bedeutet, dass Verbesserungen benötigt werden.

Wenn ein metrischer Wert aus einem bestimmten Test kleiner als 1,0 ist kann akzeptabel sein. Die Metriken sind weitere Vergleichszwecken – es können Sie sehen, welche Kombinationen von transcodieren ein-/ Ausgabe vom die Pipeline in die Echtzeit verarbeitet werden und welche nicht.

Diese Metrik Ergebnisse können auch in der Registrierung aufgefüllt werden (siehe die problemerklärung – neue Leistungsdaten verfügbar ist), und klicken Sie dann von der Pipeline Medienteile (MDE- und Medien erfassen) verwendet, um ihre Workflows optimiert.

Die anderen Metrik von der Bewertung gemeldeten ist **Codierung Dauer** misst die Zeit für eine transcodieren Vorgang für einen 20 Sekunden input Clip erforderliche. Die Metrik für dieselben Tests als **Codierung Leistung**berechnet wird.

## <a name="issues"></a>Probleme


Die folgenden Probleme und Empfehlungen basierend auf der Metriken erfasst werden, während das Media transcodieren Performance Assessment können auftreten. Sie können den Link unter **Weitere Informationen** zur Lösung dieses Problems Empfehlungen folgen. Die empfohlene Verwendung für die Bewertung ist die Leistung Media transcodieren zwei oder mehr Computer vergleichen.

### <a name="a-href-idtrascode-issue-dxvaasoftware-decoding-is-faster-than-dxva-default-decoding"></a><a href="" id="trascode-issue-dxva"></a>Software Decodierung ist kürzer als die Decodierung DXVA (Standard)

Dieses Problem wird während des ersten Tests bestimmt, die die Bewertung vor die Eingabe/Ausgabe Formate auf der Basis Variation Tests ausgeführt wird. Die Situation, in der Software Decodierung schneller als hardwarebeschleunigte ist ist möglich, wenn die System CPU-Ressourcen leistungsfähiger als die Funktionen von Grafiken Systemressourcen werden. Dies gilt in der Regel für eine hochwertige Systeme mit leistungsstarken Multi-Kern-CPUs oder die Videokarte nur geringe DXVA Profile unterstützt. Behebung des Problems kann die Leistung transcodieren wesentlich verbessert.

Um dieses Problem zu beheben, wählen Sie im Detailbereich im Problem Lösung den Link Weitere Informationen. Dadurch wird einen bestimmten Schlüssel der Registrierung hinzugefügt. Die Pipeline transcodieren prüft, ob des Schlüssels in der Registrierung, und wenn es vorhanden ist, wird DXVA nicht in die Codierung Vorgänge verwendet.

Das Vorhandensein dieser Registrierungsschlüssel verhindert auch das transcodieren Performance Assessment aus dieser Tests DXVA/nicht-DXVA erneut ausführen. Beachten Sie, dass dieser Registrierungsschlüssel nur von der Pipeline transcodieren verwendet wird. Die übliche Wiedergabe Pipeline bleibt unverändert und DXVA Decodierung wird verwendet, wenn DXVA Features zur Verfügung stehen.

### <a name="a-href-idtrascode-issue-perfanew-performance-data-is-available"></a><a href="" id="trascode-issue-perf"></a>Neue Leistungsdaten ist verfügbar

Dieses Problem ist nach jedem Ausführen in den Ergebnissen Assessment vorhanden. Mit diesem Problem bietet eine Möglichkeit für Sie zum Auffüllen der Leistungsdaten in der Registrierung oder Leistungsdaten aus der Registrierung zu löschen.

Sie haben zwei Optionen, um dieses Problem zu beheben:

1.  Wählen Sie den PerfResults.reg Link. Füllt die Daten in der Registrierung, und der Pipeline Media bietet die Möglichkeit zum Verbessern der Leistung transcodieren.

2.  Wählen Sie den Link ClearPerfResults.reg. Leistungsdaten für alle Codierung entfernt aus der Registrierung, einschließlich der Daten aus dem Test DXVA/nicht-DXVA.

Da die Daten in der Registrierung mit der Option 1 gefüllt und die Daten von der Pipeline PlayTo und das Erfassen Szenario verwendet werden, ändert diese die Benutzeroberfläche an. Option 2 können Sie Rollback der Änderungen und wieder auf die ursprüngliche Erfahrung für die Szenarien PlayTo und erfasst.

### <a name="a-href-idtrascode-issue-errorsasome-tests-have-finished-with-error"></a><a href="" id="trascode-issue-errors"></a>Für bestimmte Tests ist mit Fehler beendet.

Dieses Problem wird gemeldet, wenn einige der Tests Fehler während die Bewertung ausgeführt wurde. Am häufigsten der Grund einen Test ein Fehler auftritt, ist entweder, da die Software von Drittanbietern verhindert, dass die Pipeline ordnungsgemäß ausgeführt, oder der Grafiktreiber hat Probleme. Die Liste der fehlerhaften Tests wird in der Beschreibung des Kompatibilitätsproblems im Detailfenster angezeigt.

Die allgemeine Empfehlung werden, um dieses Problem zu beheben, stellen Sie sicher, dass die aktuellsten Grafiktreiber auf dem System installiert sind.

### <a name="a-href-idtrascode-issue-missingaimportant-metrics-are-missed"></a><a href="" id="trascode-issue-missing"></a>Wichtige Metriken werden verpasste

Dieses Problem wird gemeldet, wenn die Tests ordnungsgemäß ausgeführt und keine transcodieren Testfehler erkannt wurden, jedoch Post-Prozess konnte nicht zum Abrufen von Metriken aus dem Testlauf wird. Dieses Problem sollte nicht im normalen Fluss der Bewertung angezeigt werden. Dieses Problem verweist auf eine Probleme mit WPR (Windows-Leistung Aufzeichnung).

Um dieses Problem zu beheben, wird die allgemeine Empfehlung sichergestellt, dass WPR kann auf das System ordnungsgemäß ausgeführt, die ADK ordnungsgemäß installiert ist und keine der Funktionen von ADK manuell aus dem System entfernt wurden. Es ist außerdem wichtig, den neuesten Grafiktreiber installiert haben.

### <a name="a-href-idtrascode-issue-analysisametric-results-analysis"></a><a href="" id="trascode-issue-analysis"></a>Metrische Ergebnisanalyse

Die Anzahl der Tests umfasst die Bewertung. Metriken für einzelne pro-Testlauf zusammengestellt werden, und behandelt werden, auf der Grundlage von pro Test als auch.

Der Name des Tests erfahren Sie mehr Benutzer über die folgenden:

1.  Input Media-format

2.  Eingabe videoauflösung

3.  Ausgabeformat Medien

4.  Die Auflösung

5.  Wenn der Test auf AC oder Batterie Power ausgeführt wurde (AC ist standardmäßig)

6.  Wenn der DXVA oder nicht DXVA Pfad decodieren verwendet wurde

7.  Wenn Hardware- oder Encoder verwendet wurde

Hier ist der typische Testname: **"VC1 1080, h. 264 720 angeschlossen in DXVA auf Hardware Encoder"**. Der Name des Tests enthält das input Videoformat – VC++-1, und die Auflösung – 1080p an. Das Ausgabeformat h. 264 und die Ausgabe Auflösung wurde 720p. Der Test wurde mit DXVA eingeschaltet und Hardware Encoder auf Stromversorgung (Netzbetrieb), ausgeführt. Die Testergebnisse werden nach Metriken gruppiert.

Als allgemeine Regel muss eine moderne Systeme in Echtzeit transcodieren für Dateiformate für bis zu 720p in Echtzeit abschließen. Als allgemeine Regel muss die Leistung für niedriger Auflösung ein- und Ausgabe als für die höhere Auflösung höher sein. Wenn das Problem **Software Codierung ist schneller als DXVA** gemeldet wird, sollte DXVA deaktiviert Tests eine bessere Leistung anzeigen.

Es wird dringend empfohlen, dass Sie befolgen Sie die Empfehlungen für das Problem **neue Leistungsdaten verfügbar ist** , und füllen Sie die Daten in die Registrierung. Dies ermöglicht die PlayTo Szenarien und erfassen Szenarien, um die besten Lösungen basierend auf der Eingabe Auflösung und Leistungsdaten in der Registrierung zu übernehmen und eine bessere Wiedergabequalität sichergestellt.

Wie bereits erwähnt, werden während des Tests ETL Spuren erfasst. Die Links zu den ETL-Ablaufverfolgungsdateien für jeden Test finden Sie auf der Seite Ergebnisse zur Bewertung. Wenn Sie einen Link auswählen, öffnet WPA (Windows Performance Analyzer), damit Sie die Codierung Sitzung im Detail analysieren können.

### <a name="the-assessment-reports-an-exit-code-of-0x80050006"></a>Die Bewertung von Berichten Exit-Code 0x80050006

Dieser Fehler tritt auf, wenn Wartungsaufgaben auf dem PC erfasst wurden, aber nicht vor der Bewertung ausführen abgeschlossen. Dies verhindert, dass die Bewertung von ausgeführt, wie Wartungsaufgaben häufig Assessment Metriken auswirken.

Um dieses Problem zu beheben, führen Sie eine der folgenden Aktionen aus:

1.  Stellen Sie sicher, dass der Computer mit dem Netzwerk verbunden ist und auf Strom ausgeführt wird. Manuelles Initiieren Sie ausstehende Wartungsaufgaben mit dem folgenden Befehl aus einer Eingabeaufforderung mit erhöhten Rechten aus:

    `rundll32.exe advapi32.dll,ProcessIdleTasks`

2.  Deaktivieren Sie reguläre und im Leerlauf Wartungsaufgaben und beenden Sie alle Wartungsaufgaben vor der Bewertung wird ausgeführt.

## <a name="related-topics"></a>Verwandte Themen


[Media transcodieren Leistung](media-transcoding-performance.md)

[Windows Assessment Toolkit](index.md)

[Bewertung](assessments.md)

 

 







