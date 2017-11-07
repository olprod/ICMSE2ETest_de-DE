---
title: Freigabe und Zusammenarbeit
description: Freigabe und Zusammenarbeit
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: A75836F3-237B-4283-9948-08AB22966A7D
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 459110ebdcdc349084cd9c8a81882b4ef0e1d154
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="sharing-and-collaboration"></a>Freigabe und Zusammenarbeit


Sie können einen Trace in einer Zip-Datei zusammen mit der entsprechenden Sitzung, Anmerkungen, Packen und Symbole mit WPA (optional) geladen. Dadurch können Sie dieses Paket mit anderen Entwicklern freigeben und [WPA Sitzungen](save-state-at-the-end-of-a-wpa-session.md)ersetzt. Ein Paket WPA ("Trace Package) erfasst die gesamte Analysis-Sitzung wird:

-   Trace
-   Registerkarten
-   Diagramm-Konfigurationen
-   Filter
-   Anmerkungen
-   Symbole **Notiz** WPA Pakete Symbole nur, wenn sie geladen werden; Wenn sie sind, werden Sie von WPA im Paket eingebettet. WPA wird Stack Expansions nicht beibehalten werden.

     

## <a name="benefits-of-sharing-a-trace-package"></a>Vorteile der Freigabe ein Trace-Paket


Neben dem, Anwendungen oder Bildschirme freigeben ein Pakets Trace mit anderen Entwicklern, bieten Trace Pakete Reihe weiterer Vorteile:

-   Weniger Speicherplatz, da Trace-Pakete komprimiert werden
-   Unterstützung für und die Möglichkeit zum Öffnen der ZIP-nach-oben-Ablaufverfolgungsdateien in WPA
-   Möglichkeit, öffnen Sie ein Paket Trace mehrmals ohne den gleichen Trace mehrmals extrahieren
-   Überprüfung-Plug-in und Warnungen Wenn-Plug-Ins nicht angezeigt, wenn WPA Ihrer Trace-Paket wird geöffnet.

**Hinweis**  In diesem Prozess komprimiert up Ihre Trace im Paket. Wenn Ihre Trace ein Problem hat und empfindlichem Material enthält und Sie es uns zur weiteren Untersuchung senden, stellen Sie sicher, dass Sie vertrauliche Material zu schützen, wie Sie eine beliebige Trace an. Aufgrund von komprimieren, müssen das Paket wahrscheinlich kleinere eine im Vergleich zu einer Trace Dateigröße; Dies bedeutet nicht, dass dieses Prozesses vertraulichen Informationen entfernt.

 

## <a name="sharing-a-trace-package"></a>Freigabe eines Trace-Pakets


Konfigurieren Sie zum Erstellen eines Profils zunächst Ihre Ansichtslayout wie angezeigt werden gewünscht, und klicken Sie dann die folgenden Schritte aus:

1.  Wählen Sie im Menü **Datei** dann **Paket exportieren**. Ein Dialogfeld Speichern unter wird geöffnet.

2.  Navigieren Sie zum gewünschten Speicherort.

3.  Vergewissern Sie sich speichern als Typ-Lesevorgänge, nennen Sie Ihre Exportpaket **WPA-Paket (\*.wpapk)**und klicken Sie auf **Speichern**. Ein Wpapk-Statusleiste zeigt, Paketprozess angibt. Sie können das Fenster schließen, wie der Prozess weiterhin im Hintergrund bis zum Abschluss ausgeführt.

## <a name="related-topics"></a>Verwandte Themen


[WPA gängige Szenarien](windows-performance-analyzer-common-scenarios.md)

 

 







