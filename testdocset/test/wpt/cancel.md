---
title: Cancel
description: Cancel
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 282d79d5-7acd-442a-8528-f5894dfde2dc
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 49c4e016489e6144ec1e1d275d9fb711722f6bb1
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="cancel"></a>Cancel


Hebt auf eine Aufzeichnung ohne Speichern der Daten.

## <a name="syntax"></a>Syntax


``` syntax
HRESULT Cancel
  ([in] IProfileCollection* pProfileCollection)
;
```

## <a name="parameters"></a>Parameter


<a href="" id="pprofilecollection"></a>*pProfileCollection*  
\[in\] einen Zeiger auf ein [IProfileCollection](iprofilecollection.md) -Objekt, das enthält eine Auflistung von Profile Abbrechen.

## <a name="return-value"></a>Rückgabewert


Die folgende Tabelle beschreibt die möglichen Werte.

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
<td><p>E_INVALIDARG</p></td>
<td><p>Der Zeiger war ungültig.</p></td>
</tr>
<tr class="even">
<td><p>E_WPRC_RUNTIME_STATE_PROFILES_NOT_RUNNING</p></td>
<td><p>Das Profil wird zurzeit nicht ausgeführt.</p></td>
</tr>
<tr class="odd">
<td><p>ERROR_WMI_INSTANCE_NOT_FOUND</p></td>
<td><p>Die angeforderte Instanz wurde nicht gefunden.</p></td>
</tr>
<tr class="even">
<td><p>S_OK</p></td>
<td><p>Die Funktion wurde erfolgreich der <strong>IProfileCollection</strong>zurückgegeben.</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>Verwandte Themen


[IControlManager](icontrolmanager.md)

 

 







