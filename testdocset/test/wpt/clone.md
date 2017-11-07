---
title: Wenn Sie den Klon
description: Wenn Sie den Klon
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 0f8f2e42-f67c-4523-a81a-5a2e34dc4e8f
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: d1b57ff1ed18dd92acb398fc5a9afabdbda8e134
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="clone"></a>Wenn Sie den Klon


Geklont ganze Gruppe von Fehlern und Warnungen.

## <a name="syntax"></a>Syntax


``` syntax
HRESULT Clone
  ([out] IEnumControlWarningInfo** ppEnum)
;
```

## <a name="parameters"></a>Parameter


<a href="" id="ppenum"></a>*ppEnum*  
\[Skalieren\] auf einen Zeiger auf den Speicherort des den Klon Enumerator zurückzugeben.

## <a name="return-value"></a>Rückgabewert


In der folgenden Tabelle werden die möglichen Werte beschrieben.

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


[IEnumControlWarningInfo](ienumcontrolwarninginfo.md)

 

 







