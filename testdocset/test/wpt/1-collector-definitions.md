---
title: 1. Collector-Definitionen
description: "1"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 40712815-d517-49aa-b208-76a2115ed9fd
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 034f5324ff4613b09b0efead052ceb305dc18255
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="1-collector-definitions"></a>1. Collector-Definitionen


Windows Performance Aufzeichnung (WPR) unterstützt derzeit drei Arten von Kollektoren: Collector des Systems, Sammeln von Ereignissen und einem Heap Ereignissammlung. Die Definition des Systems Collector gibt Puffergrößen und andere Attribute für Event Tracing for Windows (ETW) System Protokollierung Sitzungen, die zusammen mit der NT Kernel-Protokollierung funktionieren. Ereignis und Heap Collector Definitionen geben Puffergrößen und andere Attribute für benutzersitzungen ETW.

Collector Definition Reihenfolge wird durch das Schema WPR beschränkt. In der Datei .wprp müssen Collector Systemdefinitionen Ereignis Collector Definitionen voranstellen. Diese Definitionen müssen sowohl der Heap Collector direkt vorangehen Anweisungen, (wenn die Definition eines Heap Collector vorhanden ist). Das Schema WPR ist im [WPRControlProfiles Schema](wprcontrolprofiles-schema.md)definiert.

## <a name="collector-attributes"></a>Collection-Attribute


Kollektoren wurden die folgenden obligatorischen Attribute:

-   **ID**: eindeutige Zeichenfolgenbezeichner, der auf die Collection-Definition in der Datei .wprp verweist.

-   **Name**: der Name der Collection; beispielsweise "WPR Collector". Der Name des Collector muss "NT Kernel-Protokollierung" sein.

Collector Definitionen müssen die folgenden Puffer Größendefinitionen enthalten:

-   **Puffergröße**: Gibt die Größe eines einzelnen Puffers, in Kilobyte (KB).

-   **Puffer**: Gibt die Anzahl der Puffer oder, falls das **PercentageOfTotalMemory** -Attribut auf "true", den Prozentsatz des Gesamtspeichers für Pufferung verwenden festgelegt ist.

Weitere Informationen zu Puffer finden Sie unter [Logging Modus](logging-mode.md).

## <a name="collector-definition-examples"></a>Beispiele für Collector Definition


Das folgende Codebeispiel zeigt eine Definition eines Systems Collector und ein Ereignis Collector Definition.

``` syntax
<SystemCollector
  Id="WPRSystemCollector"
  Name="NT Kernel Logger"
  FileName="WPRKernel.etl">
  <BufferSize
    Value="512"/>
  <Buffers
    Value="3"
    PercentageOfTotalMemory="true"/>
</SystemCollector>

<EventCollector
  Id="WPREventCollector"
  Name="WPR Event Collector"
  FileName="somefilename.etl">
  <BufferSize
    Value="128"/> 
  <Buffers
    Value="64"/>
</EventCollector>

<HeapEventCollector
  Id="Base_Heap_Collector"
  Name="Base Heap Collector"
  FileName="heap.etl">
</HeapEventCollector>
```

## <a name="inheritance-examples"></a>Beispiele für Vererbung


Windows Performance Aufzeichnung unterstützt Vererbung Objekte mithilfe der `Base=""` -Attribut in das WPR Profil XML-Schema. Dadurch Ergänzungen oder Specializations von Objekten, die beim Hinzufügen von Definitionen für häufige Wiederverwendung stetig erstellt werden.

In bestimmten Szenarien kann unbeabsichtigten Komplexität und Nebeneffekte auftreten. In diesem Abschnitt wird beschrieben, Beispiele und bewährten Methoden.

### <a name="example-1"></a>In Beispiel 1

![Vererbungsbeispiel](images/wpr-collector-definitions-example1.jpg)

Wenn ein Profil **ein Profil** mit einigen Änderungen der Ereignissammlung **Collector A** verwenden möchte, können sie einen Collector **Collector A2** , die **eine Sammlung** abgeleitet definieren (Base = "Collector A"), und klicken Sie dann auf dieser Collector **Collector A2**verweist. Dies wird empfohlen, da nur das Collection-Objekt aus einer anderen Collection-Objekt abgeleitet und direkt verwiesen wird.

### <a name="example-2"></a>In Beispiel 2

![in Vererbungsbeispiel 2](images/wpr-collector-definitions-example2.jpg)

Ein Profil **ein Profil** verweist auf eine Sammlung **Collector ein**. Ein anderes Profil **Profil B** erfordert Änderungen Profil **A** daraus abgeleitet wird, und gibt an, dessen Änderungen direkt in der Definition. Dies wird empfohlen, da das Profile-Objekt aus einer anderen Profile-Objekt abgeleitet ist.

### <a name="example-3"></a>Beispiel 3

![in Vererbungsbeispiel 3](images/wpr-collector-definitions-example3.jpg)

Ein Profil **ein Profil** verweist auf eine Sammlung **Collector ein**. Eine Sammlung **Collector A2** abgeleitet **Collector ein**. Schließlich das Profil **Profil B** abgeleitet wird aus der Tabelle **ein Profil** und auch verweist auf **eine Sammlung** , die bereits im übergeordneten Profil des **Profil B**verwiesen wird.

In diesem Fall ist es nicht eindeutig wie die Definition für **Collector A2** ausgewertet werden soll. In einem Fall die Ableitung Profil haben Vorrang vor, und in einem anderen die Ableitung Collector Vorrang. Dies wird nicht empfohlen, da der Sortierung nicht definiert ist und dazu, dass unterschiedliche Ergebnisse basierend führen kann auf der Reihenfolge der Vorgänge.

Anhand dieser sollten Sie nie abgeleiteten Objekte über mehrere Objekttypen kombinieren.

## <a name="related-topics"></a>Verwandte Themen


[Erstellung der Aufzeichnung Profile](authoring-recording-profiles.md)

[2. System- und Ereignis Anbieter-Definitionen](2-system-and-event-provider-definitions.md)

[Aufzeichnung Profil XML (engl.)](recording-profile-xml-reference.md)

 

 







