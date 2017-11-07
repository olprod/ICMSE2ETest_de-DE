---
title: ICSPNode verschieben
description: ICSPNode verschieben
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: efb359c3-5c86-4975-bf6f-a1c33922442a
ms.openlocfilehash: 247f8e876dbfd347c197ba8c9f3a980f0213eb38
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="icspnodemove"></a>ICSPNode::Move

Diese Methode verschiebt den Knoten an einen neuen Speicherort innerhalb der Konfigurationsdienstanbieter. Die Ziel-Node bereits vorhanden, sollte sie überschrieben.

## <a name="syntax"></a>Syntax

``` syntax
HRESULT Move([in] IConfigManager2URI* puriDestination);
```

## <a name="parameters"></a>Parameter

<a href="" id="puridestination"></a>*puriDestination*  
<p style="margin-left: 25px">Pfad und Namen der neuen Speicherort des Knotens relativ zum Stammknoten der Konfiguration des Dienstanbieters.</p>

## <a name="return-value"></a>Rückgabewert

Ein Wert von S\_OK gibt an, dass der Knoten erfolgreich verschoben wurde. CFGMGR\_E\_COMMANDNOTALLOWED gibt an, dass dieser Knoten die **ICSP::Move** -Methode nicht unterstützt.

## <a name="remarks"></a>Hinweise

Extern – ungeachtet Knoten, für Wenn diese Methode implementiert ist, klicken Sie dann [ICSPNode::Add](icspnodeadd.md) und [ICSPNode::SetValue](icspnodesetvalue.md) muss auch implementiert werden oder Rollback schlägt fehl.

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** None

## <a name="related-topics"></a>Verwandte Themen

[Erstellen eines benutzerdefinierten Konfiguration-Dienstanbieters](create-a-custom-configuration-service-provider.md)

 






