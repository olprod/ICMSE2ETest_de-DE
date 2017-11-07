---
title: "Übung 2 – schnellen Start von Windows Performance Toolkit bewerten"
description: "Während die Bewertung Fast Start eine einfache Möglichkeit zum Abrufen von Maßangaben in einem leicht lesbaren Bericht befindet, müssen Sie die ADK installiert werden einige Zeit ausgeführt werden sollen."
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 85DE99FB-3E14-4A41-BE0A-8EEEBBFD5949
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 4234a44fe1bd49d8639b6cc58811d33d25f0a98f
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="exercise-2---evaluate-fast-startup-using-windows-performance-toolkit"></a>Übung 2: Bewerten der schnellen Start mithilfe von Windows Performance Toolkit


Während die **Fast Start** Bewertung eine einfache Möglichkeit zum Abrufen von Maßangaben in einem leicht lesbaren Bericht ist, benötigen Sie ADK, installiert werden einige Zeit ausgeführt werden sollen. Es ist möglich, einen mit dem Tool **Windows Performance Aufzeichnung (WPR)** **Fast Start** Trace schnell zu erfassen.

## <a name="step-1-open-fast-startup-trace-using-wpa"></a>Schritt 1: Open Fast Start Trace mit WPA


1.  Öffnen Sie **Windows Performance Aufzeichnung (WPR)** aus dem Menü **Start**

2.  Ändern der Tracing-Konfiguration.

    1.  Wählen Sie aus der **Ersten Ebene Ursachenanalyse** und **CPU-Auslastung** -Anbieter.

    2.  Ändern Sie die **Leistung Szenario** in **Fast Start**.

    3.  Ändern Sie die **Anzahl von Iterationsschritten** auf 1, um ein einzelnes Trace zu erfassen.

        ![Screenshot der WPR Startmenü.](images/optimizingperformancelab11.png)

3.  Klicken Sie auf **Start**.

4.  Geben Sie einen Pfad zum Speichern des resultierenden Trace, und klicken auf **Speichern**.

    -   Dadurch wird das System neu starten, um zu erfassen und speichern Sie die Ablaufverfolgung erzwungen.

5.  Warten Sie nach dem Neustart des Systems 5 Minuten für die Überwachung auf Fertig stellen.

Sie haben nun eine Verfolgung, die mit **Windows Performance Analyzer (WPA)**analysiert werden kann.

## <a name="a-href-idstep-2---open-fast-startup-trace-using-wpaastep-2-open-fast-startup-trace-using-wpa"></a><a href="" id="step-2---open-fast-startup-trace-using-wpa"></a>Schritt 2: Open Fast Start Trace WPA verwenden


1.  Öffnen Sie **Windows Performance Analyzer (WPA)** über das Startmenü.

2.  Öffnen Sie im Menü **Datei** die Ablaufverfolgung, die Sie in Schritt 1 erstellt haben.

3.  Öffnen Sie im Menü **Profile** , und klicken Sie auf **Übernehmen...**

    1.  Klicken Sie auf **Durchsuchen Katalog...**

    2.  Wählen Sie **FastStartup.wpaprofile**aus.

    3.  Klicken Sie auf **geöffnet.**

Sie haben nun ein Profil Visualisierung der verfolgen, um einige häufig verwendete Diagramme (CPU, Datenträger usw.) abrufen angewendet.

## <a name="step-3-visualize-the-activity-timeline"></a>Schritt 3: Visualisieren der Zeitachse Aktivität


1.  Sehen Sie sich die **Bereiche von Interesse** Grafik in der Registerkarte **Analyse Tiefe**

    -   Diese Ansicht bietet eine Zeitachse Übersicht über alle in Übung 1 erwähnten **Fast zum Starten des** Zeitrahmens.

        ![Screenshot der Beispieldaten Übersicht über die Zeitachse angezeigt.](images/optimizingperformancelab12.png)

2.  Beim Bewegen der Maus über eine Region Leiste bewirkt, dass ein Popup-Fenster angezeigt werden sollen, und finden Sie weitere Informationen für die Region selbst.

    -   Wenn Sie die Maus über die **Main Startpfad** Region eingefügt, sehen Sie die Dauer. Im folgenden Beispiel dauert es 13,6 Sekunden.

        ![Ausführliche Informationen zur Region-Daten Screenshot des Popup-Fenster angezeigt.](images/optimizingperformancelab13.png)

Dauern Sie Navigieren durch die Struktur Regionen, und sehen Sie sich alle Zeitrahmens vertraut mit die Zeit.

Die Dauer **Explorer** initialisiert und Fertig stellen, ist der Zeitaufwand zum Erstellen des Windows-Desktops und für den Benutzer sichtbar zu machen. Diese Phase (und alles, was geschieht nach, als **ein-/ausschalten buchen**bezeichnet) von Prozessen, die beim Systemstart gestartet beeinträchtigt werden kann.

Wählen Sie ein Intervall von 90 zweiten beginnend am Anfang des Explorer-Initialisierung und vergrößern.

![Screenshot des Beispiel Datenansicht im WPA.](images/optimizingperformancelab14.png)![Screenshot des Beispiel-Datenansicht in WPA mit Zoomoption.](images/optimizingperformancelab15.png)

Unterhalb des Diagramms **Regionen von Interesse** sind zwei andere nützliche Diagramme: **CPU-Auslastung (gemessen wird)** und die **Datenträgerverwendung**. Sie werden zum Auswerten der Auswirkungen, das die Software laden vorab für Ressourcenverbrauch **ein-/ausschalten Posten** und Reaktionsfähigkeit verfügt verwendet werden.

Hoher CPU-Auslastung durch Anwendungen und Dienste kann benutzerfreundlich, beispielsweise nicht reagierenden Benutzeroberfläche oder Video- und Probleme beitragen. Wenn ein einzelner Prozess zu viel CPU verwendet, können andere Prozesse verzögert werden, da diese für Systemressourcen konkurrieren müssen.

Wenn ein Thread Speicherressourcen verwendet wird, können sie die Dauer der Aktivität erhöhen. Bei mehreren Threads für die Verwendung des Speichers konkurrieren, sucht die resultierende zufällige Festplatten stellen Verzögerungen wichtiger.

## <a name="step-4-analyze-process-cpu-usage"></a>Schritt 4: Analysieren der Prozess CPU-Auslastung


Um evaluieren möchten, wie viel CPU-Zeit von einem Prozess verwendet wird, im Fokus im Diagramms **CPU-Auslastung (gemessen wird)** . Die Daten, die in der **CPU-Auslastung (abgetastete)** Diagramm anzeigt stellt Beispiele der CPU-Aktivität getroffen bei regulären 1 ms sampling Intervallen. Jede Zeile in der Tabelle stellt ein einzelnes Beispiel.

Eine beliebige CPU-Aktivität, die zwischen Beispiele auftritt, wird durch diese Samplingmethode nicht aufgezeichnet werden. Aus diesem Grund werden Aktivitäten für sehr kurze Zeit wie Interrupts nicht auch im Diagramm **CPU-Sampling** dargestellt.

Überprüfen Sie die CPU-Auslastung für die einzelnen Prozesse, die Prozesse zu identifizieren, die die höchste CPU-Auslastung (**Gewicht** und **% Gewicht**) haben. Zu diesem Zweck führen Sie einen Bildlauf nach unten zu dem Diagramm **CPU-Auslastung (gemessen)**. Zeigen Sie auf der linken Seite der Liste der Prozesse. Jeder aktiven Prozess, der auf der linken zeigt das Diagramm aktiviert ist.

![Screenshot des Beispiels CPU-Auslastung der Daten.](images/optimizingperformancelab16.png)

**Tipp:**

Bei Verwendung von **WPA** Diagramme können Sie die Ansicht, um das Diagramm und die Tabelle anzuzeigen ändern. Sie können die **Maximieren** -Schaltfläche, um die andere Diagramme angezeigt, auf der Registerkarte **Analyse** Ausblenden klicken.

![Schaltfläche in WPA Screenshot von zu maximieren.](images/optimizingperformancelab17.png)

In diesem Beispiel werden **ImageSHELLY.exe** 12.4 Sekunden der CPU-Zeit über das Intervall von 90 Sekunden derzeit analysiert genutzt. Da die CPU auf dem System zwei Kerne besitzt, stellt dies einen relativen Prozentsatz der Nutzung von 6,9 %.

Mithilfe dieser Informationen können Sie untersuchen den bestimmten Prozess, der diese CPU-Auslastung verursacht oder weiterleiten, diese Angaben für dem Entwickler, der der Prozess besitzt.

Sie können zusätzliche Spalten zum Extrahieren von Informationen (rechte Maustaste auf die Tabellenspaltenüberschriften) hinzufügen:

-   **Thread-ID**: Bezeichner des Threads verursacht CPU-Auslastung

-   **Stapel**: Stapel, das den Codepfade erläutert und Funktionen, die CPU-Auslastung verursachen aufrufen

![Screenshot, der zeigt wie Ihre Ergebnisse weitere Spalten hinzugefügt. ](images/optimizingperformancelab18.png)

Im obigen Beispiel ist nur ein Großteil der CPU-Auslastung innerhalb des Prozesses **ImageSHELLY.exe** verursacht Thread: Thread 2612, mit der CPU-Aktivität 10.77 Sekunden.

Stapel zeigt, dass diese Aktivität aus dem Modul **ImageSTACEY.dll** stammt.

## <a name="step-5-analyze-process-disk-usage"></a>Schritt 5: Analysieren der Prozess die Datenträgerverwendung


Um evaluieren möchten, wie viel Datenträgerbandbreite von einem Prozess verwendet wird, Schwerpunkt liegt auf die **Datenträgerverwendung** Diagramm.

![Screenshot des WPA-Beispieldaten.](images/optimizingperformancelab19.png)

Die Spalten von Interesse sind:

-   **PRI**: Priorität des Datenträgers e/a. Die drei möglichen Prioritätsebenen sind: normal, Niedrig und sehr gering.

-   **E/a-Type**: Typ, der die e/a. Die drei möglichen e/a-Typen sind: Lesen und schreiben sowie die zu leeren.

-   **Prozess**: Bezeichner des Prozesses, der der Datenträger-e/a erstellt.

-   **Pfad-Struktur**: Struktur, die die Speicherorte der Dateien auf die von der e/a zugegriffen darstellt.

-   **Größe**: Größe (in Bytes) der e/a.

-   **Datenträgerdienst Zeit**: Anteil der Zeit, die für den Datenträger, um die e/a-service.

-   **E/a-Zeit**: Menge der Zeit, die e/a in der Windows-e/a-Warteschlange.

    -   **E/a-Zeit** ist immer länger als **Dienst Zeit** , da eine e/a Warteschlange abgelegt werden können, wenn es Datenträger Konflikte oder wenn ein e/a-Verteiler mit einer höheren Priorität zuerst erledigt werden muss.

Fügen Sie diese Spalten hinzu, und ordnen Sie diese, um diese Ansicht abzurufen:

![Screenshot der Beispieldaten mit bestimmten Spalten gefiltert.](images/optimizingperformancelab20.png)

**POST ein-/ausschalten** berücksichtigt nur Konto normaler Priorität e/as. Überprüfen Sie die Informationen zu diesen Lesevorgänge gemäß den Prozess. Lesevorgänge normalerweise Konto für mehr Datenträger Access Zeit als als große Datenmengen auf Start Schreibvorgänge, vom Datenträger gelesen werden muss, um die Prozesse und die Dienste zu starten.

1.  Klicken Sie auf die Farbe Markierungen neben den **Pri**: sehr niedrig und **Pri**: Niedrig Datenreihe, sodass nur die normale Priorität e/a im Diagramm angezeigt werden.

    ![Screenshot des Beispiel-Grafik, die sehr niedrige datennutzungs-anzeigt.](images/optimizingperformancelab21.png)

2.  Erweitern Sie in der Tabellenansicht die **normale** Priorität Zeile ein.

3.  In der Tabellenansicht erweitern Sie die Zeilen für **Schreiben**, **Lesen**und **zu leeren**, und klicken Sie dann auf die Überschrift der Spalte **Größe** der Inhalt in absteigender Reihenfolge sortiert.

    Der Bildschirm sollte etwa folgendermaßen aussehen:

    ![Screenshot des Beispielergebnisse Daten.](images/optimizingperformancelab22.png)

    Im vorstehende Beispiel wird Folgendes veranschaulicht:

    1.  152 MB der Daten wurde vom Datenträger mit normaler Priorität lesen.

    2.  129 MB der Daten wurde mit normaler Priorität auf den Datenträger geschrieben.

        -   Die handelt es sich hauptsächlich auf Datenträger schreibt die aufgezeichnete ETL-Ablaufverfolgungsdatei auf Speicher beibehalten werden.

4.  Erweitern Sie in der Tabellenansicht die **Lesetyp e/a** -Zeile ein.

    -   Sie können sollte nun die Prozesse angezeigt, die die größte Lese-Datenträger-e/a während **ein-/ausschalten buchen**verursacht.

5.  Die drei Prozesse, die zur Lesevorgänge beitragen und die keine Windows-Komponenten, zu identifizieren.

    ![Screenshot des Beispielergebnisse Daten.](images/optimizingperformancelab23.png)

6.  In der Tabellenansicht erweitern Sie die Zeile **Pfad Struktur** für **ImageSTUART.exe**und zum Navigieren durch.

    ![Screenshot des Beispielergebnisse Daten.](images/optimizingperformancelab24.png)

Im vorstehenden Beispiel **ImageSTUART.exe** liest 13,5 MB der Daten von der Festplatte, wenn während der **ein-/ausschalten buchen**gestartet, und die meisten der Zugriffe werden beim Lesen der DLL-Komponenten im Ordner **Program Files** vorgenommen.

Mithilfe dieser Informationen sollten Softwareentwickler seiner Komponenten und Prozesse zu identifizieren, und bestimmen, ob die Komponentengröße reduziert werden kann, oder wenn der Code Startpfad optimiert werden kann, um die Menge der Daten lesen vom Datenträger zu minimieren.

Diese Daten können auch die 3. Partei Prozesse identifizieren, die beim Systemstart gestartet und hohe Datenträgerverwendung beeinträchtigt. Wenn ein Vorgang für die Datenträger Konflikte Einführung werden angezeigt wird, kann dann aus dem Bild entfernt oder einfach nicht beim Systemstart gestartet.

 

 






