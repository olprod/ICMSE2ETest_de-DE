---
title: "Analysieren der Ergebnisse auf ein anderes Gerät"
description: "Analysieren Sie die Ergebnisse auf ein anderes Gerät"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 2775a4c2-6eb5-467c-b7b3-35529930cc16
ms.prod: W10
ms.mktglfcycl: plan
ms.sitesec: msdn
ms.openlocfilehash: c119d4c54cea3c0f213a19e5006921842b3c24cc
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="analyze-results-on-another-device"></a>Analysieren der Ergebnisse auf ein anderes Gerät


Sie können führen Sie eine Bewertung Spuren auf einem PC zu erfassen und Analysieren der Daten auf einem anderen PC oder zu einem späteren Zeitpunkt. Möglicherweise möchten Sie Spuren ohne Analyse zu erfassen:

-   Führen Sie auf einem PC mit mehr Arbeitsspeicher oder ein schnellerer Prozessor Analyse

-   Analyse, um die Zeit für andere hohe Priorität freizugeben Verzögerung verwendet, der Computer

-   Führen Sie auf einem PC an, die bereits konfiguriert Symbole

-   Erneut analysieren von Bewertungsdaten später mit aktualisierten diagnostic Module oder Symbole

-   Erfassen von Daten auf allen Geräten, aber nur diejenigen, die bestimmte Kriterien erfüllen analysieren

**Ablaufverfolgungsdateien erfassen, ohne Analyse**

1.  Wählen Sie einen Auftrag oder Assessment ausführen.

2.  Wählen Sie auf dem Bildschirm **Konfigurieren Auftrag** **nur Spuren erfassen**.

3.  Ausführung des Auftrags.

4.  Ablaufverfolgungsdateien für die Bewertung gespeichert werden sollen *USERPROFILE%\\Dokumente\\Assessment Ergebnisse*.

    **Hinweis**  
    Sammeln von Trace-Dateien ohne Analyse ist nicht verfügbar für alle Aufträge und Bewertung.

     

## <a name="run-analysis-on-another-device"></a>Führen Sie die Analyse auf ein anderes Gerät


Sie können auf dem PC Symbole laden, wo Sie Ablaufverfolgungsdateien analysieren möchten. Weitere Informationen finden Sie unter [Symbol Unterstützung](../wpt/symbol-support.md).

**Zum Ausführen der Analyse auf Ablaufverfolgungsdateien WAC verwenden**

1.  Klicken Sie in der Windows-Assessment-Konsole auf **Optionen**, und klicken Sie dann auf **Open Ergebnisse** , um alle Auftragsergebnisse angezeigt, die für die Anzeige verfügbar sind.

2.  Wählen Sie im Fenster **Wählen Sie Ergebnisse** die Ergebnisse, die Sie analysieren möchten.

3.  Klicken Sie auf **Öffnen** , um die Ergebnisse in der Detailansicht zu öffnen.

    Die Ergebnisse die **Analyse abgeschlossen** Zeile zeigt **False**.

4.  Klicken Sie auf **Analysieren**.

    Wenn Sie mehrere Ergebnisse geöffnet, die analysiert werden kann haben, können Sie, welche analysieren auswählen.

## <a name="related-topics"></a>Verwandte Themen


[Packen Sie einen Auftrag aus, und führen Sie es auf einem anderen computer](package-a-job-and-run-it-on-another-computer.md)

[Importergebnisse](import-results.md)

 

 







