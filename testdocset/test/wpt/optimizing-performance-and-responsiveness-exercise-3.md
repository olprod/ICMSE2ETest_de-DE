---
title: "Übung 3: Grundlegendes zu Critical Path, und warten Sie Analyse"
description: "Szenarien und Aktivitäten können unerwartet verzögert werden. Beispielsweise kann beim Öffnen einer Registerkarte innerhalb von Microsoft Edge manchmal nicht länger als erwartet dauern."
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: C17DDC73-DE68-4C4A-9968-08C5FE90CC7E
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 2a4ab95b5a25b18ee782dbd54325ba2e0ff24fe5
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="exercise-3---understand-critical-path-and-wait-analysis"></a>Übung 3: Grundlegendes zu Critical Path, und warten Sie Analyse


Szenarien und Aktivitäten können unerwartet verzögert werden. Beispielsweise kann beim Öffnen einer Registerkarte innerhalb von Microsoft Edge manchmal nicht länger als erwartet dauern.

Eine Aktivität ist definiert als eine Reihe von Operationen, einige sequenzielle und einige Parallel, die auf ein Ereignis Ende von einer Startereignis fließt. Alle Start-/End Ereignispaar in eine Verfolgung können als Aktivität angezeigt werden. Der längste Pfad durch diese Reihe von Vorgängen wird als kritisch bezeichnet. Reduzieren die Dauer der alle Vorgänge auf dem kritischen Pfad direkt reduziert die Dauer der Aktivität des gesamten.

Es wird empfohlen, dass Sie identifizieren den Prozess und der Thread, der die Aktivität abgeschlossen und Abwärtskompatibilität ab dem Zeitpunkt die Aktivität abgeschlossen arbeiten. Start durch die Analyse des Threads, der die Aktivität, um zu bestimmen, wie die meisten dieser Zeit und in welchem Zustand von diesem Thread aufgewendet wurde abgeschlossen: **ausgeführt**, **ready**oder **wartet**.

Erhebliche Zeiten darauf hinzuweisen, dass direkte CPU-Auslastung auf die Dauer des kritischen Pfades beitragen. Zeit im Zustand **bereit** gibt an, dass andere Threads auf die Dauer des kritischen Pfades beitragen, indem Sie verhindern, dass einen Thread auf dem kritischen Pfad ausführen. Zeitaufwand für **Warten** Kriterien, die e/a, Zeitgeber, oder andere Threads und Prozesse auf dem kritischen Pfad für den aktuelle Thread wartete.

Jeder Thread, der den aktuellen Thread bereitet ist wahrscheinlich einen weiteren Link im kritischen Pfad und kann ebenfalls analysiert werden, bis die Dauer des kritischen Pfades berücksichtigt wird.

Alle erforderliche Informationen wird in der **CPU-Auslastung (Precise)** Diagramm und die Tabelle in **WPA**aufgezeichnet. CPU-Auslastung Ereignisse, die vom Verteiler angemeldet sind sind Kontextwechsel zugeordnet. In dieser Tabelle liegt der Schwerpunkt auf **NewThread** also Threads, die in gewechselt wurde, und jede Zeile stellt einen Kontextwechsel. Daten werden für die folgenden Ereignissequenz erfasst:

![Diagramm zum Programmkompatibilitäts-Daten Auflistung Workflows.](images/optimizingperformancelab25.png)

1.  **NewThread** ist aufgrund einer blockierenden Funktionsaufruf out gewechselt wird.

2.  **NewThread** ist bereit zur Ausführung der readying Thread vorgenommen.

3.  **NewThread** ist in gewechselt wird dadurch eine alte Thread Auslagerung.

4.  **NewThread** wird erneut abgeschaltet.

Hier sind die interessanten Spalten in der Tabelle **CPU-Auslastung (Precise)** .

| Spalte               | Details                                                                                                                                                     |
|----------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **% CPU-Verwendung**      | Die CPU-Auslastung des neuen Threads nachdem er geändert wird. Dieser Wert wird als Prozentsatz der gesamten CPU-Zeit im aktuell angezeigten Zeitraum ausgedrückt. |
| **Count**            | Die Anzahl der Kontextwechsel, die von der Zeile dargestellt werden. Dies ist immer 1 für die einzelnen Zeilen.                                                       |
| **CPU-Auslastung (ms)**   | Die CPU-Auslastung des neuen Threads nach die Option Kontext.                                                                                                   |
| **NewProcess**       | Der Vorgang des neuen Threads.                                                                                                                              |
| **NewThreadId**      | Die Thread-ID des neuen Threads.                                                                                                                            |
| **NewThreadStack**   | Der Stapel des neuen Threads, wenn es in gewechselt wird. In der Regel gibt an, was der Thread wurde gesperrt oder wartet auf.                                            |
| **READY(s)**         | Die Zeit der Thread in der Warteschlange (aufgrund von Bezugsrechts oder Blockieren der CPU).                                                                   |
| **ReadyingThreadId** | Die Thread-ID des der readying.                                                                                                                       |
| **ReadyingProcess**  | Der Prozess, der den readying Thread besitzt.                                                                                                                  |
| **ReadyThreadStack** | Der readying Thread-Stapel.                                                                                                                           |
| **ReadyTime (s)**    | Der Zeitpunkt, wann der neue Thread Scanthreads wurde.                                                                                                                   |
| **SwitchInTime(s)**  | Der Zeitpunkt, wann in der neue Thread gewechselt wurde.                                                                                                               |
| **Wartet (s)**        | Die Zeitdauer ein Thread auf eine logische oder physische Ressource gewartet. Warten beendet, wenn **NewThreadId** durch **ReadyingThreadId**signalisiert wird.               |

 

## <a name="step-1-capture-and-open-a-trace-for-a-ui-delay-problem"></a>Schritt 1: Erfassen Sie, und öffnen Sie eine nachrichtenablaufverfolgung für eine Benutzeroberfläche Verzögerung problem


In dieser Übung konzentriert sich auf einem simulierte Prozess mit einer Benutzeroberfläche nicht reagiert. Der Vorgang ist eine einfache Windows Forms-Anwendung mit einer Schaltfläche und ein Textfeld. Wenn die Schaltfläche geklickt wird, reagiert die Benutzeroberfläche für 20 Sekunden, bis das Textfeld aktualisiert wird. Sie können den kritischen Weg dieses Vorgangs analysieren.

![Screenshot der UIDelage Beispiel-Dialogfeld.](images/optimizingperformancelab26.png)

1.  Laden Sie [hier](http://download.microsoft.com/download/9/C/5/9C562A35-2E52-4CAE-A662-753486C13F4A/UIDelay.exe) **UIDelay.exe** herunter.

2.  Starten Sie **UIDelay.exe**.

3.  **WPR** aus dem Menü **Start** zu öffnen.

4.  Ändern der Tracing-Konfiguration.

    1.  Wählen Sie **selektieren der ersten Ebene** und **CPU-Auslastung**.

    2.  Wählen Sie **Allgemeine** Leistung Szenario wie.

    3.  Wählen Sie als die Detailebene **Verbose** aus.

        ![Screenshot des WPR Dialogfeld.](images/optimizingperformancelab27.png)

5.  Klicken Sie auf **Start**.

6.  Klicken Sie in **UIDelay.exe**auf die Schaltfläche **Klicken** .

    -   Warten Sie, bis das Textfeld "Fertig!" zeigt

7.  Klicken Sie in **WPR**, die Ablaufverfolgung zu speichern, und öffnen Sie es mit **WPA.**

8.  Öffnen Sie das Menü **Trace** , und wählen Sie **Konfigurieren Symbole Pfad**.

    -   Geben Sie den Pfad des Caches Symbol. Weitere Informationen zu Symbolen finden Sie unter auf der [Supportseite Symbol](https://go.microsoft.com/fwlink/?linkid=623019) auf MSDN.

9.  Öffnen Sie das Menü **Trace** , und wählen Sie **Symbole laden**.

## <a name="step-2-identify-the-delayed-ui-thread"></a>Schritt 2: Identifizieren des verzögerten Benutzeroberflächen-Threads


Vor dem kritischen Pfad Analyse ausführen, müssen Sie zuerst identifizieren Beginn der Aktivität und Beenden von Ereignissen.

1.  Hier finden Sie im Diagramm **UI Verzögerungen** **Systemaktivitäten** Knoten des **Diagramm-Explorer**.

    ![Screenshot des Diagramms Explorer Benutzeroberfläche.](images/optimizingperformancelab28.png)

2.  Drag & drop im Diagramm **Benutzeroberfläche Verzögerungen** in der Registerkarte Analyse.

3.  Suchen Sie den Prozess **UIDelay.exe** .

    1.  Die Dauer sollte etwa 20 Sekunden. Darauf hin, dass eine Verzögerung von 20 Sekunden auf den Benutzeroberflächen-Thread der **UIDelay.exe**ist aufgetreten.

    2.  Die UI-Thread-ID wird in der Spalte **Thread-Id** angezeigt. In diesem Beispiel ist es 24174. Dieser Wert wird in der Verfolgung anders lauten die auf Ihrem Computer erfassten haben. Stellen Sie sicher, dass Sie beachten Sie die Thread-ID

        ![Screenshot der Beispieldaten.](images/optimizingperformancelab29.png)

4.  Wählen Sie die gesamte **UIDelay.exe** Zeitintervall aus, mit der rechten Maustaste und vergrößern.

    ![Screenshot des Zoomoption.](images/optimizingperformancelab30.png)

Sie sollten immer in den Regionen vergrößern, den, die Sie analysieren möchten. Es reduziert den Noise von unabhängigen Aktivitäten eingeführt.

## <a name="step-3-analyze-the-ui-delay-critical-path"></a>Schritt 3: Analysieren des Benutzeroberfläche Verzögerung kritischen Weges


Nun, dass Sie über eine Analyse Startpunkt mit die Thread-ID und den Zeitstempel verfügen, können Sie beginnen die Aktivität kritischen Weg zu verstehen, die Abfolge der Ereignisse, die zu einer Verzögerung 20 Sekunden auf den Benutzeroberflächen-Thread führen.

Die **NewThreadId** für diesen Schritt ist der Thread, den Sie in Schritt2 (Thread **UIDelay.exe** Prozess 24174) identifiziert.

1.  Das **CPU-Auslastung (Precise)** Diagramm auf der Registerkarte **Analyse** hinzufügen und die **Nutzung von Prozess, Thread** Voreinstellung anwenden.

    ![Screenshot der Beispieldaten in WPA.](images/optimizingperformancelab31.png)

2.  Maustaste auf die Spaltenüberschriften, und machen Sie die Spalten **NewThreadStack**, **ReadyThreadStack**und **CPU-Auslastung (ms)** sichtbar zu.

3.  Entfernen der **bereit (us) \[Max\] ** und **wartet (us) \[Max\] ** Spalten. Die Ansicht sollte nun wie folgt aussehen.

    ![Screenshot der Beispieldaten in WPA.](images/optimizingperformancelab32.png)

4.  Suchen und erweitern Sie den **UIDelay.exe** Prozess in der Spalte **NewProcess** sowie zum Sortieren nach **wartet (us) \[Summe\] ** , indem Sie auf die Spaltenüberschrift.

5.  Suchen Sie nach der **NewThreadId** im Prozess **UIDelay.exe** und analysieren Sie der Zeitaufwand für den Status wird ausgeführt, kann jetzt oder warten.

    -   Im folgenden Beispiel finden Sie, die:

        -   Der Thread belegt 10.025 Sekunden der CPU-Zeit.

        -   Der Thread wartet darauf, dass 5.159 Sekunden.

        -   Der Thread befindet sich im Zustand bereit für eine unerheblich Zeitspanne (10 ms).

        ![Screenshot der Beispieldaten in WPA.](images/optimizingperformancelab33.png)

    **Hinweis**  
    Sie können die 10 Sekunden des CPU-Aktivität, die anhand der in Schritt 4 **CPU-Auslastung (gemessen)** Diagramm und der Prozess **UIDelay.exe** betrachten Übung 2 beschriebenen Methode analysieren.

     

6.  Erweitern Sie zum Ermitteln von für wartete der **NewThreadId** der **NewThreadId** -Gruppe, um die **NewThreadStack**anzuzeigen.

7.  Erweitern Sie ** \[Root\] ** und identifizieren Sie die Funktionsaufrufe zu wartet.

    ![Screenshot der Beispieldaten in WPA.](images/optimizingperformancelab34.png)

In diesem Beispiel wird **UIDelay.exe** Thread, der ID 24174 wartet auf die zugrunde liegende blockierenden Funktionsaufrufe 5.073 Sekunden, die beim Klicken auf die Schaltfläche Funktion ausgelöst:

-   aufgrund der Vorgänge unterhalb der Funktion **ExecuteWMICall** werden 5.021 Sekunden.

-   35 ms werden aufgrund der Vorgänge unterhalb der Funktion **PingServer** .

### <a name="step-31-look-at-the-executewmicall-code-path"></a>Schritt 3.1: Betrachtung der Pfad für den ExecuteWMICall

Wenn Sie die Aufrufliste weiter unter **ExecuteWMICall**erweitern, werden Sie feststellen, dass der Benutzeroberflächen-Thread tatsächlich 5 Sekunden aktiviert wird durch Aufrufen von **Thread.Sleep**explizit.

![Screenshot der Beispieldaten in WPA.](images/optimizingperformancelab35.png)

Überhaupt Kosten, da er direkt Reaktionsfähigkeit beeinflusst, sollte dieser Art von Verhalten vermieden werden. Wenn der Code auf Informationen wartet muss, muss lediglich asynchron auf einem getrennten Thread und eine ereignisgesteuerte-Methode verwenden.

## <a name="step-32-look-at-the-pingserver-code"></a>Schritt 3.2: Blick auf den PingServer code


Wenn Sie die Aufrufliste Weitere unter **PingServer**erweitern, werden Sie feststellen, dass der Benutzeroberflächen-Thread e/a-abhängig ist, wie er **Ping** -Befehle über das Netzwerk sendet.

![Screenshot der Beispieldaten in WPA.](images/optimizingperformancelab36.png)

Während die Verzögerung sehr gering ist (35 in Millisekunden), sollte ein UI-Thread vermieden werden. Beachten Sie, dass die durchschnittliche Person Benutzeroberfläche größer als 100 ms bemerken beibehalten. Dieser Vorgang kann die gesamte Aktivität verstrichene Zeit über 100 ms, wodurch Benutzer müssen eine falsche Wahrnehmung der Reaktionsfähigkeit erhöhen.

Diese Vorgänge sollten asynchron in einem getrennten Thread erfolgen und die Benutzeroberfläche nicht blockiert.

 

 






