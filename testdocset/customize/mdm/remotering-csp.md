---
title: RemoteRing CSP
description: RemoteRing CSP
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 70015243-c07f-46cb-a0f9-4b4ad13a5609
ms.openlocfilehash: 19c74a4f6706970a224a12399fe0e504e87e5bb4
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="remotering-csp"></a>RemoteRing CSP


Dienstanbieter RemoteRing Konfiguration kann verwendet werden, Remote ausgelöst ein Gerät, um einen Signalton klingeln, unabhängig von der Lautstärke zu erstellen, die auf dem Gerät festgelegt ist.

Das folgende Diagramm zeigt den RemoteRing Konfiguration-Dienstanbieter in der Strukturformat.

![Bereitstellung\-Csp\-Remotering](images/provisioning-csp-remotering.png)

<a href="" id="ring"></a>**Anrufen**  
Erforderlich. Der Knoten akzeptiert Anforderungen an das Gerät weitergeleitet.

Die unterstützten Exec ist.

## <a name="examples"></a>Beispiele


Im folgende Beispiel veranschaulicht, wie ein remote Anrufen auf dem Gerät zu initiieren.

``` syntax
<Exec>
  <CmdID>5</CmdID> 
    <Item> 
    <Target> 
      <LocURI>./Vendor/MSFT/RemoteRing/Ring </LocURI> 
    </Target> 
    </Item> 
</Exec>
```

 

 






