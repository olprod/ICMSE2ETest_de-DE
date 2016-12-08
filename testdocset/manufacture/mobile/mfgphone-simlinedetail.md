---
author: kpacquer
Description: "Enthält Informationen zu einer bestimmten SIM-basierte Telefonleitung."
ms.assetid: 004fe04e-48dc-4569-882a-035ca6918498
MSHAttr: PreferredLib:/library/windows/hardware
title: MFGPHONE\_SIMLINEDETAIL-Struktur
ms.openlocfilehash: 079af4ab6a9521fe2c83935e5b933c4dab7413d0
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="mfgphonesimlinedetail-structure"></a>MFGPHONE\_SIMLINEDETAIL-Struktur


Enthält Informationen zu einer bestimmten SIM-basierte Telefonleitung. Diese **Struktur** ist über die Funktion [**MfgPhoneGetSimLineDetail**](mfgphonegetsimlinedetail.md) abgerufen.

**MFGPHONE\_SIMLINEDETAIL** Iis für Telefon Hersteller und kann nur im Modus Manufacturing aufgerufen werden.

<a name="syntax"></a>Syntax
------

```ManagedCPlusPlus
typedef struct _MFGPHONE_SIMLINEDETAIL {
  UINT                       SimSlot;
  MFGPHONE_SIMSTATE          SimState;
  MFGPHONE_REGISTRATIONSTATE RegistrationState;
  WCHAR  [64]                NetworkName;
  MFGPHONE_LINESYSTEMTYPE    LineSystemType;
  UINT                       SignalStrength;
  MFGPHONE_CALLSTATUS        CallStatus;
} MFGPHONE_SIMLINEDETAIL, *PMFGPHONE_SIMLINEDETAIL;
```

<a name="members"></a>Member
-------

**SimSlot**  
Die SIM-basierte-Telefonleitung auf der die Details in diese Struktur beziehen.

**SimState**  
Eine **Enumeration** , den aktuellen Status der SIM-basierte Telefonleitung angeben.

**RegistrationState**  
Eine **Enumeration** der Registrierung derzeitigen die Telefonleitung angeben.

**Netzwerkname**  
Mit dem Namen des Netzwerks WCHAR.

**LineSystemType**  
Eine **Enumeration** die System Art der Telefonleitung angeben.

**SignalStrength**  
Ganzzahl ohne Vorzeichen Signalstärke des die Telefonleitung enthält.

**CallStatus**  
Eine **Enumeration** den Status Aufruf der Telefonleitung angeben.

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

 

 





