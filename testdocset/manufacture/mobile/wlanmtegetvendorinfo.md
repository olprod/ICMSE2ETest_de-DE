---
author: kpacquer
Description: WlanMTEGetVendorInfo
ms.assetid: a36c1d73-252b-453e-a231-b26087d2e740
MSHAttr: PreferredLib:/library/windows/hardware
title: WlanMTEGetVendorInfo
ms.openlocfilehash: d3af3853e935fdc3de202593591d2265c85cb759
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="wlanmtegetvendorinfo"></a>WlanMTEGetVendorInfo


Herstellerspezifische Informationen anfordert, wie die Herstellerklassen-ID und die Beschreibung der Hersteller.

## <a name="span-idsyntaxspanspan-idsyntaxspanspan-idsyntaxspansyntax"></a><span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Die Syntax


``` syntax
DWORD WlanMTEGetVendorInfo(
    __in                        HANDLE  hAdapter,
    __out                       ULONG   *puVendorId,
    __in                        ULONG   uOutBufLen,
    __out_bcount(uOutBufLen)    PUCHAR  pucOutBuffer
);
```

## <a name="span-idparametersspanspan-idparametersspanspan-idparametersspanparameters"></a><span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameter


<span id="hAdapter"></span><span id="hadapter"></span><span id="HADAPTER"></span>*hAdapter*  
\[in\] das Handle für den Adapter Wi-Fi durch Aufrufen von [WlanMTEOpenHandle](wlanmteopenhandle.md)abgerufen.

<span id="puVendorId"></span><span id="puvendorid"></span><span id="PUVENDORID"></span>*puVendorId*  
\[Skalieren\] die Hersteller-ID.

<span id="uOutBufLen"></span><span id="uoutbuflen"></span><span id="UOUTBUFLEN"></span>*uOutBufLen*  
\[in\] die Länge des Puffers zum Abrufen der Hersteller Beschreibung.

<span id="pucOutBuffer"></span><span id="pucoutbuffer"></span><span id="PUCOUTBUFFER"></span>*pucOutBuffer*  
\[Skalieren\] den Puffer an, der die Hersteller beschreibende Zeichenfolge enthalten soll.

## <a name="span-idreturnvaluespanspan-idreturnvaluespanspan-idreturnvaluespanreturn-value"></a><span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Rückgabewert


Wenn die Funktion erfolgreich ist, wird der Rückgabewert ist FEHLER\_ERFOLG.

Wenn die Funktion fehlschlägt, ist der Rückgabewert eines Fehlercodes System. Die folgende Tabelle enthält die Fehlercodes, die möglicherweise zurückgegeben werden.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Fehlercode</th>
<th align="left">Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>ZUSÄTZLICH</p></td>
<td align="left"><p>Zurückgegeben, wenn der Parameter <em>PuVendorID</em>, <em>uOutBufLen</em>oder <em>PucOutBuffer</em> NULL ist.</p></td>
</tr>
<tr class="even">
<td align="left"><p>ERROR_INVALID_HANDLE</p></td>
<td align="left"><p>Zurückgegeben, wenn das durch den Parameter <em>hAdapter</em> angegebenen Adapter Handle ungültig ist.</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idrequirementsspanspan-idrequirementsspanspan-idrequirementsspanrequirements"></a><span id="Requirements"></span><span id="requirements"></span><span id="REQUIREMENTS"></span>Anforderungen


**Kopfzeile:** wifimte.w

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Wi-Fi Fertigung-API](wi-fi-manufacturing-api.md)

 

 






