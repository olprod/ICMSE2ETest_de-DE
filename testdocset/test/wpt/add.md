---
title: Add
description: Add
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 85e46ed9-12d7-45b8-8e5a-ffbd9193e668
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 80dd6e869ece0e9b7f42c796af92c385479f321e
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="add"></a>Add


Der Auflistung hinzugefügt ein Profil.

## <a name="syntax"></a>Syntax


``` syntax
HRESULT Add
  ([in] IProfile* pProfile,
  [in] VARIANT_BOOL fMerge)
;
```

## <a name="parameters"></a>Parameter


<a href="" id="pprofile"></a>*pProfile*  
\[in\] einen Zeiger auf ein **IProfile** Objekt, das der Auflistung hinzugefügt werden soll.

<a href="" id="fmerge"></a>*fMerge*  
\[in\] ein Boolean-Wert, der angibt, ob die *pProfile* mit einem in der Auflistung mit dem gleichen Namen zusammengeführt. Wenn ein änderbare Profil in der Auflistung ist, und dieser Parameter auf TRUE festgelegt ist, werden die Profile zusammengeführt. Andernfalls gibt die Methode einen Fehler zurück. Wenn ein Profil mit dem gleichen Namen in die Auflistung nicht vorhanden ist, wird die Methode ignoriert diesen Parameter und der Auflistung mit das Profil hinzugefügt.

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
<td><p>Die Funktion wird das Profil erfolgreich zur Auflistung hinzugefügt.</p></td>
</tr>
<tr class="even">
<td><p>E_INVALIDARG</p></td>
<td><p>Mindestens ein Argument ist ungültig. Verwenden Sie [IErrorInfo](http://go.microsoft.com/fwlink/p/?linkid=217161) um ausführliche Fehlerinformationen.</p></td>
</tr>
<tr class="odd">
<td><p>E_WPRC_FAILED_TO_ADD_PROFILE</p></td>
<td><p>Die Bibliothek konnte nicht-Auflistung ein Profil hinzugefügt. Verwenden Sie <strong>IErrorInfo</strong> um ausführliche Fehlerinformationen.</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>Verwandte Themen


[IProfileCollection](iprofilecollection.md)

 

 







