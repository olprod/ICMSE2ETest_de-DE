---
title: ICSPNode GetProperty
description: ICSPNode GetProperty
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: a2bdc158-72e0-4cdb-97ce-f5cf1a44b7db
ms.openlocfilehash: 8aa482ef59fd86e09c9147909079b2b575af8ad9
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="icspnodegetproperty"></a>ICSPNode::GetProperty

Diese Methode gibt einen Eigenschaftswert aus einem Knoten Konfiguration Service Provider.

## <a name="syntax"></a>Syntax

``` syntax
HRESULT GetProperty([in] REFGUID guidProperty, 
                    [in,out] VARIANT* pvarValue);
```

## <a name="parameters"></a>Parameter

<a href="" id="guidproperty"></a>*guidProperty*  
<p style="margin-left: 25px">GUID, die zurückzugebende Eigenschaft angibt.</p>

<a href="" id="pvarvalue"></a>*pvarValue*  
<p style="margin-left: 25px">Zurückzugebende Wert.</p>

## <a name="return-value"></a>Rückgabewert

Der Wert S\_OK gibt an, dass der Wert der erfolgreich zurückgegeben wurde. CFGMGR\_E\_COMMANDNOTSUPPORTED gibt an, dass der Knoten die Eigenschaft selbst nicht implementiert, aber die Verwaltung von der Eigenschaft, um ConfigManager2 delegiert.

## <a name="remarks"></a>Hinweise

Jeder Knoten muss der CFGMGR behandeln\_EIGENSCHAFT\_DATATYPE-Eigenschaft.

Für extern – ungeachtet Knoten werden keine weiteren Methoden für erfolgreiche Rollback benötigt.

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** None

## <a name="related-topics"></a>Verwandte Themen

[Erstellen eines benutzerdefinierten Konfiguration-Dienstanbieters](create-a-custom-configuration-service-provider.md)

 






