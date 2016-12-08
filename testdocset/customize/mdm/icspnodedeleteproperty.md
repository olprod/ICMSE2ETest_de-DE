---
title: ICSPNode DeleteProperty
description: ICSPNode DeleteProperty
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 7e21851f-d663-4558-b3e8-590d24b4f6c4
ms.openlocfilehash: 4c9d1c4f3d5dfb2d2660495b6e64108d55bdf2d8
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="icspnodedeleteproperty"></a>ICSPNode::DeleteProperty

Diese Methode löscht eine Eigenschaft von einem Knoten Konfiguration Service Provider.

## <a name="syntax"></a>Syntax

``` syntax
HRESULT DeleteProperty([in] REFGUID guidProperty);
```

## <a name="parameters"></a>Parameter

<a href="" id="guidproperty"></a>*guidProperty*  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;GUID der Eigenschaft zu löschen.

## <a name="return-value"></a>Rückgabewert

Der Wert S\_OK gibt an, dass ein Knoten erfolgreich gefunden wurde. CFGMGR\_E\_PROPERTYNOTSUPPORTED gibt an, dass dieser Knoten nicht verwalten ist oder implementieren die Eigenschaft selbst, aber es an delegiert ConfigManager2. E\_NOTIMPL gibt diese Methode wird von diesem Knoten nicht unterstützt.

## <a name="remarks"></a>Hinweise

Für extern – ungeachtet Knoten Wenn diese Methode implementiert ist, dann [ICSPNode::SetProperty](icspnodesetproperty.md) auch implementiert werden müssen oder Rollback schlägt fehl.

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** None

## <a name="related-topics"></a>Verwandte Themen

[Erstellen eines benutzerdefinierten Konfiguration-Dienstanbieters](create-a-custom-configuration-service-provider.md)

 






