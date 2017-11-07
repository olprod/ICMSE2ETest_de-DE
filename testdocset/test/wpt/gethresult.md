---
title: GetHResult
description: GetHResult
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 5c7606d5-3a6d-4dc5-b232-ed24974d662c
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 081288b791b6bf7fdc52df51569fca9418522a9e
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="gethresult"></a>GetHResult


Gibt einen HRESULT-Wert, der den Fehlercode angibt.

## <a name="syntax"></a>Syntax


``` syntax
HRESULT GetHResult
  ([out, retval] HRESULT* pHResult)
;
```

## <a name="parameters"></a>Parameter


<a href="" id="phresult"></a>*pHResult*  
\[Skalieren\] Zeiger auf den HRESULT-Wert, der den Fehlercode angibt.

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
<td><p>Die Funktion wurde erfolgreich den Fehlercode zurückgegeben.</p></td>
</tr>
<tr class="even">
<td><p>E_POINTER</p></td>
<td><p>Ungültiger Zeiger.</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>Verwandte Themen


[IControlErrorInfo](icontrolerrorinfo.md)

 

 







