---
title: Sitzungen
description: Sitzungen
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: cb2a15ea-3519-4efb-8031-93b19fac10d4
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: a5186b06819c8ea1db76558e7678a65ae2c417d7
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="sessions"></a>Sitzungen


Windows Performance Aufzeichnung (WPR) erweitert Event Tracing for Windows (ETW). Eine protokollierungssitzung ETW ist eine Auflistung von Puffer im Arbeitsspeicher, die Ereignisse über die ETW-Anbieter Application programming Interface (API) akzeptiert. Diese Puffer sind in der Regel nicht ausgelagerten und werden durch den Kernel verwaltet. ETW weist einen Puffer zu jedem Prozessor. Generieren von ETW-Ereignissen und Pufferung ist Sperre frei ETW sich alle Arten von Ereignissen aktivieren.

Jedes Mal, wenn diese ETW die **EventWrite** -Methode aufruft, reserviert ETW Speicherplatz im aktuellen Puffer an, dem ETW Prozessor zugeordnet wurde, die den aufrufenden Thread ausgeführt wird. ETW kopiert dann, das die Ereignisdaten für Kopf- und Benutzer in diesem Bereich. Wenn der Puffer voll ist, leert ETW Puffers in die protokollierungssitzung Protokolldatei oder Real-Time streaming Consumer. ETW weist einen freien Puffer zu dieser Prozessor.

Überschreitet der Durchsatz Protokollierung die Möglichkeit von der Flusher Puffer frei, möglicherweise alle verfügbaren Pufferspeicherplatz in die protokollierungssitzung nicht mehr verfügbar sind. Beispielsweise kann dies auftreten, der Datenträger schreiben Durchsatz niedriger als der eingehende Ereignis Durchsatz ist. Dies bewirkt, dass **EventWrite** einen FEHLER ausgelöst\_NICHT\_ENOUGH\_Speicherfehler und verlieren die Ereignisdaten. In solchen Fällen erhöht ETW die **EventsLost** -Eigenschaft der protokollierungssitzung, damit die Consumer der Datenverlust sehen können.

Weitere Informationen dazu, wie Sie Ereignisse in einer Aufzeichnung Verlust zu vermeiden finden Sie unter [Verloren Ereignissen zu vermeiden](avoid-lost-events.md).

## <a name="logging-to-memory-or-to-a-file"></a>Protokollierung im Arbeitsspeicher oder in eine Datei


Profile, um die Ereignisdaten Puffer im Arbeitsspeicher oder in eine Datei zeichnen können konfiguriert werden. Zwischenspeichern Modus ist eine kreisförmige in-Memory-Sitzung. Sie können den Inhalt dieser Sitzung als Snapshot Event Trace Log (ETL) Datei auf einem Anforderung speichern. WPR zu den Inhalt der in-Memory-Pufferspeicherplatz nicht leeren, wenn Sie den Inhalt speichern.

Lassen Sie die Pufferung Modus Sitzungen auf ständig. Dies ist besonders nützlich, wenn Sie nicht wissen, wenn das Verhalten von Interesse stattfindet. Wählen Sie Pufferung Modus wird die erforderliche kreisförmige Pufferspeicherplatz klein genug, und im Arbeitsspeicher gespeichert werden. Sequenzielle Protokolldateien sind am besten für gesteuerte Szenarien. Beispielsweise können Sie sequenzielle Protokolldateien für Regressionstests oder das Vorkommen des Verhaltens von Interesse einfacher vorhergesagt werden kann.

Weitere Informationen zu den Optionen für die Protokollierung finden Sie unter [Logging Modus](logging-mode.md).

## <a name="recording-profiles"></a>Aufzeichnung Profile


Ein Profil Aufzeichnung steuert jede Sitzung. Das Profil kann entweder ein integriertes Profil oder ein benutzerdefiniertes Profil sein. Weitere Informationen finden Sie unter [Aufzeichnung Profile](recording-profiles.md).

## <a name="buffer-size"></a>Puffergröße


Puffergröße ist für die Steuerung von e/a-Effizienz und sicherstellen, dass WPR nicht große überspringen wichtig. Effizienz der e/a-schreiben können sehr kleine Puffer reduziert werden. Es wird empfohlen, eine minimale Puffergröße 64 KB oder 128 KB zur Förderung der Schreibzugriff eine gute Leistung und Reduzierung der Mehraufwand für den Datenträger und verloren gegangene Ereignisse. Puffergröße bestimmt die maximale Dauer einer Aufzeichnung. ETW beschränkt die größte-Ereignis für etwa 64 KB.

## <a name="collectors"></a>Kollektoren


Sie müssen ein Collector des Systems und Sammeln von Ereignissen eine oder mehrere für eine Sitzung im Profil Aufzeichnung definieren. Der Name der Sammlung muss auf das System eindeutig sein, und das System benötigen exklusiven Schreibzugriff auf die Protokolldatei. Der Name der Protokolldatei muss auch zwischen den Dateinamen der Sammelstellen eindeutig sein. WPR wird nicht Umgebungsvariablen, erweitert, damit der Pfad zur Protokolldatei ohne Umgebungsvariablen angegeben werden muss. Weitere Informationen finden Sie unter [1. Collector Definitionen](1-collector-definitions.md).

## <a name="providers"></a>Anbieter


Die protokollierungssitzungen Sammeln von einem definierten Satz von System- und Ereignis-Anbieter. Dies ist ein wichtiger Element so konfigurieren Sie für einzelne pro Sitzung. Die meisten Anbieter können eine m: n-Beziehung mit Sitzungen aufweisen. Besondere Anbieter sind für einige, wie etwa Kernel oder Heap Ereignisse erforderlich. Weitere Informationen finden Sie unter [Anbieter](providers.md).

## <a name="related-topics"></a>Verwandte Themen


[WPR-Features](wpr-features.md)

[Häufige Szenarien WPR](windows-performance-recorder-common-scenarios.md)

[Aufzeichnung Profile](recording-profiles.md)

[Puffer](buffers.md)

[Puffergröße](buffersize.md)

 

 







