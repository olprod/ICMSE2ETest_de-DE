---
title: ICSPNode SetValue
description: ICSPNode SetValue
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: b218636d-fe8b-4a0f-b4e8-a621f65619d3
ms.openlocfilehash: fe88c00cf87aeba758bcdd48b90496d807ebd992
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="icspnodesetvalue"></a>ICSPNode::SetValue

Diese Methode setzt den Wert für den Knoten Konfiguration Service Provider. Es ist ein Fehler zu versuchen, den Wert des inneren Knoten festzulegen.

## <a name="syntax"></a>Syntax

``` syntax
HRESULT SetValue([in] VARIANT varValue);
```

## <a name="parameters"></a>Parameter

<a href="" id="varvalue"></a>*varValue*  
<p style="margin-left: 25px">Der Wert, der festgelegt. Um einen Endknoten Wert zu löschen, legen Sie *VarValue*Typ auf `VT_NULL`.</p>

## <a name="return-value"></a>Rückgabewert

Ein Wert von S\_OK gibt an, dass der Wert erfolgreich festgelegt wurde. CFGMGR\_E\_COMMANDNOTALLOWED zeigt an, dass dieser Knoten die **ICSP::SetValue** -Methode nicht unterstützt, oder es ist ein interner Knoten.

## <a name="remarks"></a>Hinweise

Für extern – ungeachtet Knoten müssen keine zusätzlichen Methoden implementiert werden, um Rollback zu unterstützen.

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** None

## <a name="related-topics"></a>Verwandte Themen

[Erstellen eines benutzerdefinierten Konfiguration-Dienstanbieters](create-a-custom-configuration-service-provider.md)

 






