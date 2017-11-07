---
title: SystemCollector
description: SystemCollector
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: e7b9b910-9fe4-4dca-a61a-2599f67caf00
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 4b645f9ba7cd3a71347a20203b7005012fc240bf
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="systemcollector"></a>SystemCollector


Beschreibt die Konfigurationen, um die Event Tracing for Windows (ETW) Kernelmodus-Sitzung zu aktivieren.

## <a name="element-hierarchy"></a>Hierarchie-Elements


&lt;[WindowsPerformanceRecorder](windowsperformancerecorder.md)&gt;

     &lt;[Profiles](profiles.md)&gt;

          &lt;**SystemCollector**&gt;

## <a name="syntax"></a>Syntax


``` syntax
<SystemCollector Id       = IdType
                 Base     = string
                 Name     = "NT Kernel Logger" | "Circular Kernel Context Logger"
                 Realtime = boolean>

  <!-- Child elements -->
  BufferSize,
  Buffers,
  StackCaching

</SystemCollector>
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
<td><p><strong>ID</strong></p></td>
<td><p>Identifiziert eindeutig Collector des Systems.</p></td>
<td><p>Zeichenfolge, muss mindestens ein Zeichen sein und darf keine Doppelpunkte (:)) oder Leerzeichen enthalten.</p></td>
<td><p>Ja</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p><strong>Base</strong></p></td>
<td><p>Identifiziert die Basis Collector des Systems. Abgeleitete Kollektoren haben alle Attribute des Basis-Sammlung. Diese können überschrieben werden, indem sie in der abgeleiteten Collector explizit angeben.</p></td>
<td><p>string</p></td>
<td><p>Nein</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p><strong>Name</strong></p></td>
<td><p>Gibt den Namen der Collector des Systems.</p></td>
<td><p>Dieses Attribut kann einen der folgenden Werte aufweisen:</p>
<ul>
<li><p>NT-Kernel-Protokollierung</p></li>
<li><p>Kreisförmige Kernel-Kontext-Protokollierung</p></li>
</ul></td>
<td><p>Ja</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p><strong>Echtzeit</strong></p></td>
<td><p>Gibt an, ob der Sammlung in Echtzeit funktioniert.</p></td>
<td><p>boolean</p></td>
<td><p>Nein</p></td>
<td><p>falsch</p></td>
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
<th>Anforderung.</th>
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
<td><p>[Profile](profiles.md)</p></td>
<td><p>Stellt eine Auflistung von Kollektoren, Anbieter und Profilen.</p></td>
</tr>
</tbody>
</table>

 

## <a name="remarks"></a>Hinweise


Collector Systemdefinitionen sollte Ereignis Collector Definitionen vorausgehen.

## <a name="example"></a>Beispiel


Im folgenden Codebeispiel wird definiert einen Collector des Systems.

``` syntax
<SystemCollector
  Id="WPRSystemCollector”
  Name="NT Kernel Logger"
  FileName="WPRKernel.etl">
  <BufferSize Value="512"/>
  <Buffers Value="3" PercentageOfTotalMemory="true"/>
</SystemCollector>
```

## <a name="related-topics"></a>Verwandte Themen


[Elemente](elements.md)

 

 







