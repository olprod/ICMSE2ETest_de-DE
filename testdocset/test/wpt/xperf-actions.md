---
title: Xperf Aktionen
description: Xperf Aktionen
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 14ea91eb-eb7b-4dd7-a09d-da4743dc3805
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: e584abcb254175dbe0cc3d51320786304bfde1e8
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="xperf-actions"></a>Xperf Aktionen


Xperf Aktionen sind Trace Verarbeiten der Komponenten, die Ereignisinformationen zum Erstellen von Textberichten sortiert werden sollen. Aktionen zusammengefassten Berichte erstellen, die für einen Satz von Ereignissen wie Registrierungszugriffe, Kontextwechsel, greift auf die Datei oder Systemkonfiguration spezifisch sind.

Alle Aktionen werden mit dem folgenden Muster Command-Line aufgerufen:

``` syntax
xperf -i input.etl -o output.txt -a <action_name> [action_parameters]
```

Wobei *input.etl* der Name der Protokolldatei ist, wird *output.txt* ist der Name der Berichtsdatei, und * &lt;Aktion\_Namen&gt; * ist der Name der Aktion. Der Name der Aktion immer vorangestellt ist die `-a` Befehlszeilenoption. Der Name der Aktion kann durch eine oder mehrere aktionsspezifische Parameter folgen.

## <a name="in-this-section"></a>In diesem Abschnitt


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Aktion</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>[Boot](boot.md)</p></td>
<td><p>Zeigt starten und Statistiken Herunterfahren.</p></td>
</tr>
<tr class="even">
<td><p>[bootprefetch](bootprefetch.md)</p></td>
<td><p>Zeigt starten vorab ausgewählt Ereignisse.</p></td>
</tr>
<tr class="odd">
<td><p>[cpudisk](cpudisk.md)</p></td>
<td><p>Zeigt die CPU-/ Datenträgeraktivität.</p></td>
</tr>
<tr class="even">
<td><p>[cswitch](cswitch.md)</p></td>
<td><p>Switch Kontextdaten zeigt.</p></td>
</tr>
<tr class="odd">
<td><p>[diskio](diskio.md)</p></td>
<td><p>Datenträger-e/a-Statistiken zeigt.</p></td>
</tr>
<tr class="even">
<td><p>[diskidlehistogram](diskidlehistogram.md)</p></td>
<td><p>Zeigt ein Histogramm der Datenträgeraktivität und Zeiten im Leerlauf.</p></td>
</tr>
<tr class="odd">
<td><p>[dpcisr](dpcisr.md)</p></td>
<td><p>Zeigt zurückgestellt remote Procedure Call und Interrupt-Routine Statistiken service.</p></td>
</tr>
<tr class="even">
<td><p>[drvdelay](drvdelay.md)</p></td>
<td><p>Zeigt die Verzögerung Treibers.</p></td>
</tr>
<tr class="odd">
<td><p>[Dumper](dumper.md)</p></td>
<td><p>Sichert die Ereignisse in Form von Text.</p></td>
</tr>
<tr class="even">
<td><p>[Dateiname](filename-wpa.md)</p></td>
<td><p>Zeigt Dateinamen.</p></td>
</tr>
<tr class="odd">
<td><p>[focuschange](focuschange.md)</p></td>
<td><p>Zeigt die Windows-Thread Änderungsereignisse Fokus.</p></td>
</tr>
<tr class="even">
<td><p>[hardfault](hardfault.md)</p></td>
<td><p>Zeigt schwerer Fehler Statistiken nach Prozess und die Datei.</p></td>
</tr>
<tr class="odd">
<td><p>[Heap](heap.md)</p></td>
<td><p>Zeigt Prozessinformationen Heap.</p></td>
</tr>
<tr class="even">
<td><p>[markiert](marks.md)</p></td>
<td><p>Zeigt Informationen markiert.</p></td>
</tr>
<tr class="odd">
<td><p>[Fehler](pagefault.md)</p></td>
<td><p>Zeigt Informationen zur Seite verursachte.</p></td>
</tr>
<tr class="even">
<td><p>[Perfctrs](perfctrs.md)</p></td>
<td><p>Zeigt Leistungsindikatoren zu verarbeiten.</p></td>
</tr>
<tr class="odd">
<td><p>[Plug & Play-](pnp.md)</p></td>
<td><p>Zeigt Plug & Play -Ereignisse.</p></td>
</tr>
<tr class="even">
<td><p>[Einlesen](prefetch.md)</p></td>
<td><p>Zeigt einlesen Informationen.</p></td>
</tr>
<tr class="odd">
<td><p>[Prozess](process.md)</p></td>
<td><p>Zeigt Prozess, Thread und Bildinformationen.</p></td>
</tr>
<tr class="even">
<td><p>[Profil](profile-wta.md)</p></td>
<td><p>Zeigt Sampling Profiler-Daten.</p></td>
</tr>
<tr class="odd">
<td><p>[Registrierung](registry.md)</p></td>
<td><p>Zeigt die Registrierung Access Statistik.</p></td>
</tr>
<tr class="even">
<td><p>[Dienste](services.md)</p></td>
<td><p>Zeigt Statusinformationen Service.</p></td>
</tr>
<tr class="odd">
<td><p>[Herunterfahren](shutdown.md)</p></td>
<td><p>Zeigt beim Herunterfahren Statistik.</p></td>
</tr>
<tr class="even">
<td><p>[SpinLock](spinlock.md)</p></td>
<td><p>Zeigt Informationen Spinlock.</p></td>
</tr>
<tr class="odd">
<td><p>[Stack](stack.md)</p></td>
<td><p>Zeigt Informationen zu stapeln.</p></td>
</tr>
<tr class="even">
<td><p>[Anhalten](suspend.md)</p></td>
<td><p>Zeigt anhalten Übergang Informationen.</p></td>
</tr>
<tr class="odd">
<td><p>[sysconfig](sysconfig.md)</p></td>
<td><p>Zeigt Informationen zur Systemkonfiguration.</p></td>
</tr>
<tr class="even">
<td><p>[tracestats](tracestats.md)</p></td>
<td><p>Zeigt Statistiken zu verfolgen.</p></td>
</tr>
<tr class="odd">
<td><p>[Winlogon](winlogon.md)</p></td>
<td><p>Zeigt Ereignisse an Winlogon.</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>Verwandte Themen


[Command-Line Reference Xperf](xperf-command-line-reference.md)

 

 







