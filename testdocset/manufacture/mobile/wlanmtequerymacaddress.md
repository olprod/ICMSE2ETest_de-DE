---
author: kpacquer
Description: WlanMTEQueryMacAddress
ms.assetid: 62953a75-4956-494f-983f-ca6475db2b43
MSHAttr: PreferredLib:/library/windows/hardware
title: WlanMTEQueryMacAddress
ms.openlocfilehash: e70a15eba90575aef27a93faf653f245427b2c34
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="wlanmtequerymacaddress"></a>WlanMTEQueryMacAddress


Gibt die MAC-Adresse des Adapters Wi-Fi zurück.

## <a name="span-idsyntaxspanspan-idsyntaxspanspan-idsyntaxspansyntax"></a><span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Die Syntax


``` syntax
DWORD WlanMTEQueryMacAddress(
    __in    HANDLE              hAdapter,
    __out   DOT11_MAC_ADDRESS   *pDot11MacAddress
);
```

## <a name="span-idparametersspanspan-idparametersspanspan-idparametersspanparameters"></a><span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameter


<span id="hAdapter"></span><span id="hadapter"></span><span id="HADAPTER"></span>*hAdapter*  
\[in\] das Handle für den Adapter Wi-Fi durch Aufrufen von [WlanMTEOpenHandle](wlanmteopenhandle.md)abgerufen.

<span id="pDot11MacAddress"></span><span id="pdot11macaddress"></span><span id="PDOT11MACADDRESS"></span>*pDot11MacAddress*  
\[Skalieren\] die aktuelle MAC-Adresse des Adapters Wi-Fi.

## <a name="span-idreturnvaluespanspan-idreturnvaluespanspan-idreturnvaluespanreturn-value"></a><span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Rückgabewert


Wenn die Funktion erfolgreich ist, wird der Rückgabewert ist FEHLER\_ERFOLG.

Wenn die Funktion fehlschlägt, ist der Rückgabewert eines Fehlercodes System. In der folgenden Tabelle sind die Fehlercodes, die möglicherweise zurückgegeben werden.

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
<td align="left"><p>Zurückgegeben, wenn der Parameter <em>pDot11MacAddress</em> NULL ist.</p></td>
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


[Wi-Fi Manufacturing API](wi-fi-manufacturing-api.md)

 

 






