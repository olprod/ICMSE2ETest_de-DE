---
title: ICSPNode DeleteChild
description: ICSPNode DeleteChild
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 8cf3663d-a4cf-4d11-b03a-f1d096ad7f9c
ms.openlocfilehash: 20b4c2719c35638256aa2ba69259e5ed6bdca338
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="icspnodedeletechild"></a>ICSPNode::DeleteChild

Löscht den angegebenen untergeordneten Knoten aus der Knoten Konfiguration Service Provider. [ICSPNode::Clear](icspnodeclear.md) muss immer zuerst auf dem untergeordneten Knoten aufgerufen werden, die gelöscht werden soll.

## <a name="syntax"></a>Syntax

``` syntax
HRESULT DeleteChild([in] IConfigManager2URI* puriChildToDelete);
```

## <a name="parameters"></a>Parameter

<a href="" id="purichildtodelete"></a>*puriChildToDelete*  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Der Name des untergeordneten Knotens zu löschen.

## <a name="return-values"></a>Rückgabewerte

| Rückgabewert                 | Beschreibung                                      |
|------------------------------|--------------------------------------------------|
| CFGMGR\_E\_NODENOTFOUND      | Der untergeordneten Knoten ist nicht vorhanden.                    |
| CFGMGR\_E\_COMMANDNOTALLOWED | Der untergeordneten Knoten gelöscht werden soll ist ein nur-Lese-Knoten |
| S\_OK                        | Erfolg.                                         |

 
Der Wert S\_OK gibt an, dass ein Knoten gelöscht wurde. CFGMGR\_E\_NODENOTFOUND gibt an, dass der untergeordneten Knoten nicht existiert. CFGMGR\_E\_COMMANDNOTALLOWED gibt an, dass dieser Knoten die **ICSP::DeleteChild** -Methode nicht unterstützt oder der untergeordneten Knoten gelöscht werden soll ein Knoten schreibgeschützt ist.

## <a name="remarks"></a>Hinweise

Für extern – ungeachtet Knoten können Sie, wenn diese Methode implementiert wird, klicken Sie dann [ICSPNode::Add](icspnodeadd.md) auch implementiert werden müssen oder Rollback schlägt fehl.

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** None

## <a name="related-topics"></a>Verwandte Themen

[Erstellen eines benutzerdefinierten Konfiguration-Dienstanbieters](create-a-custom-configuration-service-provider.md)

 






