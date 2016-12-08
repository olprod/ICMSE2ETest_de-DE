---
title: Puffer
description: Puffer
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 8f60d3e3-cb32-4879-8ac2-80ceaea945d3
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 9e190119bf8837b2e00539970c69d605b7227c8f
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="buffers"></a>Puffer


Entweder die Anzahl der Puffer Starten einer Sitzung oder den Prozentsatz des Gesamtspeichers für die Sitzung, abhängig vom Wert des Attributs **PercentageOfTotalMemory** zuzuweisende zuzuweisende beschreibt.

## <a name="element-hierarchy"></a>Hierarchie-Elements


&lt;[WindowsPerformanceRecorder](windowsperformancerecorder.md)&gt;

     &lt;[Profiles](profiles.md)&gt;

          &lt;[SystemCollector](systemcollector.md)&gt;

               &lt;**Buffers**&gt;

          &lt;[EventCollector](eventcollector.md)&gt;

               &lt;**Buffers**&gt;

          &lt;[HeapEventCollector](heapeventcollector.md)

               &lt;**Buffers**&gt;

          &lt;[Profile](profile-wpr.md)&gt;

               &lt;[Collectors](collectors.md)&gt;

                    &lt;[SystemCollectorId](systemcollectorid.md)&gt;

                         &lt;**Buffers**&gt;

                    &lt;[EventCollectorId](eventcollectorid.md)&gt;

                         &lt;**Buffers**&gt;

                    &lt;[HeapEventCollectorId](heapeventcollectorid.md)&gt;

                         &lt;**Buffers**&gt;

## <a name="syntax"></a>Syntax


``` syntax
<Buffers Operation               = "Set" | "Add" | “Remove”
         Value                   = unsignedLong
         PercentageOfTotalMemory = boolean>
</Buffers>
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
<td><p><strong>Verwendung</strong></p></td>
<td><p>Gibt an, ob Puffer festgelegt oder hinzugefügt werden soll.</p></td>
<td><p>Dieses Attribut kann einen der folgenden Werte aufweisen:</p>
<ul>
<li><p>Gruppe</p></li>
<li><p>Add</p></li>
<li><p>Entfernen</p></li>
</ul></td>
<td><p>Nein</p></td>
<td><p>Gruppe</p></td>
</tr>
<tr class="even">
<td><p><strong>Wert</strong></p></td>
<td><p>Gibt die Anzahl der Puffer, oder wenn <strong>PercentageOfTotalMemory</strong> festgelegt ist, dass &quot;true&quot;, den Prozentsatz des Arbeitsspeichers für die Puffer.</p></td>
<td><p>unsignedLong</p></td>
<td><p>Ja</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p><strong>PercentageOfTotalMemory</strong></p></td>
<td><p>Bei Festlegung auf &quot;true&quot;, beschränkt die Größe des Arbeitsspeichers, die auf den Wert der <strong>Wert</strong>genutzt werden kann.</p></td>
<td><p>boolean</p></td>
<td><p>Nein</p></td>
<td><p>falsch</p></td>
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
<td><p>[EventCollector](eventcollector.md)</p></td>
<td><p>Stellt eine Ereignissammlung.</p></td>
</tr>
<tr class="even">
<td><p>[EventCollectorId](eventcollectorid.md)</p></td>
<td><p>Stellt einen Bezeichner der Ereignis-Sammlung.</p></td>
</tr>
<tr class="odd">
<td><p>[HeapEventCollector](heapeventcollector.md)</p></td>
<td><p>Stellt eine Ereignissammlung Heap dar.</p></td>
</tr>
<tr class="even">
<td><p>[HeapEventCollectorId](heapeventcollectorid.md)</p></td>
<td><p>Stellt einen Bezeichner für Heap-Ereignis-Sammlung.</p></td>
</tr>
<tr class="odd">
<td><p>[SystemCollector](systemcollector.md)</p></td>
<td><p>Stellt einen Collector des Systems.</p></td>
</tr>
<tr class="even">
<td><p>[SystemCollectorId](systemcollectorid.md)</p></td>
<td><p>Stellt einen System Collector Bezeichner dar.</p></td>
</tr>
</tbody>
</table>

 

## <a name="remarks"></a>Hinweise


Dieses Element ist nur für die speicherinterne Aufnahme verwendet.

## <a name="example"></a>Beispiel


Die folgenden Beispiele zeigen die Verwendung dieses Elements Collector des Systems und Ereignis Collector Definitionen.

Im erste Beispiel wird die Puffergröße auf 512 KB und begrenzt die Gesamtmenge des belegter Arbeitsspeicher auf 3 %. Im zweiten Beispiel wird die 64-Puffer von 128 KB.

``` syntax
<SystemCollector
  Id="WPRSystemCollector"
  Name="NT Kernel Logger"
  FileName="WPRKernel.etl">
  <BufferSize
    Value="512"/> 
  <Buffers
    Value="3"
    PercentageOfTotalMemory="true"/>
</SystemCollector>

<EventCollector
  Id="WPREventCollector"
  Name="WPR Event Collector"
  FileName="somefilename.etl">
  <BufferSize
    Value="128"/>
  <Buffers
    Value="64"/>
</EventCollector>
```

## <a name="related-topics"></a>Verwandte Themen


[Elemente](elements.md)

[Puffergröße](buffersize.md)

[SystemCollector](systemcollector.md)

[EventCollector](eventcollector.md)

[HeapEventCollector](heapeventcollector.md)

 

 







