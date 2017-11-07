---
title: DisableBootRecording
description: DisableBootRecording
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 9de515ce-d77e-4a5d-95d8-b611eea5394a
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: f3acd804f134a00ea38f514d7e7b1f0a4b242b95
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="disablebootrecording"></a>DisableBootRecording


Starten Sie deaktiviert Aufzeichnung für die Auflistung der angegebenen Profil.

## <a name="syntax"></a>Syntax


``` syntax
HRESULT DisableBootRecording
  ([in] IProfileCollection* pProfileCollection)
;
```

## <a name="parameters"></a>Parameter


<a href="" id="pprofilecollection"></a>*pProfileCollection*  
\[in\] einen Zeiger auf ein [IProfileCollection](iprofilecollection.md) -Objekt, das eine Auflistung von Profile, die entfernt werden muss enthält, damit sie nicht während des Startvorgangs starten.

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
<td><p>Die Funktion deaktiviert erfolgreich Aufzeichnung starten.</p></td>
</tr>
<tr class="even">
<td><p>E_WPRC_FAILED_TO_DISABLE_PROFILES_FOR_BOOT_TRACING</p></td>
<td><p>Die Bibliothek konnte nicht die Profile zu entfernen. Verwenden Sie [IControlErrorInfo](icontrolerrorinfo.md) , um ausführliche Informationen zu erhalten.</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>Verwandte Themen


[IOnOffTransitionManager](ionofftransitionmanager.md)

 

 







