---
title: HeapEventCollectorId
description: HeapEventCollectorId
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: dcbc758e-bf3e-472b-8d7a-cfd8d357f193
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 68a0eaff0d37cc2dfc83931c8e67996199cfb289
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="heapeventcollectorid"></a>HeapEventCollectorId


Stellt einen Bezeichner für eine Sammlung von Ereignissen für das Profil Heap dar.

## <a name="element-hierarchy"></a>Hierarchie-Elements


&lt;[WindowsPerformanceRecorder](windowsperformancerecorder.md)&gt;

     &lt;[Profiles](profiles.md)&gt;

          &lt;[Profile](profile-wpr.md)&gt;

               &lt;[Collectors](collectors.md)&gt;

                    &lt;**HeapEventCollectorId**&gt;

## <a name="syntax"></a>Syntax


``` syntax
<HeapEventCollectorId Value = IdType>

  <!-- Child elements -->
  BufferSize,
  Buffers,
  StackCaching,
  HeapEventProviders

</HeapEventCollectorId>
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
<td><p>Der Heap Ereignissammlung identifiziert eindeutig.</p></td>
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
<td><p>Entweder die Anzahl der Puffer Starten einer Sitzung oder den Prozentsatz des Gesamtspeichers für die Sitzung, abhängig vom Wert des Attributs <strong>PercentageOfTotalMemory</strong> zuzuweisende zuzuweisende beschreibt.</p></td>
<td><p>Erforderlich, genau 1.</p></td>
</tr>
<tr class="odd">
<td><p>[StackCaching](stackcaching.md)</p></td>
<td><p>Zwischenspeichern der Attribute der Kollektoren Stack beschreibt.</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>[HeapEventProviders](heapeventproviders.md)</p></td>
<td><p>Stellt eine Auflistung der Heap Ereignis Anbieter-IDs und Heap Anbieter.</p></td>
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
<td><p>[Profil](profile-wpr.md)</p></td>
<td><p>Stellt eine Auflistung von Problemkategorien und Kollektoren.</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>Verwandte Themen


[Elemente](elements.md)

 

 







