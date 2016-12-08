---
title: "Übung 4: Verwenden Sie MXA zum Analysieren der Audio-Fehler"
description: "In dieser Übungseinheit werden Sie audio Probleme analysieren."
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 79BE72BB-708D-4EA9-A0F0-59D93016A7C4
ms.openlocfilehash: 5dee21ca698e4bcb1f2c588dfdf8fecee7801f50
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="exercise-4---use-mxa-to-analyze-audio-glitches"></a>Übung 4: Verwenden Sie MXA zum Analysieren der Audio-Fehler


In dieser Übungseinheit werden Sie audio Probleme analysieren. Audio-Fehler werden häufig durch eines der folgenden Probleme verursacht werden:

-   Eine zurückgestellt Prozedur-Anruf (DPC) oder ein unterbrechen Service routinemäßige (ISR), die mehr als 1 Millisekunde ausgeführt wird.

-   Ein Treiber oder Kernel Thread, der zur Versendung Ebene 1 Millisekunde oder mehr ausgeführt wird.

-   Daten können nicht vom Datenträger gelesen werden, oder das Netzwerk nicht schnell genug ist aufgrund von hohe Auslastung der Datenträger oder Netzwerk.

-   Der Decoder Hardware- oder kann nicht decodieren und verarbeiten das Stream-Objekt schneller als in Echtzeit.

## <a name="step-1-open-the-trace-in-mxa-and-drag-the-pertinent-datasets-into-panels"></a>Schritt 1: Öffnen Sie die Ablaufverfolgung in MXA, und ziehen Sie die relevanten Datasets in Bereiche


1.  Installieren Sie die **Medienfunktionen Analyzer (MXA)** die heruntergeladen werden kann [hier](https://go.microsoft.com/fwlink/?linkid=525711).

2.  Mit der rechten Maustaste auf **das Startmenü** , und klicken Sie auf **der Befehlszeile (Admin)**.

3.  Navigieren Sie zu dem Ordner, in dem Sie **MXA**installiert.

4.  Legen Sie die Pfade **MXA** Symbol auf Ihrem PC.

5.  Laden Sie **AudioGlitches\_ThreadsAtDispatchLevel.etl** [hier](http://download.microsoft.com/download/9/6/0/96000C33-FB05-44B7-96A1-9C0CF5EE865B/AudioGlitches_ThreadsAtDispatchLevel.etl).

6.  Öffnen der **AudioGlitches\_ThreadsAtDispatchLevel.etl** Ablaufverfolgungsdatei, indem Sie den folgenden Befehl eingeben:

    ``` syntax
    xa.exe -i <AudioGlitches_ThreadsAtDispatchLevel.etl location>\AudioGlitches_ThreadsAtDispatchLevel.etl
    ```

    Wenn Sie heruntergeladen haben beispielsweise **AudioGlitches\_ThreadsAtDispatchLevel.etl** c:\\Leistung\\Media, geben Sie den folgenden Befehl:

    ``` syntax
    xa.exe -i C:\Performance\Media\AudioGlitches_ThreadsAtDispatchLevel.etl
    ```

7.  Drücken Sie auf dem Begrüßungsbildschirm **MXA** die **Symbole ausschalten** Symbol Lookup deaktivieren.

    ![Screenshot von Medien Erfahrung Analyzer (MXA), Optionsfeld Symbole.](images/optimizingwindowsdeviceslab4.png)

8.  Nachdem der Trace geladen ist, schließen Sie open Bereiche, die in der Mitte der Anwendung angezeigt werden, durch Drücken das kleine X neben dem Namen der einzelnen Bereiche auf.

9.  3 neue Bereiche hinzufügen. Klicken Sie auf **Ansicht** &gt; **Neuer Bereich** , oder drücken Sie **STRG + N**.

10. Drag & drop unter dem Knoten **Media** **Audio Probleme klassische** Dataset in den oberen Bereich.

11. Drag & drop von Dataset **Scheduler** unter dem Knoten **CPU** in den 2. Bereich von oben.

12. Drag & drop Dataset **Sampling Profile** unter dem Knoten **CPU** in den 3. Bereich von oben.

13. Filtert die im Leerlauf-Prozesse aus der Ansicht, damit Sie die anderen Threadaktivität besser erkennen können. In der Struktur des Dataset erweitern Sie **Scheduler** Dataset in der **CPU** -Knoten zu, und klicken Sie auf der **Threads im Leerlauf** Knoten Checkbox zweimal ein, um es zu deaktivieren. Klicken Sie einmal auf das Kontrollkästchen werden die Daten im Diagramm behandelt; Klicken sie zweimal auf wird dieses deaktiviert.

## <a name="step-2-identify-the-region-of-the-trace-where-an-audio-glitch-occurred"></a>Schritt 2: Ermitteln des Bereichs des Trace ein audio Fehler aufgetreten ist


Betrachten Sie das audio-Modul Daten aus den Event Trace (ETL) Protokolldateien finden Sie unter eine visual Zeitachse der wann diese Probleme aufgetreten sind, und vergleichen Zeitplans, um andere Gruppen von Daten, um Muster zu suchen.

1.  Zoom auf einen audio Störung durch Klicken und ziehen die Maus über einem der Balken in der Systemsteuerung **Audio Probleme klassische** im oberen Bereich.

2.  Beachten Sie, dass der Prozess **iexplore.exe** im **Planer** Dataset in der Systemsteuerung 2nd für einen längeren Zeitraum (~ 20 35ms) direkt vor das audio Störung ausgeführt wurde.

3.  Drücken Sie ESC, um 100 % verkleinern, und wiederholen den vorherigen zwei Schritte, um das Muster zu überprüfen, auf dem der Prozess **iexplore.exe** ausgeführt wurde für lange dauern (~ 20 35 ms) vor jeder audio Störung.

4.  Um Zeit innerhalb des Bereichs zu messen, drücken Sie **die UMSCHALTTASTE** , während Sie den Mauszeiger von einem Ende des Balkens Prozess **iexplore.exe** zu einem anderen ziehen. Die QuickInfo über den Mauszeiger zeigt, wie viele Millisekunden messen auf der Zeitachse. In der folgenden **MXA** Screenshot wurde der Prozess für ungefähr 35 Millisekunden ausgeführt.

    ![Screenshot der Medienfunktionen Analyzer (MXA) mit Beispiel-Prozess für ungefähr 35 Millisekunden ausgeführt.](images/optimizingwindowsdeviceslab5.png)

## <a name="step-3-identify-the-cause-of-the-delays-in-the-pipeline"></a>Schritt 3: Identifizieren Sie die Ursache für die Verzögerung in der pipeline


Bevor Sie dieses Fehlers audio wurde der langer **iexplore.exe** Prozess auf einem der Kerne ausgeführt. Um herauszufinden, wie der Thread **iexplore.exe** Pipeline für die audio führte ist, können Sie die entsprechenden **Profile Sampling** Dataset im Knoten **CPU** betrachten.

1.  Wenn die **Aufrufliste** Dataviewer im Fenster **MXA** nicht angezeigt wird, klicken Sie auf **Ansicht** &gt; **Daten Viewer** &gt; **CallStack** zu öffnen.

2.  In der **Stichprobe Profile** panel (3rd von oben), bewegen Sie den Mauszeiger über den Beispiel-Profil-Ereignissen, die gleiche Farbe des lang andauernden **iexplore.exe** Threads übereinstimmen.

3.  Das Fenster **CallStack** zeigt die Aufrufliste für jedes Beispiel. Beachten Sie, dass ein bestimmter Treiber, **ImageRAMONA.sys**, am oberen Rand der **CallStack** Wenn Sie über die meisten Beispiele in der zugrunde liegenden, **iexplore.exe** bewegen ausgeführt wird.

4.  Obwohl der **audiodg.exe** Thread mit einer höheren Priorität (Priorität 22) als **iexplore.exe** Thread (Priorität 19), die **iexplore.exe** Thread Anrufe in einer Treiber (**ImageRAMONA.sys**), der die IRQL auslöst Ebene des Prozessors ausgeführt wird. Daher keinen **audiodg.exe**, die auf eine vom Verteiler beibehalten DPC warten ist eine Möglichkeit, auf dessen regulären 10 ms Trittfrequenz, was zu audio-Fehler auszuführen.

5.  Halten Sie die **UMSCHALTTASTE** gedrückt, um die **Aufrufliste** und **Eigenschaften Daten Viewer** fixieren und verschieben die Maus auf die **Aufrufliste**. Drücken Sie die **Kopie**.

![Screenshot von Medien Erfahrung Analyzer (MXA) mit CallStack Dataviewer.](images/optimizingwindowsdeviceslab6.png)

 

 






