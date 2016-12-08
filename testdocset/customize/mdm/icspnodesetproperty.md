---
title: ICSPNode SetProperty
description: ICSPNode SetProperty
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: e235c38f-ea04-4cd8-adec-3c6c0ce7172d
ms.openlocfilehash: b980dbd11c2ebe46afaab516b5f14ba8ab10a6be
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="icspnodesetproperty"></a>ICSPNode::SetProperty

Diese Methode legt den Wert einer Eigenschaft für ein Knoten Konfiguration Service Provider.

## <a name="syntax"></a>Syntax

``` syntax
HRESULT SetProperty([in] REFGUID guidProperty, 
                    [in] VARIANT varValue);
```

## <a name="parameters"></a>Parameter

<a href="" id="guidproperty"></a>*guidProperty*  
<p style="margin-left: 25px">Die GUID der-Eigenschaft.</p>

<a href="" id="varvalue"></a>*varValue*  
<p style="margin-left: 25px">Der zurückzugebende Wert.</p>

## <a name="return-value"></a>Rückgabewert

Der Wert S\_OK gibt an, dass ein Knoten erfolgreich gefunden wurde. CFGMGR\_E\_COMMANDNOTSUPPORTED gibt an, dass dieser Knoten die Verwaltung der Eigenschaft ConfigManager2 delegiert.

## <a name="remarks"></a>Hinweise

Alle Knoten muss ordnungsgemäß zu behandeln, die CFGMGR\_EIGENSCHAFT\_DATATYPE-Eigenschaft.

Für extern – ungeachtet Knoten werden keine weiteren Methoden für erfolgreiche Rollback benötigt.

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** None

## <a name="related-topics"></a>Verwandte Themen

[Erstellen eines benutzerdefinierten Konfiguration-Dienstanbieters](create-a-custom-configuration-service-provider.md)

 






