---
title: GetProviderNameFromGuid
description: GetProviderNameFromGuid
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 65612d2b-6fa2-4bda-b183-8e25d62605c1
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 3b668cc021c4e3e92b954034d8cf84eb59d39ebc
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="getprovidernamefromguid"></a>GetProviderNameFromGuid


Dient zum Abrufen des Anbieternamens, die eine GUID-ID zugeordnet ist.

## <a name="syntax"></a>Syntax


``` syntax
HRESULT GetProviderNameFromGuid
  ([out] BSTR* bstrProviderIdStr,
  [in] REFGUID ProviderId)
;
```

## <a name="parameters"></a>Parameter


<a href="" id="bstr--bstrprovideridstr"></a>*BSTR\* BstrProviderIdStr*  
\[Skalieren\] eine Zeichenfolge, die Namen des Anbieters angibt.

<a href="" id="refguid-providerid"></a>*REFGUID ProviderId*  
\[in\] eine GUID, die die Provider-ID angibt.

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
<td><p>E_WPRC_FAILED_TO_TRANSLATE_GUID_TO_EVENT_PROVIDER_NAME</p></td>
<td><p>WPR konnte nicht übersetzt werden die GUID an, den Namen eines Ereignisses-Anbieter.</p></td>
</tr>
<tr class="even">
<td><p>S_OK</p></td>
<td><p>Der Name wird von die Funktion erfolgreich zurückgegeben.</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>Verwandte Themen


[IControlManager](icontrolmanager.md)

 

 







