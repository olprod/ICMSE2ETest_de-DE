---
title: GetObjectType hat
description: GetObjectType hat
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 5df5ef07-aad9-4bbe-a293-05dd18c4b319
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 285f15e6a31d442488f123c75bda8ba4454cd711
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="getobjecttype"></a>GetObjectType hat


Gibt den Typ des Objekts, das den Fehler verursacht hat.

## <a name="syntax"></a>Syntax


``` syntax
HRESULT GetObjectType
  ([out, retval] CObjectType* pObjectType)
;
```

## <a name="parameters"></a>Parameter


<a href="" id="pobjecttype"></a>*pObjectType*  
\[Skalieren\] Zeiger auf das **CObjectType** dar, der das Element angibt, die den Fehler verursacht hat.

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
<td><p>Die Funktion wurde erfolgreich den Objekttyp zurückgegeben.</p></td>
</tr>
<tr class="even">
<td><p>E_POINTER</p></td>
<td><p>Ungültiger Zeiger.</p></td>
</tr>
</tbody>
</table>

 

## <a name="remarks"></a>Hinweise


Der Objekttyp kann einen der folgenden Werte:

-   Unbekannt

-   Profil

-   Collector

-   Provider

## <a name="related-topics"></a>Verwandte Themen


[IControlErrorInfo](icontrolerrorinfo.md)

 

 







