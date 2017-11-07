---
title: UpdateShutdownRecording
description: UpdateShutdownRecording
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 0efaf47c-ca92-4be2-bfd4-f71a6b300297
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 18f10624ad93e2c7ddd75bfc1051d94acc719431
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="updateshutdownrecording"></a>UpdateShutdownRecording


Herunterfahren Aufzeichnung aktualisiert.

## <a name="syntax"></a>Syntax


``` syntax
HRESULT MergeShutdownRecording
  ([in] BSTR bstrFileName,
  [in] IProfileCollection* pProfileCollection,
  [in] ITraceMergeProperties* pTraceMergeProperties)
;
```

## <a name="parameters"></a>Parameter


<a href="" id="bstrfilename"></a>*bstrFileName*  
\[in\] gibt den Namen des Ereignisses (ETL) Ablaufverfolgungsprotokolldatei an die Ereignisse protokolliert werden.

<a href="" id="pprofilecollection"></a>*pProfileCollection*  
\[in\] gibt das **IProfileCollection** -Objekt.

<a href="" id="ptracemergeproperties"></a>*pTraceMergeProperties*  
\[in\] gibt das **ITraceMergeProperties** -Objekt.

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
<td><p>Die Funktion wurde erfolgreich aktualisiert Aufzeichnung Herunterfahren.</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>Verwandte Themen


[IOnOffTransitionManager](ionofftransitionmanager.md)

 

 







