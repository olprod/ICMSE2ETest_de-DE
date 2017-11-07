---
title: Profil
description: Profil
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 92a5d494-cd6f-4a9b-942b-f1318ab48b00
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 75c0558f8dc3925f60c94848662f7956908b5925
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="profile"></a>Profil


Stellt eine Sammlung von Kategorien und Kollektoren Problem-Elementen.

## <a name="element-hierarchy"></a>Hierarchie-Elements


&lt;[WindowsPerformanceRecorder](windowsperformancerecorder.md)&gt;

     &lt;[Profiles](profiles.md)&gt;

          &lt;**Profile**&gt;

## <a name="syntax"></a>Syntax


``` syntax
<Profile Id          = IdType
         Name        = string
         Description = string
         Base        = string
         LoggingMode = "File" | "Memory"
         DetailLevel = "Verbose" | "Light"
         Strict      = boolean
         Internal    = boolean
         Default     = boolean>

  <!-- Child elements -->
  ProblemCategories,
  Collectors

</Profile>
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
<td><p>Das Profil identifiziert eindeutig.</p></td>
<td><p>Zeichenfolge, benötigen mindestens ein Zeichen und keine Doppelpunkte oder Leerzeichen enthalten.</p></td>
<td><p>Ja</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p><strong>Name</strong></p></td>
<td><p>Gibt den Namen des Profils an.</p></td>
<td><p>string</p></td>
<td><p>Ja</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p><strong>Beschreibung</strong></p></td>
<td><p>Gibt die Beschreibung des Profils an.</p></td>
<td><p>string</p></td>
<td><p>Ja</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p><strong>Base</strong></p></td>
<td><p>Gibt an, der Basis des Profils.</p></td>
<td><p>string</p></td>
<td><p>Nein</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p><strong>LoggingMode</strong></p></td>
<td><p>Gibt an, ob WPR im Arbeitsspeicher oder in eine sequenzielle Datei geschrieben.</p></td>
<td><p>Dieses Attribut kann einen der folgenden Werte aufweisen:</p>
<ul>
<li><p>File</p></li>
<li><p>Arbeitsspeicher</p></li>
</ul></td>
<td><p>Ja</p></td>
<td><p>File</p></td>
</tr>
<tr class="even">
<td><p><strong>DetailLevel</strong></p></td>
<td><p>Gibt an, ob eine Profildefinition für Timing Tracing verwendet wird (&quot;Licht&quot;) oder Analysis-Protokollierung (&quot;Verbose&quot;).</p></td>
<td><p>Dieses Attribut kann einen der folgenden Werte aufweisen:</p>
<ul>
<li><p>Ausführlich</p></li>
<li><p>Dünn</p></li>
</ul></td>
<td><p>Ja</p></td>
<td><p>Ausführlich</p></td>
</tr>
<tr class="odd">
<td><p><strong>Immer</strong></p></td>
<td><p>Gibt an, ob der Ausfall einen Anbieter oder eine Sammlung bewirkt, die Start-Vorgang fehlschlägt dass. Wenn dieses Attribut festgelegt ist, dass &quot;false&quot;, der Startvorgang erfolgreich ist, selbst wenn einige Kollektoren oder Anbieter fehl. Zum Fortsetzen des Vorgangs müssen mindestens eine Collector und einen Anbieter Erfolg haben. Wenn dieses Attribut festgelegt ist, dass &quot;true&quot;, Informationen zu Anbietern oder Kollektoren konnte nicht gestartet werden, die als Warnungen, anstelle von Fehlern bereitgestellt wird.</p></td>
<td><p>boolean</p></td>
<td><p>Nein</p></td>
<td><p>falsch</p></td>
</tr>
<tr class="even">
<td><p><strong>Interne</strong></p></td>
<td><p>Gibt an, ob das Profil intern ist.</p></td>
<td><p>boolean</p></td>
<td><p>Nein</p></td>
<td><p>falsch</p></td>
</tr>
<tr class="odd">
<td><p><strong>Standard</strong></p></td>
<td><p>Gibt an, ob die Profile ein Standardprofil ist.</p></td>
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
<td><p>[ProblemCategories](problemcategories.md)</p></td>
<td><p>Stellt eine Auflistung von Problemkategorien.</p></td>
<td><p>Erforderlich, genau 1.</p></td>
</tr>
<tr class="even">
<td><p>[Kollektoren](collectors.md)</p></td>
<td><p>Stellt eine Auflistung von Kollektoren für das Profil.</p></td>
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
<td><p>[Profile](profiles.md)</p></td>
<td><p>Stellt eine Auflistung von Kollektoren, Anbieter und Profilen.</p></td>
</tr>
</tbody>
</table>

 

## <a name="remarks"></a>Hinweise


Jede Datei .wprp enthält in der Regel mindestens zwei Profildefinitionen: eine für die beiden Modi Protokollierung. Die Ausnahme ist, dass ein-/ausschalten Übergang, Profile nur sich anmelden, an der Datei, dass die Datei .wprp für diese Profile nur ein Profildefinition enthalten kann. Jede Datei .wprp kann maximal vier Profile enthalten: einen für jede Kombination von Modus und Detail Protokollierungsstufe. Alle Profile in einer einzelnen .wprp-Datei müssen den gleichen Wert für das **Name** -Attribut aufweisen.

Erstellen Sie den Wert des **Id** -Attributs durch die Kombination der Werte der Attribute **Name**, **DetailLevel**und **LoggingMode** , getrennt durch Punkte, wie im folgenden Beispiel dargestellt.

Abgeleitete Profile haben alle Attribute des Profils Basis standardmäßig. Diese können überschrieben werden, indem sie in das abgeleitete Profil explizit angeben. Weitere Informationen finden Sie unter [Vererbung](inheritance.md).

## <a name="example"></a>Beispiel


Das folgende Codebeispiel zeigt eine Profildefinition.

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
    <EventCollectorId
      Value="WPREventCollector">
      <EventProviders>
        <EventProviderId
          Value="Win32K-provider"/>
        <EventProviderId
          Value="Search-Core-provider"/>
      </EventProviders>
    </EventCollectorId>
  </Collectors>
</Profile>
```

Kollektoren und Anbieter können auch an, in der Profildefinition definiert werden.

## <a name="related-topics"></a>Verwandte Themen


[Elemente](elements.md)

 

 







