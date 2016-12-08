---
title: IProfileCollection
description: IProfileCollection
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 74833b03-86f0-4909-b497-f409365d4ea7
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: d947dc73b6b5a11e9220e536664a280080aa4bfa
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="iprofilecollection"></a>IProfileCollection


Stellt eine Auflistung von Profilen, die als Einheit die Bibliothek ausgeführt wird. Die Benutzeroberfläche bietet Funktionen, mit denen den Client ein Profil zur Auflistung hinzufügen, vergleichen ein Profil bereits in der Auflistung der entfernen Sie eine oder alle Profile aus der Auflistung.

## <a name="syntax"></a>Syntax


``` syntax
{
    [id(1), helpstring("Add")] HRESULT Add([in] IProfile* pProfile, [in] VARIANT_BOOL fMerge);
    [id(2), helpstring("Remove")] HRESULT Remove([in] IProfile* pProfile);
    [id(3), helpstring("Clear")] HRESULT Clear();
    [id(4), helpstring("IsEqual")] HRESULT IsEqual([in] IProfileCollection* pProfileCollection);    [id(5), helpstring("LoadIntoXML")] HRESULT LoadIntoXML([out] BSTR* pbstrResults);
};
```

## <a name="functions"></a>Funktionen


In der folgenden Tabelle werden die Funktionen, die diese Schnittstelle stellt beschrieben.

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
<td><p>[Fügen Sie hinzu](add.md)</p></td>
<td><p>Der Auflistung hinzugefügt ein Profil.</p></td>
</tr>
<tr class="even">
<td><p>[Entfernen](remove.md)</p></td>
<td><p>Entfernt ein Profil aus der Auflistung.</p></td>
</tr>
<tr class="odd">
<td><p>[Löschen](clear.md)</p></td>
<td><p>Löscht alle Profile aus der Auflistung.</p></td>
</tr>
<tr class="even">
<td><p>[IsEqual](isequal-iprofilecollection.md)</p></td>
<td><p>Vergleicht zwei <strong>IProfileCollection</strong> -Objekte, um festzustellen, ob sie übereinstimmende Profileigenschaften besitzen.</p></td>
</tr>
<tr class="odd">
<td><p>[LoadIntoXML](loadintoxml.md)</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>Verwandte Themen


[Schnittstellen](interfaces-wprcontrol.md)

 

 







