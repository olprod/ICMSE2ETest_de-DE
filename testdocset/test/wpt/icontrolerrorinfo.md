---
title: IControlErrorInfo
description: IControlErrorInfo
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 47dd2be1-9217-4045-b530-c8b022c3c794
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 4e993102972e02eeaab429a2e5599f8e2d5c7511
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="icontrolerrorinfo"></a>IControlErrorInfo


Bietet Funktionen, die Abrufen von Informationen zu Fehlern, die auftreten, wenn der Steuerelement-Manager einen Vorgang ausführt. Der Fehler gibt an, den Typ des Objekts auf dem der Fehler aufgetreten ist: Profil, Collector oder Anbieter. Diese Schnittstelle kann geschachtelt werden, um eine Hierarchie von Fehlerinformationen bereitzustellen. Die Schnittstelle wird von der COM- [IErrorInfo](http://go.microsoft.com/fwlink/p/?linkid=217161) -Schnittstelle, die Funktionen bereitstellt, die kontextbezogene Fehlerinformationen zugreifen.

## <a name="syntax"></a>Syntax


``` syntax
{
  typedef enum
  {
    ObjectType_Unknown,
    ObjectType_Profile,
    ObjectType_Collector,
    ObjectType_Provider
  } CObjectType;
  [id(1), helpstring("GetObjectType")] HRESULT GetObjectType
    ([out, retval] CObjectType* pObjectType);
  [id(2), helpstring("GetHResult")] HRESULT GetHResult
    ([out, retval] HRESULT* pHResult);
  [id(3), helpstring("GetInnerErrorInfo")] HRESULT GetInnerErrorInfo
    ([out, retval] IUnknown** ppVal);
};
```

## <a name="functions"></a>Funktionen


In der folgenden Tabelle werden die Funktionen dieser Schnittstelle beschrieben.

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
<td><p>[GetObjectType hat](getobjecttype.md)</p></td>
<td><p>Gibt den Typ, der den Fehler verursacht hat.</p></td>
</tr>
<tr class="even">
<td><p>[GetHResult](gethresult.md)</p></td>
<td><p>Gibt einen HRESULT-Wert, der den Fehlercode angibt.</p></td>
</tr>
<tr class="odd">
<td><p>[GetInnerErrorInfo](getinnererrorinfo.md)</p></td>
<td><p>Zusätzliche Informationen zu dem Fehler zurückgegeben.</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>Verwandte Themen


[Schnittstellen](interfaces-wprcontrol.md)

 

 







