---
title: Profil
description: Profil
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: b0b4c89c-70e7-4fe8-986d-e057b8074c9e
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: d35f424d336707825d8a7dcf22ce16c4e8a7412b
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="profile"></a>Profil


Diese Aktion ergibt eine Textdatei, die Metriken für Profile zusammenfasst.

``` syntax
-a profile [-util [n]] [-detail] [-range T1 [T2]]
```

## <a name="options"></a>Options


<a href="" id="-util-n-"></a>**-zur bandbreitenauslastung durch***\[n\]*  
Zeigt die CPU-Auslastung für *n* -Sekunde-Intervallen. Der Standardwert ist 1 Sekunde.

<a href="" id="-detail"></a>**-Details**  
Zeigt CPU-Beispiele bucketed Prozess Modul Wenn Symbol Decodierung nicht aktiviert ist, sowie über den Prozess und die Funktion Namen Symbol Decodierung aktiviert ist.

<a href="" id="-ranget1--t2-"></a>**-Bereichs** *T1 \[T2\]*  
Zeigt Daten zwischen Mal *T1* und *T2*, beide in Mikrosekunden. Wenn *T2* nicht vorhanden ist, wird das Ende der Trace stattdessen verwendet.

<a href="" id="-freq"></a>**-freq**  
Zeigt Konstante Sampling Häufigkeit Zonen in der Verfolgung an.

## <a name="remarks"></a>Hinweise


Wenn keine der `-util`, `-detail`, oder `-freq` angegeben ist, wird standardmäßig den CPU-Auslastung Bericht angezeigt wird.

## <a name="related-topics"></a>Verwandte Themen


[Xperf Aktionen](xperf-actions.md)

 

 







