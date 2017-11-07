---
title: UpdateHeapTrace
description: UpdateHeapTrace
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 5cbff080-bdaa-412d-8412-22013f2717fb
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 9f319e5fec486aefffe45f162ae5cea6b01f23b1
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="updateheaptrace"></a>UpdateHeapTrace


\[Einige Informationen bezieht sich auf Vorabversionen Produkt, das vor der Freigabe im Handel erheblich geändert werden kann. Microsoft Gewährleistung aus, sei Sie ausdrücklich oder konkludent, in Bezug auf die hier bereitgestellten Informationen.\]

Diese Funktion aktualisiert eine vorhandene Heap tracing Sitzung mit einem neuen Satz von PID, Stackwalking Ereignisse oder andere ETW-Sitzung ändert.

``` syntax
ULONG
WINAPI
UpdateHeapTrace(
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
Ein Zeiger auf ein [EREIGNIS\_TRACE\_EIGENSCHAFTEN](https://msdn.microsoft.com/library/windows/desktop/aa363784.aspx) Struktur mit den Eigenschaften für die Sitzung aktualisiert. Verweisen auf die [ControlTrace](https://msdn.microsoft.com/library/windows/desktop/aa363696.aspx) -Funktion mit ControlCode-EREIGNIS\_TRACE\_STEUERELEMENT\_UPDATE Weitere Informationen zu den Mitgliedern dieser Struktur angegeben werden können.

<a href="" id="wszsessionname-in-"></a>*WszSessionName*\[in\]  
Der Name der Heap Tracingsitzung zu aktualisieren. Dies sollte dem gleichen Namen sein, der an StartHeapTrace übergeben wurde.

<a href="" id="pids--in-"></a>*PID* \[in\]  
Ein Array von Prozess-IDs Heap Tracing auf aktivieren.

<a href="" id="cpids--in--out-"></a>*cPids* \[eingehend, ausgehend\]  
Die Größe des Arrays PID.

<a href="" id="stacktracingeventids--in-"></a>*StackTracingEventIds* \[in\]  
Ein Array von [STAPEL\_TRACING\_EREIGNIS\_ID](https://msdn.microsoft.com/library/windows/hardware/dn631805.aspx) Strukturen, die angeben, welche Heap Ereignisse Stapel durchlaufen muss für aktiviert sein. NULL kann sein.

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

[StartHeapTrace](startheaptrace.md)

 

 







