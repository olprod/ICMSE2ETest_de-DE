---
author: kpacquer
Description: Aufrufen von SetScreenOff eingeben verbunden standby
ms.assetid: b9fddd1f-485b-4b09-9b18-93b994ebc076
MSHAttr: PreferredLib:/library/windows/hardware
title: Aufrufen von SetScreenOff eingeben verbunden standby
ms.openlocfilehash: b5b6a8a9ed011b731f3e6a99ee9ca0e2f10e777a
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="calling-setscreenoff-to-enter-connected-standby"></a>Aufrufen von SetScreenOff eingeben verbunden standby


Aufrufen der Funktion **SetScreenOff** deaktiviert den Bildschirm und die Beleuchtung, wodurch das Telefon in der verbundenen standby Power Zustand wechselt. Dieser Zustand mit niedrigere kann für das Testen des Stromverbrauchs hilfreich sein.

**Wichtige**  
Diese Funktion ist nur in der Microsoft Manufacturing OS verwenden.

 

## <a name="span-idsyntaxspanspan-idsyntaxspanspan-idsyntaxspansyntax"></a><span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Die Syntax


``` syntax
HRESULT SetScreenOff();
```

## <a name="span-idparametersspanspan-idparametersspanspan-idparametersspanparameters"></a><span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameter


Keine

## <a name="span-idreturnvaluespanspan-idreturnvaluespanspan-idreturnvaluespanreturn-value"></a><span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Rückgabewert


HRESULT

## <a name="span-idremarksspanspan-idremarksspanspan-idremarksspanremarks"></a><span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Hinweise


Es ist keine entsprechende Funktion, um das Gerät in einen Zustand volle Leistungsfähigkeit zurückzugeben.

## <a name="span-idexamplespanspan-idexamplespanspan-idexamplespanexample"></a><span id="Example"></span><span id="example"></span><span id="EXAMPLE"></span>Beispiel


SetScreenOff für die Verwendung enthalten Sie die Kopfzeile, und rufen Sie ohne Parameter aus.

``` syntax
#include <ManufacturingConnectedStandbyControl.h>
SetScreenOff();
```

## <a name="span-idrequirementsspanspan-idrequirementsspanspan-idrequirementsspanrequirements"></a><span id="Requirements"></span><span id="requirements"></span><span id="REQUIREMENTS"></span>Anforderungen


**Kopfzeile:** ManufacturingConnectedStandbyControl.h

**Bibliothek:** ManufacturingConnectedStandbyControl.lib

 

 





