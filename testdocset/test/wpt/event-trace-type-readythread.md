---
title: EREIGNIS\_TRACE\_TYP\_READYTHREAD
description: EREIGNIS\_TRACE\_TYP\_READYTHREAD
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: a34bf78c-2d42-485e-a64c-e87256ba08c7
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: a0525d4812cd9e6d871499f78790302e8d21ae74
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="eventtracetypereadythread"></a>EREIGNIS\_TRACE\_TYP\_READYTHREAD


Dieses Kennzeichen ermöglicht stapelablaufverfolgung für ReadyThread Ereignisse.

``` syntax
#define EVENT_TRACE_TYPE_READYTHREAD 0x32
```

## <a name="remarks"></a>Hinweise


Dieser Ereignistyp ähnelt der Ereignistypen in der **-EREIGNIS verwendet\_TRACE\_EIGENSCHAFTEN. EnableFlags** Member ist aber speziell für die Kernel Trace-Steuerelement-API.

**Anforderungen:**

**Versionen:** Verfügbar in Windows Vista beginnen. Diese Struktur ist mit Windows Performance Analyzer verteilt.

**Kopfzeilen:** In KernelTraceControl.h deklariert. Enthalten Sie KernelTraceControl.h.

**Bibliothek:** In KernelTraceControl.dll enthalten sind.

## <a name="related-topics"></a>Verwandte Themen


[Verfolgen von Steuerelement Ereignistypen](trace-control-event-types.md)

 

 







