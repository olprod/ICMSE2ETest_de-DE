---
title: Anhalten
description: Anhalten
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 76df9308-9496-43a7-90cb-113ff5f672a8
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 5077eff78b9e01a3b32fae9cff7f5a1ab5337eda
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="suspend"></a>Anhalten


Diese Aktion ergibt eine XML-Datei, die werden die Metriken für die Suspend-Sequenz zusammengefasst.

``` syntax
-a suspend [-summary] [-timeout <unit> [<precision>]] [-min <duration>]
```

## <a name="options"></a>Options


<a href="" id="-summary"></a>**-Zusammenfassung**  
Zeigt die Suspend-Übergänge in diesem Trace.

<a href="" id="-timeunit-unit----precision--"></a>**Timeunit -***&lt;Einheit&gt; \[ &lt;mit doppelter Genauigkeit&gt;\]*  
Konfigurieren Sie Zeit Präsentation Zeiteinheit verwenden, um &lt; *Einheit* &gt; und optional Uhrzeit mit doppelter Genauigkeit &lt; *Genauigkeit*&gt;. Mögliche Zeiteinheiten sind "ns" (Nanosekunden), "uns" (Mikrosekunden), "ms" (in Millisekunden) oder "s" (in Sekunden).

<a href="" id="-min-duration-"></a>**min -***&lt;Dauer&gt;*  
Zeigt die einzelnen Anzeigedauer länger als oder gleich &lt; *Dauer*&gt;.

## <a name="remarks"></a>Hinweise


Wenn Sie keine Option angeben **-Zusammenfassung** wird standardmäßig verwendet.

## <a name="related-topics"></a>Verwandte Themen


[Xperf Aktionen](xperf-actions.md)

[Zeit- und Timestamp-Formate](time-and-timestamp-formats.md)

 

 







