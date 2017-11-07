---
title: CaptureStateOnSave
description: CaptureStateOnSave
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: d672f309-e038-4c69-9288-fbf8e251dfc5
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 092b28a4afec0a23e870ec54170a653650d8b04b
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="capturestateonsave"></a>CaptureStateOnSave


Stellt eine Auflistung von Schlüsselwörtern, die beschreiben Ereignisse aufgezeichnet werden, wenn eine Verfolgung gespeichert wird. Die Bibliothek fordert den Anbieter die Zustandsinformationen melden, wenn der Sammlung gespeichert wird. Wenn das **Vorgang** -Attribut angegeben ist, können die **Schlüsselwort** -Elemente festzulegen oder zur Auflistung hinzugefügt.

## <a name="element-hierarchy"></a>Hierarchie-Elements


&lt;[WindowsPerformanceRecorder](windowsperformancerecorder.md)&gt;

     &lt;[Profiles](profiles.md)&gt;

          &lt;[EventProvider](eventprovider.md)&gt;

               &lt;**CaptureStateOnSave**&gt;

          &lt;[Profile](profile-wpr.md)&gt;

               &lt;[Collectors](collectors.md)&gt;

                    &lt;[EventCollectorId](eventcollectorid.md)&gt;

                         &lt;[EventProviderId](eventproviderid.md)&gt;

                              &lt;**CaptureStateOnSave**&gt;

                         &lt;[EventProvider](eventprovider.md)&gt;

                              &lt;**CaptureStateOnSave**&gt;

## <a name="syntax"></a>Syntax


``` syntax
<CaptureStateOnSave Operation = "Set" | "Add"> | “Remove”

  <!-- Child elements -->
  Keyword

</CaptureStateOnSave>
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
<td><p>Gibt an, ob die Schlüsselwörter festgelegt oder hinzugefügt werden soll.</p></td>
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
<td><p>[Schlüsselwort (in EventProvider)](keyword--in-eventprovider-.md)</p></td>
<td><p>Beschreibt das Schlüsselwort Event Tracing for Windows (ETW) für einen Anbieter im Benutzermodus.</p></td>
<td><p>Erforderlich, eine oder mehrere.</p></td>
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
<td><p>[EventProvider](eventprovider.md)</p></td>
<td><p>Stellt einen-Anbieter für das Profil.</p></td>
</tr>
<tr class="even">
<td><p>[EventProviderId](eventproviderid.md)</p></td>
<td><p>Stellt einen Ereignis Anbieter-Bezeichner.</p></td>
</tr>
</tbody>
</table>

 

## <a name="example"></a>Beispiel


Im folgenden Codebeispiel wird veranschaulicht die Verwendung dieses Elements.

``` syntax
<EventProvider Id="EventProvider_DWMWin32k_CaptureState" Name="e7ef96be-969f-414f-97d7-3ddb7b558ccc" NonPagedMemory="true" CaptureStateOnly="true" > 
  <!-- CaptureStateOnly="true" means provider is not enabled throughout the tracing session. -->
  <CaptureStateOnSave>
    <Keyword Value="0x80000"/> <!-- Provider is enabled with these keywords when tracing is saved. -->
  </CaptureStateOnSave>
</EventProvider>
```

## <a name="related-topics"></a>Verwandte Themen


[Elemente](elements.md)

[CustomKeyword](customkeyword.md)

[CaptureStateOnStart](capturestateonstart.md)

 

 







