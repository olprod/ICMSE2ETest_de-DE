---
author: kpacquer
Description: WlanMTESleep
ms.assetid: 36b6f1e4-15a3-4e2c-8afb-a455d945aede
MSHAttr: PreferredLib:/library/windows/hardware
title: WlanMTESleep
ms.openlocfilehash: b33dcf33def3154eb1d42ab7b3eb14fbe3f38850
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="wlanmtesleep"></a>WlanMTESleep


Anforderungen, die der Treiber So wechseln in den Energiesparmodus für ein angegebenes Zeitintervall oder auf unbestimmte Zeit, bis der Normalzustand-Anforderung gesendet wird.

## <a name="span-idsyntaxspanspan-idsyntaxspanspan-idsyntaxspansyntax"></a><span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Die Syntax


``` syntax
DWORD WlanMTESleep(
    __in                    HANDLE  hAdapter,
    __in                    ULONG   uSleepTime,
    __in                    PVOID   pvContext
);
```

## <a name="span-idparametersspanspan-idparametersspanspan-idparametersspanparameters"></a><span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameter


<span id="hAdapter"></span><span id="hadapter"></span><span id="HADAPTER"></span>*hAdapter*  
\[in\] das Handle für den Adapter Wi-Fi durch Aufrufen von [WlanMTEOpenHandle](wlanmteopenhandle.md)abgerufen.

<span id="uSleepTime"></span><span id="usleeptime"></span><span id="USLEEPTIME"></span>*uSleepTime*  
\[in\] die Zeit in Millisekunden für den Adapter für die in den Energiesparmodus bleiben. Wenn −1 Wert angegeben wird, wechselt der Adapter, bis eine [WlanMTEAwake](wlanmteawake.md) -Anforderung gesendet wird.

<span id="pvContext"></span><span id="pvcontext"></span><span id="PVCONTEXT"></span>*pvContext*  
\[in\] im Kontext, die dieser Anforderung in den Rückruf eindeutig identifiziert.

## <a name="span-idreturnvaluespanspan-idreturnvaluespanspan-idreturnvaluespanreturn-value"></a><span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Rückgabewert


Wenn die Funktion erfolgreich ist, wird der Rückgabewert ist FEHLER\_ERFOLG.

Wenn die Funktion fehlschlägt, ist der Rückgabewert eines Fehlercodes System. Die folgende Tabelle listet eines die Fehlercodes, die zurückgegeben werden können.

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
<td align="left"><p>Zurückgegeben, wenn der Parameter <em>uSleepTime</em> NULL ist.</p></td>
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

 

## <a name="span-idremarksspanspan-idremarksspanspan-idremarksspanremarks"></a><span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Hinweise


Während Energiesparmodus werden alle Sender deaktiviert, und der Wi-Fi-Chip ausgeschaltet. Der Adapter reawakens, wird die Anwendung Rückrufhandler, wenn eine [WlanMTERegisterCallbackHandler](wlanmteregistercallbackhandler.md), registriert wurde mit der **dot11ManufacturingCallbackType** auf festgelegt aufgerufen **dot11\_Fertigung\_Rückruf\_dem Standbymodus\_vollständige** und das Ergebnis des Vorgangs dem Standbymodus enthalten ist.

## <a name="span-idrequirementsspanspan-idrequirementsspanspan-idrequirementsspanrequirements"></a><span id="Requirements"></span><span id="requirements"></span><span id="REQUIREMENTS"></span>Anforderungen


**Kopfzeile:** wifimte.w

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[WlanMTEAwake](wlanmteawake.md)

[Wi-Fi Fertigung-API](wi-fi-manufacturing-api.md)

 

 






