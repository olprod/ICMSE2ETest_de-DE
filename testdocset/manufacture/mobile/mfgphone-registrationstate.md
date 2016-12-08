---
author: kpacquer
Description: Bietet Informationen zum Status der Telefonleitung? Rufen Sie?.
ms.assetid: 0157eda2-5066-4f2e-95f8-1ae990db2540
MSHAttr: PreferredLib:/library/windows/hardware
title: "MFGPHONE\\_REGISTRATIONSTATE-Aufzählung"
ms.openlocfilehash: b44f5a403a2b60d1861dd0d16b1f0c8ef1fa9030
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="mfgphoneregistrationstate-enumeration"></a>MFGPHONE\_REGISTRATIONSTATE-Aufzählung


Bietet Informationen zum Status der Telefonleitung? Anruf?

**MFGPHONE\_REGISTRATIONSTATE** ist für Telefon Hersteller und kann nur im Modus Manufacturing aufgerufen werden.

<a name="syntax"></a>Syntax
------

```ManagedCPlusPlus
typedef enum _MFGPHONE_REGISTRATIONSTATE { 
  MFGPHONE_REGISTRATIONSTATE_UNKNOWN           = 0,
  MFGPHONE_REGISTRATIONSTATE_NOSIGNAL          = 1,
      MFGPHONE_REGISTRATIONSTATE_UNREGISTERED  = 2,
  MFGPHONE_REGISTRATIONSTATE_REGISTERING       = 3,
  MFGPHONE_REGISTRATIONSTATE_REGISTERED        = 4,
  MFGPHONE_REGISTRATIONSTATE_DENIED            = 5
} MFGPHONE_REGISTRATIONSTATE;
```

<a name="constants"></a>Konstanten
---------

<span id="MFGPHONE_REGISTRATIONSTATE_UNKNOWN"></span><span id="mfgphone_registrationstate_unknown"></span>**MFGPHONE\_REGISTRATIONSTATE\_UNBEKANNT**  
Der Registrierungsstatus ist nicht bekannt.

<span id="MFGPHONE_REGISTRATIONSTATE_NOSIGNAL"></span><span id="mfgphone_registrationstate_nosignal"></span>**MFGPHONE\_REGISTRATIONSTATE\_NOSIGNAL**  
Wird kein Signal, um den Registrierungsstatus zu erkennen.

<span id="____MFGPHONE_REGISTRATIONSTATE_UNREGISTERED"></span><span id="____mfgphone_registrationstate_unregistered"></span>**MFGPHONE\_REGISTRATIONSTATE\_nicht REGISTRIERT**  
Der Registrierungsstatus wurde aufgehoben.

<span id="MFGPHONE_REGISTRATIONSTATE_REGISTERING"></span><span id="mfgphone_registrationstate_registering"></span>**MFGPHONE\_REGISTRATIONSTATE\_REGISTRIEREN**  
Der Registrierungsstatus ist registrieren.

<span id="MFGPHONE_REGISTRATIONSTATE_REGISTERED"></span><span id="mfgphone_registrationstate_registered"></span>**MFGPHONE\_REGISTRATIONSTATE\_REGISTERED**  
Der Registrierungsstatus registriert ist.

<span id="MFGPHONE_REGISTRATIONSTATE_DENIED"></span><span id="mfgphone_registrationstate_denied"></span>**MFGPHONE\_REGISTRATIONSTATE\_VERWEIGERT**  
Der Registrierungsstatus verweigert.

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

 

 





