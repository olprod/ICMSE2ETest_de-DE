---
title: Einlesen
description: Einlesen
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 8769558a-7749-4696-82b3-50e237d846d7
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 8ae48dc04ea49fbfc81be8ee24754a21755aa6fa
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="prefetch"></a>Einlesen


Diese Aktion ergibt eine Textdatei, die die Metriken in Bezug auf Prefetch-Funktionen zusammengefasst.

``` syntax
-a prefetch [-summary] [-timeunit <unit> [<precision>]] [-min <duration>]
```

## <a name="options"></a>Options


<a href="" id="-summary"></a>**-Zusammenfassung**  
Die Prefetch-Szenarien in das Ablaufverfolgungsprotokoll angezeigt.

<a href="" id="-timeunit-unit----precision--"></a>**Timeunit -***&lt;Einheit&gt; \[ &lt;mit doppelter Genauigkeit&gt;\]*  
Zeit Präsentation Verwendung Zeiteinheit konfiguriert &lt; *Einheit* &gt; und optional Uhrzeit Genauigkeit &lt; *Genauigkeit*&gt;. Die Einheiten möglicherweise "ns" (Nanosekunden), "uns" (Mikrosekunden), "ms" (in Millisekunden) oder "s" (in Sekunden).

<a href="" id="-min-duration-"></a>**min -***&lt;Dauer&gt;*  
Zeigt nur einzelne Anzeigedauer in Mikrosekunden, länger als oder gleich &lt; *Dauer*&gt;.

## <a name="related-topics"></a>Verwandte Themen


[Xperf Aktionen](xperf-actions.md)

[Zeit- und Timestamp-Formate](time-and-timestamp-formats.md)

 

 







