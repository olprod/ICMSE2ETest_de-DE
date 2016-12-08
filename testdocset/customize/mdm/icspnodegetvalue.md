---
title: ICSPNode GetValue
description: ICSPNode GetValue
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: c684036d-98be-4659-8ce8-f72436a39b90
ms.openlocfilehash: 487b04617e234564354ea470536b79dd98e540e6
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="icspnodegetvalue"></a>ICSPNode::GetValue

Diese Methode ruft den Typ von Wert und Daten für den Knoten ab. Interior (innerer Knotenebene) Knoten möglicherweise keinen Wert haben.

## <a name="syntax"></a>Syntax

``` syntax
HRESULT GetValue([in,out] VARIANT* pvarValue);
```

## <a name="parameters"></a>Parameter

<a href="" id="pvarvalue"></a>*pvarValue*  
<p style="margin-left: 25px">Datenwert zurückgegeben. Ein Knoten mit einem Kennwortwert gibt 16 Sternchen ("\*") für diese Methode. Ein Endknoten, deren Wert nicht festgelegt wurde, gibt eine Variante vom Typ `VT_NULL`.
</p>

## <a name="return-value"></a>Rückgabewert

Der Wert S\_OK gibt an, dass ein Knoten erfolgreich gefunden wurde. CFGMGR\_E\_COMMANDNOTALLOWED gibt an, dass dieser Knoten die **ICSP::GetValue** Methoden nicht unterstützt werden oder dies einer inneren Knoten ist.

## <a name="remarks"></a>Hinweise

Für extern – ungeachtet Knoten ist dieser Knoten nicht erforderlich, um andere Methoden für eine erfolgreiche Rollback zu implementieren.

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** None

## <a name="related-topics"></a>Verwandte Themen

[Erstellen eines benutzerdefinierten Konfiguration-Dienstanbieters](create-a-custom-configuration-service-provider.md)

 






