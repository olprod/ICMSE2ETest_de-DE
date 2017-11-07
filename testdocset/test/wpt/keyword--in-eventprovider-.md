---
title: "Schlüsselwort (in EventProvider)"
description: "Schlüsselwort (in EventProvider)"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: f5b18ec2-8b85-40d6-ac69-91ccd7e7fad9
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 9c4241668d32151be21e2fe34a356e5ca4d8faae
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="keyword-in-eventprovider"></a>Schlüsselwort (in EventProvider)


Beschreibt das Schlüsselwort Event Tracing for Windows (ETW) für einen Anbieter im Benutzermodus.

## <a name="element-hierarchy"></a>Hierarchie-Elements


&lt;[WindowsPerformanceRecorder](windowsperformancerecorder.md)&gt;

     &lt;[Profiles](profiles.md)&gt;

          &lt;[EventProvider](eventprovider.md)&gt;

               &lt;[Keywords (in EventProvider)](keywords--in-eventprovider-.md)&gt;

                    &lt;**Keyword (in EventProvider)**&gt;

               &lt;[CaptureStateOnStart](capturestateonstart.md)&gt;

                    &lt;**Keyword (in EventProvider)**&gt;

               &lt;[CaptureStateOnSave](capturestateonsave.md)&gt;

                    &lt;**Keyword (in EventProvider)**&gt;

          &lt;[HeapEventProvider](heapeventprovider.md)&gt;

               &lt;[Keywords (in EventProvider)](keywords--in-eventprovider-.md)&gt;

                    &lt;**Keyword (in EventProvider)**&gt;

          &lt;[Profile](profile-wpr.md)&gt;

               &lt;[Collectors](collectors.md)&gt;

                    &lt;[EventCollectorId](eventcollectorid.md)&gt;

                         &lt;[EventProviders](eventproviders.md)&gt;

                              &lt;[EventProviderId](eventproviderid.md)&gt;

                                   &lt;[Keywords (in EventProvider)](keywords--in-eventprovider-.md)&gt;

                                        &lt;**Keyword (in EventProvider)**&gt;

                              &lt;[EventProvider](eventprovider.md)&gt;

                                   &lt;[Keywords (in EventProvider)](keywords--in-eventprovider-.md)&gt;

                                        &lt;**Keyword (in EventProvider)**&gt;

                                   &lt;[CaptureStateOnStart](capturestateonstart.md)&gt;

                                        &lt;**Keyword (in EventProvider)**&gt;

                                   &lt;[CaptureStateOnSave](capturestateonsave.md)&gt;

                                        &lt;**Keyword (in EventProvider)**&gt;

                    &lt;[HeapEventCollectorId](heapeventcollectorid.md)&gt;

                         &lt;[HeapEventProviders](heapeventproviders.md)&gt;

                              &lt;[HeapEventProviderId](heapeventproviderid.md)&gt;

                                   &lt;[Keywords (in EventProvider)](keywords--in-eventprovider-.md)&gt;

                                        &lt;**Keyword (in EventProvider)**&gt;

                              &lt;[HeapEventProvider](heapeventprovider.md)&gt;

                                   &lt;[Keywords (in EventProvider)](keywords--in-eventprovider-.md)&gt;

                                        &lt;**Keyword (in EventProvider)**&gt;

## <a name="syntax"></a>Syntax


``` syntax
<Keyword Value string
</Keyword>
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
<td><p>Zeichenfolge, die den Namen des Ereignisses ETW ist.</p></td>
<td><p>string</p></td>
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
<td><p>[Schlüsselwörter (in EventProvider)](keywords--in-eventprovider-.md)</p></td>
<td><p>Stellt eine Auflistung von Ereignis Anbieter Schlüsselwörtern.</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>Verwandte Themen


[Elemente](elements.md)

 

 







