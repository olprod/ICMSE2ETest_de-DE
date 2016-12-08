---
title: Update
description: Update
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 4d3707c3-2694-47e9-845b-8d3767c0b2cc
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: e46e4d41257b5bb0915c53f02e7e615534ce363e
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="update"></a>Update


Aktualisiert eine Benutzerprofildienst-Auflistung.

## <a name="syntax"></a>Syntax


``` syntax
HRESULT Update
  ([in] IProfileCollection* pProfileCollection)
;
```

## <a name="parameters"></a>Parameter


<a href="" id="pprofilecollection"></a>*pProfileCollection*  
\[in\] einen Zeiger auf das [IProfileCollection](iprofilecollection.md) Objekt, das enthält eine Auflistung von Profile zu aktualisieren.

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
<td><p>Die Funktion wurde erfolgreich aktualisiert die <strong>IProfileCollection</strong>.</p></td>
</tr>
<tr class="even">
<td><p>E_INVALIDARG</p></td>
<td><p>Mindestens ein Argument ist ungültig.</p></td>
</tr>
<tr class="odd">
<td><p>E_WPRC_FAILED_TO_UPDATE_PROFILE</p></td>
<td><p>Die Bibliothek konnte ein Profil in der Auflistung Profil zu aktualisieren. Verwenden Sie [IControlErrorInfo](icontrolerrorinfo.md) , um ausführliche Fehlerinformationen.</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>Verwandte Themen


[IControlManager](icontrolmanager.md)

 

 







