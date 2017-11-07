---
title: IEnumProfile
description: IEnumProfile
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: a7f512d4-13dd-44be-881b-2b705deb973a
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: aa7de8478e29e62c373eee31d066fbdac72cfe54
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="ienumprofile"></a>IEnumProfile


Bietet eine COM-Enumeration Standardmethode für eine Auflistung von [IProfile](iprofile.md) -Schnittstellen auflisten.

## <a name="syntax"></a>Syntax


``` syntax
{
  [id(1), helpstring("Next")] HRESULT Next
    ([in] ULONG celt,
    [out, size_is(celt), length_is(*pCeltFetched)] IProfile** prgVar,
    [out] ULONG* pCeltFetched);
  [id(2), helpstring("Skip")] HRESULT Skip
    ([in] ULONG celt);
  [id(3), helpstring("Reset")] HRESULT Reset();
  [id(4), helpstring("Clone")] HRESULT Clone
    ([out] IEnumProfile** ppEnum);
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
<th>Methode</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>[Nächste](next-ienumprofile.md)</p></td>
<td><p>Gibt ein Array, das die angegebene Anzahl von Elementen enthält.</p></td>
</tr>
<tr class="even">
<td><p>[Überspringen](skip-ienumprofile.md)</p></td>
<td><p>Gibt die Anzahl von zu überspringenden Elemente.</p></td>
</tr>
<tr class="odd">
<td><p>[Zurücksetzen](reset-ienumprofile.md)</p></td>
<td><p>Setzt die Enumeration zurück.</p></td>
</tr>
<tr class="even">
<td><p>[Wenn Sie den Klon](clone-ienumprofile.md)</p></td>
<td><p>Erstellt einen Klon Enumerator.</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>Verwandte Themen


[Schnittstellen](interfaces-wprcontrol.md)

 

 







