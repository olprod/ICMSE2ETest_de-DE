---
author: kpacquer
Description: Ruft die Anzahl der derzeit erkannten SIM Slots ab.
ms.assetid: 432b3748-4444-41b8-ac0b-f227d0f36aef
MSHAttr: PreferredLib:/library/windows/hardware
title: MfgPhoneGetSimLineCount-Funktion
ms.openlocfilehash: dbfbdce8bc351b701972f43d5e06053a7a37a3e4
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="mfgphonegetsimlinecount-function"></a>MfgPhoneGetSimLineCount-Funktion


Ruft die Anzahl der derzeit erkannten SIM Slots ab.

**MfgPhoneGetSimLineCount** ist für Telefon Hersteller und kann nur im Modus Manufacturing aufgerufen werden.

<a name="syntax"></a>Syntax
------

```ManagedCPlusPlus
HRESULT APIENTRY MfgPhoneGetSimLineCount(
  _Out_ PUINT SimLineCount
);
```

<a name="parameters"></a>Parameter
----------

*SimLineCount* \[out\]  
Zeiger auf ein **UINT** an, der die Anzahl der derzeit erkannten SIM Slots angibt. Aktive und inaktive SIM Slots sind bei der Zählung eingeschlossen.

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

 

 





