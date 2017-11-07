---
author: Justinha
Description: Hohe DPI Projektion und mehrere Bildschirme-Konfigurationen
ms.assetid: 81a96303-5ab5-4002-acac-ab356e2ec829
MSHAttr: PreferredLib:/library/windows/hardware
title: Hohe DPI Projektion und mehrere Bildschirme Konfigurationen
ms.openlocfilehash: 7e3990a2e3b43bf10a6c2ce4df1245519abd501d
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="high-dpi-projection-and-multi-monitor-configurations"></a>Hohe DPI Projektion und mehrere Bildschirme Konfigurationen


Viele Unternehmensbenutzer Verwenden sekundärer zeigt für Zwecke wie andocken, Projektion oder ihren Desktop auf einen sekundären Monitor erweitern.

Diese Szenarien, wirken sich nicht auf die Anweisungen für Geräte mit 150 % und 200 %, doch für Benutzer mit 125 % Anzeigegeräte, die einer sekundären Monitor oder desktop Dockingstation auch verwenden, empfehlen wir den Windows 8-Kompatibilitätsmodus, der in [beheben verschwommenen Text in Windows 8.1 für IT-Spezialisten](fixing-blurry-text-in-windows-for-it-professionals.md#unaware)beschrieben ist. Zusätzliche Hinweise zur kompatible Geräte und Projektoren wird in diesem Thema bereitgestellt.

## <a name="span-idprojectionspanspan-idprojectionspanprojection-experiences"></a><span id="projection"></span><span id="PROJECTION"></span>Projektion Erfahrungen


Windows 8.1 wurde Unterstützung für Projektion Erfahrungen optimiert. In früheren Versionen von Windows möglicherweise der Benutzer über eine hohe DPI-Gerät finden Sie unter Inhalte, die auf dem niedrig DPI Projektor zu groß wurde erhalten Sie alle relevanten Inhalte zu Bildschirm für Präsentationszwecken optisch erschwert. Es gibt zwei Projektion Modi: *Duplizieren* und *Erweitern*. In diesem Abschnitt wird beschrieben, wie Windows alle drei Modi unterstützt.

### <a name="span-idduplicatemodedefaultforprojectionandtypicallyusedforprojectionspanspan-idduplicatemodedefaultforprojectionandtypicallyusedforprojectionspanspan-idduplicatemodedefaultforprojectionandtypicallyusedforprojectionspanduplicate-mode-default-for-projection-and-typically-used-for-projection"></a><span id="Duplicate_mode__default_for_projection_and_typically_used_for_projection_"></span><span id="duplicate_mode__default_for_projection_and_typically_used_for_projection_"></span><span id="DUPLICATE_MODE__DEFAULT_FOR_PROJECTION_AND_TYPICALLY_USED_FOR_PROJECTION_"></span>Doppelte Modus (Standard für Projektion und in der Regel für Projektion verwendet)

Der Projektion Standardmodus heißt Duplikat Modus. (Geben Sie auf der Tastatur, um eine Liste der vier mehrere Bildschirme Anzeigemodi finden Sie unter **Win + P** : **nur PC-Bildschirm**, **Duplizieren**, **Erweitern**und **zweiten** nur am Bildschirm.) Im Duplicate-Modus ist denselben Inhalt wie auf dem Projektor auf der Laptop-Bildschirm angezeigt. Dadurch wird die einfachste für den Referenten interagieren direkt mit dem Inhalt anzeigen auf dem Bildschirm, insbesondere bei Laptop oder Tablet, die Fingereingabe unterstützt wird. In diesem Modus wird Windows betrachten Sie beide anzeigen, versuchen Sie die beste Lösung für die allgemeine finden und platzieren Sie dann in dieser Lösung beide anzeigen. In Windows 8.1 weist diese Änderung Auflösung einen Einfluss auf die Anzeige Skalierungsfaktor, Windows wird dann basierend auf den neuen Skalierungsfaktor neue Skalierung vornehmen, inkrementell Projektion optimal.

### <a name="span-idextendmodetypicalformulti-monitordesktopscenariosspanspan-idextendmodetypicalformulti-monitordesktopscenariosspanspan-idextendmodetypicalformulti-monitordesktopscenariosspanextend-mode-typical-for-multi-monitor-desktop-scenarios"></a><span id="Extend_mode__typical_for_multi-monitor_desktop_scenarios_"></span><span id="extend_mode__typical_for_multi-monitor_desktop_scenarios_"></span><span id="EXTEND_MODE__TYPICAL_FOR_MULTI-MONITOR_DESKTOP_SCENARIOS_"></span>Erweiterungsmodus (Standard für desktop Szenarien mit mehreren Monitor)

In der Erweiterungsmodus ist der Projektor aus der primären Anzeige als eine separate Anzeige behandelt. Dieser Modus wird für Benutzer mit mehreren Bildschirmen oder Andocken Szenario typische. Der Benutzer kann ziehen oder Verschieben von Inhalten in getrennte Anzeige mithilfe der Maus oder Touchpad. Dies ist nicht die Standardoption, aber einige Benutzer bevorzugen diese Einstellung, (um nur ein Beispiel erteilen, da es den Benutzer ermöglicht, trennen Sie die Notizen aus ihrer Präsentation). In diesem Modus Windows 8.1 ordnet eine entsprechende Skalierungsfaktor für jeden Bildschirm, und wenn der Benutzer den Inhalt an den Projektor bewegt, Windows wird skalieren entsprechend erneut sicherstellen, dass die Projektion optimal.

### <a name="span-iditprospanspan-iditprospanwhat-this-means-for-the-it-professional"></a><span id="itpro"></span><span id="ITPRO"></span>Was bedeutet dies für IT-Experten

Für Projektion-Szenarien ist die Skalierung pro Monitor erforderlich, um eine verwendbare Projektion Erfahrung für 150 % und 200 % zeigt bereitzustellen. In einigen Fällen möglicherweise Benutzer mit 125 % Geräte Probleme mit apps, die nicht DPI wissen verschwommeneres beim projiziert wird. Anleitungen zum Deaktivieren pro app-DPI-Skalierung in diesen Fällen finden Sie unter [behoben verschwommenen Text in Windows 8.1 für IT-Experten](fixing-blurry-text-in-windows-for-it-professionals.md#unaware) .

**Wichtige**  
Projektoren Arbeit am besten in doppelte Modus, wenn sie unterstützen die Auflösung und video-Modi, die an das Gerät ähneln, die Projektion ist. Beispielsweise bei dominanten tragbaren Geräte im Unternehmen 1366 x 768 und 1920 x 1080 zeigt, sollten die Projektoren, die verwendet werden die gleichen Lösungen für die am besten doppelte Modus Erfahrungen erfolgen.

 

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Hochauflösenden Unterstützung für IT-Experten](high-dpi-support-for-it-professionals.md)

 

 






