---
title: Start
description: Start
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 58474a2e-2e53-487e-8cca-a09959559fb7
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: c8bba10d7e9176eaa7c1e57db0e2746fda799905
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="start"></a>Start


Startet eine Aufzeichnung.

## <a name="syntax"></a>Syntax


``` syntax
HRESULT Start
  ([in] IProfileCollection* pProfileCollection,
  [out, retval] CLoggingMode* pLoggingMode)
;
```

## <a name="parameters"></a>Parameter


<a href="" id="pprofilecollection"></a>*pProfileCollection*  
\[in\] einen Zeiger auf ein **IProfileCollection** Objekt, das enthält eine Auflistung von Profile zu starten.

<a href="" id="ploggingmode"></a>*pLoggingMode*  
\[Skalieren\] einen Zeiger auf ein Element der **CLoggingMode** -Enumeration, der angibt, ob die Profile melden Sie sich Arbeitsspeicher oder in eine Datei schreiben.

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
<td><p>Die Funktion wurde erfolgreich Aufzeichnung gestartet.</p></td>
</tr>
<tr class="even">
<td><p>E_INVALIDARG</p></td>
<td><p>Mindestens ein Argument ist ungültig.</p></td>
</tr>
<tr class="odd">
<td><p>Mindestens ein Argument ist ungültig.</p></td>
<td><p>Der Zeiger ist ungültig.</p></td>
</tr>
<tr class="even">
<td><p>E_WPRC_FAILED_TO_START_PROFILE</p></td>
<td><p>Die Bibliothek konnte nicht in der Auflistung Profil ein Profil zu starten. Verwenden Sie [IControlErrorInfo](icontrolerrorinfo.md) , um ausführliche Fehlerinformationen.</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>Verwandte Themen


[IControlManager](icontrolmanager.md)

 

 







