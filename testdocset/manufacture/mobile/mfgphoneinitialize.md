---
author: kpacquer
Description: Initialisiert das Telefonsystem und den internen Zustand der API von DLL-DATEI implementiert.
ms.assetid: b9a9f95e-32ca-49fe-8f8c-9bf00d899edf
MSHAttr: PreferredLib:/library/windows/hardware
title: MfgPhoneInitialize-Funktion
ms.openlocfilehash: 4be255041cdd76bc4f37e3161dcc42c4f9c12a99
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="mfgphoneinitialize-function"></a>MfgPhoneInitialize-Funktion


Initialisiert das Telefonsystem und den internen Zustand der API von DLL implementiert.

**MfgPhoneInitialize** ist für Telefon Hersteller und kann nur im Modus Manufacturing aufgerufen werden.

<a name="syntax"></a>Syntax
------

```ManagedCPlusPlus
HRESULT APIENTRY MfgPhoneInitialize(void);
```

<a name="parameters"></a>Parameter
----------

Diese Funktion besitzt keine Parameter.

<a name="return-value"></a>Rückgabewert
------------

S\_OK bei Erfolg zurückgegeben, und ein Fehlercode wird zurückgegeben, andernfalls.

<a name="requirements"></a>Anforderungen
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><p>Kopfzeile</p></td>
<td align="left">Mfgphone.h (einschließlich Mfgphone.h)</td>
</tr>
<tr class="even">
<td align="left"><p>DLL-DATEI</p></td>
<td align="left">MFGPHONE. DLL-DATEI</td>
</tr>
</tbody>
</table>

 

 





