---
author: kpacquer
Description: "Ruft eine Struktur, die aktuellen Details für einen bestimmten SIM-basierte Telefonleitung enthält, ab."
ms.assetid: 6ff31b2e-4a76-48cc-aefd-f015eb8cdf4a
MSHAttr: PreferredLib:/library/windows/hardware
title: MfgPhoneGetSimLineDetail-Funktion
ms.openlocfilehash: ffa72e5705333cedb68961a1ca9b82d3045147d8
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="mfgphonegetsimlinedetail-function"></a>MfgPhoneGetSimLineDetail-Funktion


Ruft eine Struktur, die aktuellen Details für einen bestimmten SIM-basierte Telefonleitung enthält, ab.

**MfgPhoneGetSimLineDetail** ist für Telefon Hersteller und kann nur im Modus Manufacturing aufgerufen werden.

<a name="syntax"></a>Syntax
------

```ManagedCPlusPlus
HRESULT APIENTRY MfgPhoneGetSimLineDetail(
  _In_  UINT                     SimSlot,
  _Out_ PMFGPHONE_SIMLINEDETAIL  SimLineDetail,
  _In_  ULONG                    SimLineDetailSize,
  _Out_ PULONG                   RequiredSize
);
```

<a name="parameters"></a>Parameter
----------

*SimSlot* \[in\]  
Gibt die SIM-basierte Telefonleitung an.

*SimLineDetail* \[out\]  
Zeiger auf eine [**MFGPHONE\_SIMLINEDETAIL**](mfgphone-simlinedetail.md) Struktur mit den aktuellen Details für die SIM-basierte Telefonleitung durch *SimSlot*angegeben.

*SimLineDetailSize* \[in\]  
Gibt die Größe des Parameters **SimLineDetail** .

*RequiredSize* \[out\]  
Gibt die erforderliche Größe für den Parameter **SimLineDetail** an.

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

 

 





