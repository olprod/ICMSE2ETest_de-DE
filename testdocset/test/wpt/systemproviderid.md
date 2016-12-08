---
title: SystemProviderId
description: SystemProviderId
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: f5ac9900-e43b-480b-9be7-5f5f726b1635
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: d27cbb2f9f41c807e0311844955060f153a135ef
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="systemproviderid"></a>SystemProviderId


Den Systemanbieter identifiziert eindeutig.

## <a name="element-hierarchy"></a>Hierarchie-Elements


&lt;[WindowsPerformanceRecorder](windowsperformancerecorder.md)&gt;

     &lt;[Profiles](profiles.md)&gt;

          &lt;[Profile](profile-wpr.md)&gt;

               &lt;[Collectors](collectors.md)&gt;

                    &lt;**SystemProviderId**&gt;

## <a name="syntax"></a>Syntax


``` syntax
<SystemProviderId Value = IdType>

  <!-- Child elements -->
  Keywords,
  Stacks,
  PoolTags

</SystemProviderId>
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
<td><p>Den Systemanbieter identifiziert eindeutig.</p></td>
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
<td><p>[Schlüsselwörter (in "Systemprovider")](keywords--in-systemprovider-.md)</p></td>
<td><p>Stellt eine Auflistung von Schlüsselwörtern für System-Anbieter.</p></td>
<td><p>Erforderlich, genau 1.</p></td>
</tr>
<tr class="even">
<td><p>[Stapel](stacks.md)</p></td>
<td><p>Stellt eine Auflistung von Stapeln.</p></td>
<td><p>Erforderlich, genau 1.</p></td>
</tr>
<tr class="odd">
<td><p>[PoolTags](pooltags.md)</p></td>
<td><p>Stellt eine Auflistung von Pooltags.</p></td>
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

 

## <a name="remarks"></a>Hinweise


Weitere Informationen zum Erstellen von Systemdefinitionen Anbieter finden Sie unter [2. System- und Ereignis Anbieter Definitionen](2-system-and-event-provider-definitions.md) und [3. Definitionen Profile](3-profile-definitions.md).

## <a name="example"></a>Beispiel


Im folgenden Codebeispiel wird der Abschnitt der Profildefinition eines, das dieses Element enthält.

``` syntax
<Profile
  Id="Example.Light.File"
  Name="Example"
  DetailLevel="Light"
  LoggingMode="File"
  Description="Example profile">
  <ProblemCategories> 
    <ProblemCategory
      Value="First Level Triage"/>
  </ProblemCategories> 
  <Collectors>
    <SystemCollectorId
      Value="WPRSystemCollector">
      <SystemProviderId
        Value="system-provider"/>
    </SystemCollectorId>
…
  </Collectors>
</Profile>
```

## <a name="related-topics"></a>Verwandte Themen


[Elemente](elements.md)

 

 







