---
title: WindowsPerformanceRecorder
description: WindowsPerformanceRecorder
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: e17ce0a4-9621-4611-a781-2750fba3b0cd
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 430c6d9f58d1e3775c4b771461a303edc0c95d28
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="windowsperformancerecorder"></a>WindowsPerformanceRecorder


Dieses Element ist das Stammelement des Schemas. Es stellt Metadaten für die Erstellung von Benutzerprofilen.

## <a name="element-hierarchy"></a>Hierarchie-Elements


&lt;**WindowsPerformanceRecorder**&gt;

## <a name="syntax"></a>Syntax


``` syntax
<WindowsPerformanceRecorder Version   = float
                            Author    = string
                            Team      = string
                            Copyright = string
                            Company   = string
                            Comments  = string
                            Tag       = string>

  <!-- Child elements -->
  Profiles,
  TraceMergeProperties,
  OnOffTransitionConfigurations

</WindowsPerformanceRecorder>
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
<td><p><strong>Version</strong></p></td>
<td><p>Gibt die Version des Profils an.</p></td>
<td><p>float</p></td>
<td><p>Ja</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p><strong>Author</strong></p></td>
<td><p>Gibt den Autor des Profils an.</p></td>
<td><p>string</p></td>
<td><p>Ja</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p><strong>Team</strong></p></td>
<td><p>Gibt an, das Team, das das Profil erstellt.</p></td>
<td><p>string</p></td>
<td><p>Nein</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p><strong>Copyright</strong></p></td>
<td><p>Copyright-Informationen darstellt.</p></td>
<td><p>string</p></td>
<td><p>Nein</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p><strong>Firma</strong></p></td>
<td><p>Gibt an, das Unternehmen, die das Profil erstellt.</p></td>
<td><p>string</p></td>
<td><p>Nein</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p><strong>Comments</strong></p></td>
<td><p>Optionale beschreibende Kommentare für die Profile darstellt.</p></td>
<td><p>string</p></td>
<td><p>Nein</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p><strong>Tag</strong></p></td>
<td><p>Stellt einen Eigenschaftswert aus, der verwendet werden kann, um verschiedenen Profilen zu unterscheiden.</p></td>
<td><p>string</p></td>
<td><p>Nein</p></td>
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
<td><p>[Profile](profiles.md)</p></td>
<td><p>Stellt eine Auflistung von Kollektoren, Anbieter und Profilen.</p></td>
<td><p>Erforderlich, genau 1.</p></td>
</tr>
<tr class="even">
<td><p>[TraceMergeProperties](tracemergeproperties.md)</p></td>
<td><p>Stellt eine Auflistung von Trace Merge Aktionsroutine dar.</p></td>
<td><p>Optional, wird 0 (null) oder 1.</p></td>
</tr>
<tr class="odd">
<td><p>[OnOffTransitionConfigurations](onofftransitionconfigurations.md)</p></td>
<td><p>Stellt eine Auflistung von ein-/ausschalten Konfigurationen für den Umstieg von dar.</p></td>
<td><p>Optional, wird 0 (null) oder 1.</p></td>
</tr>
</tbody>
</table>

 

### <a name="parent-elements"></a>Übergeordnete Elemente

Keine

## <a name="related-topics"></a>Verwandte Themen


[Elemente](elements.md)

 

 







