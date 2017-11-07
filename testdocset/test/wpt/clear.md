---
title: Transparent
description: Transparent
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 7c37cc24-75c5-45e3-b35a-7d874574ce54
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 15f6430cb65e6b579085a6f40aa538be3ddb0275
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="clear"></a>Transparent


Entfernt alle Profile aus der Auflistung.

## <a name="syntax"></a>Syntax


``` syntax
HRESULT Clear();
```

## <a name="parameters"></a>Parameter


Keiner.

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
<td><p>Die Funktion wurde erfolgreich entfernt alle Profile aus der Auflistung.</p></td>
</tr>
<tr class="even">
<td><p>E_WPRC_FAILED_TO_CLEAR_PROFILE_COLLECTION</p></td>
<td><p>Die Bibliothek konnte nicht alle Profile aus der Auflistung entfernt. Verwenden Sie [IErrorInfo](http://go.microsoft.com/fwlink/p/?linkid=217161 ) um ausführliche Fehlerinformationen.</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>Verwandte Themen


[IProfileCollection](iprofilecollection.md)

 

 







