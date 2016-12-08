---
title: OnEnd
description: OnEnd
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 3daba834-c555-40d4-8afa-ed0a1f6aaedf
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 44660b5d8adc97bcf98a905e19400e284172c6d7
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="onend"></a>OnEnd


Gibt einen Statuscode nach dem Ende eines Vorgangs.

## <a name="syntax"></a>Syntax


``` syntax
HRESULT OnEnd(HRESULT hrResult);
```

## <a name="parameters"></a>Parameter


<a href="" id="hrresult--in-"></a>*hrResult* \[in\]  
Statuscode des Vorgangs nach beendet.

## <a name="return-value"></a>Rückgabewert


In der folgenden Tabelle werden mögliche Rückgabewerte beschrieben. WPR ignoriert Fehler-Werte.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Rückgabewert</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>S_OK</p></td>
<td><p>Die Funktion wurde erfolgreich den Status zurückgegeben.</p></td>
</tr>
</tbody>
</table>

 

## <a name="remarks"></a>Hinweise


Die Bibliothek wird den Rückgabewert dieser Funktion nicht überprüft werden.

Beim Speichern eines Traces oder beenden, gibt dieser Rückruf auch die Anzahl der Ereignisse in der Verfolgung verloren.

## <a name="related-topics"></a>Verwandte Themen


[IControlProgressHandler](icontrolprogresshandler.md)

 

 







