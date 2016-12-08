---
author: kpacquer
Description: WlanMTEResetAdapter
ms.assetid: bb87f719-3277-4fcc-aa9f-94ff1dac34f1
MSHAttr: PreferredLib:/library/windows/hardware
title: WlanMTEResetAdapter
ms.openlocfilehash: 687f30b445895cdcb0f8e961dbbd6f44b7d64c41
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="wlanmteresetadapter"></a>WlanMTEResetAdapter


Setzt den Wi-Fi-Adapter. Die Anwendung kann einen optionalen Rückruf und Kontext Handle aufgerufen, wenn der Vorgang abgeschlossen ist angeben.

## <a name="span-idsyntaxspanspan-idsyntaxspanspan-idsyntaxspansyntax"></a><span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Die Syntax


``` syntax
DWORD WlanMTEResetAdapter(
    __in        HANDLE                  hAdapter,
    __in        DOT11_RESET_REQUEST     *pDot11ResetRequest,
    __in        WLAN_MTE_RESET_CALLBACK ResetCallback,
    __in        PVOID                   pvContext
);
```

## <a name="span-idparametersspanspan-idparametersspanspan-idparametersspanparameters"></a><span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameter


<span id="hAdapter"></span><span id="hadapter"></span><span id="HADAPTER"></span>*hAdapter*  
\[in\] das Handle für den Adapter Wi-Fi durch Aufrufen von [WlanMTEOpenHandle](wlanmteopenhandle.md)abgerufen.

<span id="pDot11ResetRequest"></span><span id="pdot11resetrequest"></span><span id="PDOT11RESETREQUEST"></span>*pDot11ResetRequest*  
\[in\] Informationen über die Anforderung zurücksetzen. Wenn die Anwendung zurücksetzen erforderlich sind, um die MAC-Adresse zu aktualisieren, sollten angeben entweder **dot11\_zurücksetzen\_Typ\_Mac** oder **dot11\_zurücksetzen\_Typ\_Phy\_und\_Mac** in der Reihenfolge für die aktualisierte MAC-Adresse in den DPP geschrieben werden. Beachten Sie, dass die MAC-Adresse ändern nur gültig sein soll, wenn das Gerät in der Fertigung Modus gestartet wurde.

<span id="ResetCallback"></span><span id="resetcallback"></span><span id="RESETCALLBACK"></span>*ResetCallback*  
\[in optionalen\] der Rückrufhandler auf aufzurufende Abschluss zurückgesetzt.

<span id="pvContext"></span><span id="pvcontext"></span><span id="PVCONTEXT"></span>*pvContext*  
\[in optionalen\] der Rückruf angegeben wird, wird dieser Kontextwert bereitgestellt, wenn der Ereignishandler aufgerufen wird.

## <a name="span-idremarksspanspan-idremarksspanspan-idremarksspanremarks"></a><span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Hinweise


Die Callback-Funktion besteht für Wi-Fi Adapter Benachrichtigungen zurücksetzen aus den folgenden Prototyp:

``` syntax
typedef VOID (WINAPI *WLAN_MTE_RESET_CALLBACK)(
    __in    DWORD   dwError,
    __in    PVOID   pvContext
    );
```

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
<td align="left"><p>Zurückgegeben, wenn der Parameter <em>pDot11ResetRequest</em> NULL ist oder der <em>pDot11ResetRequest</em> -Typ ungültig ist.</p></td>
</tr>
<tr class="even">
<td align="left"><p>ERROR_INVALID_HANDLE</p></td>
<td align="left"><p>Zurückgegeben, wenn das Handle <em>hAdapter</em> ungültig ist.</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idrequirementsspanspan-idrequirementsspanspan-idrequirementsspanrequirements"></a><span id="Requirements"></span><span id="requirements"></span><span id="REQUIREMENTS"></span>Anforderungen


**Kopfzeile:** wifimte.w

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Wi-Fi Fertigung-API](wi-fi-manufacturing-api.md)

 

 






