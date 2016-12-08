---
title: GetColumnNumber
description: GetColumnNumber
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: abe730ac-4c04-48f0-b37c-6e096dca07c5
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 1d9e3ff79047a45f7df055661a00d64224ffef2b
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="getcolumnnumber"></a>GetColumnNumber


Ruft die Anzahl der Spalten, die bei der XML-Überprüfungsfehler aufgetreten ist.

## <a name="syntax"></a>Syntax


``` syntax
HRESULT GetColumnNumber
  ([out, retval] ULONG* pColumnNumber)
;
```

## <a name="parameters"></a>Parameter


<a href="" id="pcolumnnumber"></a>*pColumnNumber*  
\[Skalieren\] ein Zeiger auf die Anzahl der Spalten, die bei der XML-Überprüfungsfehler aufgetreten ist.

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
<td><p>Die Funktion wurde erfolgreich die Spaltennummer zurückgegeben.</p></td>
</tr>
<tr class="even">
<td><p>E_POINTER</p></td>
<td><p>Gibt ein ungültiger Zeiger an.</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>Verwandte Themen


[IParsingErrorInfo](iparsingerrorinfo.md)

 

 







