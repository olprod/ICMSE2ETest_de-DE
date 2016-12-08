---
author: kpacquer
Description: "Legt einen Wert zurück, der angibt, ob der Lautsprecher des Telefons soll, im Gegensatz zu den Hörer Kopfhörer verwendet werden."
ms.assetid: ae0382d0-01fc-40eb-ae3d-72242ac4aede
MSHAttr: PreferredLib:/library/windows/hardware
title: MfgPhoneSetSpeaker-Funktion
ms.openlocfilehash: c666e28a361ee4fedadf51a5064663f1899a1251
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="mfgphonesetspeaker-function"></a>MfgPhoneSetSpeaker-Funktion


Legt einen Wert zurück, der angibt, ob der Lautsprecher des Telefons soll, im Gegensatz zu den Hörer Kopfhörer verwendet werden.

**MfgPhoneSetSpeaker** ist für Telefon Hersteller und kann nur im Modus Manufacturing aufgerufen werden.

<a name="syntax"></a>Syntax
------

```ManagedCPlusPlus
HRESULT APIENTRY MfgPhoneSetSpeaker(
  _In_ BOOL bSpeakerOn
);
```

<a name="parameters"></a>Parameter
----------

*bSpeakerOn* \[in\]  
TRUE, wenn der Lautsprecher, verwendet wird, andernfalls false sein soll.

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

 

 





