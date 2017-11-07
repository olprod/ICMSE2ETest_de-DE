---
title: "Gruppierung von Features und Einschränkungen"
description: "Gruppen Feature und Feature Einschränkungen können zusätzliche Logik, die Buildsystem zur Unterstützung der intelligenten Verarbeitung des OEMInput XML hinzugefügt werden soll."
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: b2079741-e3a8-44ab-b76f-75b287d0cd66
ms.openlocfilehash: d3f78e455f7a87e93cbc022d9e298e13cf1c47db
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="feature-groupings-and-constraints"></a>Gruppierung von Features und Einschränkungen


Gruppen Feature und Feature Einschränkungen können zusätzliche Logik, die Buildsystem zur Unterstützung der intelligenten Verarbeitung des OEMInput XML hinzugefügt werden soll.

## <a name="feature-groupings"></a>Feature-Gruppen


Feature Gruppierungen lässt eine bessere Verwaltung optionalen Features und die Organisation der Pakete zur einfacheren Verwaltung. Feature Gruppierung wird verwendet, um die Feature-Einschränkungen von Microsoft und optional vom OEM implementieren.

## <a name="feature-constraints"></a>Feature Integritätsregeln


Integritätsregeln Feature können angegeben werden, um unlogische oder unzulässiges Buildkonfigurationen zu vermeiden.

Einige Einstellungen schließen sich gegenseitig aus, und zu einem Zeitpunkt sollte nur eine Einstellung angegeben werden. Angenommen, die Features, VERSION\_PRODUKTIONS- und RELEASE\_TEST. Diese Features schließen sich gegenseitig aus. Dies bedeutet, dass bei VERSION\_TEST festgelegt ist, VERSION\_PRODUKTION muss nicht festgelegt werden.

Einschränkungen sind auf der Microsoft und OEM-Ebene des Features zusammengefasst. OEMs können nicht Microsoft Einschränkungen außer Kraft setzen. Die folgenden Einschränkungen werden unterstützt:

<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<thead>
<tr class="header">
<th>Element</th>
<th>Beschreibung</th>
<th>Mindestens ein Feature ist erforderlich</th>
<th>Features schließen sich gegenseitig aus</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Ein oder mehrere</p></td>
<td><p>Ein oder mehrere Features müssen angegeben werden.</p></td>
<td><p>wahr</p></td>
<td><p>falsch</p></td>
</tr>
<tr class="even">
<td><p>ZeroOrOne</p></td>
<td><p>Ein Feature oder keine Features können angegeben werden.</p></td>
<td><p>falsch</p></td>
<td><p>wahr</p></td>
</tr>
<tr class="odd">
<td><p>OneAndOnlyOne</p></td>
<td><p>Ein Feature ist erforderlich, und nur ein Feature angegeben werden kann.</p></td>
<td><p>wahr</p></td>
<td><p>wahr</p></td>
</tr>
<tr class="even">
<td><p>ZeroOrMore</p></td>
<td><p>Dies ist der Standardwert und gibt an, dass es keine Einschränkungen sind. Diese Option wird nur verwendet, um Gruppenfunktionen für die Veröffentlichung und werden während der Imaging ignoriert werden.</p></td>
<td><p>falsch</p></td>
<td><p>falsch</p></td>
</tr>
</tbody>
</table>

 

Im folgende XML-Beispiel veranschaulicht die Verwendung der Nebenbedingungen auf das Feature gefälschten Modem entsprechend beeinträchtigen.

``` syntax
<Features>
  <Microsoft>
    <FeatureGroup Constraint="OneAndOnlyOne">
           <FeatureIDs>
           <FeatureID>MS_IMGFAKEMODEM</FeatureID>
           <FeatureID>MS_IMGNOFAKEMODEM</FeatureID> 
          </FeatureIDs>
    </FeatureGroups >
  </Microsoft>
</Features>
```

Im Beispiel für die Einschränkungen angeben, dass IMGFAKEMODEM oder IMGNOFAKEMODEM ausgewählt werden muss. Beide Werte können nicht gleichzeitig festgelegt werden. Zu einem Zeitpunkt muss nur ein Wert festgelegt werden. Diese Einschränkung ist erforderlich, da die Funktion zum Testen des gefälschten Modem entweder aktiviert oder deaktiviert werden muss.

Im folgende XML-Beispiel veranschaulicht die Verwendung der Nebenbedingungen zu entsprechend die Produktion Buildeinstellungen beeinträchtigen. Dieses Beispiel zeigt, wie mehrere Einschränkungen ein bestimmtes Feature zugeordnet werden können.

``` syntax
<Features>
  <Microsoft>
    <FeatureGroups>
        <FeatureGroup Constraint="ZeroOrOne">
         <FeatureIDs>
          <FeatureID>RELEASE_PRODUCTION</FeatureID> 
          <FeatureID>MS_CODEINTEGRITY_PROD</FeatureID> 
        </FeatureIDs>
    </FeatureGroup>
         <FeatureGroup Constraint="ZeroOrOne">
           <FeatureIDs>
            <FeatureID>RELEASE_PRODUCTION</FeatureID>
            <FeatureID>MS_DISABLETESTSIGNING</FeatureID> 
         </FeatureIDs>
    </FeatureGroup>
  </Microsoft>
</Features>
```

Wenn &lt;ReleaseType&gt;Produktion&lt;/ReleaseType&gt; wird in der Datei OEMInput, diese Karten auf RELEASE festgelegt\_PRODUKTION. Weitere Informationen zur Freigabe finden Sie unter [OEMInput Inhalt](oeminput-file-contents.md).

Geben Sie die Einschränkungen in der Stichprobe, die:

-   Entweder VERSION\_PRODUKTION oder MS\_CODEINTEGRITY\_"Bemerkungen" ausgewählt werden kann, jedoch beide möglicherweise nicht gleichzeitig ausgewählt werden. Dies ist, da die Produktion Integrität des Codes wird automatisch aktiviert, wenn RELEASE\_PRODUKTION ausgewählt ist und deshalb nicht manuell aktiviert werden.

-   Entweder VERSION\_PRODUKTION oder MS\_DISABLETESTSIGNING ausgewählt werden kann, aber beide möglicherweise nicht gleichzeitig ausgewählt werden. Dies ist, da Test-Signatur automatisch deaktiviert wird beim FREIGEBEN\_PRODUKTION ausgewählt ist und daher nicht manuell deaktiviert werden.

Die Buildoptionen sind komplexer und werden in den folgenden XML-CODE ausgedrückt.

``` syntax
FeatureGroup Constraint="OneAndOnlyOne">
  <FeatureIDs>
    <FeatureID>RELEASE_PRODUCTION</FeatureID> 
      <FeatureID>MS_TEST</FeatureID> 
      <FeatureID>MS_HEALTH</FeatureID> 
      <FeatureID>MS_PRODUCTION</FeatureID> 
      <FeatureID>MS_SELFHOST</FeatureID> 
    </FeatureIDs>
  </FeatureGroup>
<FeatureGroup Constraint="OneAndOnlyOne">
  <FeatureIDs>
    <FeatureID>RELEASE_PRODUCTION</FeatureID> 
    <FeatureID>MS_PRODUCTION_CORE</FeatureID> 
    <FeatureID>MS_TEST</FeatureID> 
  </FeatureIDs>
</FeatureGroup>
```

Diese Einstellungen in der Stichprobe angeben, die PRODUKTION\_CORE schließen sich gegenseitig aus mit VERSION ist\_PRODUKTIONS- und TEST, ist aber keine mit STATUS, die PRODUKTION oder DAVON gegenseitig aus.

Weitere Informationen zu den Features erstellen finden Sie unter [optionale Features zum Erstellen von Bildern](optional-features-for-building-images.md).

## <a name="implicit-feature-ids"></a>Implizite Feature-IDs


Implizite Feature-IDs werden basierend auf die XML-Eingabe, mit dem Definieren von Features in Feature Manifestdateien, generiert. Feature Einschränkungen müssen implizite Feature-IDs verwenden. Dieser Abschnitt enthält die Zuordnung zwischen der XML-Eingabewerten und die generierten implizite Feature-IDs.

**Implizite Feature-vordefinierte Release Type IDs**

Es gibt zwei vordefinierte implizite Feature-IDs, die für Feature-Integritätsregeln verwendet werden können.

-   VERSION\_TEST

-   RELEASE\_PRODUKTION

Weitere Informationen zu Version Typen finden Sie unter [optionale Features zum Erstellen von Bildern](optional-features-for-building-images.md).

**OEM und Microsoft implizite Feature-IDs**

Implizite Feature-IDs werden für jedes Feature OEM und Microsoft automatisch erstellt. Dies ist meine vor dem Anfügen entweder *MS\_ * für Microsoft oder *OEM\_ * für OEM definiert Funktionen.

Beispielsweise wenn ein OEM ein Feature mit der Bezeichnung TEST erstellt\_FEATURE1 mithilfe der unten gezeigten XML-CODE: implizite Feature-ID werden *OEM\_TEST\_FEATURE1*.

``` syntax
<Features>
    <OEM>
     <PackageFile Path="%oempackageroot%\test\" 
      Name="Contoso.Test.MinTE.spkg">
        <FeatureIDs>
          <FeatureID>TEST_FEATURE1</FeatureID>
        </FeatureIDs>
      </PackageFile>
   </OEM>
</Features>
```

Verwenden Sie zum Erstellen einer Einschränkung Feature um sicherzustellen, dass dieses Testfeature Version Testtypen nur Lieferumfang ist das folgende XML.

``` syntax
<FeatureGroup Constraint="ZeroOrOne">
   <FeatureIDs>
      <FeatureID>RELEASE_PRODUCTION</FeatureID>
      <FeatureID>OEM_TEST_FEATURE1</FeatureID> 
   </FeatureIDs>
</FeatureGroup>
```

**Implizite SOC Feature-IDs**

SOC Features sind mit SOC vor dem angefügten\_. Für das Beispiel wenn *DCD6000* angegeben wird, in der Funktion manifest-XML, wäre die implizite Feature-ID *SOC\_DCD6000*.

**PA implizite Feature-IDs**

PA-Features sind mit PA vor dem angefügten\_. Für Beispiel, wenn in der Funktion *"Contoso"* angegeben ist XML manifest, wäre die implizite Feature-ID *PA\_CONTOSO*.

**GERÄT impliziten Feature-IDs**

Gerät Features sind mit Gerät vor dem angefügten\_. Für das Beispiel wenn *BETA* angegeben wird, in der Funktion manifest-XML, wäre die implizite Feature-ID *GERÄT\_BETA*.

Weitere Informationen zum Arbeiten mit den Attributen SOC, PA und GERÄTE finden Sie unter [Feature Dateiinhalt manifest](feature-manifest-file-contents.md).

## <a name="related-topics"></a>Verwandte Themen


[Optionale Features zum Erstellen von Bildern](optional-features-for-building-images.md)

 

 

[Senden Sie Kommentare zu diesem Thema an Microsoft] (mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback%20%5Bp_phFlashing\p_phFlashing%5D:%20Feature%20groupings%20and%20constraints%20%20RELEASE:%20%2810/4/2016%29&body=%0A%0APRIVACY%20STATEMENT%0A%0AWe%20use%20your%20feedback%20to%20improve%20the%20documentation.%20We%20don't%20use%20your%20email%20address%20for%20any%20other%20purpose,%20and%20we'll%20remove%20your%20email%20address%20from%20our%20system%20after%20the%20issue%20that%20you're%20reporting%20is%20fixed.%20While%20we're%20working%20to%20fix%20this%20issue,%20we%20might%20send%20you%20an%20email%20message%20to%20ask%20for%20more%20info.%20Later,%20we%20might%20also%20send%20you%20an%20email%20message%20to%20let%20you%20know%20that%20we've%20addressed%20your%20feedback.%0A%0AFor%20more%20info%20about%20Microsoft's%20privacy%20policy,%20see%20http://privacy.microsoft.com/default.aspx. "Senden Sie Kommentare zu diesem Thema an Microsoft")





