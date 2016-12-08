---
title: EventCollector
description: EventCollector
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: d7c94d21-b834-44f2-bad0-f0af6555bb5d
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 2dbf76962e83b920ebb75aa070b588bfb55e9c14
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="eventcollector"></a>EventCollector


Stellt eine Ereignissammlung für das Profil.

## <a name="element-hierarchy"></a>Hierarchie-Elements


&lt;[WindowsPerformanceRecorder](windowsperformancerecorder.md)&gt;

     &lt;[Profiles](profiles.md)&gt;

          &lt;**EventCollector**&gt;

## <a name="syntax"></a>Syntax


``` syntax
<EventCollector Id             = IdType
                Base           = string
                Name           = string
                FileName       = string
                Realtime       = boolean
                Private        = boolean
                ProcessPrivate = boolean
                Secure         = boolean>

  <!-- Child elements -->
  BufferSize,
  Buffers,
  StackCaching

</EventCollector>
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
<td><p>Der Ereignissammlung identifiziert eindeutig.</p></td>
<td><p>Zeichenfolge, muss mindestens ein Zeichen sein und darf keine Doppelpunkte (:)) oder Leerzeichen enthalten.</p></td>
<td><p>Ja</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p><strong>Base</strong></p></td>
<td><p>Die Basis der Ereignissammlung identifiziert.</p></td>
<td><p>string</p></td>
<td><p>Nein</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p><strong>Name</strong></p></td>
<td><p>Gibt den Namen der ETW-Sitzung.</p></td>
<td><p>string</p></td>
<td><p>Ja</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p><strong>FileName</strong></p></td>
<td><p>Gibt die Datei an, die zum Protokollieren von Ereignissen an.</p></td>
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
<td><p><strong>Privat</strong></p></td>
<td><p>Wenn auf festgelegt &quot;true&quot;, gibt eine Benutzermodus-Sitzung, die in demselben Prozess wie der Ereignisanbieter ausgeführt wird. Wenn auf festgelegt &quot;false&quot;; gibt eine globale Benutzermodus-Sitzung an.</p></td>
<td><p>boolean</p></td>
<td><p>Nein</p></td>
<td><p>falsch</p></td>
</tr>
<tr class="odd">
<td><p><strong>ProcessPrivate</strong></p></td>
<td><p>Wenn auf festgelegt &quot;true&quot;, gibt eine Benutzermodus-Sitzung, die in demselben Prozess wie der Ereignisanbieter ausgeführt wird und nur durch den Prozess, die den Anbieter registriert kontrolliert werden sollten. Wenn auf festgelegt &quot;false&quot;, gibt eine globale Benutzermodus-Sitzung an. Verwenden Sie dieses Attribut in Verbindung mit dem <strong>privaten</strong> Attribut.</p></td>
<td><p>boolean</p></td>
<td><p>Nein</p></td>
<td><p>falsch</p></td>
</tr>
<tr class="even">
<td><p><strong>Secure</strong></p></td>
<td><p>Wenn auf festgelegt &quot;true&quot;, gibt an, dass nur Benutzer mit Administratorrechten und ordnungsgemäßen Zugriffsrechten die Sitzung steuern können. Wenn auf festgelegt &quot;false&quot;, gibt an, dass alle Benutzer die Sitzung steuern können.</p></td>
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
<td><p>Beschreibt die Anzahl der Puffer beim Starten einer Sitzung oder den Prozentsatz des Gesamtspeichers für die Sitzung, abhängig vom Wert des Attributs <strong>PercentageOfTotalMemory</strong> zuzuweisende zugeordnet werden.</p></td>
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


Ereignis-Sammlung Definitionen müssen Collector Systemdefinitionen vorangestellt werden.

Abgeleitete Kollektoren erben alle Attribute der Basis Collection, es sei denn, sie in den abgeleiteten Collector explizit angegeben sind. Weitere Informationen finden Sie unter [Vererbung](inheritance.md).

## <a name="example"></a>Beispiel


Im folgenden Codebeispiel wird definiert, einer Ereignissammlung mit 64 Puffern 128 KB.

``` syntax
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

 

 







