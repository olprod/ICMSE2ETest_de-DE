---
title: ICSPNode GetPropertyIdentifiers
description: ICSPNode GetPropertyIdentifiers
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 8a052cd3-d74c-40c4-845f-f804b920deb4
ms.openlocfilehash: ff89818afc775b7911cd29266c34d5e83dfd62e9
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="icspnodegetpropertyidentifiers"></a>ICSPNode::GetPropertyIdentifiers

Diese Methode gibt eine Liste mit nicht standardmäßigen Eigenschaften, die von den Knoten unterstützt. Das zurückgegebene Array mit zugeteilt `CoTaskMemAlloc`.

## <a name="syntax"></a>Syntax

``` syntax
HRESULT GetPropertyIdentifiers([out] ULONG* pulCount,
                               [out,size_is(,*pulCount)] GUID** pguidProperties);
```

## <a name="parameters"></a>Parameter

<a href="" id="pulcount"></a>*pulCount*  
<p style="margin-left: 25px">Die Anzahl der nicht standardmäßigen Eigenschaften zurückgegeben werden sollen.</p>

<a href="" id="pguidproperties"></a>*pguidProperties*  
<p style="margin-left: 25px">Das Array von Eigenschaft GUIDs zurückgeben. Dieses Array mit zugeteilt `CoTaskMemAlloc`.</p>

## <a name="return-value"></a>Rückgabewert

Der Wert S\_OK gibt an, dass die Eigenschaften erfolgreich zurückgegeben wurden. E\_NOTIMPL gibt an, dass diese Methode wird von den Knoten nicht unterstützt.

## <a name="remarks"></a>Hinweise

Für extern – ungeachtet Knoten werden keine weiteren Methoden für erfolgreiche Rollback benötigt.

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** None

## <a name="related-topics"></a>Verwandte Themen

[Erstellen eines benutzerdefinierten Konfiguration-Dienstanbieters](create-a-custom-configuration-service-provider.md)

 





