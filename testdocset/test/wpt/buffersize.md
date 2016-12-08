---
title: "Puffergröße"
description: "Puffergröße"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 2ff38035-21a6-4081-b8e7-37b6fd3b6f4e
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 0dcbd5908105ed9064dac518bb61ca637aec2aef
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="buffersize"></a>Puffergröße


Beschreibt die Größe der einzelnen Puffer, in KB.

## <a name="element-hierarchy"></a>Hierarchie-Elements


&lt;[WindowsPerformanceRecorder](windowsperformancerecorder.md)&gt;

     &lt;[Profiles](profiles.md)&gt;

          &lt;[SystemCollector](systemcollector.md)&gt;

               &lt;**BufferSize**&gt;

          &lt;[EventCollector](eventcollector.md)&gt;

               &lt;**BufferSize**&gt;

          &lt;[HeapEventCollector](heapeventcollector.md)

               &lt;**BufferSize**&gt;

          &lt;[Profile](profile-wpr.md)&gt;

               &lt;[Collectors](collectors.md)&gt;

                    &lt;[SystemCollectorId](systemcollectorid.md)&gt;

                         &lt;**BufferSize**&gt;

                    &lt;[EventCollectorId](eventcollectorid.md)&gt;

                         &lt;**BufferSize**&gt;

                    &lt;[HeapEventCollectorId](heapeventcollectorid.md)&gt;

                         &lt;**BufferSize**&gt;

## <a name="syntax"></a>Syntax


``` syntax
<BufferSize Operation = "Set" | "Add" | “Remove”
            Value     = unsignedLong>
</BufferSize>
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
<td><p>Gibt an, ob Elemente festzulegen oder hinzugefügt werden soll.</p></td>
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
<td><p>Gibt die Größe der Puffer, in KB.</p></td>
<td><p>unsignedLong</p></td>
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
<td><p>[EventCollector](eventcollector.md)</p></td>
<td><p>Stellt eine Ereignissammlung.</p></td>
</tr>
<tr class="even">
<td><p>[EventCollectorId](eventcollectorid.md)</p></td>
<td><p>Stellt einen Ereignis Collector Bezeichner dar.</p></td>
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
<td><p>Stellt einen Bezeichner des System-Sammlung.</p></td>
</tr>
</tbody>
</table>

 

## <a name="remarks"></a>Hinweise


Dieses Element wird nur für speicherinterne Capture verwendet.

## <a name="example"></a>Beispiel


Die folgenden Codebeispiele veranschaulichen die Verwendung dieses Elements Collector des Systems und Ereignis-Sammlung Definitionen.

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

[Puffer](buffers.md)

[SystemCollector](systemcollector.md)

[EventCollector](eventcollector.md)

[HeapEventCollector](heapeventcollector.md)

 

 







