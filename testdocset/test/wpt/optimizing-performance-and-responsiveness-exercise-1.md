---
title: "Übung 1 – schnellen mit dem Assessment Toolkit Start bewerten"
description: "Startzeit ist eine allgemeine Richtlinie, die häufig zum Messen der Leistung von Windows verwendet wird. Während der Lebensdauer eines Systems können länger Start des Servers ein Symbol von Systemproblemen wie ineffiziente Konfiguration, Gerätekonflikte und Schadsoftware sein."
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: C5CD3A7D-5306-44A5-B2C3-E5D3BC42DA56
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: f4d0da2b2c41aece811f73ae4840154acbba20a3
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="exercise-1---evaluate-fast-startup-using-the-assessment-toolkit"></a>Übung 1 – schnellen mit dem Assessment Toolkit Start bewerten


Startzeit ist eine allgemeine Richtlinie, die häufig zum Messen der Leistung von Windows verwendet wird. Während der Lebensdauer eines Systems können länger Boot wie oft ein Indikator von Systemproblemen wie ineffiziente Konfiguration, Gerätekonflikte und Schadsoftware sein.

## <a name="step-1-collect-data-using-the-windows-assessment-tookit"></a>Schritt 1: Sammeln von Daten mithilfe der Windows-Assessment-Toolkit


Das Windows Assessment Toolkit enthält einen Test, um die Fast Startzeit messen. Sie können diese Bewertung um zu verstehen, dass die Auswirkung Treiber, Geräte und die Teiler Software auf die Fast Startzeit verwenden. Fast Startzeit kann durch Prozesse und Dienste, die zu starten, Prozesse und Dienste, die im Hintergrund ausgeführt oder Geräte initialisieren verwendeten Ressourcen im Arbeitsspeicher geladen werden, beeinträchtigt werden.

1.  Öffnen Sie **Windows-Assessment-Konsole (WAC)** im Menü **Start** .

2.  Öffnen Sie das Menü **Optionen** und wählen Sie **Neuer Auftrag...** ![Screenshot der WAC-Startmenü.](images/optimizingperformancelab2.png)

    1.  Geben Sie **FastStartupTest** als Name des Auftrags.

    2.  Wählen Sie **Erstellen eines benutzerdefiniertes Auftrags.**

3.  Klicken Sie auf **Hinzufügen Bewertung.**

    -   Fügen Sie die **Start-Leistung (Fast Start)** Bewertung, indem Sie auf das Symbol "+" hinzu.

4.  Klicken Sie auf die neu hinzugefügte **Start-Leistung (Fast Start)** zur Bewertung die Testkonfiguration eingeben.

5.  **Empfohlene Verwendung** deaktivieren Sie, und wählen Sie **Aktivieren Hiberfile Diagnose** für die Konfiguration.

    -   **Hiberfile Diagnose aktivieren** können Sie den Inhalt der Hiberfile analysieren und ermitteln Sie die Arbeitsspeicherseiten, die an seine Größe beteiligen.

6.  Sie haben zwei Möglichkeiten:

    1.  **Paket** den Auftrag, um erstellen Sie einen Ordner mit der Testressourcen und kopieren Sie es auf einem anderen System zu testen. (Klicken Sie auf das **Paket...** Schaltfläche in der unteren rechten Ecke auf diese Option auswählen.)

    2.  **Ausführen** des Auftrags direkt auf dem System an. (Klicken Sie auf die Schaltfläche **Ausführen** , in der unteren rechten Ecke auf diese Option auswählen.)

        -   Dies startet das System, um eine Ablaufverfolgung zu erfassen.

        -   Bei diesem Test kann 30 Minuten dauern.

    Die Option **Ausführen** soll.

    ![Screenshot der Option in WAC ausführen.](images/optimizingperformancelab3.png)

## <a name="step-2-visualize-the-assessment-results-using-wac"></a>Schritt 2: Visualisieren der Assessment-Ergebnisse, die mit WAC


Nach Abschluss die Ausführung Assessment können öffnen Sie den resultierenden XML-Bericht mit **WAC** und starten Sie die Zeiten **Fast Start** auswerten.

In diesem Schritt werden zwei XML-Berichten verwendet:

-   **Geplante Bericht** (**FastStartup\_Baseline.xml**): der Baseline-Bericht ist ein zuvor generierte XML-Bericht, die heruntergeladen werden kann [hier](http://download.microsoft.com/download/3/6/F/36FDC105-5ECC-4C8A-98E4-385B940F74B5/FastStartup_Baseline.xml).

    Es wurde durch Ausführen von **Fast Start** Bewertung für clean Windows Retail-Abbilder mit eine umfassende Auswahl an Treiber generiert. Ein Basisplan können Sie das optimale Szenario für ein System zu verstehen, ohne alle 3. Partei apps hinzugefügten.

-   **Lokale Bericht**: Hierbei handelt es sich um den Bericht, den Sie in Schritt 1 erstellt. Das Delta zwischen der Baselinebericht und in diesem Bericht können Sie die Auswirkungen quantifiziert, die apps hinzugefügt haben, klicken Sie auf Start des Servers.

1.  Klicken Sie im **WAC**, in der oberen rechten Ecke öffnen Sie das Menü **Optionen** , und wählen Sie **Ergebnisse zu öffnen**.

    -   Sie können auch auf der Tastatur **STRG + R** drücken.

2.  Klicken Sie auf **Durchsuchen...** Schaltfläche, und navigieren Sie zu dem Ordner, in dem Sie die beiden XML-Berichte gespeichert.

3.  Wählen Sie beide **FastStartup\_Baseline.xml** und Ihrer **lokalen Bericht** zur gleichen Zeit, und klicken Sie auf **Öffnen**.

    Die zwei Ergebnisse Side-by-Side in der Windows-Assessment-Konsole zu öffnen. In der Konsole sollte wie folgt aussehen:

![Beispiel-Screenshot des Assessment-Ergebnisse.](images/optimizingperformancelab4.png)

**Hinweis**  
Da auf einem anderen System, von dem verwendet, um die **lokale Berichte** dargestellt in die Screenshots in dieser Übung Erstellen Ihres **lokalen Bericht** generiert wurde, werden die spezifische in die Screenshots angezeigten Einträge wahrscheinlich diejenigen unterscheiden sich von, die auf Ihrem Computer angezeigt.

 

## <a name="step-3-review-the-fast-startup-report"></a>Schritt 3: Überprüfen Sie den Bericht Fast Start


Im Abschnitt mit den Assessment enthält die Daten, die Sie verwenden möchten, zu verstehen, wie ein System ausgeführt wird und Probleme zu identifizieren. Die meisten metrischen Werte sind Zahlen, die Sie verwenden können, um mit anderen Metriken oder Computern verglichen werden soll.

| Phase                                      | Beschreibung                                                                                                                                                               |
|--------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Herunterfahren Dauer (in Sekunden)**            | Die Zeit zum Herunterfahren des Computers. Sie können diesen Knoten, um zusätzliche Metriken für den tieferen Verständnis und Untersuchung verfügbar machen erweitern.                               |
| **BIOS Initialisierung Dauer (in Sekunden)** | Die Zeit der BIOS nicht initialisiert werden. Die Bewertung bietet keine Analyse und-Wartung Informationen dieser Metrik.                                                |
| **Insgesamt Boot (Sekunden)**                   | Die Zeit des Computers zum Starten nach Abschluss die BIOS-Phase. Sie können diesen Knoten, um zusätzliche Metriken für den tieferen Verständnis und Untersuchung verfügbar machen erweitern. |

 

**Tipp für Benutzer:**

**Bewertung** oft Arbeitslasten oder Szenarien mehrmals ausgeführt. Zusammenfassend an alle diese Textläufe als "Iteration", und die Werte, die gesammelt werden auf mehrere Iterationen Durchschnitt. **Fast Start** verfügt beispielsweise über drei Iterationen standardmäßig. Zum Anzeigen der einzelnen Iteration Werte mit der rechten Maustaste in der oberen Spaltenüberschrift des Namens des Computers, und wählen Sie dann **Iterationen anzeigen**.

![Beispiel-Screenshot des Menüoption Iterationen anzeigen.](images/optimizingperformancelab5.png)

Das Start-Leistung (Fast Start) Assessment bietet Boot Metriken in einer Reihe von Phasen und Komponenten.

1.  Hier finden Sie in der **WAC**der **insgesamt Boot \[BIOS ausschließen\] Dauer (in Sekunden)** Metrik, und Vergleichen der Basislinie und lokale Ergebnisse. Möglicherweise eine große angezeigt (d. h. größer als 18 Sekunden) Regressionsformel Zeit zwischen den beiden.

2.  Klicken Sie auf den Doppelpfeil neben dieser Metrik die untergeordneten Leistungsmetriken enthalten.

    -   **Main Pfad Boot Dauer**: Zeigt den Start von Windows annimmt, vom Ende der **BIOS-Initialisierung** wieder hochfahren, wenn der Desktop für den Benutzer sichtbar ist.

    -   **Beitrag weiter Dauer**: Zeigt die Zeitfenster annimmt, alle Startaufgaben ausführen, nachdem der Desktop angezeigt wurde.

    Die anderen metrischen Bereiche (**Ressourcenverbrauch** und **Details der Resume-Prozess**) CPU und die Datenträgertypen Verwendungsdaten enthalten und werden nicht in diesem Handbuch untersucht werden.

    ![Beispiel-Screenshot des Boot Leistungsergebnisse Bewertung.](images/optimizingperformancelab6.png)

## <a name="a-href-idstep-4--examine-the-resume-devices-duration-astep-4-examine-the-resume-devices-duration"></a><a href="" id="step-4--examine-the-resume-devices-duration-"></a>Schritt 4: Untersuchen Sie, die Dauer der Resume-Geräte


Gerätetreiber möglicherweise eine Datenquelle Boot verzögert. Treiber identifiziert, die Probleme, Drilldown in die **Dauer der Resume-Geräte** Metriken Probleme gefunden haben.

1.  Klicken Sie auf den Doppelpfeil neben die **Main Pfad Boot Dauer** , um ihn zu erweitern.

2.  Suchen Sie nach der **Dauer der Resume-Geräte** Metrik, erweitern Sie den Knoten, indem Sie auf den Doppelpfeil und zeigen Sie dann die untergeordneten Metriken unter der **Prozesse pro Phase** Metrik.

3.  Mit der rechten Maustaste der Spaltenüberschrift Computer Name, der Spalte Ergebnisse Test, und wählen Sie dann **Absteigend sortieren**. Dadurch wird die Daten sortiert, so, dass im oberen Bereich die größten Zahlen sind. Dadurch können Sie auf die Aufgaben konzentrieren, die die längste Dauer aufweisen.

4.  Jede Zeile darstellt, die Zeitdauer, die ein Gerät wieder hochfahren in einer aktiven versetzt wurden.

    ![Beispiel-Screenshot des Assessment-Ergebnisse.](images/optimizingperformancelab7.png)

## <a name="step-5-determine-the-hiberfile-size"></a>Schritt 5: Ermitteln der Hiberfile Größe


1.  Klicken Sie auf den Doppelpfeil neben die **Hiberfile lesen Dauer** , um ihn zu erweitern.

    Die **Größe der Hiberfile** Metrik stellt die Menge der Daten lesen vom Datenträger im Systemkontext durch den Ruhezustand Stapel wiederherstellen.

    -   Je größer der Größe der Datei, die mehr Zeit benötigt für das System zu starten. Die Größe der Datei wird direkt von Speicherverwendung von Diensten und Treibern betroffen sind.

    -   Um eine Schätzung des Datenträgers lesen Durchsatz (in MB/s) zu erhalten, können Sie durch die Metrik **Hiberfile lesen Dauer** **Hiberfile Größe** dividieren. Ist eine erhebliche Abweichung zwischen diesem Durchsatz und die Laufwerkangabe beginnt, möglicherweise ein Problem mit der Treiber oder der Speicher BIOS-Routinen lesen.

2.  Erweitern Sie, um den Inhalt der Hiberfile zu analysieren und zu bestimmen, welche Softwarekomponenten auf seine Größe beitragen, die **Hiberfile Diagnose** Metrik. Zwei Arten von Arbeitsspeicher Beitrag zu der Größe des Hiberfile:

    -   Treiber nicht ausgelagerten Speicher-pool

    -   Prozess Arbeitsseiten

![Beispiel-Screenshot des Assessment-Ergebnisse.](images/optimizingperformancelab8.png)

## <a name="step-6-examine-the-post-onoff-duration"></a>Schritt 6: Überprüfen Sie den Post ein-/ausschalten Dauer


Wert für die **Dauer der Post-weiter** stellt die benötigte Zeit für den Computer Leerlauf erreichen, nachdem der Benutzer der Desktop angezeigt wird. Während dieser Zeit kann Benutzer Reaktionsfähigkeit betroffen sein, da Systemstart im Hintergrund abgeschlossen wird. **Beitrag weiter** Abschluss der nach 5 Sekunden niedrige Priorität CPU und Speicherplatzverwendung gesammelt werden.

1.  Erweitern Sie den Knoten **Beitrag weiter Dauer (in Millisekunden)** .

2.  Erweitern Sie zum Anzeigen einer untergeordneten Tabelle mit Metriken auf den einzelnen apps und Diensten, die CPU und Speicher während dieser Phase verwenden, **Prozesse pro Phase** .

3.  Mit der rechten Maustaste in der Tabelle der letzten Spaltenüberschrift, und wählen Sie dann auf **Absteigend sortieren**.

![Beispiel-Screenshot des Assessment-Ergebnisse.](images/optimizingperformancelab9.png)

Sie können jetzt Prozesse identifizieren, die in der Phasendauer beitragen. Mehr Ressourcen nutzt, desto wahrscheinlicher wirkt sich dies auf die Phasendauer und weiter untersucht werden sollte.

## <a name="step-7-open-fast-startup-trace-with-wpa"></a>Schritt 7: Open schnellen Start Trace WPA


Die **Fast Start** Bewertung generiert drei Arten von Iterationen Spuren:

| Iteration-Typ | Beschreibung                                                                                                                                                                                          |
|----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Schulung       | Die Bewertung startet das System neu sechs Mal dafür sorgen, dass alle Beteiligten des Startvorgangs Betriebssystemkomponenten optimiert sind (Prefetcher, Superfetch usw.).                                           |
| Zeitpunkt         | Diese Spuren (gesammelt) dienen zum Berechnen der durchschnittlichen Messung im XML-Bericht angezeigt. Die Standardanzahl zulässiger Iterationen drei ist, aber es sind jedoch die Bewertung Konfiguration angepasst. |
| Analysis       | Eine einzelne Verfolgung werden erfasst, die detaillierte Ereignisse und Stapel enthält, um die Betrachtung der Sequenzierung Untersuchung Leistungsprobleme zulassen. Die Ablaufverfolgung ist umfangreicher.                                  |

 

Gehen folgendermaßen Sie vor, um die Spuren generiert, die für die Bewertung zu öffnen:

1.  Klicken Sie auf die Zelle Bericht Tabelle.

    Rechte Bereich in der **WAC** -Benutzeroberfläche aktualisiert und zeigt Links zu den von der Bewertung erfasst ETL-Ablaufverfolgungsprotokollen.

    ![Beispiel-Screenshot der Ablaufverfolgungsergebnisse von der Assessement generiert.](images/optimizingperformancelab10.png)

2.  Klicken Sie auf den Link **Trace Analyse** .

    **WPA** wird Trace automatisch geöffnet, sodass Sie Ihre Untersuchungen beginnen können. Übung 2 dieses Handbuchs führt Sie durch einige Analysis-Methoden.

 

 






