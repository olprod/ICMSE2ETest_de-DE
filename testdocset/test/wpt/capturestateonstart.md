---
title: CaptureStateOnStart
description: CaptureStateOnStart
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: c29100b6-2eba-4100-8d15-a80a6766beed
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: d645c74501546d4d256e592420e67cb175bdba9f
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="capturestateonstart"></a>CaptureStateOnStart


Stellt eine Auflistung von Schlüsselwörtern, die am Anfang einer Aufzeichnung erfasst werden Ereignisse zu beschreiben. Die Bibliothek fordert den Anbieter die Zustandsinformationen melden, wenn der Anbieter aktiviert ist. Wenn das **Vorgang** -Attribut angegeben ist, können die **Schlüsselwort** -Elemente festzulegen oder zur Auflistung hinzugefügt.

## <a name="element-hierarchy"></a>Hierarchie-Elements


&lt;[WindowsPerformanceRecorder](windowsperformancerecorder.md)&gt;

     &lt;[Profiles](profiles.md)&gt;

          &lt;[EventProvider](eventprovider.md)&gt;

               &lt;**CaptureStateOnStart**&gt;

          &lt;[Profile](profile-wpr.md)&gt;

               &lt;[Collectors](collectors.md)&gt;

                    &lt;[EventCollectorId](eventcollectorid.md)&gt;

                         &lt;[EventProviderId](eventproviderid.md)&gt;

                              &lt;**CaptureStartOnStart**&gt;

                         &lt;[EventProvider](eventprovider.md)&gt;

                              &lt;**CaptureStateOnStart**&gt;

## <a name="syntax"></a>Syntax


``` syntax
<CaptureStateOnStart Operation = "Set" | "Add"> | “Remove”

  <!-- Child elements -->
  Keyword

</CaptureStateOnStart>
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
<EventProvider Id="sample-provider" Name="SampleProvider" NonPagedMemory="true" Level="5">
  <Keywords>
    <Keyword Value="0x98"/> <!-- Provider is enabled with these keywords throughout tracing session -->
  </Keywords>
  <CaptureStateOnStart>
    <Keyword Value="0xff4"/> <!-- Provider is  enabled with these keywords when tracing is started. -->
  </CaptureStateOnStart>
  <CaptureStateOnSave>
    <Keyword Value="0x118"/> <!-- Provider is enabled with these keywords when tracing is saved. -->
  </CaptureStateOnSave>
</EventProvider>
```

## <a name="related-topics"></a>Verwandte Themen


[Elemente](elements.md)

[CustomKeyword](customkeyword.md)

[CaptureStateOnSave](capturestateonsave.md)

 

 







