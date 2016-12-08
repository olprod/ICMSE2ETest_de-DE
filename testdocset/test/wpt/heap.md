---
title: Heap
description: Heap
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 5a8b4c32-9a36-4668-831a-8dc6fa9e2c5d
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 8af99f93f0afed3fb960a70f4911319b044c5948
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="heap"></a>Heap


Schreibt eine Textdatei mit die folgenden Informationen in Tabellenform basierend auf der Ausgabedatei angegeben durch `-o`:

-   Anzahl der zuordnen

-   Zuordnen der Größe in KB

-   Skalierung Anzahl

-   Skalieren Größe in KB

-   Anzahl der realloc

-   Blöcke Größe in KB

-   Skalieren Ext Größe in KB

-   Heap handle

``` syntax
-a heap [-pid <processId>] [-stacks] [-frames] [-images] [-range T1 T2] [-lifetime T1 T2] [-size S1 S2] [-cullframes Frame1 Frame2 ... FrameN] [-requireframes Frame1 Frame2 ... FrameN] [-cullLists cullfuncs.txt] [-top <n>] [-totals]
```

## <a name="options"></a>Options


<a href="" id="-pid-processid-"></a>**pid -***&lt;ProcessId&gt;*  
Zeigt Statistiken nur für die angegebene Prozess-ID an. Wenn nicht angegeben, zeigt Statistiken für alle Prozesse.

<a href="" id="-stacks-s--o-oc-t-tc-rc--"></a>**-Stapel***\[s \[o | Oc | t | Tc | rc\]\]*  
Zeigt die Verteilung von Stapel aggregiert. Dies ist das Standardverhalten.

Sortiert nach ausstehender Größe (*so*), ausstehender Count (*Soc*, Gesamtgröße (*St*) Neubelegung Count (*Src*und Gesamtzahl (*Stc*). Der Standardwert ist *damit*.

<a href="" id="-frames-s--o-oc-t-tc-rc--"></a>**-Frames***\[s \[o | Oc | t | Tc | rc\]\]*  
Ähnlich wie `-stacks`, aber die Aggregation ist oberster Stapel Rahmen, anstelle von durch den gesamten Stapel.

<a href="" id="-images"></a>**-Bilder**  
Ähnlich wie `-stacks` und `-frames`, aber die Aggregation namentlich Bild des Rahmens oberster Stapel ist.

<a href="" id="-ranget1-t2"></a>**-Bereichs** *T1 T2*  
Verwenden von Ereignisdaten aus Mal *T1* über *T2*, beide in Mikrosekunden an.

<a href="" id="-lifetimet1-t2"></a>**-Lebensdauer** *T1 T2*  
Nur die Verteilung mit einer Lebensdauer Mikrosekunden, größer als oder gleich *T1* und kleiner als *T2*einschließen.

<a href="" id="-sizes1-s2"></a>**-Größe** *S1 S2*  
Enthalten Sie nur Zuweisungen Größen größer als oder gleich *S1* und kleiner als *S2*, in Byte.

<a href="" id="-cullframesframe1-frame2---framen"></a>**-cullframes** *"Frame1" Frame2... FrameN*  
Entfernt alle Rahmen oberster Stapel aus dem Bericht, die eines der angegebenen Framesseite entsprechen. Das Parameterformat ist `[image!][symbol]`. Die Groß-und Kleinschreibung nicht berücksichtigt.

<a href="" id="-requireframesframe1-frame2---framen"></a>**-requireframes** *"Frame1" Frame2... FrameN*  
Erfordert, dass jeder Stapel mindestens einen Frame haben, die mindestens eines der angegebenen Framesseite entspricht. Bei diesem Test tritt auf, bevor alle expliziten Frame mit culling `-cullframes`.

<a href="" id="-culllists-filename-"></a>**-CullLists***&lt;Dateiname&gt;*  
Frames in der angegebenen Datei werden vom Ergebnis ausgeschlossen werden. Wenn ein Stapel solcher Rahmen nicht enthalten ist, wird der Stack ausgeschlossen. Frames haben das gleiche Format wie für `-cullFrames`. Die Groß-und Kleinschreibung nicht berücksichtigt.

<a href="" id="-top-n-"></a>**-top***&lt;n&gt;*  
Beschränkt die Anzahl der Zuweisungen angezeigt.

<a href="" id="-totals"></a>**-Summen**  
Zeigt nur die Summen der Zuweisung Ereignisse.

## <a name="remarks"></a>Hinweise


Diese Aktion kann mehrere Minuten in Anspruch auf eine umfangreiche aufgrund der extra fette Sortierung und Abgleich ausgeführt.

Informationen zum Heap Datenerfassung finden Sie unter [Heap Datenerfassung aktivieren](enabling-heap-data-capture.md)

## <a name="related-topics"></a>Verwandte Themen


[Xperf Aktionen](xperf-actions.md)

[Zeit- und Timestamp-Formate](time-and-timestamp-formats.md)

 

 







