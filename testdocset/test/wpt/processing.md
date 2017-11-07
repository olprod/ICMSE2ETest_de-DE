---
title: Verarbeitung
description: Verarbeitung
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: effacd2f-9804-434e-bbd9-128cddd7f940
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 2ab4f11a0148c9903cbad92af73db2a0db687590
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="processing"></a>Verarbeitung


Zeigt Trace Nachbearbeitung Optionen.

``` syntax
xperf -i <trace file>… [-o output] [-symbols …] [-target {human|machine}] [-a action …[-a action …] …]
```

## <a name="parameters"></a>Parameter


<a href="" id="-itrace-file"></a>**-i** *Ablaufverfolgungsdatei*  
Die Ablaufverfolgungsdatei verarbeitet werden.

<a href="" id="-ooutput-file"></a>**-o** *Ausgabedatei*  
Der Name der Ausgabedatei. Wenn nicht angegeben, wird die **Stdout** verwendet.

<a href="" id="-symbols-options-"></a>**-Symbole***\[Optionen\]*  
Aktivieren Sie und konfigurieren Sie der Unterstützung Decodierung Symbol. Weitere Informationen finden Sie unter [Symbole](symbols.md).

<a href="" id="-target-human-machine-"></a>**-Ziel** *{human | Computer}*  
Wählen Sie die Zielgruppe der Ausgabe aus. Der Standardwert ist "human".

<a href="" id="-quiet"></a>**-quiet**  
Statusinformationen werden nicht gedruckt werden.

<a href="" id="-tle"></a>**-tle**  
Verarbeiten Sie die Ablaufverfolgung, auch wenn verloren gegangene Ereignisse. Die *TLE* Akronyms *tolerieren verloren gegangene Ereignisse*.

<a href="" id="-tti"></a>**-tti**  
Trace auch bei Inversions Zeit zu verarbeiten. Die *TTI* Akronyms *tolerieren Zeit Inversions*.

<a href="" id="-aaction----"></a>**-a** *Aktion...*  
Die Aktionen vorgenommen werden sollen. Die Standardaktion besteht, um das Ereignis in Form von Text zu sichern.

## <a name="remarks"></a>Hinweise


In der folgenden Tabelle werden die verfügbare Aktionen beschrieben.

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
<td><p>Zeigt beim Starten und Herunterfahren Statistik.</p></td>
</tr>
<tr class="even">
<td><p>[bootprefetch](bootprefetch.md)</p></td>
<td><p>Zeigt die Start-vorab Informationen.</p></td>
</tr>
<tr class="odd">
<td><p>[cpudisk](cpudisk.md)</p></td>
<td><p>Zeigt Aktivitätsbericht CPU/Datenträger.</p></td>
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
<td><p>Zeigt alle Datenträgeraktivität und im Leerlauf Zeitangaben im Histogramm-Format dar.</p></td>
</tr>
<tr class="odd">
<td><p>[dpcisr](dpcisr.md)</p></td>
<td><p>Anzeigen der DPC/ISR Statistik.</p></td>
</tr>
<tr class="even">
<td><p>[drvdelay](drvdelay.md)</p></td>
<td><p>Zeigt die Verzögerung Treibers.</p></td>
</tr>
<tr class="odd">
<td><p>[Dumper](dumper.md)</p></td>
<td><p>Sichert Ereignisse in der Verfolgung in Form von Text.</p></td>
</tr>
<tr class="even">
<td><p>[Dateiname](filename-wpa.md)</p></td>
<td><p>Dateinamen in der Verfolgung anzeigen.</p></td>
</tr>
<tr class="odd">
<td><p>[focuschange](focuschange.md)</p></td>
<td><p>Zeigt die Windows-Thread Änderungsereignisse den Fokus in das Ablaufverfolgungsprotokoll.</p></td>
</tr>
<tr class="even">
<td><p>[hardfault](hardfault.md)</p></td>
<td><p>Zeigt schwerer Fehler Statistiken nach Prozess und die Datei.</p></td>
</tr>
<tr class="odd">
<td><p>[Heap](heap.md)</p></td>
<td><p>Zeigt heap Informationen.</p></td>
</tr>
<tr class="even">
<td><p>[markiert](marks.md)</p></td>
<td><p>Zeigt Informationen markiert.</p></td>
</tr>
<tr class="odd">
<td><p>[Fehler](pagefault.md)</p></td>
<td><p>Zeigt Informationen zur Seite Fehlertoleranz in das Ablaufverfolgungsprotokoll.</p></td>
</tr>
<tr class="even">
<td><p>[Perfctrs](perfctrs.md)</p></td>
<td><p>Zeigt Leistungsindikatoren zu verarbeiten.</p></td>
</tr>
<tr class="odd">
<td><p>[Plug & Play-](pnp.md)</p></td>
<td><p>Plug & Play-Ereignisse in der Verfolgung dargestellt.</p></td>
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
<td><p>Zeigt Informationen für Spinlock Aktivität relevant.</p></td>
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
<td><p>Zeigt Windows-Anmeldung Ereignisse in der Verfolgung.</p></td>
</tr>
</tbody>
</table>

 

Wenn keine Aktion vorhanden ist, wird **Dumper** aufgerufen.

## <a name="example"></a>Beispiel


Die folgende Tabelle enthält Beispiele für die **Verarbeitung**.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><code>xperf -i trace.etl -o out.csv</code></p></td>
<td><p>Sichert die Ereignisse in trace.etl in der Datei Out.csv.</p></td>
</tr>
<tr class="even">
<td><p><code>xperf -help registry</code></p></td>
<td><p>Hilfe für die <strong>Registrierung</strong> Aktion ausgegeben.</p></td>
</tr>
<tr class="odd">
<td><p><code>xperf -i trace.etl -a registry</code></p></td>
<td><p>Druckt die Registrierung Access Statistiken für <strong>Stdout</strong>.</p></td>
</tr>
<tr class="even">
<td><p><code>xperf -i trace32.etl trace64.etl -o out.csv</code></p></td>
<td><p>Sichert die Ereignisse in Trace32.etl und Trace64.etl an der Datei Out.csv.</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>Verwandte Themen


[Xperf-Optionen](xperf-options.md)

 

 







