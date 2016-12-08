---
title: "Übung 3: Verwendung MXA zu überprüfen, dass die Audiodatenfunktion ist ausgelagert während der vollständigen Bildschirm Videowiedergabe"
description: "Verarbeitung von Audiosignalen über Chipsätze-Verschiebung, die Audio unterstützen Verschiebung der Ergebnisse im Akkulaufzeit während der von Audio- und Audio/Video-Wiedergabeszenarien, die das Media-Modul in Windows nutzen."
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 96251661-55CC-4082-A3FF-4926C4931F74
ms.openlocfilehash: 4a2fbff2729be72e33688a2ec0f9e58f63a86ee0
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="exercise-3---use-mxa-to-verify-that-audio-is-offloaded-during-full-screen-video-playback"></a>Übung 3: MXA verwenden, stellen Sie sicher, dass die Audiodatenfunktion ist ausgelagert während der vollständigen Bildschirm Videowiedergabe


Verarbeitung von Audiosignalen über Chipsätze Abladung Audio-Unterstützung Verschiebung der Ergebnisse im Akkulaufzeit während der von Audio- und Audio/Video-Wiedergabeszenarien, in denen nutzen Sie das Media-Modul in Windows. In dieser Übung verwendet das Tool **Medienfunktionen Analyzer (MXA)** , um festzustellen, ob Audio an Hardware Vollbild Videowiedergabe übergeben wurde oder nicht.

## <a name="step-1-load-an-etw-trace-that-was-captured-during-full-screen-video-playback"></a>Schritt 1: Laden eines ETW Trace, die während der Videowiedergabe Vollbild erfasst wurde


1.  Installieren von **MXA** die heruntergeladen werden kann [hier](https://go.microsoft.com/fwlink/?linkid=525711).

2.  Mit der rechten Maustaste auf **das Startmenü** , und klicken Sie auf **der Befehlszeile (Admin)**.

3.  Navigieren Sie zu dem Ordner, in dem Sie **MXA**installiert.

4.  Laden Sie **AudioNotOffloaded.etl** [hier](http://download.microsoft.com/download/A/5/D/A5D6F588-EE12-4FBA-B54C-E6D1E554F19C/AudioNotOffloaded.etl).

5.  Führen Sie den folgenden Befehl aus:

    ``` syntax
    xa -i <AudioNotOffloaded.etl location>\AudioNotOffloaded.etl
    ```

    Beispielsweise, wenn Sie auf C: **AudioNotOffloaded.etl** heruntergeladen\\Leistung\\Media\\, geben Sie den folgenden Befehl ein:

    ``` syntax
    xa -i C:\Performance\Media\AudioOffload\AudioNotOffloaded.etl
    ```

6.  Drücken Sie die **Symbole deaktivieren** Symbol Lookup deaktivieren.

## <a name="step-2-verify-audio-was-rendered-when-the-etw-trace-was-collected"></a>Schritt 2: Stellen Sie sicher, dass Audio gerendert wurde, wenn der ETW Trace gesammelt wurden


1.  Sobald die Ablaufverfolgung lädt, Drag & drop des Anbieters für **Microsoft Windows MediaFoundation Performance** in einem Bereich.

2.  Deaktivieren Sie alle Ereignisse in der **Microsoft-Windows-MediaFoundation-Leistung** Anbieter durch Klicken auf das Kontrollkästchen neben dieser Dataset zweimal ein.

3.  Aktivieren der **Aufgabe Audio\_Render – 482 Ereignisse**.

4.  Wenn Audio Rendern Ereignisse ausgelöst werden, in der gesamten Trace, Audio wurde wiedergeben, wenn der Trace gesammelt wurden.

![Screenshot der Medienfunktionen Analyzer (MXA) mit audio Trace Ereignisdaten.](images/optimizingwindowsdeviceslab1.png)

Wie wir aus dem Screenshot sehen können, Rendern Audio Ereignisse in der **Microsoft Windows-MediaFoundation-Performance** -Anbieter (**Aufgabe Audio\_Render – 482**) werden in der gesamten die gesamte Trace protokolliert. Dadurch wird sichergestellt, dass dieser Audiodatei wiedergeben wurde.

## <a name="step-3-determine-whether-audio-was-offloaded-to-hardware"></a>Schritt 3: Feststellen Sie, ob Audio an Hardware übergeben wurde


1.  Drag & drop **CPU Scheduler** Datasets in einem Bereich.

2.  Deaktivieren Sie alle Ereignisse, indem Sie auf das Kontrollkästchen im Stamm des Datasets auf **CPU Scheduler** zweimal ein.

3.  Erweitern Sie die **CPU-Scheduler** Dataset und **Systemprozesse für Windows** -Knoten.

4.  Wählen Sie den Prozess **audiodg.exe** , indem Sie das Kontrollkästchen einmal auf.

5.  Ist **audiodg.exe** Thread-Aktivität, die alle 10 ms während der Sitzung gesamte Wiedergabe auftreten, ist nicht Audiodaten übergeben wird. Ein Beispiel finden Sie unter MXA Screenshot \#1.

6.  Wenn **audiodg.exe** Threadaktivität nur während der starten und beenden, klicken Sie dann audio wird übergeben wird. Ein Beispiel finden Sie unter MXA Screenshot \#2.

7.  Laden Sie die Ablaufverfolgungsdatei **AudioOffloaded.etl** [hier](http://download.microsoft.com/download/7/A/9/7A9935AE-DD3C-4714-9457-FF86BD5A6F05/AudioOffloaded.etl).

8.  Wiederholen Sie die Schritte 1, 2 und 3 Trace **AudioOffloaded.etl** anstelle von **AudioNotOffloaded.etl**verwenden.

### <a name="a-href-idmxa-screenshot--1--trace-taken-on-a-system-where-audio-is-not-being-offloadedamxa-screenshot-1-trace-taken-on-a-system-where-audio-is-not-being-offloaded"></a><a href="" id="mxa-screenshot--1--trace-taken-on-a-system-where-audio-is-not-being-offloaded"></a>Screenshot der MXA \#1: Trace auf einem System ausgeführt werden, in dem Audio NICHT übergeben wird

Beachten Sie, dass die **audiodg.exe** von jeder 10 ms zum Verarbeiten von audio-Samples in der gesamten die gesamte Trace aktiviert ist.

![Screenshot der Medienfunktionen Analyzer (MXA) mit Trace auf einem System ausgeführt werden, in dem Audio NICHT übergeben wird.](images/optimizingwindowsdeviceslab2.png)

### <a name="a-href-idmxa-screenshot--2--trace-taken-on-a-system-where-audio-is-being-offloadedamxa-screenshot-2-trace-taken-on-a-system-where-audio-is-being-offloaded"></a><a href="" id="mxa-screenshot--2--trace-taken-on-a-system-where-audio-is-being-offloaded"></a>Screenshot, der MXA \#2: Trace auf einem System ausgeführt werden, in dem Audio übertragen wird

Beachten Sie, dass die sehr niedrige Thread-Aktivität im Prozess **audiodg.exe** am starten und Beenden von Phasen der Wiedergabe vorhanden ist. Beachten Sie, dass während der stabilen Zustand keine Threadaktivität vorhanden ist.

![Screenshot der Medienfunktionen Analyzer (MXA) mit Trace auf einem System ausgeführt werden, in dem Audio übertragen wird.](images/optimizingwindowsdeviceslab3.png)

 

 






