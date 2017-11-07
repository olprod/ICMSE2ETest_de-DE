---
title: IEnumControlWarningInfo
description: IEnumControlWarningInfo
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 49078217-91ef-444e-9d08-88f87d1b0280
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: b8c9082e82bb5f5aba51ad38933df559c9a930cc
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="ienumcontrolwarninginfo"></a>IEnumControlWarningInfo


Bietet eine COM-Enumeration Standardmethode für eine Auflistung von [IControlErrorInfo](icontrolerrorinfo.md) -Schnittstellen auflisten. Sobald die Bibliothek einen Vorgang wie Start- oder Update ausführt, kann es nicht einige Anbieter, z. B. aktivieren, die auf dem System nicht unterstützt werden. In diesem Fall erstellt die Bibliothek eine Liste von **IControlErrorInfo** -Objekten, von die jedes ausführlichere kontextbezogene Fehlerinformationen enthält, die beschreibt, warum der Anbieter nicht aktiviert wurde. Der Client kann Abfragen diese Schnittstelle aus [IControlManager](icontrolmanager.md) , um festzustellen, ob die Fehler aufgelistet sind.

## <a name="syntax"></a>Syntax


``` syntax
{
  [id(1), helpstring("Next")] HRESULT Next
    ([in] ULONG celt,
    [out, size_is(celt), length_is(*pCeltFetched)] IControlErrorInfo** prgVar,
    [out] ULONG* pCeltFetched);
  [id(2), helpstring("Skip")] HRESULT Skip
    ([in] ULONG celt);
  [id(3), helpstring("Reset")] HRESULT Reset();
  [id(4), helpstring("Clone")] HRESULT Clone
    ([out] IEnumControlWarningInfo** ppEnum);
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
<td><p>[Nächste](next.md)</p></td>
<td><p>Gibt ein Array, das die angegebene Anzahl von Elementen enthält.</p></td>
</tr>
<tr class="even">
<td><p>[Überspringen](skip.md)</p></td>
<td><p>Gibt die Anzahl von zu überspringenden Elemente.</p></td>
</tr>
<tr class="odd">
<td><p>[Zurücksetzen](reset.md)</p></td>
<td><p>Setzt die Enumeration zurück.</p></td>
</tr>
<tr class="even">
<td><p>[Wenn Sie den Klon](clone.md)</p></td>
<td><p>Erstellt einen Klon Enumerator.</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>Verwandte Themen


[Schnittstellen](interfaces-wprcontrol.md)

 

 







