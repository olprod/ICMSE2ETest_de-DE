---
title: Vermeiden Sie Ereignisse verloren
description: Vermeiden Sie Ereignisse verloren
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 7512de7a-de82-43e5-b100-d82faf59a7cb
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: a0b3911d9d880cfc3d76ee21c4ab18651e8e29ee
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="avoid-lost-events"></a>Vermeiden Sie verloren gegangene Ereignisse


In Windows Performance Aufzeichnung (WPR) generieren einiger Anwendungen so viele Ereignisse dieses Event Tracing for Windows (ETW) mit der Häufigkeit der Protokollierung halten ist nicht möglich. Sie können dieses Problem Manifeste als verloren gegangene Ereignisse in der Aufzeichnungen. Das Problem kann aufgrund unvollständiger Daten zu Probleme bei der Analyse oder fehlerhafte Schlussfolgerungen führen.

**Hinweis**  
Standardmäßig verwendet WPR ausgelagerten Arbeitsspeicher für Puffer. Legen Sie WPR nicht ausgelagerte Arbeitsspeicher für Puffer verwenden Sie zum Festlegen des *NonPagedMemory* -Attributs auf *true fest,* für den Anbieter. Weitere Informationen zum Erstellen eines benutzerdefinierten Profils finden Sie unter [Authoring Aufzeichnung Profile](authoring-recording-profiles.md) und [2. System- und Definitionen für Ereignis Anbieter](2-system-and-event-provider-definitions.md).

 

Sie können verhindern, WPR verlieren ETW-Puffer oder Ereignissen auf folgende Weise:

-   Verwenden Sie größere Puffer, um effizienter Datenträger-e/a zu aktivieren, wenn WPR Puffer auf Datenträger schreibt.

-   Count-Anforderungen für die Erfassung der ersten für die Verwendung einer bestimmten Puffer-Konfigurations auf einem Computer.

-   Verwenden Sie die Option Command-Line **RecordTempTo** an einem anderen Speicherort als für das Standardgebietsschema aufzeichnen.

-   Erhöhen der Anzahl der Puffer.

-   Vereinfachen Sie das Szenario, das Sie testen, oder wählen Sie weniger Profile.

-   Freier Speicherplatz auf dem Systemlaufwerk.

-   Verwenden Sie erweiterten Hardware zum Sammeln der Daten. Verwenden Sie beispielsweise eine Festplattensubsystem, das einer höheren Durchsatz hat. Dies ist die letzte Option, berücksichtigt werden sollten. Sie können die Ereignisse durch Auswählen von sorgfältig die Anbieter zu aktivieren und die zu verwendenden Puffer verlieren normalerweise vermeiden.

## <a name="related-topics"></a>Verwandte Themen


[Häufige Szenarien WPR](windows-performance-recorder-common-scenarios.md)

[Aufzeichnung Profile](recording-profiles.md)

[Protokollierungsmodus](logging-mode.md)

[Ändern Sie den Protokollierungsmodus](change-the-logging-mode.md)

[Detailstufe](detail-level.md)

[Ändern der Detailebene](change-the-detail-level.md)

[Sitzungen](sessions.md)

[Sitzungen (Windows-Treiber)](http://go.microsoft.com/fwlink/p/?linkid=246706)

 

 







