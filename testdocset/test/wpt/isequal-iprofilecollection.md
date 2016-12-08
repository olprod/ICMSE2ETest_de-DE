---
title: IsEqual
description: IsEqual
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 358b6599-0360-47ee-bac7-8ae0f119c01f
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: d7330fa7884dfecb104dabd316d83881efb60366
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="isequal"></a>IsEqual


Vergleicht zwei [IProfileCollection](iprofilecollection.md) -Objekte, um festzustellen, ob sie übereinstimmende Profileigenschaften besitzen. Der Profile Sortierung wird nicht berücksichtigt.

## <a name="syntax"></a>Syntax


``` syntax
HRESULT IsEqual
  ([in] IProfileCollection* pProfileCollection)
;
```

## <a name="parameters"></a>Parameter


<a href="" id="pprofilecollection"></a>*pProfileCollection*  
\[in\] einen Zeiger auf das **IProfileCollection** -Objekt verglichen werden soll.

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
<td><p>Die Auflistungen Profil sind gleich.</p></td>
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


[IProfileCollection](iprofilecollection.md)

 

 







