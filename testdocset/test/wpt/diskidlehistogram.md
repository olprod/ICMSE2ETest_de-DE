---
title: diskidlehistogram
description: diskidlehistogram
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 16552102-b666-4c50-b530-87b31c4838be
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 80cf7c897e4c0c98bb259b7f76b098ed1b626422
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="diskidlehistogram"></a>diskidlehistogram


Diese Aktion erzeugt ein Histogramm an, die alle Datenträgeraktivität und Leerlaufzeit anzeigt.

``` syntax
-a diskidlehistogram [-disknum <n>] [-buckets B1 B2 ... Bn] [-idletimeout T1 T2 ... Tn] [-idletheshold <t>] [-spindownOverhead [t]] [-spinupOverhead [t]] [-exc_file File1 File2 ... FileN] [-exc_filestr String1 String2 ... StringN] [-exc_filere <regex>]
```

## <a name="options"></a>Options


<a href="" id="-disknum-n-"></a>**-Disknum***&lt;n&gt;*  
*n* gibt die Anzahl der Datenträger (0-basierte Index) an. Der Standardwert lautet Histogramme für alle Datenträger ausgegeben.

<a href="" id="-bucketsb1-b2---bn"></a>**-Buckets** *B1 B2... Bn*  
Unterschiedliche Bereiche im Leerlauf Länge geben Sie Argumente in Sekunden an. Standard-Buckets lauten wie folgt:

-   \[0 s, 1 s\]

-   \[1 s, 5 s\]

-   \[5 s 60 s\]

-   \[60 s 180 s\]

-   \[180 s 600 s\]

-   \[600 s 900 s\]

-   \[900 s, 1200 s\]

-   \[1200 s, 1800 s\]

-   \[1800 s + INF-Datei\]

Ein Datenträger im Leerlauf Histogramm zeigt die Verteilung der Leerlaufzeit des Datenträgers und die Anzahl der Zeiträume, im Leerlauf über unterschiedliche Bereiche im Leerlauf Period Länge, wie in diesem Beispiel wird Werte in der folgenden Tabelle dargestellt.

<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<thead>
<tr class="header">
<th></th>
<th>Weniger als 1 Sekunde</th>
<th>1-600 Sekunden</th>
<th>Mehr als 600 Sekunden</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Leerlaufzeit</p></td>
<td><p>1000</p></td>
<td><p>1000</p></td>
<td><p>2000</p></td>
</tr>
<tr class="even">
<td><p>Prozent der gesamten Zeit im Leerlauf</p></td>
<td><p>25</p></td>
<td><p>25</p></td>
<td><p>50</p></td>
</tr>
<tr class="odd">
<td><p>Anzahl der im Leerlauf</p></td>
<td><p>90</p></td>
<td><p>5</p></td>
<td><p>5</p></td>
</tr>
<tr class="even">
<td><p>Prozent der Gesamtzahl der im Leerlauf</p></td>
<td><p>90</p></td>
<td><p>5</p></td>
<td><p>5</p></td>
</tr>
</tbody>
</table>

 

Die erste Zeile zeigt die Histogramm-Buckets: unterschiedliche Bereiche im Leerlauf Länge.

Die zweite Zeile zeigt die kumulierte Leerlaufzeit für jede Bucket. Beispielsweise ist die kumulierte Leerlaufzeit für alle im Leerlauf Perioden kürzer als 1 Sekunde 1.000 Sekunden.

Die dritte Zeile berechnet den Prozentsatz der Leerlaufzeit für jede Bucket durch Dividieren der Leerlaufzeit für ein Bucket durch die gesamte Zeit im Leerlauf.

Die vierte Zeile ist die Anzahl der Zeiträume, im Leerlauf für jede Bucket aufgezeichnet werden. In diesem Beispiel werden 90 dauert weniger als eine Sekunde im Leerlauf Perioden vorhanden.

Die letzte Zeile berechnet der Prozentsatz im Leerlauf Zeiträume für jede Bucket durch die Anzahl der im Leerlauf Zeiträume für ein Bucket mit der gesamten Anzahl der Zeiträume, im Leerlauf Division.

Der folgende Befehl erzeugt der Buckets in der folgenden Liste: **-Buckets 1 s 5s 60 s 180s**:

-   \[0, 1 s\]

-   \[1 s, 5 s\]

-   \[5 s 60 s\]

-   \[60 s 180 s\]

-   \[180 s + INF-Datei\]

<a href="" id="-idletimeoutt1-t2---tn"></a>**Idletimeout-** *T1 T2... TN*  
Das Leerlauftimeout Geben Sie Argumente in Sekunden an. Die Standardwerte sind 5, 60, 180, 600 und 1800.

<a href="" id="-idletheshold-t-"></a>**-Idletheshold***&lt;t&gt;*  
Argumente geben Sie den Schwellenwert im Leerlauf in Sekunden an. Im Leerlauf Punkte kürzer als dieser Schwellenwert überschritten werden ignoriert.

<a href="" id="-spindownoverhead-t-"></a>**SpindownOverhead -***\[t\]*  
Wenn Sie ein Argument nicht angeben, ist der Standardwert 0.

Eine Folge von Datenträger-e/a-Zeitstempel und einer angegebenen Leerlauftimeout verwenden, können Sie beim Datenträger nach unten und wie Hintergrundthread würde berechnen viel Zeit im Hintergrundthread Dropdownmenü Zustand, bleiben wie in der folgenden Tabelle beschrieben vererbt werden.

<table>
<colgroup>
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
</colgroup>
<thead>
<tr class="header">
<th>Timeoutwert in Sekunden</th>
<th>5</th>
<th>60</th>
<th>180</th>
<th>600</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Geschätzte Spindown Gelegenheit Zeit in Sekunden</p></td>
<td><p>3800</p></td>
<td><p>2000</p></td>
<td><p>1000</p></td>
<td><p>500</p></td>
</tr>
<tr class="even">
<td><p>Geschätzte Anzahl an Spindown Verkaufschancen</p></td>
<td><p>500</p></td>
<td><p>100</p></td>
<td><p>50</p></td>
<td><p>10</p></td>
</tr>
</tbody>
</table>

 

Die erste Zeile zeigt die Leerlauftimeout Werte für die verbleibende Zeit wird Hintergrundthread Dropdownmenü von Interesse an. Die zweite Zeile zeigt die geschätzte Hintergrundthread Dropdownmenü Gesamtzeit für jede Timeout. In diesem Beispiel wird zurückgegeben, die ein Timeout von 5 Sekunden die Hintergrundthread Dropdownmenü Gesamtzeit 3800 Sekunden. Die dritte Zeile zeigt die geschätzte Anzahl an, wie oft, die der Datenträger heruntergefahren wird, für jeden Timeoutwert.

<a href="" id="-spinupoverheadt"></a>**-spinupOverhead** *T*  
Wenn Sie ein Argument nicht angeben, ist der Standardwert 0 Sekunden.

<a href="" id="-exc-filefile1-file1---filen"></a>**- Exc\_Datei** *File1 File1... Genehmigung*  
Die bereitgestellten vollständige Dateipfade übereinstimmenden Dateien ausgeschlossen werden. Sie müssen für jede Datei den vollständigen Pfad angeben, den, die Sie ausschließen möchten.

<a href="" id="-exc-filestrstring1-string2---stringn"></a>**- Exc\_Filestr** *Zeichenfolge1 Zeichenfolge2... StringN*  
Dateien, die eine oder mehrere der angegebenen Zeichenfolgen werden ausgeschlossen.

<a href="" id="-exc-filere-regx-"></a>**-Exc\_Filere***&lt;Regx&gt; *  
Den bereitgestellten ATL regulären Ausdruck übereinstimmenden Dateien werden ausgeschlossen. Sie können beispielsweise enden mit .dll durch Angeben des Ausdrucks ignorieren ". \*\\.dll".

**Hinweis**   Wenn Sie eine neue Zeile zu definieren, müssen Sie eine Zeilenschaltung einbeziehen. Statt ** \\n**, verwenden Sie ** \\r\\n**. Durch das Einbeziehen von beide Zeichen (Wagenrücklauf = R; Zeilenvorschub = n), erstellen Sie ein Abschlusszeichen Linie. Dies ist hilfreich, wenn eine [interessante Bereiche](regions-of-interest.md) -Datei zu erstellen.

 

## <a name="remarks"></a>Hinweise


Es gibt einige Systemdateien, deren Datenträger e/as als Reaktion auf Datenträger-e/a auf andere Dateien sind. Diese Systemdateien gehören die folgenden:

-   $LogFiles

-   $Mft

-   $Bitmap

-   lastalive0.dat

-   lastalive1.dat

-   $UsnJrnl: $J

Es kann schwierig sein, unterscheiden, welche Datenträger e/a zu den anderen Dateien ein bestimmtes Laufwerk e/a auf die oben genannten Systemdateien verursachen. Aus diesem Grund, wenn Sie die Auswirkungen der Dateien angezeigt, die Sie ausgeschlossen haben möchten, müssen Sie auch diese Systemdateien ausschließen. Da diese Systemdateien Datenträger e/as als Antwort auf oder auf andere Datenträger-e/a "piggyback" sind, wird nur diese Systemdateien selbst ignoriert nicht erwartet, dass Datenträger im Leerlauf Histogramm erheblich ändern.

Ausgabe aus dieser Aktion kann in einer Kalkulationstabelle zum Sortieren und Analysis importiert werden. Für die Ausgabe werden zwei zusätzliche Metriken bereitgestellt:

<a href="" id="avgiointerval"></a>**AvgIOInterval**  
Für eine bestimmte Datei ist dies das durchschnittliche Intervall zwischen den beiden nachfolgenden e/a auf diese Datei. Diese Metrik kann irreführende werden, wenn eine Datei Abständen kleine e/a, beispielsweise Abständen von weniger als 1 Sekunde. Auch wenn diese Datei ebenfalls große e/a-Abständen, beispielsweise 30 Minuten ist das durchschnittliche e/a-Intervall sieht viel schlechter als eine andere Datei mit Mittel kurze Intervallen e/a, wie etwa 10 Minuten. Sie können in diesem Fall verwenden `-idlethreshold T` im Leerlauf Zeiten mit weniger als 1 Sekunde aus der Analyse zu entfernen.

<a href="" id="maxiointerval"></a>**MaxIOInterval**  
Für jede Datei ist dies das maximale Intervall zwischen zwei nachfolgenden e/a zu dieser Datei. Die Ausgabe wird standardmäßig basierend auf dieser Metrik sortiert. Eine Datei mit einem großen e/a-Intervall kann häufig verwendete e/a noch im Durchschnitt haben.

**Hinweis**  
Verwenden Sie beide der folgenden Metriken und pro Datei Histogramme für einen umfassenden Überblick über die Datenträgeraktivität.

 

Vermeiden Sie Modellnetz die Laufwerke unter Studie mithilfe eines anderen physischen Datenträger (oder Gerät wie ein USB-Flashlaufwerk) um die Ablaufverfolgung zu erfassen.

## <a name="example"></a>Beispiel


Das folgende Beispiel zeigt eine typische Verwendung dieser Aktion mit Standardparametern

``` syntax
Xperf -i Trace.etl -a diskidlehistogram > output.csv
```

Sammeln von Informationen auf Datenträger-e/as sowie verwandte Informationen wie Registrierung/Cswitch/Stapel für den Fall, dass tiefere Analyse erforderlich ist. `Compact_cswitch`kann verwendet werden, um Trace Dateigröße zu verringern. Im folgenden Codebeispiel wird einer Reihe von empfohlenen Xperf Kennzeichen.

``` syntax
xperf -on dispatcher+PROC_THREAD+LOADER+CSWITCH+COMPACT_CSWITCH +registry+DISK_IO+DISK_IO_INIT+FILEIO -stackwalk cswitch+readythread+DiskReadInit+DiskWriteInit+DiskFlushInit -buffersize 1024
sleep <desired trace time in seconds> or run scenario
xperf -d trace.etl
```

## <a name="related-topics"></a>Verwandte Themen


[Xperf Aktionen](xperf-actions.md)

 

 







