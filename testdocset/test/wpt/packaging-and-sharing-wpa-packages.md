---
title: Schritt 2 Verpackung und Freigabe WPA Pakete
description: "Sie können einen Trace in einer Zip-Datei zusammen mit der entsprechenden Sitzung, Anmerkungen, Packen und Symbole mit WPA (optional) geladen."
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 0F54D05A-DB6D-4553-BB31-CD4B7F28DA20
ms.openlocfilehash: 6fe45f52b98825e80f83261d3bb043db819710bd
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="step-2-packaging-and-sharing-wpa-packages"></a>Schritt 2: Packen und Freigabe WPA Pakete


Sie können einen Trace in einer Zip-Datei zusammen mit der entsprechenden Sitzung, Anmerkungen, Packen und Symbole mit WPA (optional) geladen. Dadurch können Sie dieses Paket mit anderen Entwicklern gemeinsam nutzen und WPA Sitzungen ersetzt. Ein Paket WPA ("Trace Package) erfasst die gesamte Analysis-Sitzung wird:

-   Trace
-   Registerkarten
-   Diagramm-Konfigurationen
-   Filter
-   Anmerkungen
-   Symbole **Hinweis** Hinweis WPA nur Pakete Symbole geladen werden. Wenn sie sind, werden Sie von WPA im Paket eingebettet. WPA wird Stack Expansions nicht beibehalten werden.

     

## <a name="benefits-of-sharing-a-trace-package"></a>Vorteile der Freigabe ein Trace-Paket


Neben dem, Anwendungen oder Bildschirme freigeben ein Pakets Trace mit anderen Entwicklern, bieten Trace Pakete Reihe weiterer Vorteile:

-   Weniger Speicherplatz, da Trace-Pakete komprimiert werden
-   Unterstützung für und die Möglichkeit zum Öffnen der ZIP-nach-oben-Ablaufverfolgungsdateien in WPA
-   Möglichkeit, öffnen Sie ein Paket Trace mehrmals ohne den gleichen Trace mehrmals extrahieren
-   Überprüfung-Plug-in und Warnungen Wenn-Plug-Ins nicht angezeigt, wenn WPA Ihrer Trace-Paket wird geöffnet.
    **Hinweis**  Hinweis: Dieser Prozess von Ihrer Trace im Paket komprimiert. Wenn Ihre Trace ein Problem hat und empfindlichem Material enthält und Sie es uns zur weiteren Untersuchung senden, stellen Sie sicher, dass Sie vertrauliche Material zu schützen, wie Sie eine beliebige Trace an. Aufgrund von komprimieren, müssen das Paket wahrscheinlich kleinere eine im Vergleich zu einer Trace Dateigröße; Dies bedeutet nicht, dass dieses Prozesses vertraulichen Informationen entfernt.

     

## <a name="sharing-a-trace-package"></a>Freigabe eines Trace-Pakets


Konfigurieren Sie zum Erstellen eines Profils zunächst Ihre Ansichtslayout wie angezeigt werden gewünscht, und klicken Sie dann die folgenden Schritte aus:

1.  Wählen Sie im Menü Datei dann Paket exportieren. Ein Dialogfeld Speichern unter wird geöffnet.
2.  Navigieren Sie zum gewünschten Speicherort.
3.  Nennen Sie Ihre Exportpaket, stellen Sie sicher speichern als Typ WPA Paket liest (\*.wpapk), und klicken Sie auf Speichern. Ein Wpapk-Statusleiste zeigt, Paketprozess angibt. Sie können das Fenster schließen, wie der Prozess weiterhin im Hintergrund bis zum Abschluss ausgeführt.

 

 






