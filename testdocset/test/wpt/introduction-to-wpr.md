---
title: "Einführung in WPR"
description: "Einführung in die WPR"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: f2d73e54-da70-42d6-80c6-6ff22983ea9f
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: b48705a3de80347234fea16d7b2b1d28af593338
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="introduction-to-wpr"></a>Einführung in WPR


Windows Performance Aufzeichnung (WPR) ist ein Tool, das Event Tracing for Windows (ETW) erweitert und bietet detaillierte Aufzeichnungen der System- und Verhalten und Ressource: Einsatz. WPR zusammen mit Windows Performance Analyzer (WPA) können bestimmte Bereiche der Leistung untersuchen und ein allgemeines Verständnis der Ressourcenverbrauch zu erhalten. Aktivieren WPR und WPA Entwicklungs- und IT-Experten, proaktive identifizieren und Beheben von Leistungsproblemen. WPR erfordert Windows 7 oder höhere Version des Betriebssystems.

## <a name="wpr-user-interface"></a>WPR-Benutzeroberfläche


Die WPR-Benutzeroberfläche (UI) ganz einfach um eine Aufzeichnung mithilfe von integrierten Aufzeichnung Profile zum Analysieren der CPU-Auslastung, Power Probleme, schlechter System oder Leistung der Anwendung oder andere Leistungsprobleme zu generieren.

## <a name="authoring-custom-recording-profiles"></a>Erstellen von benutzerdefinierten Aufzeichnung Profile


Sie können benutzerdefinierte Profile in XML-DATEI erstellen und diese WPR hinzufügen. Benutzerdefinierte Profile können einzeln oder zusammen mit integrierten Profile oder spezialisierte Aufzeichnungen tätigen, die für alle Verwendungsszenario vorgesehen sind.

## <a name="logging-to-file-or-memory"></a>Datei oder im Arbeitsspeicher der Protokollierung


WPR kann Ereignisse protokolliert, entweder eine Datei oder in zirkulären Puffer im Arbeitsspeicher. Es wird empfohlen, dass Sie in Datei für begrenzte Ereignisse, die wie Anwendung Startpfade oder Power-Auslastung protokollieren bei der Computer aus dem Ruhezustand hervorgeht vorhergesagt werden können. Protokollierung der Datei ist die einzige Protokollierungsmodus, in dem Ereignisse über on/off Übergänge gemessen verfügbar ist.

Es wird empfohlen, dass Sie sich auf den Speicher für unvorhersehbare Ereignisse. Sie können diese Aufzeichnungen für längere Zeit ausführen, ohne endlichen Speicherressourcen zu verarbeiten.

## <a name="detail-level"></a>Detailstufe


Sie können die Detailebene, die das Szenario passt auswählen: oberflächliche noch in "ausführlich". Helle Aufzeichnungen erfordern einen geringeren Aufwand und weniger mit dem System (sie werden auch als "Timing" Aufzeichnungen bezeichnet) in Konflikt geraten. Ausführliche Aufzeichnungen eignen sich mehr für gründliche Analyse.

## <a name="related-topics"></a>Verwandte Themen


[Windows Performance Aufzeichnung](windows-performance-recorder.md)

[Schneller Einstieg in WPR](wpr-quick-start.md)

 

 







