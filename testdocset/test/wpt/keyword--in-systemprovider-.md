---
title: "Schlüsselwort (in &quot;Systemprovider&quot;)"
description: "Schlüsselwort (in &quot;Systemprovider&quot;)"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: afe8e6db-f5ad-4a94-9878-97840f91b8b2
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: cc635aaccce829e7cc184b0f0c32980c97d6e37f
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="keyword-in-systemprovider"></a>Schlüsselwort (in "Systemprovider")


Beschreibt die Kernel Flags, die für den Kernelmodus-Sitzung aktiviert sein können.

## <a name="element-hierarchy"></a>Hierarchie-Elements


&lt;[WindowsPerformanceRecorder](windowsperformancerecorder.md)&gt;

     &lt;[Profiles](profiles.md)&gt;

          &lt;[SystemProvider](systemprovider.md)&gt;

               &lt;[Keywords (in SystemProvider)](keywords--in-systemprovider-.md)&gt;

                    &lt;**Keyword (in SystemProvider)**&gt;

          &lt;[Profile](profile-wpr.md)&gt;

               &lt;[Collectors](collectors.md)&gt;

                    &lt;[SystemCollectorId](systemcollectorid.md)&gt;

                         &lt;[SystemProviderId](systemproviderid.md)&gt;

                                &lt;[Keywords (in SystemProvider)](keywords--in-systemprovider-.md)&gt;

                                     &lt;**Keyword (in SystemProvider)**

                         &lt;[SystemProvider](systemprovider.md)&gt;

                                &lt;[Keywords (in SystemProvider)](keywords--in-systemprovider-.md)&gt;

                                     &lt;**Keyword (in SystemProvider)**

## <a name="syntax"></a>Syntax


``` syntax
<Keyword Value = "AllFaults" | "CompactCSwitch" | "ContiguousMemorygeneration" | ... >
</Keyword>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente


### <a name="attributes"></a>Attribute

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
<th>Attribut</th>
<th>Beschreibung</th>
<th>Datentyp</th>
<th>Erforderlich</th>
<th>Standard</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Wert</strong></p></td>
<td><p>Beschreibt das Systemereignis Event Tracing for Windows (ETW).</p></td>
<td><p>Finden Sie im Abschnitt "Hinweise" möglichen Werte.</p></td>
<td><p>Ja</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>

 

### <a name="child-elements"></a>Untergeordnete Elemente

Keine.

### <a name="parent-elements"></a>Übergeordnete Elemente

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Element</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>[Schlüsselwörter (in "Systemprovider")](keywords--in-systemprovider-.md)</p></td>
<td><p>Stellt eine Auflistung von Schlüsselwörtern System.</p></td>
</tr>
</tbody>
</table>

 

## <a name="remarks"></a>Hinweise


In der folgenden Tabelle werden die möglichen Werte für das **Value** -Attribut beschrieben.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Wert</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>AllFaults</p></td>
<td><p>Alle Fehler werden protokolliert.</p></td>
</tr>
<tr class="even">
<td><p>CompactCSwitch</p></td>
<td><p>In Verbindung mit verwendet &quot;CSwitch&quot;, dies reduziert die Informationen für jede CSwitch protokolliert als auch differenzielle Komprimierung und Batchverarbeitung verwendet.</p></td>
</tr>
<tr class="odd">
<td><p>ContiguousMemorygeneration</p></td>
<td><p>Zusammenhängender Arbeitsspeicher Generierung wird protokolliert.</p></td>
</tr>
<tr class="even">
<td><p>CpuConfig</p></td>
<td><p>Änderungen in CPU-Konfiguration werden protokolliert.</p></td>
</tr>
<tr class="odd">
<td><p>CSwitch</p></td>
<td><p>Kontext-Switch-Aktivität wird protokolliert.</p></td>
</tr>
<tr class="even">
<td><p>DiskIO</p></td>
<td><p>Datenträger-e/a angemeldet ist.</p></td>
</tr>
<tr class="odd">
<td><p>DiskIOInitialization</p></td>
<td><p>Datenträger-e/a-Initialisierung wird protokolliert.</p></td>
</tr>
<tr class="even">
<td><p>DPC</p></td>
<td><p>Zurückgestellte Prozeduraufrufe angemeldet sind.</p></td>
</tr>
<tr class="odd">
<td><p>Treiber</p></td>
<td><p>Treiber-Aktivität wird protokolliert.</p></td>
</tr>
<tr class="even">
<td><p>FileIO</p></td>
<td><p>E/a angemeldet ist.</p></td>
</tr>
<tr class="odd">
<td><p>FileIOInit</p></td>
<td><p>E/a-Initialisierung wird protokolliert.</p></td>
</tr>
<tr class="even">
<td><p>Dateiname</p></td>
<td><p>Der Dateiname wird protokolliert.</p></td>
</tr>
<tr class="odd">
<td><p>Speicherbedarf</p></td>
<td><p>Dies gibt an, verwendet, um Arbeitsspeicheranalyse durchzuführen, des Arbeitssatzes auf eine spezielle flush Markierung zu leeren.</p></td>
</tr>
<tr class="even">
<td><p>HardFaults</p></td>
<td><p>Schwerer Fehler protokolliert werden.</p></td>
</tr>
<tr class="odd">
<td><p>IdleStates</p></td>
<td><p>Im Leerlauf States werden protokolliert.</p></td>
</tr>
<tr class="even">
<td><p>Unterbrechen</p></td>
<td><p>Interrupts werden protokolliert.</p></td>
</tr>
<tr class="odd">
<td><p>KernelQueue</p></td>
<td><p>Änderungen an die Warteschlange Kernel werden protokolliert.</p></td>
</tr>
<tr class="even">
<td><p>Ladeprogramm</p></td>
<td><p>Kernel und Modus laden und Entladeereignisse protokolliert werden.</p></td>
</tr>
<tr class="odd">
<td><p>Arbeitsspeicher</p></td>
<td><p>Stellt Ereignisse zur Verwendung des physischen Arbeitsspeichers bereit.</p></td>
</tr>
<tr class="even">
<td><p>MemoryInfo</p></td>
<td><p>Enthält grundlegende Informationen zu der Speicher-Manager wie Anzahl von freien, wird verwendet, und standby Seiten und So weiter.</p></td>
</tr>
<tr class="odd">
<td><p>Pool</p></td>
<td><p>Änderungen an der Speicherpool angemeldet sind.</p></td>
</tr>
<tr class="even">
<td><p>Potenz</p></td>
<td><p>Stromverbrauchs wird protokolliert.</p></td>
</tr>
<tr class="odd">
<td><p>ProcessCounter</p></td>
<td><p>Gibt an, dass das Profil einen Prozess Indikator besitzt.</p></td>
</tr>
<tr class="even">
<td><p>ProcessThread</p></td>
<td><p>Prozess und Thread erstellen und Löschen von Ereignisse werden protokolliert.</p></td>
</tr>
<tr class="odd">
<td><p>ReadyThread</p></td>
<td><p>Bereit Threadereignisse werden protokolliert.</p></td>
</tr>
<tr class="even">
<td><p>Registrierung</p></td>
<td><p>Änderungen in der Registrierung werden protokolliert.</p></td>
</tr>
<tr class="odd">
<td><p>SampledProfile</p></td>
<td><p>Das Profil wird aufgenommen.</p></td>
</tr>
<tr class="even">
<td><p>SpinLock</p></td>
<td><p>SpinLock protokolliert.</p></td>
</tr>
<tr class="odd">
<td><p>SplitIO</p></td>
<td><p>Enthält die Ereignisse zu teilen e/a-Anforderungen. Einzelne e/a-Anforderungen können mehrere Anforderungen aufgrund einer Fragmentierung der Festplatte oder aus anderen Gründen aufgeteilt werden soll.</p></td>
</tr>
<tr class="even">
<td><p>SystemCall</p></td>
<td><p>Anrufe System angemeldet sind.</p></td>
</tr>
<tr class="odd">
<td><p>ThreadPriority</p></td>
<td><p>Änderungen in Thread Priority werden protokolliert.</p></td>
</tr>
<tr class="even">
<td><p>Timer</p></td>
<td><p>Stellt Ereignisse für den Timer System bereit.</p></td>
</tr>
<tr class="odd">
<td><p>VirtualAllocation</p></td>
<td><p>Zuweisung von virtuellem Speicher wird protokolliert.</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>Verwandte Themen


[Elemente](elements.md)

[CustomKeyword](customkeyword.md)

 

 







