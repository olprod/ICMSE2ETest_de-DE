---
title: HeapEventCollector
description: HeapEventCollector
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: e8f6e4d9-b037-49ca-b816-cc7757b98b3d
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: a5fd3621f8e821bd0903f69c4cd063dc4a426859
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="heapeventcollector"></a>HeapEventCollector


Stellt eine Sammlung für Heap Ereignisse.

## <a name="element-hierarchy"></a>Hierarchie-Elements


&lt;[WindowsPerformanceRecorder](windowsperformancerecorder.md)&gt;

     &lt;[Profiles](profiles.md)&gt;

          &lt;**HeapEventCollector**&gt;

## <a name="syntax"></a>Syntax


``` syntax
<HeapEventCollector Id       = IdType
                    Base     = string
                    Name     = string
                    FileName = string
                    Realtime = boolean
                    Secure   = boolean>

  <!-- Child elements -->
  BufferSize,
  Buffers,
  StackCaching

</HeapEventCollector>
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
<td><p>Der Heap Ereignissammlung identifiziert eindeutig.</p></td>
<td><p>Zeichenfolge, muss mindestens ein Zeichen sein und darf keine Doppelpunkte (:)) oder Leerzeichen enthalten.</p></td>
<td><p>Ja</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p><strong>Base</strong></p></td>
<td><p>Gibt die Basis der Sammlung an.</p></td>
<td><p>string</p></td>
<td><p>Nein</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p><strong>Name</strong></p></td>
<td><p>Gibt den Namen des der Ereignissammlung Heap an.</p></td>
<td><p>string</p></td>
<td><p>Ja</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p><strong>FileName</strong></p></td>
<td><p>Gibt den Namen der Datei an die Ereignisse geschrieben werden sollen.</p></td>
<td><p>string</p></td>
<td><p>Ja</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p><strong>Echtzeit</strong></p></td>
<td><p>Gibt an, ob der Ereignissammlung in Echtzeit ausgeführt wird.</p></td>
<td><p>boolean</p></td>
<td><p>Nein</p></td>
<td><p>falsch</p></td>
</tr>
<tr class="even">
<td><p><strong>Secure</strong></p></td>
<td><p>Wenn auf festgelegt &quot;true&quot;, gibt an, dass nur Benutzer mit Administratorrechten und ordnungsgemäßen Zugriffsrechten die Sitzung steuern können. Wenn auf festgelegt &quot;false&quot;, gibt an, dass alle Benutzer die Sitzung steuern können.</p></td>
<td><p>boolean</p></td>
<td><p>Nein</p></td>
<td><p>wahr</p></td>
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


Sammeln von Ereignissen abgeleiteten haben die Attribute von der Basis Collector standardmäßig. Diese können überschrieben werden, indem sie in der abgeleiteten Collector explizit angeben. Weitere Informationen finden Sie unter [Vererbung](inheritance.md).

## <a name="related-topics"></a>Verwandte Themen


[Elemente](elements.md)

[Vererbung (engl.)](inheritance.md)

 

 







