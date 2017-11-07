---
title: Abfrage
description: Abfrage
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 676f0ed9-641c-49ea-882f-0607e387f8d0
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 32a7cef399ab29cee540cea7e98a3d12c71cc122
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="query"></a>Abfrage


Fragt die Eigenschaften der Sitzung und Anbieter in allen Profilen.

## <a name="syntax"></a>Syntax


``` syntax
HRESULT Query
  ([out] BSTR* pbstrResults,
  [in] VARIANT_BOOL fValidateRuntimeState)
;
```

## <a name="parameters"></a>Parameter


<a href="" id="pbstrresults"></a>*pbstrResults*  
\[Skalieren\] eine Zeichenfolge in XML-Format, die Sitzung und Anbieter Eigenschaften aller Profile enthält Schritte von WPRC aus der Bibliothek.

<a href="" id="fvalidateruntimestate"></a>*fValidateRuntimeState*  
\[in\] eine vom Typ Boolean, der angibt, ob die Bibliothek bestimmt werden soll, ob die Aufzeichnung ausgeführt wird.

## <a name="return-value"></a>Rückgabewert


In der folgenden Tabelle werden die möglichen Werte beschrieben.

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
<td><p>Die Funktion wurde erfolgreich die Eigenschaften zurückgegeben.</p></td>
</tr>
<tr class="even">
<td><p>E_POINTER</p></td>
<td><p>Der Zeiger ist ungültig.</p></td>
</tr>
<tr class="odd">
<td><p>E_WPRC_FAILED_TO_QUERY_PROFILES</p></td>
<td><p>Die Eigenschaften der Sitzung und Rollenanbieter in allen Benutzerprofilen Abfrage die Bibliothek ist fehlgeschlagen. Verwenden Sie [IControlErrorInfo](icontrolerrorinfo.md) , um ausführliche Informationen zu erhalten.</p></td>
</tr>
<tr class="even">
<td><p>E_WPRC_INVALID_PROFILES_RUNTIME_STATE</p></td>
<td><p>Die Liste der Profile, die auf dem System ausgeführt werden entspricht nicht verwendet, um die Aufzeichnung zu starten. Detaillierte Informationen finden Sie unter <strong>IControlErrorInfo</strong> .</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>Verwandte Themen


[IControlManager](icontrolmanager.md)

 

 







