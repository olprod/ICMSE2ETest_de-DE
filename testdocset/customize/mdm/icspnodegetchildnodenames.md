---
title: ICSPNode GetChildNodeNames
description: ICSPNode GetChildNodeNames
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: dc057f2b-282b-49ac-91c4-bb83bd3ca4dc
ms.openlocfilehash: 13c3711bdd27b56c41305b73f6e70a6680083587
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="icspnodegetchildnodenames"></a>ICSPNode::GetChildNodeNames

Diese Methode gibt die Liste der untergeordneten Knoten ein Knoten Konfiguration Service Provider.

## <a name="syntax"></a>Syntax

``` syntax
HRESULT GetChildNodeNames([out] ULONG* pulCount,
                          [out,size_is(,*pulCount)] BSTR** pbstrNodeNames);
```

## <a name="parameters"></a>Parameter

<a href="" id="pulcount"></a>*pulCount*
<p style="margin-left: 25px">Die Anzahl der untergeordneten Knoten zurückgegeben.</p>

<a href="" id="pbstrnodenames"></a>*pbstrNodeNames*
<p style="margin-left: 25px">Das Array von untergeordneten Knotennamen. Das zurückgegebene Array mit zugeteilt `CoTaskMemAlloc`. Jedes Element des Arrays muss eine gültige, nicht NULL sein `BSTR`gibt, durch `SysAllocString` oder `SysAllocStringLen`. Die zurückgegebenen Namen müssen nicht keinerlei Kanonisierung Gründen einschließlich URI-Codierung codiert werden.</p>

## <a name="return-value"></a>Rückgabewert

Der Wert S\_OK gibt an, dass ein Knoten erfolgreich gefunden wurde. CFGMGR\_E\_COMMANDNOTALLOWED gibt an, dass dies auf einem Endknoten aufgerufen wurde (es werden keine untergeordneten Elemente zurückgegeben werden).

## <a name="remarks"></a>Hinweise

Für extern – ungeachtet Knoten werden keine weiteren Methoden für erfolgreiche Rollback benötigt.

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** None

## <a name="related-topics"></a>Verwandte Themen

[Erstellen eines benutzerdefinierten Konfiguration-Dienstanbieters](create-a-custom-configuration-service-provider.md)

 






