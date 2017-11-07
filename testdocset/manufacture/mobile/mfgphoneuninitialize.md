---
author: kpacquer
Description: Deinitialisiert das Telefonsystem und den internen Zustand der API durch DLL implementiert.
ms.assetid: 7b82c8c8-6244-4f72-ab14-390a0757f120
MSHAttr: PreferredLib:/library/windows/hardware
title: MfgPhoneUninitialize-Funktion
ms.openlocfilehash: a2458c5607c225b301fa899cc65ff910f023dee4
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="mfgphoneuninitialize-function"></a>MfgPhoneUninitialize-Funktion


Deinitialisiert das Telefonsystem und den internen Zustand der API von DLL implementiert.

**MfgPhoneUninitialize** ist für Telefon Hersteller und kann nur im Modus Manufacturing aufgerufen werden.

<a name="syntax"></a>Syntax
------

```ManagedCPlusPlus
HRESULT APIENTRY MfgPhoneUninitialize(void);
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

 

 





