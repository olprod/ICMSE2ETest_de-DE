---
title: QueryXML
description: QueryXML
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 1dd74aaf-f16c-47f8-9eda-876a404ef59a
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: e91500966ce819055f367e990285a82e1a4c7497
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="queryxml"></a>QueryXML


Gibt das XML-Format der derzeit ausgeführten Profil- und gibt an, ob das Profil ordnungsgemäß ausgeführt wird.

## <a name="syntax"></a>Syntax


``` syntax
HRESULT QueryXML
  ([out] BSTR* pbstrResults,
  [in] VARIANT_BOOL fValidateRuntimeState)
;
```

## <a name="parameters"></a>Parameter


<a href="" id="bstr--pbstrresults"></a>*BSTR\* PbstrResults*  
\[Skalieren\] einen Zeiger auf eine Ergebniszeichenfolge.

<a href="" id="variant-bool-fvalidateruntimestate"></a>*VARIANT\_BOOL fValidateRuntimeState*  
\[in\] eine vom Typ Boolean, der angibt, ob der Laufzeitzustand gültig ist.

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
<td><p>E_WPRC_RUNTIME_STATE_PROFILES_NOT_RUNNING</p></td>
<td><p>Gibt an, dass das Profil nicht ausgeführt wird.</p></td>
</tr>
<tr class="even">
<td><p>S_OK</p></td>
<td><p>Die Funktion wurde erfolgreich das XML-Format zurückgegeben.</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>Verwandte Themen


[IControlManager](icontrolmanager.md)

 

 







