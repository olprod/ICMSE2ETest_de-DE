---
author: kpacquer
Description: "Gibt einen Boolean zurück, der angibt, ob der Lautsprecher des Telefons, im Gegensatz zu den Hörer Kopfhörer verwendet wird."
ms.assetid: 933f0816-a094-4f7b-a26f-5d31ed97f677
MSHAttr: PreferredLib:/library/windows/hardware
title: MfgPhoneGetSpeaker-Funktion
ms.openlocfilehash: 3615b10e84659966eeec7d28a75b840cc5b75419
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="mfgphonegetspeaker-function"></a>MfgPhoneGetSpeaker-Funktion


Gibt einen Boolean zurück, der angibt, ob Lautsprecher des Telefons, im Gegensatz zu der Hörer Kopfhörer genutzt wird.

**MfgPhoneGetSpeaker** ist für Telefon Hersteller und kann nur im Modus Manufacturing aufgerufen werden.

<a name="syntax"></a>Syntax
------

```ManagedCPlusPlus
HRESULT APIENTRY MfgPhoneGetSpeaker(
  _Out_ PBOOL pbSpeakerOn
);
```

<a name="parameters"></a>Parameter
----------

*pbSpeakerOn* \[out\]  
True, wenn der Lautsprecher, verwendet wird, andernfalls FALSE wird.

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

 

 





