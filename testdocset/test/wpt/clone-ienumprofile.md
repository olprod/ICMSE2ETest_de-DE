---
title: Wenn Sie den Klon
description: Wenn Sie den Klon
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 057b095c-c244-434e-bf0f-09fb54089390
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: cb7606ab61862e2e418e7867a6a97ef9fa9e3258
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="clone"></a>Wenn Sie den Klon


Erstellt einen Klon Enumerator.

## <a name="syntax"></a>Syntax


``` syntax
HRESULT Clone
  ([out] IEnumProfile** ppEnum)
;
```

## <a name="parameters"></a>Parameter


<a href="" id="ppenum"></a>*ppEnum*  
\[Skalieren\] gibt einen Zeiger auf den Speicherort des den Klon Enumerator.

## <a name="return-value"></a>Rückgabewert


In der folgenden Tabelle werden mögliche Rückgabewerte beschrieben.

## <a name="exceptions"></a>Ausnahmen


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
<td><p>Die Funktion den Klon Enumerator erfolgreich erstellt.</p></td>
</tr>
<tr class="even">
<td><p>E_OUTOFMEMORY</p></td>
<td><p>Nicht genügend Speicherplatz zum Abschließen des Vorgangs angibt.</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>Verwandte Themen


[IEnumProfile](ienumprofile.md)

 

 







