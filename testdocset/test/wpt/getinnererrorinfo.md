---
title: GetInnerErrorInfo
description: GetInnerErrorInfo
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: f3cfd46e-bed5-47fd-a2bb-f7e34f7877c6
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: ad7c8f10f69fd45372fe6f00117511a7e551c9d1
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="getinnererrorinfo"></a>GetInnerErrorInfo


Zusätzliche Informationen zu dem Fehler zurückgegeben.

## <a name="syntax"></a>Syntax


``` syntax
HRESULT GetInnerErrorInfo
  ([out, retval] IUnknown** ppVal)
;
```

## <a name="parameters"></a>Parameter


<a href="" id="ppval"></a>*ppVal*  
\[Skalieren\] Zeiger auf die [IUnknown](http://go.microsoft.com/fwlink/p/?linkid=217447) -Schnittstelle an, der Zusatzinformationen über die Ursache des Fehlers angibt. Wenn keine inneren Informationen verfügbar sind, ist dieser Parameter NULL.

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
<td><p>Die Funktion wurde erfolgreich die Fehlerinformationen zurückgegeben.</p></td>
</tr>
<tr class="even">
<td><p>S_FALSE</p></td>
<td><p>Gibt an, dass keine zusätzliche Fehlerinformationen verfügbar ist, und <em>PpVal</em> NULL ist.</p></td>
</tr>
<tr class="odd">
<td><p>E_POINTER</p></td>
<td><p>Gibt ein ungültiger Zeiger an.</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>Verwandte Themen


[IControlErrorInfo](icontrolerrorinfo.md)

 

 







