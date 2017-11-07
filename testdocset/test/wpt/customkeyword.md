---
title: CustomKeyword
description: CustomKeyword
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 776e6349-4d19-44a9-b49a-a2c73e218540
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: ea23c3bc18cf2fa4db08ec9b9797d95ad2cd5fee
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="customkeyword"></a>CustomKeyword


Stellt ein benutzerdefiniertes Schlüsselwort für das Profil.

## <a name="element-hierarchy"></a>Hierarchie-Elements


&lt;[WindowsPerformanceRecorder](windowsperformancerecorder.md)&gt;

     &lt;[Profiles](profiles.md)&gt;

          &lt;[SystemProvider](systemprovider.md)&gt;

               &lt;[Keywords (in SystemProvider)](keywords--in-systemprovider-.md)&gt;

                    &lt;**CustomKeyword**&gt;

          &lt;[Profile](profile-wpr.md)&gt;

               &lt;[Collectors](collectors.md)&gt;

                    &lt;[SystemCollectorId](systemcollectorid.md)&gt;

                         &lt;[SystemProvider](systemprovider.md)&gt;

                              &lt;[Keywords (in SystemProvider)](keywords--in-systemprovider-.md)&gt;

                                   &lt;**CustomKeyword**&gt;

## <a name="syntax"></a>Syntax


``` syntax
<CustomKeyword Value = SystemCustomKeywordAttributeType>
</CustomKeyword>
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
<td><p>Der Zeichenfolgenname hexadezimal-Formular des benutzerdefinierten Ereignisses.</p></td>
<td><p>Zeichenfolge mit dem folgenden Muster erstellt: 0 x [a-Anlagen-F0-9] {1,8}.</p></td>
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
<td><p>[Schlüsselwörter (in "Systemprovider")](keywords--in-systemprovider-.md)</p></td>
<td><p>Stellt eine Auflistung von Schlüsselwörtern und benutzerdefinierte Schlüsselwörter.</p></td>
</tr>
</tbody>
</table>

 

## <a name="remarks"></a>Hinweise


Dieses Element ermöglicht die Erstellung eines benutzerdefinierten Schlüsselworts für jedes mögliche Ereignis Event Tracing for Windows (ETW).

## <a name="related-topics"></a>Verwandte Themen


[Elemente](elements.md)

 

 







