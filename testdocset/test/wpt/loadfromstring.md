---
title: LoadFromString
description: LoadFromString
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: c4661c55-e237-4143-af70-dff6de0afe9b
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 2d7507d96d0d9733d6888c496db8e573d09bc292
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="loadfromstring"></a>LoadFromString


Lädt ein Profil aus der angegebenen XML-Profil-Definition-Zeichenfolge an.

## <a name="syntax"></a>Syntax


``` syntax
HRESULT LoadFromString
  ([in] BSTR bstrProfile)
;
```

## <a name="parameters"></a>Parameter


<a href="" id="bstrprofile"></a>*bstrProfile*  
\[in\] Profil Definition für eine Zeichenfolge, die den XML-CODE enthält.

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
<td><p>Die Funktion wurde erfolgreich geladen, das Profil.</p></td>
</tr>
<tr class="even">
<td><p>E_INVALIDARG</p></td>
<td><p>Mindestens ein Argument ist ungültig. Verwenden Sie [IParsingErrorInfo](iparsingerrorinfo.md) um ausführliche Fehlerinformationen.</p></td>
</tr>
<tr class="odd">
<td><p>E_WPRC_FAILED_TO_VALIDATE_PROFILE</p></td>
<td><p>Überprüfen das Profil die Bibliothek konnte nicht. Verwenden Sie <strong>IParsingErrorInfo</strong> um ausführliche Fehlerinformationen.</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>Verwandte Themen


[IProfile](iprofile.md)

 

 







