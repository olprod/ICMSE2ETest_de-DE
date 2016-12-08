---
title: Next
description: 'Next (weiter) '
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: e1016773-7fa6-4f87-a128-cad80c35755a
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 6696231c3bfefa98e4a5a1d202b4212397b3cd7f
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="next"></a>Next (weiter) 


Gibt ein Array mit der angegebenen Anzahl von Fehler oder Warnungen aus dem aktuellen Index, der den Enumerator zurück.

## <a name="syntax"></a>Syntax


``` syntax
HRESULT Next
  ([in] ULONG celt,
  [out, size_is(celt), length_is(*pCeltFetched)] const IControlErrorInfo** prgVar,
  [out] ULONG* pCeltFetched)
;
```

## <a name="parameters"></a>Parameter


<a href="" id="celt"></a>*celt*  
\[in\] die Anzahl der Elemente zurückgegeben werden soll.

<a href="" id="prgvar"></a>*prgVar*  
\[Skalieren\] ein Array von mindestens der Größe des *Celt* in dem werden Elemente zurückgegeben werden soll.

<a href="" id="pceltfetched"></a>*pCeltFetched*  
\[Skalieren\] ein Zeiger auf die Anzahl der Elemente, die in *RgVar*oder NULL zurückgegeben.

## <a name="return-value"></a>Rückgabewert


In der folgenden Tabelle werden mögliche Rückgabewerte beschrieben.

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
<td><p>Die Funktion wurde erfolgreich das Array zurückgegeben.</p></td>
</tr>
<tr class="even">
<td><p>S_FALSE</p></td>
<td><p>Die Anzahl der zurückgegebenen Elemente ist kleiner dann <em>Celt</em>.</p></td>
</tr>
<tr class="odd">
<td><p>E_POINTER</p></td>
<td><p>Gibt ein ungültiger Zeiger an.</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>Verwandte Themen


[IEnumControlWarningInfo](ienumcontrolwarninginfo.md)

 

 







