---
title: EventCollectorId
description: EventCollectorId
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: a5a87699-9bd5-4ae9-9707-773ece45b4fc
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: e4f313ee8016320039dccf0e3c6f3cfafc4f15ca
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="eventcollectorid"></a>EventCollectorId


Stellt einen Ereignis Collector Bezeichner dar.

## <a name="element-hierarchy"></a>Hierarchie-Elements


&lt;[WindowsPerformanceRecorder](windowsperformancerecorder.md)&gt;

     &lt;[Profiles](profiles.md)&gt;

          &lt;[Profile](profile-wpr.md)&gt;

               &lt;[Collectors](collectors.md)&gt;

                    &lt;**EventCollectorId**&gt;

## <a name="syntax"></a>Syntax


``` syntax
<EventCollectorId Value = IdType>

  <!-- Child elements -->
  BufferSize,
  Buffers,
  StackCaching,
  EventProviders

</EventCollectorId>
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
<td><p>Der Ereignissammlung identifiziert eindeutig.</p></td>
<td><p>Zeichenfolge, muss mindestens ein Zeichen sein und darf keine Doppelpunkte (:)) oder Leerzeichen enthalten.</p></td>
<td><p>Ja</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>

 

### <a name="child-elements"></a>Untergeordnete Elemente

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>Element</th>
<th>Beschreibung</th>
<th>Anforderung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>[Puffergröße](buffersize.md)</p></td>
<td><p>Beschreibt die Größe der einzelnen Puffer, in KB.</p></td>
<td><p>Erforderlich, genau 1.</p></td>
</tr>
<tr class="even">
<td><p>[Puffer](buffers.md)</p></td>
<td><p>Beschreibt die Anzahl der Puffer zugeordnet werden, wenn Sie eine Sitzung starten.</p></td>
<td><p>Erforderlich, genau 1.</p></td>
</tr>
<tr class="odd">
<td><p>[StackCaching](stackcaching.md)</p></td>
<td><p>Zwischenspeichern der Attribute der Kollektoren Stack beschreibt.</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>[EventProviders](eventproviders.md)</p></td>
<td><p>Stellt eine Auflistung von Ereignis Anbieter-IDs und Anbieter.</p></td>
<td><p>Erforderlich, genau 1.</p></td>
</tr>
</tbody>
</table>

 

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
<td><p>[Kollektoren](collectors.md)</p></td>
<td><p>Stellt eine Auflistung von System Collector-IDs, Collector Bezeichner und optional Heap Collector Bezeichner.</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>Verwandte Themen


[Elemente](elements.md)

 

 







