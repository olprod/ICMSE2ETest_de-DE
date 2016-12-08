---
title: Vererbung (engl.)
description: Vererbung (engl.)
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 5caaf667-4c1a-4459-8a45-36001ce6b414
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 4f5bca1fb1c93b710443f284829dc65198f4fa6a
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="inheritance"></a>Vererbung (engl.)


Windows Performance Aufzeichnung (WPR) Aufzeichnung Profile werden in eine XML-Datei gespeichert, die Erweiterung .wprp hat. WPR unterstützt Vererbung der Objekte mithilfe der **Base = ""** Attribut im WPR Profil XML-Schema. Vererbung ermöglicht Ihnen zu behalten und wiederverwenden allgemeine Profildefinitionen spezielle Szenarien aufzeichnen aufbauen. Beispielsweise können Sie einen Anbieter zu einem bestehenden Profil hinzufügen und ändern Puffergrößen somit eine Definition im aktuellen Profil hinzugefügt, ohne.

**Wichtige**  
Wenn Sie WPRP Profile erstellen, sollten Sie Profildaten von WPRs integrierten Basis Profile erben oder gleichnamige Sitzung zu vermeiden, aktivieren den gleichen Anbieter mehrmals wiederverwenden.

 

Inhalt dieses Artikels:

-   [Basis-Profilen](#base)

-   [Beispiel](#ex)

-   [Bewährte Methoden für Vererbung](#bestprac)

## <a name="a-href-idbaseabase-profiles"></a><a href="" id="base"></a>Basis-Profilen


XML-Tags können Sie den Inhalt eines Profils ändern. Sie müssen das Attribut **Vorgang** verwenden. Die möglichen Werte für das Attribut **Vorgang** werden **festgelegt** und **Hinzufügen**. Im folgenden Beispiel wird die **CpuConfig**, **CSwitch**und **SampledProfile** Schlüsselwörter, die **BaseProfile** definiert mit **DerivedProfile** das **ReadyThread** System-Schlüsselwort hinzugefügt.

``` syntax
<SystemCollector
  Id="BaseSystemCollector" ... />

<SystemProvider
  Id="MainSystemProvider">
  <Keywords>
    <Keyword
      Value="CpuConfig"/>
    <Keyword
      Value="CSwitch"/>
    <Keyword
      Value="SampledProfile"/>
  </Keywords>
</SystemProvider>

<SystemProvider
  Id="AnotherSystemProvider">
  <Keywords> 
    <Keyword
      Value="ReadyThread"/>
  </Keywords>
</SystemProvider>

<Profile
  Id="BaseProfile"...>
  ... 
  <Collectors>
    <SystemCollectorId
      Value="BaseSystemCollector">
      <SystemProviderId
        Value="MainSystemProvider"/>
    </SystemCollectorId>
  </Collectors>
</Profile>

<Profile
  Id="DerivedProfile"
  Base="BaseProfile"...>
... 
  <Collectors Operation="Add"> <!--Use "Add" operation to add new provider to an existing one. -->
    <SystemCollectorId
      Value="BaseSystemCollector">
      <SystemProviderId
        Value="AnotherSystemProvider"/> <!--Specify provider to add. --> 
    </SystemCollectorId> 
  </Collectors>
</Profile>
```

**Hinweis**  
Wenn Sie keinen Attributs **Vorgang** Vererbung zu verwenden, wird WPR **festgelegte**Standardwert verwendet.

 

## <a name="a-href-idexaexample"></a><a href="" id="ex"></a>Beispiel


Das folgende Beispiel definiert ein Profil für Datei Protokollierung Modus. Die Version Arbeitsspeicher erbt von Dateiversion und überschreibt den Protokollierungsmodus.

``` syntax
<Profile
   Id="SampleProfile.Verbose.File"
   LoggingMode = "File"
   DetailLevel = "Verbose"
   Name = "SampleProfile"
   Description = "A sample profile">
   …

</Profile>

<Profile
   Id="SampleProfile.Verbose.Memory"
   Base="SampleProfile.Verbose.File”
   LoggingMode = "Memory"
   DetailLevel = "Verbose"
   Name = "SampleProfile"
   Description = "A sample profile"/>
```

## <a name="a-href-idbestpracainheritance-best-practices"></a><a href="" id="bestprac"></a>Bewährte Methoden für Vererbung


Schlecht entwickelte Vererbung kann unerwartete Ergebnisse erstellen. Es wird empfohlen, dass Sie nur Kollektoren Aufkäufer oder Profile von Benutzerprofilen abgeleitet. Sie sollten nie abgeleiteten Objekte über mehrere Objekttypen kombinieren.

Die folgenden drei Beispiele beschreiben zwei Methoden, wenn Vererbung verwendet wird. im dritte Beispiel wird eine schlechte Verwendung von Vererbung beschrieben.

### <a name="a-href-idex1inheraexample-1-good-use-of-inheritance"></a><a href="" id="ex1inher"></a>In Beispiel 1: Gute Verwendung der Vererbung

Verwenden Sie die Spezifikationen des Ereignisses Collector-A, mit einigen Änderungen werden soll. Dazu:

1.  Definieren Sie einen zweiten Collector (Collector B), der die Spezifikationen von Collector a erbt

2.  Ändern der Collector-B.

3.  Legen Sie das Profil auf Verweis Collector-B.

Dies ist ratsam, da nur das Collection-Objekt Attribute aus einer anderen Collection-Objekt erbt, die Sie direkt vom Profil verwiesen wird.

### <a name="a-href-idex2inheraexample-2-good-use-of-inheritance"></a><a href="" id="ex2inher"></a>Beispiel 2: Auf die Verwendung von Vererbung

1.  Profil-A-Verweise Collector-A.

2.  Profil B erbt die Attribute von Profile-A.

3.  Ändern von bestimmten Attribute in Profil-B.

Dies ist empfehlenswert, da das Profile-Objekt aus einer anderen Profile-Objekt abgeleitet ist.

### <a name="a-href-idex3inheraexample-3-poor-use-of-inheritance"></a><a href="" id="ex3inher"></a>Beispiel 3: Schlechter Verwenden von Vererbung

1.  Profil-A-Verweise Collector-A.

2.  Collector B erbt vom Collector-A.

3.  Profil B erbt von Profile-A- und auch verweist Collector-B.

In diesem Fall Profil B verweist auf Collector B zweimal: einmal durch Vererbung von Profile-A und einmal von direkten Verweis auf Collector-B. In diesem Fall ist es nicht mehr ersichtlich ist wie die Definition für Collector B ausgewertet werden soll. d. h., sollte die Ableitung Vorrang. In diesem Beispiel wird eine schlechten Code dargestellt ist, da der Sortierung nicht definiert ist und dazu, dass widersprüchlich Ergebnisse basierend führen kann auf der Reihenfolge der Vorgänge. Diese Art der Vererbung sollte vermieden werden.

## <a name="related-topics"></a>Verwandte Themen


[Authoring Aufzeichnung Profile](authoring-recording-profiles.md)

[WPRControlProfiles-Schema](wprcontrolprofiles-schema.md)

 

 







