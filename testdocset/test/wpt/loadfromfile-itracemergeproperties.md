---
title: LoadFromFile
description: LoadFromFile
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 73d323b7-1a32-4f0a-aa5a-bd61d96af687
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 373d41207a35324b0065b3c5f797db49dce01b3e
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="loadfromfile"></a>LoadFromFile


Lasten Trace Merge Eigenschaften aus einer Datei.

## <a name="syntax"></a>Syntax


``` syntax
HRESULT LoadFromFile
  ([in] BSTR bstrTraceMergeName,
  [in] BSTR bstrFileName)
;
```

## <a name="parameters"></a>Parameter


<a href="" id="bstrtracemergename"></a>*bstrTraceMergeName*  
\[in\] den Namen der Seriendruck Eigenschaften geladen werden.

<a href="" id="bstrfilename"></a>*bstrFileName*  
\[in\] den Namen der Datei, die die *BstrTraceMergeName* Merge Eigenschaften enthält.

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
<td><p>Die Funktion wurde erfolgreich geladen, die Eigenschaften.</p></td>
</tr>
<tr class="even">
<td><p>E_INVALIDARG</p></td>
<td><p>Mindestens ein Argument ist ungültig. Verwenden Sie [IParsingErrorInfo](iparsingerrorinfo.md) um ausführliche Fehlerinformationen.</p></td>
</tr>
<tr class="odd">
<td><p>E_WPRC_FAILED_TO_VALIDATE_TRACEMERGE_PROPERTIES</p></td>
<td><p>Die Bibliothek konnte nicht den XML-CODE überprüfen, die die Ablaufverfolgungsprotokoll Merge Eigenschaften definiert. Verwenden Sie <strong>IParsingErrorInfo</strong> , um ausführliche Fehlerinformationen.</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>Verwandte Themen


[ITraceMergeProperties](itracemergeproperties.md)

 

 







