---
title: ITraceMergeProperties
description: ITraceMergeProperties
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 6afd2bab-ef90-4182-9757-45d62b4be952
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: f6faf49fea713d867e30cb962c729a757c4c7d79
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="itracemergeproperties"></a>ITraceMergeProperties


Ermöglicht dem Client, um anzugeben, wie mehrere Ereignis (ETL) ablaufverfolgungsprotokolldateien zusammengeführt werden sollen, XML. Es bietet Funktionen, die Eigenschaften im XML-Format aus einer Datei oder aus einer Zeichenfolge laden.

## <a name="syntax"></a>Syntax


``` syntax
{
  [id(1), helpstring("LoadFromFile")] HRESULT LoadFromFile([in] BSTR bstrTraceMergeName, [in] BSTR bstrFileName);
  [id(2), helpstring("LoadFromString")] HRESULT LoadFromString([in] BSTR bstrTraceMerge);
  [id(3), helpstring("IsEqual")] HRESULT IsEqual([in] ITraceMergeProperties* pTraceMergeProperties);
};
```

## <a name="functions"></a>Funktionen


Die folgende Tabelle beschreibt die Funktionen, die diese Schnittstelle stellt.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Funktion</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>[IsEqual](isequal-itracemergeproperties.md)</p></td>
<td><p>Lädt die Eigenschaften aus der angegebenen Datei.</p></td>
</tr>
<tr class="even">
<td><p>[LoadFromString](loadfromstring-itracemergeproperties.md)</p></td>
<td><p>Laden die Eigenschaften aus der angegebenen Zeichenfolge.</p></td>
</tr>
<tr class="odd">
<td><p>[IsEqual](isequal-itracemergeproperties.md)</p></td>
<td><p>Vergleicht zwei <strong>ITraceMergeProperties</strong> -Objekte.</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>Verwandte Themen


[Schnittstellen](interfaces-wprcontrol.md)

 

 







