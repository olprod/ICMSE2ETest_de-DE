---
title: STACK\_TRACING\_EREIGNIS\_ID
description: STACK\_TRACING\_EREIGNIS\_ID
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: f03d36fd-9f14-4212-9be6-717e42c18f6f
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: fca9723767f9aa4720b360c52c129c63eca37532
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="stacktracingeventid"></a>STACK\_TRACING\_EREIGNIS\_ID


Diese Struktur weist die Kernelprotokollierung die Aufrufliste für die benannte Ereignisse enthalten.

``` syntax
typedef struct _STACK_TRACING_EVENT_ID {
GUID EventGuid; 
UCHAR Type; 
UCHAR Reserved[7]; 
} STACK_TRACING_EVENT_ID, *PSTACK_TRACING_EVENT_ID
```

## <a name="members"></a>Member


<a href="" id="eventguid"></a>**EventGuid**  
Die GUID an, die ein bestimmter Kernel-Ereignis identifiziert so konfiguriert, dass um Stapel zu generieren. Weitere Informationen zu diesen Member finden Sie unter [NT Kernel-Protokollierung-Konstanten](http://go.microsoft.com/fwlink/p/?LinkID=212227&clcid=0x409). **EventGuids** werden in Evntrace.h aufgelistet.

<a href="" id="type"></a>**Typ**  
Eine der das EREIGNIS\_TRACE\_TYP\_ \* Typen von evntrace.h oder eine der [Trace Steuerelement Ereignistypen](https://msdn.microsoft.com/library/windows/hardware/dn640668.aspx).

<a href="" id="reserved"></a>**Reserviert**  
Für künftige Zwecke vorbehalten.

## <a name="remarks"></a>Hinweise


Die Mitglieder dieser Struktur sind identisch mit denen der KLASSISCHEN\_EREIGNIS\_Struktur-ID in der Windows 7 und Windows Server 2008 SDK verfügbar:

``` syntax
typedef struct _CLASSIC_EVENT_ID {
GUID EventGuid; 
UCHAR Type; 
UCHAR Reserved[7]; 
} CLASSIC_EVENT_ID, *PCLASSIC_EVENT_ID;
```

**Anforderungen:**

**Versionen:** Verfügbar in Windows Vista beginnen. Diese Struktur ist mit Windows Performance Analyzer verteilt.

**Kopfzeilen:** In KernelTraceControl.h deklariert. Enthalten Sie KernelTraceControl.h.

**Bibliothek:** In KernelTraceControl.dll enthalten sind.

## <a name="related-topics"></a>Verwandte Themen


[Strukturen](structures-wpa.md)

 

 







