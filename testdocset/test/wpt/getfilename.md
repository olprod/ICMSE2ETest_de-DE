---
title: GetFileName
description: GetFileName
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 15f12bd8-a977-4c39-8da7-74b51bd7d54a
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: b6b72776e8c90355498b12bcf0bd22b87497ceea
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="getfilename"></a>GetFileName


Ruft die Zeichenfolge aus der angegebenen Datei.

## <a name="syntax"></a>Syntax


``` syntax
HRESULT GetFileName
  ([out] BSTR* pbstrFileName)
;
```

## <a name="parameters"></a>Parameter


<a href="" id="pbstrfilename"></a>*pbstrFileName*  
\[Skalieren\] einen Zeiger auf den Dateinamen der Zeichenfolge.

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

 

 







