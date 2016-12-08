---
title: Entfernen
description: Entfernen
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 41897744-5d47-4fec-8f9d-490e98e17e14
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 62bebb62c6cefeeb7f4f158801cde256f7941d32
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="remove"></a>Entfernen


Entfernt ein [IProfile](iprofile.md) -Objekt aus der Auflistung.

## <a name="syntax"></a>Syntax


``` syntax
HRESULT Remove
  ([in] IProfile* pProfile)
;
```

## <a name="parameters"></a>Parameter


<a href="" id="pprofile"></a>*pProfile*  
\[in\] einen Zeiger auf das **IProfile** Objekt aus der Auflistung entfernt werden soll.

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
<td><p>Die Funktion wird das Profil erfolgreich aus der Auflistung entfernt.</p></td>
</tr>
<tr class="even">
<td><p>E_INVALIDARG</p></td>
<td><p>Das Argument ist ungültig. Verwenden Sie [IErrorInfo](http://go.microsoft.com/fwlink/p/?linkid=217161) , um ausführliche Fehlerinformationen.</p></td>
</tr>
<tr class="odd">
<td><p>E_WPRC_FAILED_TO_REMOVE_PROFILE</p></td>
<td><p>Die Bibliothek konnte nicht das Profil aus der Auflistung zu entfernen. Verwenden Sie <strong>IErrorInfo</strong> , um ausführliche Fehlerinformationen.</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>Verwandte Themen


[IProfileCollection](iprofilecollection.md)

 

 







