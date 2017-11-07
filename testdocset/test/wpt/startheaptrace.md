---
title: StartHeapTrace
description: StartHeapTrace
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 2f3ecae0-532a-45ab-a5e3-a5ed4868decf
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 62cd9090390576c155140a761fe3285702904da4
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="startheaptrace"></a>StartHeapTrace


\[Einige Informationen bezieht sich auf Vorabversionen Produkt, das vor der Freigabe im Handel erheblich geändert werden kann. Microsoft Gewährleistung aus, sei Sie ausdrücklich oder konkludent, in Bezug auf die hier bereitgestellten Informationen.\]

Diese Funktion registriert und startet eine Heap Tracing-Sitzung für eine Reihe von PID angegebenen. Sie können auch für bestimmte Ereignisse wie Zuweisung oder Löschung mit dieser Funktion Heap Durchlaufen von Stapeln aktivieren.

Der Prozess für die, den Heap Verfolgung ist aktiviert werden soll, muss vor dem Aufrufen dieser Funktion erstellt werden. Zu erfassen Heap-Ereignisse von Anfang des Programms es wird empfohlen, dass der Prozess mit gestartet werden die [ERSTELLEN\_ANGEHALTEN](https://msdn.microsoft.com/library/windows/desktop/ms682425.aspx) kennzeichnen, und klicken Sie dann Heap Tracing aktiviert für seine PID, und klicken Sie dann auf den Prozess fortgesetzt.

Heap Tracing ist sehr ausführlich und schnell eine sehr große Ablaufverfolgungsdatei erstellen kann. Ereignisse verloren ganz einfach, wenn die Sitzung Puffer zu klein sind oder zu wenige. Es wird empfohlen, dass die Anzahl der Prozesse, für welche, die Heap Tracing aktiviert ist, damit keine Ereignisse verloren beschränkt werden. Aktivieren der Protokollierung Heap möglicherweise Leistungseinbußen auf dem Prozess aufgezeichnet.

``` syntax
ULONG
WINAPI
StartHeapTrace(
    _Out_ PTRACEHANDLE TraceHandle,
    _Inout_ PEVENT_TRACE_PROPERTIES Properties,
    _In_z_ LPCWSTR wszSessionName,
    _In_reads_opt_(cPids) const ULONG Pids[],
    _In_  ULONG cPids,
    _In_reads_opt_(cStackTracingEventIds) const STACK_TRACING_EVENT_ID StackTracingEventIds[],
    _In_  ULONG cStackTracingEventIds
    );
```

## <a name="parameters"></a>Parameter


<a href="" id="tracehandle--out-"></a>*TraceHandle* \[,\]  
Speichert einen Handle für ein Ereignis Tracing-Sitzung. Dieser Parameter ist auf 0 (null) festgelegt, wenn das Handle ungültig ist. Dieser Parameter sollte nicht verglichen werden, auf UNGÜLTIG\_BEHANDELN\_WERT. Verwenden Sie dieses Handle nicht auf, wenn die Funktion fehlschlägt.

<a href="" id="properties--in--out-"></a>*Eigenschaften* \[eingehend, ausgehend\]  
Speichert einen Zeiger auf ein [EREIGNIS\_TRACE\_EIGENSCHAFTEN](https://msdn.microsoft.com/library/windows/desktop/aa363784.aspx) Struktur. EREIGNIS\_TRACE\_EIGENSCHAFTEN konfiguriert bestimmte Aspekte des Verhaltens der Sitzung.

Es ist nicht notwendig, das Guid-Element festlegen, da diese Funktion immer verwendet die eigenen-Wert. Wenn Sie eine GUID angeben, wird es nicht verwendet werden.

<a href="" id="wszsessionname--in-"></a>*wszSessionName* \[in\]  
Session-Name zum Übergeben an [StartTrace](https://msdn.microsoft.com/library/windows/desktop/aa364117.aspx)zuzugreifen.

<a href="" id="pids--in-"></a>*PID* \[in\]  
Ein Array von Prozess-IDs Heap Tracing auf aktivieren.

<a href="" id="cpids--in-"></a>*cPids* \[in\]  
Die Größe des Arrays PID.

<a href="" id="cstacktracingeventids--in-"></a>*cStackTracingEventIds* \[in\]  
Die Größe des Arrays StackTracingEventIds.

## <a name="return-value"></a>Rückgabewert


FEHLER\_der Vorgang ERFOLGREICH war erfolgreich.

Mögliche Fehler werden in der folgenden Tabelle beschrieben.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Fehlerwert</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>ERROR_ALREADY_EXISTS</p></td>
<td><p>Nur eine einzige Instanz der Kernelprotokollierung, die auf dem System ausgeführt werden. Wenn diese Funktion versucht, starten, nachdem eine weitere Komponente Kernel Protokollierung gestartet wurde, wird möglicherweise diese Fehler zurückgegeben.</p></td>
</tr>
<tr class="even">
<td><p>ERROR_INVALID_FLAGS</p></td>
<td><p>Möglicherweise gibt an, dass ungültige Ablaufverfolgungsflags in <strong>Properties.EnableFlags</strong>.</p></td>
</tr>
<tr class="odd">
<td><p>ERROR_OUT_OF_MEMORY</p></td>
<td><p>Möglicherweise gibt Fehler EVENT_TRACE_PROPERTIES reserviert werden.</p></td>
</tr>
</tbody>
</table>

 

Wenn die Funktion einen anderen aufgeführten Grund ein Fehler auftritt, wird ein Systemfehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise


Keine

## <a name="related-topics"></a>Verwandte Themen


[Funktionen](functions-wpa.md)

[UpdateHeapTrace](updateheaptrace.md)

 

 







