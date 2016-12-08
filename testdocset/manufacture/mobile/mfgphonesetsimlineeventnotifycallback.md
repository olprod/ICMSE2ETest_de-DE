---
author: kpacquer
Description: "Callback-basierte Benachrichtigungsmechanismus für Empfangsereignisse auf SIM-basierte Telefonleitungen."
ms.assetid: 58ca5582-71d0-4b33-a3b3-68374c6ed1d5
MSHAttr: PreferredLib:/library/windows/hardware
title: MfgPhoneSetSimLineEventNotifyCallback-Funktion
ms.openlocfilehash: 1066aef2dcb3330f405c5fb5d1940c728ba40238
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="mfgphonesetsimlineeventnotifycallback-function"></a>MfgPhoneSetSimLineEventNotifyCallback-Funktion


Callback-basierte Benachrichtigungsmechanismus für den Empfang von Ereignissen für basierenden SIM Telefonleitungen.

**MfgPhoneSetSimLineEventNotifyCallback** ist für Telefon Hersteller und kann nur im Modus Manufacturing aufgerufen werden.

<a name="syntax"></a>Syntax
------

```ManagedCPlusPlus
HRESULT APIENTRY MfgPhoneSetSimLineEventNotifyCallback(
  _In_ MFGPHONE_SIMLINEEVENT_NOTIFY_CALLBACK  Callback,
  _In_ PVOID                                  Context
);
```

<a name="parameters"></a>Parameter
----------

*Rückruf* \[in\]  
Der Callback-Funktion aufgerufen, wenn das Ereignis auftritt.

*Kontext* \[in\]  
Der Kontext.

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

 

 





