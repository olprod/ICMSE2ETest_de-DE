---
author: kpacquer
Description: WlanMTEEnumAdapters
ms.assetid: f89ddb61-0c2d-446b-9f81-3e2c88311d61
MSHAttr: PreferredLib:/library/windows/hardware
title: WlanMTEEnumAdapters
ms.openlocfilehash: 8c53e26ad60329b087063315073b779c7c83354e
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="wlanmteenumadapters"></a>WlanMTEEnumAdapters


Gibt die Liste der Adapter an, die von den Wi-Fi-Stapel erkannt werden.

## <a name="span-idsyntaxspanspan-idsyntaxspanspan-idsyntaxspansyntax"></a><span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Die Syntax


``` syntax
DWORD WlanMTEEnumAdapters(
    __out_opt   WLAN_MTE_ADAPTER_LIST  **ppWlanAdapterList
);
```

## <a name="span-idparametersspanspan-idparametersspanspan-idparametersspanparameters"></a><span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameter


<span id="ppWlanAdapterList"></span><span id="ppwlanadapterlist"></span><span id="PPWLANADAPTERLIST"></span>*ppWlanAdapterList*  
\[Skalieren\] eine Liste der erkannten Wi-Fi-Adapter.

## <a name="span-idreturnvaluespanspan-idreturnvaluespanspan-idreturnvaluespanreturn-value"></a><span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Rückgabewert


Wenn die Funktion erfolgreich ist, wird der Rückgabewert ist FEHLER\_ERFOLG. Andernfalls gibt die Funktion einen Systemfehler-Code.

## <a name="span-idrequirementsspanspan-idrequirementsspanspan-idrequirementsspanrequirements"></a><span id="Requirements"></span><span id="requirements"></span><span id="REQUIREMENTS"></span>Anforderungen


**Kopfzeile:** wifimte.w

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Wi-Fi Manufacturing API](wi-fi-manufacturing-api.md)

 

 






