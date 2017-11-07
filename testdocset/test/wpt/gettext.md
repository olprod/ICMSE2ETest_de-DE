---
title: '&quot;GetText&quot;'
description: '&quot;GetText&quot;'
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 6abaf7c8-ce52-48af-b4cd-a0039123140c
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 80cb27be746f0bf9783e3cb303e1b6190428f22d
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="gettext"></a>"GetText"


Ruft den angegebenen Text.

## <a name="syntax"></a>Syntax


``` syntax
HRESULT GetText
  ([in] ULONG iText,
  [out] BSTR* pbstrText)
;
```

## <a name="parameters"></a>Parameter


<a href="" id="itext"></a>*iText*  
\[in\]

<a href="" id="pbstrtext"></a>*pbstrText*  
\[Skalieren\] ein Zeiger auf die Textzeichenfolge.

## <a name="return-value"></a>Rückgabewert


In der folgenden Tabelle werden mögliche Rückgabewerte beschrieben. Fehler bei Rückgabewerte sind implementierungsspezifischen.

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
<td><p>Gibt Erfolg an.</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>Verwandte Themen


[ITraceMergeTextHandler](itracemergetexthandler.md)

 

 







