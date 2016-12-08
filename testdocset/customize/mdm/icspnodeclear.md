---
title: "ICSPNode löschen"
description: "ICSPNode löschen"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: b414498b-110a-472d-95c0-2d5b38cd78a6
ms.openlocfilehash: e23b2e078c131a070238f862ac426ce80e76cafd
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="icspnodeclear"></a>ICSPNode::Clear

Diese Methode löscht den Inhalt und die untergeordneten Knoten des aktuellen Knotens der Konfiguration Service Provider. Diese Methode wird immer auf den untergeordneten Knoten aufgerufen, vor dem Aufruf von [ICSPNode::DeleteChild](icspnodedeletechild.md) auf dem übergeordneten Knoten.


## <a name="syntax"></a>Syntax

``` syntax
HRESULT Clear();
```


## <a name="return-value"></a>Rückgabewert

Ein Wert von S\_OK gibt an, dass der Knoten wurde erfolgreich deaktiviert. CFGMGR\_E\_COMMANDNOTALLOWED gibt an, dass dieser Knoten die **Clear** -Methode nicht unterstützt.


## <a name="remarks"></a>Hinweise

Für extern – ungeachtet Knoten Wenn diese Methode implementiert ist, dann [ICSPNode::SetValue](icspnodesetvalue.md) und [ICSPNode::SetProperty](icspnodesetproperty.md) müssen auch implementiert werden oder Rollback schlägt fehl.

Vor dem Aufruf von auf dem Zielknoten **Löschen** , versucht ConfigManager2 den aktuellen Status des Knotens zu erfassen. der übergeordnete Knoten muss nicht den Status der untergeordneten Knoten beibehalten, wenn sie extern ungeachtet sind.

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** None


## <a name="related-topics"></a>Verwandte Themen

[Erstellen eines benutzerdefinierten Konfiguration-Dienstanbieters](create-a-custom-configuration-service-provider.md)

 





