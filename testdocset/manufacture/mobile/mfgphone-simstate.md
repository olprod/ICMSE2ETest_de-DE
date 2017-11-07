---
author: kpacquer
Description: "Enthält Informationen zum Status SIM."
ms.assetid: 8533be42-70de-433c-89ac-2c623d9b4397
MSHAttr: PreferredLib:/library/windows/hardware
title: "MFGPHONE\\_SIMSTATE-Aufzählung"
ms.openlocfilehash: 768de8a27a6d6ec9abad48c088136afa6eea917d
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="mfgphonesimstate-enumeration"></a>MFGPHONE\_SIMSTATE-Aufzählung


Enthält Informationen zum Status SIM.

**MFGPHONE\_SIMSTATE** ist für Telefon Hersteller und kann nur im Modus Manufacturing aufgerufen werden.

<a name="syntax"></a>Syntax
------

```ManagedCPlusPlus
typedef enum _MFGPHONE_SIMSTATE { 
  MFGPHONE_SIMSTATE_UNKNOWN   = 0,
  MFGPHONE_SIMSTATE_NONE      = 1,
  MFGPHONE_SIMSTATE_ACTIVE    = 2,
  MFGPHONE_SIMSTATE_INVALID   = 3,
  MFGPHONE_SIMSTATE_LOCKED    = 4,
  MFGPHONE_SIMSTATE_DISABLED  = 5
} MFGPHONE_SIMSTATE;
```

<a name="constants"></a>Konstanten
---------

<span id="MFGPHONE_SIMSTATE_UNKNOWN"></span><span id="mfgphone_simstate_unknown"></span>**MFGPHONE\_SIMSTATE\_UNBEKANNT**  
Der Zustand SIM ist unbekannt.

<span id="MFGPHONE_SIMSTATE_NONE"></span><span id="mfgphone_simstate_none"></span>**MFGPHONE\_SIMSTATE\_NONE**  
Der Zustand SIM ist none. Es ist keine SIM.

<span id="MFGPHONE_SIMSTATE_ACTIVE"></span><span id="mfgphone_simstate_active"></span>**MFGPHONE\_SIMSTATE\_AKTIVEN**  
Der Zustand SIM ist aktiv.

<span id="MFGPHONE_SIMSTATE_INVALID"></span><span id="mfgphone_simstate_invalid"></span>**MFGPHONE\_SIMSTATE\_UNGÜLTIG**  
Der Zustand SIM ist ungültig.

<span id="MFGPHONE_SIMSTATE_LOCKED"></span><span id="mfgphone_simstate_locked"></span>**MFGPHONE\_SIMSTATE\_GESPERRT**  
Der Zustand SIM ist gesperrt.

<span id="MFGPHONE_SIMSTATE_DISABLED"></span><span id="mfgphone_simstate_disabled"></span>**MFGPHONE\_SIMSTATE\_DEAKTIVIERT**  
Der Zustand SIM ist deaktiviert.

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
</tbody>
</table>

 

 





