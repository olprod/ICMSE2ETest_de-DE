---
title: LoadFromFile
description: LoadFromFile
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 8816f97e-aa11-4e02-ade7-537e0b288cce
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: d8e973f3cde02a6e5fc5ee93dc80bede41540a27
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="loadfromfile"></a>LoadFromFile


Lädt ein Profil aus einer Datei.

## <a name="syntax"></a>Syntax


``` syntax
HRESULT LoadFromFile
  ([in] BSTR bstrProfileName,
  [in] BSTR bstrFileName)
;
```

## <a name="parameters"></a>Parameter


<a href="" id="bstrprofilename"></a>*bstrProfileName*  
\[in\] den Namen des Profils geladen werden.

<a href="" id="bstrfilename"></a>*bstrFileName*  
\[in\] den Namen der Datei mit dem Profil aus.

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
<td><p>Gibt Erfolg an.</p></td>
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

 

 







