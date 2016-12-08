---
title: "3. Definitionen für Profil"
description: "3"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 1d072198-f631-463a-886c-b69a48c1acd1
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: f36c15fe80b8b5ee91f4e9a29dc3ba46f47ebc5c
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="3-profile-definitions"></a>3. Definitionen für Profil


Windows Performance Aufzeichnung (WPR) Aufzeichnung Profile werden in eine XML-Datei gespeichert, die Erweiterung .wprp hat. *Profildefinitionen* vereinen die Definitionen Collector und Anbieter in der Datei .wprp.

Inhalt dieses Artikels:

-   [Profile](#profiles)

-   [Element Kollektoren](#collectors)

-   [Definition Profilbeispiel](#profdefex)

## <a name="profiles"></a>Profile


Definieren Sie ein Profil WPR mithilfe von `(<Profile> … </Profile>` XML-Tags, die auf Collector und Anbieter Definition XML-Tags verweisen, die Sie in der gleichen .wprp Datei oder in einer anderen .wprp-Datei mithilfe der Vererbung definieren. Jede Benutzerprofildienst-Definition-XML-Tag benötigen die folgenden Attribute:

-   **ID**: Eindeutiger Bezeichner der Profildefinition. Verwenden Sie die folgende Profil Bezeichner Konstruktion:

    &lt;*Namen*&gt;. &lt; *DetailLevel*&gt;. &lt; *LoggingMode*&gt;.

-   **Name**: Zeichenfolge, die den Namen des Profils angibt.

-   **DetailLevel**: Attribut, das angibt, ob eine Profildefinition Timing-Protokollierung (*hell*) oder Analysis-Protokollierung (*Verbose*) verwendet wird.

-   **LoggingMode**: Attribut, das angibt, ob das Profil in eine sequenzielle Datei oder kreisförmige Speicherpuffern Ereignisse protokolliert. Alle Profile benötigen eine Datei und einer Version Speicher in derselben .wprp Datei.

-   **Beschreibung**: Beschreibung des Profils, das der Benutzer erhält.

WPR unterstützt die Leistung für die Datei- und Arbeitsspeicher Protokollierung Modi für jede Datei .wprp außer *ein-/ausschalten Profile*aufzeichnen. Sie müssen sich abmelden auf/Profile in eine Datei, aber Sie müssen eine Datei und eine Version Speicher definieren. Da nur ein Protokollierungsmodus Definition eines einzelnen unterstützt werden kann, können zwei oder vier Profildefinitionen in eine .wprp, eine Datei für jede Kombination von Modus und Detail Protokollierungsstufe vorhanden sein. Alle Profildefinitionen in einer einzigen .wprp-Datei müssen dasselbe **Name** -Attribut haben.

&lt;*Namen*&gt;. &lt; *DetailLevel*&gt;. &lt; *LoggingMode*&gt;

Das folgende Codebeispiel zeigt **Example1.wprp**. Diese Datei enthält zwei Profildefinitionen. Mit den drei Punkten (...) stellt den Textkörper des Profils dar.

``` syntax
<Profile
  Id="Example1.Verbose.File"
  Name="Example1"
  DetailLevel="Verbose"
  LoggingMode="File"
  Description="Example1 profile">
…
</Profile>
<Profile
  Id="Example1.Verbose.Memory"
  Name="Example1"
  DetailLevel="Verbose"
  LoggingMode="Memory"
  Description="Example1 profile">
…
</Profile>
```

Im folgenden Codebeispiel wird veranschaulicht, **Example2.wprp**. Diese Datei enthält Profildefinitionen von vier. Mit den drei Punkten (...) stellt den Textkörper des Profils dar.

``` syntax
<Profile
  Id="Example2.Verbose.File"
  Name="Example2"
  DetailLevel="Verbose"
  LoggingMode="File"
  Description="Example2 profile">
…
</Profile>
<Profile
  Id="Example2.Light.File"
  Name="Example2"
  DetailLevel="Light"
  LoggingMode="File"
  Description="Example2 profile">
…
</Profile>
<Profile
  Id="Example2.Verbose.Memory"
  Name="Example2"
  DetailLevel="Verbose"
  LoggingMode="Memory"
  Description="Example2 profile">
…
</Profile>
<Profile
  Id="Example2.Light.Memory"
  Name="Example2"
  DetailLevel="Light"
  LoggingMode="Memory"
  Description="Example2 profile">
…
</Profile>
```

## <a name="a-href-idcollectorsacollectors-element"></a><a href="" id="collectors"></a>Kollektoren-Element


Das **Kollektoren** -Element enthält Verweise auf zuvor definierten System und Ereignis Kollektoren. Die Elemente [SystemCollectorId](systemcollectorid.md) und [EventCollectorId](eventcollectorid.md) Identifizieren dieser Kollektoren.

Jedes **SystemCollectorId** und **EventCollectorId** -Element enthält ein obligatorische **Value** -Attribut, das das **Id** -Attribut der Collection gibt an, die verwendet werden soll. Jedes Element **SystemCollectorId** und **EventCollectorId** enthält auch eine Liste von Elementen [SystemProviderId](systemproviderid.md) oder [EventCollectorId](eventcollectorid.md) . Diese Elemente verfügen über ähnliche Syntax. Diese Elemente beziehen sich jedoch zuvor definierten System und Ereignis-Anbieter.

Sie können außerdem Kollektoren und Anbieter in der Profildefinition definieren.

## <a name="a-href-idprofdefexaprofile-definition-example"></a><a href="" id="profdefex"></a>Definition Profilbeispiel


Im folgenden Codebeispiel zeigt eine vollständige Profildefinition.

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
      <!--Enables the system provider for this system collector. --> 
      <SystemProviderId
        Value="system-provider"/>
    </SystemCollectorId> 
    <EventCollectorId
      Value="WPREventCollector">
      <EventProviders> 
      <!--Enables two event providers for this event collector. --> 
        <EventProviderId
          Value="Win32K-provider"/>
        <EventProviderId
          Value="Search-Core-provider"/>
      </EventProviders> 
    </EventCollectorId> 
  </Collectors>
</Profile>
```

## <a name="related-topics"></a>Verwandte Themen


[Authoring Aufzeichnung Profile](authoring-recording-profiles.md)

[2. System- und Ereignis Anbieter-Definitionen](2-system-and-event-provider-definitions.md)

[Protokollierungsmodus](logging-mode.md)

[Detailstufe](detail-level.md)

[ProblemCategories](problemcategories.md)

[SystemCollectorId](systemcollectorid.md)

[HeapEventProviderId](heapeventproviderid.md)

 

 







