---
author: kpacquer
Description: Anruf beendet.
ms.assetid: 2f6ce0fe-177b-4af5-8673-a9a4316309e4
MSHAttr: PreferredLib:/library/windows/hardware
title: MfgPhoneEndCall-Funktion
ms.openlocfilehash: 4cba6ae738c4ab8ba4dae75a4aa9cca2fefdb1c7
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="mfgphoneendcall-function"></a>MfgPhoneEndCall-Funktion


Anruf beendet.

**MfgPhoneEndCall** ist für Telefon Hersteller und kann nur im Modus Manufacturing aufgerufen werden.

<a name="syntax"></a>Syntax
------

```ManagedCPlusPlus
HRESULT APIENTRY MfgPhoneEndCall(
  _In_ UINT SimSlot  
);
```

<a name="parameters"></a>Parameter
----------

*SimSlot* \[in\]  
Die SIM-basierte-Telefonleitung, dessen Anruf beendet werden soll.

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

 

 





