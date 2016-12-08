---
title: 2. System- und Ereignis Anbieter-Definitionen
description: "2"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 24358037-a8ad-41c8-b82c-b4c5111b17d3
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 577c2715b4d81c17fbd8eec2a8fd3c3f9ffdf902
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="2-system-and-event-provider-definitions"></a>2. System- und Ereignis Anbieter-Definitionen


Windows Performance Aufzeichnung (WPR) Aufzeichnung Profile werden in eine XML-Datei gespeichert, die Erweiterung .wprp hat. Die Definition eines Systems Anbieter gibt das System Schlüsselwörter, Stapel und Speicher Pooltags in der Datei .wprp an.

Inhalt dieses Artikels:

-   [Provider-Definition](#provdef)

-   [System-Anbieter](#sys)

-   [Ereignisanbieter](#event)

-   [Anbieter für Heap-Ereignis](#heap)

-   [Capture-State-Anbieter](#cap)

-   [Beispiel](#ex)

## <a name="a-href-idprovdefaprovider-definition"></a><a href="" id="provdef"></a>Provider-Definition


Elemente in der Datei .wprp müssen in der folgenden Reihenfolge definiert werden:

1.  Alle Kollektoren

2.  System-Anbieter

3.  Ereignisanbieter

4.  Heap Anbieter, falls vorhanden

5.  Alle Profile

In einigen Fällen kann Anbieter definiert in, anstatt zuvor die Benutzerprofildienst-Definition. Beispiel:

``` syntax
<EventCollector Id="Collector1" Name="Sample Event Collector">
   <BufferSize Value="128"/>
   <Buffers Value="64"/>
</EventCollector>

<Profile Id="Sample.Verbose.File" Name="Sample" Description="Sample profile" DetailLevel="Verbose" LoggingMode="File">
   <Collectors>
      <EventCollectorId Value="Collector1">
         <EventProviders>
            <EventProvider Id="EventProvider_Microsoft-Windows-Kernel-Power" Name="Microsoft-Windows-Kernel-Power" NonPagedMemory="true">
               <Keywords>
                  <Keyword Value="0x4"/>
               </Keywords>
            </EventProvider>
         </EventProviders>
      </EventCollectorId>
   </Collectors>
</Profile>
```

## <a name="a-href-idsysasystem-providers"></a><a href="" id="sys"></a>System-Anbieter


Nur obligatorische Attributs für eine Definition eines Systems Anbieter ist **-Id**an. Inneren XML-Tags Geben Sie Schlüsselwörter, Stapel und Pooltags zum Aktivieren. Listen mit allen unterstützten Schlüsselwörter und Stapel finden Sie unter [Stapel](stack-wpa.md) und [Schlüsselwort (in "Systemprovider")](keyword--in-systemprovider-.md).

Das folgende Codebeispiel zeigt eine Definition eines Systems Anbieter.

``` syntax
<SystemProvider
  Id="system-provider">
  <Keywords>
    <Keyword
      Value="ProcessThread"/>
    <Keyword
      Value="Loader"/>
    <Keyword
      Value="CSwitch"/>
  </Keywords>
  <Stacks>
    <Stack
      Value="ThreadCreate"/>
    <Stack
      Value="ReadyThread"/>
    <Stack
      Value="CSwitch"/>
  </Stacks>
  <PoolTags>
    <PoolTag
      Value="a*"/>
    <PoolTag
      Value="b*"/>
    <PoolTag
      Value="c*"/>
    <PoolTag
      Value="d*"/>
  </PoolTags>
</SystemProvider>
```

## <a name="a-href-ideventaevent-providers"></a><a href="" id="event"></a>Ereignisanbieter


Ein Ereignis Anbieter Definition gibt der Anbieter Event Tracing for Windows (ETW) verwenden und die Schlüsselwörter und Ebenen zu aktivieren. Ein Ereignis Anbieter Definition erfordert eine obligatorische Attribut **Name** und eine obligatorische **Id** -Attribut.

Das **Name** -Attribut gibt einen der folgenden Namen an:

-   Der Name eines registrierten Crimson-Anbieters, z. B. "Microsoft-Windows-Suche-Core".

-   Der Anbieter GUID wie beispielsweise "49c2c27c-fe2d-40bf-8c4e-c3fb518037e7".

-   Der Name eines früheren Anbieters, z. B. "IE6".

-   Der Name der besonderer wie "PerfTrack" oder "DotNetProvider".

Die folgenden optionalen Attribute können Sie Anbieter Parameter optimieren:

-   **Stapel**: Gibt an, ob der Anbieter Stapel erfasst wird. Die Standardeinstellung ist "false".

-   **Ebene**: Gibt die Protokollierungsstufe ETW. Die Standardeinstellung ist 0xFF.

-   **NonPagedMemory**: Gibt an, ob WPR für den Puffer nicht ausgelagerte Arbeitsspeicher für diesen Anbieter verwendet. Die Standardeinstellung ist "false".

    **Warnung**  
    Einige Windows Anbieter erfordern die Verwendung von nicht ausgelagerten Speicher während Trace-Sammlung. Ein Beispiel eines Ereignisanbieters, das NonPagedMemory erfordert ist `EventProvider_Microsoft-Windows-Win32k`.

     

-   **CaptureStateOnly**: Wenn Festlegung auf "True", gibt an, dass WPR diesem Anbieter im angegebenen Capture-Status ermöglicht.

-   **SID**: Gibt an, ob die erweiterten Daten der protokollierten Ereignisse Sicherheits-ID (SID) des Benutzers enthält.

-   **TSID**: Wenn festlegen auf "true", gibt den Terminaldienste-Sitzungsbezeichner auf erweiterte Daten aufgezeichnet.

Optionale inneren XML-Tags angeben, die Schlüsselwörter zu aktivieren. Im Gegensatz zu System-Anbieter verfügen Anbieter nicht definierte textbezogene Konstanten. Aus diesem Grund haben Anbieter Hexadezimalwerte. Die Syntax ist jedoch identisch mit der System-Anbieter. Wenn Sie Stichwörter nicht angeben, ist der Standardwert 0xFFFFFFFFFFFFFFFF.

## <a name="a-href-idheapaheap-event-providers"></a><a href="" id="heap"></a>Anbieter für Heap-Ereignis


Die Definition der Heap Anbieter gibt die Prozess-ID des Prozesses für die WPR Heap Ereignisse aufgezeichnet werden. **ID** ist die einzigen obligatorischen Attribut. Das **HeapProcessId** untergeordnete Element ist nicht zwingend erforderlich. Dieses Element gibt den Prozess- **Id** -Attributs des Prozesses, das Sie analysieren möchten. Im folgenden Beispiel wird gezeigt, wie dazu.

``` syntax
<HeapEventProvider
  Id="Base_Heap_Provider">
</HeapEventProvider>
<HeapEventProvider
  Base="Base_Heap_Provider"
  Id="Derived_Heap_Provider">
  <HeapProcessIds Operation="Set">
    <HeapProcessId Value="2314"/>
  </HeapProcessIds>
</HeapEventProvider>
```

## <a name="a-href-idcapacapture-state-providers"></a><a href="" id="cap"></a>Capture-Zustand Providers


Anders als bei regulären Anbieter, die während der gesamten Tracingsitzung aktiviert sind, sind-Zustand der Erfassung von Anbietern nur beim Speichern oder beim Starten einer Sitzung Capture aktiviert. Im folgende Beispiel werden reguläre und Capture-Zustand Anbieter.

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
  <!-- CaptureStateOnly="true" means provider is not enabled throughout the tracing session. -->
  <CaptureStateOnSave>
    <Keyword Value="0x80000"/> <!-- Provider is enabled with these keywords when tracing is saved. -->
  </CaptureStateOnSave>
</EventProvider>
```

## <a name="a-href-idexaexample"></a><a href="" id="ex"></a>Beispiel


Im folgenden Codebeispiel wird definiert zwei Anbieter.

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

## <a name="related-topics"></a>Verwandte Themen


[Authoring Aufzeichnung Profile](authoring-recording-profiles.md)

[1. Collector-Definitionen](1-collector-definitions.md)

[3. Definitionen für Profil](3-profile-definitions.md)

["Systemprovider"](systemprovider.md)

[EventProvider](eventprovider.md)

[HeapEventProvider](heapeventprovider.md)

[Schlüsselwort (in "Systemprovider")](keyword--in-systemprovider-.md)

[Stack](stack-wpa.md)

[PoolTag](pooltag.md)

 

 







