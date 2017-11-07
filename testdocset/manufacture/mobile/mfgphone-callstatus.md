---
author: kpacquer
Description: Bietet Informationen zum Status des Aufrufs an.
ms.assetid: dcd0fe41-15bf-4615-a9ed-aaf15dde5078
MSHAttr: PreferredLib:/library/windows/hardware
title: "MFGPHONE\\_CALLSTATUS-Aufzählung"
ms.openlocfilehash: 5ab0a9652869e20249b774fa33d12419b60c8ce0
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="mfgphonecallstatus-enumeration"></a>MFGPHONE\_CALLSTATUS-Aufzählung


Enthält Informationen zu den Status des Anrufs.

**MFGPHONE\_CALLSTATUS** ist für Telefon Hersteller und kann nur im Modus Manufacturing aufgerufen werden.

<a name="syntax"></a>Syntax
------

```ManagedCPlusPlus
typedef enum _MFGPHONE_CALLSTATUS { 
  MFGPHONE_CALLSTATUS_UNKNOWN   = 0,
  MFGPHONE_CALLSTATUS_IDLE      = 1,
  MFGPHONE_CALLSTATUS_CALLING   = 2,
  MFGPHONE_CALLSTATUS_INCOMING  = 3,
  MFGPHONE_CALLSTATUS_ACTIVE    = 4
} MFGPHONE_CALLSTATUS;
```

<a name="constants"></a>Konstanten
---------

<span id="MFGPHONE_CALLSTATUS_UNKNOWN_"></span><span id="mfgphone_callstatus_unknown_"></span>**MFGPHONE\_CALLSTATUS\_UNBEKANNT**   
Der Anrufstatus ist unbekannt.

<span id="MFGPHONE_CALLSTATUS_IDLE"></span><span id="mfgphone_callstatus_idle"></span>**MFGPHONE\_CALLSTATUS\_im LEERLAUF**  
Der Anrufstatus befindet sich im Leerlauf.

<span id="MFGPHONE_CALLSTATUS_CALLING"></span><span id="mfgphone_callstatus_calling"></span>**MFGPHONE\_CALLSTATUS\_AUFRUFEN**  
Der Status des Anrufs ist aufrufen.

<span id="MFGPHONE_CALLSTATUS_INCOMING"></span><span id="mfgphone_callstatus_incoming"></span>**MFGPHONE\_CALLSTATUS\_EINGEHENDE**  
Der Status des Anrufs ist eingehende.

<span id="MFGPHONE_CALLSTATUS_ACTIVE"></span><span id="mfgphone_callstatus_active"></span>**MFGPHONE\_CALLSTATUS\_AKTIV**  
Der Anrufstatus ist aktiv.

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

 

 





