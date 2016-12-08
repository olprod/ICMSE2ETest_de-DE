---
title: sysconfig
description: sysconfig
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: bd020833-a2fe-4619-8d9d-d049fd4e543c
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: c30eb4f8b356d434613acea101e0f912108b143a
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="sysconfig"></a>sysconfig


Diese Aktion ergibt eine Textdatei, die ausführliche Informationen zu dem System wurde auf dem die Verfolgung durchgeführt wurde.

``` syntax
-a sysconfig [-xml] [-netidentity] [-cpu] [-memory] [-build] [-etw] [-power] [-disk] [-idechannel] [-video] [-nic] [-irq] [-services] [-pnp]
```

## <a name="options"></a>Options


<a href="" id="-xml"></a>**Xml-**  
Ausgabe wird im XML-Format.

<a href="" id="-netidentity"></a>**Netidentity-**  
Identitätsinformationen Netzwerk wird angezeigt.

<a href="" id="-cpu"></a>**-cpu**  
Zeigt CPU-Konfiguration.

<a href="" id="-memory"></a>**-Speicher**  
Speicherkonfiguration zeigt.

<a href="" id="-build"></a>**-Erstellen**  
Zeigt Informationen zu erstellen.

<a href="" id="-etw"></a>**Etw-**  
Zeigt die ETW-Versionsinformationen.

<a href="" id="-power"></a>**-Leistung**  
Zeigt Informationen Power Status an.

<a href="" id="-disk"></a>**-Datenträger**  
Datenträgerkonfiguration zeigt.

<a href="" id="-idechannel"></a>**-idechannel**  
DDE Kanalkonfiguration Electronics IDE (Integrated Drive) angezeigt.

<a href="" id="-video"></a>**-video**  
Video zeigt die Konfiguration.

<a href="" id="-nic"></a>**Nic-**  
Zeigt Schnittstelle Controller-Netzwerkkonfiguration.

<a href="" id="-irq"></a>**Irq-**  
Zeigt Interrupt Request (IRQ) Konfiguration an.

<a href="" id="-services"></a>**-Dienste**  
Zeigt Dienstinformationen.

<a href="" id="-pnp"></a>**-Plug & Play-**  
Zeigt Plug & Play -Konfiguration.

## <a name="remarks"></a>Hinweise


Wenn keine Aktivität ausgewählt ist, werden alle Aktivitäten standardmäßig ausgewählt.

## <a name="related-topics"></a>Verwandte Themen


[Xperf Aktionen](xperf-actions.md)

 

 







