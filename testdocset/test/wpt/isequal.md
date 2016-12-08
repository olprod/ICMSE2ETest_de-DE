---
title: IsEqual
description: IsEqual
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: b555fa8d-71fc-4ca1-a1e8-592cce52d738
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 2c7eb96c40a433b32ba3a9b1cef1a35b28f7df73
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="isequal"></a>IsEqual


Vergleicht zwei [IProfile](iprofile.md) -Objekte.

## <a name="syntax"></a>Syntax


``` syntax
HRESULT IsEqual
  ([in] IProfile* pProfile)
;
```

## <a name="parameters"></a>Parameter


<a href="" id="pprofile"></a>*pProfile*  
\[in\] einen Zeiger auf ein **IProfile** -Objekt verglichen werden soll.

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
<td><p>Die Objekte weisen dieselben Eigenschaften Profildatenbank, Sitzung und Anbieter.</p></td>
</tr>
<tr class="even">
<td><p>S_FALSE</p></td>
<td><p>Die Objekte sind nicht gleich.</p></td>
</tr>
<tr class="odd">
<td><p>E_INVALIDARG</p></td>
<td><p>Mindestens ein Argument ist ungültig. Ausführliche Informationen finden Sie unter [IParsingErrorInfo](iparsingerrorinfo.md) .</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>Verwandte Themen


[IProfile](iprofile.md)

 

 







