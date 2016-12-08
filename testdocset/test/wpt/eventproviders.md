---
title: EventProviders
description: EventProviders
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: a486a6e7-56b9-4458-8b7d-23024b3b7762
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 6c54b12e55cb52f88dc69276205632153a6f0adf
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="eventproviders"></a>EventProviders


Stellt eine Auflistung der Ereignis-Provider-IDs und Anbieter.

## <a name="element-hierarchy"></a>Hierarchie-Elements


&lt;[WindowsPerformanceRecorder](windowsperformancerecorder.md)&gt;

     &lt;[Profiles](profiles.md)&gt;

          &lt;[Profile](profile-wpr.md)&gt;

               &lt;[Collectors](collectors.md)&gt;

                    &lt;[EventCollectorId](eventcollectorid.md)&gt;

                         &lt;**EventProviders**&gt;

## <a name="syntax"></a>Syntax


``` syntax
<EventProviders Operation = "Set" | "Add" | “Remove”>

  <!-- Child elements -->
  EventProviderId,
  EventProvider

</EventProviders>
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
<td><p>Gibt an, ob Anbieter festgelegt oder hinzugefügt werden soll.</p></td>
<td><p>Dieses Attribut kann einen der folgenden Werte aufweisen:</p>
<ul>
<li><p>Gruppe</p></li>
<li><p>Add</p></li>
<li><p>Entfernen</p></li>
</ul></td>
<td><p>Nein</p></td>
<td><p>Gruppe</p></td>
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
<td><p>[EventProviderId](eventproviderid.md)</p></td>
<td><p>Stellt einen Ereignis Anbieter-Bezeichner.</p></td>
<td><p>Optional, wird NULL oder mehr.</p></td>
</tr>
<tr class="even">
<td><p>[EventProvider](eventprovider.md)</p></td>
<td><p>Einen Ereignisanbieter darstellt.</p></td>
<td><p>Optional, wird NULL oder mehr.</p></td>
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
<td><p>[EventCollectorId](eventcollectorid.md)</p></td>
<td><p>Stellt einen Bezeichner der Ereignis-Sammlung.</p></td>
</tr>
</tbody>
</table>

 

## <a name="example"></a>Beispiel


Verwenden Sie für verwaltete Szenarien die folgende Ereignis Anbieter Definition:

``` syntax
<EventCollectorId Value ="WPAEventCollector">
  <EventProviders>
    <EventProviderId Value="EventProvider_DotNetProvider" />
    <EventProvider Name="Microsoft-Windows-WPA" Id="Microsoft-Windows-WPA" Stack="true">
    </EventProvider>
  </EventProviders>
</EventCollectorId>
```

## <a name="related-topics"></a>Verwandte Themen


[Elemente](elements.md)

 

 







