---
author: kpacquer
Description: "Enthält Informationen zu den Typ des Systems Linie."
ms.assetid: 03dd827c-00f4-4288-b79d-7cfb3d4feab0
MSHAttr: PreferredLib:/library/windows/hardware
title: "MFGPHONE\\_LINESYSTEMTYPE-Aufzählung"
ms.openlocfilehash: 1773d27ef49434b6dbecf9a29045a0ae413494ab
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="mfgphonelinesystemtype-enumeration"></a>MFGPHONE\_LINESYSTEMTYPE-Aufzählung


Enthält Informationen zu den Typ des Systems Linie.

**MFGPHONE\_LINESYSTEMTYPE** ist für Telefon Hersteller und kann nur im Modus Manufacturing aufgerufen werden.

<a name="syntax"></a>Syntax
------

```ManagedCPlusPlus
typedef enum _MFGPHONE_LINESYSTEMTYPE { 
  MFGPHONE_LINESYSTEMTYPE_UNKNOWN   = 0,
  MFGPHONE_LINESYSTEMTYPE_GSM       = 1,
  MFGPHONE_LINESYSTEMTYPE_CDMA      = 2,
  MFGPHONE_LINESYSTEMTYPE_IMS       = 3
} MFGPHONE_LINESYSTEMTYPE;
```

<a name="constants"></a>Konstanten
---------

<span id="MFGPHONE_LINESYSTEMTYPE_UNKNOWN_"></span><span id="mfgphone_linesystemtype_unknown_"></span>**MFGPHONE\_LINESYSTEMTYPE\_UNBEKANNT**   
Die Art der System ist unbekannt.

<span id="MFGPHONE_LINESYSTEMTYPE_GSM"></span><span id="mfgphone_linesystemtype_gsm"></span>**MFGPHONE\_LINESYSTEMTYPE\_g/M2**  
Der Typ des Systems Zeile ist g/M2.

<span id="MFGPHONE_LINESYSTEMTYPE_CDMA"></span><span id="mfgphone_linesystemtype_cdma"></span>**MFGPHONE\_LINESYSTEMTYPE\_CDMA**  
Der Typ des Systems Zeile ist CDMA.

<span id="MFGPHONE_LINESYSTEMTYPE_IMS"></span><span id="mfgphone_linesystemtype_ims"></span>**MFGPHONE\_LINESYSTEMTYPE\_IMS**  
Der Typ des Systems Zeile ist IMS.

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

 

 





