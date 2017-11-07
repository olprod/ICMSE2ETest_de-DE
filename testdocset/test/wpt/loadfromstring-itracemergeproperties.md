---
title: LoadFromString
description: LoadFromString
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: c1066650-2cf9-4ac0-bf68-9895465a844d
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: beadf42e90081242720646b94512b49114f4cd73
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="loadfromstring"></a>LoadFromString


Lasten Trace Merge Eigenschaften aus einer XML-Definitionszeichenfolge.

## <a name="syntax"></a>Syntax


``` syntax
HRESULT LoadFromString
  ([in] BSTR bstrTraceMerge)
;
```

## <a name="parameters"></a>Parameter


<a href="" id="bstrtracemerge"></a>*bstrTraceMerge*  
\[in\] eine Zeichenfolge, die die XML-formatierte Trace Merge-Eigenschaften enthält.

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
<td><p>Die Aktionsroutine wird von die Funktion erfolgreich geladen.</p></td>
</tr>
<tr class="even">
<td><p>E_INVALIDARG</p></td>
<td><p>Mindestens ein Argument ist ungültig. Verwenden Sie [IParsingErrorInfo](iparsingerrorinfo.md) um ausführliche Fehlerinformationen.</p></td>
</tr>
<tr class="odd">
<td><p>E_WPRC_FAILED_TO_VALIDATE_TRACEMERGE_PROPERTIES</p></td>
<td><p>Die Bibliothek konnte nicht den XML-CODE der Trace Merge Eigenschaften zu überprüfen. Verwenden Sie <strong>IParsingErrorInfo</strong> um ausführliche Fehlerinformationen.</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>Verwandte Themen


[ITraceMergeProperties](itracemergeproperties.md)

 

 







