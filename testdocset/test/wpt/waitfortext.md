---
title: WaitForText
description: WaitForText
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: d030b3b3-421e-4cc1-9752-d5f69a011fae
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: de6cbbffc028249c74a5490b1e577aa8331a56fb
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="waitfortext"></a>WaitForText


Wartet, bis der Benutzer die entsprechenden Textzeichenfolgen und ruft SetTextAvailable hinzufügt.

## <a name="syntax"></a>Syntax


``` syntax
HRESULT WaitForText
  ([in] ULONG Milliseconds)
;
```

## <a name="parameters"></a>Parameter


<a href="" id="milliseconds"></a>*Millisekunden*  
\[in\] gibt die Anzahl von Millisekunden für die Verzögerung warten.

## <a name="return-value"></a>Rückgabewert


In der folgenden Tabelle werden mögliche Rückgabewerte beschrieben. Fehler bei Rückgabewerte sind implementierungsspezifischen.

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
<td><p>Gibt Erfolg an.</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>Verwandte Themen


[ITraceMergeTextHandler](itracemergetexthandler.md)

 

 







