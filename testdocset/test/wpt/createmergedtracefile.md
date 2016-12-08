---
title: CreateMergedTraceFile
description: CreateMergedTraceFile
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: d641530d-2be1-4266-962b-97863cff2e57
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: ed2f3f973e839c65390e3e886ae0d2ea07e16960
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="createmergedtracefile"></a>CreateMergedTraceFile


Diese Funktion verbindet mehrere Ablaufverfolgungsdateien in eine Ausgabedatei.

``` syntax
ULONG
WINAPI
CreateMergedTraceFile(
__in LPCWSTR wszMergedFileName,
__in LPCWSTR wszTraceFileNames[],
__in ULONG cTraceFileNames,
__in DWORD dwExtendedDataFlags
);
```

## <a name="parameters"></a>Parameter


<a href="" id="wszmergedfilename--in-"></a>*wszMergedFileName* \[in\]  
Gibt den Namen der Ausgabedatei Trace.

<a href="" id="wsztracefilenames--in-"></a>*wszTraceFileNames* \[in\]  
Zeiger auf ein Array von Ablaufverfolgungsdateien zusammengeführt werden sollen.

<a href="" id="ctracefilenames--in-"></a>*cTraceFileNames* \[in\]  
Die Anzahl der Elemente im Array *WszTraceFileNames* .

<a href="" id="dwextendeddataflags--in-"></a>*dwExtendedDataFlags* \[in\]  
Diese Flags Geben Sie die Systeminformationen, in die zusammengeführten Ablaufverfolgungsdatei eingefügt werden. Weitere Informationen zu gültigen Flags finden Sie unter [Benutzerdefinierte Einfügung Systeminformationen](custom-injection-of-system-information.md).

## <a name="return-value"></a>Rückgabewert


FEHLER\_der Vorgang ERFOLGREICH war erfolgreich.

In der folgenden Tabelle sind mögliche Fehler beschrieben.

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
<td><p>ERROR_INSUFFICIENT_BUFFER</p></td>
<td><p>Möglicherweise gibt an, dass der zusammengeführte Trace keine vollständige Reihe von Ereignissen für jede Datei enthält.</p></td>
</tr>
<tr class="even">
<td><p>ERROR_REVISION_MISMATCH</p></td>
<td><p>Möglicherweise gibt an, dass die zusammengeführten Ablaufverfolgungsdateien von Ereignissen mit verschiedenen Versionen enthalten, die nicht zusammengeführt werden konnte.</p></td>
</tr>
</tbody>
</table>

 

Wenn keiner dieser Fehlerwerte zurückgegeben wird, wird ein Systemfehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise


Sie können zwei oder mehr Ablaufverfolgungsdateien von gleichzeitigen Sitzungen zusammenführen, die auf demselben Computer in einer einzigen Protokolldatei erfasst wurden. Sie können auch Ablaufverfolgungsdateien aus anderen Sitzungen Tracing zusammenführen, wenn diese Dateien dieselbe Boot mehrmals vorhanden sind. Der Zusammenführungsvorgang optional, hinzugefügt Metadaten, die über die Spuren.

Diese Funktion kann erweiterte Daten in einer einzigen Protokolldatei eingefügt. In diesem Fall enthält das *WszMergedFileName* -Array nur ein Element, das den Namen der Ablaufverfolgungsdatei ist.

**Hinweis**  
Symbole kann keiner individuellen Kernel Trace ordnungsgemäß decodiert werden.

 

Die API ist nur in Unicode implementiert.

**Anforderungen**

**Versionen:** Verfügbar in Windows Vista ab. Diese Struktur ist mit Windows Performance Analyzer verteilt.

**Kopfzeilen:** In KernelTraceControl.h deklariert. Enthalten Sie KernelTraceControl.h.

**Bibliothek:** In KernelTraceControl.dll enthalten sind.

## <a name="related-topics"></a>Verwandte Themen


[Funktionen](functions-wpa.md)

[Benutzerdefinierte Einfügung von Systeminformationen](custom-injection-of-system-information.md)

 

 







