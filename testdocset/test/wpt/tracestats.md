---
title: tracestats
description: tracestats
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 875ee44a-765d-44e4-b303-867b6c766251
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 400a1b8976be5a324c2504434d48eecd73025800
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="tracestats"></a>tracestats


Diese Aktion ergibt eine Textdatei, die Statistik zusammenfasst.

``` syntax
-a tracestats [-timespan [actual]] [-detail] [-timezone {utc | local}]
```

## <a name="options"></a>Options


<a href="" id="-timespan-actual-"></a>**Timespan -***\[tatsächlichen\]*  
Zeigt Informationen über die Sitzung und verfolgen. In der Standardeinstellung erfordert *Timespan -* Prüfung von nur Kopfzeilen Trace. übergeben Sie keine erfolgt über die Spuren der Sitzung. Wenn "tatsächlich" angegeben ist, werden den tatsächlichen Zeitpunkt des ersten-Ereignis und das letzte Ereignis in der Sitzung mit dem Bericht hinzugefügt. In diesem Fall ist eine Pass-through-die Spuren aus der Sitzung erforderlich.

<a href="" id="-detail--stack-"></a>**-Detail * \[Stapel\]***  
Zeigt detaillierte Informationen zu Anbietern, Identifiers, Aufgaben, Vorgang Codes, Versionen, Kanäle und Ereignisebenen in der Sitzung mit Anbieter und Vorgang Code Anzeigenamen. Erfordert eine vollständige Pass-through-die Spuren aus der Sitzung.

Wenn der *Stack* -Parameter angegeben wird, wird die Anzahl der Stapel für jeden Typ von Ereignis mit dem Bericht hinzugefügt. In diesem Fall ist der zweite Pass-through-die Spuren in der Sitzung erforderlich.

<a href="" id="-timezone-utc-local-"></a>**Timezone-** *{utc | lokalen}*  
Zeigt Zeitstempel in der angegebenen Zeitzone. Wenn ohne Angabe einer Zeitzone angegeben ist, wird standardmäßig die lokale Zeitzone verwendet.

## <a name="related-topics"></a>Verwandte Themen


[Xperf Aktionen](xperf-actions.md)

 

 







