---
author: kpacquer
Description: WlanMTESetData
ms.assetid: cf0cf3b4-a4e0-4818-bc78-8b5547903f4b
MSHAttr: PreferredLib:/library/windows/hardware
title: WlanMTESetData
ms.openlocfilehash: 72a96b3895b2d8a5db493252027970523950812f
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="wlanmtesetdata"></a>WlanMTESetData


Fordert, dass der Treiber Schreiben von Daten zu einer bestimmten Stelle durch einen Schlüssel und Offset-Wert definiert.

## <a name="span-idsyntaxspanspan-idsyntaxspanspan-idsyntaxspansyntax"></a><span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Die Syntax


``` syntax
DWORD WlanMTESetData(
    __in                    HANDLE  hAdapter,
    __in                    ULONG   uKey,
    __in                    ULONG   uOffset,
    __in                    ULONG   uInBufLen,
    __in_bcount(uInBufLen)  PUCHAR  pucInBuffer
);
```

## <a name="span-idparametersspanspan-idparametersspanspan-idparametersspanparameters"></a><span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameter


<span id="hAdapter"></span><span id="hadapter"></span><span id="HADAPTER"></span>*hAdapter*  
\[in\] das Handle für den Adapter Wi-Fi durch Aufrufen von [WlanMTEOpenHandle](wlanmteopenhandle.md)abgerufen.

<span id="uKey"></span><span id="ukey"></span><span id="UKEY"></span>*uKey*  
\[in\] der Schlüssel für die Anforderung schreiben.

<span id="uOffset"></span><span id="uoffset"></span><span id="UOFFSET"></span>*uOffset*  
\[in\] der Offset für die Write-Anforderung.

<span id="uInBufLen"></span><span id="uinbuflen"></span><span id="UINBUFLEN"></span>*uInBufLen*  
\[in\] die Länge des Puffers mit den Daten geschrieben werden sollen.

<span id="pucInBuffer"></span><span id="pucinbuffer"></span><span id="PUCINBUFFER"></span>*pucInBuffer*  
\[in\] der Puffer mit den Daten geschrieben werden sollen.

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
<td align="left"><p>Zurückgegeben, wenn der Parameter <em>uInBufLen</em> vorhanden ist, aber der Parameter <em>PucInBuffer</em> NULL ist.</p></td>
</tr>
<tr class="even">
<td align="left"><p>ERROR_INVALID_HANDLE</p></td>
<td align="left"><p>Zurückgegeben, wenn das Handle <em>hAdapter</em> ungültig ist.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>ERROR_OUTOFMEMORY</p></td>
<td align="left"><p>Zurückgegeben, wenn nicht genügend Arbeitsspeicher zum Ausführen des Vorgangs reserviert werden kann.</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idrequirementsspanspan-idrequirementsspanspan-idrequirementsspanrequirements"></a><span id="Requirements"></span><span id="requirements"></span><span id="REQUIREMENTS"></span>Anforderungen


**Kopfzeile:** wifimte.w

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Wi-Fi Fertigung-API](wi-fi-manufacturing-api.md)

 

 






