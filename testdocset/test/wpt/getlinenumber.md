---
title: GetLineNumber
description: GetLineNumber
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: d25dc5f0-386e-4dc1-aaaf-c59523a23c21
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: fda23c88689d8da992a0a6be66cd61139fb37292
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="getlinenumber"></a>GetLineNumber


Ruft die Anzahl der Linie, die bei der XML-Überprüfungsfehler aufgetreten ist.

## <a name="syntax"></a>Syntax


``` syntax
HRESULT GetLineNumber
  ([out, retval] ULONG* pLineNumber)
;
```

## <a name="parameters"></a>Parameter


<a href="" id="plinenumber"></a>*pLineNumber*  
\[Skalieren\] einen Zeiger auf die Nummer der Zeile, die bei der XML-Überprüfungsfehler aufgetreten ist.

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
<td><p>Die Funktion wurde erfolgreich die Nummer der Zeile zurückgegeben.</p></td>
</tr>
<tr class="even">
<td><p>E_POINTER</p></td>
<td><p>Der Zeiger ist ungültig.</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>Verwandte Themen


[IParsingErrorInfo](iparsingerrorinfo.md)

 

 







