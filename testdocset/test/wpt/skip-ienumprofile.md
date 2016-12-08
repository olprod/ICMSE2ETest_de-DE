---
title: "Überspringen"
description: "Überspringen"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 3cf0d9c8-d456-424a-8d33-1f900f78595e
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 264fe68623582c1145f5bf80a7074cb05d9ae6d9
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="skip"></a>Überspringen


Gibt die Anzahl von zu überspringenden Elemente.

## <a name="syntax"></a>Syntax


``` syntax
HRESULT Skip
  ([in] ULONG celt)
;
```

## <a name="parameters"></a>Parameter


<a href="" id="celt"></a>*celt*  
\[in\] der Anzahl von zu überspringenden Elemente.

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
<td><p>Die Funktion wurde erfolgreich die Anzahl der zu überspringenden Elemente zurückgegeben.</p></td>
</tr>
<tr class="even">
<td><p>S_FALSE</p></td>
<td><p>Die Anzahl der zurückgegebenen Elemente ist kleiner dann <em>Celt</em>.</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>Verwandte Themen


[IEnumProfile](ienumprofile.md)

 

 







