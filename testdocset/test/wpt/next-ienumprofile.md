---
title: Next
description: 'Next (weiter) '
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 488d7957-a6a6-4961-a7ff-aca254e72eb4
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 2a5ed2f511154554a005a5e163fdaeea4952d7de
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="next"></a>Next (weiter) 


Gibt ein Array, das die angegebene Anzahl von Elementen enthält.

## <a name="syntax"></a>Syntax


``` syntax
HRESULT Next
  ([in] ULONG celt,
  [out, size_is(celt), length_is(*pCeltFetched)] IProfile** prgVar,
  [out] ULONG* pCeltFetched)
;
```

## <a name="parameters"></a>Parameter


<a href="" id="celt"></a>*celt*  
\[in\] die Anzahl der zurückzugebenden Elemente.

<a href="" id="prgvar"></a>*prgVar*  
\[Skalieren\] ein Array von mindestens die Größe des *Celt*, um die Elemente enthalten.

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


[IEnumProfile](ienumprofile.md)

 

 







