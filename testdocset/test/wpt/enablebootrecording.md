---
title: EnableBootRecording
description: EnableBootRecording
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: a1b68ad9-c479-4646-be41-a1dfbf346369
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: c9a364ff9657862d94bdb71ed530d1ba0239c6df
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="enablebootrecording"></a>EnableBootRecording


Ermöglicht das Starten Aufzeichnung für die angegebene Profil-Auflistung.

## <a name="syntax"></a>Syntax


``` syntax
HRESULT EnableBootRecording
  ([in] IProfileCollection* pProfileCollection)
;
```

## <a name="parameters"></a>Parameter


<a href="" id="pprofilecollection"></a>*pProfileCollection*  
\[in\] einen Zeiger auf ein [IProfileCollection](iprofilecollection.md) -Objekt, das eine Auflistung von Profile beim Starten des Computers enthält.

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
<td><p>Aufzeichnung Boot Funktion erfolgreich aktiviert.</p></td>
</tr>
<tr class="even">
<td><p>E_WPRC_FAILED_TO_ENABLE_PROFILES_FOR_BOOT_TRACING</p></td>
<td><p>Die Profile speichern die Bibliothek ist fehlgeschlagen. Verwenden Sie [IControlErrorInfo](icontrolerrorinfo.md) , um ausführliche Informationen zu erhalten.</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>Verwandte Themen


[IOnOffTransitionManager](ionofftransitionmanager.md)

 

 







