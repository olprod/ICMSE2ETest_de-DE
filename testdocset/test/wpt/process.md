---
title: Prozess
description: Prozess
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 349abd2d-5708-4438-8448-3e9d49618ac5
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 5e4f03f0201d509d58d10719c0d5c5054f389afa
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="process"></a>Prozess


Diese Aktion wird eine Textdatei, die Metriken im Zusammenhang mit der Prozesse zusammenfasst erzeugt.

``` syntax
-a process [[-thread] [-image] [-vm]]|[-tree] [-range T1 T2] [-withsids] [-withcmdline]
```

## <a name="options"></a>Options


<a href="" id="-thread"></a>**-Thread**  
Zeigt Threads an.

<a href="" id="-image"></a>**-Bild**  
Zeigt die Bilder.

<a href="" id="-vm"></a>**Vm-**  
Zeigt reservierte virtueller Arbeitsspeicher Bereiche.

<a href="" id="-tree"></a>**-Struktur**  
Zeigt die Prozess-Struktur.

<a href="" id="-ranget1-t2"></a>**-Bereich** *T1 T2*  
Zeigt Daten zwischen Mal *T1* und *T2*, beide in Mikrosekunden.

<a href="" id="-withsid"></a>**Withsid-**  
Verarbeiten von Berichten zeigt Sicherheits-IDs (SIDs).

<a href="" id="-withcmdline"></a>**-withcmdline**  
Zeigt die Befehlszeile in Verarbeiten von Berichten.

## <a name="remarks"></a>Hinweise


Standardmäßig werden nur Prozesse angezeigt.

## <a name="related-topics"></a>Verwandte Themen


[Xperf Aktionen](xperf-actions.md)

[Zeit- und Timestamp-Formate](time-and-timestamp-formats.md)

 

 







