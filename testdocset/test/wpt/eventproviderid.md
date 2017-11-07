---
title: EventProviderId
description: EventProviderId
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: b97422a9-0fa1-484b-9b2e-8fd72dcbf494
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: fb49f763705ae9ee7f5533d8c6733a3a6ca19006
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="eventproviderid"></a>EventProviderId


Stellt einen Ereignis Anbieter Bezeichner für das Profil.

## <a name="element-hierarchy"></a>Hierarchie-Elements


&lt;[WindowsPerformanceRecorder](windowsperformancerecorder.md)&gt;

     &lt;[Profiles](profiles.md)&gt;

          &lt;[Profile](profile-wpr.md)&gt;

               &lt;[Collectors](collectors.md)&gt;

                    &lt;[EventCollectorId](eventcollectorid.md)&gt;

                         &lt;[EventProviders](eventproviders.md)&gt;

                               &lt;**EventProviderId**&gt;

## <a name="syntax"></a>Syntax


``` syntax
<EventProviderId Value = IdType>

  <!-- Child elements -->
  Keywords,
  CaptureStateOnStart,
  CaptureStateOnSave

</EventProviderId>
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
<td><p>Den Ereignisanbieter identifiziert eindeutig.</p></td>
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
<td><p>[Schlüsselwörter (in EventProvider)](keywords--in-eventprovider-.md)</p></td>
<td><p>Stellt eine Auflistung von Schlüsselwörtern.</p></td>
<td><p>Erforderlich, 1 oder mehr. Verwenden Sie <code>0x0</code> als ein Schlüsselwort, um alle Ereignisse.</p></td>
</tr>
<tr class="even">
<td><p>[CaptureStateOnStart](capturestateonstart.md)</p></td>
<td><p>Stellt eine Auflistung von Schlüsselwörtern, die am Anfang einer Aufzeichnung erfasst werden Ereignisse zu beschreiben.</p></td>
<td><p>Optional, wird 0 (null) oder 1.</p></td>
</tr>
<tr class="odd">
<td><p>[CaptureStateOnSave](capturestateonsave.md)</p></td>
<td><p>Stellt eine Auflistung von Schlüsselwörtern, die beschreiben Ereignisse aufgezeichnet werden, wenn eine Aufzeichnung gespeichert ist.</p></td>
<td><p>Optional, wird 0 (null) oder 1.</p></td>
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
<td><p>[EventProviders](eventproviders.md)</p></td>
<td><p>Stellt eine Auflistung von Anbieter und Ereignis-Anbieter-Bezeichner.</p></td>
</tr>
</tbody>
</table>

 

## <a name="example"></a>Beispiel


Verwenden Sie für verwaltete Szenarien die folgende Ereignis Anbieter Definition aus.

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

 

 







