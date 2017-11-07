---
title: MergeShutdownRecording
description: MergeShutdownRecording
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 3f8ac92e-53f4-4f48-8862-d165c84b697e
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 3518cd581cf404884f76f73ce4be3160730102f6
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="mergeshutdownrecording"></a>MergeShutdownRecording


Aufzeichnungen, die während des letzten Herunterfahrens gesammelt werden.

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
\[in\] gibt den Namen der Datei Ereignis Tracing für Windows (ETL-) angemeldet sein.

<a href="" id="pprofilecollection"></a>*pProfileCollection*  
\[in\] einen Zeiger auf ein Objekt **IProfileCollection** .

<a href="" id="ptracemergeproperties"></a>*pTraceMergeProperties*  
\[in\] einen Zeiger auf ein **ITraceMergeProperties** -Objekt.

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
<td><p>E_POINTER</p></td>
<td><p>Mindestens eines der Argumente der Funktion ist null.</p></td>
</tr>
<tr class="even">
<td><p>E_WPRC_INVALID_MERGESHUTDOWN_OPERATION</p></td>
<td><p>Gibt an einen Vorgang nicht erfolgreich. Dies kann vorkommen, wenn keine Herunterfahren Aufzeichnung während der letzten Herunterfahren ausgeführt wurde.</p></td>
</tr>
<tr class="odd">
<td><p>E_WPRC_RUNTIME_STATE_PROFILES_NOT_RUNNING</p></td>
<td><p>Gibt an, dass das Profil nicht ausgeführt wird. Dies kann vorkommen, wenn keine Herunterfahren Aufzeichnung während der letzten Herunterfahren ausgeführt wurde.</p></td>
</tr>
<tr class="even">
<td><p>S_OK</p></td>
<td><p>Die Funktion zusammengeführt wurde erfolgreich Aufzeichnung Herunterfahren.</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>Verwandte Themen


[IOnOffTransitionManager](ionofftransitionmanager.md)

 

 







