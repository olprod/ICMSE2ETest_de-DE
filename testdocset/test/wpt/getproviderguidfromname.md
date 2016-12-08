---
title: GetProviderGuidFromName
description: GetProviderGuidFromName
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 855b63df-307e-4e10-bb83-561fa71e13c2
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: d6a290dac5a2a01bbd788eb3a6f8e91867b668a2
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="getproviderguidfromname"></a>GetProviderGuidFromName


Dient zum Abrufen des Anbieters, den dem angegebenen Namen GUID zugeordnet.

## <a name="syntax"></a>Syntax


``` syntax
HRESULT GetProviderGuidFromName
  ([out] GUID* ProviderId,
  [in] BSTR bstrProViderName)
;
```

## <a name="parameters"></a>Parameter


<a href="" id="guid--providerid"></a>*GUID\* ProviderId*  
\[Skalieren\] eine GUID, die die Provider-ID angibt.

<a href="" id="bstr-bstrprovidername"></a>*BSTR bstrProViderName*  
\[in\] eine Zeichenfolge, die Namen des Anbieters angibt.

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
<td><p>E_WPRC_FAILED_TO_TRANSLATE_EVENT_PROVIDER_NAME_TO_GUID</p></td>
<td><p>WPR konnte den Namen des Ereignisses in eine GUID übersetzen.</p></td>
</tr>
<tr class="even">
<td><p>S_OK</p></td>
<td><p>Die GUID wurde erfolgreich von die Funktion zurückgegeben.</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>Verwandte Themen


[IControlManager](icontrolmanager.md)

 

 







