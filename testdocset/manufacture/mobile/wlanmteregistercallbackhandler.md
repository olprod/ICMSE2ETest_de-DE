---
author: kpacquer
Description: WlanMTERegisterCallbackHandler
ms.assetid: 7a61e9e2-fa0c-4c01-96c2-f3720aab7cde
MSHAttr: PreferredLib:/library/windows/hardware
title: WlanMTERegisterCallbackHandler
ms.openlocfilehash: 15612147b5d91be0d956338e64eb85f155f7a77a
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="wlanmteregistercallbackhandler"></a>WlanMTERegisterCallbackHandler


Registriert einen Ereignishandler, der aufgerufen wird, wenn Sie der Treiber für eine Fertigung-Funktionalität einen Rückruf ruft Ereignis.

## <a name="span-idsyntaxspanspan-idsyntaxspanspan-idsyntaxspansyntax"></a><span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Die Syntax


``` syntax
DWORD WlanMTERegisterCallbackHandler(
    __in    HANDLE                          hAdapter,
    __in    WLAN_MTE_NOTIFICATION_CALLBACK Callback
);
```

## <a name="span-idparametersspanspan-idparametersspanspan-idparametersspanparameters"></a><span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameter


<span id="hAdapter"></span><span id="hadapter"></span><span id="HADAPTER"></span>*hAdapter*  
\[in\] das Handle für den Adapter Wi-Fi durch Aufrufen von [WlanMTEOpenHandle](wlanmteopenhandle.md)abgerufen.

<span id="Callback"></span><span id="callback"></span><span id="CALLBACK"></span>*Rückruf*  
\[in\] die Handlerfunktion, wird von der Anwendung für manufacturing Rückrufe registriert.

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
<td align="left"><p>Wenn von der <em>hAdapter</em> -Parameter angegebene Adapter Handle ungültig oder NULL ist zurückgegeben.</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idremarksspanspan-idremarksspanspan-idremarksspanremarks"></a><span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Hinweise


Die Callback-Funktion besteht aus den folgenden Prototyp:

``` syntax
typedef VOID (WINAPI *WLAN_MTE_NOTIFICATION_CALLBACK)(
    __in    PDOT11_MANUFACTURING_CALLBACK_PARAMETERS    pMTECallback,
    __in    PVOID                                       pvReserved
    );
```

## <a name="span-idrequirementsspanspan-idrequirementsspanspan-idrequirementsspanrequirements"></a><span id="Requirements"></span><span id="requirements"></span><span id="REQUIREMENTS"></span>Anforderungen


**Kopfzeile:** wifimte.w

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Wi-Fi Fertigung-API](wi-fi-manufacturing-api.md)

 

 






