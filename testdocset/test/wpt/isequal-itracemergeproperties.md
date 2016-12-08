---
title: IsEqual
description: IsEqual
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: ad2c2023-6748-4fc3-b2c4-02bf92637dc0
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: a9a5af2d07ccbbae535289ef80e5f3fbf2d1ab2c
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="isequal"></a>IsEqual


Vergleicht zwei [ITraceMergeProperties](itracemergeproperties.md) -Objekte.

## <a name="syntax"></a>Syntax


``` syntax
HRESULT IsEqual
  ([in] ITraceMergeProperties* pTraceMergeProperties)
;
```

## <a name="parameters"></a>Parameter


<a href="" id="ptracemergeproperties"></a>*pTraceMergeProperties*  
\[in\] einen Zeiger auf ein Objekt **ITraceMergeProperties** verglichen werden soll.

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
<td><p>Die Objekte weisen dieselbe Trace Eigenschaften zusammenführen.</p></td>
</tr>
<tr class="even">
<td><p>S_FALSE</p></td>
<td><p>Die Objekte müssen nicht die gleichen Trace Merge-Eigenschaften.</p></td>
</tr>
<tr class="odd">
<td><p>E_INVALIDARG</p></td>
<td><p>Mindestens ein Argument ist ungültig. Verwenden Sie [IParsingErrorInfo](iparsingerrorinfo.md) um ausführliche Fehlerinformationen.</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>Verwandte Themen


[ITraceMergeProperties](itracemergeproperties.md)

 

 







