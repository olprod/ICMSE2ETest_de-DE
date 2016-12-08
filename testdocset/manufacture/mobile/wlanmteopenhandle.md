---
author: kpacquer
Description: WlanMTEOpenHandle
ms.assetid: 82017f67-a089-4c99-af7e-f10735db60c3
MSHAttr: PreferredLib:/library/windows/hardware
title: WlanMTEOpenHandle
ms.openlocfilehash: cf3e03f52ee4cb0a30b3e40371a8d28c33ae2a04
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="wlanmteopenhandle"></a>WlanMTEOpenHandle


Öffnet ein Handle auf der Grundlage der angegebenen GUID-Schnittstelle Treiber, und gibt das Handle mit dem Anrufer zurück.

## <a name="span-idsyntaxspanspan-idsyntaxspanspan-idsyntaxspansyntax"></a><span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Die Syntax


``` syntax
DWORD WlanMTEOpenHandle(
    __in    GUID    *pAdapterGuid,
    __out   HANDLE  *phAdapter
);
```

## <a name="span-idparametersspanspan-idparametersspanspan-idparametersspanparameters"></a><span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameter


<span id="pAdapterGuid"></span><span id="padapterguid"></span><span id="PADAPTERGUID"></span>*pAdapterGuid*  
\[in\] einen Zeiger auf die GUID, identifiziert der Wi-Fi-Netzwerkadapter, auf dem das Handle geöffnet werden.

<span id="phAdapter"></span><span id="phadapter"></span><span id="PHADAPTER"></span>*phAdapter*  
\[Skalieren\] einen Zeiger auf das Handle Wi-Fi, wenn sie erfolgreich geöffnet wurde.

## <a name="span-idreturnvaluespanspan-idreturnvaluespanspan-idreturnvaluespanreturn-value"></a><span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Rückgabewert


Wenn die Funktion erfolgreich ist, wird der Rückgabewert ist FEHLER\_ERFOLG.

Wenn die Funktion eines der Fehlercodes System Ausfall wird zurückgegeben. Die folgende Tabelle enthält die Fehlercodes, die möglicherweise zurückgegeben werden.

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
<td align="left"><p>Wenn die Parameter <em>pAdapterGuid</em> oder <em>PhAdapter</em> NULL sind zurückgegeben.</p></td>
</tr>
<tr class="even">
<td align="left"><p>ERROR_INVALID_STATE</p></td>
<td align="left"><p>Zurückgegeben, wenn Sie der aktuelle Modus der Dot11-Operation nicht abgerufen werden kann.</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idremarksspanspan-idremarksspanspan-idremarksspanremarks"></a><span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Hinweise


Die Liste der Wi-Fi-Schnittstelle können durch den aufrufenden [WlanMTEEnumAdapters](wlanmteenumadapters.md)GUIDs abgerufen werden.

## <a name="span-idrequirementsspanspan-idrequirementsspanspan-idrequirementsspanrequirements"></a><span id="Requirements"></span><span id="requirements"></span><span id="REQUIREMENTS"></span>Anforderungen


**Kopfzeile:** wifimte.w

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Wi-Fi Fertigung-API](wi-fi-manufacturing-api.md)

 

 






