---
title: Starten
description: Starten
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: f99fd1e6-bcc0-443f-9f28-555a46d6c02f
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 3cd2b836e8acfddd3cb747058bb0a009a2ccefa4
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="start"></a>Starten


Protokollierung Startoptionen angezeigt.

``` syntax
xperf [-start [LoggerName] [ProfileFileName!ProfileName|SessionName]|-update [LoggerName]|[ProfileFileName!ProfileName|SessionName]] -flush [LoggerName] -save ProfileFileName!ProfileName|SessionName merged.etl -setprofint [<n>] [cached] -seteresourcesample <n1> <n2> <n3> -setspinlocksample <n1> <n2> <n3> -pooltag <P1>+<P2>+<P3>+<P4> -on (GUID|KnownProviderName)[:Flags[:Level[<:0xnnnnnnnn|’stack|[,]sid[,]tsid’]]]
```

## <a name="parameters"></a>Parameter


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Befehl</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>-start</strong> <em>[LoggerName] | [ProfileFileName! Profilname | Sitzungsname]]</em></p></td>
<td><p>Startet eine protokollierungssitzung für <em>LoggerName</em>, startet Protokollierungsmodule im Profil, die in der Datei <em>ProfileFileName</em> <em>Profilname</em> definiert haben, oder startet Protokollierung, die in der Datei <em>ProfileFileName</em> <em>Sitzungsname</em> definiert haben.</p></td>
</tr>
<tr class="even">
<td><p><strong>-Aktualisieren</strong> <em>[LoggerName] | [ProfileFileName! Profilname | Sitzungsname]]</em></p></td>
<td><p>Aktualisiert eine protokollierungssitzung für <em>LoggerName</em>, aktualisiert und Protokollierungsmodule im Profil, die in der Datei <em>ProfileFileName</em> <em>Profilname</em> definiert haben, oder Updates-Protokollierung, die in der Datei <em>ProfileFileName</em> <em>Sitzungsname</em> definiert haben.</p></td>
</tr>
<tr class="odd">
<td><p><strong>-leeren</strong> <em>LoggerName</em></p></td>
<td><p>Leert eine protokollierungssitzung für <em>LoggerName</em>. Dieser Parameter ist erforderlich, um einen Puffer Modus Trace zu speichern (finden Sie unter <em>-Pufferung</em> Parameter Sie weiter unten). Um einen Puffer Modus Trace zu speichern, müssen Sie Problem der <em>-leeren</em> Parameter.</p></td>
</tr>
<tr class="even">
<td><p><strong>-Capturestate</strong> <em>LoggerName Flags</em></p></td>
<td><p>Erfasst Zustand, der nicht Kernel protokollierungssitzung von Anbietern in <em>Flags</em>angegeben. Das akzeptierte Anbieter Format ist identisch <em>-auf</em>. Wenn Flags und Ebene angegeben sind, werden sie während der Aufnahme Zustand aktiviert.</p>
<p>Wird aufgerufen, für die Protokollierung gestartet, mit der <strong>– Pufferung</strong> Option. Es muss folgen <strong>– Beenden</strong> auf Protokollierung stoppen.</p></td>
</tr>
<tr class="odd">
<td><p><strong>-Klicken Sie auf</strong> <em>Flags | Gruppen</em></p></td>
<td><p>Die Abfolge der Kernel Flags und Gruppen aktiviert werden soll, Kernel protokollierungssitzungen getrennt durch Pluszeichen (+). Für Benutzer protokollierungssitzungen die Abfolge der Anbieter aktiviert werden soll, getrennt durch Pluszeichen (+). Das Format akzeptierte Anbieter ist <code>(GUID|KnownProviderName)[:Flags[:Level]]</code>. Finden Sie unter [Anbieter](providers-wpa.md) für eine Liste der gültigen Flags.</p></td>
</tr>
<tr class="even">
<td><p><strong>-f</strong> <em>Filename</em></p></td>
<td><p>Protokolliert Ereignisse in der angegebenen Datei. Der Standardwert ist \Kernel.etl für Kernel Spuren und \User.etl für Benutzer Spuren an.</p></td>
</tr>
<tr class="odd">
<td><p><strong>-Puffergröße</strong> <em>Größe</em></p></td>
<td><p>Legt Ablaufverfolgungsinformationen Puffergröße auf <em>Größe</em>in KB. Mögliche Werte sind 4 auf 1024. Der Standardwert ist 64.</p></td>
</tr>
<tr class="even">
<td><p><strong>-Minbuffers</strong> <em>n</em></p></td>
<td><p>Legt die minimale Anzahl von Trace-Puffer auf <em>n</em>fest. Der Standardwert ist 64.</p></td>
</tr>
<tr class="odd">
<td><p><strong>-MaxPuffer</strong> <em>n</em></p></td>
<td><p>Legt die maximale Anzahl von Trace-Puffer auf <em>n</em>fest. Der Standardwert ist 320.</p></td>
</tr>
<tr class="even">
<td><p><strong>Maxfile -</strong> <em>Größe</em></p></td>
<td><p>Maximale Dateigröße festgelegt auf <em>Größe</em> MB.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Flushtimer -</strong> <em>n</em></p></td>
<td><p>Den flush Timer festgelegt auf <em>n</em> Sekunden.</p></td>
</tr>
<tr class="even">
<td><p><strong>-Boottrace</strong> <em>Flags | Gruppen | deaktiviert</em></p></td>
<td><p>Konfiguriert die Protokollierung Event Tracing for Windows Trace starten. Legen Sie Flags auf &quot;deaktiviert&quot; Boot-Protokollierung deaktivieren. Alle Protokollierung Steuerelement kann in Verbindung mit diesem verwendet werden. Verwenden Sie in Verbindung mit <strong>-f</strong> in einer Datei als \Perf.etl protokolliert.</p></td>
</tr>
<tr class="odd">
<td><p><strong>-Echtzeit</strong></p></td>
<td><p>Ermöglicht die Verfolgung in Echtzeit.</p></td>
</tr>
<tr class="even">
<td><p><strong>-Pufferung</strong></p></td>
<td><p>Modus Tracing Pufferung ermöglicht. Speichern der <strong>-leeren</strong>. Das <strong>-Beenden</strong> Option wird die Ablaufverfolgung nicht gespeichert.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Filemode -</strong> <em>Modus</em></p></td>
<td><p>Legt den Dateimodus fest. Der Standardwert ist &quot;sequenzieller&quot;. Mögliche Modi: &quot;sequenzieller&quot;, &quot;kreisförmige&quot;, &quot;Append&quot;, und &quot;NewFile&quot;.</p></td>
</tr>
<tr class="even">
<td><p><strong>-Clocktype</strong> <em>ClockType</em></p></td>
<td><p>Legt den Uhr fest. Der Standardwert ist &quot;PerfCounter&quot;. Mögliche Typen: &quot;Cycle&quot;, &quot;PerfCounter&quot;, und &quot;SystemTime&quot;.</p></td>
</tr>
<tr class="odd">
<td><p><strong>-stackwalk</strong> <em>flags|@file</em></p></td>
<td><p>Ermöglicht für die angegebenen als Ereignisse durchlaufen von Stapeln <code>Flag+...</code>, oder die Datei für Flags <em>Datei</em> analysiert. Weitere Informationen finden Sie unter [Stackwalk](stackwalk.md).</p></td>
</tr>
<tr class="even">
<td><p><strong>PID -</strong> <em>pid [...]</em></p></td>
<td><p>Prozesse Flags betrifft <code>pid [...]</code>. In Verbindung mit privaten Protokollierungsmodule verwendet.</p></td>
</tr>
<tr class="odd">
<td><p><strong>-Pidnewprocess</strong> <em>&lt;Command-Line&gt;</em></p></td>
<td><p>Einen neuen Prozess, der mit Xperf gestartet wird Flags betrifft &lt; <em>Command-Line</em>&gt;. In Verbindung mit privaten Protokollierungsmodule verwendet.</p></td>
</tr>
<tr class="even">
<td><p><strong>-waitfornewprocess</strong></p></td>
<td><p>Wartet auf einen neuen Prozess mit erstellt <code>-pidNewProcess</code> zurückzugebenden vor dem Beenden.</p></td>
</tr>
<tr class="odd">
<td><p><strong>-Heap</strong></p></td>
<td><p>Ermöglicht die Heap Verfolgung in Prozessen <em>PID</em> und <em>PidNewProcess</em>angegeben wird.</p></td>
</tr>
<tr class="even">
<td><p><strong>-critsec</strong></p></td>
<td><p>Ermöglicht die Verfolgung von kritischen Abschnitt in Prozessen <em>PID</em> und <em>PidNewProcess</em>angegeben wird.</p></td>
</tr>
<tr class="odd">
<td><p><strong>-Setprofint</strong> <em>[&lt;n&gt;] [Cache]</em></p></td>
<td><p>Legt Sampling Zeitabstand für das Profil <code>&lt;n&gt; [1221..10000000]</code>. Wenn zwischengespeichert wird angegeben, Intervallen werden in ETW zwischengespeichert und erneut angewendet, wenn neue ETW Kernel Protokollierungsmodule mit aufgenommene Profil gestartet werden. Die Einheiten sind 100ns. Der Standardwert für <em>n</em> ist 10000. d. h., 1 ms: nicht zwischengespeichert.</p></td>
</tr>
<tr class="even">
<td><p><strong>-Speichern</strong> <em>ProfileFileName! Profilname | Sitzungsname "merged.ETL" enthält</em></p></td>
<td><p>Leert die Protokollierungsmodule im Profil <em>Profilname</em> , die in der Datei <em>ProfileFileName</em> definiert und führt die ETL-Dateien in "merged.ETL" enthält. oder leert Protokollierung <em>Sitzungsname</em> in Datei <em>ProfileFileName</em> definiert und führt die ETL-Datei "merged.ETL" enthält.</p></td>
</tr>
<tr class="odd">
<td><p><strong>-Seteresourcesample</strong> <em>&lt;n1&gt; &lt;n2&gt; &lt;n3&gt;</em></p></td>
<td><p>Legt ERESOURCE Sampling, wobei n1 Samplingrate Version ist größer als oder gleich 1000, n2 Konflikte Samplingrate ist größer als oder gleich 1 und n3 Anzahl übermäßig viele Timeouts ist größer als oder gleich 1. Die Konflikte Abtastrate ist die Rate an, der SpinLock Ereignisse erworben werden, wenn Konflikte auftreten. Wenn dieser Wert 100 ist, wird ein Spinlock Ereignis beispielsweise für jede hundert drehen Sperre Kollisionen erworben.</p></td>
</tr>
<tr class="even">
<td><p><strong>-Setspinlocksample</strong> <em>&lt;n1&gt; &lt;n2&gt; &lt;n3&gt;</em></p></td>
<td><p>Legt den Schwellenwert für die Spinlock Drehfeld auf <code>&lt;n1&gt; [ &gt;=1]</code>. Legt den Spinlock erwerben Samplingrate, <code>&lt;n2&gt; [ &gt;= 1000]</code>. Legt die Spinlock Konflikte Abtastrate auf <code>&lt;n3&gt; [ &gt;= 1]</code>. Nur 64-Bit-Windows 7, Windows Server 2008 R2 und neuere Versionen des Betriebssystems unterstützt Spinlock Instrumentation.</p></td>
</tr>
<tr class="odd">
<td><p><strong>-pooltag</strong> <em>&lt;P1&gt;+&lt;P2&gt;+&lt;P3&gt;+&lt;P4&gt;</em></p></td>
<td><p>Setzt den Pool Tag-Filter (<em>Pn</em>) durch Pluszeichen (+) oder ein Semikolon (;) voneinander getrennt werden. Verwenden Sie ein Fragezeichen (?) für ein einzelnes Zeichen Platzhalter oder ein Sternchen (*) für ein Platzhalterzeichen. Bis zu vier Filter kann angegeben werden.</p></td>
</tr>
</tbody>
</table>

 

## <a name="remarks"></a>Hinweise


Mehrere Protokollierungsmodule können mehrere Optionen zum Starten von gestartet werden, jeweils gefolgt von den Optionen auf, diese Protokollierung angewendet werden soll. Wenn *LoggerName* oder `-start LoggerName` ausgelassen wird, wird die Kernelprotokollierung impliziert. Nur eine einzige Instanz der Kernelprotokollierung kann jederzeit vorhanden sein. Wenn eines der Protokollierungsmodule nicht gestartet werden, werden alle Protokollierungsmodule, die bereits gestartet werden beendet.

## <a name="related-topics"></a>Verwandte Themen


[Xperf-Optionen](xperf-options.md)

 

 







