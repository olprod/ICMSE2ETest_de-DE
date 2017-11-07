---
title: EventProvider
description: EventProvider
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: bf7e4e86-e837-41f8-847f-42fc12c5a98c
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 17140550564b359627bff139880c85d621c36590
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="eventprovider"></a>EventProvider


Den Event Tracing for Windows (ETW) im Benutzermodus Anbieter konfiguriert.

## <a name="element-hierarchy"></a>Hierarchie-Elements


&lt;[WindowsPerformanceRecorder](windowsperformancerecorder.md)&gt;

     &lt;[Profiles](profiles.md)&gt;

          &lt;**EventProvider**&gt;

          &lt;[Profile](profile-wpr.md)&gt;

               &lt;[Collectors](collectors.md)&gt;

                    &lt;[EventCollectorId](eventcollectorid.md)&gt;

                         &lt;[EventProviders](eventproviders.md)&gt;

                              &lt;**EventProvider**&gt;

## <a name="syntax"></a>Syntax


``` syntax
<EventProvider Id               = IdType
               Name             = string
               Base             = string
               NonPageMemory    = boolean
               Stack            = boolean
               SID              = boolean
               TSID             = boolean
               Level            = unsigendByte
               CaptureStateOnly = boolean>

  <!-- Child elements -->
  Keywords,
  CaptureStateOnStart,
  CaptureStateOnSave

</EventProvider>
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
<td><p>Den Ereignisanbieter identifiziert eindeutig.</p></td>
<td><p>Zeichenfolge, muss mindestens ein Zeichen sein und darf keine Doppelpunkte (:)) oder Leerzeichen enthalten.</p></td>
<td><p>Ja</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p><strong>Name</strong></p></td>
<td><p>Gibt den Namen des Ereignisanbieters an.</p></td>
<td><p>Dieses Attribut kann einen der folgenden Werte aufweisen:</p>
<ul>
<li><p>Eine registriert Crimson-Anbieter, z. B. &quot;Microsoft-Windows-Suche-Core&quot;.</p></li>
<li><p>Ein Anbieter GUID, beispielsweise &quot;49c2c27c-fe2d-40bf-8c4e-c3fb518037e7&quot;.</p></li>
<li><p>Der Name eines legacy-Anbieters, z. B. &quot;IE6&quot;.</p></li>
<li><p>Ein besonderer Namen, z. B. &quot;PerfTrack&quot; oder &quot;DotNetProvider&quot;.</p></li>
</ul></td>
<td><p>Ja</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p><strong>ProcessExeFilter</strong></p></td>
<td><p>Filtert ein Ereignis basierend auf den angegebenen Vorgang .exe-Namen.</p></td>
<td><p>Dies ist ein optionales Attribut, die, das Sie die <strong>EventProvider-ID</strong> im WPR Profil hinzufügen. Beispiel:</p>
<ul>
<li><p>&quot;ProcessExeFilter =&quot;wpa.exe&quot;</p></li>
</ul>
<div class="alert">
<strong>Hinweis</strong>  
<p>WPR übergibt im Wesentlichen auf dem .exe-Namen in die [EVENT_FILTER_DESCRIPTOR](https://msdn.microsoft.com/library/windows/desktop/aa363758.aspx) -Struktur.</p>
</div>
<div>
 
</div></td>
<td><p>Nein</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p><strong>Base</strong></p></td>
<td><p>Gibt die Basis für den Anbieter an.</p></td>
<td><p>string</p></td>
<td><p>Nein</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p><strong>NonPagedMemory</strong></p></td>
<td><p>Gibt an, ob nicht ausgelagerten Speicher verwendet werden.</p></td>
<td><p>boolean</p></td>
<td><p>Nein</p></td>
<td><p>falsch</p></td>
</tr>
<tr class="even">
<td><p><strong>Stapel</strong></p></td>
<td><p>Gibt an, ob der Anbieter Stapel erfassen soll.</p></td>
<td><p>boolean</p></td>
<td><p>Nein</p></td>
<td><p>falsch</p></td>
</tr>
<tr class="odd">
<td><p><strong>SID</strong></p></td>
<td><p>Gibt an, ob die Sicherheits-ID (SID) des Benutzers an die erweiterten Daten der protokollierten Ereignisse.</p></td>
<td><p>boolean</p></td>
<td><p>Nein</p></td>
<td><p>falsch</p></td>
</tr>
<tr class="even">
<td><p><strong>TSID</strong></p></td>
<td><p>Gibt an, ob der Bezeichner des Terminaldienste-Sitzung in den erweiterten Daten der protokollierten Ereignisse enthalten ist.</p></td>
<td><p>boolean</p></td>
<td><p>Nein</p></td>
<td><p>falsch</p></td>
</tr>
<tr class="odd">
<td><p><strong>Level</strong></p></td>
<td><p>Gibt den Wert Ebenen.</p></td>
<td><p>unsignedByte</p></td>
<td><p>Nein</p></td>
<td><p>0 (null), die als 0xFFFFFFFFFFFFFFFF ETW behandelt.</p></td>
</tr>
<tr class="even">
<td><p><strong>CaptureStateOnly</strong></p></td>
<td><p>Gibt an, ob ein Anbieter nur zu Beginn aktiviert ist, oder Speichern einer Tracing-Sitzung.</p></td>
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
<td><p>[Schlüsselwörter (in EventProvider)](keywords--in-eventprovider-.md)</p></td>
<td><p>Stellt eine Auflistung von Elementen [Schlüsselwort (in EventProvider)](keyword--in-eventprovider-.md) .</p></td>
<td><p>Erforderlich, 1 oder mehr.</p></td>
</tr>
<tr class="even">
<td><p>[CaptureStateOnStart](capturestateonstart.md)</p></td>
<td><p>Stellt eine Auflistung von [Keyword (in EventProvider)](keyword--in-eventprovider-.md) -Elemente für Ereignisse, das am Anfang einer Ablaufverfolgung aufgezeichnet werden.</p></td>
<td><p>Optional, wird 0 (null) oder 1.</p></td>
</tr>
<tr class="odd">
<td><p>[CaptureStateOnSave](capturestateonsave.md)</p></td>
<td><p>Stellt eine Auflistung von [Keyword (in EventProvider)](keyword--in-eventprovider-.md) -Elemente, um Ereignisse aufgezeichnet werden, wenn eine Verfolgung gespeichert wird.</p></td>
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
<td><p>Stellt eine Auflistung von <strong>EventProvider</strong> Elementen.</p></td>
</tr>
<tr class="even">
<td><p>[Profile](profiles.md)</p></td>
<td><p>Stellt eine Auflistung von Kollektoren, Anbieter und Profilen.</p></td>
</tr>
</tbody>
</table>

 

## <a name="remarks"></a>Hinweise


Anbieter Definition Reihenfolge ist von Bedeutung. Definitionen müssen in der folgenden Reihenfolge in der Datei .wprp werden angezeigt:

1.  Kollektoren

2.  Systemanbieter

3.  Ereignis-Anbieter

Optionale inneren XML-Tags angeben, welche Schlüsselwörtern zu aktivieren. Im Gegensatz zu für System-Anbieter, es sind keine textbezogene Konstanten definiert Anbieter, damit Zeichenfolgen im Hexadezimal-Format verwendet werden müssen. Die Syntax ist jedoch die gleichen wie für Systemanbieter. Wenn keine Stichwörter angegeben sind, wird der Standardwert 0 (null) (die vom ETW als die Zeichenfolge 0xFFFFFFFFFFFFFFFF behandelt wird).

Abgeleitete Anbieter haben alle Attribute des Anbieters Basis standardmäßig. Sie können überschrieben werden, indem sie in den abgeleiteten Anbieter explizit angeben. Weitere Informationen finden Sie unter [Vererbung](inheritance.md).

## <a name="example"></a>Beispiel


Im folgende Beispiel definiert zwei Anbieter.

``` syntax
<EventProvider
  Id="Win32K-provider"
  Name="Microsoft-Windows-Win32K"
  NonPagedMemory="true"
  Stack="true"> 
  <Keywords>
    <Keyword
      Value="0x240000"/>
  </Keywords>
</EventProvider>

<EventProvider
  Id="Search-Core-provider"
  Name="Microsoft-Windows-Search-Core"/>
```

Die folgenden Codebeispiele definieren-Zustand der Erfassung von Anbietern.

``` syntax
<EventProvider Id="sample-provider" Name="SampleProvider" NonPagedMemory="true" Level="5">
  <Keywords>
    <Keyword Value="0x98"/> <!-- Provider is enabled with these keywords throughout the tracing session. -->
  </Keywords>
  <CaptureStateOnStart>
    <Keyword Value="0xff4"/> <!-- Provider is enabled with these keywords when tracing is started. -->
  </CaptureStateOnStart>
  <CaptureStateOnSave>
    <Keyword Value="0x118"/> <!-- Provider is enabled with these keywords when tracing is saved. -->
  </CaptureStateOnSave>
</EventProvider>

<EventProvider Id="EventProvider_DWMWin32k_CaptureState" Name="e7ef96be-969f-414f-97d7-3ddb7b558ccc" NonPagedMemory="true" CaptureStateOnly="true" > 
  <!-- CaptureStateOnly="true" means that provider is not enabled throughout the tracing session. -->
  <CaptureStateOnSave>
    <Keyword Value="0x80000"/> <!-- Provider is enabled with these keywords when tracing is saved. -->
  </CaptureStateOnSave>
</EventProvider>
```

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

 

 







