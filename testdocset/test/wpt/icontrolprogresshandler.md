---
title: IControlProgressHandler
description: IControlProgressHandler
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 05c08784-fcfe-46f8-8209-51fd2b1367fe
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 77178c34a6f89d99649b8fa313e1e4f6b7bc4358
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="icontrolprogresshandler"></a>IControlProgressHandler


Diese Schnittstelle ist eine Client-Side-Handler, von der Updates erhält, wenn die Bibliothek einen Vorgang ausführt. Die Bibliothek führt dann synchrone Rückrufe an den Client zurück, der den Status des Vorgangs angibt. Je nach die Aktion des Benutzers, dass Code die Bibliothek entweder mit dem Vorgang fortfahren oder andernfalls ihn abbrechen weist der Client zurück. Auf diese Weise können die Benutzeroberfläche dem Benutzer den Fortschritt des langer Vorgänge wie **Speichern**angezeigt. Wenn der Benutzer entscheidet, den Vorgang abzubrechen, gibt die Benutzeroberfläche den entsprechenden Code zu der Dokumentbibliothek zurück.

## <a name="syntax"></a>Syntax


``` syntax
{
  [id(1), helpstring("OnBegin")] HRESULT OnBegin();
  [id(2), helpstring("OnUpdate")] HRESULT OnUpdate
    ([in] ULONG CurrentValuePercent);
  [id(3), helpstring("OnEnd")] HRESULT OnEnd
    ([in] HRESULT hrResult);
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
<td><p>[OnBegin](onbegin.md)</p></td>
<td><p>Weist die Bibliothek, um eine Operation beginnen.</p></td>
</tr>
<tr class="even">
<td><p>[OnUpdate](onupdate.md)</p></td>
<td><p>Weist die Bibliothek, um den Fortschritt eines Vorgangs Vorgang fortzusetzen.</p></td>
</tr>
<tr class="odd">
<td><p>[OnEnd](onend.md)</p></td>
<td><p>Gibt einen Statuscode nach dem Ende eines Vorgangs.</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>Verwandte Themen


[Schnittstellen](interfaces-wprcontrol.md)

 

 







