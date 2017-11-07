---
title: GetElementType
description: GetElementType
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 4546c402-5966-4f36-acad-51418a1698d1
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 4cfd8e0fbcf6b846130a5c3431a3483a473a96a9
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="getelementtype"></a>GetElementType


Gibt den Typ des Elements, die bei der XML-Überprüfungsfehler aufgetreten ist.

## <a name="syntax"></a>Syntax


``` syntax
HRESULT GetElementType
  ([out, retval] BSTR* pbstrElementType)
;
```

## <a name="parameters"></a>Parameter


<a href="" id="pbstrelementtype"></a>*pbstrElementType*  
\[Skalieren\] einen Zeiger auf den Typ des Elements, die bei der XML-Überprüfungsfehler aufgetreten ist.

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
<td><p>Typ des Elements wurde erfolgreich von die Funktion zurückgegeben.</p></td>
</tr>
<tr class="even">
<td><p>E_POINTER</p></td>
<td><p>Der Zeiger ist ungültig.</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>Verwandte Themen


[IParsingErrorInfo](iparsingerrorinfo.md)

 

 







