---
title: Speichern
description: Speichern
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: eedd3310-1f95-4e44-9be2-b33ed98dfa9a
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: afdfca25fdaf0cb5f9b7a58836f2d78ed4fd3684
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="save"></a>Speichern


Speichert eine Aufzeichnung, die in zirkulären Puffer im Arbeitsspeicher auf das angegebene Ereignis Ablaufverfolgungs-Protokolldatei (ETL) angemeldet ist. Die Aufzeichnung wird weiterhin ausgeführt.

## <a name="syntax"></a>Syntax


``` syntax
HRESULT Save
  ([in] BSTR bstrFileName,
  [in] IProfileCollection* pProfileCollection,
  [in] ITraceMergeProperties* pTraceMergeProperties)
;
```

## <a name="parameters"></a>Parameter


<a href="" id="bstrfilename"></a>*bstrFileName*  
\[in\] den Namen der Datei, welche verbundene Ereignisse aus Aufzeichnungen aller die Profile gespeichert sind.

<a href="" id="pprofilecollection"></a>*pProfileCollection*  
\[in\] einen Zeiger auf das [IProfileCollection](iprofilecollection.md) -Objekt, das eine Auflistung von Profile speichern enthält.

<a href="" id="ptracemergeproperties"></a>*pTraceMergeProperties*  
\[in\] ein Zeiger auf das [ITraceMergeProperties](itracemergeproperties.md) -Objekt, das Eigenschaften mit dem Zusammenführen von Aufzeichnungen enthält.

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
<td><p>Die Funktion wurde erfolgreich die Aufzeichnung gespeichert.</p></td>
</tr>
<tr class="even">
<td><p>E_INVALIDARG</p></td>
<td><p>Mindestens ein Argument ist ungültig.</p></td>
</tr>
<tr class="odd">
<td><p>E_WPRC_FAILED_TO_SAVE_PROFILE</p></td>
<td><p>Die Bibliothek konnte nicht in der Auflistung Profil ein Profil zu speichern. Verwenden Sie [IControlErrorInfo](icontrolerrorinfo.md) , um ausführliche Fehlerinformationen.</p></td>
</tr>
<tr class="even">
<td><p>E_WPRC_TRACE_MERGE_LOST_EVENTS</p></td>
<td><p>Die Sitzung Event Tracing for Windows (ETW) Ereignisse verloren, und Zusammenführen von der Event Trace (ETL) Protokolldateien aus der Sitzung kann eine unvollständige ETL-Datei erstellen.</p></td>
</tr>
</tbody>
</table>

 

## <a name="remarks"></a>Hinweise


Diese Funktion wird nur für Profile verwendet, die zirkulären Puffer protokollieren. Nachdem die Sitzungen gespeichert werden, wird die Aufzeichnung weiterhin ausgeführt.

## <a name="related-topics"></a>Verwandte Themen


[IControlManager](icontrolmanager.md)

 

 







