---
title: GetElementId
description: GetElementId
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 43a95260-6098-47a9-b087-fd1b477af263
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: c49541f168fbff75272b4a695f6d901eaea4554c
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="getelementid"></a>GetElementId


Gibt den Bezeichner des Elements, die bei der XML-Überprüfungsfehler aufgetreten ist.

## <a name="syntax"></a>Syntax


``` syntax
HRESULT GetElementId
  ([out, retval] BSTR* pbstrElementId)
;
```

## <a name="parameters"></a>Parameter


<a href="" id="pbstrelementid"></a>*pbstrElementId*  
\[Skalieren\] einen Zeiger auf den Bezeichner des Elements, die bei der XML-Überprüfungsfehler aufgetreten ist.

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
<td><p>Die Funktion wurde erfolgreich die Element-ID zurückgegeben.</p></td>
</tr>
<tr class="even">
<td><p>E_POINTER</p></td>
<td><p>Der Zeiger ist ungültig.</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>Verwandte Themen


[IParsingErrorInfo](iparsingerrorinfo.md)

 

 







