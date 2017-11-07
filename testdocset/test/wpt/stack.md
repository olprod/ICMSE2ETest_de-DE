---
title: Stapel
description: Stapel
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 7f8b4905-4702-4bba-998e-baa533adcdb2
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 0c2046f70fa861254642f2325bec02ed8a06de5e
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="stack"></a>Stapel


Diese Aktion ergibt eine Textdatei, die Metriken im Zusammenhang mit Stapel zusammengefasst.

``` syntax
-a stack [-butterfly [n]] [-range T1 T2] [-export <format>] [-pid <pid> ...] [-tid <tid> ...] [-process RegEx1 RegEx2 ... RegExN] [-symbol RegEx1 RegEx2 ... RegExN] [-event RegEx1 RegEx2 ... RegExN]
```

## <a name="options"></a>Options


<a href="" id="-butterfly-n-"></a>**-Schmetterling***\[n\]*  
Zeigt die Schmetterling Ansicht der Stapel im dieser Trace, einschließlich nur Symbole, die mindestens &lt; *min\_Treffer* &gt; liegt, gibt an, ob jedes Vorkommen gezählt wird oder nur das erste auftreten. Der Standardwert der *min\_Treffer* ist 10.

<a href="" id="-ranget1-t2"></a>**-Bereichs** *T1 T2*  
Grenzwerte für den Bericht auf das Intervall `[lo, hi]`. Der Standardwert von *T1* ist 0 (null). Ist der Standardwert der *T2* `_I64_MAX`.

<a href="" id="-pid-pid-"></a>**pid -***&lt;pid&gt;*  
Enthält nur Stapel von Geschäftsprozessen mit übereinstimmenden Prozess-IDs.

<a href="" id="-tid-tid-"></a>**Tid -***&lt;Tid&gt;*  
Enthält nur Stapel von Threads mit übereinstimmenden Thread-IDs.

<a href="" id="-processregex1-regex2---regexn"></a>**-Prozess** *RegEx1 RegEx2... RegExN*  
Enthält nur Stapel von Threads, die die bereitgestellten ATL reguläre Ausdrücke entsprechen.

<a href="" id="-symbolregex1-regex2---regexn"></a>**-Symbol** *RegEx1 RegEx2... RegExN*  
Enthält nur Stapel, die Symbole enthalten, die bereitgestellten ATL reguläre Ausdrücke entsprechen.

<a href="" id="-eventregex1-regex2---regexn"></a>**-Ereignis** *RegEx1 RegEx2... RegExN*  
Enthält nur Stapel für Ereignisse, die die bereitgestellten ATL regulären Ausdrücke entsprechen.

## <a name="related-topics"></a>Verwandte Themen


[Xperf Aktionen](xperf-actions.md)

[Zeit- und Timestamp-Formate](time-and-timestamp-formats.md)

 

 







