---
title: "Übung 2: Nachverfolgen Benutzer Modus Prozess Zuweisungen"
description: "Heapzuweisungen direkt über Heap APIs (HeapAlloc, HeapRealloc und C/C++-Zuweisungen wie neu zuordnen, Realloc, Calloc) vorgenommen werden und mit drei Typen von Heaps bedient werden"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: A1548D9A-6865-46FF-86B3-2874F559C893
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 2c2d70ad779a3a4ad8623011d3cc921c05356926
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="exercise-2---track-user-mode-process-allocations"></a>Übung 2: Nachverfolgen Benutzer Modus Prozess Zuweisungen


**Heap** Zuweisungen direkt über **Heap** APIs (**HeapAlloc**, **HeapRealloc**und C/C++-Zuweisungen wie **neue**, **zuordnen**, **Realloc**, **Calloc**) vorgenommen werden und mit drei Typen von Heaps bedient werden:

1.  **Neuen NT Heap** – Services Zuweisung Anforderungen von Größen kleiner als 64 KB.

2.  **Niedrig Fragmentierung Heap** – Looks von untergeordneten Segmenten, die Zuordnung fester Größe-Blöcke Anforderungen.

3.  **VirtualAlloc** – Services Zuweisung Anforderungen Größen größer als 64 KB.

**VirtualAlloc** wird für großen dynamischen Arbeitsspeicher Zuweisungen verwendet, die direkt über die API **VirtualAlloc** vorgenommen werden. Typischerweise ist normalerweise für Bitmaps oder Puffer auf. **VirtualAlloc** können Sie einen Block von Seiten reservieren und nehmen Sie dann zusätzliche Aufrufe an **VirtualAlloc** für einzelne Seiten aus dem reservierten Block ein Commit ausgeführt. Dies ermöglicht es einem Prozess reservieren, einen Bereich des virtuellen Adressraums ohne physischen Speicher verarbeiten, bis diese benötigt wird.

Es gibt zwei Konzepte zu verstehen, in diesem Bereich:

1.  **Reservierter Speicher**: reserviert für die Verwendung ein Adressbereichs jedoch keinen Speicherressourcen erwirbt.

2.  **Ein Commit Arbeitsspeicher**: wird sichergestellt, dass physikalischen Arbeitsspeichers oder Auslagerungsdatei verfügbar ist, wenn Sie die Adressen referenziert werden.

In dieser Übung erfahren Sie, wie zu sammeln Spuren zum untersuchen, wie ein Benutzer Modus Prozess Speicher reserviert.

Die Übung liegt der Schwerpunkt auf dummytests sogenannten **MemoryTestApp.exe** , das über Speicher zuweist:

1.  **VirtualAlloc** API für große Speicherpuffern ein Commit ausgeführt.

2.  Der **neue** C++-Operator kleine Objekte zu instanziieren.

Sie können **MemoryTestApp.exe** [hier](http://download.microsoft.com/download/9/C/8/9C88C0A1-1200-416A-B92B-2EBB128E4A4B/MemoryTestApp.exe)heruntergeladen werden.
## <a name="step-1-gather-a-virtualallocheap-trace-using-wpr"></a>Schritt 1: Erfassen Sie Ablaufverfolgungsdaten VirtualAlloc-Heap mit WPR


Große Speicher Zuweisungen sind normalerweise diejenigen aus, die Auswirkung auf die Speicherbedarf von einem Prozess und von **VirtualAlloc** API bedient werden. Hierbei handelt es sich um Where alle Untersuchungen beginnen soll, aber es ist außerdem möglich, dass ein Vorgang mit einer kleineren Zuweisungen verursacht (z. B. Speicherverluste mithilfe **Neuer** Operator in C++ usw..). Heap Tracing ist nützlich, wenn dies der Fall ist.

### <a name="a-href-idstep-1-1---prepare-the-system-for-heap-tracingastep-11-prepare-the-system-for-heap-tracing"></a><a href="" id="step-1-1---prepare-the-system-for-heap-tracing"></a>Schritt 1.1: Bereiten Sie das System für Heap tracing

Heap Tracing berücksichtigt optional sein sollen, und wenn fertig **VirtualAlloc** Analysis bietet keine relevanten Erläuterung bei einem Speicher Usage Problem. Heap Tracing ist größere Spuren zu erzeugen, und es wird empfohlen, die Verfolgung nur für die einzelnen Prozesse zu aktivieren, die Sie untersuchen möchten.

Fügen Sie den Registrierungsschlüssel für den Prozess von Interesse (**MemoryTestApp.exe** in diesem Fall); Heap Tracing ist für jede nachfolgende Erstellung aktiviert.

``` syntax
reg add "HKLM\Software\Microsoft\Windows NT\CurrentVersion\Image File Execution Options\MemoryTestApp.exe" /v TracingFlags /t REG_DWORD /d 1 /f
```

### <a name="a-href-idstep-1-2--capture-a-trace-using-wpr-astep-12-capture-a-trace-using-wpr"></a><a href="" id="step-1-2--capture-a-trace-using-wpr-"></a>Schritt 1.2: Erfassen einer Ablaufverfolgungs für WPR verwenden

In diesem Schritt werden Sie eine Verfolgung von **WPR** , das Daten **VirtualAlloc** und **Heap** enthält sammeln.

1.  Öffnen Sie **WPR** , und ändern Sie die Konfiguration der Protokollierung.

    1.  Wählen Sie die **VirtualAlloc** und **Heap** -Anbieter.

    2.  Wählen Sie **Allgemeine** **Leistung Szenario**wie.

    3.  Wählen Sie als der **Protokollierung Modus** **Allgemein** .

        ![Screenshot der WPR Tracing Optionen im Menü.](images/memoryfootprintlab11.png)

2.  Klicken Sie auf **Starten** , um das Tracing starten.

3.  Starten Sie **MemoryTestApp.exe**, und warten Sie, bis der Prozess beendet (es dauert etwa 30 Sekunden).

4.  Zurück zu **WPR**, speichern Sie die Ablaufverfolgung und mit **Windows Performance Analyzer (WPA)**zu öffnen.

5.  Öffnen Sie das Menü **Trace** , und wählen Sie **Konfigurieren Symbole Pfad**.

    -   Geben Sie den Pfad des Caches Symbol. Weitere Informationen zu Symbolen finden Sie unter auf der [Supportseite Symbol](https://go.microsoft.com/fwlink/?linkid=623019) auf MSDN.

6.  Öffnen Sie das Menü **Trace** , und wählen Sie **Symbole laden**.

Sie haben nun eine Verfolgung, die alle Memory Allocation Muster für den Prozess **MemoryTestApp.exe** während ihrer Lebensdauer enthält.

## <a name="step-2-review-virtualalloc-dynamic-allocations"></a>Schritt 2: Überprüfen VirtualAlloc dynamische Zuweisungen


Die detaillierten **VirtualAlloc** Daten werden über das Diagramm **' VirtualAlloc Commit Lebensdauer '** in WPA verfügbar gemacht. Die Schlüsselspalten von Interesse sind folgende:

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Spalte</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Prozessfarben</strong></td>
<td><p>Der Name des Prozesses, der Speicher Zuweisungen über <strong>VirtualAlloc</strong>ausgeführt wird.</p></td>
</tr>
<tr class="even">
<td><strong>Commit Stack</strong></td>
<td><p>Die Aufrufliste, die zeigt, den Codepfad zum Speicher reserviert werden.</p></td>
</tr>
<tr class="odd">
<td><strong>Commit Zeit</strong></td>
<td><p>Der Zeitstempel des beim Arbeitsspeicher belegt wurde.</p></td>
</tr>
<tr class="even">
<td><strong>Einen Decommit auszuführen Zeit</strong></td>
<td><p>Der Zeitstempel des beim Speicher freigegeben wurde.</p></td>
</tr>
<tr class="odd">
<td><strong>Beeinträchtigung der Größe</strong></td>
<td><p>Die Größe der ausstehenden Zuweisungen oder der der Größenunterschied zwischen Anfang und Ende des ausgewählten Zeitintervalls. Diese Größe des Textrahmens wird basierend auf den Port für die ausgewählte Ansicht.</p>
<p>Der <strong>Größe Beeinträchtigung der</strong> Wert ist gleich NULL, wenn alle von einem Prozess reservierte Speicher am Ende der visuell dargestellte Intervall in freigegeben ist <strong>WPA.</strong></p></td>
</tr>
<tr class="even">
<td><strong>Größe</strong></td>
<td><p>Die kumulative Summe alle Zuweisung während dem ausgewählten Zeitraum.</p></td>
</tr>
</tbody>
</table>

 

Befolgen Sie diese Schritte, um **MemoryTestApp.exe** analysieren

1.  Hier finden Sie im Diagramm **VirtualAlloc Commit Lebensdauer** in der Kategorie **Speicher** des **Diagramm-Explorer**.

2.  Drag & drop auf der Registerkarte **Analyse** der **VirtualAlloc Commit Gültigkeitsdauer** .

3.  Organisieren der Tabelle, um diese Spalten anzeigen. Mit der rechten Maustaste auf die Spaltenüberschriften hinzufügen oder Entfernen von Spalten.

    1.  **Prozess**

    2.  **Störenden Typ**

    3.  **Commit Stack**

    4.  **Zusichern der Zeit** und **einen Decommit auszuführen Zeit**

    5.  **Count**

    6.  **Beeinträchtigung der Größe** und **Größe**

4.  Hier finden Sie **MemoryTestApp.exe** in der Prozessliste.

5.  Anwenden eines Filters **MemoryTestApp.exe** nur im Diagramm beibehalten.

    -   Mit der rechten Maustaste, und wählen Sie **Filter** zur Auswahl.

![Screenshot, der zeigt, wie das Filtern der Ergebnisse.](images/memoryfootprintlab12.png)

Ihre Ansicht Analyse sollte etwa wie folgt aussehen:

![Beispiel: Grafik darüber, welche die Daten aussehen würde Wenn gefiltert.](images/memoryfootprintlab13.png)

Im vorstehenden Beispiel werden zwei Werte von Interesse sind:

-   **Größe** der 126 MB: darauf hin, dass **MemoryTestApp.exe** insgesamt 125 MB im Verlauf der Lebensdauer zugewiesen. Es stellt die kumulative Summe alle **VirtualAlloc** API-Aufrufe durch den Prozess und die zugehörigen Dateien.

-   **Beeinträchtigung der Größe** von 0 MB: darauf hin, dass alle durch den Prozess Arbeitsspeicher freigegeben am Ende das Zeitintervall wird gerade überprüft. Das System nicht über einen Anstieg der seiner stabilen Zustand Speicherverwendung beeinträchtigt werden.

### <a name="step-21-analyze-steady-state-memory-usage"></a>Schritt 2.1: Analysieren der Speicherverwendung stabilen Zustand

Beim Untersuchen arbeitsspeicherreservierung sollten Sie versuchen, die Frage zu beantworten: "Warum die Speicherverwendung stabilen Zustand wächst für dieses Szenario?" Im Beispiel **MemoryTestApp.exe** sehen Sie sich, dass er verfügt über etwa 10 MB Speichermenge stabilen Zustand am Anfang, und klicken Sie dann auf einen halben 20 MB erhöht.

![Screenshot der Beispieldaten, die Speicherverwendung angezeigt.](images/memoryfootprintlab14.png)

Um dieses Problem zu untersuchen, Grenzen Sie den Zoom, um das Zeitintervall die stattfindende tritt in der Mitte der Verfolgung ein.

![Screenshot, der zeigt, wie Sie die Daten zu vergrößern.](images/memoryfootprintlab15.png)

Die Ansicht sollte wie folgt aussehen.

![Screenshot der Beispieldaten nach dem Anwenden der Zoomoption.](images/memoryfootprintlab16.png)

Wie Sie sehen können, ist die **Größe Paketverlust beeinflusst** jetzt **10 MB**. Dies bedeutet, dass die zwischen Anfang und Ende der analysierten Zeitintervall, eine 10 MB erhöhen im stabilen Zustand Speicherverwendung vorhanden ist.

1.  Sortieren nach **Größe Paketverlust beeinflusst** , indem Sie auf die Spaltenüberschrift.

2.  Erweitern Sie die **MemoryTestApp.exe** Zeile (in der Spalte **Prozess** ).

3.  Erweitern Sie die Zeile **Impacting** (in der Spalte **Typ beeinträchtigen** ).

4.  Navigieren Sie durch den Prozess **Commit Stapel** , bis Sie die Funktion gefunden, die 10 MB Speicher zugewiesen.

    ![Screenshot der Beispieldaten.](images/memoryfootprintlab17.png)

In diesem Beispiel weist die **Main** -Funktion **MemoryTestApp.exe** 10 MB Speicher in der Mitte der Arbeitslast durch Aufrufen von **VirtualAlloc**direkt. In der Praxis sollte der Anwendungsentwickler festlegen, wenn die Zuordnung angemessene ist oder wenn der Code neu angeordnet werden konnte, um die Anhebung der stabilen Zustand Arbeitsspeicher Verwendung zu minimieren.

Sie können jetzt **Verkleinern** der Ansicht in WPA.

![Screenhsot der Verkleinern im Menü.](images/memoryfootprintlab18.png)

### <a name="step-22-analyze-transient-or-peak-memory-usage"></a>Schritt 2.2: Analysieren der Speicherverwendung vorübergehende (oder Spitzenzeiten)

Beim Arbeitsspeicher Zuweisungen untersuchen, sollten Sie versuchen, die Frage zu beantworten: "Warum es eine vorübergehende Spitze in die Speicherverwendung für diesen Teil des Szenarios ist?" Vorübergehende Zuweisungen abgeschwächt werden in Speicherverwendung verursachen, und auf Fragmentierung und Push wertvolle Inhalte aus dem System Standby-Cache führen können, wenn kein ausreichender Speicher vorhanden ist.

Im Beispiel **MemoryTest** sehen Sie sich, dass 10 verschiedene Spitzen der Speicherverwendung (von 10 MB) die Ablaufverfolgung gleichmäßig verteilt sind.

![Screenshot der Grafik, die Arbeitsspeicher-Verwendungsdaten anzeigt.](images/memoryfootprintlab19.png)

Schränken Sie den Zoom auf die letzten vier abgeschwächt werden, um den Schwerpunkt auf einen kleineren Interessenbereich und Rauschen aus nicht relevant Verhaltensweisen.

![Screenshot des Zoomoption.](images/memoryfootprintlab20.png)

Die Ansicht sollte wie folgt aussehen:

![Screenshot der Grafik, die Arbeitsspeicher-Verwendungsdaten mithilfe der Zoomoption anzeigt.](images/memoryfootprintlab21.png)

1.  Sortieren nach **Größe** , indem Sie auf die Spaltenüberschrift.

2.  Erweitern Sie die **MemoryTestApp.exe** Zeile (in der Spalte **Prozess** ).

3.  Klicken Sie auf die **vorübergehende** Zeile (in der Spalte **Typ beeinträchtigen** ).

    -   Dies sollte alle Spitzen der Speicherverwendung in die Ansicht in blau markieren.

4.  Notieren Sie den Wert der verschiedenen Spalten:

    1.  **Count** = 4: darauf hin, dass vier temporärer Speicher Zuweisungen während dieses Zeitintervalls vorgenommen wurden.

    2.  **Beeinträchtigung der Größe** 0 MB =: darauf hin, dass alle vier temporärer Speicher Zuweisungen durch das Ende des Zeitintervalls freigegeben wurden.

    3.  **Größe** = 40 MB: Dies gibt die Summe der alle vier temporärer Speicher Zuweisungen Speichermenge auf 40 MB an.

5.  Navigieren Sie durch den Prozess **Commit Stapel** , bis Sie die Funktionen gefunden, die 40 MB Arbeitsspeicher zugewiesen.

    ![Screenshot der Verwendungsdaten Arbeitsspeicher.](images/memoryfootprintlab22.png)

In diesem Beispiel ruft die **Main** -Funktion der **MemoryTestApp.exe** eine Funktion mit dem Namen **Arbeitsgang1 gibt es**, die wiederum eine Funktion Anrufe **ManipulateTemporaryBuffer**genannt. Diese Funktion **ManipulateTemporaryBuffer** direkt ruft dann **VirtualAlloc** Vierfache, erstellen und Freigeben von einer 10 MB Speicher Puffer jedes Mal. Die Puffer nur letzten 100 ms jeder. Die Puffer Zuweisung und freie Zeiten werden spaltenweise **Commit Zeit** und **Einen Decommit auszuführen** dargestellt.

In der Praxis würde der Anwendungsentwickler bestimmen, ob diese Zuweisungen kurzlebige vorübergehende temporären Puffer erforderlich sind, oder, wenn sie einen Puffer permanenten Speicher für den Vorgang mit ersetzt werden können.

Sie können jetzt **Verkleinern** der Ansicht in **WPA**.

## <a name="step-3-review-heap-dynamic-allocations"></a>Schritt 3: Überprüfen Sie Heap dynamische Zuweisungen


Bisher wurde die Analyse nur großer Arbeitsspeicher Zuweisungen der Schwerpunkt auf, die durch die API **VirtualAlloc** verwaltet werden. Im nächste Schritt ist zu ermitteln, ob Probleme mit anderen kleinen Zuweisungen, die durch den Prozess, indem zunächst erfassten Daten Heap vorhanden sind.

Die detaillierten Daten Heap werden über das Diagramm **"Heapzuweisungen"** WPA verfügbar gemacht. Die Schlüsselspalten von Interesse sind folgende:

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Spalte</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Prozessfarben</strong></td>
<td>Der Name des Prozesses, mit dem arbeitsspeicherreservierung ausgeführt wird.</td>
</tr>
<tr class="even">
<td><strong>Behandeln</strong></td>
<td><p>Der Bezeichner des Heap, das verwendet wird, um die Zuordnung zu bedienen.</p>
<p>Heaps können erstellt werden, damit es mehrere Heap Handles für den Prozess kann.</p></td>
</tr>
<tr class="odd">
<td><strong>Stapel</strong></td>
<td>Die Aufrufliste, die der Codepfad angezeigt wird, der in den Speicher reserviert werden führt.</td>
</tr>
<tr class="even">
<td><strong>Zeit zuordnen</strong></td>
<td>Der Zeitstempel des beim Arbeitsspeicher belegt wurde.</td>
</tr>
<tr class="odd">
<td><strong>Beeinträchtigung der Größe</strong></td>
<td>Die Größe der ausstehenden Zuweisungen oder den Unterschied zwischen dem Start und Ende für die ausgewählte Ansicht. Diese Größe des Textrahmens wird basierend auf dem ausgewählten Zeitraum.</td>
</tr>
<tr class="even">
<td><strong>Größe</strong></td>
<td>Die kumulative Summe alle Zuweisungen/Deallocations.</td>
</tr>
</tbody>
</table>

 

Befolgen Sie diese Schritte, um **MemoryTestApp.exe** analysieren

1.  Hier finden Sie im Diagramm **Heapzuweisungen** in der Kategorie **Speicher** des **Diagramm-Explorer**.

2.  Drag & drop auf der Registerkarte **Analyse** der **Heapzuweisungen** .

3.  Organisieren der Tabelle, um diese Spalten werden angezeigt:

    1.  **Prozess**

    2.  **Behandeln**

    3.  **Störenden Typ**

    4.  **Stack**

    5.  **AllocTime**

    6.  **Count**

    7.  **Beeinträchtigung der Größe** und **Größe**

4.  Hier finden Sie **MemoryTestApp.exe** in der Prozessliste.

5.  Anwenden eines Filters **MemoryTestApp.exe** nur im Diagramm beibehalten.

    -   Mit der rechten Maustaste, und wählen Sie **Filter** zur Auswahl.

Die Ansicht sollte wie folgt aussehen:

![Screenshot der Beispieldaten.](images/memoryfootprintlab23.png)

In diesem Beispiel sehen Sie sich, dass eine der Heaps ständig Größe über einen Zeitraum mit einer Konstante Rate zunimmt. 1200 Arbeitsspeicher Zuweisungen auf diesem Heap accounting für 130 KB verwendeter Speicher am Ende des Intervalls sind vorhanden.

1.  Zoom auf einen kleineren Intervall (beispielsweise 10 Sekunden) in der Mitte der Trace.

2.  Erweitern Sie den Kopf **behandeln** , die den größten Betrag der Zuweisungen zeigt (wie in der Spalte **Größe beeinträchtigen** dargestellt).

3.  Erweitern Sie den **Impacting** -Typ.

4.  Navigieren Sie durch den Prozess **Stapel** , bis Sie mit die Funktion, die gefunden für alle diese Arbeitsspeicher zuständig ist.

    ![Screenshot der Beispieldaten nach dem Anwenden der Zoomoption.](images/memoryfootprintlab24.png)

In diesem Beispiel ruft die **Main** -Funktion der **MemoryTestApp.exe** eine Funktion mit dem Namen **InnerLoopOperation**. Diese Funktion **InnerLoopOperation** ordnet dann 40 Bytes Speicher 319 Zeiten mit den **neuen** C++-Operator. Dieser Speicher bleibt zugewiesenen, bis der Prozess beendet wird.

In der Praxis Anwendungsentwickler sollte dann ermitteln, ob dieses Verhalten mögliche Speicherverluste impliziert das Problem zu beheben.

## <a name="step-4-clean-up-the-test-system"></a>Schritt 4: Bereinigen des Testsystems


Sobald die Analyse abgeschlossen ist, sollten Sie Bereinigen der Registrierung, um sicherzustellen, dass für den Prozess Heap Tracing deaktiviert ist. Führen Sie diesen Befehl auf eine Eingabeaufforderung mit erhöhten Rechten:

``` syntax
reg delete "HKLM\Software\Microsoft\Windows NT\CurrentVersion\Image File Execution Options\MemoryTestApp.exe" /v TracingFlags /f
```

 

 






