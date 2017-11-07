---
title: Stopp
description: Stopp
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 7f5736cc-4ec7-4b6a-bf93-b421a3fd5c39
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 2f1d6b6f2acdfbe896398482ae759ffe1f117ac0
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="stop"></a>Stopp


Beendet eine Aufzeichnung im Dateimodus Protokollierung.

## <a name="syntax"></a>Syntax


``` syntax
HRESULT Stop
  ([in] BSTR bstrFileName,
  [in] IProfileCollection* pProfileCollection,
  [in] ITraceMergeProperties* pTraceMergeProperties)
;
```

## <a name="parameters"></a>Parameter


<a href="" id="bstrfilename"></a>*bstrFileName*  
\[in\] den Namen der Datei, welche verbundene Ereignisse aus Aufzeichnungen aller die Profile gespeichert sind.

<a href="" id="pprofilecollection"></a>*pProfileCollection*  
\[in\] einen Zeiger auf ein [IProfileCollection](iprofilecollection.md) -Objekt, das eine Auflistung von Profile speichern enthält.

<a href="" id="ptracemergeproperties"></a>*pTraceMergeProperties*  
\[in\] einen Zeiger auf ein [ITraceMergeProperties](itracemergeproperties.md) Objekt, das Eigenschaften mit dem Zusammenführen von Aufzeichnungen enthält.

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
<td><p>Die Funktion wurde erfolgreich beendet die Aufzeichnung.</p></td>
</tr>
<tr class="even">
<td><p>E_INVALIDARG</p></td>
<td><p>Mindestens ein Argument ist ungültig.</p></td>
</tr>
<tr class="odd">
<td><p>E_WPRC_FAILED_TO_STOP_PROFILE</p></td>
<td><p>Die Bibliothek konnte nicht beendet werden in der Auflistung Profil ein Profil. Verwenden Sie [IControlErrorInfo](icontrolerrorinfo.md) , um ausführliche Fehlerinformationen.</p></td>
</tr>
<tr class="even">
<td><p>E_WPRC_TRACE_MERGE_LOST_EVENTS</p></td>
<td><p>Die Event Tracing for Windows (ETW) Sitzung verloren Ereignisse, und Zusammenführen von der Ereignis (ETL) Ablaufverfolgungsdateien aus der Sitzung kann unvollständige ETL-Datei erstellen.</p></td>
</tr>
</tbody>
</table>

 

## <a name="remarks"></a>Hinweise


Verwenden Sie diese Funktion nur für Profile, die nacheinander in eine Datei protokollieren. Nachdem die Sitzungen gespeichert sind, wird die Aufzeichnung beendet.

## <a name="related-topics"></a>Verwandte Themen


[IControlManager](icontrolmanager.md)

 

 







