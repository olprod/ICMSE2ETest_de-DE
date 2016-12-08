---
title: Aktivieren der Heap Datenerfassung
description: Aktivieren der Heap Datenerfassung
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 73d49914-7f60-426e-9833-cee7c5ec5d10
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: b07e44edbd1c4c12769be2e824451a4ef9637717
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="enabling-heap-data-capture"></a>Aktivieren der Heap Datenerfassung


Heap Analyse ist am effektivsten Stapel Erfassen von Ereignissen **HeapAlloc** und **HeapRealloc** erfasst werden. Um Stapel mit Symbole decodieren, müssen Sie das Symbol Decodierung aktivieren. Sie können Heapdaten erfassen, wenn ein Prozess gestartet wird oder auf einem vorhandenen Prozess.

## <a name="to-enable-data-capture-when-a-process-is-started"></a>Zum Aktivieren der Datenerfassung, wenn ein Prozess gestartet wird


In diesem Beispiel startet die analysierten aus der Command-Line Sequenz, die Datenerfassung beginnt. Datenerfassung aktivieren, wenn ein Prozess gestartet wird sichergestellt, dass es keinen Verlust der Zuordnungsinformationen oder der Verlauf gibt. Führen Sie die folgenden Schritte zur Datenerfassung Prozess beim Starten zu ermöglichen:

1.  Geben Sie aus einer Eingabeaufforderung mit erhöhten Rechten den folgenden Befehl ein:`xperf -on Base -BufferSize 1024 -MinBuffers 10 -MaxBuffers 16`

2.  Es folgt ein Beispielbefehl:`xperf -start HeapSession -heap -PidNewProcess "C:\Program Files\Windows Sidebar\sidebar.exe" -BufferSize 1024 -MinBuffers 128 -MaxBuffers 128 -stackwalk HeapAlloc+HeapRealloc`

    Die Randleiste auf dem Desktop wird geöffnet.

    In der folgenden Tabelle sind diese Befehle erläutert.

    <table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th>Befehl</th>
    <th>Beschreibung</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p>-HeapSession starten</p></td>
    <td><p>Initialisiert eine Tracing oder Protokollierung Sitzung. In diesem Fall die Sitzung heißt &quot;HeapSession&quot;.</p></td>
    </tr>
    <tr class="even">
    <td><p>-Heap</p></td>
    <td><p>Identifiziert &quot;HeapSession&quot; als ein Heap Trace.</p></td>
    </tr>
    <tr class="odd">
    <td><p>-PidNewProcess</p></td>
    <td><p>Initialisiert einen Prozess. In diesem Fall initialisiert die Windows-Sidebar.</p></td>
    </tr>
    <tr class="even">
    <td><p>-Puffergröße</p></td>
    <td><p>Legt die Puffergröße des Puffers, in dem die Ereignisdaten gespeichert ist. Eine optimale Größe für einen Puffer ist 1.024 KB. Der Standardwert ist 64 KB.</p></td>
    </tr>
    <tr class="odd">
    <td><p>-MinBuffers</p></td>
    <td><p>Legt die minimale Anzahl der Puffer zum Speichern von Daten. <strong>MinBuffers</strong> sollte <strong>MaxPuffer</strong> Sicherstellen der Konsistenz zwischen Spuren gleich sein.</p></td>
    </tr>
    <tr class="even">
    <td><p>MaxBuffers-</p></td>
    <td><p>Reservieren Sie <strong>MaxPuffer</strong> konservativ, da Puffer aus dem Speicher nicht ausgelagerten zugeordnet werden, die eine begrenzte Systemressource ist.</p></td>
    </tr>
    <tr class="odd">
    <td><p>-stackwalk</p></td>
    <td><p>Initialisiert die Stackwalk Möglichkeit zum Sammeln von Informationen Reservierung und Freigabe, und ordnen Sie diese Informationen bestimmten Threads an.</p></td>
    </tr>
    <tr class="even">
    <td><p>HeapAlloc + HeapRealloc</p></td>
    <td><p>Bestimmte Heap Ereignisse um erfasst und präsentiert von der Funktion Stackwalk identifiziert.</p></td>
    </tr>
    </tbody>
    </table>

     

3.  Geben Sie den folgenden Befehl ein:`xperf -stop -stop HeapSession -d HeapTrace.etl`

    Die `-d HeapTrace.etl` Befehl Spuren in der Sitzung in die Datei HeapTrace.etl erstellt werden.

## <a name="to-enable-data-capture-on-an-existing-process"></a>So aktivieren Sie die Datenerfassung an einen vorhandenen Prozess


Diese Option ermöglicht die Datenerfassung ohne Beenden und erneutes Starten des Prozesses. Dies kann Vorteil sein, wenn das analysierten Szenario nicht der Fall, bis nach der Anwendung gestartet wird, und die anfängliche Heapzuweisung (sehr große Ablaufverfolgungsdateien erstellen kann) nicht erforderlich ist.

Führen Sie die folgenden Schritte aus:

1.  Starten Sie von einer Eingabeaufforderung mit erhöhten Rechten der NT-Kernel-Protokollierung mit dem BASIS-Flag wie folgt:`xperf -on BASE`

2.  Um Heap Tracing auf einen vorhandenen Prozess zu aktivieren, ersetzen Sie die aktuelle Prozess-ID für *XXX* in den folgenden Befehl ein:`xperf -start HeapSession -heap -Pid XXX -BufferSize 1024 -MinBuffers 128 -MaxBuffers 128 -stackwalk HeapAlloc+HeapRealloc`

3.  Vorbereiten der ablaufverfolgungen für die Analyse auf die gleiche Weise wie für die Datenerfassung erledigt, wenn ein Prozess gestartet wird:`xperf -stop -stop HeapSession -d heapTrace.etl`

## <a name="related-topics"></a>Verwandte Themen


[Heap](heap.md)

 

 







