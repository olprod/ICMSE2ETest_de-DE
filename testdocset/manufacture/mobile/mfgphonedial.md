---
author: kpacquer
Description: "Bewirkt, dass das Telefon So wählen Sie einen Anruf."
ms.assetid: f01afc0d-70cf-4d13-8d99-fb27bb329376
MSHAttr: PreferredLib:/library/windows/hardware
title: MfgPhoneDial-Funktion
ms.openlocfilehash: f825cc0422ef996088b0912389364118ff50aa62
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="mfgphonedial-function"></a>MfgPhoneDial-Funktion


Bewirkt, dass das Telefon So wählen Sie einen Anruf.

**MfgPhoneDial** ist für Telefon Hersteller und kann nur im Modus Manufacturing aufgerufen werden.

<a name="syntax"></a>Syntax
------

```ManagedCPlusPlus
HRESULT APIENTRY MfgPhoneDial(
  _In_ UINT    SimSlot,
  _In_ PCWSTR  DialNumber
);
```

<a name="parameters"></a>Parameter
----------

*SimSlot* \[in\]  
Die SIM-basierte Telefonleitung verwendet.

*DialNumber* \[in\]  
Die Telefonnummer gewählt.

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

 

 





