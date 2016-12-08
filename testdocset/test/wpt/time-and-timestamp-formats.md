---
title: Zeit- und Timestamp-Formate
description: Zeit- und Timestamp-Formate
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 4ef3a58b-da6e-46cb-9655-9c81abce7b71
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 8ae028772788d18c5ed78224743864efc581ad56
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="time-and-timestamp-formats"></a>Zeit- und Timestamp-Formate


Zeigt den Formaten Zeit und Timespan in der Befehlszeile.

``` syntax
xperf -help format
```

## <a name="remarks"></a>Hinweise


Verschiedene Xperf Aktionen support-Optionen, die Zeit- und Timespan-Parameter verwendet werden.

Zeitparameter werden in der Regel durch geschaltet `-range` Optionen. Zeit kann auf eine der in der folgenden Tabelle beschriebenen Formate gelesen werden.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>1234 [s | ms | uns | ns]</p></td>
<td><p>1234 [Sekunden | Millisekunden | Mikrosekunden | Nanosekunden] seit dem Start der Protokolldatei.</p>
<p>Die Standardeinstellung ist Mikrosekunden.</p></td>
</tr>
<tr class="even">
<td><p>2004/12/04:20:05:20.1234[+UTC] physische Systemzeit.</p></td>
<td><p>Alle Komponenten von Datum und Uhrzeit sind mit Ausnahme der Zeitzone zwingend erforderlich. Ohne Angabe einer Zeitzone angegeben ist, wird davon ausgegangen, dass das Zeit werden in der lokalen Zeitzone. (Dies ist auch das Zeitformat von <code>-a tracestats</code>.)</p></td>
</tr>
</tbody>
</table>

 

**Hinweis**  
Nur lokale Zeitzone und UTC werden derzeit unterstützt.

 

TimeSpan Parameter werden normalerweise durch Optionen akzeptieren Auflösungen geschaltet. Zeitspannen können eine der in der folgenden Tabelle beschriebenen Formate gelesen werden.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>1234 [s | ms | uns | ns]</p></td>
<td><p>1234 [Sekunden | Millisekunden | Mikrosekunden | Nanosekunden]</p></td>
</tr>
<tr class="even">
<td><p>20:05:20.1234</p></td>
<td><p>20 Stunden 5 Minuten 20 Sekunden 123.4 Millisekunden. Alle Zeitkomponenten sind zwingend erforderlich.</p></td>
</tr>
</tbody>
</table>

 

**Hinweis**  
Ereignis-Zeitstempel in der Xperf Trace Dump werden immer in Millisekunden dargestellt.

 

## <a name="related-topics"></a>Verwandte Themen


[Xperf Command-Line Reference](xperf-command-line-reference.md)

 

 







