---
title: Stackwalk
description: Stackwalk
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 00864c2f-0a49-4d6f-a65d-a792245f2875
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: f02db1488480c0320c7d64d5ceea61106c5509b2
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="stackwalk"></a>Stackwalk


Zeigt Optionen Stapel durchlaufen. Flags-Stapel durchlaufen können direkt in der Befehlszeile oder in einer Datei angegeben werden.

``` syntax
xperf -on base -stackwalk ThreadCreate+ProcessCreate
```

- Oder -

``` syntax
xperf -on base -stackwalk ThreadCreate -stackwalk ProcessCreate
```

- Oder -

``` syntax
xperf -on base -stackwalk @stack.txt
```

- Oder -

``` syntax
xperf -on base -stackwalk 0x0501
```

## <a name="remarks"></a>Hinweise


Benutzerdefinierte Stapel durchlaufen Flags im Format angegeben werden kann: 0 X*Mmnn*, wobei *mm* Ereignisgruppe und *Nn* Ereignistyp ist.

Leere Zeilen oder Kommentare, die durch ein Ausrufezeichen (!) als Präfix vorangestellt ist, kann die Datei enthalten.

Die folgende Liste enthält die erkannten Kennzeichen Stapel durchlaufen:

-   AlpcClosePort

-   AlpcConnectFail

-   AlpcConnectRequest

-   AlpcConnectSuccess

-   AlpcReceiveMessage

-   AlpcSendMessage

-   AlpcUnwait

-   AlpcWaitForNewMessage

-   AlpcWaitForReply

-   CcCanIWriteFail

-   CcFlushCache

-   CcFlushSection

-   CcLazyWriteScan

-   CcReadAhead

-   CcWorkitemComplete

-   CcWorkitemDequeue

-   CcWorkitemEnqueue

-   CcWriteBehind

-   ContiguousMemoryGeneration

-   CritSecCollision

-   CSwitch

-   DiskFlushInit

-   DiskReadInit

-   DiskWriteInit

-   ExecutiveResource

-   FileCleanup

-   FileClose

-   DateiErstellen

-   Datei löschen

-   FileDirEnum

-   FileDirNotify

-   FileFlush

-   FileFSCTL

-   FileOpEnd

-   FileQueryInformation

-   FileRead

-   FileRename

-   FileSetInformation

-   FileWrite

-   HardFault

-   HeapAlloc

-   HeapCreate

-   HeapDestroy

-   HeapFree

-   HeapRangeCreate

-   HeapRangeDestroy

-   HeapRangeRelease

-   HeapRangeReserve

-   HeapRealloc

-   ImageLoad

-   ImageUnload

-   KernelQueueDequeue

-   KernelQueueEnqueue

-   KernelSignal

-   KernelSignalInit

-   KernelSync

-   KernelSyncAll

-   KernelWaitSync

-   KernelWaitSyncAll

-   MapFile

-   Mark

-   MiniFilterPostOpInit

-   MiniFilterPreOpInit

-   PagefaultAV

-   PagefaultCopyOnWrite

-   PagefaultDemandZero

-   PagefaultGuard

-   PagefaultHard

-   PagefaultTransition

-   PagefileBackedImageMapping

-   PageRangeAccess

-   PageRangeRelease

-   Pool zuweisen

-   PoolAllocSession

-   PoolFree

-   PoolFreeSession

-   PowerDeviceNotify

-   PowerDeviceNotifyComplete

-   PowerIdleStateChange

-   PowerPerfStateChange

-   PowerPostSleep

-   PowerPreSleep

-   PowerSessionCallout

-   PowerSessionCalloutReturn

-   PowerSetDevicesState

-   PowerSetDevicesStateReturn

-   PowerSetPowerAction

-   PowerSetPowerActionReturn

-   PowerThermalConstraint

-   ProcessCreate

-   ProcessDelete

-   Profil

-   ProfileSetInterval

-   ReadyThread

-   RegCloseKey

-   Funktionen RegCreateKey

-   RegDeleteKey

-   Fehler bei RegDeleteValue

-   RegEnumerateKey

-   RegEnumerateValueKey

-   RegFlush

-   RegKcbCreate

-   RegKcbDelete

-   RegOpenKey

-   RegQueryKey

-   RegQueryMultipleValue

-   RegQueryValue

-   RegSetInformation

-   RegSetValue

-   RegVirtualize

-   SplitIO

-   SyscallEnter

-   SyscallExit

-   ThreadCreate

-   ThreadDelete

-   ThreadPoolCallbackCancel

-   ThreadPoolCallbackDequeue

-   ThreadPoolCallbackEnqueue

-   ThreadPoolCallbackStart

-   ThreadPoolCallbackStop

-   ThreadPoolClose

-   ThreadPoolCreate

-   ThreadPoolSetMaxThreads

-   ThreadPoolSetMinThreads

-   ThreadSetBasePriority

-   ThreadSetPriority

-   TimerSetOneShot

-   TimerSetPeriodic

-   UnMapFile

-   VirtualAlloc

-   VirtualFree

## <a name="example"></a>Beispiel


Die Stapel durchlaufen Flag Datei kann eine beliebige Anzahl von Stapel durchlaufen Flags pro Zeile, getrennt durch Leerzeichen, Pluszeichen (+), oder klicken Sie auf neue Zeilen, wie im folgenden Beispiel dargestellt enthalten.

``` syntax
ThreadCreate ProcessCreate
DiskReadInit+DiskWriteInit+DiskFlushInit
CSwitch
```

## <a name="related-topics"></a>Verwandte Themen


[Xperf-Optionen](xperf-options.md)

 

 







